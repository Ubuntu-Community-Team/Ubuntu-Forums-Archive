---
title: "Alps touchpad Ubuntu 7.10 - how to disable while typing"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by none-letmebe on 2008-02-24
Dear everyone,

I would like to disable the laptop touchpad while I am typing.  I have an ALPS touchpad 

cat /proc/bus/input/devices|grep ALP
N: Name="AlpsPS/2 ALPS GlidePoint"

and have made these changes to xorg.conf 

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Alps Touchpad"
EndSection

Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event2"
        Option          "Protocol"              "event"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event2"
        Option          "Protocol"              "event"
        Option "LeftEdge" "120"
        Option "RightEdge" "830"
        Option "TopEdge" "120"
        Option "BottomEdge" "650"
        Option "FingerLow" "14"
        Option "FingerHigh" "15"
        Option "MaxTapTime" "180"
        Option "MaxTapMove" "110"
        Option "ClickTime" "0"
        Option "EmulateMidButtonTime" "75"
        Option "VertScrollDelta" "10"
        Option "HorizScrollDelta" "0"
        Option "MinSpeed" "0.45"
        Option "MaxSpeed" "0.75"
        Option "AccelFactor" "0.020"
        Option "EdgeMotionMinSpeed" "200"
        Option "EdgeMotionMaxSpeed" "200"
        Option "UpDownScrolling" "1"
        Option "CircularScrolling" "0"
        Option "CircScrollDelta" "0.1"
        Option "CircScrollTrigger" "2"
        Option "SHMConfig" "true"
EndSection

I have rebooted.  When I type this it produces an error:
syndaemon -i 1 -d
Can't access shared memory area. SHMConfig disabled?

What did I miss?

Regards.

PS. Details were taken from this thread: 
[http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/](http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/)

---

### Post by deepclutch on 2008-02-24
may be u can try:
"tpconfig" ?
> configure touchpad devices 
This program can show or modify the configuration of several
different kinds of touchpad devices, including the Synaptics
TouchPad and the ALPS Glidepad/Stickpointer.

---

