---
title: "Radeon M10 : Trying to set up dual monitors"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by frank05 on 2005-08-10
I've been trying to set up my laptop graphics chipset to drive my laptop flat panel and LG 795FT as two seperate x displays (i.e. not a stretched desktop). I installed the standard **fglrx drivers** provided for ubuntu with apt-get. My problem is when I use both monitors, only the LCD screen works. The CRT refresh rate is always set too low at 42Hz. It needs to be between 50 and 160 (which is what I specified!). Does anybody know how to fix this? Thanks,

My xorg.conf follows:
```

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

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
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "device0" # ATI Radeon Mobility M10 internal
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
#       Option "DesktopSetup"               "0x00000200" # stretch desktop
        Option "DesktopSetup"               "0x00000000" # two screens?
        Option "MonitorLayout"              "LVDS, CRT"
        Option "HSync2"                     "30-96"
        Option "VRefresh2"                  "50-160"
        Screen  0
EndSection

Section "Device"
        Identifier      "device1" # ATI Radeon Mobility M10 D-Sub
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen  1
EndSection

Section "Monitor"
        Identifier      "monitor0" # integrated LCD flatpanel
        Option          "DPMS"
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
        Identifier      "monitor1" # LG Flatron 795FT
        HorizSync       30-96
        VertRefresh     50-160
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "device0"
        Monitor         "monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x960" "1280x768" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "device1"
        Monitor         "monitor1"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x960" "1280x768" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "multi"
        Screen          "screen0"
        Screen          "screen1" RightOf "screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

fglrxinfo:

```


display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)


display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)


```

---

