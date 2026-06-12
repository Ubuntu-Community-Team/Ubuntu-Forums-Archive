---
title: "[SOLVED] nvidia driver gives no signal but nv works fine"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by skroops on 2007-12-27
I can't get the nvidia restricted driver to work on my 7600GS with 40" LCD HDTV running Gutsy amd64.

the nv driver works and I have no problems in windows mce.  As soon as I enable the restricted driver, on restart, the splash screen appears and when it completes loading the monitor loses signal input.

My card has two outputs, one is VGA and the other is DVI.  There is no integrated video.  I am connected on the VGA.  I've tried using "Option UseDisplayDevice "CRT"" in the screen section of my xorg.conf, and that hasn't done anything.  I'm sure that X is still loading because I hear the ubuntu start-up sound but there is just no display.

Here is my xorg.conf and Xorg.0.log
```
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux cecil 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 27 13:57:06 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G70 [GeForce 7600 GS]"
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
(**) Extension "Composite" is enabled
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
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,04,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0392 card 3842,c549 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 11ab,4362 card 1148,4340 rev 20 class 02,00,00 hdr 00
(II) PCI: 05:06:0: chip 3388,0021 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 05:07:0: chip 11ab,1faa card 1385,6b00 rev 03 class 02,00,00 hdr 00
(II) PCI: 06:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 06:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,6), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xcd000000 - 0xcd0fffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xc9ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xca000000 - 0xccffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (5:6:0), (5,6,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xca000000/24, 0xb0000000/28, 0xcb000000/24, I/O @ 0x9000/7
(--) PCI: (6:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xc0000000/26
(--) PCI: (6:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xc4000000/26
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
	[0] -1	0	0xcd010000 - 0xcd01ffff (0x10000) MX[B]
	[1] -1	0	0xcd000000 - 0xcd00ffff (0x10000) MX[B]
	[2] -1	0	0xc9000000 - 0xc9003fff (0x4000) MX[B]
	[3] -1	0	0xcd100000 - 0xcd100fff (0x1000) MX[B]
	[4] -1	0	0xcd101000 - 0xcd101fff (0x1000) MX[B]
	[5] -1	0	0xcd102000 - 0xcd102fff (0x1000) MX[B]
	[6] -1	0	0xcd103000 - 0xcd103fff (0x1000) MX[B]
	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[8] -1	0	0xcd104000 - 0xcd104fff (0x1000) MX[B]
	[9] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xca000000 - 0xcaffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[18] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[19] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[20] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[29] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[30] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[32] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcd010000 - 0xcd01ffff (0x10000) MX[B]
	[1] -1	0	0xcd000000 - 0xcd00ffff (0x10000) MX[B]
	[2] -1	0	0xc9000000 - 0xc9003fff (0x4000) MX[B]
	[3] -1	0	0xcd100000 - 0xcd100fff (0x1000) MX[B]
	[4] -1	0	0xcd101000 - 0xcd101fff (0x1000) MX[B]
	[5] -1	0	0xcd102000 - 0xcd102fff (0x1000) MX[B]
	[6] -1	0	0xcd103000 - 0xcd103fff (0x1000) MX[B]
	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[8] -1	0	0xcd104000 - 0xcd104fff (0x1000) MX[B]
	[9] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xca000000 - 0xcaffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[17] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[18] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[19] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[20] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[29] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[30] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[32] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
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
	[4] -1	0	0xcd010000 - 0xcd01ffff (0x10000) MX[B]
	[5] -1	0	0xcd000000 - 0xcd00ffff (0x10000) MX[B]
	[6] -1	0	0xc9000000 - 0xc9003fff (0x4000) MX[B]
	[7] -1	0	0xcd100000 - 0xcd100fff (0x1000) MX[B]
	[8] -1	0	0xcd101000 - 0xcd101fff (0x1000) MX[B]
	[9] -1	0	0xcd102000 - 0xcd102fff (0x1000) MX[B]
	[10] -1	0	0xcd103000 - 0xcd103fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xcd104000 - 0xcd104fff (0x1000) MX[B]
	[13] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xca000000 - 0xcaffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[23] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[24] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[25] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[26] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[35] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[36] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[37] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[38] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.07  Thu Dec 13 19:15:29 PST 2007
(II) Loading extension GLX
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
(II) NVIDIA dlloader X Driver  169.07  Thu Dec 13 18:36:37 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
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
	[4] -1	0	0xcd010000 - 0xcd01ffff (0x10000) MX[B]
	[5] -1	0	0xcd000000 - 0xcd00ffff (0x10000) MX[B]
	[6] -1	0	0xc9000000 - 0xc9003fff (0x4000) MX[B]
	[7] -1	0	0xcd100000 - 0xcd100fff (0x1000) MX[B]
	[8] -1	0	0xcd101000 - 0xcd101fff (0x1000) MX[B]
	[9] -1	0	0xcd102000 - 0xcd102fff (0x1000) MX[B]
	[10] -1	0	0xcd103000 - 0xcd103fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xcd104000 - 0xcd104fff (0x1000) MX[B]
	[13] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xca000000 - 0xcaffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[23] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[24] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[25] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[26] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[35] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[36] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[37] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[38] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcd010000 - 0xcd01ffff (0x10000) MX[B]
	[5] -1	0	0xcd000000 - 0xcd00ffff (0x10000) MX[B]
	[6] -1	0	0xc9000000 - 0xc9003fff (0x4000) MX[B]
	[7] -1	0	0xcd100000 - 0xcd100fff (0x1000) MX[B]
	[8] -1	0	0xcd101000 - 0xcd101fff (0x1000) MX[B]
	[9] -1	0	0xcd102000 - 0xcd102fff (0x1000) MX[B]
	[10] -1	0	0xcd103000 - 0xcd103fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xcd104000 - 0xcd104fff (0x1000) MX[B]
	[13] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xca000000 - 0xcaffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[36] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[37] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[38] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[39] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[40] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[41] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.03
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     Sony KDL-40S2000 (CRT-1)
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Sony KDL-40S2000 (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1360x768"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1360 x 768
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcd010000 - 0xcd01ffff (0x10000) MX[B]
	[5] -1	0	0xcd000000 - 0xcd00ffff (0x10000) MX[B]
	[6] -1	0	0xc9000000 - 0xc9003fff (0x4000) MX[B]
	[7] -1	0	0xcd100000 - 0xcd100fff (0x1000) MX[B]
	[8] -1	0	0xcd101000 - 0xcd101fff (0x1000) MX[B]
	[9] -1	0	0xcd102000 - 0xcd102fff (0x1000) MX[B]
	[10] -1	0	0xcd103000 - 0xcd103fff (0x1000) MX[B]
	[11] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[12] -1	0	0xcd104000 - 0xcd104fff (0x1000) MX[B]
	[13] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xcb000000 - 0xcbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xca000000 - 0xcaffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[36] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[37] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[38] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[39] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[40] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[41] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1360x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

I don't see any significant errors in the log, so it seems as far as X is concerned everything is working fine, I just can't see it.

---

### Post by Yellow Pasque on 2007-12-27
Just an observation:
> (II) NVIDIA(0): Setting mode "1360x768"
> SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
Shouldn't you add 1360x768 as a valid mode?

---

### Post by skroops on 2007-12-27
I've solved the problem.  Nvidia for some reason was defaulting the DVI out on my graphics card, for whatever reason.  I hooked up a dvi-to-vga converter and then configure nvidia-settings.  This is probably a bug because if you don't have a way to connect to the DVI port on the card there really isn't anything I could figure out to do about it.  But anyway that's what worked.

---

