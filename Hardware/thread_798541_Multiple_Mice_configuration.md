---
title: "Multiple Mice configuration"
date: 2008-05-18
forum: Hardware
---

### Post by kyozo on 2008-05-18
Hi, I have an IBM keyboard with a trackpoint and touchpad, and a separate mouse (ps2 connection), I have fiddled a bit with my xorg.conf, to disable the touchpad, but I cannot get the trackpoint and the mouse to work at the same time, any ideas?

This is my xorg.conf - I thought I could just add both my mouse identifier and the trackpoint identifier to the serverlayout section, but only 1 of them is working, and depending on which InputDevice is listed first, that is the one working.


```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "IBM Ultranav Keyboard"
    InputDevice    "IBM Trackpoint"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "IBM Ultranav Keyboard"
    Driver         "kbd"
    Option 	   "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "dk"
EndSection

Section "InputDevice"
    Identifier     "IBM Trackpoint"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mouse2"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "EmulateWheel" "true"
    Option         "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
    Identifier     "PS2 Mouse"
    Driver         "mouse"
    Option         "Device" "/dev/input/mouse3"
    Option         "Protocol" "ImPS/2"
EndSection

Section "Monitor"
    Identifier     "HP2408w"
EndSection

Section "Device"
    Identifier     "NVidia GeForce 8500"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVidia GeForce 8500"
    Monitor        "HP2408w"
    DefaultDepth    24
    Option         "NoLogo" "True"
EndSection

```


I'm using Ubuntu 8.04

Thanks

Kyozo

---

