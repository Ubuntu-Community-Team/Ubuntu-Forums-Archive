---
title: "Samsung 245T Monitor?"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by dark_phantom on 2008-01-08
Has anyone been able to setup this 24" widescreen monitor successfully?  I can't seem to make it work, I was able to add it via the .inf file from the included cd from samsung.  But I still can't get it to work, I can see it on the xorg.conf file.  I'm not at my home pc right now, but any help would be appreciated?

TIA

---

### Post by dark_phantom on 2008-01-08
bump

---

### Post by Yellow Pasque on 2008-01-08
Hi. I'm confused. How did you use an .inf file on Linux?

Also, post your xorg.conf file and try and elaborate on what's wrong with your monitor.

---

### Post by dark_phantom on 2008-01-08
I remember I did something similar with my laptop's internal wireless card, where all I need was the .inf and .exe files to configure it.  I basically added via the "screen and graphics" window and it recognized it, but it won't display on the actual monitor.  I saw something on the logs yesterday as well regarding the display.  The funny thing is that in the xorg file it doesn't contain an entry for my dell 1503fp monitor, which is the one I'm using right now.

```
Section "Files"
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "nVidia Corporation G80 [GeForce 8600 GT]"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Samsung"
        Modelname       "SyncMaster 245T(Digital)"
        Horizsync       30-81
        Vertrefresh     56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8600 GT]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1920    1200
                Modes           "1280x768@60"   "1280x720@60"   "800x600@60"   "1280x800@75"    "800x600@75"    "1280x768@75"   "800x600@72"    "1280x800@60"  "800x600@56"     "1440x900@75"   "1440x900@60"   "1600x1024@60"  "1680x1050@60" "1920x1200@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by Yellow Pasque on 2008-01-08
The only other thing I know to do is look in the /var/log/Xorg.0.log file after you boot with the monitor and see if that gives any hints.

> I remember I did something similar with my laptop's internal wireless card, where all I need was the .inf and .exe files to configure it
There's a special program called ndiswrapper that allows the use of Windows wireless drivers, but generally, .inf files aren't going to work for Linux, so get out of that habit.

---

### Post by dark_phantom on 2008-01-08
> **Temüjin said:**
> The only other thing I know to do is look in the /var/log/Xorg.0.log file after you boot with the monitor and see if that gives any hints.

Part of the Xorg.0.log file:
```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8600 GT (G84) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.51.00.07
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600 GT at PCI:1:0:0:
(--) NVIDIA(0):     DELL 1503FP (CRT-0)
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): DELL 1503FP (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x768@60"; removing.
(WW) NVIDIA(0): No valid modes for "1280x800@75"; removing.
(WW) NVIDIA(0): No valid modes for "1280x768@75"; removing.
(WW) NVIDIA(0): No valid modes for "1280x800@60"; removing.
(WW) NVIDIA(0): No valid modes for "800x600@56"; removing.
(WW) NVIDIA(0): No valid modes for "1440x900@75"; removing.
(WW) NVIDIA(0): No valid modes for "1440x900@60"; removing.
(WW) NVIDIA(0): No valid modes for "1600x1024@60"; removing.
(WW) NVIDIA(0): No valid modes for "1680x1050@60"; removing.
(WW) NVIDIA(0): No valid modes for "1920x1200@60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x720@60"
(II) NVIDIA(0):     "800x600@60"
(II) NVIDIA(0):     "800x600@75"
(II) NVIDIA(0):     "800x600@72"
(**) NVIDIA(0): Virtual screen size configured to be 1920 x 1200
(--) NVIDIA(0): DPI set to (108, 83); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp

```

In the screen models there's only Syncmaster 240t, 241mp, and 243t.  But when I imported the .inf file it added the Syncmaster 245T.
> 
There's a special program called ndiswrapper that allows the use of Windows wireless drivers, but generally, .inf files aren't going to work for Linux, so get out of that habit.
Good to know, thanks.

---

### Post by Yellow Pasque on 2008-01-08
You should probably removet the .inf as I think it might be causing problems. Just use a generic monitor setting.

---

