---
title: "K9VGM-V Problem with graphics card"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by mauman on 2008-03-04
Hi, this is my first post in the Ubuntu Forum, nice to meet all of you!

I'm running Ubuntu 7.10 on both my laptop and work pc, with no problems.
At home I installed a new machine based on the motherboard MSI K9VGM-V which work with no problems under Windows.
With Ubuntu I have problems with the graphics driver. I installed the OpenChrome driver but it seems that the video card is still recognized as Generic VESA. I'm not looking for accelerations, I would like to set up a 1024 * 768 screen at 85 Hz, but it is still impossible on my machine.

I can provide you any conf/log file you need to understand where the problem is, just tell me what you need.

Thank you very much for your help!

Maurizio

---

### Post by mauman on 2008-03-04
Let me add that if I open the "screens and resolutions" panel I still cannot see the VIA driver, the one that should be installed by OpenChrome. I can manually set it in the xorg.conf file but it seems that nothing changes...

Maurizio

---

### Post by mauman on 2008-03-04
the card is correctly detected:


sudo lspci -vv -s 1:0
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890 [Chrome9] Integrated Video (rev 11) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7253
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 1: Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at de000000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [70] AGP version 3.0
                Status: RQ=256 Iso- ArqSz=0 Cal=7 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW- Rate=<none>

---

### Post by mauman on 2008-03-05
Ok, it seems that I'm the only one having this problem... However, the problem is still there, let me describe it with further details.

The video card is always recognized as generic VESA, no matter which driver I install (VIA, UniChrome, ...). The connected monitor is a LG 775FT which is also not detected. For now I can work at 800*600 60 Hz, nothing more. I could stay with VESA but I would like to at least switch to a better resolution.

Any ideas?

Thanks,
Maurizio

---

### Post by mauman on 2008-03-05
this is the full result of lspci:

00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890 [Chrome9] Integrated Video (rev 11)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

---

### Post by mauman on 2008-03-05
and this is Xorg.0.log when the driver fails to load. as you can see, at the very end of the file, it seems that the vga is not there!


> X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux casa 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar  5 14:10:31 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "monitor1"
(**) |   |-->Device "s3vga"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cdb20
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
(II) PCI: 00:00:0: chip 1106,0336 card 1106,0336 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:5: chip 1106,5336 card 0000,0000 rev 00 class 08,00,20 hdr 80
(II) PCI: 00:00:7: chip 1106,7336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1106,a238 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 1106,c238 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,0591 card 1462,7253 rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1462,7253 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1462,7253 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1462,7253 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1462,7253 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1462,7253 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1462,7253 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3337 card 1106,3337 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:7: chip 1106,287e card 1106,337e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1462,7253 rev 7c class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,337b card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:13:1: chip 1106,337a card 0000,0000 rev 00 class 06,04,01 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1106,3230 card 1462,7253 rev 11 class 03,00,00 hdr 00
(II) PCI: 80:01:0: chip 1106,3288 card 1462,7253 rev 10 class 04,03,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,128), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0018 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdeffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xdfb00000 - 0xdfbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:19:1), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xdfa00000 - 0xdfafffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xdf900000 - 0xdf9fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 128: bridge is at (0:0:0), (128,128,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 128 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 128 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 128 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3230) rev 17, Mem @ 0xc0000000/28, 0xdd000000/24
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd0000000 to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xbfffc000 - 0xbfffffff (0x4000) MX[B]
	[1] -1	0	0xdfffe000 - 0xdfffe0ff (0x100) MX[B]
	[2] -1	0	0xdffff000 - 0xdffff0ff (0x100) MX[B]
	[3] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[4] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0x0000f200 - 0x0000f2ff (0x100) IX[B]
	[7] -1	0	0x0000f600 - 0x0000f61f (0x20) IX[B]
	[8] -1	0	0x0000f700 - 0x0000f71f (0x20) IX[B]
	[9] -1	0	0x0000f800 - 0x0000f81f (0x20) IX[B]
	[10] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[11] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[12] -1	0	0x0000f400 - 0x0000f4ff (0x100) IX[B]
	[13] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[15] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xbfffc000 - 0xbfffffff (0x4000) MX[B]
	[1] -1	0	0xdfffe000 - 0xdfffe0ff (0x100) MX[B]
	[2] -1	0	0xdffff000 - 0xdffff0ff (0x100) MX[B]
	[3] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[4] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0x0000f200 - 0x0000f2ff (0x100) IX[B]
	[7] -1	0	0x0000f600 - 0x0000f61f (0x20) IX[B]
	[8] -1	0	0x0000f700 - 0x0000f71f (0x20) IX[B]
	[9] -1	0	0x0000f800 - 0x0000f81f (0x20) IX[B]
	[10] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[11] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[12] -1	0	0x0000f400 - 0x0000f4ff (0x100) IX[B]
	[13] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[15] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[17] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
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
	[4] -1	0	0xbfffc000 - 0xbfffffff (0x4000) MX[B]
	[5] -1	0	0xdfffe000 - 0xdfffe0ff (0x100) MX[B]
	[6] -1	0	0xdffff000 - 0xdffff0ff (0x100) MX[B]
	[7] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[8] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000f200 - 0x0000f2ff (0x100) IX[B]
	[13] -1	0	0x0000f600 - 0x0000f61f (0x20) IX[B]
	[14] -1	0	0x0000f700 - 0x0000f71f (0x20) IX[B]
	[15] -1	0	0x0000f800 - 0x0000f81f (0x20) IX[B]
	[16] -1	0	0x0000f900 - 0x0000f91f (0x20) IX[B]
	[17] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[18] -1	0	0x0000f400 - 0x0000f4ff (0x100) IX[B]
	[19] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[21] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
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
(II) v4l driver for Video4Linux
[B](II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400, VM800/CN700/P4M800Pro
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.[/B]

Fatal server error:
no screens found

---

### Post by mauman on 2008-03-05
I'm wondering if the location PCI:1.0.0 may be wrong... the graphic card is integrated so maybe I should use another reference. what do you think about this?

---

### Post by mauman on 2008-03-06
The problem is still there... I tried with the three drivers: Ubuntu Via driver, UniChrome and OpenChrome.
The system always answer that no device is found. It looks very strange, as the VGA adapter is listed as one of the PCI devices.
Can anybody help me to find a solution to this problem?

Maurizio

---

### Post by mauman on 2008-03-06
I fixed the problem. If you have such a card, [B]YOU DON'T HAVE TO INSTALL OPENCHROME THROUGH UBUNTU!
[/B]
Instead, download, compile and install the driver following the instructions you can find at the site [http://www.openchrome.org/](http://www.openchrome.org/)

Regards,
Maurizio

---

### Post by madjr on 2008-05-18
Thanks, this has been very helpful i just purchased one.

you might also want to try
[http://linux.via.com.tw](http://linux.via.com.tw)

they'll add open drivers from time to time.

---

### Post by ubot on 2008-06-26
I'm working on a linux robot and would this be an easy board to setup if the video quality doesn't matter?  I've been looking for a Athlon 64 + Mobo combo less than $100 to replace y Pentium III 750MHz w/ 768MB RAM. (this mobo=$50, athlon 64 2.4GHz=$45)
                                             Nathaniel

---

