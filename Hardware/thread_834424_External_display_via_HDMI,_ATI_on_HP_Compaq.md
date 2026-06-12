---
title: "External display via HDMI, ATI on HP Compaq"
date: 2008-06-19
forum: Hardware
---

### Post by Leazand on 2008-06-19
Hello to you all!

First of all I need to take this line to thank the helpful community on this forum. I've solved just about 90% of all my linux-related issues on this forum! :) Unfortunatly I could not find a solution to my problem this time! (it's the first time, and I've used linux for over 6 months! this forum is great!)

So, to the issue at hand. I have a HP Compaq 8510p with a ATI Radeon HD X2600 (not sure about the "X") on 8.04 LTS.

I'm trying to connect to my LCD TV, a 42" Samsung display, via HDMI. My laptop has a HDMI out, so it's no DVI adapters or anything like that. There's no image when I connect the HDMI cable from the laptop to the TV, except that the screen "flickers" and goes from "Check signal cable" to "No Signal". So there's obviously some sort of connection there.

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2600
OpenGL version string: 2.1.7412 Release

```

xrandr -q
```
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      60.0* 
   1440x900       60.0  
   1400x1050      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
   640x432        60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  

```

well that's it I guess, hope some of you can help :)

Leazand:)

---

### Post by markbuntu on 2008-06-19
Did you try rebooting or ctrl-alt-backspace with the tv on and connected?

x and the ATI driver should see it automatically.

Screen0 is most likely the laptop screen.

What does your var/log/Xorg.0.log say about what is going on?

---

### Post by Leazand on 2008-06-22
I tried rebooting several times with some different configurations, all ending up with wierd resolutions (on the laptop screen) or nothing happening at all. I never got any signal on the tv, although I will try the ctrl-alt-backspace thingy.

_Zeh log:_

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux mrlaptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 22 12:56:53 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Screen "aticonfig-Screen[1]" (1)
(**) |   |-->Monitor "aticonfig-Monitor[1]"
(**) |   |-->Device "aticonfig-Device[1]"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
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
(II) PCI: 00:00:0: chip 8086,2a00 card 103c,30c5 rev 0c class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2a01 card 0000,0000 rev 0c class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 8086,2a04 card 103c,30c5 rev 0c class 07,80,00 hdr 80
(II) PCI: 00:03:2: chip 8086,2a06 card 103c,30c5 rev 0c class 01,01,85 hdr 00
(II) PCI: 00:03:3: chip 8086,2a07 card 103c,30c5 rev 0c class 07,00,02 hdr 00
(II) PCI: 00:19:0: chip 8086,1049 card 103c,30c5 rev 03 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 103c,30c5 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 103c,30c5 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 103c,30c5 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 103c,30c5 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 103c,30c5 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 103c,30c5 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 103c,30c5 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 103c,30c5 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2811 card 103c,30c5 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 103c,30c5 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2829 card 103c,30c5 rev 03 class 01,06,01 hdr 00
(II) PCI: 01:00:0: chip 1002,9581 card 103c,30c5 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,aa08 card 103c,30c5 rev 00 class 04,03,00 hdr 80
(II) PCI: 02:06:0: chip 1180,0476 card 1400,0000 rev b9 class 06,07,00 hdr 82
(II) PCI: 02:06:1: chip 1180,0476 card 1c00,0000 rev b9 class 06,07,00 hdr 82
(II) PCI: 02:06:2: chip 1180,0832 card 103c,30c5 rev 03 class 0c,00,10 hdr 80
(II) PCI: 02:06:3: chip 1180,0822 card 103c,30c5 rev 20 class 08,05,00 hdr 80
(II) PCI: 02:06:4: chip 1180,0843 card 103c,30c5 rev 10 class 08,80,00 hdr 80
(II) PCI: 10:00:0: chip 8086,4229 card 8086,1101 rev 61 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,40), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4400000 - 0xe44fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 8: bridge is at (0:28:0), (0,8,8), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 16: bridge is at (0:28:1), (0,16,16), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 16 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe40fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 40: bridge is at (0:28:4), (0,40,40), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 40 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
	[4] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[5] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[6] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[7] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 40 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,7), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe4100000 - 0xe43fffff (0x300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:6:0), (2,3,3), BCTRL: 0x0580 (VGA_EN is cleared)
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (2:6:1), (2,4,7), BCTRL: 0x0500 (VGA_EN is cleared)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x9581) rev 0, Mem @ 0xd0000000/28, 0xe4400000/16, I/O @ 0x4000/8
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
	[0] -1	0	0xe4000000 - 0xe4001fff (0x2000) MX[B]
	[1] -1	0	0xe4104000 - 0xe41040ff (0x100) MX[B]
	[2] -1	0	0xe4103000 - 0xe41030ff (0x100) MX[B]
	[3] -1	0	0xe4102000 - 0xe41027ff (0x800) MX[B]
	[4] -1	0	0xe4410000 - 0xe4413fff (0x4000) MX[B]
	[5] -1	0	0xe4549000 - 0xe45497ff (0x800) MX[B]
	[6] -1	0	0xe4548000 - 0xe45483ff (0x400) MX[B]
	[7] -1	0	0xe4544000 - 0xe4547fff (0x4000) MX[B]
	[8] -1	0	0xe4541000 - 0xe45413ff (0x400) MX[B]
	[9] -1	0	0xe4540000 - 0xe4540fff (0x1000) MX[B]
	[10] -1	0	0xe4520000 - 0xe453ffff (0x20000) MX[B]
	[11] -1	0	0xe4501000 - 0xe4501fff (0x1000) MX[B]
	[12] -1	0	0xe4500000 - 0xe450000f (0x10) MX[B]
	[13] -1	0	0xe4400000 - 0xe440ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x00005140 - 0x0000515f (0x20) IX[B]
	[16] -1	0	0x00001574 - 0x00001577 (0x4) IX[B]
	[17] -1	0	0x00001370 - 0x00001377 (0x8) IX[B]
	[18] -1	0	0x000015f4 - 0x000015f7 (0x4) IX[B]
	[19] -1	0	0x000013f0 - 0x000013f7 (0x8) IX[B]
	[20] -1	0	0x00005100 - 0x0000510f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000050e0 - 0x000050ff (0x20) IX[B]
	[26] -1	0	0x000050c0 - 0x000050df (0x20) IX[B]
	[27] -1	0	0x000050a0 - 0x000050bf (0x20) IX[B]
	[28] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[29] -1	0	0x00005060 - 0x0000507f (0x20) IX[B]
	[30] -1	0	0x00005040 - 0x0000505f (0x20) IX[B]
	[31] -1	0	0x00005030 - 0x00005037 (0x8) IX[B]
	[32] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[33] -1	0	0x00005018 - 0x0000501b (0x4) IX[B]
	[34] -1	0	0x00005010 - 0x00005017 (0x8) IX[B]
	[35] -1	0	0x00005008 - 0x0000500b (0x4) IX[B]
	[36] -1	0	0x00005000 - 0x00005007 (0x8) IX[B]
	[37] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe4000000 - 0xe4001fff (0x2000) MX[B]
	[1] -1	0	0xe4104000 - 0xe41040ff (0x100) MX[B]
	[2] -1	0	0xe4103000 - 0xe41030ff (0x100) MX[B]
	[3] -1	0	0xe4102000 - 0xe41027ff (0x800) MX[B]
	[4] -1	0	0xe4410000 - 0xe4413fff (0x4000) MX[B]
	[5] -1	0	0xe4549000 - 0xe45497ff (0x800) MX[B]
	[6] -1	0	0xe4548000 - 0xe45483ff (0x400) MX[B]
	[7] -1	0	0xe4544000 - 0xe4547fff (0x4000) MX[B]
	[8] -1	0	0xe4541000 - 0xe45413ff (0x400) MX[B]
	[9] -1	0	0xe4540000 - 0xe4540fff (0x1000) MX[B]
	[10] -1	0	0xe4520000 - 0xe453ffff (0x20000) MX[B]
	[11] -1	0	0xe4501000 - 0xe4501fff (0x1000) MX[B]
	[12] -1	0	0xe4500000 - 0xe450000f (0x10) MX[B]
	[13] -1	0	0xe4400000 - 0xe440ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x00005140 - 0x0000515f (0x20) IX[B]
	[16] -1	0	0x00001574 - 0x00001577 (0x4) IX[B]
	[17] -1	0	0x00001370 - 0x00001377 (0x8) IX[B]
	[18] -1	0	0x000015f4 - 0x000015f7 (0x4) IX[B]
	[19] -1	0	0x000013f0 - 0x000013f7 (0x8) IX[B]
	[20] -1	0	0x00005100 - 0x0000510f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000050e0 - 0x000050ff (0x20) IX[B]
	[26] -1	0	0x000050c0 - 0x000050df (0x20) IX[B]
	[27] -1	0	0x000050a0 - 0x000050bf (0x20) IX[B]
	[28] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[29] -1	0	0x00005060 - 0x0000507f (0x20) IX[B]
	[30] -1	0	0x00005040 - 0x0000505f (0x20) IX[B]
	[31] -1	0	0x00005030 - 0x00005037 (0x8) IX[B]
	[32] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[33] -1	0	0x00005018 - 0x0000501b (0x4) IX[B]
	[34] -1	0	0x00005010 - 0x00005017 (0x8) IX[B]
	[35] -1	0	0x00005008 - 0x0000500b (0x4) IX[B]
	[36] -1	0	0x00005000 - 0x00005007 (0x8) IX[B]
	[37] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
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
	[4] -1	0	0xe4000000 - 0xe4001fff (0x2000) MX[B]
	[5] -1	0	0xe4104000 - 0xe41040ff (0x100) MX[B]
	[6] -1	0	0xe4103000 - 0xe41030ff (0x100) MX[B]
	[7] -1	0	0xe4102000 - 0xe41027ff (0x800) MX[B]
	[8] -1	0	0xe4410000 - 0xe4413fff (0x4000) MX[B]
	[9] -1	0	0xe4549000 - 0xe45497ff (0x800) MX[B]
	[10] -1	0	0xe4548000 - 0xe45483ff (0x400) MX[B]
	[11] -1	0	0xe4544000 - 0xe4547fff (0x4000) MX[B]
	[12] -1	0	0xe4541000 - 0xe45413ff (0x400) MX[B]
	[13] -1	0	0xe4540000 - 0xe4540fff (0x1000) MX[B]
	[14] -1	0	0xe4520000 - 0xe453ffff (0x20000) MX[B]
	[15] -1	0	0xe4501000 - 0xe4501fff (0x1000) MX[B]
	[16] -1	0	0xe4500000 - 0xe450000f (0x10) MX[B]
	[17] -1	0	0xe4400000 - 0xe440ffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00005140 - 0x0000515f (0x20) IX[B]
	[22] -1	0	0x00001574 - 0x00001577 (0x4) IX[B]
	[23] -1	0	0x00001370 - 0x00001377 (0x8) IX[B]
	[24] -1	0	0x000015f4 - 0x000015f7 (0x4) IX[B]
	[25] -1	0	0x000013f0 - 0x000013f7 (0x8) IX[B]
	[26] -1	0	0x00005100 - 0x0000510f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000050e0 - 0x000050ff (0x20) IX[B]
	[32] -1	0	0x000050c0 - 0x000050df (0x20) IX[B]
	[33] -1	0	0x000050a0 - 0x000050bf (0x20) IX[B]
	[34] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[35] -1	0	0x00005060 - 0x0000507f (0x20) IX[B]
	[36] -1	0	0x00005040 - 0x0000505f (0x20) IX[B]
	[37] -1	0	0x00005030 - 0x00005037 (0x8) IX[B]
	[38] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[39] -1	0	0x00005018 - 0x0000501b (0x4) IX[B]
	[40] -1	0	0x00005010 - 0x00005017 (0x8) IX[B]
	[41] -1	0	0x00005008 - 0x0000500b (0x4) IX[B]
	[42] -1	0	0x00005000 - 0x00005007 (0x8) IX[B]
	[43] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
	compiled for 7.1.0, module version = 8.47.3
	Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.471                    
(II) ATI Proprietary Linux Driver Build Date: Feb 25 2008 21:22:09
(--) Chipset Supported AMD Graphics Processor (0x9581) found
(--) Chipset Supported AMD Graphics Processor (0x9581) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4000000 - 0xe4001fff (0x2000) MX[B]
	[5] -1	0	0xe4104000 - 0xe41040ff (0x100) MX[B]
	[6] -1	0	0xe4103000 - 0xe41030ff (0x100) MX[B]
	[7] -1	0	0xe4102000 - 0xe41027ff (0x800) MX[B]
	[8] -1	0	0xe4410000 - 0xe4413fff (0x4000) MX[B]
	[9] -1	0	0xe4549000 - 0xe45497ff (0x800) MX[B]
	[10] -1	0	0xe4548000 - 0xe45483ff (0x400) MX[B]
	[11] -1	0	0xe4544000 - 0xe4547fff (0x4000) MX[B]
	[12] -1	0	0xe4541000 - 0xe45413ff (0x400) MX[B]
	[13] -1	0	0xe4540000 - 0xe4540fff (0x1000) MX[B]
	[14] -1	0	0xe4520000 - 0xe453ffff (0x20000) MX[B]
	[15] -1	0	0xe4501000 - 0xe4501fff (0x1000) MX[B]
	[16] -1	0	0xe4500000 - 0xe450000f (0x10) MX[B]
	[17] -1	0	0xe4400000 - 0xe440ffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00005140 - 0x0000515f (0x20) IX[B]
	[22] -1	0	0x00001574 - 0x00001577 (0x4) IX[B]
	[23] -1	0	0x00001370 - 0x00001377 (0x8) IX[B]
	[24] -1	0	0x000015f4 - 0x000015f7 (0x4) IX[B]
	[25] -1	0	0x000013f0 - 0x000013f7 (0x8) IX[B]
	[26] -1	0	0x00005100 - 0x0000510f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000050e0 - 0x000050ff (0x20) IX[B]
	[32] -1	0	0x000050c0 - 0x000050df (0x20) IX[B]
	[33] -1	0	0x000050a0 - 0x000050bf (0x20) IX[B]
	[34] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[35] -1	0	0x00005060 - 0x0000507f (0x20) IX[B]
	[36] -1	0	0x00005040 - 0x0000505f (0x20) IX[B]
	[37] -1	0	0x00005030 - 0x00005037 (0x8) IX[B]
	[38] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[39] -1	0	0x00005018 - 0x0000501b (0x4) IX[B]
	[40] -1	0	0x00005010 - 0x00005017 (0x8) IX[B]
	[41] -1	0	0x00005008 - 0x0000500b (0x4) IX[B]
	[42] -1	0	0x00005000 - 0x00005007 (0x8) IX[B]
	[43] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820c648
(II) fglrx(1): pEnt->device->identifier=0x820c648
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4000000 - 0xe4001fff (0x2000) MX[B]
	[5] -1	0	0xe4104000 - 0xe41040ff (0x100) MX[B]
	[6] -1	0	0xe4103000 - 0xe41030ff (0x100) MX[B]
	[7] -1	0	0xe4102000 - 0xe41027ff (0x800) MX[B]
	[8] -1	0	0xe4410000 - 0xe4413fff (0x4000) MX[B]
	[9] -1	0	0xe4549000 - 0xe45497ff (0x800) MX[B]
	[10] -1	0	0xe4548000 - 0xe45483ff (0x400) MX[B]
	[11] -1	0	0xe4544000 - 0xe4547fff (0x4000) MX[B]
	[12] -1	0	0xe4541000 - 0xe45413ff (0x400) MX[B]
	[13] -1	0	0xe4540000 - 0xe4540fff (0x1000) MX[B]
	[14] -1	0	0xe4520000 - 0xe453ffff (0x20000) MX[B]
	[15] -1	0	0xe4501000 - 0xe4501fff (0x1000) MX[B]
	[16] -1	0	0xe4500000 - 0xe450000f (0x10) MX[B]
	[17] -1	0	0xe4400000 - 0xe440ffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00005140 - 0x0000515f (0x20) IX[B]
	[25] -1	0	0x00001574 - 0x00001577 (0x4) IX[B]
	[26] -1	0	0x00001370 - 0x00001377 (0x8) IX[B]
	[27] -1	0	0x000015f4 - 0x000015f7 (0x4) IX[B]
	[28] -1	0	0x000013f0 - 0x000013f7 (0x8) IX[B]
	[29] -1	0	0x00005100 - 0x0000510f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000050e0 - 0x000050ff (0x20) IX[B]
	[35] -1	0	0x000050c0 - 0x000050df (0x20) IX[B]
	[36] -1	0	0x000050a0 - 0x000050bf (0x20) IX[B]
	[37] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[38] -1	0	0x00005060 - 0x0000507f (0x20) IX[B]
	[39] -1	0	0x00005040 - 0x0000505f (0x20) IX[B]
	[40] -1	0	0x00005030 - 0x00005037 (0x8) IX[B]
	[41] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[42] -1	0	0x00005018 - 0x0000501b (0x4) IX[B]
	[43] -1	0	0x00005010 - 0x00005017 (0x8) IX[B]
	[44] -1	0	0x00005008 - 0x0000500b (0x4) IX[B]
	[45] -1	0	0x00005000 - 0x00005007 (0x8) IX[B]
	[46] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
	[47] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 2600" (Chipset = 0x9581)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x30c5)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe4400000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
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
(II) fglrx(0): VESA VBE OEM Software Rev: 10.56
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M76
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
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: QDS  Model: 3f  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 20
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.566 redY: 0.330   greenX: 0.308 greenY: 0.553
(II) fglrx(0): blueX: 0.158 blueY: 0.143   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.0 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) fglrx(0):  QUANTADISPLAY
(II) fglrx(0):  QD15AL013
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0044933f0000000000
(II) fglrx(0): 	000f0103802114780a2ea091544e8d28
(II) fglrx(0): 	24505400000001010101010101010101
(II) fglrx(0): 	0101010101017c2e90a0601a1e403020
(II) fglrx(0): 	36004bcf100000180000000f0006320c
(II) fglrx(0): 	78011402141e8c021900000000fe0051
(II) fglrx(0): 	55414e5441444953504c4159000000fe
(II) fglrx(0): 	0051443135414c3031330a2020200081
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 18 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1440x900": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  119.00  1440 1728 1760 1840  900 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1400x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  119.00  1400 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1280x1024": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  119.00  1280 1728 1760 1840  1024 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1280x960": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  119.00  1280 1728 1760 1840  960 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1280x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0  119.00  1280 1728 1760 1840  768 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1280x720": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0  119.00  1280 1728 1760 1840  720 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1152x864": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0  119.00  1152 1728 1760 1840  864 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1024x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0  119.00  1024 1728 1760 1840  768 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "800x600": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0  119.00  800 1728 1760 1840  600 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "720x480": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0  119.00  720 1728 1760 1840  480 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "640x480": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0  119.00  640 1728 1760 1840  480 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "640x432": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0  119.00  640 1728 1760 1840  432 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "640x400": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0  119.00  640 1728 1760 1840  400 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "512x384": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0  119.00  512 1728 1760 1840  384 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "400x300": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0  119.00  400 1728 1760 1840  300 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "320x240": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0  119.00  320 1728 1760 1840  240 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "320x200": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0  119.00  320 1728 1760 1840  200 1053 1059 1080 +hsync +vsync (64.7 kHz)
(--) fglrx(0): Display dimensions: (330, 200) mm
(--) fglrx(0): DPI set to (129, 133)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1440x900": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  119.00  1440 1728 1760 1840  900 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1400x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  119.00  1400 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1280x1024": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  119.00  1280 1728 1760 1840  1024 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1280x960": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  119.00  1280 1728 1760 1840  960 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1280x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0  119.00  1280 1728 1760 1840  768 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1280x720": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0  119.00  1280 1728 1760 1840  720 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1152x864": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0  119.00  1152 1728 1760 1840  864 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1024x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0  119.00  1024 1728 1760 1840  768 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "800x600": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0  119.00  800 1728 1760 1840  600 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "720x480": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0  119.00  720 1728 1760 1840  480 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "640x480": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0  119.00  640 1728 1760 1840  480 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "640x432": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0  119.00  640 1728 1760 1840  432 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "640x400": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0  119.00  640 1728 1760 1840  400 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "512x384": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0  119.00  512 1728 1760 1840  384 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "400x300": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0  119.00  400 1728 1760 1840  300 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "320x240": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0  119.00  320 1728 1760 1840  240 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "320x200": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0  119.00  320 1728 1760 1840  200 1053 1059 1080 +hsync +vsync (64.7 kHz)
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
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(1): === [atiddxPreInit] === begin
(EE) fglrx(1): Quitting secondary screen -- no monitor specified.
(EE) fglrx(1): PreInit failed
(II) fglrx(1): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe4400000 - 0xe440ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe4000000 - 0xe4001fff (0x2000) MX[B]
	[7] -1	0	0xe4104000 - 0xe41040ff (0x100) MX[B]
	[8] -1	0	0xe4103000 - 0xe41030ff (0x100) MX[B]
	[9] -1	0	0xe4102000 - 0xe41027ff (0x800) MX[B]
	[10] -1	0	0xe4410000 - 0xe4413fff (0x4000) MX[B]
	[11] -1	0	0xe4549000 - 0xe45497ff (0x800) MX[B]
	[12] -1	0	0xe4548000 - 0xe45483ff (0x400) MX[B]
	[13] -1	0	0xe4544000 - 0xe4547fff (0x4000) MX[B]
	[14] -1	0	0xe4541000 - 0xe45413ff (0x400) MX[B]
	[15] -1	0	0xe4540000 - 0xe4540fff (0x1000) MX[B]
	[16] -1	0	0xe4520000 - 0xe453ffff (0x20000) MX[B]
	[17] -1	0	0xe4501000 - 0xe4501fff (0x1000) MX[B]
	[18] -1	0	0xe4500000 - 0xe450000f (0x10) MX[B]
	[19] -1	0	0xe4400000 - 0xe440ffff (0x10000) MX[B](B)
	[20] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[21] 0	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00005140 - 0x0000515f (0x20) IX[B]
	[25] -1	0	0x00001574 - 0x00001577 (0x4) IX[B]
	[26] -1	0	0x00001370 - 0x00001377 (0x8) IX[B]
	[27] -1	0	0x000015f4 - 0x000015f7 (0x4) IX[B]
	[28] -1	0	0x000013f0 - 0x000013f7 (0x8) IX[B]
	[29] -1	0	0x00005100 - 0x0000510f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000050e0 - 0x000050ff (0x20) IX[B]
	[35] -1	0	0x000050c0 - 0x000050df (0x20) IX[B]
	[36] -1	0	0x000050a0 - 0x000050bf (0x20) IX[B]
	[37] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[38] -1	0	0x00005060 - 0x0000507f (0x20) IX[B]
	[39] -1	0	0x00005040 - 0x0000505f (0x20) IX[B]
	[40] -1	0	0x00005030 - 0x00005037 (0x8) IX[B]
	[41] -1	0	0x00005020 - 0x0000502f (0x10) IX[B]
	[42] -1	0	0x00005018 - 0x0000501b (0x4) IX[B]
	[43] -1	0	0x00005010 - 0x00005017 (0x8) IX[B]
	[44] -1	0	0x00005008 - 0x0000500b (0x4) IX[B]
	[45] -1	0	0x00005000 - 0x00005007 (0x8) IX[B]
	[46] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
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
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [drm] installed DRM signal handler
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.47.3
(II) fglrx(0):     Date: Feb 25 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01008000
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,2432)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 1382
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 10
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
Receive enable interrupt ret message
...irqEnableMask: 60000001
...dwIRQEnableId: 00000006
Receive enable interrupt ret message
...irqEnableMask: 00000040
...dwIRQEnableId: 00000007
Receive enable interrupt ret message
...irqEnableMask: ff00002c
...dwIRQEnableId: 00000008
Receive enable interrupt ret message
...irqEnableMask: ff00002d
...dwIRQEnableId: 00000009
Receive enable interrupt ret message
...irqEnableMask: 20000400
...dwIRQEnableId: 0000000a
(II) fglrx(0): Finished Initialize PPLIB!
(II) fglrx(0): Enable the clock gating
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
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
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
(**) Option "XkbLayout" "no"
(**) Generic Keyboard: XkbLayout: "no"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
(II) XAA: Evicting pixmaps
```

yay.

Thanks for the reply :) Hope you can see something out of this jibberish log of mine :)

Leazand

---

