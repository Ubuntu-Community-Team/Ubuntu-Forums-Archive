---
title: "Very odd blank screen after nvidia driver install"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by Devrethman on 2007-10-09
I've just installed ubuntu on my laptop, cause I need it to just work (I use gentoo on my other boxen, but I don't trust it with anything required to observe deadlines) so I'm quite well versed in the ways of this linucks thing, but a complete noob to ubuntu. I used the restricted drivers manager thing to install the nvidia drivers, and after rebooting, when X would normally start, my screen just dies. It doesn't blank, it flashes, turns black, and then kind of fades to white in a method that freaked me out because I thought I had just permanently messed it up. The little bongo sound that GDM normally makes still plays, and I can imagine my computer singing Pink Floyd's "comfortably numb" while wondering where my username and password are. Enough of that. 
I have a Toshiba 5105-S901 laptop with an MX440-go graphics chip and a brandless LCD screen which does 1600x1200 at 60hz, and here's my xorg.log:
```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux inu 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct  8 22:39:48 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV17 [GeForce4 440 Go]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
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
(II) PCI: 00:00:0: chip 8086,1a30 card 1179,0001 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2482 card 1179,0001 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2484 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2487 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 42 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,248c card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,248a card 1179,0001 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,2485 card 1179,0002 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,2486 card 1179,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0174 card 1179,0001 rev a3 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 104c,8023 card 1179,0001 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:08:0: chip 8086,1031 card 1179,0001 rev 42 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 104c,ac50 card 0000,0000 rev 01 class 06,07,00 hdr 02
(II) PCI: 02:0b:0: chip 1179,0617 card d800,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0b:1: chip 1179,0617 card 1c00,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0c:0: chip 1179,0804 card 1179,0001 rev 03 class 08,80,00 hdr 00
(II) PCI: 02:0d:0: chip 1179,0805 card 1179,0001 rev 03 class 08,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,9), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd7f00000 - 0xdfffffff (0x8100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,12), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfce00000 - 0xfcefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x3bffffff (0xc000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:10:0), (2,3,4), BCTRL: 0x0540 (VGA_EN is cleared)
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (2:11:0), (2,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[1] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x34000000 - 0x37ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (2:11:1), (2,9,12), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 9 prefetchable memory range:
	[0] -1	0	0x38000000 - 0x3bffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 440 Go] rev 163, Mem @ 0xfd000000/24, 0xd8000000/27, 0xd7f80000/19
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
	[0] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[1] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[2] -1	0	0xfce07000 - 0xfce077ff (0x800) MX[B]
	[3] -1	0	0x3c000000 - 0x3c0003ff (0x400) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[6] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[9] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[10] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[11] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[12] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[13] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfce07800 - 0xfce079ff (0x200) MX[B]
	[1] -1	0	0xfce07a00 - 0xfce07a1f (0x20) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[1] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[2] -1	0	0xfce07000 - 0xfce077ff (0x800) MX[B]
	[3] -1	0	0x3c000000 - 0x3c0003ff (0x400) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[6] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[7] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[9] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[10] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[11] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[12] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[13] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfce07800 - 0xfce079ff (0x200) MX[B]
	[1] -1	0	0xfce07a00 - 0xfce07a1f (0x20) MX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3bffffff (0x3bf00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3bffffff (0x3bf00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[5] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[6] -1	0	0xfce07000 - 0xfce077ff (0x800) MX[B]
	[7] -1	0	0x3c000000 - 0x3c0003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0xfce07800 - 0xfce079ff (0x200) MX[B]
	[13] -1	0	0xfce07a00 - 0xfce07a1f (0x20) MX[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[17] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[27] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[28] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3bffffff (0x3bf00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[5] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[6] -1	0	0xfce07000 - 0xfce077ff (0x800) MX[B]
	[7] -1	0	0x3c000000 - 0x3c0003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0xfce07800 - 0xfce079ff (0x200) MX[B]
	[13] -1	0	0xfce07a00 - 0xfce07a1f (0x20) MX[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[17] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[27] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[28] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3bffffff (0x3bf00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[5] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[6] -1	0	0xfce07000 - 0xfce077ff (0x800) MX[B]
	[7] -1	0	0x3c000000 - 0x3c0003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0xfce07800 - 0xfce079ff (0x200) MX[B]
	[13] -1	0	0xfce07a00 - 0xfce07a1f (0x20) MX[B]
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[20] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[21] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[23] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[24] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[30] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[31] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce4 440 Go at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.00.41.c5
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 440 Go at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 224.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3bffffff (0x3bf00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[8] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[9] -1	0	0xfce07000 - 0xfce077ff (0x800) MX[B]
	[10] -1	0	0x3c000000 - 0x3c0003ff (0x400) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0xfce07800 - 0xfce079ff (0x200) MX[B]
	[16] -1	0	0xfce07a00 - 0xfce07a1f (0x20) MX[B]
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000df40 - 0x0000df7f (0x40) IX[B]
	[23] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[24] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[25] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[26] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[27] -1	0	0x0000cfa0 - 0x0000cfaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[33] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[34] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms" "true"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
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
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 17 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
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
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

If you need it, I can kill it again and get the Xorg.conf that's causing the crash, but I can't imagine that it's any different from anyone else's (I know my vertrefresh and horizsync are right, so that's not causing it)

I also searched the forum and found a couple other people with the same-ish problem, but no real solutions (to any of theirs or to mine)
Thanks in advance for any help :lolflag: (Sorry, i just had to try that smiley, the ones on the gentoo forum are so bland...)

---

### Post by Devrethman on 2007-10-09
=bump=

---

### Post by r3uk on 2007-10-12
Hello.

I have the same problem on my Toshiba laptop. Your GeForce chipset is detecting a non existent CRT display over the built-in LCD laptop display. The clues are in your log file here:

(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 224.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.

Press CTRL-ALT-F1 to for a command line login then try putting this line into the Device section of xorg.conf:

Options "ConnectedMonitor" "DFP-0"

Alternatively, try:

Options "UseDisplayDevice" "DFP-0"

Save xorg.conf and restart X (sudo /etc/init.d/gdm restart    or CTRL-ALT-BACKSPACE)

Either line worked for me and got me back to a graphical login. My only remaining problem is that my top resolution of 1600x1200 isn't working (although I have 1280x1024) - need to work further on that.

Hope this helps.

---

