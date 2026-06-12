---
title: "Display problems with external monitor on Dell 1501"
date: 2008-08-02
forum: Hardware
---

### Post by rdavidso on 2008-08-02
I have a dell inspiron 1501. On its own this laptop works perfectly with ubuntu. However when I connect my 22" monitor to the laptop the display resolution is rubbish on the monitor. I have tried changing the display resolution in preferences but I do not see a entry for 1600X1200, which is the resolution I require on the monitor. In windows I have the laptop running 1280X768 and the monitor running  1600X1200, and a extended desktop spanning across them both. How can I get this setup in ubuntu?

The graphics card is an 'ATI Radeon&#65533; Xpress 1150'. I have installed the latest ATI driver from the website for this.

My current xorg.conf is shown below. I have tried changing this with numerous combinations and I keep getting the problems with the display loading and I have to revert back to my old config. COuld someone supply me with a valid xorg.conf for extended desktop and the correct resolution?
Thanks

```

ection "ServerLayout
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option        "SendCoreEvents" "true"
    Option        "Device" "/dev/psaux"
    Option        "Protocol" "auto-dev"
    Option        "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    Option        "DesktopSetup" "horizontal"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection


```

---

