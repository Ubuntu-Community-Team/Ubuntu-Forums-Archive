---
title: "Error using MacBook Pro gen3 and Dell 3007wfp hc"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by DeegC on 2007-12-26
Hello,

I've set up my MBP to dual boot OS/X and Gutsy (the Ubuntu wiki was a life-saver!) and I'm having a problem.  I'm trying to use my Dell 3007wfp hc as an external monitor but all I get is an extremely annoying flickering on the Dell.  I've installed the latest nvidia driver as reported by the [nV news Forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") and installed the new glx driver.  My xorg.conf follows.  Can someone take a quick look to see what I might have misconfigured?

Thanks!


```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load           "i2c"
        Load           "bitmap"
        Load           "ddc"
        Load           "extmod"
        Load           "freetype"
        Load           "glx"
        Load           "int10"
        Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Apple"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL3007WFPHC"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0 - 60.0
    Option          "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen         0
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen         1
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1440x900 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 2560x1600 +0+0"

        DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "2560x1600"
    EndSubSection
EndSection
```

---

