---
title: "ATI Sapphire X1600Pro PCIe (fglrx 8.36.5)   - Still not working :("
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by pupdawg on 2007-04-19
I've been using Ubuntu for a few years now and have loved it... I'm very excited for Feisty now but I've been having no luck with my Video card that worked fine in Edgy.   I had been thinking it was because the fglrx driver did not support the new kernel or X 7.2 but now they do and still this card will not work.   

What happens when I load the drivers from ATI or using restricted modules the system will boot to a black screen and seems to have froze there.   The last time I have this card working was with fglrx 8.28 something and Edgy.  Does anyone have any idea how to figure this one out ?

Thanks

---

### Post by pupdawg on 2007-04-22
Here is my Xorg.log file... if anyone can help :)  The end result is a black screen and Ctrl, Alt, Backspace will not work and the system seems to hang.


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux pupdawg-linux 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 19 19:25:12 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
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
(II) PCI: 00:00:0: chip 10de,02f5 card 1462,7207 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1462,7207 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1462,7207 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1462,7207 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1462,7207 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1462,7207 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1462,7207 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1462,7207 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 1462,7207 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0261 card 1462,7207 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1462,7207 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1462,7207 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1462,7207 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1462,7207 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:14:0: chip 10de,0269 card 1462,7207 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 1002,71c2 card 174b,0840 rev 00 class 03,00,00 hdr 80
(II) PCI: 03:00:1: chip 1002,71e2 card 174b,0841 rev 00 class 03,80,00 hdr 00
(II) PCI: 04:06:0: chip 1033,0035 card 1033,0035 rev 43 class 0c,03,10 hdr 80
(II) PCI: 04:06:1: chip 1033,0035 card 1033,0035 rev 43 class 0c,03,10 hdr 00
(II) PCI: 04:06:2: chip 1033,00e0 card 0ee4,3383 rev 04 class 0c,03,20 hdr 00
(II) PCI: 04:07:0: chip 1106,3044 card 1106,3044 rev 46 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(3:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0xd0000000/28, 0xfeaf0000/16, I/O @ 0xd000/8, BIOS @ 0xfeac0000/17
(--) PCI: (3:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xfeae0000/16
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
	[0] -1	0	0xfebfd000 - 0xfebfd7ff (0x800) MX[B]
	[1] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[2] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[3] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[4] -1	0	0xfe9bc000 - 0xfe9bcfff (0x1000) MX[B]
	[5] -1	0	0xfe9bec00 - 0xfe9becff (0x100) MX[B]
	[6] -1	0	0xfe9bf000 - 0xfe9bffff (0x1000) MX[B]
	[7] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[8] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[9] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[15] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebfd000 - 0xfebfd7ff (0x800) MX[B]
	[1] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[2] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[3] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[4] -1	0	0xfe9bc000 - 0xfe9bcfff (0x1000) MX[B]
	[5] -1	0	0xfe9bec00 - 0xfe9becff (0x100) MX[B]
	[6] -1	0	0xfe9bf000 - 0xfe9bffff (0x1000) MX[B]
	[7] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[8] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[9] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[15] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfebfd000 - 0xfebfd7ff (0x800) MX[B]
	[5] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[8] -1	0	0xfe9bc000 - 0xfe9bcfff (0x1000) MX[B]
	[9] -1	0	0xfe9bec00 - 0xfe9becff (0x100) MX[B]
	[10] -1	0	0xfe9bf000 - 0xfe9bffff (0x1000) MX[B]
	[11] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[12] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[13] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[21] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.36.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) Primary Device is: PCI 03:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.36.5
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.36g1                           
(II) ATI Proprietary Linux Driver Build Date: Apr 17 2007 10:04:24
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.36.1.1.2.3-driver-lnx-x86-x86_64-338188
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x71C2) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfd000 - 0xfebfd7ff (0x800) MX[B]
	[5] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[8] -1	0	0xfe9bc000 - 0xfe9bcfff (0x1000) MX[B]
	[9] -1	0	0xfe9bec00 - 0xfe9becff (0x100) MX[B]
	[10] -1	0	0xfe9bf000 - 0xfe9bffff (0x1000) MX[B]
	[11] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[12] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[13] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[21] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e4650
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfd000 - 0xfebfd7ff (0x800) MX[B]
	[5] -1	0	0xfebfdc00 - 0xfebfdcff (0x100) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[8] -1	0	0xfe9bc000 - 0xfe9bcfff (0x1000) MX[B]
	[9] -1	0	0xfe9bec00 - 0xfe9becff (0x100) MX[B]
	[10] -1	0	0xfe9bf000 - 0xfe9bffff (0x1000) MX[B]
	[11] -1	0	0xfeae0000 - 0xfeaeffff (0x10000) MX[B](B)
	[12] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[13] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[24] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 3 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1600 Series" (Chipset = 0x71c2)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0840)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfeaf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.36.5
	ABI class: X.Org Server Extension, version 0.3

---

### Post by lavinog on 2007-04-24
first of all this web site is pretty helpful with ati drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

can you post your /etc/X11/xorg.conf

did you use the manual installation?

did you:
```
Section "Extensions"
        Option  "Composite" "Disable" 
EndSection
```
also
> Note: Use "0" instead of "Disable" if you get the black screen of death. 

also check out the section at the bottom of the page that says:
>  If suspend is not working

If after fglrx installation suspend stops working, meaning it suspends not start and just gives black screen. Then changing a few options is reported to work for some hardware (Bug 84991 ). 

what i have noticed is that ati is listing xorg 7.2.0 on one page and not on all of their other pages, so i have to wonder if the 8.36.5 driver actually supports 7.2

i have a ati radeon express 200m and can boot and use 2d just fine, but cant get this driver to load yet for 3d or the overlay.
i noticed that both of our xorg.logs say:
> (II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.36.5


i expect that ati will be releasing another driver soon.

---

