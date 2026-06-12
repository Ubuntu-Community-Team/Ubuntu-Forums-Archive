---
title: "Unable to swtich video output on Thinkpad T60p"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by GumbyX on 2008-02-19
Heyo. I have been working on this all day and I haven't come up with anything. Hopefully someone can help me out with this.

Currently, I am running Gutsy on my T60p with the fglrx proprietary drivers and XGL. The problem I am having is that I cannot get the laptop to output to the VGA port. I had a T43p that had 6.10 on it and I didn't have a problem with this. ATM, I cannot get flgrx to even recognize that there is another monitor connected to it. The weirdest part of the problem is if I boot the system up with an external monitor connected, I get output on both the external monitor and laptop LCD. It is fine on the laptop LCD and at a low resolution (the screen scrolls to keep up with my mouse pointer on the screen) on the external monitor,  but fglrx STILL doesn't reconize that there is another monitor connected to the laptop. Anyone think they can help me out? I have tried everything I can think of, including info I found at ThinkWiki ([http://www.thinkwiki.org/wiki/Problem_with_video_output_switching](http://www.thinkwiki.org/wiki/Problem_with_video_output_switching)) and nothing seems to work. The only thing I haven't tried yet is compiling my own fglrx driver from source.

ATM, I am tempted to just try and use the open source Radeon/ATI drivers and see if they work. I will probably try compiling the fglrx driver from source and if that doesn't work, try the Open-Source drivers.

Thanks ahead of time to anyone who can help me out.

---

### Post by GumbyX on 2008-02-21
: sigh: Can anyone please help me out? I have to use my laptop for presentations in my courses.

Update: ATI drivers will not work for some reason, and when i manually installed fglrx 8.443.1, I ran into resolution problems (for some reason, I couldn't get the max resolution to work, which it does with the fglrx drivers in the repositories). I am lost on what i should do.'

---

### Post by Yellow Pasque on 2008-02-21
Please post your xorg.conf and /var/log/Xorg.0.log
What kind of video chip do you have?

EDIT: I guess you've seen this:? [http://thinkwiki.org/wiki/Fglrx#Display_Switching_.28Dynamic_Display_Management.29](http://thinkwiki.org/wiki/Fglrx#Display_Switching_.28Dynamic_Display_Management.29)

---

### Post by GumbyX on 2008-02-21
> **Temüjin said:**
> Please post your xorg.conf and /var/log/Xorg.0.log
What kind of video chip do you have?

EDIT: I guess you've seen this:? [http://thinkwiki.org/wiki/Fglrx#Display_Switching_.28Dynamic_Display_Management.29](http://thinkwiki.org/wiki/Fglrx#Display_Switching_.28Dynamic_Display_Management.29)

Thank you for helping me out.

I am running a ATI Mobility FireGL V5250 for a graphics chip. Will post xorg.conf and Xorg.0.log in a few (currently stuck using Windows side of laptop for some C# programming).

As for the Dynamic Display Management: When I use the query-monitor command, it says no external monitors are connected. Currently using fglrx in repository (believe its 8.37). Will post exact output when I post xorg.conf.

Not sure if this would cause a problem, but I am running xgl because I can't get the Open-source driver with (or without) AIGLX to with this graphics card.

---

### Post by Yellow Pasque on 2008-02-21
I just checked with the head xf86-radeon developer (David Airlie) and he confirmed that Compiz is not yet supported on R500 hardware (your chip is based on mobility radeon x1700/R520), so we'll have to try with fglrx/xgl.

---

### Post by GumbyX on 2008-02-21
> **Temüjin said:**
> I just checked with the head xf86-radeon developer (David Airlie) and he confirmed that Compiz is not yet supported on R500 hardware (your chip is based on mobility radeon x1700/R520), so we'll have to try with fglrx/xgl.

Thanks for the heads up. Here are my files:

**/var/log/Xorg.0.log**
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux gumby-linux-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 21 16:40:51 2008
(==) Using config file: "/etc/X11/xorg.conf"
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
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 8086,27a0 card 17aa,2015 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 17aa,2010 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 17aa,200a rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 17aa,200a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 17aa,200a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 17aa,200a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 17aa,200b rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 17aa,2009 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 17aa,200e rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 17aa,200f rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,71d4 card 17aa,20a4 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 8086,109a card 17aa,2001 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 168c,1014 card 1014,058a rev 01 class 02,00,00 hdr 00
(II) PCI: 15:00:0: chip 104c,ac56 card a000,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,22), BCTRL: 0x0008 (VGA_EN is set)
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
	[0] -1	0	0xee100000 - 0xee1fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xee000000 - 0xee0fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
	[4] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[5] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[6] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[7] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe40fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,11), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[1] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[2] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[3] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
	[4] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[5] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[6] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[7] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe9ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xe4100000 - 0xe41fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:3), (0,12,19), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 12 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[4] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[5] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[6] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[7] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xea000000 - 0xebffffff (0x2000000) MX[B]
(II) Bus 12 prefetchable memory range:
	[0] -1	0	0xe4200000 - 0xe42fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 21: bridge is at (0:30:0), (0,21,24), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 21 I/O range:
	[0] -1	0	0x0000a000 - 0x0000dfff (0x4000) IX[B]
(II) Bus 21 non-prefetchable memory range:
	[0] -1	0	0xe4300000 - 0xe7ffffff (0x3d00000) MX[B]
(II) Bus 21 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 22: bridge is at (21:0:0), (21,22,23), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 22 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
(II) Bus 22 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x71d4) rev 0, Mem @ 0xd0000000/28, 0xee100000/16, I/O @ 0x2000/8
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
	[0] -1	0	0xedf00000 - 0xedf0ffff (0x10000) MX[B]
	[1] -1	0	0xee000000 - 0xee01ffff (0x20000) MX[B]
	[2] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[3] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[4] -1	0	0xee100000 - 0xee10ffff (0x10000) MX[B](B)
	[5] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[6] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[7] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[8] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[9] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[10] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[13] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[14] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[15] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[16] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xedf00000 - 0xedf0ffff (0x10000) MX[B]
	[1] -1	0	0xee000000 - 0xee01ffff (0x20000) MX[B]
	[2] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[3] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[4] -1	0	0xee100000 - 0xee10ffff (0x10000) MX[B](B)
	[5] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[6] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[7] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[8] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[9] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[10] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[13] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[14] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[15] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[16] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
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
	[4] -1	0	0xedf00000 - 0xedf0ffff (0x10000) MX[B]
	[5] -1	0	0xee000000 - 0xee01ffff (0x20000) MX[B]
	[6] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[7] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[8] -1	0	0xee100000 - 0xee10ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[13] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[20] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[21] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[22] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[23] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(--) Chipset Supported AMD Graphics Processor (0x71D4) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xedf00000 - 0xedf0ffff (0x10000) MX[B]
	[5] -1	0	0xee000000 - 0xee01ffff (0x20000) MX[B]
	[6] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[7] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[8] -1	0	0xee100000 - 0xee10ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[13] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[20] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[21] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[22] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[23] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8206750
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xedf00000 - 0xedf0ffff (0x10000) MX[B]
	[5] -1	0	0xee000000 - 0xee01ffff (0x20000) MX[B]
	[6] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[7] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[8] -1	0	0xee100000 - 0xee10ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[16] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[17] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
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
(--) fglrx(0): Chipset: "ATI MOBILITY FireGL V5250" (Chipset = 0x71d4)
(--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x20a4)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xee100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
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
(II) fglrx(0): VESA VBE OEM Product: M66GL
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(WW) fglrx(0): GetVBEMode failed
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
	compiled for 7.1.0, module version = 8.37.6
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: IBM  Model: 2887  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.596 redY: 0.347   greenX: 0.335 greenY: 0.543
(II) fglrx(0): blueX: 0.158 blueY: 0.143   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 120.6 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1680  h_sync: 1712  h_sync_end 1760 h_blank_end 1888 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1065 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 100.5 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1680  h_sync: 1712  h_sync_end 1760 h_blank_end 1888 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1065 v_border: 0
(II) fglrx(0):  LP154W02-TL06
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00244d872800000000
(II) fglrx(0): 	000f0103802115780abca59858558b28
(II) fglrx(0): 	24505400000001010101010101010101
(II) fglrx(0): 	0101010101011c2f90d0601a0f402030
(II) fglrx(0): 	13004bcf10000019452790d0601a0f40
(II) fglrx(0): 	203013004bcf100000190000000f00b3
(II) fglrx(0): 	0a32b30a28140100320c0000000000fe
(II) fglrx(0): 	004c503135345730322d544c303600bf
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 432/324MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 128/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 324/135MHz @ 60Hz [enable sleep]
(II) fglrx(0):   5. 378/324MHz @ 60Hz [enable sleep, thermal diode mode]
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
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050@60": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050@60"  120.60  1680 1712 1760 1888  1050 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "800x600@60": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600@60"  120.60  800 1712 1760 1888  600 1051 1054 1065 +hsync +vsync
(**) fglrx(0): *Mode "800x600@56": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600@56"  120.60  800 1712 1760 1888  600 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "1280x1024": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  120.60  1280 1712 1760 1888  1024 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "1152x864": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  120.60  1152 1712 1760 1888  864 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  120.60  1024 1712 1760 1888  768 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "960x600": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x600"  120.60  960 1712 1760 1888  600 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "768x480": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "768x480"  120.60  768 1712 1760 1888  480 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  120.60  640 1712 1760 1888  480 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  120.60  640 1712 1760 1888  400 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  120.60  512 1712 1760 1888  384 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  120.60  400 1712 1760 1888  300 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  120.60  320 1712 1760 1888  240 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  120.60  320 1712 1760 1888  200 1051 1054 1065 +hsync +vsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (129, 126)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050@60": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050@60"  120.60  1680 1712 1760 1888  1050 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "800x600@60": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600@60"  120.60  800 1712 1760 1888  600 1051 1054 1065 +hsync +vsync
(**) fglrx(0): *Mode "800x600@56": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600@56"  120.60  800 1712 1760 1888  600 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "1280x1024": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  120.60  1280 1712 1760 1888  1024 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "1152x864": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  120.60  1152 1712 1760 1888  864 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  120.60  1024 1712 1760 1888  768 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "960x600": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "960x600"  120.60  960 1712 1760 1888  600 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "768x480": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "768x480"  120.60  768 1712 1760 1888  480 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  120.60  640 1712 1760 1888  480 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  120.60  640 1712 1760 1888  400 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  120.60  512 1712 1760 1888  384 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  120.60  400 1712 1760 1888  300 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  120.60  320 1712 1760 1888  240 1051 1054 1065 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 120.6 MHz (scaled from 0.0 MHz), 63.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  120.60  320 1712 1760 1888  200 1051 1054 1065 +hsync +vsync
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
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
	[0] 0	0	0xee100000 - 0xee10ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xedf00000 - 0xedf0ffff (0x10000) MX[B]
	[7] -1	0	0xee000000 - 0xee01ffff (0x20000) MX[B]
	[8] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[9] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[10] -1	0	0xee100000 - 0xee10ffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[15] 0	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[19] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[26] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[27] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[29] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
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
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7f7c000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): FIREGL Board Found
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
```

**Xorg.conf**
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"GLcore"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0	-	65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by GumbyX on 2008-02-23
So...... anyone think they can help me out? This has probably been buried under a bunch of stuff, so I am bumping it once more. Sorry but I really need help with this.

---

