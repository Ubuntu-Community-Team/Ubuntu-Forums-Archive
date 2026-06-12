---
title: "Nvidia XORG problem"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by sudobash on 2008-01-28
Hello About 2 weeks ago I decided to upgrade from 7.04 to 7.10 and didn't have any problems except I had to reconfigure my Nvidia driver and Xorg file... Anyways yesterday I decided to do a sudo apt-get update and then sudo apt-get upgrade and apparently it upgraded and installed quite a few files... well my X server crashed on me and I figured it would be the same deal... Just install the driver again and redo the xorg file... Well none of the drivers are working... I have tried the Nvidia-GLX, Nvidia-GLX-new, the actualy Nvidia Installer, and the Nvidia restricted driver... Anyways none of these worked (yes i tried nvidia-xconfig, custom config, and even starting with old and fresh xorg configs) nothing works, but I am not empty handed... Here is some info:

First off I have an AMD Athlon XP 2400+, 1 GB ram, Geforce FX 5200 256MB... 
Linux wisdom 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux

Here are some logs (xorg driver: nvidia not nv )

This one isn't too important because it is trying startx without the nvidia driver installed so I am going to leave the first part out
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.09  Fri Jan 11 15:31:25 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(EE) No drivers available.

Fatal server error:
no screens found

Notice the one above does not say 

(EE) Screen(s) found, but none have a usable configuration.

but instead says: 
Fatal server error:
no screens found

Here is the log with the older GLX driver:

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux wisdom 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 28 02:35:39 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL D1028L"
(**) |   |-->Device "nVidia Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01a4 card 0000,0000 rev b2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01ac card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ad card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01aa card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,01b2 card 10de,0c11 rev c3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,01b4 card 10de,0c11 rev c1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,01c2 card 10de,0c11 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:03:0: chip 10de,01c2 card 10de,0c11 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:04:0: chip 10de,01c3 card 1043,0c11 rev c2 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,01b0 card 1043,0c11 rev c2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,01b1 card 1043,8384 rev c2 class 04,01,00 hdr 80
(II) PCI: 00:08:0: chip 10de,01b8 card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,01bc card 10de,0c11 rev c3 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01b7 card 0000,0000 rev b2 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 01:07:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 01:07:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: 02:00:0: chip 10de,0322 card 196e,01ad rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge

(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge

(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge

(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcc800000 - 0xccffffff (0x800000) MX[B]
(II) PCI-to-PCI bridge

(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xcb000000 - 0xcc7fffff (0x1800000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xdfffffff (0x10100000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xcb000000/24, 0xd0000000/28, BIOS @ 0xcffe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[1] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[2] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[3] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[4] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[5] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[14] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[16] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[17] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[18] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[1] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[2] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[3] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[4] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[5] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[14] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[16] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[17] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[18] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[5] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[6] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[7] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[8] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[9] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[22] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[23] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[24] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000043gl
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9639
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9639  Mon Apr 16 20:21:54 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[5] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[6] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[7] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[8] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[9] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[22] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[23] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[24] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[5] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[6] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[7] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[8] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[9] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[23] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[25] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[26] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[27] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Here is the log with the new driver: 

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux wisdom 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 28 02:34:27 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL D1028L"
(**) |   |-->Device "nVidia Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01a4 card 0000,0000 rev b2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01ac card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ad card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01aa card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,01b2 card 10de,0c11 rev c3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,01b4 card 10de,0c11 rev c1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,01c2 card 10de,0c11 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:03:0: chip 10de,01c2 card 10de,0c11 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:04:0: chip 10de,01c3 card 1043,0c11 rev c2 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,01b0 card 1043,0c11 rev c2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,01b1 card 1043,8384 rev c2 class 04,01,00 hdr 80
(II) PCI: 00:08:0: chip 10de,01b8 card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,01bc card 10de,0c11 rev c3 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01b7 card 0000,0000 rev b2 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 01:07:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 01:07:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: 02:00:0: chip 10de,0322 card 196e,01ad rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge

(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge

(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge

(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcc800000 - 0xccffffff (0x800000) MX[B]
(II) PCI-to-PCI bridge

(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xcb000000 - 0xcc7fffff (0x1800000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xdfffffff (0x10100000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xcb000000/24, 0xd0000000/28, BIOS @ 0xcffe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[1] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[2] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[3] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[4] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[5] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[14] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[16] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[17] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[18] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[1] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[2] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[3] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[4] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[5] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[11] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[14] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[16] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[17] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[18] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[5] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[6] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[7] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[8] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[9] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[22] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[23] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[24] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000042gl
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[5] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[6] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[7] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[8] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[9] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[20] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[22] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[23] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[24] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcc800000 - 0xcc8000ff (0x100) MX[B]
	[5] -1	0	0xcd000000 - 0xcd000fff (0x1000) MX[B]
	[6] -1	0	0xcd800000 - 0xcd87ffff (0x80000) MX[B]
	[7] -1	0	0xce000000 - 0xce0003ff (0x400) MX[B]
	[8] -1	0	0xce800000 - 0xce800fff (0x1000) MX[B]
	[9] -1	0	0xcf000000 - 0xcf000fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xcffe0000 - 0xcfffffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[23] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d807 (0x8 IX[B]
	[25] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[26] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[27] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

notice it says (EE) Screen(s) found, but none have a usable configuration. 

Here is the Xorg config used for the above tests:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL D1028L"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "DELL D1028L"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

To me everything seems to be in place and should work... To get X when it crashes is replace the     Driver "nvidia" with     Driver  "nv" 
and X will pull up with no problem because it is the default driver... 
Can anyone help me out?

---

### Post by sudobash on 2008-01-28
anyone have any ideas?

---

### Post by Waldo2020 on 2008-01-28
Nvidia's drivers are seriously broken for some time now.
The issue appears to be broken EDID readout from the monitor/lcd.
All my resolutions were broken except 640x480: useless!
Finally after googling and reading here I was able to get
800x600 by have the driver completely ignore the EDID and 
I supplied my own setting. Still it stupidly tries all the mode
settings IT feels like rejecting all but 2, despite my modelines.
Finally, I turned on error level 5 logging  to get more details
and was able to get 1280x1024 by manually running startx as root.
I'd like to have a talk with the idiot that broke that driver, and from
the looks of it, thousands of other users, not only on Ubuntu but
every other flavour of Linux and BSD relying on this broken closed driver.

---

