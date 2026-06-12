---
title: "HDMI -&gt; PLASMA no display"
date: 2008-09-11
forum: General Help
---

### Post by FloBo2067 on 2008-09-11
Hi,

ich habe nun Mythbuntu 8.04 installiert und den fglrx über envy. Folgende xorg.conf habe ich nun erstellt. Xorg erkennt auch 1080p Auflösungen, aber ich bekomme kein Bild auf meinem TV.

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection


Section "ServerFlags"
Option "AIGLX" "off"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Xorg.0.log

```

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 11 18:29:48 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(**) Option "AIGLX" "off"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,7910 card 1043,826d rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,7912 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1002,7917 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 1043,81ef rev 00 class 01,06,01 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 1043,81ef rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 1043,81ef rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 1043,81ef rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 1043,81ef rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 1043,81ef rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 1043,81ef rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1043,81ef rev 14 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 1043,81ef rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1043,8249 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 1043,81ef rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,791e card 1043,826d rev 00 class 03,00,00 hdr 80
(II) PCI: 01:05:2: chip 1002,7919 card 1002,7919 rev 00 class 04,03,00 hdr 00
(II) PCI: 02:00:0: chip 10ec,8168 card 1043,81aa rev 01 class 02,00,00 hdr 00
(II) PCI: 03:06:0: chip 1131,7146 card 1894,0014 rev 01 class 04,80,00 hdr 00
(II) PCI: 03:07:0: chip 1106,3044 card 1043,81fe rev c0 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdbfffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:7:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc Radeon X1200 Series rev 0, Mem @ 0xd0000000/28, 0xfdbe0000/16, 0xfda00000/20, I/O @ 0xde00/8
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
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff1ff (0x200) MX[B]
	[2] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[3] -1	0	0xfdbfc000 - 0xfdbfffff (0x4000) MX[B]
	[4] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[5] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[12] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B](B)
	[13] -1	0	0xfdbe0000 - 0xfdbeffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[16] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[17] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[23] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[25] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[28] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff1ff (0x200) MX[B]
	[2] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[3] -1	0	0xfdbfc000 - 0xfdbfffff (0x4000) MX[B]
	[4] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[5] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[6] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[7] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[12] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B](B)
	[13] -1	0	0xfdbe0000 - 0xfdbeffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[16] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[17] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[23] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[25] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[28] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
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
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff1ff (0x200) MX[B]
	[6] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[7] -1	0	0xfdbfc000 - 0xfdbfffff (0x4000) MX[B]
	[8] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[9] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[10] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[11] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[12] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[13] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[14] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[15] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[16] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B](B)
	[17] -1	0	0xfdbe0000 - 0xfdbeffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[23] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[30] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[31] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[32] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[33] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[34] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "extmod"
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.50.3
	Module class: X.Org Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.50.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.501                    
(II) ATI Proprietary Linux Driver Build Date: Jun  2 2008 22:47:36
(--) Chipset Supported AMD Graphics Processor (0x791E) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff1ff (0x200) MX[B]
	[6] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[7] -1	0	0xfdbfc000 - 0xfdbfffff (0x4000) MX[B]
	[8] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[9] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[10] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[11] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[12] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[13] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[14] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[15] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[16] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B](B)
	[17] -1	0	0xfdbe0000 - 0xfdbeffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[23] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[30] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[31] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[32] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[33] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[34] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7f8630
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff1ff (0x200) MX[B]
	[6] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[7] -1	0	0xfdbfc000 - 0xfdbfffff (0x4000) MX[B]
	[8] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[9] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[10] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[11] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[12] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[13] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[14] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[15] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[16] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B](B)
	[17] -1	0	0xfdbe0000 - 0xfdbeffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[25] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[26] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[32] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[34] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[35] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[36] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[37] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon X1200 Series" (Chipset = 0x791e)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x826d)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfdbe0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.55
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS690
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.50.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0x60000000, MCFBSize = 0x20000000)
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: DFP on external TMDS [tmds2]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MEI  Model: a064  Serial#: 424
(II) fglrx(0): Year: 2007  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.345   greenX: 0.291 greenY: 0.635
(II) fglrx(0): blueX: 0.163 blueY: 0.093   whiteX: 0.288 whiteY: 0.296
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 74.2 MHz   Image Size:  1434 x 806 mm
(II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 74.2 MHz   Image Size:  1434 x 806 mm
(II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) fglrx(0): Monitor name: PANASONIC-TV
(II) fglrx(0): Ranges: V min: 23  V max: 61 Hz, H min: 15  H max: 68 kHz, PixClock max 150 MHz
(II) fglrx(0): Number of EDID sections to follow: 1
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0034a964a0a8010000
(II) fglrx(0): 	2f110103800000780adaffa3584aa229
(II) fglrx(0): 	17494b00000001010101010101010101
(II) fglrx(0): 	010101010101011d80d0721c1620102c
(II) fglrx(0): 	25809a265300009e011d8018711c1620
(II) fglrx(0): 	582c25009a265300009e000000fc0050
(II) fglrx(0): 	414e41534f4e49432d54560a000000fd
(II) fglrx(0): 	00173d0f440f000a2020202020200104
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on external TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 27 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1080 (pitch 0)
(**) fglrx(0): *Mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 67.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 (67.5 kHz)
(**) fglrx(0):  Default mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 56.2 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 (56.2 kHz)
(**) fglrx(0):  Default mode "1920x1080": 74.2 MHz (scaled from 0.0 MHz), 33.8 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace (33.8 kHz)
(**) fglrx(0):  Default mode "1920x1080": 74.2 MHz (scaled from 0.0 MHz), 28.1 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace (28.1 kHz)
(**) fglrx(0):  Default mode "1920x1080": 74.2 MHz (scaled from 0.0 MHz), 27.0 kHz, 24.0 Hz
(II) fglrx(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 (27.0 kHz)
(**) fglrx(0): *Mode "1776x1000": 147.1 MHz (scaled from 0.0 MHz), 62.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1776x1000"x60.0  147.05  1776 1880 2072 2368  1000 1001 1004 1035 +hsync (62.1 kHz)
(**) fglrx(0):  Default mode "1776x1000": 69.2 MHz (scaled from 0.0 MHz), 31.1 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"x30.0   69.18  1776 1824 2000 2224  1000 1001 1004 1037 interlace +hsync (31.1 kHz)
(**) fglrx(0): *Mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +vsync (65.3 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 (45.0 kHz)
(**) fglrx(0):  Default mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 37.5 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 (37.5 kHz)
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1152x648": 59.9 MHz (scaled from 0.0 MHz), 40.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync (40.3 kHz)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0): *Mode "720x576": 27.0 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 +hsync +vsync (31.2 kHz)
(**) fglrx(0): *Mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   27.00  720 736 798 858  480 489 495 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(++) fglrx(0): DPI set to (100, 100)
(--) fglrx(0): Virtual size is 1920x1080 (pitch 1920)
(**) fglrx(0): *Mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 67.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 (67.5 kHz)
(**) fglrx(0):  Default mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 56.2 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 (56.2 kHz)
(**) fglrx(0):  Default mode "1920x1080": 74.2 MHz (scaled from 0.0 MHz), 33.8 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace (33.8 kHz)
(**) fglrx(0):  Default mode "1920x1080": 74.2 MHz (scaled from 0.0 MHz), 28.1 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace (28.1 kHz)
(**) fglrx(0):  Default mode "1920x1080": 74.2 MHz (scaled from 0.0 MHz), 27.0 kHz, 24.0 Hz
(II) fglrx(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 (27.0 kHz)
(**) fglrx(0): *Mode "1776x1000": 147.1 MHz (scaled from 0.0 MHz), 62.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1776x1000"x60.0  147.05  1776 1880 2072 2368  1000 1001 1004 1035 +hsync (62.1 kHz)
(**) fglrx(0):  Default mode "1776x1000": 69.2 MHz (scaled from 0.0 MHz), 31.1 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"x30.0   69.18  1776 1824 2000 2224  1000 1001 1004 1037 interlace +hsync (31.1 kHz)
(**) fglrx(0): *Mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +vsync (65.3 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 (45.0 kHz)
(**) fglrx(0):  Default mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 37.5 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 (37.5 kHz)
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1152x648": 59.9 MHz (scaled from 0.0 MHz), 40.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync (40.3 kHz)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0): *Mode "720x576": 27.0 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 +hsync +vsync (31.2 kHz)
(**) fglrx(0): *Mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   27.00  720 736 798 858  480 489 495 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000b
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
	[1] 0	0	0xfdbe0000 - 0xfdbeffff (0x10000) MX[B]
	[2] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[8] -1	0	0xfdeff000 - 0xfdeff1ff (0x200) MX[B]
	[9] -1	0	0xfdfff000 - 0xfdffffff (0x1000) MX[B]
	[10] -1	0	0xfdbfc000 - 0xfdbfffff (0x4000) MX[B]
	[11] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[12] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[13] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[14] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[15] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[16] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[17] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[18] -1	0	0xfe02f000 - 0xfe02f3ff (0x400) MX[B]
	[19] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B](B)
	[20] -1	0	0xfdbe0000 - 0xfdbeffff (0x10000) MX[B](B)
	[21] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[25] 0	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[29] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[30] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[36] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[37] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[38] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[39] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[40] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[41] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.90
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.50.3
(II) fglrx(0):     Date: Jun  2 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 18.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x60000000 FBMappedSize: 0x0100e000
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,2192)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1080) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 1112
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		22 256x256 slots
(II) fglrx(0): Acceleration enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
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
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetKbdSettings - type: 1060 rate: 30 delay: 500 snumlk: 0
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetVBEMode failed

```

Wo kann der Fehler liegen ?

Gruß

Florian

---

