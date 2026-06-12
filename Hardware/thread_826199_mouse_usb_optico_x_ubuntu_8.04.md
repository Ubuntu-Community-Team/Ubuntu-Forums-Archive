---
title: "mouse usb optico x ubuntu 8.04"
date: 2008-06-11
forum: Hardware
---

### Post by eliasjr on 2008-06-11
I put a mouse optico usb in my ubuntu hh ( a note vaio vgncr120e) but it dont work...

My xorg.conf:

mouse usb: (after many attempts unsuccessful...)
```

Section "InputDevice"
    Identifier    "USB Mouse"
    Driver        "mouse"
    Option        "device"        "/dev/input/mice"
    Option        "SendCoreEvents"    "true"
    Option        "Protocol"        "IMPS/2"
    Option            "ZAxisMapping"            "4 5"
    Option            "Buttons"            "5"

EndSection
```

touchpad:

```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection
```


```
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    Inputdevice    "USB Mouse"        "Corepointer"
    InputDevice    "Synaptics Touchpad"
EndSection
```

Please someone know how configure this mouse??

Obs.: sorry my english, i am brazilian.

---

