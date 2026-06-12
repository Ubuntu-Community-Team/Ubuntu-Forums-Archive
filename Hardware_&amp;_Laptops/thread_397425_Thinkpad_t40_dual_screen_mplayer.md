---
title: "Thinkpad t40 dual screen mplayer"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by brownrl on 2007-03-30
OK this is a doozy!

I have a IBM thinkpad T40.

It has an ATI Radeon mobility 7xxx video card.

The open source 'radeon' xorg driver is great and almost everything is perfect except...

mplayer plays full screen on the internal laptop 1024x768 screen all the way full screen edge to edge. ( SUPER SWEET! )

mplayer plays full screen on the external 17" 1280x1024 LCD screen but it only plays at 1024x768 in the top left corner. The rest of screen is black as though its almost there. ( Almost SUPER SUPER SWEET! )

Here is a CnP of the crucial section of my xorg.conf:

```
Section "Device"
        Identifier      "ATI"
        Driver          "radeon"
        # accelration
        Option          "AGPMode" "4"
        Option          "EnablePageFlip" "on"
        Option          "RenderAccel" "on"
        Option          "EnablePageFlip"        "on"
        # enable (partial) PowerPlay features
        Option          "DynamicClocks" "on"
        # use bios hot keys on thinkpad (aka fn+f7)
        Option          "BIOSHotkeys" "on"
        # enable radeon specific xinerama
        Option          "MergedFB" "true"
        Option          "CRT2Position" "RightOf"
        Option          "CRT2Hsync" "50-75"
        Option          "CRT2VRefresh" "30-82"
        Option          "MetaModes" "1024x768-1280x1024"
        Option          "MergedNonRectangular" "true"
        Option          "MonitorLayout" "LVDS, CRT"
        Option          "OverlayOnCRTC1"        "on"
        Option          "OverlayOnCRTC2"        "on"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier "InternalLCD"
        Option "DPMS"
EndSection
Section "Screen"
        Identifier "Default Screen"
        Device "ATI"
        Monitor "InternalLCD"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1280x1024" "1024x768"
        EndSubSection
EndSection

```

BTW, this xorg.conf section really is the bomb for performance and I am getting good glxgears rendering. However, if someone knows the voodoo to getting true full screen on the second monitor or if you know some other good tweaks I should do, I would be extremely honored to try them out.

Thanks for any pointers...
Rob

---

### Post by brownrl on 2007-03-30
OI

Sorry but I am using mplayer in 'Xv' mode if that helps...

Regards
Rob

---

