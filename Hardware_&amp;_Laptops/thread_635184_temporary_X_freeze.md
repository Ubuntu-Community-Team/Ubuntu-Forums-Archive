---
title: "temporary X freeze"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by plh on 2007-12-08
Hello,

I have a samsung Q35 (graphics card INTEL 945GM) under gutsy, and X11 "freezes" from time to time, for a dration of approx. 30 sec. It was already the case with feisty fawn.

Did the same thing happen to anyone else?
Thanks in advance for any help. Her is my xorg.conf:

----------------------------------

[HTML]
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express 
Integrated Graphics Controller"
        Driver          "intel"
        Option          "XAANoOffscreenPixmaps" "1"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express 
Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
[/HTML]

---

### Post by Gandi on 2008-01-20
I had the very same problem on a Samsung R65. In my system log I found the message "ata1: port is slow to respond" whenever a freeze occured. A firmware update of the DVD drive (TS-L632D) from version SC01 to SC04, which I downloaded from [www.samsungodd.com](www.samsungodd.com), solved the problem.

---

### Post by plh on 2008-01-24
Hello,

Thanks for replying!
I changed the firmware last night. I cannot be shure the problem is solved since I didn't let it run long enough, but I am shure the cd-drive does not work any more: no read, no write, no eject, no nothing :-(

Looks like I'm stuck in a trap eh? :-(

Any idea ?

---

