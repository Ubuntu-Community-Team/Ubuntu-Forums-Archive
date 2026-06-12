---
title: "Radeon Xpress 200G problems"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by revx on 2007-12-02
I'm unable to get a secondary display up and running on my Compaq R4000 laptop (x86-64).  I've used the open-source drivers with a single display, but it won't even start with fglrx.  Every time xorg starts with fglrx as a driver, I get the following on the tail of my xorg log:

```

Backtrace:
0: /usr/X11R6/bin/Xorg(xf86SigHandler+0x6d) [0x48670d]
1: /lib/libc.so.6 [0x2ac404bdc7d0]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlDalHelperValidateModeFromDAL+0x549) [0x2ac4063b14e9]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x2ac406391dae]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x8b3) [0x2ac40638d4b3]
5: /usr/X11R6/bin/Xorg(InitOutput+0x9bd) [0x4691dd]
6: /usr/X11R6/bin/Xorg(main+0x275) [0x439d65]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2ac404bc8b44]
8: /usr/X11R6/bin/Xorg(FontFileCompleteXLFD+0x231) [0x439249]

```

I'm using Ubuntu 7.10 on this machine, and here's the lspci dump of the card:
```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 3085
        Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at b0120000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2

```

The complete log is here:
```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Stella 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.9.log", Time: Sun Dec  2 17:04:51 2007
(++) Using config file: "/tmp/dcg-jVlIPf5652/testserver.config"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
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
(II) Loader magic: 0x7cd8a0
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
(--) using VT number 8

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 103c,3085 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 1002,5a36 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 1002,4374 card 1002,4374 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1002,4375 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1002,4373 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,3085 rev 10 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,3085 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,3085 rev 01 class 04,01,00 hdr 80
(II) PCI: 00:14:6: chip 1002,4378 card 103c,3085 rev 01 class 07,03,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5955 card 103c,3085 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 104c,8023 card 103c,3085 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:02:0: chip 14e4,4318 card 103c,1355 rev 02 class 02,80,00 hdr 00
(II) PCI: 03:04:0: chip 104c,8031 card a400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 03:04:3: chip 104c,8033 card 103c,3085 rev 00 class 01,80,00 hdr 80
(II) PCI: 03:04:4: chip 104c,8034 card 103c,3085 rev 00 class 08,05,00 hdr 80
(II) PCI: 03:06:0: chip 10ec,8139 card 103c,3085 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb0100000 - 0xb01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,7), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xb0200000 - 0xb02fffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:4:0), (3,4,7), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[1] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) rev 0, Mem @ 0xc0000000/28, 0xb0100000/16, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[1] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[2] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[3] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[4] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[5] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[6] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[7] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[8] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[9] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[10] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[11] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[12] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[13] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[14] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[1] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[2] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[3] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[4] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[5] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[6] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[7] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[8] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[9] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[10] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[11] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[12] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[13] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[14] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
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
	[4] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[5] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[6] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[7] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[8] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[9] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[10] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[11] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[12] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[13] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[14] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[15] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[16] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[17] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[18] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:40
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(--) Chipset Supported AMD Graphics Processor (0x5955) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[5] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[6] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[7] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[8] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[9] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[10] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[11] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[12] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[13] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[14] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[15] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[16] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[17] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[18] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f3950
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[5] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[6] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[7] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[8] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[9] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[10] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[11] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[12] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[13] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[14] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[15] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[16] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[17] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[18] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[26] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[32] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3085)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xb0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON Xpress 200G Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information. 
(II) fglrx(0): Connected Display2: LCD on internal LVDS [lvds]
(II) fglrx(0): Display2 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) fglrx(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0):  LGPhilipsLCD
(II) fglrx(0):  LP154W01-TLA2
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00320c000000000000
(II) fglrx(0): 	000f0102802115780a0f109758528828
(II) fglrx(0): 	23505400000001010101010101010101
(II) fglrx(0): 	010101010101d51b00a0502017303020
(II) fglrx(0): 	26002115100000190000000000000000
(II) fglrx(0): 	00000000000000000000000000fe004c
(II) fglrx(0): 	475068696c6970734c43440a000000fe
(II) fglrx(0): 	004c503135345730312d544c41320008
(II) fglrx(0): End of Display2 EDID data --------------------
(WW) fglrx(0): More than one displays are connected,so clone mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Secondary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 301/250MHz @ 60Hz [enable load balancing]
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 17 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1200 (pitch 0)
(**) fglrx(0):  Default mode "800x600@72": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600@72"   71.25  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "800x600@75": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600@75"   71.25  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "800x600@56": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600@56"   71.25  800 1088 1120 1440  600 702 708 823
(**) fglrx(0): *Mode "800x600@60": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600@60"   71.25  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "1280x800@75": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800@75"   71.25  1280 1328 1360 1440  800 802 808 823
(**) fglrx(0): *Mode "1280x800@60": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800@60"   71.25  1280 1328 1360 1440  800 802 808 823
(**) fglrx(0):  Default mode "1024x768": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.25  1024 1200 1232 1440  768 786 792 823
(**) fglrx(0):  Default mode "848x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.25  848 1112 1144 1440  480 642 648 823
(**) fglrx(0):  Default mode "720x576": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   71.25  720 1048 1080 1440  576 690 696 823
(**) fglrx(0):  Default mode "720x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.25  720 1048 1080 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x480": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.25  640 1008 1040 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x400": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.25  640 1008 1040 1440  400 602 608 823
(**) fglrx(0):  Default mode "640x350": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.25  640 1008 1040 1440  350 577 583 823
(**) fglrx(0):  Default mode "512x384": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.25  512 944 976 1440  384 594 600 823
(**) fglrx(0):  Default mode "400x300": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.25  400 888 920 1440  300 702 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.25  320 848 880 1440  240 642 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.2 MHz (scaled from 0.0 MHz), 49.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.25  320 848 880 1440  200 602 608 823 doublescan

Backtrace:
0: /usr/X11R6/bin/Xorg(xf86SigHandler+0x6d) [0x48670d]
1: /lib/libc.so.6 [0x2ac404bdc7d0]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlDalHelperValidateModeFromDAL+0x549) [0x2ac4063b14e9]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x2ac406391dae]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x8b3) [0x2ac40638d4b3]
5: /usr/X11R6/bin/Xorg(InitOutput+0x9bd) [0x4691dd]
6: /usr/X11R6/bin/Xorg(main+0x275) [0x439d65]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2ac404bc8b44]
8: /usr/X11R6/bin/Xorg(FontFileCompleteXLFD+0x231) [0x439249]

Fatal server error:
Caught signal 11.  Server aborting

```

Something keeps changing the xorg.conf in use so I could post that but it wouldn't be of much use as a result.  When I try starting x without gdm running, the whole machine dies and I must do a hard reset.  Any help on this issue would be appreciated.


Update:
When I use the 'radeon' driver I can set the display to 1280x800, but no secondary.  I'll mess with the clone options in a minute, but for now I find it odd that I must use the 'fallback terminal' session because gdm kills X if I use a normal gnome session.  I have firefox, gnome-terminal, and other apps running fine -- just not started from a gnome session :/

---

