---
title: "Intel 82945G/GZ occasional graphics issues"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by mrintegrity on 2007-09-19
At least twice since installing Ubuntu on this desktop pc, X has failed to start after booting. Here is the Xorg log, note the resource conflict messages - does this represent impending hardware failure or just a random Ubuntu bug?


```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux lina-desktop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 19 10:39:59 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "HIQ T91D"
(**) |   |-->Device "Intel Corporation 82945G/GZ Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1043,817a rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2772 card 1043,817a rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2776 card 1043,817a rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,81f6 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,8179 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,8179 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1043,8179 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1043,8179 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1043,2601 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1043,8179 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:02:0: chip 1106,3044 card 1043,81fe rev c0 class 0c,00,10 hdr 00
(II) PCI: 02:00:0: chip 10ec,8168 card 1043,81aa rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[2] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xdfc80000/19, 0xc0000000/28, 0xdfd80000/18, I/O @ 0xb800/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xdfd00000/19
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
(II) Active PCI resource ranges:
	[0] -1	0	0xdfeff800 - 0xdfefffff (0x800) MX[B]
	[1] -1	0	0xdfdffc00 - 0xdfdfffff (0x400) MX[B]
	[2] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[3] -1	0	0xdfd00000 - 0xdfd7ffff (0x80000) MX[B](B)
	[4] -1	0	0xdfd80000 - 0xdfdbffff (0x40000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xdfc80000 - 0xdfcfffff (0x80000) MX[B](B)
	[7] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[8] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[9] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[10] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[12] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[13] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[22] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x0000e800 - 0xdfffffff (0xdfff1800) MX[B]
	[1] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfeff800 - 0xdfefffff (0x800) MX[B]
	[1] -1	0	0xdfdffc00 - 0xdfdfffff (0x400) MX[B]
	[2] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[3] -1	0	0xdfd00000 - 0xdfd7ffff (0x80000) MX[B](B)
	[4] -1	0	0xdfd80000 - 0xdfdbffff (0x40000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xdfc80000 - 0xdfcfffff (0x80000) MX[B](B)
	[7] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[8] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[9] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[10] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[12] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[13] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[22] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x0000e800 - 0xdfffffff (0xdfff1800) MX[B]
	[1] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
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
	[4] -1	0	0xdfeff800 - 0xdfefffff (0x800) MX[B]
	[5] -1	0	0xdfdffc00 - 0xdfdfffff (0x400) MX[B]
	[6] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[7] -1	0	0xdfd00000 - 0xdfd7ffff (0x80000) MX[B](B)
	[8] -1	0	0xdfd80000 - 0xdfdbffff (0x40000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdfc80000 - 0xdfcfffff (0x80000) MX[B](B)
	[11] -1	0	0x0000e800 - 0xdfffffff (0xdfff1800) MX[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[15] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[19] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B](B)
	[31] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.7.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfeff800 - 0xdfefffff (0x800) MX[B]
	[5] -1	0	0xdfdffc00 - 0xdfdfffff (0x400) MX[B]
	[6] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[7] -1	0	0xdfd00000 - 0xdfd7ffff (0x80000) MX[B](B)
	[8] -1	0	0xdfd80000 - 0xdfdbffff (0x40000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdfc80000 - 0xdfcfffff (0x80000) MX[B](B)
	[11] -1	0	0x0000e800 - 0xdfffffff (0xdfff1800) MX[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[15] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[19] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B](B)
	[31] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
(II) Found conflict at: 0xbffff
(II) Found conflict at: 0xb7fff
(II) Found conflict at: 0xaffff
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfeff800 - 0xdfefffff (0x800) MX[B]
	[5] -1	0	0xdfdffc00 - 0xdfdfffff (0x400) MX[B]
	[6] -1	0	0xdfdf8000 - 0xdfdfbfff (0x4000) MX[B]
	[7] -1	0	0xdfd00000 - 0xdfd7ffff (0x80000) MX[B](B)
	[8] -1	0	0xdfd80000 - 0xdfdbffff (0x40000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdfc80000 - 0xdfcfffff (0x80000) MX[B](B)
	[11] -1	0	0x0000e800 - 0xdfffffff (0xdfff1800) MX[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[15] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x0000c480 - 0x0000c483 (0x4) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[19] -1	0	0x0000c880 - 0x0000c883 (0x4) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc07 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000c080 - 0x0000c09f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[29] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B](B)
	[31] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//i810_drv.so [0xb7df6c53]
3: /usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
4: /usr/X11R6/bin/X(main+0x27b) [0x807456b]
5: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0x4423cebc]
6: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting
```

---

