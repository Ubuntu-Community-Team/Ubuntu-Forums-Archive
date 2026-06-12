---
title: "Savage: Battle for Newerth resolution problems with dual monitors."
date: 2008-11-16
forum: General Help
---

### Post by KameZero on 2008-11-16
I have a nvidia 6200 card with the latest drivers installed with 2 1024x768 monitors using Twinview. Savage currently runs across both monitors in 2048x768 mode, and there are no options in the resolution menu. I want to be able to run this game on one monitor(1024x768) while still being able to use the other monitor. Any help at all would be appreciated.

Xorg.conf:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E773c"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Gateway EV700"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1024+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0,CRT-1"
    Option         "metamodes" "CRT-0: 1024x768 +1024+0, CRT-1: 1024x768_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
EndSection
```

---

### Post by KameZero on 2008-11-16
Anyone have any ideas at all?

I also have a game called Regnum online installed and that runs fine across one monitor. Also, even when Savage is put into windowed mode it has no resolution options.

---

