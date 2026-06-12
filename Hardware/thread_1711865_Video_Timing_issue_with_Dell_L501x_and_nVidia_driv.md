---
title: "Video Timing issue with Dell L501x and nVidia drivers"
date: 2011-03-21
forum: Hardware
---

### Post by chanman on 2011-03-21
Some Background:
I have installed a new LCD into my L501x. I purchased the AUO B156HW01 V4, which is a 1080p display. The Dells originally come with the B156HW01 V7 upgrade option, which is are a glossy display. I purchased my Dell with a 720p screen and swapped out the screen myself.

The screen works fine when I run windows, but its discolored and stretched out horizontally when running under linux with the nvidia drivers. When I run it with the Nouveau, it displays fine but only runs at 800x600.

tried running "sudo ddcprobe | grep monitorrange" but got nothing. I tried running "sudo xvidtune -show" got a error saying it can't find the display

Here is my config
```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 60.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

Here is the error in the xorg log
```
[   228.785] (--) NVIDIA(0): Connected display device(s) on GeForce GT 435M at PCI:2:0:0
[   228.785] (--) NVIDIA(0):     LEN (DFP-0)
[   228.785] (--) NVIDIA(0): LEN (DFP-0): 330.0 MHz maximum pixel clock
[   228.785] (--) NVIDIA(0): LEN (DFP-0): Internal Dual Link LVDS
[   228.789] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1920x1080"
[   228.789] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[   228.789] (WW) NVIDIA(0):     HorizSync range (56.502-67.804 kHz) would exclude this
[   228.789] (WW) NVIDIA(0):     mode's HorizSync (45.2 kHz); ignoring HorizSync check for
[   228.789] (WW) NVIDIA(0):     mode "1920x1080".
[   228.789] (WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1920x1080"
[   228.789] (WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
[   228.789] (WW) NVIDIA(0):     HorizSync range (56.502-67.804 kHz) would exclude this
[   228.789] (WW) NVIDIA(0):     mode's HorizSync (45.2 kHz); ignoring HorizSync check for
[   228.789] (WW) NVIDIA(0):     mode "1920x1080".
[   228.809] (II) NVIDIA(0): Assigned Display Device: DFP-0
[   228.809] (==) NVIDIA(0): 
[   228.809] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   228.809] (==) NVIDIA(0):     will be used as the requested mode.

```

---

