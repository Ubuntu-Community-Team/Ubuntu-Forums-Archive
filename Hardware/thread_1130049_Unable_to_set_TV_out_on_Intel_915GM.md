---
title: "Unable to set TV out on Intel 915GM"
date: 2009-04-19
forum: Hardware
---

### Post by medvet on 2009-04-19
Intel 915GM on my HP NC6120 stopped seeing my TV S-VIDEO output when upgrading to intrepid - it was working in hardy (with "intel" modesetting driver as well as old "i810"). It's not working even after a fresh intrepid install & upgrade to jaunty.
I'm unable to get it detected, I tried a bunch of different xorg configurations as well as the default (empty) one.

xorg.conf #1
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

xorg.conf #2
```
Section "Device"
    Identifier "Intel Graphics Accelerator 915GM"
        VendorName "Intel Corporation"
        BoardName "Intel(R) 915GM"
        BusID "PCI:0:2:0"
    Driver "intel"
    Option "monitor-TV" "TV"
    Option "monitor-LVDS" "LVDS"
EndSection

Section "Monitor"
  Identifier "TV"
  VendorName "Generic"
  ModelName "Generic television"
  Option "Ignore" "false"
  Option "TV Format" "PAL"
  Option "TVFormat" "PAL"
  Option "TV_FORMAT" "PAL"
  Option "dpms" "false"
EndSection

Section "Monitor"
  Identifier "LVDS"
  VendorName "HP"
  ModelName "NC6120"
  Option "dpms" "true"
EndSection

Section "Screen"
  Identifier "Screen 0"
  Device "Intel Graphics Accelerator 915GM"
  Monitor "TV"
  Option "TVOutFormat" "SVIDEO"
  Option "TVStandard" "PAL-G"
  SubSection "Display"
    Viewport 0 0
    Depth 16
  EndSubSection
  SubSection "Display"
    Viewport 0 0
    Depth 24
    Modes "640x480"
  EndSubSection
EndSection

```

lspci -vvvvvvv output & xorg.0.log file with conf #1 attached.

The Fn+F4 switch works in console (but it gives a picture out of sync - probably a NTSC output).

What am I missing?

---

### Post by EdwinVL on 2009-11-25
I am suffering with exact the same hardware. I can not get any signal at the svhs plug. Are you using the sync signal from the svhs plug. It needs to be added to the video signal.

---

