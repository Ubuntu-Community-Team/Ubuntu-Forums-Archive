---
title: "GeForce 9400M G (Seiko/Epson) resolution &amp; black screen"
date: 2014-03-07
forum: Hardware
---

### Post by dankermix2 on 2014-03-07
Hi. I have resolution 800x600 (scaled). If i and Option "ExactModeTimingsDVI" "True" and then switch to example 800x600 i have black screen.
Main resolution is 1366x768 only 60 Hz, but in specification 85/75/60 Hz ([http://multi.gnt.lt/Pages/brochures/Acer/as5737Z.pdf](http://multi.gnt.lt/Pages/brochures/Acer/as5737Z.pdf)) 
How to fix this. Sorry for my english.

Aspire 5737Z
Ubuntu 14.04 (64)
Nvidia driver 331.38

> Screen 0: minimum 8 x 8, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
HDMI-0 disconnected (normal left inverted right x axis y axis)


/etc/X11/xorg.conf
> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       30.0 - 75.0
    VertRefresh     59.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400M G"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "on"
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection





[ATTACH=CONFIG]250937[/ATTACH][ATTACH=CONFIG]250938[/ATTACH][ATTACH=CONFIG]250939[/ATTACH]

---

### Post by Bashing-om on 2014-03-08
dankermix2; Hi ! Welcome to the forum.

Switchable graphics in linux is an ongoing problem, Nvidia, for what ever reason, does not devote resources in support of their driver for linux, so we (ubuntu) make do the best we can.

Rather then repeat myself , your attention is directed to this thread.
[http://ubuntuforums.org/showthread.php?t=2209720&p=12950223#post12950223](http://ubuntuforums.org/showthread.php?t=2209720&p=12950223#post12950223)

Let us know how it goes - the open source support in release 14.04 is much improved.

we all work
[INDENT][INDENT]to make it better
[/INDENT][/INDENT]

---

