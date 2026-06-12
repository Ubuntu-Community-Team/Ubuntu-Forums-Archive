---
title: "Nvidia Geforce 5200 FX Overheats!!"
date: 2008-05-25
forum: Hardware
---

### Post by jesushero on 2008-05-25
I have a desktop computer with an Asus Albatron mb, a genuine Intel P4 2.6 GHz, 512mb RAM, a Sound Blaster Live 1024 sound card and an NVidia GeForce 5200 FX graphics card. 

I've been running Ubuntu for several months now, having only one unsolved problem! The graphics card constantly overheats, causing the whole system to crash! This only happens when GDM is running (I've removed it from the startup services). If I'm only working on the tty's, there's no problems whatsoever. It has had an uptime of 30 days with no problems with GDM disabled. (I have tried both the NV drivers and the NVidia ones, with the NVidia simply providing more options but same amount of crashing)

A friend of mine has almost the same machine setup, with the same graphics card, which has the same problem. It overheats. His has a fan built in, mine doesn't. Do you think I could solve the problem by adding a fan? 

Is it safe to replace the graphics card with something totally different, without reinstalling ubuntu and with loads of data in it? Should I keep the existing one and try to add a fan? 

Another idea that I'm having is using this machine as a server, so I'd run it with GDM disabled. (I am running the RT kernel as I'm using it as a server for Audio/Visual applications) Is it safe/stable to leave this card in there and not using GDM? Is it possible to run the machine with NO graphics card in it (since I'll only SSH into it)??

Any ideas/suggestions/comments would be greatly appreciated!

---

### Post by &amp;wP*!) on 2008-05-25
> **jesushero said:**
> I have a desktop computer with an Asus Albatron mb, a genuine Intel P4 2.6 GHz, 512mb RAM, a Sound Blaster Live 1024 sound card and an NVidia GeForce 5200 FX graphics card. 

I've been running Ubuntu for several months now, having only one unsolved problem! The graphics card constantly overheats, causing the whole system to crash! This only happens when GDM is running (I've removed it from the startup services). If I'm only working on the tty's, there's no problems whatsoever. It has had an uptime of 30 days with no problems with GDM disabled. (I have tried both the NV drivers and the NVidia ones, with the NVidia simply providing more options but same amount of crashing)

A friend of mine has almost the same machine setup, with the same graphics card, which has the same problem. It overheats. His has a fan built in, mine doesn't. Do you think I could solve the problem by adding a fan? 

Is it safe to replace the graphics card with something totally different, without reinstalling ubuntu and with loads of data in it? Should I keep the existing one and try to add a fan? 

Another idea that I'm having is using this machine as a server, so I'd run it with GDM disabled. (I am running the RT kernel as I'm using it as a server for Audio/Visual applications) Is it safe/stable to leave this card in there and not using GDM? Is it possible to run the machine with NO graphics card in it (since I'll only SSH into it)??

Any ideas/suggestions/comments would be greatly appreciated!

Hi, I have an MSI KT6 Ultra MS-6590 on which GeForce 5200 FX is plugged. I am using this hardware for 3 years, without any system crash. I have installed Windows XP, Ubuntu, Fedora, OpenSuse, Mandriva. I have used third-party drivers (Restricted one at Ubuntu, Livna at Fedora), did not see anything.

Restart your Ubuntu and let him crash again. Can you send us then:
/var/log/messages
/var/log/syslog
/var/log/Xorg.0.log
and output of **lspci -vvv**.

Attach these 3 files here. And tell us what kind of crash do you see? What do you mean with "crash"? Kernel panic?

---

### Post by nebben11 on 2008-05-25
Replacing the fan is easy it just unscrews, but it might not solve the problem, I would also look in to replacing the heat sink and adding case fans to the back of the computer, I'v had a ton of cards blowup due to bad circulation

---

### Post by &amp;wP*!) on 2008-05-25
> **nebben11 said:**
> Replacing the fan is easy it just unscrews, but it might not solve the problem, I would also look in to replacing the heat sink and adding case fans to the back of the computer, I'v had a ton of cards blowup due to bad circulation
Also, removing the dust of the motherboard mostly helps. I sometimes even vacuum the case.

I had a lot of times that my system did not boot because of dust in the hardware.

---

### Post by jesushero on 2008-05-26
> **pencuse said:**
> Hi, I have an MSI KT6 Ultra MS-6590 on which GeForce 5200 FX is plugged. I am using this hardware for 3 years, without any system crash. I have installed Windows XP, Ubuntu, Fedora, OpenSuse, Mandriva. I have used third-party drivers (Restricted one at Ubuntu, Livna at Fedora), did not see anything.

Restart your Ubuntu and let him crash again. Can you send us then:
/var/log/messages
/var/log/syslog
/var/log/Xorg.0.log
and output of **lspci -vvv**.

Attach these 3 files here. And tell us what kind of crash do you see? What do you mean with "crash"? Kernel panic?

Hello, thanks for your reply. I haven't had a crash in a while now as I only run GDM for 5-10 minutes every time.. I usually run tty-only mode, which has no problems. /var/log/Xorg.0.log never had any specific information relating to the crashes. /var/log/messages and /var/log/syslog either contain an entry for a Kernel oops or an entry for a faulty Keyring.so module. I will post them as soon as I get them again. 

The command with the most interesting output is [B[acpi -t[/B] 
In normal, tty-only running, the temperature is 44oC. When using GDM, shortly before a crash I've spotted temperatures up to 65oC. This is the AMBIENT temperature, not the CPU temperature! I have checked this against the BIOS temperature meter, which contains a separate reading for the CPU, always a bit warmer than the 44oC ambient temperature. The CPU is usually at 46-48oC. An easily repeatable way of heating up the graphics card is through video rendering, especially using cinelerra. 

Here's the lspci -vvv:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Albatron Corp. Unknown device 2570
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: f0000000-f7ffffff
	Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Albatron Corp. Unknown device 24c2
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at d800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Albatron Corp. Unknown device 24c2
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 4: I/O ports at d000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Albatron Corp. Unknown device 24c2
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at d400 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Albatron Corp. Unknown device 24cd
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 19
	Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: fff00000-000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Albatron Corp. Unknown device 24c2
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at f000 [size=16]
	Region 5: Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Subsystem: Albatron Corp. Unknown device 24c2
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 11
	Region 4: I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 248 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at f9000000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: 3Com Corporation 3CSOHO100B-TX 910-A01 [tulip] (rev 31)
	Subsystem: 3Com Corporation Unknown device 1000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (16000ns min, 32000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at c000 [size=256]
	Region 1: Memory at fb008000 (32-bit, non-prefetchable) [size=1K]
	[virtual] Expansion ROM at fa000000 [disabled] [size=128K]
	Capabilities: <access denied>

02:04.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
	Subsystem: Creative Labs CT4832 SBLive! Value
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at c400 [size=32]
	Capabilities: <access denied>

02:04.1 Input device controller: Creative Labs SB Live! Game Port (rev 06)
	Subsystem: Creative Labs Gameport Joystick
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Region 0: I/O ports at c800 [size=8]
	Capabilities: <access denied>

02:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: SiteCom Europe BV Unknown device 90ab
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>

```

And here's the Xorg.0.log:

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
Current Operating System: Linux Levendis 2.6.24-16-rt #1 SMP PREEMPT RT Thu Apr 10 15:15:40 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 27 01:35:09 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
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
(II) PCI: 00:00:0: chip 8086,2570 card 17f2,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 17f2,24c2 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 17f2,24c2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 17f2,24c2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 17f2,24cd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 17f2,24c2 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 17f2,24c2 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 10b7,9300 card 10b7,1000 rev 31 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1102,0002 card 1102,8027 rev 06 class 04,01,00 hdr 80
(II) PCI: 02:04:1: chip 1102,7002 card 1102,0020 rev 06 class 09,80,00 hdr 80
(II) PCI: 02:0a:0: chip 1814,0301 card 182d,90ab rev 00 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xf8000000/24, 0xf0000000/27
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
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xefffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfb000000 - 0xfb007fff (0x8000) MX[B]
	[1] -1	0	0xfb008000 - 0xfb0083ff (0x400) MX[B]
	[2] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[3] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[4] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[5] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[8] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[9] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[10] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[11] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfb000000 - 0xfb007fff (0x8000) MX[B]
	[1] -1	0	0xfb008000 - 0xfb0083ff (0x400) MX[B]
	[2] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[3] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[4] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[5] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[8] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[9] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[10] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[11] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb000000 - 0xfb007fff (0x8000) MX[B]
	[5] -1	0	0xfb008000 - 0xfb0083ff (0x400) MX[B]
	[6] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[7] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[16] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.05  Tue Jan 22 20:11:30 PST 2008
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  96.43.05  Tue Jan 22 19:38:46 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb000000 - 0xfb007fff (0x8000) MX[B]
	[5] -1	0	0xfb008000 - 0xfb0083ff (0x400) MX[B]
	[6] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[7] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[16] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfb000000 - 0xfb007fff (0x8000) MX[B]
	[5] -1	0	0xfb008000 - 0xfb0083ff (0x400) MX[B]
	[6] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[7] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[19] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.42.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     ADI PnP Monitor (CRT-0)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): ADI PnP Monitor (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (92, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[1] 0	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfb000000 - 0xfb007fff (0x8000) MX[B]
	[7] -1	0	0xfb008000 - 0xfb0083ff (0x400) MX[B]
	[8] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[9] -1	0	0xfc000000 - 0xfc0003ff (0x400) MX[B]
	[10] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

```

I hope this helps... Let me know if you come up with something..

---

### Post by jesushero on 2008-05-26
> **nebben11 said:**
> Replacing the fan is easy it just unscrews, but it might not solve the problem, I would also look in to replacing the heat sink and adding case fans to the back of the computer, I'v had a ton of cards blowup due to bad circulation

It never had a fan to start with! So I'd have to find one that attaches to the heat sink. The heat sink is fairly large. I have a big fan in the back of the case and one mounted on the CPU heatsink. Running the computer with no sides doesn't help much. I think what happens is that the graphics card processor overheats and causes some fault in the system, causing it to crash.

---

### Post by jesushero on 2008-05-26
> **pencuse said:**
> Also, removing the dust of the motherboard mostly helps. I sometimes even vacuum the case.

I had a lot of times that my system did not boot because of dust in the hardware.

I've tried this as well, didn't make any difference. I spent hours taking the dust off of all the tiny spaces. Especially the graphics card is shiny and clean. Thanks anyway..

---

### Post by jesushero on 2008-05-26
> **pencuse said:**
> And tell us what kind of crash do you see? What do you mean with "crash"? Kernel panic?

Forgot to answer this before, usually while everything seems fine, the screen freezes up, the sound (if playing) loops a few miliseconds over and over again, and the caps-lock on the keyboard does not respond (the led doesn't go on). I believe it is an X lock-up, since the internal stuff still works. For example, once, during a crash there was an active open ssh connection to this machine. While the computer was unusable locally, the remote user experienced no difference in behavior and was still able to work on the computer over ssh for about 20 minutes. The only problem over ssh was the "sudo reboot now" command, which killed the connection but did not reboot the machine. Nothing changed on the frozen screen locally, and the user was not able to re-establish an ssh connection up until I pressed the reset button. In some rare cases, the keyboard leds flash, in sync with the music looping. 

One idea I had to test my X theory is to somehow map "Ctrl-Alt-Backspace" to the power button, which operates with a 4 second delay to switch the power off. So when the computer freezes, I would press the power button to reset the X server. If I'm right, the X should successfully restart. Any ideas on how I can do that?

PS: All the crash information is the same for both of the two similar machines. This started with Gutsy and is still here with Hardy.

---

