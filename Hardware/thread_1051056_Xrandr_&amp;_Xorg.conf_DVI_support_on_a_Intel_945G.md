---
title: "Xrandr &amp; Xorg.conf DVI support on a Intel 945GSE chipset. Ubuntu 8.10"
date: 2009-01-26
forum: Hardware
---

### Post by _UsUrPeR_ on 2009-01-26
Hey, guys. I am having a lot of problems getting dual-monitor output on boot from my 945GSE intel board.

Here's a list of the things operating from xrandr's perspective:

```
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 3360 x 1050
VGA connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+   60.0  
   1600x1024      60.2  
   1400x1050      74.8     70.0     60.0     60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1360x765       60.0  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1024x768       60.0 +   85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+   60.0  
   1600x1024      60.2  
   1400x1050      74.8     70.0     60.0     60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1360x765       60.0  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
TV disconnected (normal left inverted right x axis y axis)
```

When I boot my computer, the monitor attched to the DVI output (labeled TMDS-1 through xrandr) shuts off. Strangely enough, that same monitor is the one that displays the ubuntu login screen.

The easiest way to enable two monitors to work at 1680x1050 is as follows:

```
~$ xrandr --output LVDS --off
~$ xrandr --output TMDS-1 --off
~$ xrandr --output TMDS-1 --auto (this turns on the DVI monitor, which mirrors VGA output)
~$ xrandr --output TMDS-1 --right-of VGA
```

The above commands will make the DVI monitor turn on and behave as an extended desktop. My question is: is there a way to do this on boot? In gnome's Screen Resolution utility (System>Preferences>Screen Resolution), I am able to see both monitors are "active" on boot, but the DVI monitor will not be on. If I change the resolution of the DVI monitor, it will turn on. I am able to then switch to the monitor's native resolution of 1680x1050, and the monitor will work fine.

Here's my Xorg.7.log file:

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ltsp 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.7.log", Time: Mon Jan 26 18:22:54 2009
(++) Using config file: "/myxorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xfde80000/0, 0xd0000000/0, 0xfdf80000/0, I/O @ 0x0000ff00/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xfdf00000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "xtrap"

(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DEC-XTRAP
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "wacom"

(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.1-4 $
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
(--) intel(0): Chipset: "945GME"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFDE80000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Monitor0
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): SDVOB: device VID/DID: 02:3C.06, clock range 25.0MHz - 200.0MHz
(II) intel(0): SDVOB: 1 input channel
(II) intel(0): SDVOB: TMDS0 output reported
(II) intel(0): Output TV has no monitor section
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Output VGA connected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TMDS-1 connected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA using initial mode 1024x768
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): Output TMDS-1 using initial mode 1024x768
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (470, 300) mm
(**) intel(0): DPI set to (181, 88)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000b00 to 0x00000f00
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x80000a03 to 0x00000203
(WW) intel(0): PIPEASTAT before: status: FIFO_UNDERRUN GMBUS_INT_STATUS VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x00000202 to 0x00000000
(WW) intel(0): PIPEBSTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status:
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x10000010 to 0x000c0010
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 110080 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 440316 kB available
(EE) intel(0): Cannot support DRI with frame buffer width > 2048.
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): adjusting plane->pipe mappings to allow for framebuffer compression
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 51609600 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x03ac0000 (pgoffset 15040)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000001f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000001fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000001fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000001fe33000 physical
)
(II) intel(0): 0x00640000-0x03abffff: front buffer (53760 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x03ac0000-0x06bf7fff: exa offscreen (50400 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane B is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TMDS-1 is connected to pipe A
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Disabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
(**) Option "Protocol" "auto"
(**) Option "Device" "/dev/input/mice"
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(**) Mouse0: Device: "/dev/input/mice"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Mouse0: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5 6 7"
(**) Mouse0: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Mouse0: Buttons: 11
(**) Mouse0: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/input/wacom: Tablet PC buttons on 
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/input/wacom: Tablet PC buttons on 
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/input/wacom: Tablet PC buttons on 
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.15.2
Synaptics Touchpad no synaptics event device found
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1, removing from list!
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device HID Keyboard Device
(**) HID Keyboard Device: always reports core events
(**) HID Keyboard Device: Device: "/dev/input/event2"
(II) HID Keyboard Device: Found 1 mouse buttons
(II) HID Keyboard Device: Found keys
(II) HID Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID Keyboard Device: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID Keyboard Device: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HID Keyboard Device: xkb_layout: "us"
(**) HID Keyboard Device: YAxisMapping: buttons 4 and 5
(**) HID Keyboard Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device HID Keyboard Device
(**) HID Keyboard Device: always reports core events
(**) HID Keyboard Device: Device: "/dev/input/event1"
(II) HID Keyboard Device: Found keys
(II) HID Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID Keyboard Device: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID Keyboard Device: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HID Keyboard Device: xkb_layout: "us"
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): First SDVOB output reported failure to sync
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) config/hal: Adding input device USB Optical Mouse
(**) USB Optical Mouse: always reports core events
(**) USB Optical Mouse: Device: "/dev/input/event6"
(II) USB Optical Mouse: Found x and y relative axes
(II) USB Optical Mouse: Found 3 mouse buttons
(II) USB Optical Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
(**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!

(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(EE) intel(0): First SDVOB output reported failure to sync
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1440x900"x75.0  136.49  1440 1536 1688 1936  900 901 904 940 -hsync +vsync (70.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(II) intel(0): EDID vendor "ACR", prod id 13
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
```


Here is my xorg.conf. Notice the virtual resolution entry to allow for a larger screen:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"cursor"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
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
EndSection

Section "Module"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "record"
	Load  "xtrap"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	"XkbRules"	"xorg"
	Option	"XkbModel"	"pc105"
	Option	"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
	Option	"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver	"synaptics"
	Option	"SendCoreEvents"	"true"
	Option	"Device"	"/dev/psaux"
	Option	"Protocol"	"auto-dev"
	Option	"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver	"wacom"
	Identifier	"stylus"
	Option	"Device"	"/dev/input/wacom"
	Option	"Type"		"stylus"
	Option	"ForceDevice"	"ISDV4"	# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver	"wacom"
	Identifier	"eraser"
	Option	"Device"	"/dev/input/wacom"
	Option	"Type"		"eraser"
	Option	"ForceDevice"	"ISDV4"	# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver	"wacom"
	Identifier	"cursor"
	Option	"Device"	"/dev/input/wacom"
	Option	"Type"		"cursor"
	Option	"ForceDevice"	"ISDV4"	# Tablet PC ONLY
EndSection

Section "Monitor"
	#DisplaySize	  470   300	# mm
	Identifier   "Monitor0"
	VendorName   "ACR"
	ModelName    "X223W"
	HorizSync    31.0 - 84.0
	VertRefresh  56.0 - 77.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GME Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24
	SubSection "Display"
	Virtual  3360 1050
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
	Virtual  3360 1050
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
	Virtual  3360 1050
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
	Virtual  3360 1050
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
	Virtual  3360 1050
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
	Virtual  3360 1050
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection
```

I know the Xorg.7.log file shows a lot of underrun errors, but I assure you that the image output on the monitor is crisp and clear.

Any help would be greatly appreciated. :D

---

### Post by _UsUrPeR_ on 2009-01-26
UPDATE:

it appears if I switch to TTY1~6, then switch back to TTY7, the DVI monitor comes up properly.

---

