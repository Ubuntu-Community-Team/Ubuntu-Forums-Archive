---
title: "help with kde4 and dual head ati hd 3650"
date: 2010-02-18
forum: Hardware
---

### Post by aarons6 on 2010-02-18
ok so yesterday i upgraded my video card and i have had nothing but problems with kde4.

first the details, i moved from an old 128mb nvidia 6600gt to an ati 1gb hd 3650.

ive uninstalled the nvidia drivers and modules and loaded up the ati catalyst drivers from ati website.

ive setup my xorg.conf file for dual head support.. 

mon0 
mon1 rightof mon0
blah blah.. it works in gnome with NO ISSUES.

KDE4 will not boot.. it gets to the splash screen, hard drive lights up, tools light up, world starts to light up, crash.

ok so here is what ive tried.. if i turn on xinerama kde4 boots up. its slow and when you move the windows around you can see them draw. i dont think opengl is working with xinerama.

also compositing wont turn on with xinerama on, not even on xrender.


i was using twinview with the nvidia drivers. ati doesnt seem to have a function like that.. they have whats called big desktop. it just makes a virtual screen the size of both monitors.. thats how i have it setup now and its working in gnome, i can move the windows around. i have tried to turn on visual effects but it says it cannot be enabled..

im missing something.. any ideas?
here is my xorg.conf 

###########################
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option        "Xinerama" "off"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "dri"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
    Option        "AIGLX"
EndSection

Section "InputDevice"

    # generated from default
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/psaux"
    Option        "Emulate3Buttons" "no"
    Option        "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1440x900"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "1440 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2720 2720
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Group        "video"
    Mode         0660
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

---

