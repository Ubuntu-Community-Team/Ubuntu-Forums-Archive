---
title: "Screen Resolution problem with ATI card on ThinkPad W500"
date: 2010-04-03
forum: Hardware
---

### Post by Patransky on 2010-04-03
Hi everyone, 

I just bought a Lenovo ThinkPad W500 with an ATI Technologies Inc Mobility Radeon HD 3650. The default screen resolution is 1900x1200, however I cannot find a way to decrease it. 

I've installed the ATI catalyst control center, but even if I change the Screen resolution I see only a shrinked screen with black stripes around it. 

In the BIOS I have the Discrete card option enabled, and by typing "lspci" I get the correct  card controller:
"01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650"

Any suggestion ? I'm getting blind by reading from such a screen :-)

Below I post a copu of my xorg.conf file.

Many thanks for any help you could provide !
 

xorg.conf:

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-LCD"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-LCD" "0-LCD"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

