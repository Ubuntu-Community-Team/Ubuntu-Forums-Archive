---
title: "fglrx 11.11 dual GPU issues"
date: 2011-11-17
forum: Hardware
---

### Post by magowiz82 on 2011-11-17
Hi,
I have in my laptop (hp pavilion dv6 3100sl) 2 integrated ati card :
radeon hd 4250 and radeon hd 5470

the first one (4200) works without problems and it's recognized by catalyst, catalyst is also aware that there are 2 cards but if I choose to set the more performant as default it doesn't change anything after reboot (hd 4250 selected).

I created the xorg.conf using ati-config --initial -f

If I create xorg.conf using ati-config --adapters=all --initial -f I notice that also other card (which is on pci 2:0.0) is included and 2 screen sections are configured : one per each Device.

The problem with this xorg.conf is that xorg doesn't even start giving this info :
fglrx invalid video bios signature

I have no vga options in my BIOS and it's the last one provided for my laptop by HP.

I also suspect that I cannot use HDMI output because of RadeonHD 5470 not being properly set up.

---

### Post by magowiz82 on 2011-11-18
Preface : what I would like to obtain is : display of internal monitor cloned on hdtv via hdmi ( which is the way it works in windows 7 out of the box) 

I have some news : after some tries I obtained two scenarios (that don't satisfy me) :

1) disabling 4250 hd I get hdmi working but internal monitor (notebook one) is blank, even if I choose to clone screen 4 (hdmi out) on screen 3 (notebook screen via 5470 hd)

2) enabling both all 2 screen works, catalyst detect 3 attached screen : notebook via 4250hd aka 1 , notebook via 5470 hd aka 3 , hdtv (hdmi) via 5470hd aka 4. If I choose to clone 3 on 4 I get a blank screen at the right of 1 that is not managed by unity but I can see number 4 on hdtv and I can view the pointer on it (only this), I cannot clone 1 to 3 or 1 to 4, so I have my unity desktop on screen 1 , almost nothing on 3 and 4. If I disable screen 1 I cannot see nothing on internal notebook monitor so it seems that 5470hd cannot access to internal monitor.

I attach scenario 2 xorg.conf :
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[1]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1360x768"
EndSection

Section "Monitor"
    Identifier   "1-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1360x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1360x768"
    Option        "TargetRefresh" "50"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1360x768"
    Option        "TargetRefresh" "50"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[2]-1"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:2:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[2]-1"
    Device     "amdcccle-Device[2]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

---

### Post by gcbzzzz on 2011-12-09
i'm also getting the bios invalid something error message.

mine GPUs are both inside the amd cpu. one is simply a "ati device 9648" and the other is a "radeon HD 6470M"

---

