---
title: "Unsupported graphical card on 11.10 &amp; 12.04 release while OK with Fedora 16"
date: 2011-12-10
forum: Hardware
---

### Post by phil4000n on 2011-12-10
(L)unbutu 11.10 & 12.04 alpha1 fails to support my graphical card (in the sence that the screen is heavy vertically interlaced, to a point that one can not see what's on the screen).

**OK with Fedora 16 & AV Linux 5.0.2**
RE: [http://www.commandlinefu.com/commands/view/6894/get-information-on-your-graphics-card-on-linux-such-as-graphics-memory-size](http://www.commandlinefu.com/commands/view/6894/get-information-on-your-graphics-card-on-linux-such-as-graphics-memory-size)

**For the sake of clarity I put it bold the command line instruction from the working AV Linux:**
**tester@tester:~$ glxinfo | grep renderer**
OpenGL renderer string: Software Rasterizer
**tester@tester:~$ lspci**
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Volari V3XT/V5/V8 (rev 02)
**tester@tester:~$ lspci -v -s `lspci | awk '/VGA/{print $1}'`**
01:00.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Volari V3XT/V5/V8 (rev 02) (prog-if 00 [VGA controller])
    Subsystem: XGI Technology Inc. (eXtreme Graphics Innovation) Volari V3XT/V5/V8
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    BIST result: 00
    Memory at b0000000 (32-bit, prefetchable) [size=256M]
    Memory at cfec0000 (32-bit, non-prefetchable) [size=256K]
    I/O ports at bc00 [size=128]
    Expansion ROM at cfeb0000 [disabled] [size=64K]
    Capabilities: <access denied>

tester@tester:~$

---

### Post by MoreOrLess on 2011-12-10
Post output of /var/log/Xorg.0.log
Is this issue limited to Unity desktop? (I suggest using lxde to test).

---

### Post by phil4000n on 2011-12-11
Thanks for the swift reply.

As I wrote I tried with precise-desktop-i386 (Lubuntu 12.04 alpha 1) or even Linux Mint LXDE 11 they share the same problem.

But no problem with
AV Linux 5.x
or
Fedora 16 LXDE

Simply (L)ubuntu do not recognize properly the graphical card and so takes the wrong driver, while the other distro do correctly detect.

>Post output of /var/log/Xorg.0.log
From AV Linux:
tester@tester:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied

If you need for more command line result either from the working distro or from the failing one, just ask to that it's fixed and i'll check that in a build.

---

### Post by phil4000n on 2011-12-19
Also works with Fudundu

---

### Post by Perfect Storm on 2011-12-19
> **phil4000n said:**
> Also works with Fudundu

It's because it's Fedora Based. So it's likely if it works with Fedora, it works Fuduntu.

---

### Post by fuduntu on 2011-12-19
> **phil4000n said:**
> Also works with Fudundu

Fuduntu uses a newer version of Xorg.  We upgraded to 1.11.1 in October.

---

### Post by phil4000n on 2011-12-21
Well, works also on Sabayon7 LXDE (Gentoo based)
AV Linux don't know on what it is based, but it also works

---

### Post by phil4000n on 2011-12-24
**Well interestingly it works on Puppy Linux 3-headed(Ubuntu 10.04 based I think), but more recent Puppy such as racy Puppy 2.2 no.**

**So I publish the 2 for comparisons.**

Result for Puppy Linux 3-headed dog ([http://www.murga-linux.com/puppy/viewtopic.php?t=70736](http://www.murga-linux.com/puppy/viewtopic.php?t=70736))
> sh-4.1# lspci -vv
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
	Capabilities: [c0] AGP version 3.0
		Status: RQ=32 Iso- ArqSz=2 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel driver in use: agpgart-sis
	Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=64
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: cfd00000-cfefffff
	Prefetchable memory behind bridge: afa00000-cfbfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 0
	Region 4: I/O ports at 0c00 [size=32]
	Kernel modules: i2c-sis96x

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 128
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at ff00 [size=16]
	Kernel driver in use: pata_sis

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] C-Media AC'97 Sound Controller (rev a0)
	Subsystem: Elitegroup Computer Systems Device 1b25
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (13000ns min, 2750ns max)
	Interrupt: pin C routed to IRQ 18
	Region 0: I/O ports at dc00 [size=256]
	Region 1: I/O ports at d800 [size=128]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 21
	Region 0: Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin D routed to IRQ 23
	Region 0: Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (13000ns min, 2750ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at d400 [size=256]
	Region 1: Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at cffa0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: sis900
	Kernel modules: sis900

01:00.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Volari V3XT/V5/V8 (rev 02) (prog-if 00 [VGA controller])
	Subsystem: XGI Technology Inc. (eXtreme Graphics Innovation) Volari V3XT/V5/V8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 4000ns max)
	Interrupt: pin A routed to IRQ 11
	BIST result: 00
	Region 0: Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Region 1: Memory at cfec0000 (32-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at bc00 [size=128]
	Expansion ROM at cfeb0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] AGP version 3.0
		Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

sh-4.1#


**Results for racyNOP-5.2.2 (racy Puppy with XFCE)**
[http://www.murga-linux.com/puppy/viewtopic.php?t=73728](http://www.murga-linux.com/puppy/viewtopic.php?t=73728)

> # lspci -vv
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
	Capabilities: [c0] AGP version 3.0
		Status: RQ=32 Iso- ArqSz=2 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel driver in use: agpgart-sis

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=64
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: cfd00000-cfefffff
	Prefetchable memory behind bridge: afa00000-cfbfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 0
	Region 4: I/O ports at 0c00 [size=32]
	Kernel driver in use: sis96x_smbus

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 128
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at ff00 [size=16]
	Kernel driver in use: pata_sis

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] C-Media AC'97 Sound Controller (rev a0)
	Subsystem: Elitegroup Computer Systems Device 1b25
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (13000ns min, 2750ns max)
	Interrupt: pin C routed to IRQ 18
	Region 0: I/O ports at dc00 [size=256]
	Region 1: I/O ports at d800 [size=128]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: Intel ICH

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 21
	Region 0: Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin D routed to IRQ 23
	Region 0: Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
	Subsystem: Elitegroup Computer Systems Device 1808
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (13000ns min, 2750ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at d400 [size=256]
	Region 1: Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at cffa0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: sis900

01:00.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Volari V3XT/V5/V8 (rev 02) (prog-if 00 [VGA controller])
	Subsystem: XGI Technology Inc. (eXtreme Graphics Innovation) Volari V3XT/V5/V8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 4000ns max)
	Interrupt: pin A routed to IRQ 16
	BIST result: 00
	Region 0: Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Region 1: Memory at cfec0000 (32-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at bc00 [size=128]
	Expansion ROM at cfeb0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] AGP version 3.0
		Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel driver in use: xgifb

# 


---

### Post by phil4000n on 2011-12-26
WinMerge shows some differences between the lspci -vv of 3headed dog and racyNOP, notably for IDE interface, on the working 3headed dog it shows:
> Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
While on the non-working racyNOP those are flaged as [disabled]
I presume that's where the issue lies, though there are some other differences.

Thanks if someone could fix this

---

### Post by grahammechanical on 2011-12-26
You say that this is the issue:

> Simply (L)ubuntu do not recognize properly the graphical card and so takes the wrong driver, while the other distro do correctly detect.

So, what are the drivers being used by Fedora and the other OSes that recognise this card correctly. Is there a Debian/Ubuntu based distro that works with the video card? If so, what driver is that OS using?

Searching for Volari V3XT I find this:

[http://www.phoronix.com/scan.php?page=article&item=619&num=1]("http://www.phoronix.com/scan.php?page=article&item=619&num=1")

[http://www.phoronix.com/scan.php?page=article&item=207&num=1]("http://www.phoronix.com/scan.php?page=article&item=207&num=1")

[http://www.downloadsource.net/761/XGI-Volari-V8-V5-V3XT-Driver-Linux/]("http://www.downloadsource.net/761/XGI-Volari-V8-V5-V3XT-Driver-Linux/")

Note: the compatible with 32bit Linux comment. Not 64bit?

It seems to me that once again the blame lies squarely at the door of the manufacturer for failing to support Linux.

Regards.

---

### Post by fuduntu on 2011-12-26
> **grahammechanical said:**
> It seems to me that once again the blame lies squarely at the door of the manufacturer for failing to support Linux.

Uhh, no.  It works with the newer version of Xorg shipped with Fedora 16.

---

### Post by phil4000n on 2011-12-26
> It seems to me that once again the blame lies squarely at the door of the manufacturer for failing to support Linux.
No I think it's either a regression bug or a scripting bug.
Apparently distros based on
1/ Ubuntu 10.04 works, but no more if based on 11.10 or 12.04
2/ Non Ubuntu based distros seems to work fine.

Some working ones are:
Fedora 16
avlinux5.0.2-lxde-i386-en
Puppy 528
Sabayon_Linux_7_x86_LXDE
PartedMagic 5.10

Some failing distros
Linux Mint LXDE 11
Linux Mint 12
(L)Ubuntu 11.10 & 12.04 alpha1
archbang-2011.11-i686
PartedMagic 6.0
More recent Puppy Based distros such as luki-003 or racy-5.2.2

---

