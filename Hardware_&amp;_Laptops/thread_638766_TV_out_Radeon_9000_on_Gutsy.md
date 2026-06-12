---
title: "TV out Radeon 9000 on Gutsy"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by hibbits on 2007-12-12
Please help, I use this system to run MythTV for my kids.  I apologize for starting a  new thread, but the other similar one seems to not get much attention.

I have an Sapphire Radeon 9000 64MB with TV out.  Everything was running fine with the patched opensource driver on feisty.  Saturday I upgraded to Gutsy and I lost the tv out.

After searching around I found the following commands can be issued to make it work:
> 
> xrandr --addmode S-video 800x600
> xrandr --output S-video --mode 800x600
> xrandr --output S-video --set tv_standard ntsc
> xrandr --output S-video --off
> xrandr --output S-video --mode 800x600

[http://lists.freedesktop.org/archives/xorg/2007-October/029292.html](http://lists.freedesktop.org/archives/xorg/2007-October/029292.html)

The problem is this is not static, after reboot I loose the TV out again.  I assume there is something wrong with my xorg.conf, but I have not been able to find the right options.  Here is my xorg.conf:

> Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
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
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "MonitorLayout" "AUTO, NONE"
        Option "TVOutput"       "NTSC"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "extensions"
Option "Composite" "Enable"
EndSection

---

