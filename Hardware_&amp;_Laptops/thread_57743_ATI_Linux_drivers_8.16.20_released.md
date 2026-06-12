---
title: "ATI Linux drivers 8.16.20 released"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by MightyPez on 2005-08-17
From the release notes:

> **Workstation Performance Improvement**

This release of the ATI Proprietary Linux driver provides a noticeable performance increase for all supported ATI Workstation products. 

**Improved Display Detection Support**

This release improves automatic detection of display devices when connected to an ATI graphics adapter. This allows for the display device to be configured using its Extended Display Identification Data (EDID) or to manually configured. For more information, refer to /usr/share/doc/fglrx/configure.html once the driver is installed.

**Linux 2.6.12 Kernel Support**

This release of the ATI Proprietary Linux driver introduces driver compatibly with Linux 2.6.12 kernel.

**GCC 4.0 Support**

The latest ATI Proprietary Linux driver now provides support for building the driver kernel module on systems with GCC 4.0
Driver Package Update

The **Debian and Ubuntu** operating systems are now supported by the ATI Installer Package Generator. Updates have occured to the SuSE package generation. 

 

[Grab them here.](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300) 


I'll be installing them in a minute.

---

### Post by MightyPez on 2005-08-17
Ok, installed them and ran glxgears on my 9700 pro:

> **8.14.13**

18780 frames in 5.0 seconds = 3756.000 FPS
21462 frames in 5.0 seconds = 4292.400 FPS
21475 frames in 5.0 seconds = 4295.000 FPS
21495 frames in 5.0 seconds = 4299.000 FPS
21473 frames in 5.0 seconds = 4294.600 FPS
21481 frames in 5.0 seconds = 4296.200 FPS
21491 frames in 5.0 seconds = 4298.200 FPS
21461 frames in 5.0 seconds = 4292.200 FPS


**8.16.20**

20044 frames in 5.0 seconds = 4008.800 FPS
21466 frames in 5.0 seconds = 4293.200 FPS
21476 frames in 5.0 seconds = 4295.200 FPS
21507 frames in 5.0 seconds = 4301.400 FPS
21492 frames in 5.0 seconds = 4298.400 FPS
21493 frames in 5.0 seconds = 4298.600 FPS
21487 frames in 5.0 seconds = 4297.400 FPS
21472 frames in 5.0 seconds = 4294.400 FPS

Looks like the performance boost really is only for workstation cards.

---

### Post by sc0rpi0n on 2005-08-17
what is the path to follow to install them? i'm using right now the ones inclueded in repositories.. tnx

---

### Post by Jengu on 2005-08-17
[QUOTE=MightyPez]Ok, installed them and ran glxgears on my 9700 pro:
[/QUOTE]

 How did you get them to install? I chose the make distribution specific package option because they've added ubuntu support. I told it I was running Hoary (5.04) which I am, and it generated a normal package and a dev package. I installed the dev package then the normal package using dpkg -i. Then I hit Ctrl+Alt+F1 and from the terminal did /etc/init.d/kdm restart to restart X. But now glxinfo reports direct rendering is off (didn't have this problem last version) and if I look at /var/log/Xorg.0.log it says the kernel version and the fglrx module version don't match! :P

I also tried the direct install option, same problem.

Lastly, don't use glxgears as a benchmark. For any modern card it's meaningless beyond telling you whether DRI is on. Run a real 3D app like a game under wine or ut2004 or doom3.

---

### Post by MightyPez on 2005-08-17
Installing them was a breeze. I just ran the large installer package:

```
sudo sh ./ati-driver-installer-8.16.20-i386.run
```

Choose the automated method, and let it install over the previous set. 

The *previous* set, however, required a few more steps. I pretty much had to follow the steps in [this](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=8.14.13) thread.

---

### Post by m0unds on 2005-08-17
and even though my hardware is supported, the driver still won't work. PHENOMENAL.


i get an error that there is "no matching Device entry for BusID PCI:1:0:1"

if i add one, with fglrx as the driver for both it won't work. ati as primary driver and fglrx as secondary, x loads, but with mesa as the library. set fglrx as the primary display driver and ati as secondary, it says there's no matching entry for 1:0:0. yippee.

anyone have a workaround for this issue?

(i've tried doing the fixes listed in other threads to no avail-- i've tried installing the ATI drivers with and without the old ubuntu FGLRX drivers [and they don't work, either..] )

---

### Post by Caboose on 2005-08-18
On my 9800 XT I increased from 2200 to 2500 :(

Why do I get such crappy framerates :(

---

### Post by Septor on 2005-08-18
[QUOTE=Jengu]How did you get them to install? I chose the make distribution specific package option because they've added ubuntu support. I told it I was running Hoary (5.04) which I am, and it generated a normal package and a dev package. I installed the dev package then the normal package using dpkg -i. Then I hit Ctrl+Alt+F1 and from the terminal did /etc/init.d/kdm restart to restart X. But now glxinfo reports direct rendering is off (didn't have this problem last version) and if I look at /var/log/Xorg.0.log it says the kernel version and the fglrx module version don't match! :P

I also tried the direct install option, same problem.

Lastly, don't use glxgears as a benchmark. For any modern card it's meaningless beyond telling you whether DRI is on. Run a real 3D app like a game under wine or ut2004 or doom3.[/QUOTE]

There is no binary kernel module provided with the Ubuntu package.  This is due to people's varying kernel versions.  To build the kernel module you can do the following (for 2.6 kernels).
```

cd /usr/src
tar -jxvf fglrx.tar.bz2
cd /usr/src/linux-<your kernel version>
make SUBDIRS=/usr/src/modules/fglrx modules modules_install

```
 fglrx.tar.bz2 is created by the fglrx-kernel-source package, so make sure you install that first.

---

### Post by Septor on 2005-08-18
[QUOTE=m0unds]and even though my hardware is supported, the driver still won't work. PHENOMENAL.


i get an error that there is "no matching Device entry for BusID PCI:1:0:1"

if i add one, with fglrx as the driver for both it won't work. ati as primary driver and fglrx as secondary, x loads, but with mesa as the library. set fglrx as the primary display driver and ati as secondary, it says there's no matching entry for 1:0:0. yippee.

anyone have a workaround for this issue?

(i've tried doing the fixes listed in other threads to no avail-- i've tried installing the ATI drivers with and without the old ubuntu FGLRX drivers [and they don't work, either..] )[/QUOTE]

Post your xorg.conf and /var/log/Xorg.0.log

That message is not an error, but a warning is it not?

---

### Post by m0unds on 2005-08-18
in its working state-- 

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
 Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 XT PE (R481)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART" "no"
 EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Secondary (R481)"
	Driver		"fglrx"
	BusID		"PCI:1:0:1"
	Option		"UseInternalAGPGART" "no"
EndSection



Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X850 XT PE (R481)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
``` 

substitute FGLRX in the place of "ati" to replicate the error/warning (WW then EE) i'm receiving in my log.

---

### Post by m0unds on 2005-08-18
```
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux m0undsbox 2.6.10-5-686-smp #1 SMP Fri Jun 24 18:12:58 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-686-smp (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Fri Jun 24 18:12:58 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 17 22:51:17 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon X850 XT PE (R481)"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2578 card 1695,4003 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1695,4003 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1695,4003 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1695,4003 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1695,4003 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1695,4003 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1695,4003 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1695,4003 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4b4c card 1002,0312 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4b6c card 1002,0313 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:00:0: chip 1103,0008 card 1103,0001 rev 07 class 01,04,00 hdr 80
(II) PCI: 02:00:1: chip 1103,0008 card 1103,0001 rev 07 class 01,04,00 hdr 80
(II) PCI: 02:01:0: chip 14e4,1653 card 1695,9013 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:06:0: chip 1102,0004 card 1102,1002 rev 04 class 04,01,00 hdr 80
(II) PCI: 02:06:1: chip 1102,7003 card 1102,0060 rev 04 class 09,80,00 hdr 80
(II) PCI: 02:06:2: chip 1102,4001 card 1102,0010 rev 04 class 0c,00,10 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
```

---

### Post by m0unds on 2005-08-18
```
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x4b4c) rev 0, Mem @ 0xe0000000/27, 0xf1000000/16, I/O @ 0xc000/8
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x4b6c) rev 0, Mem @ 0xe8000000/27, 0xf1010000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.16.20
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4

(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.16.20
(II) ATI Proprietary Linux Driver Release Identifier: @@UNRELEASED_AND_UNSUPPORTED_DRIVER@@
(II) ATI Proprietary Linux Driver Build Date: Aug 16 2005 00:15:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.16.1-driver-lnx-206829
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```

culled some extraneous PCI range info

---

### Post by Septor on 2005-08-18
mOunds: what card do you have?  Is it a Radeon 850XT?  If so try adding **one** of the following to your fglrx device section:

```

ChipID 0x5D4F  # Radeon X850 Pro
ChipID 0x5D52  # Radeon X850 XT
ChipID 0x5D4D  # Radeon X850 XT Platinum Edition

```

---

### Post by m0unds on 2005-08-18
it loaded x just fine now, but there's no direct rendering available. 

2d acceleration is working a-ok.

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

---

### Post by Septor on 2005-08-18
Did you install the kernel module (fglrx.ko)?  If you ran the ATI installer, it should have done this for you, if you installed the Ubuntu packages you might have more to do.  What does the output from "dmesg" show?

---

### Post by Cobra78 on 2005-08-18
[QUOTE=m0unds]in its working state-- 

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
 Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 XT PE (R481)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART" "no"
 EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Secondary (R481)"
	Driver		"fglrx"
	BusID		"PCI:1:0:1"
	Option		"UseInternalAGPGART" "no"
EndSection



Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X850 XT PE (R481)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
``` 

substitute FGLRX in the place of "ati" to replicate the error/warning (WW then EE) i'm receiving in my log.[/QUOTE]
 :(

I installed this driver, but same problem: wen i put Driver "fglrx" in xorg.conf it says no screen found ;_;

I also have a strange problem: i can't retrive fglrx.ko O__O

After many reinstallation of ATI driver and varius related pakeges this file won't appear in my /lib/bla bla bla/drivers/video  directory  ;_;

---

### Post by Septor on 2005-08-18
[QUOTE=Cobra78]:(

I installed this driver, but same problem: wen i put Driver "fglrx" in xorg.conf it says no screen found ;_;

I also have a strange problem: i can't retrive fglrx.ko O__O

After many reinstallation of ATI driver and varius related pakeges this file won't appear in my /lib/bla bla bla/drivers/video  directory  ;_;[/QUOTE]

make sure you uninstall the old Ubuntu fglrx packages before using the ATI installer.  Then download the 50MB ATI installer and run it with sudo.  Then reboot.

I recommend people with problems checkout [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88) for ATI Linux driver help.

---

### Post by fragmental on 2005-08-18
[QUOTE=Jengu]How did you get them to install? I chose the make distribution specific package option because they've added ubuntu support. I told it I was running Hoary (5.04) which I am, and it generated a normal package and a dev package. I installed the dev package then the normal package using dpkg -i. Then I hit Ctrl+Alt+F1 and from the terminal did /etc/init.d/kdm restart to restart X. But now glxinfo reports direct rendering is off (didn't have this problem last version) and if I look at /var/log/Xorg.0.log it says the kernel version and the fglrx module version don't match! :P

I also tried the direct install option, same problem.

Lastly, don't use glxgears as a benchmark. For any modern card it's meaningless beyond telling you whether DRI is on. Run a real 3D app like a game under wine or ut2004 or doom3.[/QUOTE]

I recieved this message when I was running Gentoo linux and all I had to do was restart the computer.

I believe that _**everyone should try restarting the computer **_before believing it's some other issue.

> There is no binary kernel module provided with the Ubuntu package. This is due to people's varying kernel versions. To build the kernel module you can do the following (for 2.6 kernels).
Code:

cd /usr/src tar -jxvf fglrx.tar.bz2 cd /usr/src/linux-<your kernel version> make SUBDIRS=/usr/src/modules/fglrx modules modules_install


fglrx.tar.bz2 is created by the fglrx-kernel-source package, so make sure you install that first.

Are you referring to ati's binary module driver?  It seems like they would add a binary for ubuntu hoary's kernel.  Obviously, if someone recompiles there kernel that person would have to recompile the module, but for those who use the default hoary kernel, they probably don't have to.

I have yet to install the drivers so I can't confirm this, but it sounds right.

> substitute FGLRX in the place of "ati" to replicate the error/warning (WW then EE) i'm receiving in my log.

Are you saying that you are changing "fglrx" to "ati" and then getting that error?  If so, the answer is pretty obvious.  "ati" is x.org's driver and "fglrx" is ATI's. x.org's does not have hardware acceleration.

---

### Post by NuSYS on 2005-08-18
anyone got problem with screen resolution?
After installing these new drivers I'm not able to set 1280x800.

---

### Post by m0unds on 2005-08-18
[QUOTE=fragmental]

Are you saying that you are changing "fglrx" to "ati" and then getting that error?  If so, the answer is pretty obvious.  "ati" is x.org's driver and "fglrx" is ATI's. x.org's does not have hardware acceleration.[/QUOTE]

No. Substituting fglrx in the place of ati = putting "fglrx" where the driver would say "ati" as  default. 

this machine has been rebooted countless times. every time i install the ati driver, i reboot. i have installed, removed, installed, removed and so on and so forth-- removing all files manually, etc. there are no traces of the ubuntu fglrx drivers remaining.

---

### Post by m0unds on 2005-08-18
```

Linux version 2.6.10-5-686-smp (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Fri Jun 24 18:12:58 UTC 2005
Total of 2 processors activated (12828.67 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking TSC synchronization across 2 CPUs: passed.
Brought up 2 CPUs
CPU0:
 domain 0: span 01
  groups: 01
  domain 1: span 03
   groups: 01 02
CPU1:
 domain 0: span 02
  groups: 02
  domain 1: span 03
   groups: 02 01

ACPI: PCI interrupt 0000:02:00.1[A] -> GSI 16 (level, low) -> IRQ 16
HPT37X: using 33MHz PCI clock
    ide4: BM-DMA at 0xd900-0xd907, BIOS settings: hdi:pio, hdj:pio
    ide5: BM-DMA at 0xd908-0xd90f, BIOS settings: hdk:pio, hdl:pio
Probing IDE interface ide2...
hdf: MAXTOR 6L040J2, ATA DISK drive
ide2 at 0xd000-0xd007,0xd102 on irq 16
hdf: max request size: 128KiB
hdf: 78177792 sectors (40027 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
hdf: cache flushes supported
 /dev/ide/host2/bus0/target1/lun0: p1
Probing IDE interface ide3...
hdg: Maxtor 6E040L0, ATA DISK drive
ide3 at 0xd200-0xd207,0xd302 on irq 16
hdg: max request size: 128KiB
hdg: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hdg: cache flushes supported
 /dev/ide/host2/bus1/target0/lun0: p1
Probing IDE interface ide4...
Probing IDE interface ide5...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (470 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 867468k swap on /dev/hdb5.  Priority:-1 extents:1
EXT3 FS on hdb2, internal journal
hdc: ATAPI 48X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
parport0: Printer, Canon S520
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: hdd: mrw address space DMA selected
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel i875 Chipset.
agpgart: Maximum main memory to use for agp memory: 941M
agpgart: AGP aperture is 256M @ 0xd0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0xe300
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0xe000
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xe100
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0xe200
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 1-2: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xf4000000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usbcore: registered new driver hiddev
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random hardware driver 1.0.0 loaded
usbhid: probe of 1-2:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
tg3.c:v3.14 (November 15, 2004)
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 17
eth0: Tigon3 [partno(BCM95705A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:04:61:57:f7:b5
eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1]
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 22 (level, low) -> IRQ 22
usb 1-2: USB disconnect, address 2
usb 1-2: new low speed USB device using uhci_hcd and address 3
gameport: pci0000:02:06.1 speed 1147 kHz
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:06.2[B] -> GSI 23 (level, low) -> IRQ 23
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[f3014000-f30147ff]  Max Packet=[2048]
input: USB HID v1.10 Gamepad [Gravis Eliminator AfterShock   ] on usb-0000:00:1d.0-2
usb 2-1: new low speed USB device using uhci_hcd and address 2
NET: Registered protocol family 17
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c00910742c4]
tg3: eth0: Link is up at 100 Mbps, half duplex.
tg3: eth0: Flow control is off for TX and off for RX.
input: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D Pro] on usb-0000:00:1d.2-2
usb 4-2: new full speed USB device using uhci_hcd and address 2
usbcore: registered new driver snd-usb-audio
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0317e40(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3

```

output from dmesg

---

### Post by m0unds on 2005-08-18
```
(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x078ef000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ef000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x07ff0000
(II) fglrx(0): Splitting WC range: base: 0xe0000000, size: 0x7ff0000
(II) fglrx(0): Splitting WC range: base: 0xe4000000, size: 0x3ff0000
(II) fglrx(0): Splitting WC range: base: 0xe6000000, size: 0x1ff0000
(II) fglrx(0): Splitting WC range: base: 0xe7000000, size: 0xff0000
(II) fglrx(0): Splitting WC range: base: 0xe7800000, size: 0x7f0000
(II) fglrx(0): Splitting WC range: base: 0xe7c00000, size: 0x3f0000
(II) fglrx(0): Splitting WC range: base: 0xe7e00000, size: 0x1f0000
(II) fglrx(0): Splitting WC range: base: 0xe7f00000, size: 0xf0000
(II) fglrx(0): Splitting WC range: base: 0xe7f80000, size: 0x70000
(II) fglrx(0): Splitting WC range: base: 0xe7fc0000, size: 0x30000
(==) fglrx(0): Write-combining range (0xe7fe0000,0x10000)
(==) fglrx(0): Write-combining range (0xe7fc0000,0x30000)
(==) fglrx(0): Write-combining range (0xe7f80000,0x70000)
(==) fglrx(0): Write-combining range (0xe7f00000,0xf0000)
(==) fglrx(0): Write-combining range (0xe7e00000,0x1f0000)
(==) fglrx(0): Write-combining range (0xe7c00000,0x3f0000)
(==) fglrx(0): Write-combining range (0xe7800000,0x7f0000)
(WW) fglrx(0): Failed to set up write-combining range (0xe7000000,0xff0000)
(WW) fglrx(0): Failed to set up write-combining range (0xe6000000,0x1ff0000)
(WW) fglrx(0): Failed to set up write-combining range (0xe4000000,0x3ff0000)
(WW) fglrx(0): Failed to set up write-combining range (0xe0000000,0x7ff0000)
``` 

NEW and improved x.org log output.

---

### Post by brj on 2005-08-18
[QUOTE=sc0rpi0n]what is the path to follow to install them? i'm using right now the ones inclueded in repositories.. tnx[/QUOTE]
 i installed it using the installer-gui. 
and i'm happy with it because for the first time i can use the dvi output of my radeon 9200 under linux :D

jakob

---

### Post by easy_target on 2005-08-18
I have nothing to complain about the new drivers. ATI has come a long way in the development and I am quite happy with my performance. I encourage anyone willing to try to go ahead and they won't be disappointed.

---

### Post by fragmental on 2005-08-18
[QUOTE=Septor]make sure you uninstall the old Ubuntu fglrx packages before using the ATI installer.  Then download the 50MB ATI installer and run it with sudo.  Then reboot.

I recommend people with problems checkout [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88) for ATI Linux driver help.[/QUOTE]

If you check that link, it looks like Septor is the one who submitted the ubuntu/debian drivers so it might be a good idea to read his answers if you're stuck.

It would be nice if someone created a little howto(with trouble shooting) for installing the ubuntu drivers via the installer.

---

### Post by Septor on 2005-08-19
[QUOTE=NuSYS]anyone got problem with screen resolution?
After installing these new drivers I'm not able to set 1280x800.[/QUOTE]

NuSYS, this is a known issue that popped up shortly after the release came out.  It is due to the fact that your laptop (eMachines, Samsung display I guess?) does not report its display resolutions via EDID correctly.  A bug in the driver further prevents you from specifying a correct 1200x800 modeline.  Until a next release, if it is bothering you, stick with 8.14 for now.

---

### Post by Septor on 2005-08-19
[QUOTE=fragmental]If you check that link, it looks like Septor is the one who submitted the ubuntu/debian drivers so it might be a good idea to read his answers if you're stuck.

It would be nice if someone created a little howto(with trouble shooting) for installing the ubuntu drivers via the installer.[/QUOTE]

Using the installer should be trivial to get working. Here is a quicky howto:

1) Download the 50MB(!) installer from ATI ([http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run))
2) check that you have your kernel headers in /usr/src/linux-<version> and that /usr/src/linux is a symbolic link to that directory.  This is needed to compile the fglrx kernel module.
3) change to single user mode via "sudo telinit 1", this will drop you to the console.
4) start the installer as root: "sudo sh ./ati-driver-installer-xxxxx"
5) most people can just accept the defaults in the installer (just hit enter at each screen) until the driver starts installation.
6) wait for installation to finish (shouldn't take too long, 30sec at most maybe).
7) run "sudo fglrxconfig" to generate your /etc/X11/xorg.conf file or simply change "radeon" to "fglrx" in your Device section if it exists already.
8.) sync && reboot (I recommend a reboot, even though it is technically not necessary, as I've hit problems before when not rebooting).
9) Enjoy 3D :)  For problems I highly recommend the forums at Rage3D as there is a large community of willing people with lots of experience with these drivers: [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88)

I did create the Ubuntu package scripts, but they tend to be more useful for packagers than for end-users.  Hopefully with the scripts in the ATI package, we can get this driver into the Ubuntu repository sooner making upgrades a lot smoother.

---

### Post by drummer on 2005-08-19
The fglrx drivers didn't work for me at first, I needed to do what's here: [http://ubuntuforums.org/showpost.php?p=163115&postcount=6](http://ubuntuforums.org/showpost.php?p=163115&postcount=6) (the line in bold). Otherwise the kernel modile wasn't overwritten by the ATI installer. This was with the 8.14.13 version, but it may be the same or similar problem with the install of the drivers. My $0.02.

---

### Post by Cobra78 on 2005-08-20
Finally i installed ATI Driver, but yet i don't have 3D acceleration, i read Xorg.0.log and found this.

[http://paste.ubuntulinux.nl/1436](http://paste.ubuntulinux.nl/1436) 

Anyone had any idea?

---

### Post by Cobra78 on 2005-08-20
[QUOTE=Cobra78]Finally i installed ATI Driver, but yet i don't have 3D acceleration, i read Xorg.0.log and found this.

[http://paste.ubuntulinux.nl/1436](http://paste.ubuntulinux.nl/1436) 

Anyone had any idea?[/QUOTE]
 Nobody had any idea?

:(

---

### Post by fragmental on 2005-08-21
[QUOTE=Cobra78]Nobody had any idea?

:([/QUOTE]
 Well, you have the entire log pasted there.  Maybe you should indicate what you found.  

Also, read the rest of this thread and the thread or threads at rage3d.  You can use the search function to see if anyone else has had the same problem.

---

### Post by Cobra78 on 2005-08-21
```

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

The problem is here, but i have tried other solutions in this tread with no effects :/

---

### Post by Hamman on 2005-08-21
Worked fine for me! Installed with sudo sh .ati-blalal, just removed the fglrx-driver with synaptic first. I get the same glxgears fps on my 9600 pro (~4500), but the extended control panel looks nice. BTW, used fglrxconfig to generate my xorg.conf.

---

### Post by NuSYS on 2005-08-21
[QUOTE=Septor]NuSYS, this is a known issue that popped up shortly after the release came out.  It is due to the fact that your laptop (eMachines, Samsung display I guess?) does not report its display resolutions via EDID correctly.  A bug in the driver further prevents you from specifying a correct 1200x800 modeline.  Until a next release, if it is bothering you, stick with 8.14 for now.[/QUOTE]

thanks for the answer :)

---

### Post by alxarch on 2005-08-21
i have th following problem: all how to's i 've read DON'T work 4 me bcause in most of the cases they refer to dload rpms or .run files from ati. I have a sony laptop with x600 mobility radeon and in the ati website they say: go to yr vendor of the laptop to dload(thanks a lot, sony has only xin drivers). whenever i try to put fglrx as driver (i installed the package xorg driver fglrx blah blah)the screen goes blank when ixserver runs any suggestions?

---

### Post by Jeezis on 2005-08-22
[QUOTE=MightyPez]From the release notes:

 

[Grab them here.](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300) 


I'll be installing them in a minute.[/QUOTE]
 will this driver help give me better framerates on my ati radeon 320m igp?

what about 3d hardware acceleration?

i could really use some help, any ideas or anything would be appreciated

---

### Post by NumbSkullMD on 2005-08-22
It resulted in better frame rates and performance for me.

:?

---

### Post by RogerSilva on 2005-08-22
Hi, 
I've tried to install this driver using automatic install with no success(it simply currupted the XOrg configuration and the OnpeGL libraries(the fglrx module installed get some memory allocation errors  and the XServer doesn't work, and since it is not possible to uninstall I had to install all my system again).  So I tried to generate the package for Ubuntu 5.04, and I got the folowing erro:

```

Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.16.20-1
dpkg-buildpackage: source maintainer is ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture is amd64
debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
if [ -f /tmp/fglrx/debian/driver.$i ]; then \
sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
/tmp/fglrx/debian/xorg-driver-fglrx.$i; \
fi; \
done
dh_testdir
dh_testdir
fakeroot debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
if [ -f /tmp/fglrx/debian/driver.$i ]; then \
sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
/tmp/fglrx/debian/xorg-driver-fglrx.$i; \
fi; \
done
dh_testdir
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
usr/X11R6 \
usr/X11R6/bin \
usr/X11R6/lib \
usr/X11R6/lib/modules \
usr/share/fglrx/diversions
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
usr/X11R6/lib32 \
usr/X11R6/lib32/modules \
emul/ia32-linux/usr/X11R6/lib \
emul/ia32-linux/usr/X11R6/lib/modules/driver \
emul/ia32-linux/usr/X11R6/lib/modules/linux \
emul/ia32-linux/usr/X11R6/lib/modules/dri
dh_installdirs -pxorg-driver-fglrx-dev \
usr/X11R6 \
usr/X11R6/include \
usr/X11R6/lib \
usr/include
dh_installdirs -pfglrx-kernel-source \
usr/src/modules/fglrx \
usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
usr/X11R6 \
usr/X11R6/bin \
usr/share \
usr/share/applnk \
usr/share/gnome \
usr/share/gnome/apps \
usr/share/icons \
usr/share/pixmaps
dh_installdirs -pfglrx-sources \
usr/src
dh_install
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*" "usr/X11R6/bin"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*" "usr/X11R6/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*" "usr/X11R6/lib/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*" "usr/X11R6/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/*" "usr/X11R6/lib32/modules"
dh_link -pxorg-driver-fglrx "usr/X11R6/lib32/libGL.so.1.2" \
"emul/ia32-linux/usr/X11R6/lib/libGL.so.1.2"
dh_link -pxorg-driver-fglrx "usr/X11R6/lib32/libfglrx_gamma.so.1.0" \
"emul/ia32-linux/usr/X11R6/lib/libfglrx_gamma.so.1.0"
dh_link -pxorg-driver-fglrx "usr/X11R6/lib32/modules/driver/fglrx_drv.o" \
"emul/ia32-linux/usr/X11R6/lib/modules/driver/fglrx_drv.o"
dh_link -pxorg-driver-fglrx "usr/X11R6/lib32/modules/linux/libfglrxdrm.a" \
"emul/ia32-linux/usr/X11R6/lib/modules/linux/libfglrxdrm.a"
dh_link -pxorg-driver-fglrx "usr/X11R6/lib32/modules/dri/atiogl_a_dri.so" \
"emul/ia32-linux/usr/X11R6/lib/modules/dri/atiogl_a_dri.so"
dh_link -pxorg-driver-fglrx "usr/X11R6/lib32/modules/dri/fglrx_dri.so" \
"emul/ia32-linux/usr/X11R6/lib/modules/dri/fglrx_dri.so"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/X11R6/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/X11R6/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*" "usr/include"
dh_install -pfglrx-kernel-source \
lib/modules/fglrx/build_mod/*.c \
lib/modules/fglrx/build_mod/*.h \
lib/modules/fglrx/build_mod/*.sh \
lib/modules/fglrx/build_mod/lib* \
lib/modules/fglrx/build_mod/2.6.x/Makefile \
usr/src/modules/fglrx
dh_install -pfglrx-kernel-source "debian/changelog" "usr/src/modules/fglrx/debian"
dh_install -pfglrx-kernel-source \
debian/copyright \
debian/compat \
module/rules \
module/control.template \
module/dirs.template \
usr/src/modules/fglrx/debian
(cd debian/fglrx-kernel-source/usr/src \
&& chown -R root:src modules \
&& tar -c modules | bzip2 > fglrx.tar.bz2 \
&& rm -rf modules)
# install panel files
dh_install -A -pfglrx-control "usr/X11R6/bin/fireglcontrolpanel" "usr/X11R6/bin"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm" "usr/share/icons"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm" "usr/share/pixmaps"
dh_install -A -pfglrx-control "usr/share/gnome/apps/fireglcontrol.desktop" "usr/share/gnome/apps"
dh_install -A -pfglrx-control "usr/share/applnk/fireglcontrol.kdelnk" "usr/share/applnk"
dh_install -pfglrx-sources "usr/src/*" "usr/src"
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of libfglrx_gamma.1 not recognized
debian/xorg-driver-fglrx/usr/X11R6/lib32/modules/dri/fglrx_dri.so: error while loading shared libraries: libfakeroot.so.0: cannot open shared object file: No such file or directory
dpkg-shlibdeps: failure: ldd on `debian/xorg-driver-fglrx/usr/X11R6/lib32/modules/dri/fglrx_dri.so' gave error exit status 1
dh_shlibdeps: command returned error code 256
make: ** [binary] Erro 1
~/linuxDrivers/ATI/fglrx-install
[Error] Generate Package - error generating package : Ubuntu/5.04

``` 

I'm using Ubuntu 5.04 for AMD64.
Could anyone help me please??
I'm new in Linux and I don't know what is causing this to fail...

thanks a lot,
Roger

---

### Post by Jeezis on 2005-08-22
for some reason ati's website isn't letting me get to the download link...it keeps saying my session is expired...is there another place i can download it from perhaps? i think this problem may be caused by using tor and privoxy, but i don't want to mess with them because everything else works fine.

*EDIT*

nevermind, i got it to start downloading :-p hopefully it will help. it's very hard to find support for the radeon 320m igp

---

### Post by RogerSilva on 2005-08-22
Please, could anyone help me to install this dirver??
I am new in Linux, so I don't know what this error messages that appears on the package generation means...


thanks,
Roger

---

### Post by m0unds on 2005-08-22
[QUOTE=Cobra78]```

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

The problem is here, but i have tried other solutions in this tread with no effects :/[/QUOTE]


you and i are both having similar problems, and we've both been trying the solutions listed in the countless "broken ATI" threads scattered throughout this forum.

---

### Post by RogerSilva on 2005-08-23
[QUOTE=m0unds]you and i are both having similar problems, and we've both been trying the solutions listed in the countless "broken ATI" threads scattered throughout this forum.[/QUOTE]
Hi,
thanks for helping :-)
I'm confused because this is the first Linux that i installed (I just give up of using windows(it crash too much), but I'm having too much headaches to make linux work on my system)...
I'm trying to ask for help here, but  that nobody care about...


thanks,
Roger

---

### Post by Cobra78 on 2005-08-23
[QUOTE=RogerSilva]Hi,
thanks for helping :-)
I'm confused because this is the first Linux that i installed (I just give up of using windows(it crash too much), but I'm having too much headaches to make linux work on my system)...
I'm trying to ask for help here, but  that nobody care about...


thanks,
Roger[/QUOTE]
 Ai've tried all the guides thath i can find in this and other forums :(

My 9700 Pro won't work with Ubuntu :(

---

### Post by drummer on 2005-08-23
[QUOTE=RogerSilva]Hi,
thanks for helping :-)
I'm confused because this is the first Linux that i installed (I just give up of using windows(it crash too much), but I'm having too much headaches to make linux work on my system)...
I'm trying to ask for help here, but  that nobody care about...


thanks,
Roger[/QUOTE]
 These drivers are very new and probably not many people have tried them much, so that might be why there are so few answers on this thread. They didn't work straight away for me so I went back to using the previous version from ATI (8.14.13) which work ok with my radeon 9250. A difficulty with graphics drivers are that they are propriatry and so the sources are owned by ATI; because of this we can only work with what we've got and fix problems by adapting to the drivers, rather than adapting the drivers to our systems: making it harder to solve problems.

If the newest drivers aren't working for you, you could try the previous release or wait for the next version and go without 3d accelleration for the time being. Keep checking back though and looking in other threads here, a solution or other peoples experienced are bound to be posted when more people move to the newer drivers.

Stick in there with Linux and things should eventually sort themselves out. And it's a lot of fun along the way.  ;-)

---

### Post by RogerSilva on 2005-08-23
[QUOTE=drummer]These drivers are very new and probably not many people have tried them much, so that might be why there are so few answers on this thread. They didn't work straight away for me so I went back to using the previous version from ATI (8.14.13) which work ok with my radeon 9250. A difficulty with graphics drivers are that they are propriatry and so the sources are owned by ATI; because of this we can only work with what we've got and fix problems by adapting to the drivers, rather than adapting the drivers to our systems: making it harder to solve problems.

If the newest drivers aren't working for you, you could try the previous release or wait for the next version and go without 3d accelleration for the time being. Keep checking back though and looking in other threads here, a solution or other peoples experienced are bound to be posted when more people move to the newer drivers.

Stick in there with Linux and things should eventually sort themselves out. And it's a lot of fun along the way.  ;-)[/QUOTE]

Hi,
the problem is that the X-Server doesn't work correctly with my video card...
And the only ATi driver that support my video card is the version I'm trying to install, so I have 2 options: try to make this driver works or give up on Linux...
As I said so, I've tried the autommatic install that corrupted all OpenGl librireis(I've had to re-install all the librireis that the driver mofified...) and I tryed to generate the package for Ubuntu (that make the error log that I reported)....
Please, could some one help me??


thanks,
Roger

---

### Post by Farner on 2005-08-23
How do I know which driver I should download? I have downloaded Check.sh and when I did sh check.sh I only get this: ```
=====================================================================
 ATI Technologies
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.


```
I am in the console, and I have tried to do sudo sh check.sh and only sh check.sh. Nothing works. :(

---

### Post by RogerSilva on 2005-08-23
[QUOTE=Farner]How do I know which driver I should download? I have downloaded Check.sh and when I did sh check.sh I only get this: ```
=====================================================================
 ATI Technologies
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.


```
I am in the console, and I have tried to do sudo sh check.sh and only sh check.sh. Nothing works. :([/QUOTE]
Hi,
it seems that the only think this script (Check.sh) do is to check if you have the compatible XFree or XOrg versions...
You will need the kernel headers to try to install the driver...

roger

---

### Post by fragmental on 2005-08-23
[QUOTE=RogerSilva]Hi,
the problem is that the X-Server doesn't work correctly with my video card...
And the only ATi driver that support my video card is the version I'm trying to install, so I have 2 options: try to make this driver works or give up on Linux...
As I said so, I've tried the autommatic install that corrupted all OpenGl librireis(I've had to re-install all the librireis that the driver mofified...) and I tryed to generate the package for Ubuntu (that make the error log that I reported)....
Please, could some one help me??


thanks,
Roger[/QUOTE]

What is your video chipset or card?  The 2d xorg drivers worked, right?  Have you tried installing the ati drivers from synaptic or apt-get.  Those are the easiest to get to work.

BTW, I'm not trying to offend, I'm just curious;  is your native language english?

---

### Post by fragmental on 2005-08-23
[QUOTE=Septor]Using the installer should be trivial to get working. Here is a quicky howto:

1) Download the 50MB(!) installer from ATI ([http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run))
2) check that you have your kernel headers in /usr/src/linux-<version> and that /usr/src/linux is a symbolic link to that directory.  This is needed to compile the fglrx kernel module.
3) change to single user mode via "sudo telinit 1", this will drop you to the console.
4) start the installer as root: "sudo sh ./ati-driver-installer-xxxxx"
5) most people can just accept the defaults in the installer (just hit enter at each screen) until the driver starts installation.
6) wait for installation to finish (shouldn't take too long, 30sec at most maybe).
7) run "sudo fglrxconfig" to generate your /etc/X11/xorg.conf file or simply change "radeon" to "fglrx" in your Device section if it exists already.
8.) sync && reboot (I recommend a reboot, even though it is technically not necessary, as I've hit problems before when not rebooting).
9) Enjoy 3D :)  For problems I highly recommend the forums at Rage3D as there is a large community of willing people with lots of experience with these drivers: [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88)

I did create the Ubuntu package scripts, but they tend to be more useful for packagers than for end-users.  Hopefully with the scripts in the ATI package, we can get this driver into the Ubuntu repository sooner making upgrades a lot smoother.[/QUOTE]

I'm not sure if it was explained in this thread elsewhere, but I would like to add how to get the linux kernel headers.  (I found this in the [nvidia howto thread.](http://ubuntuforums.org/showthread.php?t=57368&highlight=kernel+headers)   Sometimes linux problems need parallel thinking.)
> Make sure you have the kernel headers of your current kernel installed. If not, you can install them following these steps:

Open either Terminal or Konsole and type:

uname -r (this will tell you the name and version of the kernel you are using)

Open either Synaptic or Kynaptic

press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-the name you got from uname -r"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

click on the files and select "Mark for installation"

Press the "Apply" button.


  You also need to uninstall the ubuntu hoary fglrx drivers, if you have them installed, by using synaptic or apt-get to uninstall the package "xorg-driver-fglrx".  Can anyone confirm if you need to reboot after uninstalling the drivers?  You might also need to uninstall "fglrx-control" if it's installed but I'm not sure.  So that would be step  1.1 and 1.2 maybe.

Notes on setp #2. If the symbolic link is missing you can add it by using "ln -s (name of the directory) linux."  Mine, and probably many other hoary users, is "ln -s linux-headers-2.5.10-5-386".  It should be whatever uname -r says probably.

You also might want to make sure that any dependencies for the" xorg-driver-fglrx" drivers are installed.  You don't need xorg-driver-fglrx but you might need the dependencies.

Also, about step 7, I think ATI recommends you make a backup of your xorg.conf, and then generate a new one using fglrx config and then look at them both to see what has changed.

Does anyone know if you need "nvidia-kernel-common"?  This isn't totally related to the ATI drivers, but I noticed I have the "nvidia-kernel-common" package installed and I'm not sure if it should be.  It probably comes with ubuntu, because I don't know why else it would be installed.  When I tried to uninstall it, it looked like it was going to uninstall some packages I might need so I quit.

---

### Post by jamesrw on 2005-08-23
I loaded the drivers pretty sucessfully.. ecept for two (minor?) issues:

this comes up in my dmesg:
```
[fglrx] Maximum main memory to use for locked dma buffers: 308 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
```

when i try to run the 'ATI Control' (/usr/X11R6/bin/fireglcontrolpanel) in the applications menu nothing comes up, so I then tried to run it from command. output shows:
```
james@tux64:~$ sudo /usr/X11R6/bin/fireglcontrolpanel
/usr/X11R6/bin/fireglcontrolpanel: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
```
tried to modprobe the library... no luck

Should I really worry about this? Anyone run into similar issues? I have a wide screen display and things seems more like they're a little stretched out instead but not bad at all.

---

### Post by fragmental on 2005-08-23
[QUOTE=m0unds]you and i are both having similar problems, and we've both been trying the solutions listed in the countless "broken ATI" threads scattered throughout this forum.[/QUOTE]

Hey, i finally tried it myself and I'm having the same problem too.  However, I found this line in my dmesg output.  

> [fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0

So you might want to check and see if you always have that line.  I kind of fudged up my install though and didn't uninstall the ubuntu package 8.8 package until after I installed ATI's 8.20.

Edit: Well, I fixed that by copying the fglrx.ko from /lib/modules/fglrx/ to /lib/modules/2.6.10-5-386/kernel/drivers/video/.  That wrote over the 8.8 driver.

This probably would have worked too, but I decided to do it the other way.
[QUOTE=drummer]The fglrx drivers didn't work for me at first, I needed to do what's here: [http://ubuntuforums.org/showpost.php?p=163115&postcount=6](http://ubuntuforums.org/showpost.php?p=163115&postcount=6) (the line in bold). Otherwise the kernel modile wasn't overwritten by the ATI installer. This was with the 8.14.13 version, but it may be the same or similar problem with the install of the drivers. My $0.02.[/QUOTE] 

However, after I rebooted I got the same error messages in the xorg.0.log about wrong version of whatever.  So I tried to modinfo the module and it said " could not open /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko: No such file or directory".  I tried to modprobe it and it said exactly the same thing.  It's there, it just doesn't like it or something.  Maybe I have nasty bits of 8.8 floating around that's interferring?

Edit:  Well that was dumb /lib/modules/fglrx/fglrx.ko was just a symbolic link. I tried copying the linked file to /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko but now it says "FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko): Operation not permitted
"

---

### Post by fragmental on 2005-08-23
[QUOTE=fragmental]Hey, i finally tried it myself and I'm having the same problem too.  However, I found this line in my dmesg output.  



So you might want to check and see if you always have that line.  I kind of fudged up my install though and didn't uninstall the ubuntu package 8.8 package until after I installed ATI's 8.20.

Edit: Well, I fixed that by copying the fglrx.ko from /lib/modules/fglrx/ to /lib/modules/2.6.10-5-386/kernel/drivers/video/.  That wrote over the 8.8 driver.

This probably would have worked too, but I decided to do it the other way.
 

However, after I rebooted I got the same error messages in the xorg.0.log about wrong version of whatever.  So I tried to modinfo the module and it said " could not open /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko: No such file or directory".  I tried to modprobe it and it said exactly the same thing.  It's there, it just doesn't like it or something.  Maybe I have nasty bits of 8.8 floating around that's interferring?

Edit:  Well that was dumb /lib/modules/fglrx/fglrx.ko was just a symbolic link. I tried copying the linked file to /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko but now it says "FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko): Operation not permitted
"[/QUOTE]
 Hey hey! I took my own advice and rebooted after that last step.  After that everything works like a charm.  I feel like dancing.

So, I'm going to rewrite the howto.

The unnoficial ATI ubuntu howto:

1)If you have installed the drivers through synaptic or apt-get, uninstall them using apt-get or synaptic(or kynaptic).
2) Download the 50MB(!) installer from ATI ([http://www2.ati.com/drivers/linux/a....16.20-i386.run](http://www2.ati.com/drivers/linux/a....16.20-i386.run))
3) check that you have your kernel headers in /usr/src/linux-headers-<version> and that /usr/src/linux is a symbolic link to that directory. This is needed to compile the fglrx kernel module.
3.1)If you don't have the headers get them by finding the package in synaptic called "linux-headers-(the name you got from uname -r)".  Then "ln -s /usr/src/linux-headers<version> /usr/src/linux".
4) change to single user mode via "sudo telinit 1", this will drop you to the console.
5) start the installer as root: "sudo sh ./ati-driver-installer-xxxxx"
6) most people can just accept the defaults in the installer (just hit enter at each screen) until the driver starts installation.
7) wait for installation to finish (shouldn't take too long, 30sec at most maybe).
8) run "sudo fglrxconfig" to generate your /etc/X11/xorg.conf file or simply change "radeon" to "fglrx" in your Device section if it exists already.  It might be a good idea to generate one even if you have one already just to see how they are different.  Make sure you don't copy over the original!
9.)reboot (I recommend a reboot, even though it is technically not necessary, as I've hit problems before when not rebooting).

Troubleshooting:
Direct Rendering doesn't work:
Try "ls -l /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko".  It should say the same date as the date you ran the ati driver installer. If not you will have to copy the fglrx driver from /lib/modules/fglrx/.  First rename or delete /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko and then "sudo cp /lib/modules/fglrx/fglrx.(kernel version).ko /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko".  Then, make sure you REBOOT.

Direct Rendering still doesn't work:  Yeah...that happens.  Check [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88) and search the rage3d forum and google for the ati linux howto and search this forum.  Someone may have had one of your problems already.  If you find a solution feel free to tell everybody.

---

### Post by Jeezis on 2005-08-24
[QUOTE=MightyPez]From the release notes:

 

[Grab them here.](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300) 


I'll be installing them in a minute.[/QUOTE]
 i think my card just isn't supported by the fglrx driver. it installed fine and i ran the fglrxconfig fine, but when i reboot x won't start. i guess i have to stick with the radeon driver and no 3d acceleration. i hate this graphics card! it's given me nothing but problems since day one! (it's an ati radeon 320m igp)

---

### Post by RogerSilva on 2005-08-24
[QUOTE=fragmental]What is your video chipset or card?  The 2d xorg drivers worked, right?  Have you tried installing the ati drivers from synaptic or apt-get.  Those are the easiest to get to work.

BTW, I'm not trying to offend, I'm just curious;  is your native language english?[/QUOTE]
Hi,
sorry by the english errors, I am not native language english.
I think that installing this apt-get drivers will not work, I have read in another thread that this is a older version that probably will not support my video card...
I have a Radeon Radeon X850 XT...

thanks,
Roger

---

### Post by PeP on 2005-08-24
[QUOTE=Jengu]
Lastly, don't use glxgears as a benchmark. For any modern card it's meaningless beyond telling you whether DRI is on. Run a real 3D app like a game under wine or ut2004 or doom3.[/QUOTE]
why not? 
When I switched from the fglrx driver provided by linux-restricted-modules to the next version, I **doubled** my fps on glxgears!

---

### Post by Cobra78 on 2005-08-24
[QUOTE=PeP]why not? 
When I switched from the fglrx driver provided by linux-restricted-modules to the next version, I **doubled** my fps on glxgears![/QUOTE]
 I've retried the driver installation, now i get this error

[http://paste.ubuntulinux.nl/1574](http://paste.ubuntulinux.nl/1574)

Can someone help me?

---

### Post by RogerSilva on 2005-08-24
[QUOTE=fragmental]Hey hey! I took my own advice and rebooted after that last step.  After that everything works like a charm.  I feel like dancing.

So, I'm going to rewrite the howto.

The unnoficial ATI ubuntu howto:

1)If you have installed the drivers through synaptic or apt-get, uninstall them using apt-get or synaptic(or kynaptic).
2) Download the 50MB(!) installer from ATI ([http://www2.ati.com/drivers/linux/a....16.20-i386.run](http://www2.ati.com/drivers/linux/a....16.20-i386.run))
3) check that you have your kernel headers in /usr/src/linux-headers-<version> and that /usr/src/linux is a symbolic link to that directory. This is needed to compile the fglrx kernel module.
3.1)If you don't have the headers get them by finding the package in synaptic called "linux-headers-(the name you got from uname -r)".  Then "ln -s /usr/src/linux-headers<version> /usr/src/linux".
4) change to single user mode via "sudo telinit 1", this will drop you to the console.
5) start the installer as root: "sudo sh ./ati-driver-installer-xxxxx"
6) most people can just accept the defaults in the installer (just hit enter at each screen) until the driver starts installation.
7) wait for installation to finish (shouldn't take too long, 30sec at most maybe).
8) run "sudo fglrxconfig" to generate your /etc/X11/xorg.conf file or simply change "radeon" to "fglrx" in your Device section if it exists already.  It might be a good idea to generate one even if you have one already just to see how they are different.  Make sure you don't copy over the original!
9.)reboot (I recommend a reboot, even though it is technically not necessary, as I've hit problems before when not rebooting).

Troubleshooting:
Direct Rendering doesn't work:
Try "ls -l /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko".  It should say the same date as the date you ran the ati driver installer. If not you will have to copy the fglrx driver from /lib/modules/fglrx/.  First rename or delete /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko and then "sudo cp /lib/modules/fglrx/fglrx.(kernel version).ko /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko".  Then, make sure you REBOOT.

Direct Rendering still doesn't work:  Yeah...that happens.  Check [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88) and search the rage3d forum and google for the ati linux howto and search this forum.  Someone may have had one of your problems already.  If you find a solution feel free to tell everybody.[/QUOTE]

Hi, 
thanks for the how to, but this steps seems only to work with the 32 bits driver....
Does anyone knows how to make the 64 bits drive to work?

thanks,
Roger

---

### Post by jamesrw on 2005-08-24
Roger,
worked fine on my 64bit, cept for the dmesg output errors:
```
[fglrx] Maximum main memory to use for locked dma buffers: 308 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
```

---

### Post by andlinux on 2005-08-29
I have the next problem now.

This is standing in the fglrx-install.log:
```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
Error:
kernel includes at /lib/modules/2.6.10-5-686/build/include do not match current kernel.
they are versioned as "2.6.10"
instead of "2.6.10-5-686".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
``` 

I already deleted the 2.6.10 kernel-header and if I want to delete the 2.6.10-5 kernel-header it want to remove the 2.6.10-5-686 also.

Then that symbolic link, how can I create that (this is maybe a stupid question) but if I go to the /usr/src/ directory I see there a file called "linux" and I open it I see something from bitkeeper. :s

How can I create a symbolic link ?

---

### Post by fragmental on 2005-08-29
[QUOTE=Jeezis]i think my card just isn't supported by the fglrx driver. it installed fine and i ran the fglrxconfig fine, but when i reboot x won't start. i guess i have to stick with the radeon driver and no 3d acceleration. i hate this graphics card! it's given me nothing but problems since day one! (it's an ati radeon 320m igp)[/QUOTE]

There are a lot of reasons why X won't start.  One thing you can try is to use your old xorg.conf and simply change the ati(or radeon) line to fglrx.  After I installed my system wouldn't boot into X because I had the mouse and keyboard configured incorrectly.  Check the Xorg.0.log(sp?) to see what it says.

[QUOTE=andlinux]

How can I create a symbolic link ?[/QUOTE]

Created symbolic link by typing "ln -s" in the console with the name of the directory or file and then the name of the link....for example "ln -s linux-2.6.10 linux".  Type "ln --help" for more information. I might have the source and output backwards.

---

### Post by fragmental on 2005-08-29
[QUOTE=Cobra78]I've retried the driver installation, now i get this error

[http://paste.ubuntulinux.nl/1574](http://paste.ubuntulinux.nl/1574)

Can someone help me?[/QUOTE]

Try my troubleshooting tip above.  It might not work but it's worth a shot.

---

### Post by ManLord on 2005-08-30
I have a problem after installing these drivers, all my fonts has been scaled up like 3-4 steps or something. Why is this? Does it have something to do with dpi? Maybe the installer changed the dpi to a lower value?

Please help me, sure I can adjust every font settings in every program, but not all programs do have that setting. and the setting in Kcontrol does not affect all.

---

### Post by fragmental on 2005-09-09
[QUOTE=fragmental]Hey hey! I took my own advice and rebooted after that last step.  After that everything works like a charm.  I feel like dancing.

So, I'm going to rewrite the howto.

The unnoficial ATI ubuntu howto:

1)If you have installed the drivers through synaptic or apt-get, uninstall them using apt-get or synaptic(or kynaptic).
2) Download the 50MB(!) installer from ATI ([http://www2.ati.com/drivers/linux/a....16.20-i386.run](http://www2.ati.com/drivers/linux/a....16.20-i386.run))
3) check that you have your kernel headers in /usr/src/linux-headers-<version> and that /usr/src/linux is a symbolic link to that directory. This is needed to compile the fglrx kernel module.
3.1)If you don't have the headers get them by finding the package in synaptic called "linux-headers-(the name you got from uname -r)".  Then "ln -s /usr/src/linux-headers<version> /usr/src/linux".
4) change to single user mode via "sudo telinit 1", this will drop you to the console.
5) start the installer as root: "sudo sh ./ati-driver-installer-xxxxx"
6) most people can just accept the defaults in the installer (just hit enter at each screen) until the driver starts installation.
7) wait for installation to finish (shouldn't take too long, 30sec at most maybe).
8) run "sudo fglrxconfig" to generate your /etc/X11/xorg.conf file or simply change "radeon" to "fglrx" in your Device section if it exists already.  It might be a good idea to generate one even if you have one already just to see how they are different.  Make sure you don't copy over the original!
9.)reboot (I recommend a reboot, even though it is technically not necessary, as I've hit problems before when not rebooting).

Troubleshooting:
Direct Rendering doesn't work:
Try "ls -l /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko".  It should say the same date as the date you ran the ati driver installer. If not you will have to copy the fglrx driver from /lib/modules/fglrx/.  First rename or delete /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko and then "sudo cp /lib/modules/fglrx/fglrx.(kernel version).ko /lib/modules/(kernel version)/kernel/drivers/video/fglrx.ko".  Then, make sure you REBOOT.

Direct Rendering still doesn't work:  Yeah...that happens.  Check [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88) and search the rage3d forum and google for the ati linux howto and search this forum.  Someone may have had one of your problems already.  If you find a solution feel free to tell everybody.[/QUOTE]


I missed a part, sort of.  You might need the build tools...like gcc.  You can get build-essentials, but you might not need build-essentials specifically, but it has all the other stuff you need, I think.

---

### Post by fragmental on 2005-09-09
[QUOTE=fragmental]I missed a part, sort of.  You might need the build tools...like gcc.  You can get build-essentials, but you might not need build-essentials specifically, but it has all the other stuff you need, I think.[/QUOTE]
 I missed another step!  Before you try to install the ati drivers you must first uninstall the "nvidia-kernel-common" package.  That should also uninstall the "linux-restricted-modules" package which will interfere with the fglrx install.

---

### Post by elfurbe on 2005-09-11
I'm trying to install this in Breezy, and I'm having a heck of a time.  It's not building the kernel module, for whatever reason.  I followed the steps above, and I keep getting errors during the module build portion of the installer.

Contents of /usr/share/fglrx/fglrx-install.log:
```

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

```

I'm not sure which readme they want me to consult here.

Anyone got this going on Breezy?

---

### Post by fragmental on 2005-09-11
[QUOTE=elfurbe]I'm trying to install this in Breezy, and I'm having a heck of a time.  It's not building the kernel module, for whatever reason.  I followed the steps above, and I keep getting errors during the module build portion of the installer.

Contents of /usr/share/fglrx/fglrx-install.log:
```

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

```

I'm not sure which readme they want me to consult here.

Anyone got this going on Breezy?[/QUOTE]

Do you have the kernel headers and the build environment?

makes sure "nvidia-kernel-common" is uninstalled and "build-essentials" is installed as well as installing "linux-headers-(the name you got from uname -r)". Then "ln -s /usr/src/linux-headers<version> /usr/src/linux".

---

### Post by elfurbe on 2005-09-12
Alright, I had the wrong kernel headers installed, got that fixed, and it built the module, though it didn't copy it over.  So I copied it manually to drivers/video for the kernel, then rebooted and did an lsmod, and it wasn't there.  So I switched to singleuser, insmoded the fglrx.ko and did lsmod and it showed fglrx and agpgart, so I did telinit 3 to restart multiuser and when X loaded, I popped up a terminal and did glxgears, and got the error:
xlib: extension "XFree86-DRI" missing on display ":0.0"

Same error when I run fglrxinfo.

So, now I have two concerns.  One, why isn't fglrx.ko loading by default when I boot, and two, why isn't dri working?

EDIT:
More interesting infos:

First, there's a bug about this in Ubuntu's bugzilla:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=14383]("http://bugzilla.ubuntu.com/show_bug.cgi?id=14383")

Second, there's a guy that got DRI working in this thread:
[http://www.ubuntuforums.org/showthread.php?p=339627#post339627]("http://www.ubuntuforums.org/showthread.php?p=339627#post339627")

I tried his fix, and I no longer get the DRI errors, but glxgears is still choppy as all heck, so I don't know if it's working properly or not.

---

### Post by fragmental on 2005-09-13
[QUOTE=elfurbe]Alright, I had the wrong kernel headers installed, got that fixed, and it built the module, though it didn't copy it over.  So I copied it manually to drivers/video for the kernel, then rebooted and did an lsmod, and it wasn't there.  So I switched to singleuser, insmoded the fglrx.ko and did lsmod and it showed fglrx and agpgart, so I did telinit 3 to restart multiuser and when X loaded, I popped up a terminal and did glxgears, and got the error:
xlib: extension "XFree86-DRI" missing on display ":0.0"

Same error when I run fglrxinfo.

So, now I have two concerns.  One, why isn't fglrx.ko loading by default when I boot, and two, why isn't dri working?

EDIT:
More interesting infos:

First, there's a bug about this in Ubuntu's bugzilla:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=14383]("http://bugzilla.ubuntu.com/show_bug.cgi?id=14383")

Second, there's a guy that got DRI working in this thread:
[http://www.ubuntuforums.org/showthread.php?p=339627#post339627]("http://www.ubuntuforums.org/showthread.php?p=339627#post339627")

I tried his fix, and I no longer get the DRI errors, but glxgears is still choppy as all heck, so I don't know if it's working properly or not.[/QUOTE]

That looks like a breezy bug.  Are you using breezy?

Does fgl_glxgears work?  Does glxinfo say that that direct rendering is enabled?  Does fglrxinfo say ATI?  Does dmesg or xorg.0.log have any errors?

If fglrx.ko is not loading, dmesg might tell you why. If dmesg doesn't say anything, then it must not be looking for it correctly. A reinstall might be in order.

---

### Post by mlomker on 2005-09-13
[QUOTE=elfurbe]xlib: extension "XFree86-DRI" missing on display ":0.0"
[/QUOTE]

Do you, by chance, have a laptop with a Samsung LCD display?  This is a known bug and you'll want to roll back to the older driver.  They made some changes to how the driver queries the display for information and it breaks with certain displays.

There's a thread on the rage3d.com forums.

---

### Post by _cell on 2005-09-17
Has enyone met anything like this while building kernel module?
I'm kinda newbie to Linux and I even on't know where to dig now... 
Please, help 
> zion@ubuntu:/lib/modules/fglrx/build_mod$ sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule for building target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [kmod_build] Error 2
build failed with return value 2

---

### Post by LeLaulau on 2005-09-29
Hello,

I think, I've a problem while upgrading from hoary to breezy. I've searched all the threads in the forum (how there are a lot!) and didn't found my answer.

My problem is with the x-server. apt told me that
```
Paramétrage de xfree86-common (6.8.2-10.1) ...
xfree86-common postinst warning: /usr/bin/X11 symbolic link points to wrong
   location ../bin
Analyzing /usr/bin/X11:
drwxr-xr-x  13 root root 4096 2005-09-29 00:12 /usr
drwxr-xr-x  2 root root 32768 2005-09-29 10:53 /usr/bin
lrwxrwxrwx  1 root root 6 2005-09-28 23:29 /usr/bin/X11 -> ../bin
Analyzing ../bin:
drwxr-xr-x  21 root root 4096 2005-09-29 00:44 /..
drwxr-xr-x  2 root root 4096 2005-09-29 00:12 /../bin
Searching for overlapping packages...
The following packages appear to have file overlaps with the XFree86 packages;
these packages are either very old, or in violation of Debian Policy.  Try
upgrading each of these packages to the latest available version if possible:
for example, with the command "apt-get install".  If no newer version of a
package is available, you will have to remove it; for example, with the command
"apt-get remove".  If even the latest available version of the package has
this file overlap, please file a bug against that package with the Debian Bug
Tracking System.  You may want to refer the package maintainer to section 12.8
of the Debian Policy manual.
The overlapping packages are:
x-common
xfree86-common postinst error: bad symbolic links on system
dpkg : erreur de traitement de xfree86-common (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 74
Des erreurs ont été rencontrées pendant l'exécution :
 xfree86-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I installed on the Hoary the ATI driver from the executable (not from the rpm). and I didn't uninstall anything.

I've already tried to install the new package for fglrx but it doesn't change anything. I tried dpkg-reconfigure xserver-xorg.

Can anyone help me to handle this.... A pc without x-server, it's not so interesting :)

---

### Post by fragmental on 2005-09-29
[QUOTE=LeLaulau]Hello,
I think, I've a problem while upgrading from hoary to breezy. I've searched all the threads in the forum (how there are a lot!) and didn't found my answer.
My problem is with the x-server. apt told me that
```
Paramétrage de xfree86-common (6.8.2-10.1) ...
xfree86-common postinst warning: /usr/bin/X11 symbolic link points to wrong
location ../bin
Analyzing /usr/bin/X11:
drwxr-xr-x  13 root root 4096 2005-09-29 00:12 /usr
drwxr-xr-x  2 root root 32768 2005-09-29 10:53 /usr/bin
lrwxrwxrwx  1 root root 6 2005-09-28 23:29 /usr/bin/X11 -> ../bin
Analyzing ../bin:
drwxr-xr-x  21 root root 4096 2005-09-29 00:44 /..
drwxr-xr-x  2 root root 4096 2005-09-29 00:12 /../bin
Searching for overlapping packages...
The following packages appear to have file overlaps with the XFree86 packages;
these packages are either very old, or in violation of Debian Policy.  Try
upgrading each of these packages to the latest available version if possible:
for example, with the command "apt-get install".  If no newer version of a
package is available, you will have to remove it; for example, with the command
"apt-get remove".  If even the latest available version of the package has
this file overlap, please file a bug against that package with the Debian Bug
Tracking System.  You may want to refer the package maintainer to section 12.8
of the Debian Policy manual.
The overlapping packages are:
x-common
xfree86-common postinst error: bad symbolic links on system
dpkg : erreur de traitement de xfree86-common (--configure) :
le sous-processus post-installation script a retourné une erreur de sortie d'état 74
Des erreurs ont été rencontrées pendant l'exécution :
xfree86-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I installed on the Hoary the ATI driver from the executable (not from the rpm). and I didn't uninstall anything.
I've already tried to install the new package for fglrx but it doesn't change anything. I tried dpkg-reconfigure xserver-xorg.
Can anyone help me to handle this.... A pc without x-server, it's not so interesting :)[/QUOTE]


I don't think that breezy is supported by the installer.  Maybe the package would still work, but you might need to recompile the kernel driver.  This looks like it might be an issue unrelated with the ATI drivers, but if it is, you might just try uninstalling the ATI drivers and then see if you still get the error.  you might also try uninstalling the x-server and reinstalling.  I don't know if dpkg-reconfigure essentially does the same thing, but it's worth a try.

---

### Post by LeLaulau on 2005-09-29
That was indirectly my question: how can I uninstall the driver of the ATI installer?

I have uninstall xfree86 and it seem ok with xorg.... But I'm not at home and cannot test it really (with a ssh -X it doesn't work).

---

