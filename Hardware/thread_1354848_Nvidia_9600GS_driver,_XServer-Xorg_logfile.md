---
title: "Nvidia 9600GS driver, XServer-Xorg logfile"
date: 2009-12-14
forum: Hardware
---

### Post by pjf.weeks on 2009-12-14
Having ridiculously difficult time installing drivers for 9600GS in ubuntu 8.04. Drivers will install but resolution is stuck at 640x480, quality is terrible,  and lists my monitor as SyncMaster CRT (is actually SyncMaster 2043 LCD with 1600x900 max). EnvyNG doesn't work, tried a half dozen drivers from NVidia site, don't work. Tried creating modelines in XServer-Xorg AND in terminal, doesn't work. Here's logfile from XServer-Xorg:


X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Grosvenor-desktop 2.6.24-24-generic #1 SMP Fri Sep 18 16:49:39 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Dec 14 11:17:44 2009
(++) Using config file: "test_xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
    Using the first keyboard device.
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 2.0
    X.Org XInput driver : 2.0
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(--) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0754 card 1462,7374 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,075d card 1462,7374 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0752 card 1462,7374 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,0751 card 1462,7374 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,0753 card 1462,7374 rev a2 class 0b,40,00 hdr 80
(II) PCI: 00:01:4: chip 10de,0568 card 1462,7374 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,077b card 1462,7374 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,077c card 1462,7374 rev a1 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,077d card 1462,7374 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:04:1: chip 10de,077e card 1462,7374 rev a1 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0759 card f462,7374 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0774 card 1462,7374 rev a1 class 04,03,00 hdr 00
(II) PCI: 00:08:0: chip 10de,075a card 0000,0000 rev a1 class 06,04,01 hdr 01
(II) PCI: 00:09:0: chip 10de,0ad0 card 1462,7374 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0a:0: chip 10de,0760 card 1462,7374 rev a2 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 10de,0778 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:11:0: chip 10de,0779 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 10de,077a card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:14:0: chip 10de,077a card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1200 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1201 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1202 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1203 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:4: chip 1022,1204 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:07:0: chip 1131,7130 card 1a7f,2008 rev 01 class 04,80,00 hdr 00
(II) PCI: 01:09:0: chip 1106,3044 card 1462,7374 rev c0 class 0c,00,10 hdr 00
(II) PCI: 03:00:0: chip 10de,0623 card 174b,9420 rev a1 class 03,00,00 hdr 00
(II) PCI: 04:00:0: chip 197b,2363 card 1462,7374 rev 03 class 01,06,01 hdr 80
(II) PCI: 04:00:1: chip 197b,2363 card 1462,7374 rev 03 class 01,01,85 hdr 00
(II) PCI: End of PCI scan
(--) PCI:*(3:0:0) nVidia Corporation unknown chipset (0x0623) rev 161, Mem @ 0xfc000000/24, 0xd0000000/28, 0xfa000000/25, I/O @ 0xdc00/7, BIOS @ 0xfde80000/19
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.12  Thu Jul 17 18:36:35 PDT 2008
(II) Loading extension GLX
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 0.1.1
    ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  173.14.12  Thu Jul 17 18:15:54 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:1:3) found
(--) Chipset NVIDIA GPU found
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9600 GS (G94) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 786432 kBytes
(--) NVIDIA(0): VideoBIOS: 62.94.21.00.30
(II) NVIDIA(0): Detected PCI Express Link width: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9600 GS at PCI:3:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
(--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "640x480@60"; removing.
(WW) NVIDIA(0): No valid modes for "1600x900@60"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(**) NVIDIA(0): Virtual screen size configured to be 640 x 480
(--) NVIDIA(0): DPI set to (36, 48); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.

---

### Post by jocko on 2009-12-14
Don't worry about the "CRT-1". That simply means your monitor is connected through a vga port and has nothing to do with what type of monitor it is.
You'll probably need to post your /etc/X11/xorg.conf, as the log file doesn't really help on its own.
And try to put the text you pasted in a code box. Put [noparse]```
 before the pasted text and 
```[/noparse] after it. That way it will be a lot easier to read this thread.

---

### Post by pjf.weeks on 2009-12-14
Thanks for the advice!

```
# xorg.conf (X.Org X Window System server configuration file)
# 
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
# 
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
# sudo dpkg-reconfigure -phigh xserver-xorg
#
# File edited by xorg-edit v07.08.11 at Mon Dec 14 11:14:53 2009

Section "Module"
    Load "glx"
    Load "GLcore"
    Load "v4l"
EndSection

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
EndSection

Section "Device"
    # Boardname "NVIDIA GeForce (fbdev)"
    # Vendorname "NVIDIA"
    Identifier "Configured Video Device"
    Driver "nvidia"
    BusID "PCI:3:0:0"
    Screen 0
EndSection

Section "Monitor"
    # Vendorname "Plug 'n' Play"
    # Modelname "Plug 'n' Play"
    Identifier "Configured Monitor"
    Gamma 1.0
    Modeline "1600x900_60.00" 118.25 1600 1696 1856 2112 900 903 908 934 -hsync +vsync
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Configured Video Device"
    Monitor "Configured Monitor"
    DefaultDepth 24
    Option "AddARGBGLXVisuals" "True"
    SubSection "Display"
        Depth 24
        Virtual 640 480
        Modes "640x480@60" "1600x900@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier "Default Layout"
    Screen "Default Screen"
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

---

### Post by jocko on 2009-12-14
> **pjf.weeks said:**
> ```
...
Section "Device"
    # Boardname "NVIDIA GeForce (fbdev)"
    # Vendorname "NVIDIA"
    Identifier "Configured Video Device"
    Driver "nvidia"
    BusID "PCI:3:0:0"
    Screen 0
EndSection

Section "Monitor"
    # Vendorname "Plug 'n' Play"
    # Modelname "Plug 'n' Play"
    Identifier "Configured Monitor"
    Gamma 1.0
    Modeline "1600x900_60.00" 118.25 1600 1696 1856 2112 900 903 908 934 -hsync +vsync
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Configured Video Device"
    Monitor "Configured Monitor"
    DefaultDepth 24
    Option "AddARGBGLXVisuals" "True"
    SubSection "Display"
        Depth 24
[COLOR=Red]        Virtual 640 480
        Modes "640x480@60" "1600x900@60"[/COLOR]
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier "Default Layout"
    Screen "Default Screen"
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```
Edit your xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```Remove or comment out the "[COLOR=Red]Virtual 640 480[/COLOR]" line. That line limits the combined resolution of all outputs to 640x480, which is the cause of your problem. Also remove [COLOR=Red]"640x480@60"[/COLOR] from the "Modes" line, as this option makes 640x480 default, even if there are other modes available.
If that still doesn't help, delete your /etc/X11/xorg.conf and generate a new one with:
```
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```

---

### Post by pjf.weeks on 2009-12-14
You are a god amongst men. It worked! I've been trying to fix that all week! thankyouthankyouthankyou!

---

### Post by jocko on 2009-12-14
You're very welcome!

---

