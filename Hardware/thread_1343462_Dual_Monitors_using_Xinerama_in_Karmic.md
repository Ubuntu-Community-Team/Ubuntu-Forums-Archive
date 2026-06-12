---
title: "Dual Monitors using Xinerama in Karmic"
date: 2009-12-01
forum: Hardware
---

### Post by gnat79 on 2009-12-01
Hi, I have an r128 Rage ATI card and a GeForce4 MX 4000 nVidia card. I want to use these two cards with two FP monitors that are of the same size, etc.

I've had this working in the past, but on upgrading (downgrading?) to Karmic it only uses the primary (nv) card. I haven't had any luck getting things to work. Here is my config file. I'd be very appreciative for any help. (hope my attachment works)

Screw it... I'll just post the whole thing in text.
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
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
#       Load  "dri2"
#       Load  "dri"
        Load  "glx"
        Load  "record"
        Load  "extmod"
        Load  "dbe"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        #DisplaySize      380   300     # mm
        Identifier   "Monitor0"
        VendorName   "AOP"
        ModelName    "F90JS"
        HorizSync    30.0 - 83.0
        VertRefresh  50.0 - 76.0
        Option      "DPMS"
EndSection
Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "ViewSonic"
        ModelName    "Q9-2 Series"
        HorizSync    30.0 - 80.0
        VertRefresh  55.0 - 75.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "HWcursor"                  # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "UseFBDev"                  # [<bool>]
        #Option     "Rotate"                    # [<str>]
        #Option     "VideoKey"                  # <i>
        #Option     "FlatPanel"                 # [<bool>]
        #Option     "FPDither"                  # [<bool>]
        #Option     "CrtcNumber"                # <i>
        #Option     "FPScale"                   # [<bool>]
        #Option     "FPTweak"                   # <i>
        #Option     "DualHead"                  # [<bool>]
        Identifier  "Card0"
        Driver      "nv"
        VendorName  "nVidia Corporation"
        BoardName   "NV18 [GeForce4 MX 4000]"
        BusID       "PCI:2:0:0"
EndSection
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "Dac8Bit"                   # [<bool>]
        #Option     "DMAForXv"                  # [<bool>]
        #Option     "ForcePCIMode"              # [<bool>]
        #Option     "CCEPIOMode"                # [<bool>]
        #Option     "CCENoSecurity"             # [<bool>]
        #Option     "CCEusecTimeout"            # <i>
        #Option     "AGPMode"                   # <i>
        #Option     "AGPSize"                   # <i>
        #Option     "RingSize"                  # <i>
        #Option     "BufferSize"                # <i>
        #Option     "EnablePageFlip"            # [<bool>]
        #Option     "Display"                   # <str>
        #Option     "PanelWidth"                # <i>
        #Option     "PanelHeight"               # <i>
        #Option     "ProgramFPRegs"             # [<bool>]
        #Option     "UseFBDev"                  # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "ShowCache"                 # [<bool>]
        #Option     "VGAAccess"                 # [<bool>]
        Identifier  "Card1"
        Driver      "r128"
        VendorName  "ATI Technologies Inc"
        BoardName   "Rage 128 PP/PRO TMDS [Xpert 128]"
        BusID       "PCI:1:6:0"
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
Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
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

Section "ServerFlags"
    Option         "Xinerama" "true"
    Option         "DontZap" "false"
EndSection
```

---

