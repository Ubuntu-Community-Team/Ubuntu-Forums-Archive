---
title: "NVIDIA 9300M Graphics Card Problem"
date: 2009-07-20
forum: Hardware
---

### Post by SilasWan on 2009-07-20
Hi Guys, I have an ASUS W7SG laptop which comes with an NVIDIA 9300M G graphics card. I recently installed Ubuntu 9.04 in the laptop and has been having display problem since. Basically it says the X Server configuration is not correct and X server could not start. More specifically, it fails to load glx and the Nvidia kernel. I am stuck with low resolution mode.

The NVIDIA graphics card incompatibility with Ubuntu was well-documented. I have tried most of the solutions offered in this forum and others with no avail. Solutions I have tried include:
1. Installed the NVIDIA drivers through envy-ng throught Synaptic.I have tried both versions 180 and 173 independently, but neither worked.
2. Installed the NVIDIA drivers directly by downloading the latest from their website (NVIDIA-Linux-x86-185.18.14-pkg1.run). I installed it successfully, but the problem didn't go away......
3. I've done the nvidia-xconfig in all cases. Didn't seem to help.
4. Installing the "standard" drivers through System->Administration->Hardware Drivers. 

etc etc

My Xorg.conf is below. Any help?


[INDENT][INDENT]Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
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

Section "Module"
    Load  "extmod"
    Load  "record"
    Load  "dbe"
    Load    "glx"
    Disable    "dri2"
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

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Device"
    Identifier  "Card0"
    VendorName  "nVidia Corporation"
    BoardName   "GeForce 9300M G"
    BusID       "PCI:1:0:0"
    Driver    "nvidia"
    ### Available Driver options are:-
    ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
    ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
    ### [arg]: arg optional
    #Option     "SWcursor"               # [<bool>]
    #Option     "HWcursor"               # [<bool>]
    #Option     "NoAccel"                # [<bool>]
    #Option     "ShadowFB"               # [<bool>]
    #Option     "UseFBDev"               # [<bool>]
    #Option     "Rotate"                 # [<str>]
    #Option     "VideoKey"               # <i>
    #Option     "FlatPanel"              # [<bool>]
    #Option     "FPDither"               # [<bool>]
    #Option     "CrtcNumber"             # <i>
    #Option     "FPScale"                # [<bool>]
    #Option     "FPTweak"                # <i>
    #Option     "DualHead"               # [<bool>]
EndSection
[/INDENT][/INDENT]

---

### Post by utnubuuser on 2009-07-20
Cannot offer help, though there's a link in this week's fridge-newsletter for a Nvidea troubleshooting wiki.  Issue #150 >> Tutorial of the week ( I think).

---

