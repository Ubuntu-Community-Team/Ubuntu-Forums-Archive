---
title: "Ati card is very limited :("
date: 2010-06-05
forum: Hardware
---

### Post by sourchier on 2010-06-05
My ati card has very limited 3d game capability. It is a Radeon HD 4650 pci express card. So far the only game I can play without crashing has been Extreme Tux racer. I consistently get over 100 fps in that game.
	Now the bad:

Yo! frankie crashes with a segmentation fault.

Doom3 hangs during the intro.

Quake 4 hangs during the first level.

I am currently using  the flgrx drivers. However, I have used the open source drivers. They work, but cannot provide 3d support. When I use the xorg ppa or the xorg edgers ppa, the open source drivers cause strange artifacts, shadow rendering issues. Some of the characters/sprites are even drawn upside down.

Here is my xorg.conf 

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "TexturedVideo" "on"
        Option      "UseFastTLS" "1"
        BusID       "PCI:1:0:0"
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

Section "Extensions"
        Option      "Composite" "off"
EndSection

I have tried with different xorg.conf settings and even using no xorg.conf.

I am using a GA-MA770T-UD3P with the latest bios. Does anyone know any way to get these cards working without crashing?

Thank you all for your time reading this post.

---

