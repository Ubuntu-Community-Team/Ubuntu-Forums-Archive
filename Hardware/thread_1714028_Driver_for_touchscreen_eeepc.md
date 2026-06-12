---
title: "Driver for touchscreen eeepc"
date: 2011-03-24
forum: Hardware
---

### Post by Dsky on 2011-03-24
I need drivers for the touchscreen for my Eee pc for ubuntu 10.10...

where can i find them?

---

### Post by Dsky on 2011-03-26
can someone help me?

i did this

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

and then

> Linux driver installer for TouchKitTouch controller 

(I) Check user permission: root, you are the supervisor.
(I) Begin to setup the TouchKitTouch driver.
(I) Found and removed previous TouchKitTouch driver.
(I) Extract TouchKitTouch driver archive to /usr/local/TouchKit32.
(I) Create TouchKit utility shortcut in /usr/bin.
(I) Create TKCal tool shortcut in /usr/bin.
(I) Check X window version: 6.9.0 ~ 7.2.0
(I) Copy X module: x69/egalax_drv.so to /usr/lib/xorg/modules/input.

(Q) Which interface controller do you use?
(I) [1] RS232 [2] PS/2 [3] USB : 3
(I) Using interface: USB
(I) Found a HID compliant touch controller.
(I) Found inbuilt kernel module: usbtouchscreen.
(I) It is highly recommended that add it into blacklist.
(Q) Do you want to add it into blacklist? (y/n) y

(I) Found X configuration file: /etc/X11/xorg.conf.
(I) Removed touch configuration from /etc/X11/xorg.conf.
(I) Add touch configuration into /etc/X11/xorg.conf.

(I) Please reboot the system for some changes to take effect.
(I) After booting, type "TouchKit" to do calibration.


but still "no touch controller found"

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "glx"
    Load  "record"
    Load  "dri"
    Load  "dri2"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

