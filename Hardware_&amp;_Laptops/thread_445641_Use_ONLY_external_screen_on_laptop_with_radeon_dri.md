---
title: "Use ONLY external screen on laptop with radeon driver?"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by bogoliubov on 2007-05-16
Hello. I originally posted about this in the PPC forum, but I realized that some people may know about it without using a Mac...

I use the open source radeon driver on my iBook laptop (Radeon 9200 I think). I'd like to use ONLY the external screen, but I'm not sure how to do this. I have a pretty well optimized xorg.conf, but when I use dual screens the graphics is a but slow, so only the external would be perfect!
Does anyone know how to do this? Any help is greatly appreciated!

---

### Post by bogoliubov on 2007-05-16
I've solved it! However, it's not as fast as I had hoped for, nor does Desktop effects work OK.
Anyhow, these are the settings that I've used: (note that these settings are for a specific monitor!)




Section "Device"
        Identifier      "ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Option          "DRI" "true"
        Option          "ColorTiling" "on"
### XAA is faster than EXA, at least on Xorg Jan 2007
        Option          "AccelMethod" "XAA"
        Option          "XAANoOffscreenPixmaps"
        Option      "AGPMode" "4"
        Option      "AGPFastWrite" "on"
####    Option      "EnablePageFlip" "on"
        Option          "UseInternalAGPGART" "no"
        Option      "ColorTiling"   "on"
### RenderAccel should be enable by default if its supported
#       Option      "RenderAccel" "true"
        Option      "UseFWPLL" "true"
        Option      "EnableDepthMoves" "true"
        Option      "backingStore" "true"
        Option          "AllowGLXWithComposite" "true"
### External screen only...
        Option          "MonitorLayout" "NONE, CRT"
        Option          "DynamicClocks" "on"
        Option          "MergedFB" "true"
EndSection

Section "Monitor"
        Identifier  "COLOR LCD"
        Option      "LVDS"
EndSection

Section "Monitor"
        Identifier      "EXTERNAL"
        Option          "VGA"
        HorizSync       30-82
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
    Monitor     "EXTERNAL"
            DefaultDepth    24
        SubSection "Display"
                Depth       24
                Modes "1280x1024" "1024x768" "800x600"
EndSubSection

---

