---
title: "trying to get three monitors going"
date: 2011-05-29
forum: Hardware
---

### Post by gobucks747 on 2011-05-29
Hello all, 

I am attempting to get three monitors going. I have a GeForce 7300 LE running two monitors well. I am looking to add one and maybe two more monitors. My motherboard has a vga port, I was hoping to get that port running along with the geforce card running two more. Is there a way to have both cards running at once? Here is my xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer X193W"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
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
    BoardName      "GeForce 7300 LE"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 LE"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT-0: 1360x768 +0+768, CRT-1: 1360x768_60 +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT-0: 1360x768 +0+0"
# Removed Option "metamodes" "CRT-0: 1360x768 +0+768, CRT-1: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: 1360x768 +0+768, CRT-1: 1440x900 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1440x900 +0+900, CRT-1: 1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



Does anyone have any ideas? Is there another option for getting some more monitors going? I daytrade and I an suffering monitor withdrawal running ubuntu, but I am too subborn to switch back. I have been exclusively running ubuntu on my machines since 2004 and I am not ready to give up.

---

