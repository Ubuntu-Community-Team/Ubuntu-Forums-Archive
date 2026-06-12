---
title: "Intel GMA X3100 problem (Acer Travelmate 6292)"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by Bettwurst on 2008-01-30
Hello

I have some problems with my Intel GMA X3100 graphics.
This is out of /var/log/gdm/:0.log:

(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found

Anyway, compiz and dri seems to work nearly fine but I have the feeling that someting is wrong and I can not use the full potential of this video card :) Compiz flickers a little and windows that use 3d stuff have no decoration, hence I can't resize them, etc.

This is my xorg.conf:

Section "Files"
        Modulepath      "/usr/lib64/xorg/modules"
EndSection

Section "Module"
          Load "dbe"
           Load  "extmod"

           Load  "xtrap"
           Load  "record"
   Load  "dbe"
           Load  "dri"
           Load  "freetype"

        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection



Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
#       BusID           "PCI:0:2:0"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Monitor"
        Identifier      "Standardbildschirm"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Standardbildschirm"
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
        Inputdevice     "Synaptics Touchpad"

EndSection

Any suggestions?
Thanks

---

### Post by notanatheist on 2008-02-17
Looking at the top of your post I see /usr/lib64. Are you running a 64 bit version? 

Are you seriously hoping for 3D video capabilities on a laptop with Intel graphics? I turned Compiz OFF to maximize battery and performance.

---

