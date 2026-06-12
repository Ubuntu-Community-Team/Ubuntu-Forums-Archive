---
title: "zenith zds versa sx (trident cyber 9388 rev 211)"
date: 2009-12-15
forum: Hardware
---

### Post by hjele on 2009-12-15
in case that some other person still ownes a old notebook (1996) like me and uses the karmic koala (which still works fine) you find here a working xorg.conf for the vga chip trident cyber 9388 (rev 211).

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
        Load  "extmod"
        Load  "record"
        Load  "dri2"
        Load  "dri"
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
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync 31.5-48.5
        VertRefresh 40-70
        #modeline     "640x480@60"
        #modeline     "800x600@60"
        modeline     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"               # [<str>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "PciRetry"                  # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SetMClk"                   # <freq>
        #Option     "MUXThreshold"              # <i>
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "Rotate"                    # [<str>]
        #Option     "VideoKey"                  # <i>
        #Option     "NoMMIO"                    # [<bool>]
        #Option     "NoPciBurst"                # [<bool>]
        #Option     "MMIOonly"                  # [<bool>]
        #Option     "CyberShadow"               # [<bool>]
        #Option     "CyberShadow"               # [<bool>]
        #Option     "CyberStretch"              # [<bool>]
        #Option     "XvHsync"                   # <i>
        #Option     "XvVsync"                   # <i>
        #Option     "XvBskew"                   # <i>
        #Option     "XvRskew"                   # <i>
        #Option     "FpDelay"                   # <i>
        #Option     "Display1400"               # [<bool>]
        #Option     "Display"                   # [<str>]
        #Option     "GammaBrightness"           # [<str>]
        #Option     "TVChipset"                 # [<str>]
        #Option     "TVSignal"                  # <i>
        Identifier  "Card0"
        Driver      "trident"
        VendorName  "Trident Microsystems"
        BoardName   "Cyber 9388"
        BusID       "PCI:0:2:0"
        VideoRam 4096
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        Defaultdepth 8
        SubSection "Display"
                Viewport   0 0
                Depth     1
                Modes      "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
                Modes      "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
                Modes      "1024x768@60" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
                Modes      "1024x768@60" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes      "1024x768@60" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

---

