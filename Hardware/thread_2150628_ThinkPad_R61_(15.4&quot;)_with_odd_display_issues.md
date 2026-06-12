---
title: "ThinkPad R61 (15.4&quot;) with odd display issues"
date: 2013-06-01
forum: Hardware
---

### Post by 64bitiso on 2013-06-01
[COLOR=#ff0000][B]<<__SOLVED!__>> 

The fault was that the WSXGA+ screen I installed was an old one, and the CCFL was drawing too much current and tripping out.[/B][/COLOR]

Hi there! :)

I have a Lenovo ThinkPad R61, 15.4" screen, sub-model 8930-A41. This machine came to me as nearly new, with the default 1280x800 LCD, but I have just installed an official Lenovo WSXGA+ (1680x1050) LCD:

[http://www.ebay.co.uk/itm/151032798468?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649](http://www.ebay.co.uk/itm/151032798468?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649)

LG type: [COLOR=#333333][FONT=Trebuchet][B]LP154W02 (TL)(10) 




[/B][/FONT][/COLOR]Also, I had to put a new, higher res LCD cable in, FRU number: "93P4380" (the original was FRU "93P4446" - didn't support WSXGA+). I now have some odd issues:
[COLOR=#333333][FONT=Trebuchet][B]
[SIZE=2]#1 The backlight turns itself off every now and again, with no rhyme no reason :S
[/SIZE]
[SIZE=2]#2 There is some video tearing - I am running Linux Mint 15 x64 Cinnamon


Here is the result from "dmesg | grep backlight":

[/SIZE][/B][/FONT][/COLOR]```
dmesg | grep backlight[   21.952373] thinkpad_acpi: ACPI backlight control delay disabled
[   21.953342] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   22.809507] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[ 1963.711919] thinkpad_acpi: ACPI backlight control delay disabled
[ 1963.882097] video LNXVIDEO:00: >Restoring backlight state
[ 3033.157321] thinkpad_acpi: ACPI backlight control delay disabled
[ 3033.335000] video LNXVIDEO:00: >Restoring backlight state
```
[COLOR=#333333][FONT=Trebuchet][B][SIZE=2]

Here is the result from "cvt 1680 1050":

[/SIZE][/B][/FONT][/COLOR]```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz[COLOR=#333333][FONT=Trebuchet][B][SIZE=2]
[/SIZE][/B][/FONT][/COLOR]
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```[COLOR=#333333][FONT=Trebuchet][B][SIZE=2]




Here is the result from "xrandr":

[/SIZE][/B][/FONT][/COLOR]```
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      60.0*+   60.0     59.9     50.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

TV1 disconnected (normal left inverted right x axis y axis)
```[COLOR=#333333][FONT=Trebuchet][B][SIZE=2]




I have attached the Xorg.0.log for you to inspect:

[/SIZE][/B][/FONT][/COLOR]```
[    24.509] X.Org X Server 1.13.0
Release Date: 2012-09-05
[    24.509] X Protocol Version 11, Revision 0
[    24.509] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
[    24.509] Current Operating System: Linux matt-ThinkPad-R61 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[    24.509] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=bad5b480-51e8-4340-87aa-527130b2c9ee ro quiet splash vt.handoff=7
[    24.509] Build Date: 08 October 2012  03:34:01PM
[    24.509] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    24.509] Current version of pixman: 0.26.0
[    24.509]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.509] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.509] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun  1 20:47:52 2013
[    24.533] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.533] (==) No Layout section.  Using the first Screen section.
[    24.533] (==) No screen section available. Using defaults.
[    24.533] (**) |-->Screen "Default Screen Section" (0)
[    24.533] (**) |   |-->Monitor "<default monitor>"
[    24.533] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.533] (==) Automatically adding devices
[    24.533] (==) Automatically enabling devices
[    24.533] (==) Automatically adding GPU devices
[    24.533] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.533]     Entry deleted from font path.
[    24.533] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.533]     Entry deleted from font path.
[    24.533] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.533]     Entry deleted from font path.
[    24.533] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.533]     Entry deleted from font path.
[    24.533] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.533]     Entry deleted from font path.
[    24.533] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    24.533]     Entry deleted from font path.
[    24.533] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    24.533] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.533] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.533] (II) Loader magic: 0x7f0bd323dc40
[    24.533] (II) Module ABI versions:
[    24.533]     X.Org ANSI C Emulation: 0.4
[    24.533]     X.Org Video Driver: 13.0
[    24.533]     X.Org XInput driver : 18.0
[    24.533]     X.Org Server Extension : 7.0
[    24.534] (II) config/udev: Adding drm device (/dev/dri/card0)
[    24.536] (--) PCI:*(0:0:2:0) 8086:2a02:17aa:20b5 rev 12, Mem @ 0xf8000000/1048576, 0xe0000000/268435456, I/O @ 0x00001800/8
[    24.536] (--) PCI: (0:0:2:1) 8086:2a03:17aa:20b5 rev 12, Mem @ 0xf8100000/1048576
[    24.536] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.536] Initializing built-in extension Generic Event Extension
[    24.536] Initializing built-in extension SHAPE
[    24.536] Initializing built-in extension MIT-SHM
[    24.536] Initializing built-in extension XInputExtension
[    24.536] Initializing built-in extension XTEST
[    24.536] Initializing built-in extension BIG-REQUESTS
[    24.536] Initializing built-in extension SYNC
[    24.536] Initializing built-in extension XKEYBOARD
[    24.536] Initializing built-in extension XC-MISC
[    24.536] Initializing built-in extension SECURITY
[    24.536] Initializing built-in extension XINERAMA
[    24.536] Initializing built-in extension XFIXES
[    24.536] Initializing built-in extension RENDER
[    24.536] Initializing built-in extension RANDR
[    24.536] Initializing built-in extension COMPOSITE
[    24.536] Initializing built-in extension DAMAGE
[    24.536] Initializing built-in extension MIT-SCREEN-SAVER
[    24.536] Initializing built-in extension DOUBLE-BUFFER
[    24.536] Initializing built-in extension RECORD
[    24.536] Initializing built-in extension DPMS
[    24.536] Initializing built-in extension X-Resource
[    24.536] Initializing built-in extension XVideo
[    24.536] Initializing built-in extension XVideo-MotionCompensation
[    24.536] Initializing built-in extension XFree86-VidModeExtension
[    24.536] Initializing built-in extension XFree86-DGA
[    24.536] Initializing built-in extension XFree86-DRI
[    24.536] Initializing built-in extension DRI2
[    24.536] (II) LoadModule: "glx"
[    24.703] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.703] (II) Module glx: vendor="X.Org Foundation"
[    24.703]     compiled for 1.13.0, module version = 1.0.0
[    24.703]     ABI class: X.Org Server Extension, version 7.0
[    24.703] (==) AIGLX enabled
[    24.703] Loading extension GLX
[    24.703] (==) Matched intel as autoconfigured driver 0
[    24.703] (==) Matched intel as autoconfigured driver 1
[    24.703] (==) Matched vesa as autoconfigured driver 2
[    24.703] (==) Matched modesetting as autoconfigured driver 3
[    24.703] (==) Matched fbdev as autoconfigured driver 4
[    24.703] (==) Assigned the driver to the xf86ConfigLayout
[    24.703] (II) LoadModule: "intel"
[    24.703] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.704] (II) Module intel: vendor="X.Org Foundation"
[    24.704]     compiled for 1.13.0, module version = 2.20.9
[    24.704]     Module class: X.Org Video Driver
[    24.704]     ABI class: X.Org Video Driver, version 13.0
[    24.704] (II) LoadModule: "vesa"
[    24.704] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.704] (II) Module vesa: vendor="X.Org Foundation"
[    24.704]     compiled for 1.12.99.902, module version = 2.3.2
[    24.704]     Module class: X.Org Video Driver
[    24.704]     ABI class: X.Org Video Driver, version 13.0
[    24.704] (II) LoadModule: "modesetting"
[    24.704] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    24.704] (II) Module modesetting: vendor="X.Org Foundation"
[    24.704]     compiled for 1.13.0, module version = 0.5.0
[    24.704]     Module class: X.Org Video Driver
[    24.704]     ABI class: X.Org Video Driver, version 13.0
[    24.704] (II) LoadModule: "fbdev"
[    24.705] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.705] (II) Module fbdev: vendor="X.Org Foundation"
[    24.705]     compiled for 1.12.99.902, module version = 0.4.3
[    24.705]     Module class: X.Org Video Driver
[    24.705]     ABI class: X.Org Video Driver, version 13.0
[    24.705] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    24.705] (II) VESA: driver for VESA chipsets: vesa
[    24.705] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    24.705] (II) FBDEV: driver for framebuffer: fbdev
[    24.705] (++) using VT number 8


[    24.710] (II) intel(0): using device path '/dev/dri/card0'
[    24.710] (WW) Falling back to old probe method for vesa
[    24.710] (WW) Falling back to old probe method for modesetting
[    24.710] (WW) Falling back to old probe method for fbdev
[    24.710] (II) Loading sub module "fbdevhw"
[    24.710] (II) LoadModule: "fbdevhw"
[    24.711] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.711] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.711]     compiled for 1.13.0, module version = 0.0.2
[    24.711]     ABI class: X.Org Video Driver, version 13.0
[    24.711] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.711] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.711] (==) intel(0): RGB weight 888
[    24.711] (==) intel(0): Default visual is TrueColor
[    24.711] (--) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    24.711] (**) intel(0): Relaxed fencing enabled
[    24.711] (**) intel(0): Wait on SwapBuffers? enabled
[    24.711] (**) intel(0): Triple buffering? enabled
[    24.711] (**) intel(0): Framebuffer tiled
[    24.711] (**) intel(0): Pixmaps tiled
[    24.711] (**) intel(0): 3D buffers tiled
[    24.711] (**) intel(0): SwapBuffers wait enabled
[    24.711] (==) intel(0): video overlay key set to 0x101fe
[    24.711] (II) intel(0): Output LVDS1 has no monitor section
[    24.711] (--) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    24.732] (II) intel(0): Output VGA1 has no monitor section
[    25.056] (II) intel(0): Output TV1 has no monitor section
[    25.056] (II) intel(0): EDID for output LVDS1
[    25.056] (II) intel(0): Manufacturer: IBM  Model: 2887  Serial#: 0
[    25.056] (II) intel(0): Year: 2005  Week: 0
[    25.056] (II) intel(0): EDID Version: 1.3
[    25.056] (II) intel(0): Digital Display Input
[    25.056] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    25.056] (II) intel(0): Gamma: 2.20
[    25.056] (II) intel(0): No DPMS capabilities specified
[    25.056] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.056] (II) intel(0): First detailed timing is preferred mode
[    25.056] (II) intel(0): redX: 0.596 redY: 0.347   greenX: 0.335 greenY: 0.543
[    25.056] (II) intel(0): blueX: 0.158 blueY: 0.143   whiteX: 0.313 whiteY: 0.329
[    25.056] (II) intel(0): Manufacturer's mask: 0
[    25.056] (II) intel(0): Supported detailed timing:
[    25.056] (II) intel(0): clock: 120.6 MHz   Image Size:  331 x 207 mm
[    25.056] (II) intel(0): h_active: 1680  h_sync: 1712  h_sync_end 1760 h_blank_end 1888 h_border: 0
[    25.056] (II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1065 v_border: 0
[    25.056] (II) intel(0): Supported detailed timing:
[    25.056] (II) intel(0): clock: 100.5 MHz   Image Size:  331 x 207 mm
[    25.056] (II) intel(0): h_active: 1680  h_sync: 1712  h_sync_end 1760 h_blank_end 1888 h_border: 0
[    25.056] (II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1065 v_border: 0
[    25.056] (II) intel(0): Unknown vendor-specific block f
[    25.056] (II) intel(0):  LP154W02-TL06
[    25.056] (II) intel(0): EDID (in hex):
[    25.056] (II) intel(0):     00ffffffffffff00244d872800000000
[    25.056] (II) intel(0):     000f0103802115780abca59858558b28
[    25.056] (II) intel(0):     24505400000001010101010101010101
[    25.056] (II) intel(0):     0101010101011c2f90d0601a0f402030
[    25.056] (II) intel(0):     13004bcf10000019452790d0601a0f40
[    25.056] (II) intel(0):     203013004bcf100000190000000f00b3
[    25.056] (II) intel(0):     0a32b30a28140100320c0000000000fe
[    25.056] (II) intel(0):     004c503135345730322d544c303600bf
[    25.056] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.056] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.056] (II) intel(0): Printing probed modes for output LVDS1
[    25.056] (II) intel(0): Modeline "1680x1050"x60.0  120.60  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (63.9 kHz eP)
[    25.056] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[    25.056] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[    25.056] (II) intel(0): Modeline "1680x1050"x50.0  100.53  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (53.2 kHz e)
[    25.056] (II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    25.056] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    25.056] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    25.056] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    25.056] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    25.057] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    25.057] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    25.057] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    25.057] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    25.057] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    25.057] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    25.057] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    25.072] (II) intel(0): EDID for output VGA1
[    25.360] (II) intel(0): EDID for output TV1
[    25.360] (II) intel(0): Output LVDS1 connected
[    25.360] (II) intel(0): Output VGA1 disconnected
[    25.360] (II) intel(0): Output TV1 disconnected
[    25.360] (II) intel(0): Using exact sizes for initial modes
[    25.360] (II) intel(0): Output LVDS1 using initial mode 1680x1050
[    25.360] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.360] (II) intel(0): Kernel page flipping support detected, enabling
[    25.360] (==) intel(0): DPI set to (96, 96)
[    25.360] (II) Loading sub module "fb"
[    25.360] (II) LoadModule: "fb"
[    25.360] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.360] (II) Module fb: vendor="X.Org Foundation"
[    25.360]     compiled for 1.13.0, module version = 1.0.0
[    25.360]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.360] (II) Loading sub module "dri2"
[    25.360] (II) LoadModule: "dri2"
[    25.360] (II) Module "dri2" already built-in
[    25.360] (II) UnloadModule: "vesa"
[    25.360] (II) Unloading vesa
[    25.360] (II) UnloadModule: "modesetting"
[    25.360] (II) Unloading modesetting
[    25.360] (II) UnloadModule: "fbdev"
[    25.360] (II) Unloading fbdev
[    25.360] (II) UnloadSubModule: "fbdevhw"
[    25.360] (II) Unloading fbdevhw
[    25.360] (==) Depth 24 pixmap format is 32 bpp
[    25.360] (II) intel(0): [DRI2] Setup complete
[    25.360] (II) intel(0): [DRI2]   DRI driver: i965
[    25.360] (II) intel(0): Allocated new frame buffer 1728x1050 stride 7168, tiled
[    25.370] (II) UXA(0): Driver registered support for the following operations:
[    25.371] (II)         solid
[    25.371] (II)         copy
[    25.371] (II)         composite (RENDER acceleration)
[    25.371] (II)         put_image
[    25.371] (II)         get_image
[    25.371] (==) intel(0): Backing store disabled
[    25.371] (==) intel(0): Silken mouse enabled
[    25.371] (II) intel(0): Initializing HW Cursor
[    25.371] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.373] (==) intel(0): DPMS enabled
[    25.373] (==) intel(0): Intel XvMC decoder enabled
[    25.373] (II) intel(0): Set up textured video
[    25.373] (II) intel(0): Set up overlay video
[    25.373] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    25.373] (II) intel(0): direct rendering: DRI2 Enabled
[    25.373] (==) intel(0): hotplug detection: "enabled"
[    25.404] (--) RandR disabled
[    25.413] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.413] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.413] (II) AIGLX: enabled GLX_ARB_create_context
[    25.413] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    25.413] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    25.413] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.413] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.413] (II) AIGLX: Loaded and initialized i965
[    25.413] (II) GLX: Initialized DRI2 GL provider for screen 0
[    25.413] (II) intel(0): Setting screen physical size to 444 x 277
[    25.420] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.423] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    25.423] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.423] (II) LoadModule: "evdev"
[    25.423] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.424] (II) Module evdev: vendor="X.Org Foundation"
[    25.424]     compiled for 1.13.0, module version = 2.7.3
[    25.424]     Module class: X.Org XInput Driver
[    25.424]     ABI class: X.Org XInput driver, version 18.0
[    25.424] (II) Using input driver 'evdev' for 'Power Button'
[    25.424] (**) Power Button: always reports core events
[    25.424] (**) evdev: Power Button: Device: "/dev/input/event2"
[    25.424] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.424] (--) evdev: Power Button: Found keys
[    25.424] (II) evdev: Power Button: Configuring as keyboard
[    25.424] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    25.424] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.424] (**) Option "xkb_rules" "evdev"
[    25.424] (**) Option "xkb_model" "pc105"
[    25.424] (**) Option "xkb_layout" "gb"
[    25.426] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    25.426] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    25.426] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.426] (II) Using input driver 'evdev' for 'Video Bus'
[    25.426] (**) Video Bus: always reports core events
[    25.426] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    25.426] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    25.426] (--) evdev: Video Bus: Found keys
[    25.426] (II) evdev: Video Bus: Configuring as keyboard
[    25.426] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    25.426] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    25.426] (**) Option "xkb_rules" "evdev"
[    25.426] (**) Option "xkb_model" "pc105"
[    25.426] (**) Option "xkb_layout" "gb"
[    25.427] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.427] (II) No input driver specified, ignoring this device.
[    25.427] (II) This device may have been added with another device file.
[    25.427] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    25.427] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.427] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.427] (**) Sleep Button: always reports core events
[    25.427] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    25.427] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    25.427] (--) evdev: Sleep Button: Found keys
[    25.427] (II) evdev: Sleep Button: Configuring as keyboard
[    25.427] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    25.427] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    25.427] (**) Option "xkb_rules" "evdev"
[    25.427] (**) Option "xkb_model" "pc105"
[    25.427] (**) Option "xkb_layout" "gb"
[    25.427] (II) config/udev: Adding drm device (/dev/dri/card0)
[    25.428] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    25.428] (II) No input driver specified, ignoring this device.
[    25.428] (II) This device may have been added with another device file.
[    25.428] (II) config/udev: Adding input device HDA Intel Dock Mic (/dev/input/event7)
[    25.428] (II) No input driver specified, ignoring this device.
[    25.428] (II) This device may have been added with another device file.
[    25.428] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[    25.428] (II) No input driver specified, ignoring this device.
[    25.428] (II) This device may have been added with another device file.
[    25.429] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.429] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.429] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.429] (**) AT Translated Set 2 keyboard: always reports core events
[    25.429] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.429] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    25.429] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    25.429] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    25.429] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.429] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    25.429] (**) Option "xkb_rules" "evdev"
[    25.429] (**) Option "xkb_model" "pc105"
[    25.429] (**) Option "xkb_layout" "gb"
[    25.429] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event10)
[    25.429] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.429] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    25.429] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    25.429] (II) LoadModule: "synaptics"
[    25.430] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.430] (II) Module synaptics: vendor="X.Org Foundation"
[    25.430]     compiled for 1.12.99.905, module version = 1.6.2
[    25.430]     Module class: X.Org XInput Driver
[    25.430]     ABI class: X.Org XInput driver, version 18.0
[    25.430] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    25.430] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    25.430] (**) Option "Device" "/dev/input/event10"
[    25.430] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023
[    25.430] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767
[    25.430] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    25.430] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    25.430] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    25.430] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    25.430] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    25.430] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    25.430] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    25.430] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[    25.430] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 10)
[    25.430] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.430] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: MaxSpeed is now 1.75
[    25.430] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: AccelFactor is now 0.156
[    25.431] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    25.431] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    25.431] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    25.431] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    25.431] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    25.431] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse1)
[    25.431] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    25.431] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event9)
[    25.431] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    25.431] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    25.431] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    25.431] (**) DualPoint Stick: always reports core events
[    25.431] (**) evdev: DualPoint Stick: Device: "/dev/input/event9"
[    25.431] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    25.431] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    25.431] (--) evdev: DualPoint Stick: Found relative axes
[    25.431] (--) evdev: DualPoint Stick: Found x and y relative axes
[    25.431] (II) evdev: DualPoint Stick: Configuring as mouse
[    25.431] (**) Option "Emulate3Buttons" "true"
[    25.431] (**) Option "EmulateWheel" "true"
[    25.431] (**) Option "EmulateWheelButton" "2"
[    25.431] (**) Option "YAxisMapping" "4 5"
[    25.431] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    25.431] (**) Option "XAxisMapping" "6 7"
[    25.431] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    25.431] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.431] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    25.431] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 11)
[    25.431] (II) evdev: DualPoint Stick: initialized for relative axes.
[    25.432] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    25.432] (**) DualPoint Stick: (accel) acceleration profile 0
[    25.432] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    25.432] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    25.432] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse0)
[    25.432] (II) No input driver specified, ignoring this device.
[    25.432] (II) This device may have been added with another device file.
[    25.434] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event4)
[    25.434] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    25.434] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    25.434] (**) ThinkPad Extra Buttons: always reports core events
[    25.434] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event4"
[    25.434] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[    25.434] (--) evdev: ThinkPad Extra Buttons: Found keys
[    25.434] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[    25.434] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input4/event4"
[    25.434] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 12)
[    25.434] (**) Option "xkb_rules" "evdev"
[    25.434] (**) Option "xkb_model" "pc105"
[    25.434] (**) Option "xkb_layout" "gb"
[    25.978] (II) intel(0): EDID vendor "IBM", prod id 10375
[    25.978] (II) intel(0): Printing DDC gathered Modelines:
[    25.978] (II) intel(0): Modeline "1680x1050"x0.0  120.60  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (63.9 kHz eP)
[    25.978] (II) intel(0): Modeline "1680x1050"x0.0  100.53  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (53.2 kHz e)
[    27.072] (II) intel(0): EDID vendor "IBM", prod id 10375
[    27.072] (II) intel(0): Printing DDC gathered Modelines:
[    27.072] (II) intel(0): Modeline "1680x1050"x0.0  120.60  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (63.9 kHz eP)
[    27.072] (II) intel(0): Modeline "1680x1050"x0.0  100.53  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (53.2 kHz e)
[    28.421] (II) XKB: reuse xkmfile /var/lib/xkb/server-7996F6726817F73651B9DE0FDA11E35FC4524568.xkm
[    29.186] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[    31.510] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[    31.515] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[    31.521] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[    31.527] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[    31.536] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[    31.541] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[    31.556] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[    49.229] (II) intel(0): EDID vendor "IBM", prod id 10375
[    49.229] (II) intel(0): Printing DDC gathered Modelines:
[    49.229] (II) intel(0): Modeline "1680x1050"x0.0  120.60  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (63.9 kHz eP)
[    49.229] (II) intel(0): Modeline "1680x1050"x0.0  100.53  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (53.2 kHz e)
[   627.838] (II) intel(0): EDID vendor "IBM", prod id 10375
[   627.838] (II) intel(0): Printing DDC gathered Modelines:
[   627.839] (II) intel(0): Modeline "1680x1050"x0.0  120.60  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (63.9 kHz eP)
[   627.839] (II) intel(0): Modeline "1680x1050"x0.0  100.53  1680 1712 1760 1888  1050 1051 1054 1065 -hsync -vsync (53.2 kHz e)
[  1153.796] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[  1273.174] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
[  1347.910] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm

[  1564.228] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF0ACC71A066167C59471BF2F4F51653FF6F85ED.xkm
```[COLOR=#333333][FONT=Trebuchet][B][SIZE=2]

Thank you so much! I am stumped.


[/SIZE]
[/B][/FONT][/COLOR]

---

