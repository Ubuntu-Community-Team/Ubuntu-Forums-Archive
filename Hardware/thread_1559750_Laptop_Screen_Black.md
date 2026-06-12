---
title: "Laptop Screen Black"
date: 2010-08-23
forum: Hardware
---

### Post by jdm12989 on 2010-08-23
Alright, so I am new to using Linux and I've been having some trouble getting the full features of my graphics card.

Ubuntu 10.04 LTS
Alienware M17 R1
ATI Mobility Radeon HD3870

The issue is after installing and setting everything up I want to get the full feature drivers working so I go to System > Administration > Hardware Drivers , and install the "ATI/AMD proprietary FGLRX graphics driver". Then I reboot and I get past the grub but the my laptop screen goes to a blank state with the backlight on. In this configuration I can plug in a external VGA or HDMI moniter and see the screen, so it's still semi-functional.

Any help would be greatly appreciated and if there is any logs you need just tell me the terminal commands and I'll post them ASAP.

---

### Post by jdm12989 on 2010-08-24
The xorg.conf that when used causes the black screen.

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:6:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by jdm12989 on 2010-08-25
Alright, so I followed the instruction here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and it installed fine and catalyst control center works.

However, there is still a noticeable lack of power...

---

