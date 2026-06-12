---
title: "upgrade to 9.04 - cant access 2nd display with mouse"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by NorthernSuze on 2009-10-31
Today I pushed the upgrade button from 8.10 to 9.04... 
I am using the restricted drivers for nVidia with separate x screens (xinerama) 

The 2nd display CRT shows up as before the upgrade, programs open on both displays and but the mouse is trapped on the laptop screen ....  a true instance of, "you can't get there from here!" <grin>

I have searched forums and restored an older working xorg.conf. I have googled, but can't seem to find a solution. I hate not being able to figure this out myself, it seems like it should be so obvious! If you can help it would be much appreciated.

Suzanne
I wanted to attach a copy of my xorg.conf as a txt file but the manage attachment window is opening on the CRT display!!!

*****I did discover I can use the wacom tablet to move cursor between displays (rather erratically); a ghost cursor is left behind, and still leaves cursor bound within new display 

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 1024
    Screen      1  "Screen1" 160 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
    Option	   "DontZap"  "off"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "NEC FP955"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9650M GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9650M GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "1440x900_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1440x900_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: 1440x900 +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

