---
title: "nvidia 8600m gt optimization"
date: 2008-07-30
forum: Hardware
---

### Post by shrndegruv on 2008-07-30
I was wondering if anyone with this card (I have a Dell M1530) has optimized the the default xorg.conf?  I am using the nvidia drivers xubuntu came with - so i havent updated the driver.  Im just wondering if performance can be increased by enabling some modules in the xorg.conf....

In general compiz performs pretty well. The only thing i notice is that closing/minimizing/maximizing windows  has a short lag (with the fade effect).  

I read that all 8000 level cards have a fundamental flaw related to heat.  the gpu heat never goes above 65 degress (threshold is in the 100 range).  has anyone experience problems?

---

### Post by tuxxy on 2008-07-30
I run the 8600GTS flawlessly in GNOME, all 3D modes and effects are fantastic.

---

### Post by shrndegruv on 2008-07-30
did you enable blurring?

---

### Post by tuxxy on 2008-07-30
I dont remember doing so no, is it in nvidia-settings?

---

### Post by shrndegruv on 2008-07-30
no its a compiz thing.  are you using gnomes effects or compiz?

---

### Post by tuxxy on 2008-07-30
Im using compiz fusion and Emerald for the window management, still dont remember a blurring option Im afraid :(

---

### Post by shrndegruv on 2008-07-30
its in the compiz-config settings manager.

---

### Post by tuxxy on 2008-07-30
Yes I gathered that, where exactly is its location and ill have a look for you.

---

### Post by shrndegruv on 2008-07-30
I don't know its exact location -- it looks like a red circle and has the pattern blur* in it.  should be easy to find ;)

in any event, i was wondering if anyone has added stuff to their xorg.conf to increase performance....

---

### Post by varun.s on 2008-08-05
hi shrndegruv

i am having problem in installing Ubuntu on M1530
can you have a look into these attachments

Xorg.0.log
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug  4 23:25:54 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NVIDIA Default Card"
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
(II) PCI: 00:00:0: chip 8086,2a00 card 1028,022e rev 0c class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2a01 card 0000,0000 rev 0c class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,022e rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,022e rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,022e rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,022e rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,022e rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,022e rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,022e rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,022e rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card 1028,022e rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 1028,022e rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2829 card 1028,022e rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,022e rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0407 card 1028,022e rev a1 class 03,00,00 hdr 00
(II) PCI: 03:09:0: chip 1180,0832 card 1028,022e rev 05 class 0c,00,10 hdr 80
(II) PCI: 03:09:1: chip 1180,0822 card 1028,022e rev 22 class 08,05,01 hdr 80
(II) PCI: 03:09:2: chip 1180,0843 card 1028,022e rev 12 class 08,80,00 hdr 80
(II) PCI: 03:09:3: chip 1180,0592 card 1028,022e rev 12 class 08,80,00 hdr 80
(II) PCI: 03:09:4: chip 1180,0852 card 1028,022e rev 12 class 08,80,00 hdr 80
(II) PCI: 09:00:0: chip 11ab,4354 card 1028,022e rev 12 class 02,00,00 hdr 00
(II) PCI: 0b:00:0: chip 8086,4229 card 8086,1120 rev 61 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,12), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[b]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfeafffff (0x4b00000) MX[b]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:28:0), (0,9,9), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 9 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[b]
(II) Bus 9 non-prefetchable memory range:
	[0] -1	0	0xf9f00000 - 0xf9ffffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:1), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 11 non-prefetchable memory range:
	[0] -1	0	0xf9e00000 - 0xf9efffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:4), (0,12,13), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[b]
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xf9c00000 - 0xf9dfffff (0x200000) MX[b]
(II) Bus 12 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf01fffff (0x200000) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf9b00000 - 0xf9bfffff (0x100000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0407) rev 161, Mem @ 0xfd000000/24, 0xe0000000/28, 0xfa000000/25, I/O @ 0xef00/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[b]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[b]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[b]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[b]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[b]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
	[0] -1	0	0xf9efe000 - 0xf9efffff (0x2000) MX[b]
	[1] -1	0	0xf9ffc000 - 0xf9ffffff (0x4000) MX[b]
	[2] -1	0	0xf9bff700 - 0xf9bff7ff (0x100) MX[b]
	[3] -1	0	0xf9bff600 - 0xf9bff6ff (0x100) MX[b]
	[4] -1	0	0xf9bff500 - 0xf9bff5ff (0x100) MX[b]
	[5] -1	0	0xf9bff400 - 0xf9bff4ff (0x100) MX[b]
	[6] -1	0	0xf9bff800 - 0xf9bfffff (0x800) MX[b]
	[7] -1	0	0xfebfb700 - 0xfebfb7ff (0x100) MX[b]
	[8] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[b]
	[9] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[b]
	[10] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[b]
	[11] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[b]
	[12] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[b](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
	[15] -1	0	0x0000de00 - 0x0000deff (0x100) IX[b]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[b]
	[17] -1	0	0x00006ee0 - 0x00006eff (0x20) IX[b]
	[18] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[b]
	[19] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[b]
	[20] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[b]
	[21] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[b]
	[22] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[b]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[b]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[b]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[b]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[b]
	[27] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[b]
	[28] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[b]
	[29] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[b]
	[30] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[b]
	[31] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[b]
	[32] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf9efe000 - 0xf9efffff (0x2000) MX[b]
	[1] -1	0	0xf9ffc000 - 0xf9ffffff (0x4000) MX[b]
	[2] -1	0	0xf9bff700 - 0xf9bff7ff (0x100) MX[b]
	[3] -1	0	0xf9bff600 - 0xf9bff6ff (0x100) MX[b]
	[4] -1	0	0xf9bff500 - 0xf9bff5ff (0x100) MX[b]
	[5] -1	0	0xf9bff400 - 0xf9bff4ff (0x100) MX[b]
	[6] -1	0	0xf9bff800 - 0xf9bfffff (0x800) MX[b]
	[7] -1	0	0xfebfb700 - 0xfebfb7ff (0x100) MX[b]
	[8] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[b]
	[9] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[b]
	[10] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[b]
	[11] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[b]
	[12] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[b](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
	[15] -1	0	0x0000de00 - 0x0000deff (0x100) IX[b]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[b]
	[17] -1	0	0x00006ee0 - 0x00006eff (0x20) IX[b]
	[18] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[b]
	[19] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[b]
	[20] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[b]
	[21] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[b]
	[22] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[b]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[b]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[b]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[b]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[b]
	[27] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[b]
	[28] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[b]
	[29] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[b]
	[30] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[b]
	[31] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[b]
	[32] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[b]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[b]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[b]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[b]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[b]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[b]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[b]
	[4] -1	0	0xf9efe000 - 0xf9efffff (0x2000) MX[b]
	[5] -1	0	0xf9ffc000 - 0xf9ffffff (0x4000) MX[b]
	[6] -1	0	0xf9bff700 - 0xf9bff7ff (0x100) MX[b]
	[7] -1	0	0xf9bff600 - 0xf9bff6ff (0x100) MX[b]
	[8] -1	0	0xf9bff500 - 0xf9bff5ff (0x100) MX[b]
	[9] -1	0	0xf9bff400 - 0xf9bff4ff (0x100) MX[b]
	[10] -1	0	0xf9bff800 - 0xf9bfffff (0x800) MX[b]
	[11] -1	0	0xfebfb700 - 0xfebfb7ff (0x100) MX[b]
	[12] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[b]
	[13] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[b]
	[14] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[b]
	[15] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[b]
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[b](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[b]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[b]
	[21] -1	0	0x0000de00 - 0x0000deff (0x100) IX[b]
	[22] -1	0	0x000010c0 - 0x000010df (0x20) IX[b]
	[23] -1	0	0x00006ee0 - 0x00006eff (0x20) IX[b]
	[24] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[b]
	[25] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[b]
	[26] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[b]
	[27] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[b]
	[28] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[b]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[b]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[b]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[b]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[b]
	[33] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[b]
	[34] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[b]
	[35] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[b]
	[36] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[b]
	[37] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[b]
	[38] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[b](B)
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
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 2.0.0
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	Quadro FX 5600, Quadro FX 4600


Contd... in next post
```

---

### Post by varun.s on 2008-08-05
```
(II) Primary Device is: PCI 01:00:0
(--) Chipset Unknown NVIDIA chip found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[b]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[b]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[b]
	[4] -1	0	0xf9efe000 - 0xf9efffff (0x2000) MX[b]
	[5] -1	0	0xf9ffc000 - 0xf9ffffff (0x4000) MX[b]
	[6] -1	0	0xf9bff700 - 0xf9bff7ff (0x100) MX[b]
	[7] -1	0	0xf9bff600 - 0xf9bff6ff (0x100) MX[b]
	[8] -1	0	0xf9bff500 - 0xf9bff5ff (0x100) MX[b]
	[9] -1	0	0xf9bff400 - 0xf9bff4ff (0x100) MX[b]
	[10] -1	0	0xf9bff800 - 0xf9bfffff (0x800) MX[b]
	[11] -1	0	0xfebfb700 - 0xfebfb7ff (0x100) MX[b]
	[12] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[b]
	[13] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[b]
	[14] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[b]
	[15] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[b]
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[b](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[b]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[b]
	[21] -1	0	0x0000de00 - 0x0000deff (0x100) IX[b]
	[22] -1	0	0x000010c0 - 0x000010df (0x20) IX[b]
	[23] -1	0	0x00006ee0 - 0x00006eff (0x20) IX[b]
	[24] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[b]
	[25] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[b]
	[26] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[b]
	[27] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[b]
	[28] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[b]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[b]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[b]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[b]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[b]
	[33] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[b]
	[34] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[b]
	[35] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[b]
	[36] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[b]
	[37] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[b]
	[38] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[b](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[b]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[b]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[b]
	[4] -1	0	0xf9efe000 - 0xf9efffff (0x2000) MX[b]
	[5] -1	0	0xf9ffc000 - 0xf9ffffff (0x4000) MX[b]
	[6] -1	0	0xf9bff700 - 0xf9bff7ff (0x100) MX[b]
	[7] -1	0	0xf9bff600 - 0xf9bff6ff (0x100) MX[b]
	[8] -1	0	0xf9bff500 - 0xf9bff5ff (0x100) MX[b]
	[9] -1	0	0xf9bff400 - 0xf9bff4ff (0x100) MX[b]
	[10] -1	0	0xf9bff800 - 0xf9bfffff (0x800) MX[b]
	[11] -1	0	0xfebfb700 - 0xfebfb7ff (0x100) MX[b]
	[12] -1	0	0xfebfb800 - 0xfebfbfff (0x800) MX[b]
	[13] -1	0	0xfed1c000 - 0xfed1c3ff (0x400) MX[b]
	[14] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[b]
	[15] -1	0	0xfed1c400 - 0xfed1c7ff (0x400) MX[b]
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[b](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[b]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[b]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[b]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[b]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[b]
	[24] -1	0	0x0000de00 - 0x0000deff (0x100) IX[b]
	[25] -1	0	0x000010c0 - 0x000010df (0x20) IX[b]
	[26] -1	0	0x00006ee0 - 0x00006eff (0x20) IX[b]
	[27] -1	0	0x00006ec8 - 0x00006ecb (0x4) IX[b]
	[28] -1	0	0x00006ec0 - 0x00006ec7 (0x8) IX[b]
	[29] -1	0	0x00006eb8 - 0x00006ebb (0x4) IX[b]
	[30] -1	0	0x00006eb0 - 0x00006eb7 (0x8) IX[b]
	[31] -1	0	0x00006fa0 - 0x00006faf (0x10) IX[b]
	[32] -1	0	0x00000374 - 0x00000374 (0x1) IX[b]
	[33] -1	0	0x00000170 - 0x00000177 (0x8) IX[b]
	[34] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[b]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[b]
	[36] -1	0	0x00006f40 - 0x00006f5f (0x20) IX[b]
	[37] -1	0	0x00006f60 - 0x00006f7f (0x20) IX[b]
	[38] -1	0	0x00006f80 - 0x00006f9f (0x20) IX[b]
	[39] -1	0	0x00006f00 - 0x00006f1f (0x20) IX[b]
	[40] -1	0	0x00006f20 - 0x00006f3f (0x20) IX[b]
	[41] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[b](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[b]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) NV(0): Initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NV(0): MMIO registers at 0xfd000000
(--) NV(0): Linear framebuffer at 0xe0000000
(II) NV(0): MMIO registers mapped at 0xb6b4c000
(--) NV(0): Mapping 255.0 of 256.0 MB of video RAM
(II) NV(0): Linear framebuffer mapped at 0xa6c4c000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(--) NV(0): I2C map:
(--) NV(0):   Bus 0 -> DAC1
(--) NV(0):   Bus 1 -> SOR1
(--) NV(0):   Bus 2 -> SOR0
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): I2C bus "DDC" removed.
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): I2C bus "DDC" removed.
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): I2C bus "DDC" removed.
(--) NV(0): Trying load detection on DAC0 ... nothing.
(--) NV(0): Trying load detection on DAC1 ... nothing.
(--) NV(0): Trying load detection on DAC2 ... nothing.
(EE) NV(0): No display devices found
(II) UnloadModule: "nv"
(II) UnloadModule: "ddc"
(II) UnloadModule: "i2c"
(II) Unloading /usr/lib/xorg/modules//libi2c.so
(II) UnloadModule: "vm86"
(II) Unloading /usr/lib/xorg/modules//libvm86.so
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```


I am trying to install Feisty.
I get error regarding not able to start x server

thanks
varun

---

### Post by shrndegruv on 2008-08-05
First off, I returned my 1530 because it had an nvidia 8600, which is one of the cards that has the fundamental flaw.

I installed hardy.  The touchpad didn't work right off the bat; had to edit a file to get it to work.  Search for "install ubuntu hardy on 1530" on google and you will find a way to get around that.  or search 1530 touchpad in these forums and you will find the solution.

Second, the wireless card didn't work and the nvidia closed drivers were unavailable after clean install.  I plugged an ethernet cable and it made my system current (sudo apt-get update followed by sudo-apt-get upgrade) and after that it detected the wireless driver and nvidia driver.

So I would say install hardy.  I really can't help more as I no longer have the machine.

---

