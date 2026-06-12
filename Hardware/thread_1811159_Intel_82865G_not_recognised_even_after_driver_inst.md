---
title: "Intel 82865G not recognised even after driver installed"
date: 2011-07-24
forum: Hardware
---

### Post by winnest on 2011-07-24
Hi,
I am posting this thing problem after searching heavily and trying too many things but to no good.
I am using ubuntu 10.10 on a machine with Intel82865G graphics controller and pentium D (64bit) microprocesoor. Also I have a HP vs17e monitor. The pproblem is that  OS detetcs the monitor as unknown as runs on a resolution of 1024x768@60Hz, although the monitor supports 1280x1024 @60hz. I searched around in forums , upgraded packages which indeed installed the xserver-xorg-video-intel drivers for the chipset . but nothing happened , the monitor is still unknown and I cannot set the resolution to 1280x1024. I even tried xrandr --newmode  & ---addmode commands as according to post -- 
[http://ubuntuforums.org/showthread.php?t=1364460&highlight=UNKNOWN+MONITOR](http://ubuntuforums.org/showthread.php?t=1364460&highlight=UNKNOWN+MONITOR)

but it shifts the screen to a top left potion with rest of the screenbeing black.

even the xorg.conf file does not recognise my graphics controller . I am pasting its contents below
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
    Load  "record"
    Load  "extmod"
    Load  "dri"
    Load  "dri2"
    Load  "dbe"
    Load  "glx"
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
  
```:(

Pls help or guide in proper direction!!

---

