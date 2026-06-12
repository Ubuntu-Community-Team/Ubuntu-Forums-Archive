---
title: "ATI Black Screen.. Please help!"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by pailhead on 2005-07-21
I'm having an issue with the ATI drivers on my AMD64 machine. I've installed them via the How-to's in the forums and I'm having a hard time getting them to work. I've changed my xorg.conf according to the directions but I'm having a problem with it when gdm launches. **I get a black screen and that's it**. I have to reset my machine so I can go into "safe mode" if you pardon the phrase.

Here's my xorg.conf log..

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154247 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 x86_64 [ELF] 
Current Operating System: Linux ubuntu 2.6.10-5-amd64-generic #1 Fri Jun 24 16:54:18 UTC 2005 x86_64
Build Date: 05 April 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-amd64-generic (buildd@yellow) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 16:54:18 UTC 2005 T
Markers: (--) probed, () from config file, () default setting,
	() from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
() Log file: "/var/log/Xorg.0.log", Time: Thu Jul 21 20:19:52 2005
() Using config file: "/etc/X11/xorg.conf"
() ServerLayout "Default Layout"
() |-->Screen "Default Screen" (0)
() |   |-->Monitor "Generic Monitor"
() |   |-->Device "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
() |-->Input Device "Generic Keyboard"
() Option "XkbRules" "xorg"
() XKB: rules: "xorg"
() Option "XkbModel" "pc104"
() XKB: model: "pc104"
() Option "XkbLayout" "us"
() XKB: layout: "us"
() Keyboard: CustomKeycode disabled
() |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
() FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
() RgbPath set to "/usr/X11R6/lib/X11/rgb"
() ModulePath set to "/usr/X11R6/lib/modules"
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
() using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3188 card 1106,3188 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1102,0004 card 1102,0040 rev 03 class 04,01,00 hdr 80
(II) PCI: 00:07:2: chip 1102,4001 card 0000,0000 rev 00 class 0c,00,10 hdr 80
(II) PCI: 00:0a:0: chip 168c,0013 card 1186,3a13 rev 01 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 10ec,8169 card 1462,702c rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1462,7020 rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1462,7020 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1462,7020 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1462,7020 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1462,7020 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1462,7020 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1462,7020 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1106,3227 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1462,0080 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,4e48 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4e68 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcfe00000 - 0xcfefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xafd00000 - 0xcfcfffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800] rev 0, Mem @ 0xc0000000/27, 0xcfef0000/16, I/O @ 0xa800/8, BIOS @ 0xcfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary) rev 0, Mem @ 0xb8000000/27, 0xcfee0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xcfffb500 - 0xcfffb5ff (0x100) MX[B]
	[1] -1	0	0xcfffb700 - 0xcfffb7ff (0x100) MX[B]
	[2] -1	0	0xcffe0000 - 0xcffeffff (0x10000) MX[B]
	[3] -1	0	0xcfff4000 - 0xcfff7fff (0x4000) MX[B]
	[4] -1	0	0xcfffb800 - 0xcfffbfff (0x800) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[9] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[12] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfffb500 - 0xcfffb5ff (0x100) MX[B]
	[1] -1	0	0xcfffb700 - 0xcfffb7ff (0x100) MX[B]
	[2] -1	0	0xcffe0000 - 0xcffeffff (0x10000) MX[B]
	[3] -1	0	0xcfff4000 - 0xcfff7fff (0x4000) MX[B]
	[4] -1	0	0xcfffb800 - 0xcfffbfff (0x800) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B](B)
	[7] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[9] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[12] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[16] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffb500 - 0xcfffb5ff (0x100) MX[B]
	[6] -1	0	0xcfffb700 - 0xcfffb7ff (0x100) MX[B]
	[7] -1	0	0xcffe0000 - 0xcffeffff (0x10000) MX[B]
	[8] -1	0	0xcfff4000 - 0xcfff7fff (0x4000) MX[B]
	[9] -1	0	0xcfffb800 - 0xcfffbfff (0x800) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B](B)
	[12] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[14] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
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

```

Please has anyone seen this issue? If so and you've fixed it how did you do it?

Please any insite would be great.

Thanks...

pailhead

---

### Post by pailhead on 2005-07-21
Here's more of my log file....

```

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
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 6.5.6
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
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireGL D1100 (RV370) 5B65 (PCIE),
	ATI Radeon Mobility M300 (M22) 5460 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
	ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
	ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
	ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
	ATI RADEON X700 SE, ATI RADEON X700 SE,
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
	ATI FireGL V7100 (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
	ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
	ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
	ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
	ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
	ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
	ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
	ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)".
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9800PRO NH (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffb500 - 0xcfffb5ff (0x100) MX[B]
	[6] -1	0	0xcfffb700 - 0xcfffb7ff (0x100) MX[B]
	[7] -1	0	0xcffe0000 - 0xcffeffff (0x10000) MX[B]
	[8] -1	0	0xcfff4000 - 0xcfff7fff (0x4000) MX[B]
	[9] -1	0	0xcfffb800 - 0xcfffbfff (0x800) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B](B)
	[12] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[14] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffb500 - 0xcfffb5ff (0x100) MX[B]
	[6] -1	0	0xcfffb700 - 0xcfffb7ff (0x100) MX[B]
	[7] -1	0	0xcffe0000 - 0xcffeffff (0x10000) MX[B]
	[8] -1	0	0xcfff4000 - 0xcfff7fff (0x4000) MX[B]
	[9] -1	0	0xcfffb800 - 0xcfffbfff (0x800) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B](B)
	[12] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[14] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[34] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[35] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xcfef0000
(II) RADEON(0): PCI bus 1 card 0 func 0
() RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
() RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
() RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9800PRO NH (AGP)" (ChipID = 0x4e48)
(--) RADEON(0): Linear framebuffer at 0xc0000000
(--) RADEON(0): BIOS at 0xcfec0000
(--) RADEON(0): VideoRAM: 131072 kByte (256 bit DDR SDRAM)
(II) RADEON(0): AGP card detected
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 3a2  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 31
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 1.91
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): GTF timings supported
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.285 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.075   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): #6: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  352 x 264 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 110 kHz, PixClock max 290 MHz
(II) RADEON(0): Monitor name: hp p930
(II) RADEON(0): Serial No: MYA33100Y7
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=33800
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
() RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Generic Monitor: Using hsync range of 30.00-110.00 kHz
(II) RADEON(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)

```

I hope this will help cause man I need it  :cry:

---

### Post by pailhead on 2005-07-21
And the last portion...

```

(--) RADEON(0): Virtual size is 1600x1200 (pitch 1600)
() RADEON(0): *Default mode "1600x1200": 229.5 MHz, 106.2 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1600x1200"  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
() RADEON(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) RADEON(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
() RADEON(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) RADEON(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
() RADEON(0):  Default mode "1600x1200": 202.5 MHz, 93.8 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1600x1200"  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0):  Default mode "1600x1200": 189.0 MHz, 87.5 kHz, 70.0 Hz
(II) RADEON(0): Modeline "1600x1200"  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0):  Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
(II) RADEON(0): Modeline "1600x1200"  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0):  Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0):  Default mode "1400x1050": 184.0 MHz, 93.9 kHz, 85.3 Hz
(II) RADEON(0): Modeline "1400x1050"  184.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
() RADEON(0):  Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(II) RADEON(0): Modeline "1400x1050"  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync
() RADEON(0):  Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
(II) RADEON(0): Modeline "1400x1050"  151.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
() RADEON(0):  Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1400x1050"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync
() RADEON(0):  Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
() RADEON(0):  Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
() RADEON(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
() RADEON(0):  Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1440x900"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync
() RADEON(0):  Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x960"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
() RADEON(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
() RADEON(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
() RADEON(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) RADEON(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
() RADEON(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
() RADEON(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
() RADEON(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) RADEON(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
() RADEON(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
() RADEON(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
() RADEON(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
() RADEON(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.1 Hz (I)
(II) RADEON(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
() RADEON(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
() RADEON(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
() RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
() RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
() RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
() RADEON(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
() RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
() RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
() RADEON(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
() RADEON(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
() RADEON(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
() RADEON(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 87.1 Hz (D)
(II) RADEON(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
() RADEON(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RADEON(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
() RADEON(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
() RADEON(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RADEON(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
() RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
() RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(--) RADEON(0): Display dimensions: (360, 270) mm
(--) RADEON(0): DPI set to (112, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): AGP Fast Write disabled by default
(II) RADEON(0): Depth moves disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffb500 - 0xcfffb5ff (0x100) MX[B]
	[8] -1	0	0xcfffb700 - 0xcfffb7ff (0x100) MX[B]
	[9] -1	0	0xcffe0000 - 0xcffeffff (0x10000) MX[B]
	[10] -1	0	0xcfff4000 - 0xcfff7fff (0x4000) MX[B]
	[11] -1	0	0xcfffb800 - 0xcfffbfff (0x800) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B](B)
	[14] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[16] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[33] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[34] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[36] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[37] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[38] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
() RADEON(0): Write-combining range (0xc0000000,0x8000000)
(WW) RADEON(0): Direct rendering not yet supported on Radeon 9500 and newer cards
(II) RADEON(0): Memory manager initialized to (0,0) (1600,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1600,1202)
(II) RADEON(0): Largest offscreen area available: 1600 x 6989
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
() RADEON(0): Backing store disabled
() RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1202)
(II) RADEON(0): Largest offscreen area available: 1600 x 6986
() Option "dpms"
() RADEON(0): DPMS enabled
(II) RADEON(0): Direct rendering disabled
() RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
() Generic Keyboard: Core Keyboard
() Option "Protocol" "standard"
() Generic Keyboard: Protocol: standard
() Option "AutoRepeat" "500 30"
() Option "XkbRules" "xorg"
() Generic Keyboard: XkbRules: "xorg"
() Option "XkbModel" "pc104"
() Generic Keyboard: XkbModel: "pc104"
() Option "XkbLayout" "us"
() Generic Keyboard: XkbLayout: "us"
() Option "CustomKeycodes" "off"
() Generic Keyboard: CustomKeycodes disabled
() Option "Protocol" "ImPS/2"
() Configured Mouse: Device: "/dev/input/mice"
() Configured Mouse: Protocol: "ImPS/2"
() Option "CorePointer"
() Configured Mouse: Core Pointer
() Option "Device" "/dev/input/mice"
() Option "Emulate3Buttons" "true"
() Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
() Option "ZAxisMapping" "4 5"
() Configured Mouse: ZAxisMapping: buttons 4 and 5
() Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

```

---

### Post by black hole sun on 2005-07-22
[QUOTE=pailhead]And the last portion...

```

(--) RADEON(0): Virtual size is 1600x1200 (pitch 1600)
() RADEON(0): *Default mode "1600x1200": 229.5 MHz, 106.2 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1600x1200"  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
() RADEON(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) RADEON(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
() RADEON(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) RADEON(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
() RADEON(0):  Default mode "1600x1200": 202.5 MHz, 93.8 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1600x1200"  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0):  Default mode "1600x1200": 189.0 MHz, 87.5 kHz, 70.0 Hz
(II) RADEON(0): Modeline "1600x1200"  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0):  Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
(II) RADEON(0): Modeline "1600x1200"  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0):  Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
() RADEON(0):  Default mode "1400x1050": 184.0 MHz, 93.9 kHz, 85.3 Hz
(II) RADEON(0): Modeline "1400x1050"  184.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
() RADEON(0):  Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(II) RADEON(0): Modeline "1400x1050"  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync
() RADEON(0):  Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
(II) RADEON(0): Modeline "1400x1050"  151.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
() RADEON(0):  Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1400x1050"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync
() RADEON(0):  Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
() RADEON(0):  Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
() RADEON(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
() RADEON(0):  Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1440x900"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync
() RADEON(0):  Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "1280x960"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
() RADEON(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
() RADEON(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
() RADEON(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) RADEON(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
() RADEON(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
() RADEON(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
() RADEON(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) RADEON(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
() RADEON(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
() RADEON(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
() RADEON(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
() RADEON(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.1 Hz (I)
(II) RADEON(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
() RADEON(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
() RADEON(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
() RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
() RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
() RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
() RADEON(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
() RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
() RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
() RADEON(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) RADEON(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
() RADEON(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
() RADEON(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RADEON(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
() RADEON(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 87.1 Hz (D)
(II) RADEON(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
() RADEON(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RADEON(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
() RADEON(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
() RADEON(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RADEON(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
() RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
() RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(--) RADEON(0): Display dimensions: (360, 270) mm
(--) RADEON(0): DPI set to (112, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): AGP Fast Write disabled by default
(II) RADEON(0): Depth moves disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffb500 - 0xcfffb5ff (0x100) MX[B]
	[8] -1	0	0xcfffb700 - 0xcfffb7ff (0x100) MX[B]
	[9] -1	0	0xcffe0000 - 0xcffeffff (0x10000) MX[B]
	[10] -1	0	0xcfff4000 - 0xcfff7fff (0x4000) MX[B]
	[11] -1	0	0xcfffb800 - 0xcfffbfff (0x800) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xcfee0000 - 0xcfeeffff (0x10000) MX[B](B)
	[14] -1	0	0xb8000000 - 0xbfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xcfec0000 - 0xcfedffff (0x20000) MX[B](B)
	[16] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[33] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[34] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[36] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[37] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[38] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
() RADEON(0): Write-combining range (0xc0000000,0x8000000)
(WW) RADEON(0): Direct rendering not yet supported on Radeon 9500 and newer cards
(II) RADEON(0): Memory manager initialized to (0,0) (1600,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1600,1202)
(II) RADEON(0): Largest offscreen area available: 1600 x 6989
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
() RADEON(0): Backing store disabled
() RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1202)
(II) RADEON(0): Largest offscreen area available: 1600 x 6986
() Option "dpms"
() RADEON(0): DPMS enabled
(II) RADEON(0): Direct rendering disabled
() RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
() Generic Keyboard: Core Keyboard
() Option "Protocol" "standard"
() Generic Keyboard: Protocol: standard
() Option "AutoRepeat" "500 30"
() Option "XkbRules" "xorg"
() Generic Keyboard: XkbRules: "xorg"
() Option "XkbModel" "pc104"
() Generic Keyboard: XkbModel: "pc104"
() Option "XkbLayout" "us"
() Generic Keyboard: XkbLayout: "us"
() Option "CustomKeycodes" "off"
() Generic Keyboard: CustomKeycodes disabled
() Option "Protocol" "ImPS/2"
() Configured Mouse: Device: "/dev/input/mice"
() Configured Mouse: Protocol: "ImPS/2"
() Option "CorePointer"
() Configured Mouse: Core Pointer
() Option "Device" "/dev/input/mice"
() Option "Emulate3Buttons" "true"
() Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
() Option "ZAxisMapping" "4 5"
() Configured Mouse: ZAxisMapping: buttons 4 and 5
() Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

```[/QUOTE]
 Um, according to the log you're using the "radeon" driver. This should be "fglrx". Change the driver line in xorg.conf to read fglrx.

---

### Post by pailhead on 2005-07-22
[QUOTE=black hole sun]Um, according to the log you're using the "radeon" driver. This should be "fglrx". Change the driver line in xorg.conf to read fglrx.[/QUOTE]

Ahh shoot yeah I gave you a newer log not the right one.  I'll redo the fglrx change and I'll post the log again and my xorg.conf.

Sorry about that.

---

### Post by ThatRickGuy on 2005-07-22
If you find an answer to this, please post it. I'm having a similar problem (ATI x700, monitor goes to 'no signal' when GDM loads).

I managed to atleast get the GDM to load using the vesa drivers. But performance is pretty sad.

-Rick

---

### Post by ThatRickGuy on 2005-07-22
Also, I saw that you are loading (II) Loading extension XFree86-DGA. most of the ATI  how to's  I've seen say to omit this line.

in the module section:
```

	#Load	"extmod"
	SubSection "extmod"
		Option "omit fxree86-dga"
	EndSubSection

```

-Rick

---

### Post by pailhead on 2005-07-23
Ok so I started over and installed the stock drivers from ATI. Now I don't have a black screen and can now get to my gnome desktop at 1600x1200 so I'm good as far as that goes.

Now when I run glxgears I recieve the following error message:

> glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory 

I've attached both my xorg.conf and xorg.o.log in the archive.

I've searched for this error and I guess I'm not using the right keyword because I can't seem to find anything.  I'm new with linux and really would like to play some decent games from time to time :)

Thanks...

---

### Post by black hole sun on 2005-07-23
[QUOTE=pailhead]Ok so I started over and installed the stock drivers from ATI. Now I don't have a black screen and can now get to my gnome desktop at 1600x1200 so I'm good as far as that goes.

Now when I run glxgears I recieve the following error message:

 

I've attached both my xorg.conf and xorg.o.log in the archive.

I've searched for this error and I guess I'm not using the right keyword because I can't seem to find anything.  I'm new with linux and really would like to play some decent games from time to time :)

Thanks...[/QUOTE]
 libGL should be in /usr/X11R6/lib/. It is provided with the ATI driver.

How exactly did you install the driver? You should have d/l the rpm from ATI, converted it to deb and then use --force-all to install it with dpkg.

---

### Post by mjkelly on 2005-07-23
Ive tried everything there is to try about this. From these forums to the wiki ubuntu site to IRC even to a couple good debian forums, and noone could help me. I have a Radeon 9250 tho and i talked someone through installed fglrx for a radeon 9800 with these directions:

[https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28driver%29%7C%28binary%29](https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28driver%29%7C%28binary%29)

Before you use that guide I would do a couple of things first.

1. Make sure the kernel is the 686 brand.  In a console type  uname -r   Your looking for this 2.6.10-5-686    If it looks like that with the 686 and you already upgraded it to 686 then forget part 1 :)
If it has a 386 at the end, open synaptic and search for  linux-image  and install the package that looks like this    linux-image-2.6.10-5-686
Then install   linux-headers-2.6.10-5-686 and linux-restricted-modules-2.6.10-5-686
Restart the computer and load the new kernel. Grub will automatically select it as default.

2. Uninstall the previous fglrx
A simple uninstall of the fglrx driver you have previously installed wont work. Check in /usr/share/fglrx for an uninstall script. I dont know the exact name of it bc i gave up on trying to have it installed. Run the script with "sudo sh fglrx.uninstall.sh" If you cant find the script search the system using "Place > Search for files" and search for fglrx and it should turn up there then go into a console and run that script. It works well. If you cant find that cuz it doesnt existon ur system, search on synaptic for fglrx and uninstall anything thats installed, then do a manual search on the system for fglrx and remove those files as well. If you try to force-overwrite as someone suggested, it doesnt really seem to work. You end up with one type of fglrx here and one type here and it everything gets confusing. Its better to start from scratch in this instance then overwriting from my experience.

3. Then follow this guide here [https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28driver%29%7C%28binary%29](https://wiki.ubuntu.com/BinaryDriverHowto?highlight=%28driver%29%7C%28binary%29)
Ive seen that guide work but i cant speak for all the other ones. Remember to restart after certain commands like it says to before running the next one.

BTW mine does the exact same thing with the black screen. If you try to play a song before starting the X server, the song even freezes when the server hangs. Someone pointed out to me in one of the Debian chatrooms that this indicated a really hard hang on the system.

On my system, even after the fglrx drivers are installed properly and the kernel accepts them in the kern.log, they still cause it to hang. Ive actually pinpointed it down to a problem caused by DRM and DRI, but thats as far as i tried then gave up after about a week. Lemme know how it goes.

---

### Post by pailhead on 2005-07-23
[QUOTE=black hole sun]libGL should be in /usr/X11R6/lib/. It is provided with the ATI driver.

How exactly did you install the driver? You should have d/l the rpm from ATI, converted it to deb and then use --force-all to install it with dpkg.[/QUOTE]

I installed the ati-driver-installer-8.14.13.run file from the ATI website. It installed just fine, as far as getting to the desktop but 3D games etc does'nt work.

Did you see anything in my files that seem off or should be on but are off?

---

### Post by pailhead on 2005-07-23
[QUOTE=mjkelly]
2. Uninstall the previous fglrx
A simple uninstall of the fglrx driver you have previously installed wont work. Check in /usr/share/fglrx for an uninstall script. I dont know the exact name of it bc i gave up on trying to have it installed. Run the script with "sudo sh fglrx.uninstall.sh" If you cant find the script search the system using "Place > Search for files" and search for fglrx and it should turn up there then go into a console and run that script. It works well. If you cant find that cuz it doesnt existon ur system, search on synaptic for fglrx and uninstall anything thats installed, then do a manual search on the system for fglrx and remove those files as well. If you try to force-overwrite as someone suggested, it doesnt really seem to work. You end up with one type of fglrx here and one type here and it everything gets confusing. Its better to start from scratch in this instance then overwriting from my experience.
[/QUOTE]

This is how I uninstall the ATI drivers?  This will remove the files etc that go with this install?

---

### Post by norman_h on 2005-07-23
Hi guys!

I have an AMD64 and ati9600xt card.  I have not installed any specialised drivers, I am only using the standard 5.04 release.

I have had a couple of problems when upgrading software through the update manager.  For some reason the modules don't load after an upgrade, and gdm doesn't run.  I can boot into "safe-mode" and things work nicely.  The best workaround solution I have found is to add the module names to /etc/modules so that they are automatically insterted at boot time.

---

### Post by mjkelly on 2005-07-24
Yeah that uninstall script is the most effective way of removing fglrx to start over. You said it installed correctly, so do a "grep fglrx /var/log/kern.log" and see what ya get, i dunno if u need to sudo that or not. If you get something like Module loaded correctly, then dont worry about reinstalling it.

If it is installed correctly and you get a black screen, which is the same thing i got and still get, i dont know what to tell you. I do know that its not the fglrx driver then but something with direct rendering. I wish i had all my information from when i was trying at this but i reformatted after failing at it and lost all the saved logs i had. Somehow during the one restart of X when it crashed, it wrote out a log to Xorg.0.log.old and when i grepped fglrx there was a whole bunch of information and alotta errors regarding DRM.

If ya happen to figure it out make sure ya post how cuz theres alot of ppl who cant get it to work.

---

### Post by pailhead on 2005-07-24
[QUOTE=mjkelly]Yeah that uninstall script is the most effective way of removing fglrx to start over. You said it installed correctly, so do a "grep fglrx /var/log/kern.log" and see what ya get, i dunno if u need to sudo that or not. If you get something like Module loaded correctly, then dont worry about reinstalling it.

If it is installed correctly and you get a black screen, which is the same thing i got and still get, i dont know what to tell you. I do know that its not the fglrx driver then but something with direct rendering. I wish i had all my information from when i was trying at this but i reformatted after failing at it and lost all the saved logs i had. Somehow during the one restart of X when it crashed, it wrote out a log to Xorg.0.log.old and when i grepped fglrx there was a whole bunch of information and alotta errors regarding DRM.

If ya happen to figure it out make sure ya post how cuz theres alot of ppl who cant get it to work.[/QUOTE]

I've attached my kern.log. It looks as though fglrx is loading fine. What do you thinK?

The 2D is working though performance is not grand but it's working much faster than vesa but slower than the default ati drivers Ubuntu installed.

Boy they need to make installing this easier.

---

### Post by mjkelly on 2005-07-24
Heres the important part:
Jul 23 21:00:44 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 917 MBytes.
Jul 23 21:00:44 localhost kernel: [fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
Jul 23 21:00:44 localhost kernel: [fglrx:firegl_unlock] *ERROR* Process 7418 using kernel context 0

Ive never seen that error before. I dont think its related to this, bc mine didnt have it and i had the same black screen you have. Whats your fullscreen glxgears score? Whats "modprobe fglrx" look like? Whats "fglrxinfo" look like?

Try this, it might work with the logs.
1 Change the driver to fglrx in xorg.conf
2 Restart the comp and let X hang
3 Restart in safe mode and while in safe mode run this command "grep fglrx /var/log/Xorg.0.log.old > /home/USERNAME/Xorg.log.old"
4 While in safe mode run this command as well "grep fglrx /var/log/Xorg.0.log > /home/USERNAME/Xorg.log"
5 After replacing the xorg.conf with one that works, log back in and look at both of those logs. It might not work at all, but if it does then maybe we'll get a glimpse into what makin X hang. 

I got this to work once with the xorg.log.old file and thats what pointed me in the direction or DRM. See if it works, ya aint got nuttin to lose anyways hehe :)

---

### Post by mjkelly on 2005-07-24
I might have just figured it out. Im not too sure hehe

Save these to a file so ya dont forget em before shuttin down X.

1 try "sudo /etc/init.d/gdm stop" ----- tell X to shut itself down
2 try "sudo modprobe remove radeon"      -----------       this will tell the kernel to remove radeon for the session, wont work unless X is shut down
3 try "sudo modprobe remove ati"      -------------             either this one or number 2 will work
4 try "sudo modprobe remove drm"       ----------         this will tell the kernel to remove the module drm, wont work unless radeon has been removed first bc it depends on this like fglrx does
5 try "sudo modprobe fglrx"     ----------      this will install fglrx, this wont work unless drm has been removed bc it needs drm to install correctly
6 try "sudo modprobe drm"        -------     this SHOULD install drm and attach it to the fglrx module as a dependency kind of,     I get an error saying it cant allocate enough memory to install correctly. See if you get the same thing, if ya dont it might fix this whole mess and we mighta actually figured this shit out


I think this is our problem right here. After the fglrx module is inserted correctly, DRM wont load onto it. If anyone out there has experience with the DRM module, speak up please hehe :)

-
-

Information on DRM - [http://dri.freedesktop.org/wiki/DRM](http://dri.freedesktop.org/wiki/DRM)
Information on DRI - [http://dri.freedesktop.org/wiki/FrontPage](http://dri.freedesktop.org/wiki/FrontPage)

EDIT
Ok now im reading on the DRM mailing list that drm and fglrx cant be installed at the same time because they both try to run the same piece of hardware. So maybe im on the complete wrong track hehe :(

---

### Post by pailhead on 2005-07-24
[QUOTE=mjkelly]Heres the important part:
Jul 23 21:00:44 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 917 MBytes.
Jul 23 21:00:44 localhost kernel: [fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
Jul 23 21:00:44 localhost kernel: [fglrx:firegl_unlock] *ERROR* Process 7418 using kernel context 0

Ive never seen that error before. I dont think its related to this, bc mine didnt have it and i had the same black screen you have. Whats your fullscreen glxgears score? Whats "modprobe fglrx" look like? Whats "fglrxinfo" look like?[/quote]

Well ran both and got nothing.  I'm not having the black screen issue since I installed the ATI downloaded drivers.  Now I'm getting this error, which I got when I ran "fglrxinfo"

```
root@ubuntu:/home/pailhead # fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
``` 

wish just installing drivers like these were like on Windows  ](*,)

---

### Post by mjkelly on 2005-07-25
Yeah but ati has made giant improvements in linux drivers and such. Im such Breezy wont have any sort of ati problems like this. I didnt have half as much trouble with fedora core 4. Still i think ubuntu is much better tho. Just personal preference tho.

About the drivers, im back at step one myself. Im just going to keep the radeon driver with drm installed. Its weird too... if i install xorg-fglrx package off of synaptic my glxgears score goes from ~550 to ~175 fps (smallscreen), even if i dont change the modules that are loaded or my xorg.conf or anything. Like right now im getting 575fps, but now ill go into synaptic and install that package and now its 175. I didnt change anything, no other modules have been loaded. Wtf????? How can that happen??? Now all i do is uninstall the package and its back to 550. Isnt that strange?

Does anyone have any advice on tweaking the "radeon" driver or the DRM driver to get better performance from a radeon card? I was talking to someone on #ubuntu a little while ago who was getting 2000fps using the radeon driver but we couldnt figure out how.

---

### Post by JayCnrs on 2005-07-25
I was having a similar problem except with Nvidia drivers. Try lsmod | grep intel_agp.  If this module shows you can try blacklisting that module, I found it was causing conflicts with the Nvidia drivers. Go to **/etc/hotplug** then edit the blacklist file by using **sudo pico blacklist** at the end add **intel_agp**

---

