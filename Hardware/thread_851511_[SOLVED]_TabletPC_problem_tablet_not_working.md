---
title: "[SOLVED] TabletPC problem: tablet not working"
date: 2008-07-06
forum: Hardware
---

### Post by bwald on 2008-07-06
I recently did a fresh install of Hardy Heron, and my tablet stopped working.  I have a Toshiba Tecra M4 which has run Ubuntu since Dapper, and with every previous version of Ubuntu the tablet was automatically detected.  I've tried making some changes to my xorg.conf, but nothing seems to work when I reboot.  I've copied below the default xorg.conf that is automatically generated for me when I run
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
Does anyone else who has a working tablet please tell me your xorg.conf settings?

Thank you very much.

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection
```

edit: solved

I booted with a Feisty LiveCD, and it autorecognized the screen and produced a working xorg.conf.  I copied that xorg.conf and put it in Hardy, and everything is working now.

---

### Post by bwald on 2008-07-08
bump

---

