---
title: "HDTV Samsung R7 1360x768 resolution + Asus W7J laptop"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by ryousuke on 2007-09-22
hi guys,

new to the world of linux but exciting neither the less...

hopefully can get some help with gettin 1360x768 resolution to work on my foresight settup.

firstly my setup
asus W7J laptop connected to Samsung 32" HDTV

can someone shoot me their xorg.conf file so i can see what i'm doing wrong?

i've installed lastest nvidia drivers

when i add "1360x768" in my file i still cant select that resolution under nvidia-settings

---

### Post by snkorea on 2007-12-14
did you manage to make it work?
i have the same Asus w7j and another Asus LCD.
i managed to have the TwinScreen with the nvidia-glx-new driver
but i just can't have more than 640x480 on the LCD ...

[code]
Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72M [GeForce Go 7400]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [GeForce Go 7400]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Modes      "1280x800"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection     "Display"
        Depth       16
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    16
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection
[code]

This is the xorg.conf i get when i use 
# sudo nvidia-settings
and this is the only way i managed to make the LCD works ...
Others xorg.conf manually set just failed ...

i just can't understand why i cant manage to have more than 640x480...
if someone could help me ...
thanks for all

JF

---

### Post by lancest on 2007-12-25
Same W7j with Nvidia 7300
Unable to get anything but 480x640, and 800x600 on Epson projector
Previously able to use Twinview with cloning at 1280x800 before last Nvidia driver update. Tested with an LCD monitor and works fine though. 
Not sure what to do about this.

---

### Post by ptumik on 2008-05-06
Same problem here.
Asus W7J and Toshiba 37" TV (1360x786). All options that I have are: 640 and 320 resolutions. :(
Have tried to play with xorg.conf - doesn't help. I suspect that the problem is in driver. :(

But it's working fine under XP.

---

