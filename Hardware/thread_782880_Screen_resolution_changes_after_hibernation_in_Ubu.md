---
title: "Screen resolution changes after hibernation in Ubuntu 8.04"
date: 2008-05-05
forum: Hardware
---

### Post by smatric on 2008-05-05
Hello,

After upgrading to Ubuntu 8.04 there appeared three problems:
- sudo returns: "could not resolve host name"
- HDD is being killed by too many load cycles
- screen resolution changes after hibernation

I've managed to resolve first and second problem, but third remains. I would be thankful if someone could help me. Here are details:

Every time I load system from scratch screen resolution is set up properly (1280x800), but after hibernation it changes into smaller one and the previous resolution is being simulated (need to move mouse to see whole desktop). Restarting X server doesn't help. I need to boot up system again to have the proper resolution.

My computer:
Linux 2.6.24-16-generic i686 GNU/Linux
Fujitsu Siemens AMILO Pi 1505

/etc/X11/xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
Section "Files"
        # path to defoma fonts
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/100dpi:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/usr/local/share/fonts"
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
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pl"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by smatric on 2008-05-18
I've found the way to fix this problem. I've removed following files from /etc/acpi/resume.d:

13-855-resolution-set.sh
13-915-resolution-set.sh
49-855-resolution-set.sh
49-915-resolution-set.sh

---

### Post by tsr on 2008-05-19
Hi,

I got a similar problem, but the proposed solution doesn't work for me.

If I reboot the screen uses a narrower resolution and leaves a black unused area to the right (I assume it's the difference between 1024 ans 1280).

The only way I managed to get my wanted resolution (1280x768) back is to re-install 915resolution and reboot again.

Any hints appriciated? (oh and ofc this is new in Hardy, hibernate worked flawlessly in both 7.04 and 7.10)
/tsr

---

