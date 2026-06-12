---
title: "segmentation fault with fglrxinfo in e17 but not in failsafe"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by Derviansoul on 2008-03-05
Hello

By accident today i found out that i was getting segmentation fault when i was logged into e17 but not when i logged into failsafe.
Basically when i typed fglrxinfo logged in the e17 was getting this error.
```

OpenGL vendor string:ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string:1.4 (2.1.7281 Release)

Segmentation fault

```
and there is no direct rendering

if I log into failsafe I get this message with fglrxinfo
```

OpenGL vendor string:ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string:1.4 (2.1.7281 Release)

```
and there is direct rendering!

Why does this happens? can someone help me please!

this is my xorg.conf
```

	BUSID	    "PCI:1:0:0"

	Screen	    1

EndSection



Section "Device"

	Identifier  "aticonfig-Device[0]"

	Driver      "fglrx"

   	Option       "no_accel" "no"

   	Option       "no_dri" "no"

   	Option       "DynamicClocks" "on"

   	Option       "mtrr" "on"

   	Option       "DesktopSetup" "Single"

   	Option       "ScreenOverlap" "0"

   	Option       "Capabilities" "0x00000000"

   	Option       "CapabilitiesEx" "0x00000000"

   	Option       "VideoOverlay" "on"

   	Option       "OpenGLOverlay" "off"

   	Option       "CenterMode" "off"

   	Option       "PseudoColorVisuals" "off"

   	Option       "Stereo" "off"

   	Option       "StereoSyncEnable" "1"

   	Option       "FSAAEnable" "no"

   	Option       "FSAAScale" "1"

   	Option       "FSAADisableGamma" "no"

   	Option       "FSAACustomizeMSPos" "no"

   	Option       "FSAAMSPosX0" "0.000000"

   	Option       "FSAAMSPosY0" "0.000000"

   	Option       "FSAAMSPosX1" "0.000000"

   	Option       "FSAAMSPosY1" "0.000000"

   	Option       "FSAAMSPosX2" "0.000000"

   	Option       "FSAAMSPosY2" "0.000000"

   	Option       "FSAAMSPosX3" "0.000000"

   	Option       "FSAAMSPosY3" "0.000000"

   	Option       "FSAAMSPosX4" "0.000000"

   	Option       "FSAAMSPosY4" "0.000000"

   	Option       "FSAAMSPosX5" "0.000000"

   	Option       "FSAAMSPosY5" "0.000000"

   	Option       "UseFastTLS" "0"

   	Option       "BlockSignalsOnLock" "on"

   	Option       "UseInternalAGPGART" "no"

   	Option       "ForceGenericCPU" "no"

   	Option       "KernelModuleParm" "agplock=0"

   	Option       "PowerState" "1"

   	BusID       "PCI:1:0:0"

EndSection



Section "Screen"

	Identifier "aticonfig-Screen[0]"

	Device     "aticonfig-Device[0]"

	Monitor    "aticonfig-Monitor[0]"

	DefaultDepth     24

	SubSection "Display"

		Viewport   0 0

		Depth     24

		Modes    "1440x900"

	EndSubSection

EndSection



Section "Screen"

	Identifier "aticonfig-Screen[1]"

	Device     "aticonfig-Device[1]"

	Monitor    "aticonfig-Monitor[1]"

	DefaultDepth     24

	SubSection "Display"

		Viewport   0 0

		Depth     24

	EndSubSection

EndSection



```

this is my Xorg.0.log when i logged into the e17!
can anyone help me please!!
```

X Window System Version 1.3.0

Release Date: 19 April 2007

X Protocol Version 11, Revision 0, Release 1.3

Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)

Current Operating System: Linux ricardo-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

Build Date: 18 January 2008

	Before reporting problems, check http://wiki.x.org

	to make sure that you have the latest version.

Module Loader present

Markers: (--) probed, (**) from config file, (==) default setting,

	(++) from command line, (!!) notice, (II) informational,

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  6 00:54:15 2008

(==) Using config file: "/etc/X11/xorg.conf"

(==) ServerLayout "Default Layout"

(**) |-->Screen "aticonfig-Screen[0]" (0)

(**) |   |-->Monitor "aticonfig-Monitor[0]"

(**) |   |-->Device "aticonfig-Device[0]"

(**) |-->Screen "aticonfig-Screen[1]" (1)

(**) |   |-->Monitor "aticonfig-Monitor[1]"

(**) |   |-->Device "aticonfig-Device[1]"

(**) |-->Input Device "Generic Keyboard"

(**) |-->Input Device "Configured Mouse"

(**) Option "Xinerama"

(**) Xinerama: enabled

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

(++) using VT number 7



(II) PCI: PCI scan (all values are in hex)

(II) PCI: 00:00:0: chip 8086,277c card 147b,107a rev c0 class 06,00,00 hdr 00

(II) PCI: 00:01:0: chip 8086,277d card 0000,0000 rev c0 class 06,04,00 hdr 01

(II) PCI: 00:1b:0: chip 8086,27d8 card 147b,107a rev 01 class 04,03,00 hdr 00

(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81

(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81

(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81

(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81

(II) PCI: 00:1c:4: chip 8086,27e0 card 0000,0000 rev 01 class 06,04,00 hdr 81

(II) PCI: 00:1d:0: chip 8086,27c8 card 147b,107a rev 01 class 0c,03,00 hdr 80

(II) PCI: 00:1d:1: chip 8086,27c9 card 147b,107a rev 01 class 0c,03,00 hdr 00

(II) PCI: 00:1d:2: chip 8086,27ca card 147b,107a rev 01 class 0c,03,00 hdr 00

(II) PCI: 00:1d:3: chip 8086,27cb card 147b,107a rev 01 class 0c,03,00 hdr 00

(II) PCI: 00:1d:7: chip 8086,27cc card 147b,107a rev 01 class 0c,03,20 hdr 00

(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01

(II) PCI: 00:1f:0: chip 8086,27b8 card 8086,27b8 rev 01 class 06,01,00 hdr 80

(II) PCI: 00:1f:1: chip 8086,27df card 147b,107a rev 01 class 01,01,8a hdr 00

(II) PCI: 00:1f:2: chip 8086,27c0 card 147b,107a rev 01 class 01,01,8f hdr 00

(II) PCI: 00:1f:3: chip 8086,27da card 147b,107a rev 01 class 0c,05,00 hdr 00

(II) PCI: 01:00:0: chip 1002,7142 card 17af,2056 rev 00 class 03,00,00 hdr 80

(II) PCI: 01:00:1: chip 1002,7162 card 17af,2057 rev 00 class 03,80,00 hdr 00

(II) PCI: 03:00:0: chip 1095,3132 card 1095,3132 rev 01 class 01,80,00 hdr 00

(II) PCI: 04:00:0: chip 10ec,8168 card 147b,107a rev 01 class 02,00,00 hdr 00

(II) PCI: 05:00:0: chip 1095,3132 card 1095,3132 rev 01 class 01,80,00 hdr 00

(II) PCI: 06:00:0: chip 10ec,8168 card 147b,107a rev 01 class 02,00,00 hdr 00

(II) PCI: 07:02:0: chip 104c,8023 card 147b,107a rev 00 class 0c,00,10 hdr 00

(II) PCI: End of PCI scan

(II) Intel Bridge workaround enabled

(II) Host-to-PCI bridge:

(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)

(II) Bus 0 I/O range:

	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]

(II) Bus 0 non-prefetchable memory range:

	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]

(II) Bus 0 prefetchable memory range:

	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]

(II) PCI-to-PCI bridge:

(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)

(II) Bus 1 I/O range:

	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]

(II) Bus 1 non-prefetchable memory range:

	[0] -1	0	0xfd500000 - 0xfd5fffff (0x100000) MX[B]

(II) Bus 1 prefetchable memory range:

	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]

(II) PCI-to-PCI bridge:

(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)

(II) Bus 2 I/O range:

	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]

(II) Bus 2 non-prefetchable memory range:

	[0] -1	0	0xfd200000 - 0xfd2fffff (0x100000) MX[B]

(II) Bus 2 prefetchable memory range:

	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]

(II) PCI-to-PCI bridge:

(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)

(II) Bus 3 I/O range:

	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]

(II) Bus 3 non-prefetchable memory range:

	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]

(II) Bus 3 prefetchable memory range:

	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]

(II) PCI-to-PCI bridge:

(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)

(II) Bus 4 I/O range:

	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]

(II) Bus 4 non-prefetchable memory range:

	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]

(II) Bus 4 prefetchable memory range:

	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]

(II) PCI-to-PCI bridge:

(II) Bus 5: bridge is at (0:28:3), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)

(II) Bus 5 I/O range:

	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]

(II) Bus 5 non-prefetchable memory range:

	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]

(II) Bus 5 prefetchable memory range:

	[0] -1	0	0xfd800000 - 0xfd8fffff (0x100000) MX[B]

(II) PCI-to-PCI bridge:

(II) Bus 6: bridge is at (0:28:4), (0,6,6), BCTRL: 0x0000 (VGA_EN is cleared)

(II) Bus 6 I/O range:

	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]

(II) Bus 6 non-prefetchable memory range:

	[0] -1	0	0xfd700000 - 0xfd7fffff (0x100000) MX[B]

(II) Bus 6 prefetchable memory range:

	[0] -1	0	0xfd600000 - 0xfd6fffff (0x100000) MX[B]

(II) Subtractive PCI-to-PCI bridge:

(II) Bus 7: bridge is at (0:30:0), (0,7,7), BCTRL: 0x0000 (VGA_EN is cleared)

(II) Bus 7 I/O range:

	[0] -1	0	0x00008000 - 0x00008fff (0x1000) IX[B]

(II) Bus 7 non-prefetchable memory range:

	[0] -1	0	0xfd400000 - 0xfd4fffff (0x100000) MX[B]

(II) Bus 7 prefetchable memory range:

	[0] -1	0	0xfd300000 - 0xfd3fffff (0x100000) MX[B]

(II) PCI-to-ISA bridge:

(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)

(--) PCI:*(1:0:0) ATI Technologies Inc RV515 PRO [ATI Radeon X1300/X1550 Series] rev 0, Mem @ 0xd0000000/28, 0xfd5f0000/16, I/O @ 0xce00/8

(--) PCI: (1:0:1) ATI Technologies Inc RV515 PRO [ATI Radeon X1300/X1550 Series Secondary] rev 0, Mem @ 0xfd5e0000/16

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

	[0] -1	0	0xfd4f8000 - 0xfd4fbfff (0x4000) MX[B]

	[1] -1	0	0xfd4ff000 - 0xfd4ff7ff (0x800) MX[B]

	[2] -1	0	0xfd7ff000 - 0xfd7fffff (0x1000) MX[B]

	[3] -1	0	0xfd9f8000 - 0xfd9fbfff (0x4000) MX[B]

	[4] -1	0	0xfd9ff000 - 0xfd9ff07f (0x80) MX[B]

	[5] -1	0	0xfdbff000 - 0xfdbfffff (0x1000) MX[B]

	[6] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]

	[7] -1	0	0xfddff000 - 0xfddff07f (0x80) MX[B]

	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[9] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]

	[10] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]

	[11] -1	0	0xfd5e0000 - 0xfd5effff (0x10000) MX[B](B)

	[12] -1	0	0xfd5f0000 - 0xfd5fffff (0x10000) MX[B](B)

	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[14] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]

	[15] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]

	[16] -1	0	0x00009e00 - 0x00009eff (0x100) IX[B]

	[17] -1	0	0x0000af00 - 0x0000af7f (0x80) IX[B]

	[18] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[19] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]

	[20] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[21] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[22] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]

	[23] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]

	[24] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]

	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[29] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[30] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[31] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[32] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[33] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

(II) Active PCI resource ranges after removing overlaps:

	[0] -1	0	0xfd4f8000 - 0xfd4fbfff (0x4000) MX[B]

	[1] -1	0	0xfd4ff000 - 0xfd4ff7ff (0x800) MX[B]

	[2] -1	0	0xfd7ff000 - 0xfd7fffff (0x1000) MX[B]

	[3] -1	0	0xfd9f8000 - 0xfd9fbfff (0x4000) MX[B]

	[4] -1	0	0xfd9ff000 - 0xfd9ff07f (0x80) MX[B]

	[5] -1	0	0xfdbff000 - 0xfdbfffff (0x1000) MX[B]

	[6] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]

	[7] -1	0	0xfddff000 - 0xfddff07f (0x80) MX[B]

	[8] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[9] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]

	[10] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]

	[11] -1	0	0xfd5e0000 - 0xfd5effff (0x10000) MX[B](B)

	[12] -1	0	0xfd5f0000 - 0xfd5fffff (0x10000) MX[B](B)

	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[14] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]

	[15] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]

	[16] -1	0	0x00009e00 - 0x00009eff (0x100) IX[B]

	[17] -1	0	0x0000af00 - 0x0000af7f (0x80) IX[B]

	[18] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[19] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]

	[20] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[21] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[22] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]

	[23] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]

	[24] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]

	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[29] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[30] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[31] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[32] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[33] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

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

	[4] -1	0	0xfd4f8000 - 0xfd4fbfff (0x4000) MX[B]

	[5] -1	0	0xfd4ff000 - 0xfd4ff7ff (0x800) MX[B]

	[6] -1	0	0xfd7ff000 - 0xfd7fffff (0x1000) MX[B]

	[7] -1	0	0xfd9f8000 - 0xfd9fbfff (0x4000) MX[B]

	[8] -1	0	0xfd9ff000 - 0xfd9ff07f (0x80) MX[B]

	[9] -1	0	0xfdbff000 - 0xfdbfffff (0x1000) MX[B]

	[10] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]

	[11] -1	0	0xfddff000 - 0xfddff07f (0x80) MX[B]

	[12] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[13] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]

	[14] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]

	[15] -1	0	0xfd5e0000 - 0xfd5effff (0x10000) MX[B](B)

	[16] -1	0	0xfd5f0000 - 0xfd5fffff (0x10000) MX[B](B)

	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[20] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]

	[21] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]

	[22] -1	0	0x00009e00 - 0x00009eff (0x100) IX[B]

	[23] -1	0	0x0000af00 - 0x0000af7f (0x80) IX[B]

	[24] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[25] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]

	[26] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[27] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[28] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]

	[29] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]

	[30] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]

	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[35] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[36] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[37] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[38] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[39] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

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

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so

(II) Module glx: vendor="X.Org Foundation"

	compiled for 1.3.0, module version = 1.0.0

	ABI class: X.Org Server Extension, version 0.3

(==) AIGLX enabled

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

(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so

(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."

	compiled for 7.1.0, module version = 8.45.5

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

(II) Primary Device is: PCI 01:00:0

(II) ATI Proprietary Linux Driver Version Identifier:8.45.5

(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.455.2                  

(II) ATI Proprietary Linux Driver Build Date: Feb  1 2008 10:11:22

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

(--) Chipset Supported AMD Graphics Processor (0x7142) found

(--) Chipset Supported AMD Graphics Processor (0x7142) found

(II) AMD Video driver is running on a device belonging to a group targeted for this release

(II) AMD Video driver is signed

(II) resource ranges after xf86ClaimFixedResources() call:

	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0xfd4f8000 - 0xfd4fbfff (0x4000) MX[B]

	[5] -1	0	0xfd4ff000 - 0xfd4ff7ff (0x800) MX[B]

	[6] -1	0	0xfd7ff000 - 0xfd7fffff (0x1000) MX[B]

	[7] -1	0	0xfd9f8000 - 0xfd9fbfff (0x4000) MX[B]

	[8] -1	0	0xfd9ff000 - 0xfd9ff07f (0x80) MX[B]

	[9] -1	0	0xfdbff000 - 0xfdbfffff (0x1000) MX[B]

	[10] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]

	[11] -1	0	0xfddff000 - 0xfddff07f (0x80) MX[B]

	[12] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[13] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]

	[14] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]

	[15] -1	0	0xfd5e0000 - 0xfd5effff (0x10000) MX[B](B)

	[16] -1	0	0xfd5f0000 - 0xfd5fffff (0x10000) MX[B](B)

	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[20] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]

	[21] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]

	[22] -1	0	0x00009e00 - 0x00009eff (0x100) IX[B]

	[23] -1	0	0x0000af00 - 0x0000af7f (0x80) IX[B]

	[24] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[25] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]

	[26] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[27] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[28] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]

	[29] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]

	[30] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]

	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[35] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[36] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[37] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[38] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[39] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

(II) fglrx(0): pEnt->device->identifier=0x8209830

(II) fglrx(1): pEnt->device->identifier=0x8209830

(II) resource ranges after probing:

	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[4] -1	0	0xfd4f8000 - 0xfd4fbfff (0x4000) MX[B]

	[5] -1	0	0xfd4ff000 - 0xfd4ff7ff (0x800) MX[B]

	[6] -1	0	0xfd7ff000 - 0xfd7fffff (0x1000) MX[B]

	[7] -1	0	0xfd9f8000 - 0xfd9fbfff (0x4000) MX[B]

	[8] -1	0	0xfd9ff000 - 0xfd9ff07f (0x80) MX[B]

	[9] -1	0	0xfdbff000 - 0xfdbfffff (0x1000) MX[B]

	[10] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]

	[11] -1	0	0xfddff000 - 0xfddff07f (0x80) MX[B]

	[12] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[13] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]

	[14] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]

	[15] -1	0	0xfd5e0000 - 0xfd5effff (0x10000) MX[B](B)

	[16] -1	0	0xfd5f0000 - 0xfd5fffff (0x10000) MX[B](B)

	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]

	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]

	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]

	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[23] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]

	[24] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]

	[25] -1	0	0x00009e00 - 0x00009eff (0x100) IX[B]

	[26] -1	0	0x0000af00 - 0x0000af7f (0x80) IX[B]

	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[28] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]

	[29] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[30] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[31] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]

	[32] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]

	[33] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]

	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[38] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[39] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[40] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[41] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[42] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]

	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

(II) Setting vga for screen 0.

(II) Setting vga for screen 1.

(II) fglrx(0): === [atiddxPreInit] === begin

(II) Loading sub module "vgahw"

(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so

(II) Module vgahw: vendor="X.Org Foundation"

	compiled for 1.3.0, module version = 0.1.0

	ABI class: X.Org Video Driver, version 1.2

(II) fglrx(0): PCI bus 1 card 0 func 0

(**) fglrx(0): Depth 24, (--) framebuffer bpp 32

(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)

(==) fglrx(0): Default visual is TrueColor

(**) fglrx(0): Option "NoAccel" "no"

(**) fglrx(0): Option "NoDRI" "no"

(**) fglrx(0): Option "Capabilities" "0x00000000"

(**) fglrx(0): Option "CapabilitiesEx" "0x00000000"

(**) fglrx(0): Option "KernelModuleParm" "agplock=0"

(**) fglrx(0): Option "OpenGLOverlay" "off"

(**) fglrx(0): Option "VideoOverlay" "on"

(**) fglrx(0): Option "DesktopSetup" "Single"

(**) fglrx(0): Option "ScreenOverlap" "0"

(**) fglrx(0): Option "UseInternalAGPGART" "no"

(**) fglrx(0): Option "Stereo" "off"

(**) fglrx(0): Option "StereoSyncEnable" "1"

(**) fglrx(0): Option "UseFastTLS" "0"

(**) fglrx(0): Option "BlockSignalsOnLock" "on"

(**) fglrx(0): Option "ForceGenericCPU" "no"

(**) fglrx(0): Option "CenterMode" "off"

(**) fglrx(0): Option "PseudoColorVisuals" "off"

(**) fglrx(0): Option "DPMS" "true"

(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb

(==) fglrx(0): RGB weight 888

(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)

(==) fglrx(0): Gamma Correction for I is 0x06419064

(==) fglrx(0): Gamma Correction for II is 0x06419064

(==) fglrx(0): Buffer Tiling is ON

(--) fglrx(0): Chipset: "Radeon X1300 / X1550 Series" (Chipset = 0x7142)

(--) fglrx(0): (PciSubVendor = 0x17af, PciSubDevice = 0x2056)

(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI

(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000

(--) fglrx(0): MMIO registers at 0xfd5f0000

(==) fglrx(0): ROM-BIOS at 0x000c0000

(**) fglrx(0): Option "mtrr" "on"

(II) Loading sub module "int10"

(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so

(II) Module int10: vendor="X.Org Foundation"

	compiled for 1.3.0, module version = 1.0.0

	ABI class: X.Org Video Driver, version 1.2

(II) fglrx(0): Primary V_BIOS segment is: 0xc000

(II) Loading sub module "vbe"

(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so

(II) Module vbe: vendor="X.Org Foundation"

	compiled for 1.3.0, module version = 1.1.0

	ABI class: X.Org Video Driver, version 1.2

(II) fglrx(0): VESA BIOS detected

(II) fglrx(0): VESA VBE Version 3.0

(II) fglrx(0): VESA VBE Total Mem: 16384 kB

(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS

(II) fglrx(0): VESA VBE OEM Software Rev: 9.12

(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 

(II) fglrx(0): VESA VBE OEM Product: RV515

(II) fglrx(0): VESA VBE OEM Product Rev: 01.00

(II) fglrx(0): ATI Video BIOS revision 9 or later detected

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 7, (OK)

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 7, (OK)

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 7, (OK)

drmGetBusid returned ''

(II) Loading sub module "fglrxdrm"

(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so

(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."

	compiled for 7.1.0, module version = 8.45.5

	ABI class: X.Org Server Extension, version 0.3

(II) fglrx(0): Using adapter: 1:0.0.

(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2

(II) fglrx(0): PCIE card detected

(WW) fglrx(0): board is an unknown third party board, chipset is supported

(WW) fglrx(0): Dual head is configured, DesktopSetup setting "Single" will not be used

(II) Loading sub module "ddc"

(II) LoadModule: "ddc"(II) Module already built-in

(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]

(II) fglrx(0): Display1 EDID data ---------------------------

(II) fglrx(0): Manufacturer: ACI  Model: 19a6  Serial#: 16843009

(II) fglrx(0): Year: 2006  Week: 36

(II) fglrx(0): EDID Version: 1.3

(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V

(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen

(II) fglrx(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27

(II) fglrx(0): Gamma: 2.20

(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display

(II) fglrx(0): Default color space is primary color space

(II) fglrx(0): First detailed timing is preferred mode

(II) fglrx(0): redX: 0.640 redY: 0.334   greenX: 0.286 greenY: 0.599

(II) fglrx(0): blueX: 0.144 blueY: 0.076   whiteX: 0.313 whiteY: 0.329

(II) fglrx(0): Supported VESA Video Modes:

(II) fglrx(0): 720x400@70Hz

(II) fglrx(0): 640x480@60Hz

(II) fglrx(0): 640x480@67Hz

(II) fglrx(0): 640x480@72Hz

(II) fglrx(0): 640x480@75Hz

(II) fglrx(0): 800x600@56Hz

(II) fglrx(0): 800x600@60Hz

(II) fglrx(0): 800x600@72Hz

(II) fglrx(0): 800x600@75Hz

(II) fglrx(0): 832x624@75Hz

(II) fglrx(0): 1024x768@60Hz

(II) fglrx(0): 1024x768@70Hz

(II) fglrx(0): 1024x768@75Hz

(II) fglrx(0): 1280x1024@75Hz

(II) fglrx(0): 1152x870@75Hz

(II) fglrx(0): Manufacturer's mask: 0

(II) fglrx(0): Supported Future Video Modes:

(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897

(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337

(II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149

(II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989

(II) fglrx(0): Supported additional Video Mode:

(II) fglrx(0): clock: 106.0 MHz   Image Size:  410 x 256 mm

(II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0

(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0

(II) fglrx(0): Serial No: 69LV003352

(II) fglrx(0): Ranges: V min: 50  V max: 75 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz

(II) fglrx(0): Monitor name: ASUS VW192Sÿÿ

(II) fglrx(0): EDID (in hex):

(II) fglrx(0): 	00ffffffffffff000469a61901010101

(II) fglrx(0): 	241001030e2b1b782ee5e5a355499924

(II) fglrx(0): 	135054bfef808180714f9500950f0101

(II) fglrx(0): 	0101010101016829a0d0518422305098

(II) fglrx(0): 	36009a001100001c000000ff0036394c

(II) fglrx(0): 	563030333335320a2020000000fd0032

(II) fglrx(0): 	4b1e5215000a202020202020000000fc

(II) fglrx(0): 	004153555320565731393253ffff00a6

(II) fglrx(0): End of Display1 EDID data --------------------

(II) fglrx(0): Connected Display2: CRT on secondary DAC [crt2]

(II) fglrx(0): Display2 EDID data ---------------------------

(II) fglrx(0): Manufacturer: GSM  Model: 438d  Serial#: 261836

(II) fglrx(0): Year: 2005  Week: 6

(II) fglrx(0): EDID Version: 1.3

(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V

(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen

(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27

(II) fglrx(0): Gamma: 2.20

(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display

(II) fglrx(0): First detailed timing is preferred mode

(II) fglrx(0): redX: 0.641 redY: 0.342   greenX: 0.292 greenY: 0.611

(II) fglrx(0): blueX: 0.147 blueY: 0.068   whiteX: 0.313 whiteY: 0.329

(II) fglrx(0): Supported VESA Video Modes:

(II) fglrx(0): 720x400@70Hz

(II) fglrx(0): 640x480@60Hz

(II) fglrx(0): 640x480@75Hz

(II) fglrx(0): 800x600@60Hz

(II) fglrx(0): 800x600@75Hz

(II) fglrx(0): 832x624@75Hz

(II) fglrx(0): 1024x768@60Hz

(II) fglrx(0): 1024x768@75Hz

(II) fglrx(0): 1280x1024@75Hz

(II) fglrx(0): 1152x870@75Hz

(II) fglrx(0): Manufacturer's mask: 0

(II) fglrx(0): Supported Future Video Modes:

(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273

(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293

(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321

(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897

(II) fglrx(0): Supported additional Video Mode:

(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm

(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0

(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0

(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz

(II) fglrx(0): Monitor name: L1730S

(II) fglrx(0): Monitor name: 

(II) fglrx(0): EDID (in hex):

(II) fglrx(0): 	00ffffffffffff001e6d8d43ccfe0300

(II) fglrx(0): 	060f01036e221b78ea2ee5a4574a9c25

(II) fglrx(0): 	115054a56b80314f454f614f81800101

(II) fglrx(0): 	010101010101302a009851002a403070

(II) fglrx(0): 	1300520e1100001e000000fd00384b1e

(II) fglrx(0): 	530e000a202020202020000000fc004c

(II) fglrx(0): 	31373330530a202020202020000000fc

(II) fglrx(0): 	00200a2020202020202020202020001f

(II) fglrx(0): End of Display2 EDID data --------------------

(II) fglrx(0): Primary Controller - CRT on primary DAC

(II) fglrx(0): Secondary Controller - CRT on secondary DAC

(II) fglrx(0): Internal Desktop Setting: 0x00000001

(II) fglrx(0): POWERplay not supported on this hardware

(==) fglrx(0): Qbs is not supported in this release. Disabled.

(==) fglrx(0): FAST_SWAP disabled

(**) fglrx(0):  PseudoColor visuals disabled

(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)

(**) fglrx(0): Center Mode is disabled 

(==) fglrx(0): TMDS coherent mode is enabled 

(II) fglrx(0): Total of 33 modes found for primary display.

(--) fglrx(0): Virtual size is 1440x900 (pitch 0)

(**) fglrx(0): *Mode "1440x900": 136.8 MHz (scaled from 0.0 MHz), 70.6 kHz, 75.0 Hz

(II) fglrx(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 +hsync

(**) fglrx(0):  Default mode "1440x900": 106.0 MHz (scaled from 0.0 MHz), 55.7 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1440x900"  106.00  1440 1520 1672 1904  900 903 909 934 +hsync

(**) fglrx(0):  Default mode "1360x768": 85.5 MHz (scaled from 0.0 MHz), 47.7 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1360x768"   85.50  1360 1424 1536 1792  768 771 777 795

(**) fglrx(0):  Default mode "1280x768": 102.2 MHz (scaled from 0.0 MHz), 60.3 kHz, 75.0 Hz

(II) fglrx(0): Modeline "1280x768"  102.25  1280 1360 1488 1696  768 771 778 805 +hsync

(**) fglrx(0):  Default mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1280x768"   79.50  1280 1344 1472 1664  768 771 778 798 +hsync

(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync

(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz

(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900

(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz

(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync

(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync

(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz

(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800

(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz

(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync

(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz

(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync

(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync

(**) fglrx(0):  Default mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz

(II) fglrx(0): Modeline "848x480"   33.75  848 864 976 1088  480 486 494 517

(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz

(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625

(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz

(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666

(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz

(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync

(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz

(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628

(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz

(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625

(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz

(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync

(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz

(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync

(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz

(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync

(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz

(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync

(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz

(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449

(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz

(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525

(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz

(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416

(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz

(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497

(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)

(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan

(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)

(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan

(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)

(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan

(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)

(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan

(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)

(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan

(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)

(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan

(--) fglrx(0): Display dimensions: (430, 270) mm

(--) fglrx(0): DPI set to (85, 84)

(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)

(**) fglrx(0): *Mode "1440x900": 136.8 MHz (scaled from 0.0 MHz), 70.6 kHz, 75.0 Hz

(II) fglrx(0): Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 +hsync

(**) fglrx(0):  Default mode "1440x900": 106.0 MHz (scaled from 0.0 MHz), 55.7 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1440x900"  106.00  1440 1520 1672 1904  900 903 909 934 +hsync

(**) fglrx(0):  Default mode "1360x768": 85.5 MHz (scaled from 0.0 MHz), 47.7 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1360x768"   85.50  1360 1424 1536 1792  768 771 777 795

(**) fglrx(0):  Default mode "1280x768": 102.2 MHz (scaled from 0.0 MHz), 60.3 kHz, 75.0 Hz

(II) fglrx(0): Modeline "1280x768"  102.25  1280 1360 1488 1696  768 771 778 805 +hsync

(**) fglrx(0):  Default mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1280x768"   79.50  1280 1344 1472 1664  768 771 778 798 +hsync

(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync

(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz

(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900

(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz

(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync

(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync

(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz

(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800

(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz

(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync

(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz

(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync

(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz

(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync

(**) fglrx(0):  Default mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz

(II) fglrx(0): Modeline "848x480"   33.75  848 864 976 1088  480 486 494 517

(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz

(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625

(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz

(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666

(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz

(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync

(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz

(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628

(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz

(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625

(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz

(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync

(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz

(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync

(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz

(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync

(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz

(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync

(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz

(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449

(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz

(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525

(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz

(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416

(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz

(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497

(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)

(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan

(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)

(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan

(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)

(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan

(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)

(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan

(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)

(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan

(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)

(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan

(II) Loading sub module "fb"

(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so

(II) Module fb: vendor="X.Org Foundation"

	compiled for 1.3.0, module version = 1.0.0

	ABI class: X.Org ANSI C Emulation, version 0.3

(II) Loading sub module "ramdac"

(II) LoadModule: "ramdac"(II) Module already built-in

(**) fglrx(0): NoAccel = NO

(II) Loading sub module "xaa"

(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so

(II) Module xaa: vendor="X.Org Foundation"

	compiled for 1.3.0, module version = 1.2.0

	ABI class: X.Org Video Driver, version 1.2

(**) fglrx(0): NoDRI = NO

(II) Loading sub module "fglrxdrm"

(II) LoadModule: "fglrxdrm"

(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so

(II) fglrx(0): Depth moves disabled by default

(**) fglrx(0): Capabilities: 0x00000000

(**) fglrx(0): CapabilitiesEx: 0x00000000

(**) fglrx(0): cpuFlags: 0x8000001d

(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"

(**) fglrx(0): KernelModuleParm: "agplock=0"

(**) fglrx(0): ATI GART size: 256 MB

(II) fglrx(0): [pcie] 258048 kB allocated

(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536

(**) fglrx(0): UseFastTLS=0

(**) fglrx(0): BlockSignalsOnLock=1

(II) fglrx(1): === [atiddxPreInit] === begin

(II) Loading sub module "vgahw"

(II) LoadModule: "vgahw"

(II) Reloading /usr/lib/xorg/modules//libvgahw.so

(II) fglrx(1): PCI bus 1 card 0 func 0

(**) fglrx(1): Depth 24, (--) framebuffer bpp 32

(II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)

(==) fglrx(1): Default visual is TrueColor

(II) fglrx(1): Loading PCS database from /etc/ati/amdpcsdb

(==) fglrx(1): RGB weight 888

(II) fglrx(1): Using 8 bits per RGB (8 bit DAC)

(==) fglrx(1): Buffer Tiling is ON (copy from primary)

(--) fglrx(1): Chipset: "Radeon X1300 / X1550 Series" (Chipset = 0x7142)

(--) fglrx(1): (PciSubVendor = 0x17af, PciSubDevice = 0x2056)

(--) fglrx(1): board vendor info: third party graphics adapter - NOT original ATI

(--) fglrx(1): VideoRAM: 131072 kByte, Type: DDR2

(WW) fglrx(1): board is an unknown third party board, chipset is supported

(**) fglrx(1):  PseudoColor visuals disabled

(==) fglrx(1): Using gamma correction (1.0, 1.0, 1.0)

(**) fglrx(1): Center Mode is disabled 

(==) fglrx(1): TMDS coherent mode is enabled 

(II) fglrx(1): Total of 34 modes found for primary display.

(--) fglrx(1): Virtual size is 1280x1024 (pitch 0)

(**) fglrx(1): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz

(II) fglrx(1): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066

(**) fglrx(1):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz

(II) fglrx(1): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync

(**) fglrx(1):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066

(**) fglrx(1): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000

(**) fglrx(1): *Mode "1280x768": 102.2 MHz (scaled from 0.0 MHz), 60.3 kHz, 75.0 Hz

(II) fglrx(1): Modeline "1280x768"  102.25  1280 1360 1488 1696  768 771 778 805 +hsync

(**) fglrx(1):  Default mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1280x768"   79.50  1280 1344 1472 1664  768 771 778 798 +hsync

(**) fglrx(1): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync

(**) fglrx(1): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz

(II) fglrx(1): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900

(**) fglrx(1):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz

(II) fglrx(1): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync

(**) fglrx(1):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync

(**) fglrx(1): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz

(II) fglrx(1): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800

(**) fglrx(1):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz

(II) fglrx(1): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync

(**) fglrx(1):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz

(II) fglrx(1): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync

(**) fglrx(1):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync

(**) fglrx(1): *Mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz

(II) fglrx(1): Modeline "848x480"   33.75  848 864 976 1088  480 486 494 517

(**) fglrx(1): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz

(II) fglrx(1): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625

(**) fglrx(1):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz

(II) fglrx(1): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666

(**) fglrx(1):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz

(II) fglrx(1): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync

(**) fglrx(1):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz

(II) fglrx(1): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628

(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz

(II) fglrx(1): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625

(**) fglrx(1): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz

(II) fglrx(1): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync

(**) fglrx(1): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz

(II) fglrx(1): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync

(**) fglrx(1):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz

(II) fglrx(1): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync

(**) fglrx(1):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz

(II) fglrx(1): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync

(**) fglrx(1):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz

(II) fglrx(1): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449

(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz

(II) fglrx(1): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525

(**) fglrx(1):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz

(II) fglrx(1): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416

(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz

(II) fglrx(1): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497

(**) fglrx(1):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)

(II) fglrx(1): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan

(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)

(II) fglrx(1): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan

(**) fglrx(1):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)

(II) fglrx(1): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan

(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)

(II) fglrx(1): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan

(**) fglrx(1):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)

(II) fglrx(1): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan

(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)

(II) fglrx(1): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan

(--) fglrx(1): Display dimensions: (340, 270) mm

(--) fglrx(1): DPI set to (95, 96)

(--) fglrx(1): Virtual size is 1280x1024 (pitch 1280)

(**) fglrx(1): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz

(II) fglrx(1): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066

(**) fglrx(1):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz

(II) fglrx(1): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync

(**) fglrx(1):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066

(**) fglrx(1): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000

(**) fglrx(1): *Mode "1280x768": 102.2 MHz (scaled from 0.0 MHz), 60.3 kHz, 75.0 Hz

(II) fglrx(1): Modeline "1280x768"  102.25  1280 1360 1488 1696  768 771 778 805 +hsync

(**) fglrx(1):  Default mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1280x768"   79.50  1280 1344 1472 1664  768 771 778 798 +hsync

(**) fglrx(1): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync

(**) fglrx(1): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz

(II) fglrx(1): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900

(**) fglrx(1):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz

(II) fglrx(1): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync

(**) fglrx(1):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync

(**) fglrx(1): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz

(II) fglrx(1): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800

(**) fglrx(1):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz

(II) fglrx(1): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync

(**) fglrx(1):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz

(II) fglrx(1): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync

(**) fglrx(1):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz

(II) fglrx(1): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync

(**) fglrx(1): *Mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz

(II) fglrx(1): Modeline "848x480"   33.75  848 864 976 1088  480 486 494 517

(**) fglrx(1): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz

(II) fglrx(1): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625

(**) fglrx(1):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz

(II) fglrx(1): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666

(**) fglrx(1):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz

(II) fglrx(1): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync

(**) fglrx(1):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz

(II) fglrx(1): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628

(**) fglrx(1):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz

(II) fglrx(1): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625

(**) fglrx(1): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz

(II) fglrx(1): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync

(**) fglrx(1): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz

(II) fglrx(1): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync

(**) fglrx(1):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz

(II) fglrx(1): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync

(**) fglrx(1):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz

(II) fglrx(1): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync

(**) fglrx(1):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz

(II) fglrx(1): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449

(**) fglrx(1):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz

(II) fglrx(1): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525

(**) fglrx(1):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz

(II) fglrx(1): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416

(**) fglrx(1):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz

(II) fglrx(1): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497

(**) fglrx(1):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)

(II) fglrx(1): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan

(**) fglrx(1):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)

(II) fglrx(1): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan

(**) fglrx(1):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)

(II) fglrx(1): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan

(**) fglrx(1):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)

(II) fglrx(1): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan

(**) fglrx(1):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)

(II) fglrx(1): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan

(**) fglrx(1):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)

(II) fglrx(1): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan

(II) Loading sub module "fb"

(II) LoadModule: "fb"

(II) Reloading /usr/lib/xorg/modules//libfb.so

(==) fglrx(1): NoAccel = NO (copy from primary screen)

(==) fglrx(1): bNoDRI = NO (copy from primary screen)

(**) fglrx(1): UseFastTLS=0

(**) fglrx(1): BlockSignalsOnLock=1

(--) Depth 24 pixmap format is 32 bpp

(II) do I need RAC?  Yes, I do.

(II) resource ranges after preInit:

	[0] 0	0	0xfd5f0000 - 0xfd5fffff (0x10000) MX[B]

	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]

	[2] 0	0	0xfd5f0000 - 0xfd5fffff (0x10000) MX[B]

	[3] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]

	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)

	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]

	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[8] -1	0	0xfd4f8000 - 0xfd4fbfff (0x4000) MX[B]

	[9] -1	0	0xfd4ff000 - 0xfd4ff7ff (0x800) MX[B]

	[10] -1	0	0xfd7ff000 - 0xfd7fffff (0x1000) MX[B]

	[11] -1	0	0xfd9f8000 - 0xfd9fbfff (0x4000) MX[B]

	[12] -1	0	0xfd9ff000 - 0xfd9ff07f (0x80) MX[B]

	[13] -1	0	0xfdbff000 - 0xfdbfffff (0x1000) MX[B]

	[14] -1	0	0xfddf8000 - 0xfddfbfff (0x4000) MX[B]

	[15] -1	0	0xfddff000 - 0xfddff07f (0x80) MX[B]

	[16] -1	0	0xfdffe000 - 0xfdffe3ff (0x400) MX[B]

	[17] -1	0	0xfdfff000 - 0xfdfff3ff (0x400) MX[B]

	[18] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]

	[19] -1	0	0xfd5e0000 - 0xfd5effff (0x10000) MX[B](B)

	[20] -1	0	0xfd5f0000 - 0xfd5fffff (0x10000) MX[B](B)

	[21] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)

	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)

	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)

	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)

	[25] 0	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]

	[26] 0	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]

	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]

	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]

	[30] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]

	[31] -1	0	0x00009e00 - 0x00009eff (0x100) IX[B]

	[32] -1	0	0x0000af00 - 0x0000af7f (0x80) IX[B]

	[33] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]

	[34] -1	0	0x0000f600 - 0x0000f60f (0x10) IX[B]

	[35] -1	0	0x0000f700 - 0x0000f703 (0x4) IX[B]

	[36] -1	0	0x0000f800 - 0x0000f807 (0x8) IX[B]

	[37] -1	0	0x0000f900 - 0x0000f903 (0x4) IX[B]

	[38] -1	0	0x0000fa00 - 0x0000fa07 (0x8) IX[B]

	[39] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]

	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[42] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]

	[43] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]

	[44] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]

	[45] -1	0	0x0000fd00 - 0x0000fd1f (0x20) IX[B]

	[46] -1	0	0x0000fe00 - 0x0000fe1f (0x20) IX[B]

	[47] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]

	[48] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B](B)

	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)

	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)

(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0

(II) fglrx(0): detected X.org 7.1.0.0

(II) Loading extension ATIFGLRXDRI

(II) fglrx(0): doing DRIScreenInit

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 7, (OK)

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 7, (OK)

drmOpenByBusid: Searching for BusID PCI:1:0:0

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 7, (OK)

drmOpenByBusid: drmOpenMinor returns 7

drmOpenByBusid: drmGetBusid reports 

drmOpenDevice: node name is /dev/dri/card1

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card2

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card3

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card4

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card5

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card6

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card7

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card8

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card9

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card10

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card11

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card12

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card13

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card14

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: open result is -1, (No such device)

drmOpenDevice: Open failed

drmOpenByBusid: drmOpenMinor returns -19

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 7, (OK)

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 7, (OK)

drmGetBusid returned ''

(II) fglrx(0): [drm] DRM interface version 1.0

(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"

(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000

(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7679000

(II) fglrx(0): [drm] framebuffer handle = 0x3000

(II) fglrx(0): [drm] added 1 reserved context for kernel

(II) fglrx(0): DRIScreenInit done

(II) fglrx(0): Kernel Module Version Information:

(II) fglrx(0):     Name: fglrx

(II) fglrx(0):     Version: 8.45.5

(II) fglrx(0):     Date: Feb  1 2008

(II) fglrx(0):     Desc: ATI FireGL DRM kernel module

(II) fglrx(0): Kernel Module version matches driver.

(II) fglrx(0): Kernel Module Build Time Information:

(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic

(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes

(II) fglrx(0):     Build-Kernel __SMP__:            yes

(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000

(II) fglrx(0): [drm] register handle = 0x00004000

(II) fglrx(0): Interrupt handler installed at IRQ 16.

(II) fglrx(0): Exposed events to the /proc interface

(II) fglrx(0): DRI initialization successfull!

(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01009800

(II) fglrx(0): FBMM initialized for area (0,0)-(1472,2856)

(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)

(II) fglrx(0): Largest offscreen area available: 1472 x 1956

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

	Offscreen Pixmaps

	Setting up tile and stipple cache:

		32 128x128 slots

		13 256x256 slots

		5 512x512 slots

(II) fglrx(0): Acceleration enabled

(WW) fglrx(0): Option "DynamicClocks" is not used

(WW) fglrx(0): Option "FSAAEnable" is not used

(WW) fglrx(0): Option "FSAAScale" is not used

(WW) fglrx(0): Option "FSAADisableGamma" is not used

(WW) fglrx(0): Option "FSAACustomizeMSPos" is not used

(WW) fglrx(0): Option "FSAAMSPosX0" is not used

(WW) fglrx(0): Option "FSAAMSPosY0" is not used

(WW) fglrx(0): Option "FSAAMSPosX1" is not used

(WW) fglrx(0): Option "FSAAMSPosY1" is not used

(WW) fglrx(0): Option "FSAAMSPosX2" is not used

(WW) fglrx(0): Option "FSAAMSPosY2" is not used

(WW) fglrx(0): Option "FSAAMSPosX3" is not used

(WW) fglrx(0): Option "FSAAMSPosY3" is not used

(WW) fglrx(0): Option "FSAAMSPosX4" is not used

(WW) fglrx(0): Option "FSAAMSPosY4" is not used

(WW) fglrx(0): Option "FSAAMSPosX5" is not used

(WW) fglrx(0): Option "FSAAMSPosY5" is not used

(WW) fglrx(0): Option "PowerState" is not used

(WW) fglrx(0): Option "VendorName" is not used

(WW) fglrx(0): Option "ModelName" is not used

(II) fglrx(0): X context handle = 0x1

(II) fglrx(0): [DRI] installation complete

(II) fglrx(0): Direct rendering enabled

[atiddx] ASYNCIO init succeed!

Receive enable interrupt ret message

...irqEnableMask: 20008000

...dwIRQEnableId: 00000008

(==) fglrx(0): Silken mouse enabled

(==) fglrx(0): Using hardware cursor

(==) RandR enabled

(II) fglrx(1): driver needs X.org 7.1.x.y with x.y >= 0.0

(II) fglrx(1): detected X.org 7.1.0.0

(II) fglrx(1): doing DRIScreenInit

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 9, (OK)

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 9, (OK)

drmOpenByBusid: Searching for BusID PCI:1:0:0

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 9, (OK)

drmOpenByBusid: drmOpenMinor returns 9

drmOpenByBusid: drmGetBusid reports PCI:1:0:0

(II) fglrx(1): [drm] DRM interface version 1.0

(II) fglrx(1): [drm] created "fglrx" driver at busid "PCI:1:0:0"

(II) fglrx(1): [drm] added 8192 byte SAREA at 0x2000

(II) fglrx(1): [drm] mapped SAREA 0x2000 to 0xb5a75000

(II) fglrx(1): [drm] framebuffer handle = 0x3000

(II) fglrx(1): [drm] added 1 reserved context for kernel

(II) fglrx(1): DRIScreenInit done

(II) fglrx(1): DRI initialization successfull!

(II) fglrx(1): FBADPhys: 0xc1010000 FBMappedSize: 0x00708000

(II) fglrx(1): FBMM initialized for area (0,0)-(1280,1440)

(II) fglrx(1): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)

(II) fglrx(1): Largest offscreen area available: 1280 x 416

(==) fglrx(1): Backing store disabled

(**) fglrx(1): Textured Video is enabled.

(II) fglrx(1): Using XFree86 Acceleration Architecture (XAA)

	Screen to screen bit blits

	Solid filled rectangles

	8x8 mono pattern filled rectangles

	Solid Lines

	Dashed Lines

	Offscreen Pixmaps

	Setting up tile and stipple cache:

		30 128x128 slots

(II) fglrx(1): Acceleration enabled

(II) fglrx(1): X context handle = 0x2

(II) fglrx(1): [DRI] installation complete

(II) fglrx(1): Direct rendering enabled

(==) fglrx(1): Silken mouse enabled

(==) fglrx(1): Using hardware cursor

(==) RandR enabled

(II) Entity 0 shares no resources

(II) Entity 1 shares no resources

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

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 10, (OK)

drmOpenByBusid: Searching for BusID PCI:1:0:0

drmOpenDevice: node name is /dev/dri/card0

drmOpenDevice: open result is 10, (OK)

drmOpenByBusid: drmOpenMinor returns 10

drmOpenByBusid: drmGetBusid reports PCI:1:0:0

(WW) AIGLX: 3D driver claims to not support visual 0x23

(WW) AIGLX: 3D driver claims to not support visual 0x24

(WW) AIGLX: 3D driver claims to not support visual 0x25

(WW) AIGLX: 3D driver claims to not support visual 0x26

(WW) AIGLX: 3D driver claims to not support visual 0x27

(WW) AIGLX: 3D driver claims to not support visual 0x28

(WW) AIGLX: 3D driver claims to not support visual 0x29

(WW) AIGLX: 3D driver claims to not support visual 0x2a

(WW) AIGLX: 3D driver claims to not support visual 0x2b

(WW) AIGLX: 3D driver claims to not support visual 0x2c

(WW) AIGLX: 3D driver claims to not support visual 0x2d

(WW) AIGLX: 3D driver claims to not support visual 0x2e

(WW) AIGLX: 3D driver claims to not support visual 0x2f

(WW) AIGLX: 3D driver claims to not support visual 0x30

(WW) AIGLX: 3D driver claims to not support visual 0x31

(WW) AIGLX: 3D driver claims to not support visual 0x32

(WW) AIGLX: 3D driver claims to not support visual 0x33

(WW) AIGLX: 3D driver claims to not support visual 0x34

(WW) AIGLX: 3D driver claims to not support visual 0x35

(WW) AIGLX: 3D driver claims to not support visual 0x36

(WW) AIGLX: 3D driver claims to not support visual 0x37

(WW) AIGLX: 3D driver claims to not support visual 0x38

(WW) AIGLX: 3D driver claims to not support visual 0x39

(WW) AIGLX: 3D driver claims to not support visual 0x3a

(WW) AIGLX: 3D driver claims to not support visual 0x3b

(WW) AIGLX: 3D driver claims to not support visual 0x3c

(WW) AIGLX: 3D driver claims to not support visual 0x3d

(WW) AIGLX: 3D driver claims to not support visual 0x3e

(WW) AIGLX: 3D driver claims to not support visual 0x3f

(WW) AIGLX: 3D driver claims to not support visual 0x40

(WW) AIGLX: 3D driver claims to not support visual 0x41

(WW) AIGLX: 3D driver claims to not support visual 0x42

(WW) AIGLX: 3D driver claims to not support visual 0x43

(WW) AIGLX: 3D driver claims to not support visual 0x44

(WW) AIGLX: 3D driver claims to not support visual 0x45

(WW) AIGLX: 3D driver claims to not support visual 0x46

(WW) AIGLX: 3D driver claims to not support visual 0x47

(WW) AIGLX: 3D driver claims to not support visual 0x48

(WW) AIGLX: 3D driver claims to not support visual 0x49

(WW) AIGLX: 3D driver claims to not support visual 0x4a

(WW) AIGLX: 3D driver claims to not support visual 0x4b

(WW) AIGLX: 3D driver claims to not support visual 0x4c

(WW) AIGLX: 3D driver claims to not support visual 0x4d

(WW) AIGLX: 3D driver claims to not support visual 0x4e

(WW) AIGLX: 3D driver claims to not support visual 0x4f

(WW) AIGLX: 3D driver claims to not support visual 0x50

(WW) AIGLX: 3D driver claims to not support visual 0x51

(WW) AIGLX: 3D driver claims to not support visual 0x52

(WW) AIGLX: 3D driver claims to not support visual 0x53

(WW) AIGLX: 3D driver claims to not support visual 0x54

(WW) AIGLX: 3D driver claims to not support visual 0x55

(WW) AIGLX: 3D driver claims to not support visual 0x56

(WW) AIGLX: 3D driver claims to not support visual 0x57

(WW) AIGLX: 3D driver claims to not support visual 0x58

(WW) AIGLX: 3D driver claims to not support visual 0x59

(WW) AIGLX: 3D driver claims to not support visual 0x5a

(WW) AIGLX: 3D driver claims to not support visual 0x5b

(WW) AIGLX: 3D driver claims to not support visual 0x5c

(WW) AIGLX: 3D driver claims to not support visual 0x5d

(WW) AIGLX: 3D driver claims to not support visual 0x5e

(WW) AIGLX: 3D driver claims to not support visual 0x5f

(WW) AIGLX: 3D driver claims to not support visual 0x60

(WW) AIGLX: 3D driver claims to not support visual 0x61

(WW) AIGLX: 3D driver claims to not support visual 0x62

(WW) AIGLX: 3D driver claims to not support visual 0x63

(WW) AIGLX: 3D driver claims to not support visual 0x64

(WW) AIGLX: 3D driver claims to not support visual 0x65

(WW) AIGLX: 3D driver claims to not support visual 0x66

(WW) AIGLX: 3D driver claims to not support visual 0x67

(WW) AIGLX: 3D driver claims to not support visual 0x68

(WW) AIGLX: 3D driver claims to not support visual 0x69

(WW) AIGLX: 3D driver claims to not support visual 0x6a

(WW) AIGLX: 3D driver claims to not support visual 0x6b

(WW) AIGLX: 3D driver claims to not support visual 0x6c

(WW) AIGLX: 3D driver claims to not support visual 0x6d

(WW) AIGLX: 3D driver claims to not support visual 0x6e

(WW) AIGLX: 3D driver claims to not support visual 0x6f

(WW) AIGLX: 3D driver claims to not support visual 0x70

(WW) AIGLX: 3D driver claims to not support visual 0x71

(WW) AIGLX: 3D driver claims to not support visual 0x72

(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so

(II) GLX: Initialized DRI GL provider for screen 0

(WW) AIGLX: 3D driver claims to not support visual 0x8a

(WW) AIGLX: 3D driver claims to not support visual 0x8b

(WW) AIGLX: 3D driver claims to not support visual 0x8c

(WW) AIGLX: 3D driver claims to not support visual 0x8d

(WW) AIGLX: 3D driver claims to not support visual 0x8e

(WW) AIGLX: 3D driver claims to not support visual 0x8f

(WW) AIGLX: 3D driver claims to not support visual 0x90

(WW) AIGLX: 3D driver claims to not support visual 0x91

(WW) AIGLX: 3D driver claims to not support visual 0x92

(WW) AIGLX: 3D driver claims to not support visual 0x93

(WW) AIGLX: 3D driver claims to not support visual 0x94

(WW) AIGLX: 3D driver claims to not support visual 0x95

(WW) AIGLX: 3D driver claims to not support visual 0x96

(WW) AIGLX: 3D driver claims to not support visual 0x97

(WW) AIGLX: 3D driver claims to not support visual 0x98

(WW) AIGLX: 3D driver claims to not support visual 0x99

(WW) AIGLX: 3D driver claims to not support visual 0x9a

(WW) AIGLX: 3D driver claims to not support visual 0x9b

(WW) AIGLX: 3D driver claims to not support visual 0x9c

(WW) AIGLX: 3D driver claims to not support visual 0x9d

(WW) AIGLX: 3D driver claims to not support visual 0x9e

(WW) AIGLX: 3D driver claims to not support visual 0x9f

(WW) AIGLX: 3D driver claims to not support visual 0xa0

(WW) AIGLX: 3D driver claims to not support visual 0xa1

(WW) AIGLX: 3D driver claims to not support visual 0xa2

(WW) AIGLX: 3D driver claims to not support visual 0xa3

(WW) AIGLX: 3D driver claims to not support visual 0xa4

(WW) AIGLX: 3D driver claims to not support visual 0xa5

(WW) AIGLX: 3D driver claims to not support visual 0xa6

(WW) AIGLX: 3D driver claims to not support visual 0xa7

(WW) AIGLX: 3D driver claims to not support visual 0xa8

(WW) AIGLX: 3D driver claims to not support visual 0xa9

(WW) AIGLX: 3D driver claims to not support visual 0xaa

(WW) AIGLX: 3D driver claims to not support visual 0xab

(WW) AIGLX: 3D driver claims to not support visual 0xac

(WW) AIGLX: 3D driver claims to not support visual 0xad

(WW) AIGLX: 3D driver claims to not support visual 0xae

(WW) AIGLX: 3D driver claims to not support visual 0xaf

(WW) AIGLX: 3D driver claims to not support visual 0xb0

(WW) AIGLX: 3D driver claims to not support visual 0xb1

(WW) AIGLX: 3D driver claims to not support visual 0xb2

(WW) AIGLX: 3D driver claims to not support visual 0xb3

(WW) AIGLX: 3D driver claims to not support visual 0xb4

(WW) AIGLX: 3D driver claims to not support visual 0xb5

(WW) AIGLX: 3D driver claims to not support visual 0xb6

(WW) AIGLX: 3D driver claims to not support visual 0xb7

(WW) AIGLX: 3D driver claims to not support visual 0xb8

(WW) AIGLX: 3D driver claims to not support visual 0xb9

(WW) AIGLX: 3D driver claims to not support visual 0xba

(WW) AIGLX: 3D driver claims to not support visual 0xbb

(WW) AIGLX: 3D driver claims to not support visual 0xbc

(WW) AIGLX: 3D driver claims to not support visual 0xbd

(WW) AIGLX: 3D driver claims to not support visual 0xbe

(WW) AIGLX: 3D driver claims to not support visual 0xbf

(WW) AIGLX: 3D driver claims to not support visual 0xc0

(WW) AIGLX: 3D driver claims to not support visual 0xc1

(WW) AIGLX: 3D driver claims to not support visual 0xc2

(WW) AIGLX: 3D driver claims to not support visual 0xc3

(WW) AIGLX: 3D driver claims to not support visual 0xc4

(WW) AIGLX: 3D driver claims to not support visual 0xc5

(WW) AIGLX: 3D driver claims to not support visual 0xc6

(WW) AIGLX: 3D driver claims to not support visual 0xc7

(WW) AIGLX: 3D driver claims to not support visual 0xc8

(WW) AIGLX: 3D driver claims to not support visual 0xc9

(WW) AIGLX: 3D driver claims to not support visual 0xca

(WW) AIGLX: 3D driver claims to not support visual 0xcb

(WW) AIGLX: 3D driver claims to not support visual 0xcc

(WW) AIGLX: 3D driver claims to not support visual 0xcd

(WW) AIGLX: 3D driver claims to not support visual 0xce

(WW) AIGLX: 3D driver claims to not support visual 0xcf

(WW) AIGLX: 3D driver claims to not support visual 0xd0

(WW) AIGLX: 3D driver claims to not support visual 0xd1

(WW) AIGLX: 3D driver claims to not support visual 0xd2

(WW) AIGLX: 3D driver claims to not support visual 0xd3

(WW) AIGLX: 3D driver claims to not support visual 0xd4

(WW) AIGLX: 3D driver claims to not support visual 0xd5

(WW) AIGLX: 3D driver claims to not support visual 0xd6

(WW) AIGLX: 3D driver claims to not support visual 0xd7

(WW) AIGLX: 3D driver claims to not support visual 0xd8

(WW) AIGLX: 3D driver claims to not support visual 0xd9

(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so

(II) GLX: Initialized DRI GL provider for screen 1

(**) Option "CoreKeyboard"

(**) Generic Keyboard: Core Keyboard

(**) Option "Protocol" "standard"

(**) Generic Keyboard: Protocol: standard

(**) Option "AutoRepeat" "500 30"

(**) Option "XkbRules" "xorg"

(**) Generic Keyboard: XkbRules: "xorg"

(**) Option "XkbModel" "pc105"

(**) Generic Keyboard: XkbModel: "pc105"

(**) Option "XkbLayout" "gb"

(**) Generic Keyboard: XkbLayout: "gb"

(**) Option "CustomKeycodes" "off"

(**) Generic Keyboard: CustomKeycodes disabled

(**) Option "Protocol" "ImPS/2"

(**) Configured Mouse: Device: "/dev/input/mice"

(**) Configured Mouse: Protocol: "ImPS/2"

(**) Option "CorePointer"

(**) Configured Mouse: Core Pointer

(**) Option "Device" "/dev/input/mice"

(**) Option "Emulate3Buttons" "true"

(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50

(**) Option "ZAxisMapping" "4 5"

(**) Configured Mouse: ZAxisMapping: buttons 4 and 5

(**) Configured Mouse: Buttons: 9

(**) Configured Mouse: Sensitivity: 1

(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)

(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)

(II) Configured Mouse: ps2EnableDataReporting: succeeded


```

---

### Post by Derviansoul on 2008-03-06
please anyone help!!:-(

---

### Post by Derviansoul on 2008-03-08
fixed with a clean install fglrx working now, what happened was that i was using gOS now i tried with the ubuntu gutsy distro and it's working with no mess!!
thanks anyway

---

