---
title: "Problems with fonts rendering under ubuntu feisty ?!"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by 6sic6 on 2007-08-05
hello
my laptop mount an ATI mobility radeon 9700 , my screen resolution is
1280x800
I trying to set the correct rendering of the fonts under ubuntu feisty
```

$ xdpyinfo | grep -A1 dimen

```
gives me

dimensions:    1280x800 pixels (339x212 millimeters)
  resolution:    96x96 dots per inch

now I try to force the millimeters in the xorg.conf and put something
like this
```

...
Section "Monitor"
        Identifier      "Generic Monitor"
        #Option          "DPMS"
        DisplaySize     344 215
        HorizSync       28-51
        VertRefresh     43-60
EndSection
....
Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon
9600 M10]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "IgnoreEDID" "true"
EndSection
....

```
I set the DisplaySize on 344 215 (this is the correct size for my
resolution of 1280x800)
I set also Option "IgnoreEDID" "true" under the Device section

i reboot my laptop but
$ xdpyinfo | grep -A1 dimen
gives me one more time the same  millimeters (339x212 millimeters)

It doesn't take the DisplaySize of 344 215 I set under my xorg.conf

Someone knows what's the problem?

here is my xorg.conf
```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/
TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"    "xorg"
        Option          "XkbModel"    "pc105"
        Option          "XkbLayout"   "it"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"              "/dev/input/mice"
        Option          "Protocol"            "ImPS/2"
        Option          "ZAxisMapping"                "4 5"
        Option          "Emulate3Buttons"     "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"      "/dev/input/wacom"
        Option          "Type"                "stylus"
        Option          "ForceDevice" "ISDV4"               # Tablet
PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"      "/dev/input/wacom"
        Option          "Type"                "eraser"
        Option          "ForceDevice" "ISDV4"               # Tablet
PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"      "/dev/input/wacom"
        Option          "Type"                "cursor"
        Option          "ForceDevice" "ISDV4"               # Tablet
PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon
9600 M10]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode"       "8"
        Option          "AccelMethod"   "XAA"
        Option          "ColorTiling"   "on
        Option          "IgnoreEDID"  "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
       # Option          "DPMS"
        DisplaySize     344 215
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 [Mobility Radeon
9600 M10]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800" "1024x768" "800x600"
"640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800" "1024x768" "800x600"
"640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800" "1024x768" "800x600"
"640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800" "1024x768" "800x600"
"640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800" "1024x768" "800x600"
"640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600"
"640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"      "SendCoreEvents"
        InputDevice     "cursor"      "SendCoreEvents"
        InputDevice     "eraser"      "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

