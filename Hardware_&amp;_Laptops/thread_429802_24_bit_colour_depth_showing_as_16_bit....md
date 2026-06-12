---
title: "24 bit colour depth showing as 16 bit..."
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by Dakiraun on 2007-05-01
This is occurring on a Dell Precision M65 laptop, which uses a nVidia Q-FX 350 GPU.  The nVidia Xorg driver is installed, and I manually edited xorg.conf to set the default to 24 (it was at 16 for some reason), but after restarting X (as well as rebooting) the video mode remains 16 bit, though the xorg.conf is set to 24.  Is there a way to troubleshoot this or force it to use the correct colour depth?

---

### Post by taurus on 2007-05-01
Can you post your /etc/X11/xorg.conf?

```
cat /etc/X11/xorg.conf
```

---

### Post by Dakiraun on 2007-05-01
Aye, here it is (less top commentary):

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
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
        Option          "XkbLayout"     "us"
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
        Option          "MinSpeed"              "0.18"
        Option          "MaxSpeed"              "0.36"
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
        Identifier      "nVidia Corporation Quadro FX 350M"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation Quadro FX 350M"
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

### Post by Dakiraun on 2007-05-01
A brief update: I seem to have it working, but it was a strange path.  I installed the nVidia restricted drivers using Synaptics, and that actually caused more problems than it helped.  For some reason it would only launch X-windows manually at that point.  Since it was a fresh install (and rather than just resetting xorg to defaults), I wanted to try from a clean slate so did a reinstall of Ubuntu.  Again it didn't get the modes right.  This time I just enabled the restricted driver using the restricted driver tool, and it pulled down the same files I did myself before, only this time, it seemed to do the trick after a reboot.  Not quite sure what was different but it obviously works better by using the Restricted Drivers app.  Anyway, it's working as it should be now.

So, long story short: Precision M65 users; go to the Restricted Drivers Manager (System > Administration > Restricted Drivers Manager), and enable the Nvidia driver.  It will download what it needs and prompt you to reboot.  :)

---

