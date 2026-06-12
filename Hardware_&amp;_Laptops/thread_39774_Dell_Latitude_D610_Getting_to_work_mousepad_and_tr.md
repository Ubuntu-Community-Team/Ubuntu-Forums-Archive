---
title: "Dell Latitude D610: Getting to work mousepad and trackpoint"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by Matt05 on 2005-06-06
Hi,

I'm running kubuntu 5.04 on a Dell D610 notebook. It only runs sufficiently stable using the 2.6.12-1 kernel image from breezy, so I have this kernel running (with kernel options: "pci=bios idle=halt").

I have trackpoint and mousepad on the notebook and want to use both. I managed to get them to work (see xorg.conf below) BUT: as soon as I start a non-kde (e.g. gnome) application the trackpoint stops to work. It just sits there and does nothing. Same with the corresponding mouse buttons. Since konqueror crashes quite often I usually resort to firefox for web browsing and this is when the error shows up.

Has anybody an explanation for this behavior? Or even a fix?

Thanks in advance,

Matthias


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
        Option          "XkbLayout"     "de"
        Option          "XkbOptions"    "nodeadkeys"
EndSection

Section "InputDevice"
        Identifier      "Touchpad"
        Driver          "synaptics"
        #Option         "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "IMPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
Driver          "ati"
        #BusID          "PCI:1:0:0"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        #HorizSync 75.0
        #VertRefresh 60.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        ##InputDevice   "Configured Mouse"
        #InputDevice    "Synaptics Touchpad"
        InputDevice     "Touchpad"
        #InputDevice     "Trackpoint"
        #InputDevice     "USB Mouse" "SendCoreEvents"
EndSection

#Section "DRI"
#       Mode    0666
#EndSection

```

---

### Post by antwerx on 2005-06-20
Hello - Can you boot and run the Live CD version of Ubuntu and Kubuntu with full Trackpoint and Touchpad support?

---

### Post by bugmenot on 2005-08-20
There are some problem with the alps touchpad code in the kernel, you may need to apply a patch to fix this. The following site has some more info: [http://home.comcast.net/~canez/d610](http://home.comcast.net/~canez/d610)

In particular, look at the alps_touchpad_fixes patch.

---

