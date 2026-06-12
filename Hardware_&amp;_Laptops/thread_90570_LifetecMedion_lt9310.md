---
title: "Lifetec/Medion lt9310"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by dlfa on 2005-11-15
As far as I know, this graphics tablet is the same as some Aiptek tablet. But, alas, it is not the USB-Version but some old serial device and I can't  use it, neither mouse nor pen move.

I googled and found a lot about some hyperpen_drv.o having to be replaced by hyperpen.o written by some Roland Jansen, but I can't find a place to download this driver. Furthermore all descriptions available are only for the old xf86config files.

Besides, some say one wouldn't need that because Hoary already has some built-in aiptek drivers. 

I tried the following things:
#> cat /var/log/Xorg.0.log | grep aiptek
(II) LoadModule: "aiptek"
(II) Loading /usr/X11R6/lib/modules/input/aiptek_drv.o
(II) Module aiptek: vendor="X.Org Foundation"
(II) LoadModule: "aiptek"
(II) Reloading /usr/X11R6/lib/modules/input/aiptek_drv.o
Able to open aiptek device
Able to open aiptek device
Able to open aiptek device

So it seems there really is an aiptek driver.
A cat /dev/input/event0-3 showed the mouse on event0, keyboard on event1, *something* on event3 but nothing connected to the tablet.

This is my xorg.conf:
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
#       Load    "xf86HyperPen.so"
        Load "aiptek"
EndSection
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier "cursor"
        Driver "aiptek"
        Option "Device" "/dev/ttyS0"
        Option "Type" "cursor"
        # Option "USB" "on"
EndSection

Section "InputDevice"
        Driver "aiptek"
        Identifier "stylus"
        Option "Device" "/dev/ttyS0" # SERIAL ONLY
        # Option "Device" "/dev/input/event0" # USB ONLY
        Option "Type" "stylus"
        # Option "USB" "on" # USB ONLY
        # Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver "aiptek"
        Identifier "eraser"
        Option "Device" "/dev/ttyS0" # SERIAL ONLY
        # Option "Device" "/dev/input/event0" # USB ONLY
        Option "Type" "eraser"
        # Option "USB" "on" # USB ONLY
        # Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "cursor"     "AlwaysCore"
        InputDevice     "stylus"     "AlwaysCore"
        InputDevice     "eraser"     "AlwaysCore"
EndSection

May seem unusual, but the tablet connects to the computer via COM1 AND (PS2) keyboard. 
Anybody got any idea what to do next?

Bye,
dlfa

---

