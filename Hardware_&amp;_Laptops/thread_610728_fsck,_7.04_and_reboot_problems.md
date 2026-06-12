---
title: "fsck, 7.04 and reboot problems"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by hunkybill on 2007-11-12
Hi,

I am looking for some troubleshooting tips with my 7.04 installation on my Fujitsu Lifebook. Whenever the fsck checks kick in, after the preset 20 or 30 reboots, the boot process shows me that it is checking a drive like /dev/sda2 or whatever happens to need fsck processing.

When the check completes (with no problems).. the next stages of boot, invoking X for example, always seem to lock up and fail. I can see the screen go dark, go backlight, go dark, go backlight, as if X is confused and trying to figure out what to do. I wait 5 minutes and when nothing happens, I simply reboot. This second reboot goes fine and X fires up and I am in business again.

This is clearly not an optimal situation. fsck seems to work fine, and I know my X is fine, it is simply the combination of the two at boot-up where they don't mix... any tips???

---

### Post by morgan_greywolf on 2007-11-12
It looks like your X server is in a state of constantly restarting after the fsck.  This is usually due to some failure to initialize the video card.  Could you post the Xorg.0.log from one of these sessions?  Juist boot the machine, when the screen cycles like that reboot and the file you're looking to post is Xorg.0.log.old (as opposed to Xorg.0.log, which is for your current session.)

---

### Post by hunkybill on 2007-11-13
Thanks for the response morgan_greywolf! I opened up the log for the old file and I checked it out. It does not expose any obvious errors to me, but then I am perhaps not very skilled at deciphering problems with X.org logs. I will post the old one here now for clarity... and hopefully the next time this happens, I will be sure to grab the .old file immediately after a positive reboot, for further analysis.

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux unconcious.cryptonomicon.com 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 11 15:31:42 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "MX Revolution Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(II) No default mouse found, adding one
(**) |-->Input Device "<default pointer>"
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
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 8086,27a0 card 10cf,1378 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 10cf,1397 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 10cf,1389 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 10cf,1389 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 10cf,138a rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 10cf,1384 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 10cf,1385 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 10cf,1387 rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 10cf,1388 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7145 card 10cf,139e rev 00 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4363 card 10cf,139a rev 12 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 8086,4222 card 8086,1000 rev 02 class 02,80,00 hdr 00
(II) PCI: 08:03:0: chip 1217,7134 card 4001,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 08:03:1: chip 1217,7134 card 4801,0000 rev 21 class 06,07,00 hdr 82
(II) PCI: 08:03:2: chip 1217,7120 card 10cf,131e rev 01 class 08,05,00 hdr 00
(II) PCI: 08:03:3: chip 1217,7130 card 10cf,131e rev 01 class 06,80,00 hdr 00
(II) PCI: 08:03:4: chip 1217,00f7 card 1217,00f7 rev 02 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf00fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf0100000 - 0xf01fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x90000000 - 0x900fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x90100000 - 0x901fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:30:0), (0,8,16), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 8 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 8 non-prefetchable memory range:
	[0] -1	0	0xf0300000 - 0xf03fffff (0x100000) MX[B]
(II) Bus 8 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8fffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 9: bridge is at (8:3:0), (8,9,12), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 9 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
(II) Bus 9 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 13: bridge is at (8:3:1), (8,13,16), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[1] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0x8c000000 - 0x8fffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility X1400 rev 0, Mem @ 0xe0000000/28, 0xf0000000/16, I/O @ 0x2000/8
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
	[0] -1	0	0xf0300800 - 0xf0300fff (0x800) MX[B]
	[1] -1	0	0xf0302000 - 0xf0302fff (0x1000) MX[B]
	[2] -1	0	0xf0301000 - 0xf0301fff (0x1000) MX[B]
	[3] -1	0	0xf0300000 - 0xf03000ff (0x100) MX[B]
	[4] -1	0	0x90100000 - 0x90100fff (0x1000) MX[B]
	[5] -1	0	0xf0100000 - 0xf0103fff (0x4000) MX[B]
	[6] -1	0	0xf0604400 - 0xf06047ff (0x400) MX[B]
	[7] -1	0	0xf0604000 - 0xf06043ff (0x400) MX[B]
	[8] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[9] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[12] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[15] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[16] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[27] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf0300800 - 0xf0300fff (0x800) MX[B]
	[1] -1	0	0xf0302000 - 0xf0302fff (0x1000) MX[B]
	[2] -1	0	0xf0301000 - 0xf0301fff (0x1000) MX[B]
	[3] -1	0	0xf0300000 - 0xf03000ff (0x100) MX[B]
	[4] -1	0	0x90100000 - 0x90100fff (0x1000) MX[B]
	[5] -1	0	0xf0100000 - 0xf0103fff (0x4000) MX[B]
	[6] -1	0	0xf0604400 - 0xf06047ff (0x400) MX[B]
	[7] -1	0	0xf0604000 - 0xf06043ff (0x400) MX[B]
	[8] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[9] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[12] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[15] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[16] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[17] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[18] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[27] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
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
	[4] -1	0	0xf0300800 - 0xf0300fff (0x800) MX[B]
	[5] -1	0	0xf0302000 - 0xf0302fff (0x1000) MX[B]
	[6] -1	0	0xf0301000 - 0xf0301fff (0x1000) MX[B]
	[7] -1	0	0xf0300000 - 0xf03000ff (0x100) MX[B]
	[8] -1	0	0x90100000 - 0x90100fff (0x1000) MX[B]
	[9] -1	0	0xf0100000 - 0xf0103fff (0x4000) MX[B]
	[10] -1	0	0xf0604400 - 0xf06047ff (0x400) MX[B]
	[11] -1	0	0xf0604000 - 0xf06043ff (0x400) MX[B]
	[12] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[13] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[18] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[19] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[20] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[21] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[22] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[23] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[24] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
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
(**) AIGLX disabled
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
	compiled for 7.1.0, module version = 8.38.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.38.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.38g1                           
(II) ATI Proprietary Linux Driver Build Date: Jun 22 2007 13:10:21
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.38.1.1.2.3-driver-lnx-x86-x86_64-351593
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x7145) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0300800 - 0xf0300fff (0x800) MX[B]
	[5] -1	0	0xf0302000 - 0xf0302fff (0x1000) MX[B]
	[6] -1	0	0xf0301000 - 0xf0301fff (0x1000) MX[B]
	[7] -1	0	0xf0300000 - 0xf03000ff (0x100) MX[B]
	[8] -1	0	0x90100000 - 0x90100fff (0x1000) MX[B]
	[9] -1	0	0xf0100000 - 0xf0103fff (0x4000) MX[B]
	[10] -1	0	0xf0604400 - 0xf06047ff (0x400) MX[B]
	[11] -1	0	0xf0604000 - 0xf06043ff (0x400) MX[B]
	[12] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[13] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[18] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[19] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[20] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[21] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[22] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[23] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[24] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e7cd0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0300800 - 0xf0300fff (0x800) MX[B]
	[5] -1	0	0xf0302000 - 0xf0302fff (0x1000) MX[B]
	[6] -1	0	0xf0301000 - 0xf0301fff (0x1000) MX[B]
	[7] -1	0	0xf0300000 - 0xf03000ff (0x100) MX[B]
	[8] -1	0	0x90100000 - 0x90100fff (0x1000) MX[B]
	[9] -1	0	0xf0100000 - 0xf0103fff (0x4000) MX[B]
	[10] -1	0	0xf0604400 - 0xf06047ff (0x400) MX[B]
	[11] -1	0	0xf0604000 - 0xf06043ff (0x400) MX[B]
	[12] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[13] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[21] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[22] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[23] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[24] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[25] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[26] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[27] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[36] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "dri" "true"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
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
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1400" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x10cf, PciSubDevice = 0x139e)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xf0000000
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
(II) fglrx(0): VESA VBE OEM Product: M54P
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
	compiled for 7.1.0, module version = 8.38.6
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 60  vid: 16497
(II) fglrx(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.2 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1052  v_sync_end 1058 v_blanking: 1096 v_border: 0
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00367f000000000000
(II) fglrx(0): 	0000010380281e00f200000000000000
(II) fglrx(0): 	00000021080031404540614071408140
(II) fglrx(0): 	000000000000952e90a0601a2e403020
(II) fglrx(0): 	26000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000012
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 439/450MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 128/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 324/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 11 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.25  1680 1728 1760 1840  1050 1052 1058 1096
(**) fglrx(0): *Mode "1280x1024": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  119.25  1280 1728 1760 1840  1024 1052 1058 1096
(**) fglrx(0): *Mode "1152x864": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.25  1152 1728 1760 1840  864 1052 1058 1096
(**) fglrx(0): *Mode "1024x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  119.25  1024 1728 1760 1840  768 1052 1058 1096
(**) fglrx(0): *Mode "800x600": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  119.25  800 1728 1760 1840  600 1052 1058 1096
(**) fglrx(0): *Mode "640x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  119.25  640 1728 1760 1840  480 1052 1058 1096
(**) fglrx(0):  Default mode "640x400": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  119.25  640 1728 1760 1840  400 1052 1058 1096
(**) fglrx(0):  Default mode "512x384": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  119.25  512 1728 1760 1840  384 1052 1058 1096
(**) fglrx(0):  Default mode "400x300": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  119.25  400 1728 1760 1840  300 1052 1058 1096
(**) fglrx(0):  Default mode "320x240": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  119.25  320 1728 1760 1840  240 1052 1058 1096
(**) fglrx(0):  Default mode "320x200": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  119.25  320 1728 1760 1840  200 1052 1058 1096
(--) fglrx(0): Display dimensions: (400, 300) mm
(--) fglrx(0): DPI set to (106, 88)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.25  1680 1728 1760 1840  1050 1052 1058 1096
(**) fglrx(0): *Mode "1280x1024": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  119.25  1280 1728 1760 1840  1024 1052 1058 1096
(**) fglrx(0): *Mode "1152x864": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.25  1152 1728 1760 1840  864 1052 1058 1096
(**) fglrx(0): *Mode "1024x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  119.25  1024 1728 1760 1840  768 1052 1058 1096
(**) fglrx(0): *Mode "800x600": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  119.25  800 1728 1760 1840  600 1052 1058 1096
(**) fglrx(0): *Mode "640x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  119.25  640 1728 1760 1840  480 1052 1058 1096
(**) fglrx(0):  Default mode "640x400": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  119.25  640 1728 1760 1840  400 1052 1058 1096
(**) fglrx(0):  Default mode "512x384": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  119.25  512 1728 1760 1840  384 1052 1058 1096
(**) fglrx(0):  Default mode "400x300": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  119.25  400 1728 1760 1840  300 1052 1058 1096
(**) fglrx(0):  Default mode "320x240": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  119.25  320 1728 1760 1840  240 1052 1058 1096
(**) fglrx(0):  Default mode "320x200": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  119.25  320 1728 1760 1840  200 1052 1058 1096
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) LoadModule: "glesx.so" (glesx)
(WW) LoadModule: given non-canonical module name "glesx.so"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0000000 - 0xf000ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf0300800 - 0xf0300fff (0x800) MX[B]
	[7] -1	0	0xf0302000 - 0xf0302fff (0x1000) MX[B]
	[8] -1	0	0xf0301000 - 0xf0301fff (0x1000) MX[B]
	[9] -1	0	0xf0300000 - 0xf03000ff (0x100) MX[B]
	[10] -1	0	0x90100000 - 0x90100fff (0x1000) MX[B]
	[11] -1	0	0xf0100000 - 0xf0103fff (0x4000) MX[B]
	[12] -1	0	0xf0604400 - 0xf06047ff (0x400) MX[B]
	[13] -1	0	0xf0604000 - 0xf06043ff (0x400) MX[B]
	[14] -1	0	0xf0600000 - 0xf0603fff (0x4000) MX[B]
	[15] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[24] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[25] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[26] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[27] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[28] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[29] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[30] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[36] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[37] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[38] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[39] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
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
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7cb9000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.38.6
(II) fglrx(0):     Date: Jun 22 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x008f7000
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,1360)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 304
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
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
		26 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "ColorTiling" is not used
(WW) fglrx(0): Option "EnablePageFlip" is not used
(WW) fglrx(0): Option "AccelMethod" is not used
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
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
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(II) evdev brain: Rescanning devices (1).
(**) Option "SendCoreEvents"
(**) MX Revolution Mouse-PNP0C0C/button/input0: always reports core events
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "SHMConfig" "on"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "CorePointer"
(**) Synaptics Touchpad: Core Pointer
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "MX Revolution Mouse-PNP0C0C/button/input0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) MX Revolution Mouse-PNP0C0C/button/input0: Init
Synaptics DeviceInit called
SynapticsCtrl called.
(II) evdev brain: Rescanning devices (2).
(II) MX Revolution Mouse-PNP0C0C/button/input0: On
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) evdev brain: Rescanning devices (3).
(II) evdev brain: Rescanning devices (4).
SynapticsCtrl called.
SynapticsCtrl called.
SynapticsCtrl called.
Synaptics DeviceOff called
(II) MX Revolution Mouse-PNP0C0C/button/input0: Off
(II) UnloadModule: "evdev"
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7cb9000
```

---

