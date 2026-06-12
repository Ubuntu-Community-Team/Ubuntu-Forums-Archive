---
title: "wacom pen stoped working"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by the-65 on 2006-07-08
Hi everyone,

i have a strange problem with the wacom stylus pen on my HP TC1100. It worked well with breezy and even worked after update to dapper, but 2 weeks ago it stopped working. Sorry can't say exactly when it stopped, so i can't say exactly if i changed anything before.

The situation is:
The script /etc/init.d/wacom-tools detects the pen on /dev/ttyS4 and creates a link as /dev/wacom
wacdump -f c100 /dev/wacom shows the usal screens and detects motions of the pen
Everything seems fine but:
X doeesn't load the drivers and doesn't configure the coresponding input devices. The pen doesn't work under X at all.

Here is my xorg.conf
```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
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
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"        "/dev/ttyS4"
    Option        "InputFashion" "Tablet"
    Option        "ForceDevice"    "ISDV4"
    Option        "Name" "GRAPHIRE / INTUOS (SERIAL)"
    Option        "SendCoreEvents" "on"
    Option        "Type"          "cursor"
    Option        "Mode"          "absolute"
    Option        "Vendor" "WACOM"
    Option        "Speed"         "3.0"
    Option        "Threshold"     "1"
    Option        "Tilt"          "on"
    Option        "Button2"     "3"
    Option    "DebugLevel"    "10"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"        "/dev/ttyS4"
    Option        "Type"          "stylus"
    Option        "InputFashion" "Pen"
    Option        "SendCoreEvents" "on"
    Option        "Name"          "GRAPHIRE / INTUOS Stylus (SERIAL)"
    Option        "ForceDevice"    "ISDV4"
    Option        "Mode"          "absolute"
    Option        "Vendor" "WACOM"
    Option        "Tilt"          "on"
    Option        "TiltInvert"    "on"
    Option        "Threshold"     "1"
    Option           "Button2"  "3"
    Option    "DebugLevel"    "10"
EndSection

Section "InputDevice"
 Driver       "wacom"
 Identifier   "eraser"
 Option       "Device" "/dev/ttyS4"
 Option       "InputFashion" "Eraser"
 Option       "Name" "GRAPHIRE / INTUOS Eraser (SERIAL)"
 Option       "Type" "eraser"
 Option       "Mode" "absolute"
 Option       "Vendor" "WACOM"
 Option       "ForceDevice" "ISDV4"
 Option        "SendCoreEvents" "on"
EndSection


Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Standardbildschirm"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
        Monitor         "Standardbildschirm"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "cursor"    "SendCoreEvents"
        InputDevice     "stylus"    "SendCoreEvents"
        InputDevice     "eraser"    "SendCoreEvents"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

and here is an excerpt from the Xorg log file

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux pionier 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  8 18:52:42 2006
(==) Using config file: "/etc/X11/xorg.conf"
(++) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Standardbildschirm"
(**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(WW) The core pointer device wasn't specified explicitly in the layout.
        Using the first core pointer device.
(WW) The core keyboard device wasn't specified explicitly in the layout.
        Using the first core keyboard device.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fon
ts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"


```

As you can see, X only detects the mouse and keyboard as input devices not the stylus, cursor or eraser. Next strange thing is the warning about the missing core pointer and core keyboard device, because i give the CoreMouse and CoreKeyboard Options for the keyboard and the mouse in the xorg.conf file. I'm sure X uses this xorg.conf, because if i add some syntax errors, X won't start anymore.

Anyone got an idea? After three evenings of work, I'm completly clueless now.

tia
the

Update:
Btw.: The hardware isn't broken, I have an older version of ubuntu (breezy) installed and if i boot this version the pen works fine, even under X.

---

### Post by the-65 on 2006-07-21
I did a reinstall and the problem is away. I don't have a clue what was wrong with the old installation

---

