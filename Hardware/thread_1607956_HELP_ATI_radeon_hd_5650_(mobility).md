---
title: "HELP ATI radeon hd 5650 (mobility)"
date: 2010-10-28
forum: Hardware
---

### Post by surveyor2 on 2010-10-28
HI
 
this is my problem I enable propriatary driver and i have a black screen at boot
I try some tuto but I have always problem
 
 
when I do lspci | grep VGA
I see
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]

```
when i do fglrxinfo I have
```
segmentation fault
```
I think this is because i don't reboot
 
this xorg.conf after aticonfig --initial
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection
Section "Files"
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

```
 
and in modules at /etc/
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp
rtc
```

---

