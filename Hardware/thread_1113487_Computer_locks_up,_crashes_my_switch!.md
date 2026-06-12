---
title: "Computer locks up, crashes my switch!"
date: 2009-04-01
forum: Hardware
---

### Post by grantemsley on 2009-04-01
I'm a computer technician, so I'm usually pretty good at figuring these things out.  But after pouring over forums and bug reports, I've got nothing.

I just built a new shuttle computer ([http://us.shuttle.com/barebone/Models/SN68SG2.html](http://us.shuttle.com/barebone/Models/SN68SG2.html)), with NVDIA GeForce7025/nForce™630a chipset (shows as MCP68 in lcpci).

The computer will work fine for awhile, then hangs.  Can't turn the numlock light on or off, can't use the magic sysreq keys to reboot the system.

When it does this, the ethernet lights go CRAZY, blinking as fast as possible.  A few seconds later, my switch (24 port freedom9 100mb) decides to stop switching and all the computers on the lan get disconnected.

It seems to happen most with high hard drive or lan activity.  The most notable times have been:

- Copying files to the hard drive during setup with mythbuntu 8.10 and 9.04 beta
- apt-get upgrade while downloading or installing files (again, with both versions of mythbuntu)

I ran a memory test and hard drive test, both passed.
I tried a different cable and switch.

I'm at a loss as to how to debug this one.  Is it a driver problem?  Is it a bad motherboard?  Any ideas on how I can figure this out would be much appreciated!


lspci -v -v -v

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: nVidia Corporation Device cb84
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=0 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=3 IsocEn- LSEn+ ExtCTL- 64b-
		Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 1.0GHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 200MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 10
	Region 0: I/O ports at fc00 [size=64]
	Region 4: I/O ports at 1c00 [size=64]
	Region 5: I/O ports at 1c40 [size=64]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: nVidia Corporation Device cb84
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 21
	Region 0: Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f297:3114
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
		Masking: 00000000  Pending: 00000000
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fd200000-fd2fffff
	Prefetchable memory behind bridge: fdf00000-fdffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Capabilities: [b8] Subsystem: nVidia Corporation Device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 2296
	Region 0: I/O ports at 09f0 [size=8]
	Region 1: I/O ports at 0bf0 [size=4]
	Region 2: I/O ports at 0970 [size=8]
	Region 3: I/O ports at 0b70 [size=4]
	Region 4: I/O ports at dc00 [size=16]
	Region 5: Memory at fe026000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [8c] SATA HBA <?>
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
		Address: 00000000fee0300c  Data: 4189
	Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3114
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 2295
	Region 0: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at d800 [size=8]
	Region 2: Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
	Region 3: Memory at fe029000 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
		Address: 00000000fee0300c  Data: 41c1
		Masking: 000000fe  Pending: 00000000
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f6000000-f9ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4149
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  1, PowerLimit 75.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet+ LinkState+
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4151
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 256 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  2, PowerLimit 10.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4159
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 256 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  3, PowerLimit 10.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4161
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 256 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #3, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  4, PowerLimit 10.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fd800000-fd8fffff
	Prefetchable memory behind bridge: 00000000fd700000-00000000fd7fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4169
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 256 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #4, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  5, PowerLimit 10.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: fd600000-fd6fffff
	Prefetchable memory behind bridge: 00000000fd500000-00000000fd5fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4171
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 256 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #5, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  6, PowerLimit 10.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fd400000-fd4fffff
	Prefetchable memory behind bridge: 00000000fd300000-00000000fd3fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
		Address: 00000000fee0300c  Data: 4179
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
		Mapping Address Base: 00000000fee00000
	Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 256 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #6, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  7, PowerLimit 10.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		!!! Possibly incomplete decoding
		Command: WarmRst+ DblEnd-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
		Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Revision ID: 1.02

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3126
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fd2ff000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at fd2f8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
	Subsystem: nVidia Corporation Device 05cc
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at f9000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [78] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel modules: nvidiafb


```

DMESG


```
[    0.000000] BIOS EBDA/lowmem at: 0009f400/0009f400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #37-Ubuntu SMP Mon Mar 23 16:40:00 UTC 2009 (Ubuntu 2.6.28-11.37-generic)
[    0.000000] Command line: root=UUID=0e1405a7-8fad-49d8-a34e-a4adfc09e548 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7fef0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  modified: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  modified: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007fef0000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fef0000 page 4k
[    0.000000] kernel direct mapping tables up to 7fef0000 @ 10000-14000
[    0.000000] last_map_addr: 7fef0000 end: 7fef0000
[    0.000000] RAMDISK: 3784e000 - 37fef8f3
[    0.000000] ACPI: RSDP 000F7F20, 0014 (r0 Shuttl)
[    0.000000] ACPI: RSDT 7FEF3000, 003C (r1 Shuttl Shuttle  42302E31 NVDA        0)
[    0.000000] ACPI: FACP 7FEF3080, 0074 (r1 Shuttl Shuttle  42302E31 NVDA        0)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080926]
[    0.000000] ACPI: DSDT 7FEF3100, 6EBC (r1 SHUTTL SN68SV10     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEF0000, 0040
[    0.000000] ACPI: SSDT 7FEFA040, 0248 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 7FEFA2C0, 0038 (r1 Shuttl Shuttle  42302E31 NVDA       98)
[    0.000000] ACPI: MCFG 7FEFA300, 003C (r1 Shuttl Shuttle  42302E31 NVDA        0)
[    0.000000] ACPI: SLIC 7FEFA340, 0176 (r1 Shuttl Shuttle  42302E31 NVDA        0)
[    0.000000] ACPI: APIC 7FEF9FC0, 0072 (r1 Shuttl Shuttle  42302E31 NVDA        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003784e000 - 0037fef8f3]          RAMDISK ==> [003784e000 - 0037fef8f3]
[    0.000000]   #4 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f3d50] 000f3d50
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fef0
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2540 pages reserved
[    0.000000]   DMA zone: 1387 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7109 pages used for memmap
[    0.000000]   DMA32 zone: 512811 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514198
[    0.000000] Kernel command line: root=UUID=0e1405a7-8fad-49d8-a34e-a4adfc09e548 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2300.384 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 20971520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 39bc000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 2024972k/2096064k available (4764k kernel code, 452k absent, 70068k reserved, 2541k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4600.76 BogoMIPS (lpj=9201536)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] tseg: 007ff00000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] ACPI: Core revision 20080926
[    0.004000] ACPI: Checking initramfs for custom DSDT
[    0.270025] Setting APIC routing to flat
[    0.270557] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.310254] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02
[    0.312001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4600.44 BogoMIPS (lpj=9200895)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.396171] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02
[    0.396187] Brought up 2 CPUs
[    0.396189] Total of 2 processors activated (9201.21 BogoMIPS).
[    0.396272] CPU0 attaching sched-domain:
[    0.396274]  domain 0: span 0-1 level CPU
[    0.396276]   groups: 0 1
[    0.396281] CPU1 attaching sched-domain:
[    0.396282]  domain 0: span 0-1 level CPU
[    0.396283]   groups: 1 0
[    0.396340] net_namespace: 1400 bytes
[    0.396340] Booting paravirtualized kernel on bare hardware
[    0.396340] Time: 18:41:30  Date: 04/01/09
[    0.396340] regulator: core version 0.5
[    0.396340] NET: Registered protocol family 16
[    0.396340] node 0 link 0: io port [5000, ffff]
[    0.396340] TOM: 0000000080000000 aka 2048M
[    0.396340] node 0 link 0: mmio [a0000, bffff]
[    0.396340] node 0 link 0: mmio [80000000, efffffff]
[    0.396340] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.396340] node 0 link 0: mmio [f0000000, f07fffff]
[    0.396340] bus: [00,08] on node 0 link 0
[    0.396340] bus: 00 index 0 io port: [0, ffff]
[    0.396340] bus: 00 index 1 mmio: [a0000, bffff]
[    0.396340] bus: 00 index 2 mmio: [80000000, f3ffffff]
[    0.396340] bus: 00 index 3 mmio: [f4000000, fcffffffff]
[    0.396340] ACPI: bus type pci registered
[    0.396340] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.396340] PCI: MCFG area at f0000000 reserved in E820
[    0.399124] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.399126] PCI: Using configuration type 1 for base access
[    0.400791] ACPI: EC: Look up EC in DSDT
[    0.409295] ACPI: Interpreter enabled
[    0.409298] ACPI: (supports S0 S3 S4 S5)
[    0.409316] ACPI: Using IOAPIC for interrupt routing
[    0.418099] ACPI: No dock devices found.
[    0.418110] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.418287] pci 0000:00:01.1: reg 10 io port: [0xfc00-0xfc3f]
[    0.418297] pci 0000:00:01.1: reg 20 io port: [0x1c00-0x1c3f]
[    0.418300] pci 0000:00:01.1: reg 24 io port: [0x1c40-0x1c7f]
[    0.418310] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.418315] pci 0000:00:01.1: PME# disabled
[    0.418362] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
[    0.418378] pci 0000:00:02.0: supports D1 D2
[    0.418379] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418382] pci 0000:00:02.0: PME# disabled
[    0.418402] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
[    0.418419] pci 0000:00:02.1: supports D1 D2
[    0.418420] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418423] pci 0000:00:02.1: PME# disabled
[    0.418446] pci 0000:00:04.0: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.418462] pci 0000:00:04.0: supports D1 D2
[    0.418463] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418466] pci 0000:00:04.0: PME# disabled
[    0.418485] pci 0000:00:04.1: reg 10 32bit mmio: [0xfe02c000-0xfe02c0ff]
[    0.418502] pci 0000:00:04.1: supports D1 D2
[    0.418504] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418507] pci 0000:00:04.1: PME# disabled
[    0.418536] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]
[    0.418564] pci 0000:00:07.0: reg 10 32bit mmio: [0xfe020000-0xfe023fff]
[    0.418580] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.418583] pci 0000:00:07.0: PME# disabled
[    0.418628] pci 0000:00:09.0: reg 10 io port: [0x9f0-0x9f7]
[    0.418631] pci 0000:00:09.0: reg 14 io port: [0xbf0-0xbf3]
[    0.418634] pci 0000:00:09.0: reg 18 io port: [0x970-0x977]
[    0.418637] pci 0000:00:09.0: reg 1c io port: [0xb70-0xb73]
[    0.418640] pci 0000:00:09.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.418643] pci 0000:00:09.0: reg 24 32bit mmio: [0xfe026000-0xfe027fff]
[    0.418675] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.418678] pci 0000:00:0a.0: reg 14 io port: [0xd800-0xd807]
[    0.418682] pci 0000:00:0a.0: reg 18 32bit mmio: [0xfe02a000-0xfe02a0ff]
[    0.418685] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xfe029000-0xfe02900f]
[    0.418695] pci 0000:00:0a.0: supports D1 D2
[    0.418696] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418700] pci 0000:00:0a.0: PME# disabled
[    0.418721] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418723] pci 0000:00:0b.0: PME# disabled
[    0.418743] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418745] pci 0000:00:0c.0: PME# disabled
[    0.418764] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418767] pci 0000:00:0d.0: PME# disabled
[    0.418786] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418788] pci 0000:00:0e.0: PME# disabled
[    0.418807] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418809] pci 0000:00:0f.0: PME# disabled
[    0.418829] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418831] pci 0000:00:10.0: PME# disabled
[    0.418850] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.418852] pci 0000:00:11.0: PME# disabled
[    0.418941] pci 0000:01:08.0: reg 10 32bit mmio: [0xfd2ff000-0xfd2ff7ff]
[    0.418946] pci 0000:01:08.0: reg 14 32bit mmio: [0xfd2f8000-0xfd2fbfff]
[    0.418969] pci 0000:01:08.0: supports D1 D2
[    0.418970] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot
[    0.418973] pci 0000:01:08.0: PME# disabled
[    0.418997] pci 0000:00:08.0: transparent bridge
[    0.418999] pci 0000:00:08.0: bridge io port: [0xc000-0xcfff]
[    0.419002] pci 0000:00:08.0: bridge 32bit mmio: [0xfd200000-0xfd2fffff]
[    0.419005] pci 0000:00:08.0: bridge 32bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.419026] pci 0000:02:00.0: reg 10 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.419033] pci 0000:02:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.419039] pci 0000:02:00.0: reg 1c 64bit mmio: [0xf6000000-0xf7ffffff]
[    0.419043] pci 0000:02:00.0: reg 24 io port: [0xbc00-0xbc7f]
[    0.419047] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.419086] pci 0000:00:0b.0: bridge io port: [0xb000-0xbfff]
[    0.419088] pci 0000:00:0b.0: bridge 32bit mmio: [0xf6000000-0xf9ffffff]
[    0.419091] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.419122] pci 0000:00:0c.0: bridge io port: [0xa000-0xafff]
[    0.419125] pci 0000:00:0c.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.419127] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.419159] pci 0000:00:0d.0: bridge io port: [0x9000-0x9fff]
[    0.419161] pci 0000:00:0d.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.419164] pci 0000:00:0d.0: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.419195] pci 0000:00:0e.0: bridge io port: [0x8000-0x8fff]
[    0.419197] pci 0000:00:0e.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
[    0.419200] pci 0000:00:0e.0: bridge 64bit mmio pref: [0xfd900000-0xfd9fffff]
[    0.419231] pci 0000:00:0f.0: bridge io port: [0x7000-0x7fff]
[    0.419233] pci 0000:00:0f.0: bridge 32bit mmio: [0xfd800000-0xfd8fffff]
[    0.419236] pci 0000:00:0f.0: bridge 64bit mmio pref: [0xfd700000-0xfd7fffff]
[    0.419267] pci 0000:00:10.0: bridge io port: [0x6000-0x6fff]
[    0.419269] pci 0000:00:10.0: bridge 32bit mmio: [0xfd600000-0xfd6fffff]
[    0.419272] pci 0000:00:10.0: bridge 64bit mmio pref: [0xfd500000-0xfd5fffff]
[    0.419303] pci 0000:00:11.0: bridge io port: [0x5000-0x5fff]
[    0.419306] pci 0000:00:11.0: bridge 32bit mmio: [0xfd400000-0xfd4fffff]
[    0.419309] pci 0000:00:11.0: bridge 64bit mmio pref: [0xfd300000-0xfd3fffff]
[    0.419320] bus 00 -> node 0
[    0.419327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.419779] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.479366] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.479544] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[    0.479719] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.479892] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.480070] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.480246] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 *11 14 15)
[    0.480420] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.480594] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.480768] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.480943] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[    0.481117] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.481292] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.481470] ACPI: PCI Interrupt Link [LU1B] (IRQs 5 7 9 *10 11 14 15)
[    0.481644] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 10 *11 14 15)
[    0.481819] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[    0.481994] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.482169] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.482344] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.482525] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.482701] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.482917] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.483126] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.483334] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.483543] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.483751] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.483958] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
[    0.484172] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.484380] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.484588] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.484797] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.485006] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[    0.485215] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[    0.485428] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[    0.485641] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.485851] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.486060] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.486269] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.486477] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.486686] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.486894] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.487067] ACPI: WMI: Mapper loaded
[    0.487140] SCSI subsystem initialized
[    0.487140] libata version 3.00 loaded.
[    0.487140] usbcore: registered new interface driver usbfs
[    0.487140] usbcore: registered new interface driver hub
[    0.487140] usbcore: registered new device driver usb
[    0.487140] PCI: Using ACPI for IRQ routing
[    0.496008] Bluetooth: Core ver 2.13
[    0.496022] NET: Registered protocol family 31
[    0.496022] Bluetooth: HCI device and connection manager initialized
[    0.496022] Bluetooth: HCI socket layer initialized
[    0.496022] NET: Registered protocol family 8
[    0.496022] NET: Registered protocol family 20
[    0.496029] NetLabel: Initializing
[    0.496030] NetLabel:  domain hash size = 128
[    0.496031] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.496045] NetLabel:  unlabeled traffic allowed by default
[    0.496184] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.496187] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.500065] AppArmor: AppArmor Filesystem Enabled
[    0.504014] Switched to high resolution mode on CPU 0
[    0.504174] Switched to high resolution mode on CPU 1
[    0.512014] pnp: PnP ACPI init
[    0.512025] ACPI: bus type pnp registered
[    0.513237] ACPI Error (psargs-0358): [GUR_._BAS] Namespace lookup failure, AE_NOT_FOUND
[    0.513242] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.MBIO._CRS] (Node ffff88007f814800), AE_NOT_FOUND
[    0.517446] pnp: PnP ACPI: found 12 devices
[    0.517447] ACPI: ACPI bus type pnp unregistered
[    0.517460] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.517462] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.517468] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.517473] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.517475] system 00:0b: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.517477] system 00:0b: iomem range 0x7fef0000-0x7fefffff could not be reserved
[    0.517479] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.517481] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.517484] system 00:0b: iomem range 0x100000-0x7feeffff could not be reserved
[    0.517486] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.517488] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.517490] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.517492] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.517495] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.517497] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.522168] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.522171] pci 0000:00:08.0:   IO window: 0xc000-0xcfff
[    0.522174] pci 0000:00:08.0:   MEM window: 0xfd200000-0xfd2fffff
[    0.522177] pci 0000:00:08.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.522183] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.522185] pci 0000:00:0b.0:   IO window: 0xb000-0xbfff
[    0.522187] pci 0000:00:0b.0:   MEM window: 0xf6000000-0xf9ffffff
[    0.522190] pci 0000:00:0b.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.522192] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.522194] pci 0000:00:0c.0:   IO window: 0xa000-0xafff
[    0.522197] pci 0000:00:0c.0:   MEM window: 0xfde00000-0xfdefffff
[    0.522199] pci 0000:00:0c.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.522202] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.522204] pci 0000:00:0d.0:   IO window: 0x9000-0x9fff
[    0.522206] pci 0000:00:0d.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.522208] pci 0000:00:0d.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.522211] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:05
[    0.522213] pci 0000:00:0e.0:   IO window: 0x8000-0x8fff
[    0.522215] pci 0000:00:0e.0:   MEM window: 0xfda00000-0xfdafffff
[    0.522217] pci 0000:00:0e.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.522220] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:06
[    0.522222] pci 0000:00:0f.0:   IO window: 0x7000-0x7fff
[    0.522225] pci 0000:00:0f.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.522227] pci 0000:00:0f.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.522230] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.522232] pci 0000:00:10.0:   IO window: 0x6000-0x6fff
[    0.522234] pci 0000:00:10.0:   MEM window: 0xfd600000-0xfd6fffff
[    0.522236] pci 0000:00:10.0:   PREFETCH window: 0x000000fd500000-0x000000fd5fffff
[    0.522239] pci 0000:00:11.0: PCI bridge, secondary bus 0000:08
[    0.522241] pci 0000:00:11.0:   IO window: 0x5000-0x5fff
[    0.522243] pci 0000:00:11.0:   MEM window: 0xfd400000-0xfd4fffff
[    0.522246] pci 0000:00:11.0:   PREFETCH window: 0x000000fd300000-0x000000fd3fffff
[    0.522253] pci 0000:00:08.0: setting latency timer to 64
[    0.522257] pci 0000:00:0b.0: setting latency timer to 64
[    0.522261] pci 0000:00:0c.0: setting latency timer to 64
[    0.522264] pci 0000:00:0d.0: setting latency timer to 64
[    0.522268] pci 0000:00:0e.0: setting latency timer to 64
[    0.522271] pci 0000:00:0f.0: setting latency timer to 64
[    0.522275] pci 0000:00:10.0: setting latency timer to 64
[    0.522278] pci 0000:00:11.0: setting latency timer to 64
[    0.522280] bus: 00 index 0 io port: [0x00-0xffff]
[    0.522282] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.522284] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.522286] bus: 01 index 1 mmio: [0xfd200000-0xfd2fffff]
[    0.522288] bus: 01 index 2 mmio: [0xfdf00000-0xfdffffff]
[    0.522289] bus: 01 index 3 io port: [0x00-0xffff]
[    0.522291] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.522293] bus: 02 index 0 io port: [0xb000-0xbfff]
[    0.522294] bus: 02 index 1 mmio: [0xf6000000-0xf9ffffff]
[    0.522296] bus: 02 index 2 mmio: [0xe0000000-0xefffffff]
[    0.522297] bus: 02 index 3 mmio: [0x0-0x0]
[    0.522299] bus: 03 index 0 io port: [0xa000-0xafff]
[    0.522300] bus: 03 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.522302] bus: 03 index 2 mmio: [0xfdd00000-0xfddfffff]
[    0.522304] bus: 03 index 3 mmio: [0x0-0x0]
[    0.522305] bus: 04 index 0 io port: [0x9000-0x9fff]
[    0.522307] bus: 04 index 1 mmio: [0xfdc00000-0xfdcfffff]
[    0.522308] bus: 04 index 2 mmio: [0xfdb00000-0xfdbfffff]
[    0.522310] bus: 04 index 3 mmio: [0x0-0x0]
[    0.522311] bus: 05 index 0 io port: [0x8000-0x8fff]
[    0.522313] bus: 05 index 1 mmio: [0xfda00000-0xfdafffff]
[    0.522315] bus: 05 index 2 mmio: [0xfd900000-0xfd9fffff]
[    0.522316] bus: 05 index 3 mmio: [0x0-0x0]
[    0.522318] bus: 06 index 0 io port: [0x7000-0x7fff]
[    0.522319] bus: 06 index 1 mmio: [0xfd800000-0xfd8fffff]
[    0.522321] bus: 06 index 2 mmio: [0xfd700000-0xfd7fffff]
[    0.522322] bus: 06 index 3 mmio: [0x0-0x0]
[    0.522324] bus: 07 index 0 io port: [0x6000-0x6fff]
[    0.522325] bus: 07 index 1 mmio: [0xfd600000-0xfd6fffff]
[    0.522327] bus: 07 index 2 mmio: [0xfd500000-0xfd5fffff]
[    0.522329] bus: 07 index 3 mmio: [0x0-0x0]
[    0.522330] bus: 08 index 0 io port: [0x5000-0x5fff]
[    0.522332] bus: 08 index 1 mmio: [0xfd400000-0xfd4fffff]
[    0.522333] bus: 08 index 2 mmio: [0xfd300000-0xfd3fffff]
[    0.522335] bus: 08 index 3 mmio: [0x0-0x0]
[    0.522346] NET: Registered protocol family 2
[    0.556057] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.556517] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.558489] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.559006] TCP: Hash tables configured (established 262144 bind 65536)
[    0.559008] TCP reno registered
[    0.568094] NET: Registered protocol family 1
[    0.568206] checking if image is initramfs... it is
[    1.108642] Freeing initrd memory: 7814k freed
[    1.113381] audit: initializing netlink socket (disabled)
[    1.113398] type=2000 audit(1238611290.112:1): initialized
[    1.120467] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.121500] VFS: Disk quotas dquot_6.5.1
[    1.121544] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.122033] fuse init (API version 7.10)
[    1.122099] msgmni has been set to 3971
[    1.122276] alg: No test for stdrng (krng)
[    1.122290] io scheduler noop registered
[    1.122292] io scheduler anticipatory registered
[    1.122293] io scheduler deadline registered
[    1.122329] io scheduler cfq registered (default)
[    1.122358] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.153057] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.153071] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.153085] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.153101] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.153115] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.153129] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.153143] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.153156] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.153170] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.153184] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.153198] pci 0000:00:11.0: Enabling HT MSI Mapping
[    1.153221] pci 0000:02:00.0: Boot video device
[    1.159903] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.159923] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.159938] pcieport-driver 0000:00:0b.0: irq 2303 for MSI/MSI-X
[    1.159944] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.159956] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.159987] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.160009] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.160020] pcieport-driver 0000:00:0c.0: irq 2302 for MSI/MSI-X
[    1.160025] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.160035] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.160067] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.160085] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.160095] pcieport-driver 0000:00:0d.0: irq 2301 for MSI/MSI-X
[    1.160100] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.160110] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.160139] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    1.160157] pcieport-driver 0000:00:0e.0: found MSI capability
[    1.160168] pcieport-driver 0000:00:0e.0: irq 2300 for MSI/MSI-X
[    1.160173] pci_express 0000:00:0e.0:pcie00: allocate port service
[    1.160183] pci_express 0000:00:0e.0:pcie03: allocate port service
[    1.160212] pcieport-driver 0000:00:0f.0: setting latency timer to 64
[    1.160230] pcieport-driver 0000:00:0f.0: found MSI capability
[    1.160240] pcieport-driver 0000:00:0f.0: irq 2299 for MSI/MSI-X
[    1.160245] pci_express 0000:00:0f.0:pcie00: allocate port service
[    1.160255] pci_express 0000:00:0f.0:pcie03: allocate port service
[    1.160285] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.160302] pcieport-driver 0000:00:10.0: found MSI capability
[    1.160312] pcieport-driver 0000:00:10.0: irq 2298 for MSI/MSI-X
[    1.160318] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.160330] pci_express 0000:00:10.0:pcie03: allocate port service
[    1.160359] pcieport-driver 0000:00:11.0: setting latency timer to 64
[    1.160377] pcieport-driver 0000:00:11.0: found MSI capability
[    1.160387] pcieport-driver 0000:00:11.0: irq 2297 for MSI/MSI-X
[    1.160392] pci_express 0000:00:11.0:pcie00: allocate port service
[    1.160405] pci_express 0000:00:11.0:pcie03: allocate port service
[    1.160444] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.160452] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.160579] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.160582] ACPI: Power Button (FF) [PWRF]
[    1.160620] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.160622] ACPI: Power Button (CM) [PWRB]
[    1.160675] fan PNP0C0B:00: registered as cooling_device0
[    1.160681] ACPI: Fan [FAN] (on)
[    1.160991] processor ACPI_CPU:00: registered as cooling_device1
[    1.161034] processor ACPI_CPU:01: registered as cooling_device2
[    1.165381] thermal LNXTHERM:01: registered as thermal_zone0
[    1.165704] ACPI: Thermal Zone [THRM] (40 C)
[    1.193244] Linux agpgart interface v0.103
[    1.193254] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.194036] brd: module loaded
[    1.194303] loop: module loaded
[    1.194364] Fixed MDIO Bus: probed
[    1.194369] PPP generic driver version 2.4.2
[    1.194421] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.194449] Driver 'sd' needs updating - please use bus_type methods
[    1.194457] Driver 'sr' needs updating - please use bus_type methods
[    1.194495] ahci 0000:00:09.0: version 3.0
[    1.194873] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.194884] ahci 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.194924] ahci 0000:00:09.0: irq 2296 for MSI/MSI-X
[    1.194986] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.194989] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.194992] ahci 0000:00:09.0: setting latency timer to 64
[    1.195376] scsi0 : ahci
[    1.195513] scsi1 : ahci
[    1.195575] scsi2 : ahci
[    1.195640] scsi3 : ahci
[    1.195727] ata1: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 2296
[    1.195730] ata2: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 2296
[    1.195732] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 2296
[    1.195734] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 2296
[    1.676017] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.679253] ata1.00: ATAPI: HL-DT-ST DVDRAM GH20NS10, EL00, max UDMA/100
[    1.683126] ata1.00: configured for UDMA/100
[    2.684015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.684580] ata2.00: ATA-7: ST3250310AS, 3.AAF, max UDMA/133
[    2.684582] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.685314] ata2.00: configured for UDMA/133
[    3.004015] ata3: SATA link down (SStatus 0 SControl 300)
[    3.324014] ata4: SATA link down (SStatus 0 SControl 300)
[    3.326837] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL00 PQ: 0 ANSI: 5
[    3.659695] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.659698] Uniform CD-ROM driver Revision: 3.20
[    3.659796] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.659839] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    3.659896] scsi 1:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[    3.659983] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.659996] sd 1:0:0:0: [sda] Write Protect is off
[    3.659998] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.660018] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.660074] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.660086] sd 1:0:0:0: [sda] Write Protect is off
[    3.660088] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.660106] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.660109]  sda: sda1 sda2 < sda5 sda6 >
[    3.689173] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.689203] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.689409] pata_amd 0000:00:06.0: version 0.3.10
[    3.689450] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.689544] scsi4 : pata_amd
[    3.689613] scsi5 : pata_amd
[    3.690194] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.690196] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    3.854938] ata6: port disabled. ignoring.
[    3.855321] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.855663] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    3.855673] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    3.855691] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.855693] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.855745] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.855774] ehci_hcd 0000:00:02.1: debug port 1
[    3.855778] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.855797] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    3.864017] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    3.864080] usb usb1: configuration #1 chosen from 1 choice
[    3.864105] hub 1-0:1.0: USB hub found
[    3.864112] hub 1-0:1.0: 5 ports detected
[    3.864386] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    3.864514] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    3.864521] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    3.864528] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    3.864530] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    3.864568] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    3.864594] ehci_hcd 0000:00:04.1: debug port 1
[    3.864597] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    3.864611] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfe02c000
[    3.876016] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    3.876068] usb usb2: configuration #1 chosen from 1 choice
[    3.876088] hub 2-0:1.0: USB hub found
[    3.876094] hub 2-0:1.0: 5 ports detected
[    3.876169] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.876497] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    3.876503] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    3.876512] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.876514] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.876557] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    3.876578] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    3.934041] usb usb3: configuration #1 chosen from 1 choice
[    3.934063] hub 3-0:1.0: USB hub found
[    3.934071] hub 3-0:1.0: 5 ports detected
[    3.934457] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    3.934460] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    3.934468] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    3.934470] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    3.934506] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    3.934526] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfe02d000
[    3.990042] usb usb4: configuration #1 chosen from 1 choice
[    3.990062] hub 4-0:1.0: USB hub found
[    3.990069] hub 4-0:1.0: 5 ports detected
[    3.990142] uhci_hcd: USB Universal Host Controller Interface driver
[    3.990205] usbcore: registered new interface driver libusual
[    3.990236] usbcore: registered new interface driver usbserial
[    3.990248] USB Serial support registered for generic
[    3.990258] usbcore: registered new interface driver usbserial_generic
[    3.990260] usbserial: USB Serial Driver core
[    3.990300] PNP: No PS/2 controller found. Probing ports directly.
[    4.022836] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    4.022837] If AUX port is really absent please use the 'i8042.noaux' option.
[    4.272104] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.281039] mice: PS/2 mouse device common for all mice
[    4.317060] rtc_cmos 00:05: RTC can wake from S4
[    4.317097] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    4.317133] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    4.317190] device-mapper: uevent: version 1.0.3
[    4.317282] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.317395] device-mapper: multipath: version 1.0.5 loaded
[    4.317398] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.317531] cpuidle: using governor ladder
[    4.317532] cpuidle: using governor menu
[    4.317889] TCP cubic registered
[    4.317952] NET: Registered protocol family 10
[    4.318277] lo: Disabled Privacy Extensions
[    4.318512] NET: Registered protocol family 17
[    4.318530] Bluetooth: L2CAP ver 2.11
[    4.318531] Bluetooth: L2CAP socket layer initialized
[    4.318533] Bluetooth: SCO (Voice Link) ver 0.6
[    4.318534] Bluetooth: SCO socket layer initialized
[    4.318573] Bluetooth: RFCOMM socket layer initialized
[    4.318578] Bluetooth: RFCOMM TTY layer initialized
[    4.318579] Bluetooth: RFCOMM ver 1.10
[    4.318623] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (2 cpu cores) (version 2.20.00)
[    4.318685] powernow-k8:    0 : fid 0xf (2300 MHz), vid 0xc
[    4.318687] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xd
[    4.318689] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xf
[    4.318690] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0x11
[    4.318692] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
[    4.318834] registered taskstats version 1
[    4.318983]   Magic number: 5:104:695
[    4.319028] pci 0000:00:00.0: hash matches
[    4.319087] rtc_cmos 00:05: setting system clock to 2009-04-01 18:41:34 UTC (1238611294)
[    4.319090] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.319091] EDD information not available.
[    4.319129] Freeing unused kernel memory: 536k freed
[    4.319409] Write protecting the kernel read-only data: 6712k
[    4.537025] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    4.579768] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    4.579782] ohci1394 0000:01:08.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    4.579787] ohci1394 0000:01:08.0: setting latency timer to 64
[    4.592906] FDC 0 is a post-1991 82077
[    4.632404] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fd2ff000-fd2ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.660784] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.661177] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    4.661181] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    4.661186] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.769107] usb 3-1: configuration #1 chosen from 1 choice
[    4.881650] usbcore: registered new interface driver hiddev
[    4.894403] input:   USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/input/input3
[    4.920082] generic-usb 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:02.0-1/input0
[    4.943105] input:   USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.1/input/input4
[    4.965056] generic-usb 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:02.0-1/input1
[    4.965075] usbcore: registered new interface driver usbhid
[    4.965078] usbhid: v2.6:USB HID core driver
[    5.072022] usb 3-5: new full speed USB device using ohci_hcd and address 3
[    5.184752] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 19, addr 00:30:1b:81:f6:76
[    5.184757] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    5.280106] usb 3-5: configuration #1 chosen from 1 choice
[    5.312300] PM: Starting manual resume from disk
[    5.312303] PM: Resume from partition 8:5
[    5.312304] PM: Checking hibernation image.
[    5.312457] PM: Resume from disk failed.
[    5.323592] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.323595] EXT3-fs: write access will be enabled during recovery.
[    5.900204] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000301b47a6b2]
[    7.618245] kjournald starting.  Commit interval 5 seconds
[    7.618259] EXT3-fs: sda1: orphan cleanup on readonly fs
[    7.641020] ext3_orphan_cleanup: deleting unreferenced inode 190932
[    7.641048] ext3_orphan_cleanup: deleting unreferenced inode 190931
[    7.641055] ext3_orphan_cleanup: deleting unreferenced inode 190930
[    7.641061] ext3_orphan_cleanup: deleting unreferenced inode 190929
[    7.641246] ext3_orphan_cleanup: deleting unreferenced inode 190927
[    7.641253] EXT3-fs: sda1: 5 orphan inodes deleted
[    7.641254] EXT3-fs: recovery complete.
[    7.644946] EXT3-fs: mounted filesystem with ordered data mode.
[    9.082355] udev: starting version 140
[    9.541546] lirc_dev: IR Remote Control driver registered, major 61 
[    9.627955] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.647988] parport_pc 00:09: reported by Plug and Play ACPI
[    9.648038] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.668643] 
[    9.668646] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[    9.668648] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[    9.749742] ppdev: user-space parallel port driver
[    9.857035] usb 3-5: reset full speed USB device using ohci_hcd and address 3
[   10.071033] lirc_dev: lirc_register_plugin: sample_rate: 0
[   10.077887] lirc_mceusb2[3]: Philips eHome Infrared Transceiver on usb3:3
[   10.077938] usbcore: registered new interface driver lirc_mceusb2
[   10.374941] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   10.374946] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   10.375017] HDA Intel 0000:00:07.0: setting latency timer to 64
[   10.764016] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   11.363121] lp0: using parport0 (interrupt-driven).
[   11.588974] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[   12.213465] EXT3 FS on sda1, internal journal
[   13.113671] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   13.115463] SGI XFS Quota Management subsystem
[   13.163266] XFS mounting filesystem sda6
[   13.321772] Starting XFS recovery on filesystem: sda6 (logdev: internal)
[   13.401732] Ending XFS recovery on filesystem: sda6 (logdev: internal)
[   13.954287] type=1505 audit(1238611304.133:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1906
[   13.954424] type=1505 audit(1238611304.133:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1906
[   13.954469] type=1505 audit(1238611304.133:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1906
[   13.954512] type=1505 audit(1238611304.133:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1906
[   14.080964] type=1505 audit(1238611304.257:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1914
[   14.081171] type=1505 audit(1238611304.261:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1914
[   14.120791] type=1505 audit(1238611304.297:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=1951
[   14.152887] type=1505 audit(1238611304.329:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1964
[   21.257273] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.257277] Bluetooth: BNEP filters: protocol multicast
[   21.295889] Bridge firewalling registered
[   26.821214] forcedeth 0000:00:0a.0: irq 2295 for MSI/MSI-X
[   37.456018] eth0: no IPv6 routers present
[   88.001019] Clocksource tsc unstable (delta = -168489059 ns)
[  211.151412] forcedeth 0000:00:0a.0: irq 2295 for MSI/MSI-X
[  211.252082] forcedeth 0000:00:0a.0: irq 2295 for MSI/MSI-X

```

---

### Post by grantemsley on 2009-04-03
For anyone else who happens to find this thread:

It seems to be working now.  I changed the RAM speed in the BIOS to 533MHz, although it is rated (and passes memory tests) at 667MHz, and the board supports up to 800.  Once I changed that, the problem disappeared.

Since this is just a media center and not a gaming machine, I haven't bothered to look into making it run any faster than that.

---

