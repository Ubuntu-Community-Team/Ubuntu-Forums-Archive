---
title: "hotplug projector as separate X screen"
date: 2013-10-12
forum: Hardware
---

### Post by dawus on 2013-10-12
I'm running kubuntu 13.04 with an ATI HD 7700 graphics card and the distribution's catalyst drivers. My intention is to use the system as a regular desktop PC with one monitor attached to it. However, when I hotplug a projector, it should be configured as a separate X screen without restarting X (to be used with XBMC in fullscreen mode).

Here is my xorg.conf (greated by Catalyst Control Center):

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
    Screen      1  "amdcccle-Screen[1]-1" 2560 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "0-DFP6"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "2560 0"
    Option        "Rotate" "normal"
    Option        "Disable" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1280x720"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "2560x1440"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:0:0"
        Screen      0
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP5" "0-DFP5"
    BusID       "PCI:1:0:0"
    Screen      1
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

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

This setup works basically, but suffers from two issues:

  1) X restart required (when projector is hotplugged, it displays a cloned view), i.e. logout and login again
  2) KDE task switcher gets confused (pressing <alt>+<tab> displays task switcher on second screen with no running applications; a second <alt>+<tab> has no effect anymore until you focus a window on the first screen again which brings the task switcher up on the second screen again..)

Has anybody an idea how to overcome these issues?

Many thanks!

---

### Post by dawus on 2013-10-13
Second issue should be fixed in KDE 4.11

[https://bugs.kde.org/show_bug.cgi?id=256242](https://bugs.kde.org/show_bug.cgi?id=256242)

Still looking for a solution to hotplug a monitor / projector and to get it configured as a new separate X screen without restarting X.

---

