---
title: "HD Access Light Constantly On"
date: 2010-12-23
forum: Hardware
---

### Post by cowboydren on 2010-12-23
I have a Maverick install on a brand-spankin'-new Acer Aspire 5252 (-V140) laptop. I ran the amd64 Ubuntu installer, and everything was fine. I allowed the Update Manager to fully upgrade all packages on my system (including the kernel), and now my HD access light is constantly on. It also seems that the disk is a little busier than normal (I can hear it pretty clearly when it's doing a read, very clearly when it's doing a write). I'm about to buy a 64GB SSD for this machine, but I don't want to spend $100 if the kernel is making the SATA controller do stupid things and fry my new SSD...

I've done very little to optimize or tune this system. Ten years ago, I was a certified Linux admin (I worked on all distros, but specialized in SuSE for customers and Debian at home), but I'm a little rusty. Hope the attached log files can help somebody help me track this down. If I need to file a bug report, I'd be happy to.

uname -a
```
Linux bec-Aspire-5252 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
```

lspci -vv
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=0 UnitCnt=12 MastHost- DefDir- DUL-
		Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 3.00
		Link Frequency 0: 1.6GHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC- LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 200MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE- OFlE- PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: 92100000-922fffff
	Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00005fff
	Memory behind bridge: 91100000-920fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us
			ClockPM- Surprise- LLActRep+ BwNot+
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #4, PowerLimit 25.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet+ LinkState+
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis- ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0100c  Data: 4149
	Capabilities: [b0] Subsystem: Acer Incorporated [ALI] Device 0489
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [110 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: 91000000-910fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #2, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us
			ClockPM- Surprise- LLActRep+ BwNot+
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #5, PowerLimit 25.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet+ LinkState+
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis- ARIFwd-
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0100c  Data: 4151
	Capabilities: [b0] Subsystem: Acer Incorporated [ALI] Device 0489
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [110 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 42
	Region 0: I/O ports at 7038 [size=8]
	Region 1: I/O ports at 704c [size=4]
	Region 2: I/O ports at 7030 [size=8]
	Region 3: I/O ports at 7048 [size=4]
	Region 4: I/O ports at 7010 [size=16]
	Region 5: Memory at 92306000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] MSI: Enable+ Count=1/8 Maskable- 64bit+
		Address: 00000000fee0100c  Data: 4169
	Capabilities: [70] SATA HBA v1.0 InCfgSpace
	Capabilities: [a4] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at 92305000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at 92306500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at 92304000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at 92306400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at 92300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=64
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b+
		Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Revision ID: 3.00
		Link Frequency: 1.6GHz
		Link Error: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE-

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at 80000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at 6000 [size=256]
	Region 2: Memory at 92200000 (32-bit, non-prefetchable) [size=64K]
	Region 5: Memory at 92100000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
	Subsystem: Acer Incorporated [ALI] Device 0489
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at 92210000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 036d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 43
	Region 0: Memory at 91100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [60] Vendor Specific Information: Len=6c <?>
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0100c  Data: 4179
	Capabilities: [cc] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 4096 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <32us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [13c v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 1c-75-08-ff-fe-45-bc-2a
	Capabilities: [16c v1] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

08:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a32:2309
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at 91000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [140 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 00-15-17-ff-ff-24-14-12
	Capabilities: [170 v1] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k
```

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=2a988366-b0c1-4f95-ad06-492fb8c05a3d ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006e444000 (usable)
[    0.000000]  BIOS-e820: 000000006e444000 - 000000006e644000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006e644000 - 000000006fd3f000 (usable)
[    0.000000]  BIOS-e820: 000000006fd3f000 - 000000006fdbf000 (reserved)
[    0.000000]  BIOS-e820: 000000006fdbf000 - 000000006febf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006febf000 - 000000006fef7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fef7000 - 000000006ff00000 (usable)
[    0.000000]  BIOS-e820: 000000006ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f7000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x6ff00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFFC0000000 write-back
[    0.000000]   1 base 000040000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 000060000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000FFE00000 mask FFFFFFE00000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006e444000 (usable)
[    0.000000]  modified: 000000006e444000 - 000000006e644000 (ACPI NVS)
[    0.000000]  modified: 000000006e644000 - 000000006fd3f000 (usable)
[    0.000000]  modified: 000000006fd3f000 - 000000006fdbf000 (reserved)
[    0.000000]  modified: 000000006fdbf000 - 000000006febf000 (ACPI NVS)
[    0.000000]  modified: 000000006febf000 - 000000006fef7000 (ACPI data)
[    0.000000]  modified: 000000006fef7000 - 000000006ff00000 (usable)
[    0.000000]  modified: 000000006ff00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f7000000 - 00000000f8000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-000000006ff00000
[    0.000000]  0000000000 - 0040000000 page 1G
[    0.000000]  0040000000 - 006fe00000 page 2M
[    0.000000]  006fe00000 - 006ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 6ff00000 @ 16000-19000
[    0.000000] RAMDISK: 37571000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 000000006fef6120 0005C (v01 ACRSYS ACRPRDCT 00000003      01000013)
[    0.000000] ACPI: FACP 000000006fef5000 000F4 (v04 ACRSYS ACRPRDCT 00000003 1025 01000013)
[    0.000000] ACPI: DSDT 000000006fee6000 0B23D (v01 ACRSYS ACRPRDCT F0000000 1025 01000013)
[    0.000000] ACPI: FACS 000000006fe99000 00040
[    0.000000] ACPI: HPET 000000006fef4000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 000000006fef3000 00084 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 000000006fef2000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 000000006fee5000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 000000006fee4000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT 000000006fee3000 001B7 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000006ff00000
[    0.000000] Initmem setup node 0 0000000000000000-000000006ff00000
[    0.000000]   NODE_DATA [0000000001d18200 - 0000000001d1d1ff]
[    0.000000]  [ffffea0000000000-ffffea00019fffff] PMD -> [ffff880002600000-ffff880003ffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0006e444
[    0.000000]     0: 0x0006e644 -> 0x0006fd3f
[    0.000000]     0: 0x0006fef7 -> 0x0006ff00
[    0.000000] On node 0 totalpages: 457431
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3927 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6213 pages used for memmap
[    0.000000]   DMA32 zone: 447235 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [18000 - 187ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000006e444000 - 000000006e644000
[    0.000000] PM: Registered nosave memory: 000000006fd3f000 - 000000006fdbf000
[    0.000000] PM: Registered nosave memory: 000000006fdbf000 - 000000006febf000
[    0.000000] PM: Registered nosave memory: 000000006febf000 - 000000006fef7000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:77000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 451162
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=2a988366-b0c1-4f95-ad06-492fb8c05a3d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ fdfc000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Subtract (53 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037571000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [000009f800 - 0000100000]   BIOS reserved
[    0.000000]   #4 [0001d18000 - 0001d181f7]             BRK
[    0.000000]   #5 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #6 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #7 [0000016000 - 0000018000]         PGTABLE
[    0.000000]   #8 [0001d18200 - 0001d1d200]       NODE_DATA
[    0.000000]   #9 [0001d1d200 - 0001d1e200]         BOOTMEM
[    0.000000]   #10 [0001d17140 - 0001d17290]         BOOTMEM
[    0.000000]   #11 [000251f000 - 0002520000]         BOOTMEM
[    0.000000]   #12 [0002520000 - 0002521000]         BOOTMEM
[    0.000000]   #13 [0002600000 - 0004000000]        MEMMAP 0
[    0.000000]   #14 [0001d172c0 - 0001d17440]         BOOTMEM
[    0.000000]   #15 [0001d1e200 - 0001d2a200]         BOOTMEM
[    0.000000]   #16 [0001d2b000 - 0001d2c000]         BOOTMEM
[    0.000000]   #17 [0001d17440 - 0001d17481]         BOOTMEM
[    0.000000]   #18 [0001d174c0 - 0001d17503]         BOOTMEM
[    0.000000]   #19 [0001d17540 - 0001d178f8]         BOOTMEM
[    0.000000]   #20 [0001d17900 - 0001d17968]         BOOTMEM
[    0.000000]   #21 [0001d17980 - 0001d179e8]         BOOTMEM
[    0.000000]   #22 [0001d17a00 - 0001d17a68]         BOOTMEM
[    0.000000]   #23 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #24 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #25 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #26 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #27 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #28 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #29 [0001d17d80 - 0001d17de8]         BOOTMEM
[    0.000000]   #30 [0001d17e00 - 0001d17e68]         BOOTMEM
[    0.000000]   #31 [0001d17e80 - 0001d17ee8]         BOOTMEM
[    0.000000]   #32 [0001d17f00 - 0001d17f68]         BOOTMEM
[    0.000000]   #33 [0001d17f80 - 0001d17fe8]         BOOTMEM
[    0.000000]   #34 [0001d2a200 - 0001d2a268]         BOOTMEM
[    0.000000]   #35 [0001d2a280 - 0001d2a2e8]         BOOTMEM
[    0.000000]   #36 [0001d2a300 - 0001d2a320]         BOOTMEM
[    0.000000]   #37 [0001d2a340 - 0001d2a360]         BOOTMEM
[    0.000000]   #38 [0001d2a380 - 0001d2a3a0]         BOOTMEM
[    0.000000]   #39 [0001d2a3c0 - 0001d2a42a]         BOOTMEM
[    0.000000]   #40 [0001d2a440 - 0001d2a4aa]         BOOTMEM
[    0.000000]   #41 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #42 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #43 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #44 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #45 [0001d2a4c0 - 0001d2a4c8]         BOOTMEM
[    0.000000]   #46 [0001d2a500 - 0001d2a508]         BOOTMEM
[    0.000000]   #47 [0001d2a540 - 0001d2a550]         BOOTMEM
[    0.000000]   #48 [0001d2a580 - 0001d2a5a0]         BOOTMEM
[    0.000000]   #49 [0001d2a5c0 - 0001d2a6f0]         BOOTMEM
[    0.000000]   #50 [0001d2a700 - 0001d2a750]         BOOTMEM
[    0.000000]   #51 [0001d2a780 - 0001d2a7d0]         BOOTMEM
[    0.000000]   #52 [0001d2c000 - 0001d34000]         BOOTMEM
[    0.000000] Memory: 1778312k/1833984k available (5711k kernel code, 4260k absent, 51412k reserved, 5379k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:712
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 18350080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2294.121 MHz processor.
[    0.020009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4588.23 BogoMIPS (lpj=22941180)
[    0.020014] pid_max: default: 32768 minimum: 301
[    0.020037] Security Framework initialized
[    0.020055] AppArmor: AppArmor initialized
[    0.020056] Yama: becoming mindful.
[    0.020304] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.021668] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.022111] Mount-cache hash table entries: 256
[    0.022241] Initializing cgroup subsys ns
[    0.022245] Initializing cgroup subsys cpuacct
[    0.022249] Initializing cgroup subsys memory
[    0.022258] Initializing cgroup subsys devices
[    0.022260] Initializing cgroup subsys freezer
[    0.022262] Initializing cgroup subsys net_cls
[    0.022286] tseg: 006ff00000
[    0.022288] mce: CPU supports 6 MCE banks
[    0.022299] using C1E aware idle routine
[    0.022301] Performance Events: AMD PMU driver.
[    0.022306] ... version:                0
[    0.022308] ... bit width:              48
[    0.022309] ... generic registers:      4
[    0.022311] ... value mask:             0000ffffffffffff
[    0.022312] ... max period:             00007fffffffffff
[    0.022314] ... fixed-purpose events:   0
[    0.022315] ... event mask:             000000000000000f
[    0.022366] SMP alternatives: switching to UP code
[    0.033734] ACPI: Core revision 20100428
[    0.050008] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.050013] ftrace: allocating 22678 entries in 89 pages
[    0.056509] Setting APIC routing to flat
[    0.056813] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.159235] CPU0: AMD V140 Processor stepping 03
[    0.160000] Brought up 1 CPUs
[    0.160000] Total of 1 processors activated (4588.23 BogoMIPS).
[    0.160000] devtmpfs: initialized
[    0.160000] regulator: core version 0.5
[    0.160000] Time:  5:28:06  Date: 12/23/10
[    0.160000] NET: Registered protocol family 16
[    0.160000] node 0 link 0: io port [0, ffffff]
[    0.160000] TOM: 0000000080000000 aka 2048M
[    0.160000] Fam 10h mmconf [f7000000, f7ffffff]
[    0.160000] node 0 link 0: mmio [a0000, bffff]
[    0.160000] node 0 link 0: mmio [80000000, 8fffffff]
[    0.160000] node 0 link 0: mmio [90000000, 920fffff]
[    0.160000] node 0 link 0: mmio [92100000, 922fffff]
[    0.160000] node 0 link 0: mmio [92300000, f6ffffff]
[    0.160000] node 0 link 0: mmio [f7000000, f7ffffff] ==> none
[    0.160000] node 0 link 0: mmio [f8000000, ffdfffff]
[    0.160000] bus: [00, 1f] on node 0 link 0
[    0.160000] bus: 00 index 0 [io  0x0000-0xffff]
[    0.160000] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.160000] bus: 00 index 2 [mem 0x80000000-0xf6ffffff]
[    0.160000] bus: 00 index 3 [mem 0xf8000000-0xfcffffffff]
[    0.160000] ACPI: bus type pci registered
[    0.160000] PCI: MMCONFIG for domain 0000 [bus 00-0f] at [mem 0xf7000000-0xf7ffffff] (base 0xf7000000)
[    0.160000] PCI: MMCONFIG at [mem 0xf7000000-0xf7ffffff] reserved in E820
[    0.160000] PCI: Using configuration type 1 for base access
[    0.160000] bio: create slab <bio-0> at 0
[    0.160000] ACPI: EC: Look up EC in DSDT
[    0.160000] ACPI: Executed 1 blocks of module-level executable AML code
[    0.162525] ACPI: BIOS _OSI(Linux) query ignored
[    0.162736] System has AMD C1E enabled
[    0.162746] Switch to broadcast mode on CPU0
[    0.182715] ACPI: Interpreter enabled
[    0.182719] ACPI: (supports S0 S1 S3 S4 S5)
[    0.182746] ACPI: Using IOAPIC for interrupt routing
[    0.330428] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.330707] ACPI: No dock devices found.
[    0.330710] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.331681] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.333502] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.333505] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.333507] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.333509] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.333511] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.333513] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.333516] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.333518] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.333520] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.333522] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.333524] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.333526] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.333528] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.333530] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.333532] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.333535] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf6ffffff]
[    0.333537] pci_root PNP0A08:00: host bridge window [mem 0xf8000000-0xfed3ffff]
[    0.333539] pci_root PNP0A08:00: host bridge window [mem 0xfed45000-0xffffffff]
[    0.334029] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.334032] pci 0000:00:04.0: PME# disabled
[    0.334065] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.334068] pci 0000:00:05.0: PME# disabled
[    0.334120] pci 0000:00:11.0: reg 10: [io  0x7038-0x703f]
[    0.334126] pci 0000:00:11.0: reg 14: [io  0x704c-0x704f]
[    0.334132] pci 0000:00:11.0: reg 18: [io  0x7030-0x7037]
[    0.334138] pci 0000:00:11.0: reg 1c: [io  0x7048-0x704b]
[    0.334144] pci 0000:00:11.0: reg 20: [io  0x7010-0x701f]
[    0.334150] pci 0000:00:11.0: reg 24: [mem 0x92306000-0x923063ff]
[    0.334206] pci 0000:00:12.0: reg 10: [mem 0x92305000-0x92305fff]
[    0.334265] pci 0000:00:12.2: reg 10: [mem 0x92306500-0x923065ff]
[    0.334312] pci 0000:00:12.2: supports D1 D2
[    0.334314] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.334317] pci 0000:00:12.2: PME# disabled
[    0.334344] pci 0000:00:13.0: reg 10: [mem 0x92304000-0x92304fff]
[    0.334403] pci 0000:00:13.2: reg 10: [mem 0x92306400-0x923064ff]
[    0.334449] pci 0000:00:13.2: supports D1 D2
[    0.334451] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.334455] pci 0000:00:13.2: PME# disabled
[    0.334539] pci 0000:00:14.2: reg 10: [mem 0x92300000-0x92303fff 64bit]
[    0.334577] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.334580] pci 0000:00:14.2: PME# disabled
[    0.334759] pci 0000:01:05.0: reg 10: [mem 0x80000000-0x8fffffff pref]
[    0.334762] pci 0000:01:05.0: reg 14: [io  0x6000-0x60ff]
[    0.334766] pci 0000:01:05.0: reg 18: [mem 0x92200000-0x9220ffff]
[    0.334772] pci 0000:01:05.0: reg 24: [mem 0x92100000-0x921fffff]
[    0.334784] pci 0000:01:05.0: supports D1 D2
[    0.334798] pci 0000:01:05.1: reg 10: [mem 0x92210000-0x92213fff]
[    0.334817] pci 0000:01:05.1: supports D1 D2
[    0.334855] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.334859] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    0.334862] pci 0000:00:01.0:   bridge window [mem 0x92100000-0x922fffff]
[    0.334865] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.334947] pci 0000:02:00.0: reg 10: [mem 0x91100000-0x9110ffff 64bit]
[    0.335001] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.335005] pci 0000:02:00.0: PME# disabled
[    0.350062] pci 0000:00:04.0: PCI bridge to [bus 02-07]
[    0.350068] pci 0000:00:04.0:   bridge window [io  0x2000-0x5fff]
[    0.350072] pci 0000:00:04.0:   bridge window [mem 0x91100000-0x920fffff]
[    0.350076] pci 0000:00:04.0:   bridge window [mem 0x90000000-0x90ffffff 64bit pref]
[    0.350133] pci 0000:08:00.0: reg 10: [mem 0x91000000-0x9100ffff 64bit]
[    0.350181] pci 0000:08:00.0: supports D1
[    0.350183] pci 0000:08:00.0: PME# supported from D0 D1 D3hot
[    0.350187] pci 0000:08:00.0: PME# disabled
[    0.370030] pci 0000:00:05.0: PCI bridge to [bus 08-08]
[    0.370035] pci 0000:00:05.0:   bridge window [io  0xfffffffffffff000-0x0000] (disabled)
[    0.370039] pci 0000:00:05.0:   bridge window [mem 0x91000000-0x910fffff]
[    0.370043] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.370109] pci 0000:00:14.4: PCI bridge to [bus 09-09] (subtractive decode)
[    0.370113] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.370117] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.370121] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.370124] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.370126] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.370128] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.370130] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.370132] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.370134] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.370136] pci 0000:00:14.4:   bridge window [mem 0x000cc000-0x000cffff] (subtractive decode)
[    0.370138] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.370140] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.370142] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.370144] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.370146] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.370148] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.370150] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.370152] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.370154] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xf6ffffff] (subtractive decode)
[    0.370156] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xfed3ffff] (subtractive decode)
[    0.370159] pci 0000:00:14.4:   bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
[    0.370184] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.370413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.370499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.370587] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.370738] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.381097] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.381306] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.381511] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.381713] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.382287] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.382431] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.382574] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.382716] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.382769] HEST: Table is not found!
[    0.382840] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.382842] vgaarb: loaded
[    0.382956] SCSI subsystem initialized
[    0.383013] libata version 3.00 loaded.
[    0.383053] usbcore: registered new interface driver usbfs
[    0.383063] usbcore: registered new interface driver hub
[    0.383081] usbcore: registered new device driver usb
[    0.383448] ACPI: WMI: Mapper loaded
[    0.383450] PCI: Using ACPI for IRQ routing
[    0.383452] PCI: pci_cache_line_size set to 64 bytes
[    0.383588] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.383590] reserve RAM buffer: 000000006e444000 - 000000006fffffff 
[    0.383593] reserve RAM buffer: 000000006fd3f000 - 000000006fffffff 
[    0.383595] reserve RAM buffer: 000000006ff00000 - 000000006fffffff 
[    0.383673] NetLabel: Initializing
[    0.383674] NetLabel:  domain hash size = 128
[    0.383675] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.383688] NetLabel:  unlabeled traffic allowed by default
[    0.383725] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.383728] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.385753] Switching to clocksource tsc
[    0.390000] AppArmor: AppArmor Filesystem Enabled
[    0.390000] pnp: PnP ACPI init
[    0.390000] ACPI: bus type pnp registered
[    0.454344] pnp: PnP ACPI: found 10 devices
[    0.454348] ACPI: ACPI bus type pnp unregistered
[    0.454367] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.454370] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.454372] system 00:01: [mem 0xf7000000-0xf7ffffff] has been reserved
[    0.454380] system 00:08: [io  0x0400-0x04cf] has been reserved
[    0.454383] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.454385] system 00:08: [io  0x04d6] has been reserved
[    0.454387] system 00:08: [io  0x0550] has been reserved
[    0.454389] system 00:08: [io  0x0680-0x06ff] has been reserved
[    0.454391] system 00:08: [io  0x077a] has been reserved
[    0.454392] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.454395] system 00:08: [io  0x0c14] has been reserved
[    0.454396] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.454398] system 00:08: [io  0x0c6c] has been reserved
[    0.454400] system 00:08: [io  0x0c6f] has been reserved
[    0.454402] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
[    0.454405] system 00:08: [io  0xfd60-0xfd63] has been reserved
[    0.454410] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.454412] system 00:09: [mem 0xffe00000-0xffffffff] has been reserved
[    0.460237] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.460240] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    0.460244] pci 0000:00:01.0:   bridge window [mem 0x92100000-0x922fffff]
[    0.460247] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.460251] pci 0000:00:04.0: PCI bridge to [bus 02-07]
[    0.460253] pci 0000:00:04.0:   bridge window [io  0x2000-0x5fff]
[    0.460256] pci 0000:00:04.0:   bridge window [mem 0x91100000-0x920fffff]
[    0.460259] pci 0000:00:04.0:   bridge window [mem 0x90000000-0x90ffffff 64bit pref]
[    0.460263] pci 0000:00:05.0: PCI bridge to [bus 08-08]
[    0.460264] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.460267] pci 0000:00:05.0:   bridge window [mem 0x91000000-0x910fffff]
[    0.460270] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.460273] pci 0000:00:14.4: PCI bridge to [bus 09-09]
[    0.460274] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.460279] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.460282] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.460294] pci 0000:00:01.0: setting latency timer to 64
[    0.460301]   alloc irq_desc for 16 on node 0
[    0.460303]   alloc kstat_irqs on node 0
[    0.460310] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.460313] pci 0000:00:04.0: setting latency timer to 64
[    0.460318]   alloc irq_desc for 17 on node 0
[    0.460319]   alloc kstat_irqs on node 0
[    0.460323] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.460325] pci 0000:00:05.0: setting latency timer to 64
[    0.460332] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.460334] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.460337] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.460339] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.460341] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.460343] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.460345] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.460347] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.460349] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.460351] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.460353] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.460355] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.460357] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.460359] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.460362] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.460364] pci_bus 0000:00: resource 19 [mem 0x80000000-0xf6ffffff]
[    0.460366] pci_bus 0000:00: resource 20 [mem 0xf8000000-0xfed3ffff]
[    0.460368] pci_bus 0000:00: resource 21 [mem 0xfed45000-0xffffffff]
[    0.460370] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
[    0.460372] pci_bus 0000:01: resource 1 [mem 0x92100000-0x922fffff]
[    0.460375] pci_bus 0000:01: resource 2 [mem 0x80000000-0x8fffffff 64bit pref]
[    0.460377] pci_bus 0000:02: resource 0 [io  0x2000-0x5fff]
[    0.460379] pci_bus 0000:02: resource 1 [mem 0x91100000-0x920fffff]
[    0.460382] pci_bus 0000:02: resource 2 [mem 0x90000000-0x90ffffff 64bit pref]
[    0.460384] pci_bus 0000:08: resource 1 [mem 0x91000000-0x910fffff]
[    0.460386] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
[    0.460388] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
[    0.460390] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
[    0.460392] pci_bus 0000:09: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.460395] pci_bus 0000:09: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.460397] pci_bus 0000:09: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.460399] pci_bus 0000:09: resource 10 [mem 0x000cc000-0x000cffff]
[    0.460401] pci_bus 0000:09: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.460403] pci_bus 0000:09: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.460405] pci_bus 0000:09: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.460407] pci_bus 0000:09: resource 14 [mem 0x000dc000-0x000dffff]
[    0.460409] pci_bus 0000:09: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.460411] pci_bus 0000:09: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.460413] pci_bus 0000:09: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.460415] pci_bus 0000:09: resource 18 [mem 0x000ec000-0x000effff]
[    0.460417] pci_bus 0000:09: resource 19 [mem 0x80000000-0xf6ffffff]
[    0.460420] pci_bus 0000:09: resource 20 [mem 0xf8000000-0xfed3ffff]
[    0.460422] pci_bus 0000:09: resource 21 [mem 0xfed45000-0xffffffff]
[    0.460455] NET: Registered protocol family 2
[    0.460553] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.461219] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.463082] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.463531] TCP: Hash tables configured (established 262144 bind 65536)
[    0.463534] TCP reno registered
[    0.463545] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.463568] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.463676] NET: Registered protocol family 1
[    0.463694] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.584348] pci 0000:01:05.0: Boot video device
[    0.584389] PCI: CLS 64 bytes, default 64
[    0.584509] Trying to unpack rootfs image as initramfs...
[    0.634621] Simple Boot Flag at 0x44 set to 0x1
[    0.634748] Scanning for low memory corruption every 60 seconds
[    0.634860] audit: initializing netlink socket (disabled)
[    0.634871] type=2000 audit(1293082085.630:1): initialized
[    0.654730] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.664559] VFS: Disk quotas dquot_6.5.2
[    0.664644] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.665170] fuse init (API version 7.14)
[    0.665238] msgmni has been set to 3473
[    0.665865] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.665868] io scheduler noop registered
[    0.665871] io scheduler deadline registered
[    0.665901] io scheduler cfq registered (default)
[    0.674599] pcieport 0000:00:04.0: setting latency timer to 64
[    0.674622]   alloc irq_desc for 40 on node 0
[    0.674624]   alloc kstat_irqs on node 0
[    0.674632] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    0.674712] pcieport 0000:00:05.0: setting latency timer to 64
[    0.674729]   alloc irq_desc for 41 on node 0
[    0.674731]   alloc kstat_irqs on node 0
[    0.674735] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    0.674804] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.674820] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.684645] ACPI: AC Adapter [ACAD] (on-line)
[    0.684707] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.684713] ACPI: Power Button [PWRB]
[    0.684743] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.684746] ACPI: Sleep Button [SLPB]
[    0.684796] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.684888] ACPI: Lid Switch [LID]
[    0.684923] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.684926] ACPI: Power Button [PWRF]
[    0.685227] ACPI: acpi_idle registered with cpuidle
[    0.685287] ACPI: processor limited to max C-state 1
[    0.764820] ACPI: Invalid active0 threshold
[    0.774532] thermal LNXTHERM:01: registered as thermal_zone0
[    0.774543] ACPI: Thermal Zone [THRM] (53 C)
[    0.774629] ERST: Table is not found!
[    0.774755] Linux agpgart interface v0.103
[    0.774776] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.775831] brd: module loaded
[    0.776193] loop: module loaded
[    0.776600] Fixed MDIO Bus: probed
[    0.776625] PPP generic driver version 2.4.2
[    0.776653] tun: Universal TUN/TAP device driver, 1.6
[    0.776655] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.776725] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.784454] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.784480] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    0.784484] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.784551] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.784591] ehci_hcd 0000:00:12.2: debug port 1
[    0.784617] ehci_hcd 0000:00:12.2: irq 17, io mem 0x92306500
[    0.804539] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.804696] hub 1-0:1.0: USB hub found
[    0.804701] hub 1-0:1.0: 5 ports detected
[    0.814581] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.814606] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    0.814610] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.814697] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.814740] ehci_hcd 0000:00:13.2: debug port 1
[    0.814755] ehci_hcd 0000:00:13.2: irq 17, io mem 0x92306400
[    0.834519] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.834665] hub 2-0:1.0: USB hub found
[    0.834669] hub 2-0:1.0: 5 ports detected
[    0.834762] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.835378] Freeing initrd memory: 10748k freed
[    0.839947]   alloc irq_desc for 18 on node 0
[    0.839949]   alloc kstat_irqs on node 0
[    0.839960] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.839984] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    0.839988] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.840071] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.840111] ohci_hcd 0000:00:12.0: irq 18, io mem 0x92305000
[    0.898535] hub 3-0:1.0: USB hub found
[    0.898547] hub 3-0:1.0: 5 ports detected
[    0.898656] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.898675] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    0.898678] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.898711] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    0.898728] ohci_hcd 0000:00:13.0: irq 18, io mem 0x92304000
[    0.958553] hub 4-0:1.0: USB hub found
[    0.958596] hub 4-0:1.0: 5 ports detected
[    0.958669] uhci_hcd: USB Universal Host Controller Interface driver
[    0.958764] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    0.977084] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.977089] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.977166] mice: PS/2 mouse device common for all mice
[    0.977601] rtc_cmos 00:04: RTC can wake from S4
[    0.977632] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.977654] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    0.977730] device-mapper: uevent: version 1.0.3
[    0.977794] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.977829] device-mapper: multipath: version 1.1.1 loaded
[    0.977831] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.977924] cpuidle: using governor ladder
[    0.977925] cpuidle: using governor menu
[    0.978141] TCP cubic registered
[    0.978244] NET: Registered protocol family 10
[    0.978554] lo: Disabled Privacy Extensions
[    0.978713] NET: Registered protocol family 17
[    0.978740] powernow-k8: Found 1 AMD V140 Processor (1 cpu cores) (version 2.20.00)
[    0.978790] powernow-k8:    0 : pstate 0 (2300 MHz)
[    0.978792] powernow-k8:    1 : pstate 1 (1700 MHz)
[    0.978793] powernow-k8:    2 : pstate 2 (800 MHz)
[    0.978906] PM: Resume from disk failed.
[    0.978916] registered taskstats version 1
[    0.979180]   Magic number: 6:220:467
[    0.979301] rtc_cmos 00:04: setting system clock to 2010-12-23 05:28:07 UTC (1293082087)
[    0.979303] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.979305] EDD information not available.
[    0.979380] Freeing unused kernel memory: 908k freed
[    0.979694] Write protecting the kernel read-only data: 10240k
[    0.979830] Freeing unused kernel memory: 412k freed
[    0.980100] Freeing unused kernel memory: 1644k freed
[    0.995454] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.998507] udev[92]: starting version 163
[    1.180086] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.227083] tg3.c:v3.110 (April 9, 2010)
[    1.227133] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.227143] tg3 0000:02:00.0: setting latency timer to 64
[    1.252322] tg3 mdio bus: probed
[    1.252472] ahci 0000:00:11.0: version 3.0
[    1.252488]   alloc irq_desc for 19 on node 0
[    1.252490]   alloc kstat_irqs on node 0
[    1.252498] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.252536]   alloc irq_desc for 42 on node 0
[    1.252537]   alloc kstat_irqs on node 0
[    1.252546] ahci 0000:00:11.0: irq 42 for MSI/MSI-X
[    1.252607] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.252611] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.252784] scsi0 : ahci
[    1.252964] scsi1 : ahci
[    1.253086] ata1: SATA max UDMA/133 abar m1024@0x92306000 port 0x92306100 irq 42
[    1.253089] ata2: SATA max UDMA/133 abar m1024@0x92306000 port 0x92306180 irq 42
[    1.274091] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address 1c:75:08:45:bc:2a
[    1.274095] tg3 0000:02:00.0: eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=200:01)
[    1.274098] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.274100] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.480103] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    1.570552] ACPI: Battery Slot [BAT1] (battery present)
[    1.800058] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.800086] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.801873] ata1.00: ATA-8: ST9250315AS, 0001SDM1, max UDMA/133
[    1.801877] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.804101] ata1.00: configured for UDMA/133
[    1.814865] ata2.00: ATAPI: PIONEER DVD-RW DVRTD10RS, 1.00, max UDMA/100
[    1.820142] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    1.820271] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.820456] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.820489] sd 0:0:0:0: [sda] Write Protect is off
[    1.820491] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.820505] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.820597]  sda:
[    1.827507] ata2.00: configured for UDMA/100
[    1.839828]  sda1 sda2 sda3 sda4 <
[    1.843493] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW DVRTD10RS 1.00 PQ: 0 ANSI: 5
[    1.848212] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.848216] Uniform CD-ROM driver Revision: 3.20
[    1.848328] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.848383] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.861217]  sda5 sda6 >
[    1.885456] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.905660] Initializing USB Mass Storage driver...
[    1.905754] scsi2 : usb-storage 2-2:1.0
[    1.905856] usbcore: registered new interface driver usb-storage
[    1.905858] USB Mass Storage support registered.
[    2.220130] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    2.428729] usbcore: registered new interface driver hiddev
[    2.432752] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input5
[    2.432899] generic-usb 0003:046D:C51B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-1/input0
[    2.438826] generic-usb 0003:046D:C51B.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-1/input1
[    2.438924] usbcore: registered new interface driver usbhid
[    2.438926] usbhid: USB HID core driver
[    2.697842] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.903052] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.903394] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.909542] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   14.607308] Adding 4140028k swap on /dev/sda6.  Priority:-1 extents:1 across:4140028k 
[   14.607754] udev[411]: starting version 163
[   14.661299] lp: driver loaded but no devices found
[   14.910218] acpi device:01: registered as cooling_device1
[   14.910311] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6
[   14.910363] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.970505] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.178370] EDAC MC: Ver: 2.1.0 Dec  2 2010
[   15.244486] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   15.292619] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   15.292623] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   15.319239] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.347104] EDAC amd64_edac:  Ver: 3.3.0 Dec  2 2010
[   15.361973] type=1400 audit(1293103701.878:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=772 comm="apparmor_parser"
[   15.362228] type=1400 audit(1293103701.878:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=772 comm="apparmor_parser"
[   15.362368] type=1400 audit(1293103701.878:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=772 comm="apparmor_parser"
[   15.369731] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   15.369737] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   15.369738]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   15.369740]  (Note that use of the override may cause unknown side effects.)
[   15.369754] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   15.388472] Linux video capture interface: v2.00
[   15.423255] cfg80211: Calling CRDA to update world regulatory domain
[   15.423485] uvcvideo: Found UVC 1.00 device 1.3M WebCam (064e:a219)
[   15.434409] input: 1.3M WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input7
[   15.434727] usbcore: registered new interface driver uvcvideo
[   15.434730] USB Video Class driver (v0.1.0)
[   15.451385] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.451390] Disabling lock debugging due to kernel taint
[   15.494071] cfg80211: World regulatory domain updated:
[   15.494076]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.494079]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.494081]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.494083]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.494085]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.494087]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.636654] [fglrx] Maximum main memory to use for locked dma buffers: 1635 MBytes.
[   15.636688] [fglrx]   vendor: 1002 device: 9712 count: 1
[   15.636914] [fglrx] ioport: bar 1, base 0x6000, size: 0x100
[   15.636930] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.636934] pci 0000:01:05.0: setting latency timer to 64
[   15.637161] [fglrx] Kernel PAT support is enabled
[   15.637182] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   15.640621] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.640631] ath9k 0000:08:00.0: setting latency timer to 64
[   15.811431] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.811478] HDA Intel 0000:00:14.2: setting latency timer to 64
[   15.873356]   alloc irq_desc for 43 on node 0
[   15.873359]   alloc kstat_irqs on node 0
[   15.873374] tg3 0000:02:00.0: irq 43 for MSI/MSI-X
[   15.897125] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.914139] type=1400 audit(1293103702.428:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=959 comm="apparmor_parser"
[   15.918324] type=1400 audit(1293103702.428:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=962 comm="apparmor_parser"
[   15.918582] type=1400 audit(1293103702.428:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=962 comm="apparmor_parser"
[   15.918727] type=1400 audit(1293103702.428:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=962 comm="apparmor_parser"
[   15.937935] hda_codec: ALC272X: BIOS auto-probing.
[   15.944225] type=1400 audit(1293103702.458:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=964 comm="apparmor_parser"
[   15.948254] type=1400 audit(1293103702.458:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=964 comm="apparmor_parser"
[   15.956060] type=1400 audit(1293103702.468:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=964 comm="apparmor_parser"
[   15.958129] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.958209] HDA Intel 0000:01:05.1: setting latency timer to 64
[   15.965378] ath: EEPROM regdomain: 0x65
[   15.965381] ath: EEPROM indicates we should expect a direct regpair map
[   15.965385] ath: Country alpha2 being used: 00
[   15.965387] ath: Regpair used: 0x65
[   16.004956] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.005438] Registered led device: ath9k-phy0::radio
[   16.005451] Registered led device: ath9k-phy0::assoc
[   16.005464] Registered led device: ath9k-phy0::tx
[   16.005476] Registered led device: ath9k-phy0::rx
[   16.005482] phy0: Atheros AR9287 Rev:2 mem=0xffffc90001b20000, irq=17
[   16.124407] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.271158] tg3 0000:02:00.0: eth0: Link is down
[   16.453177] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000/0xa0000
[   16.527596] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   16.774599] ppdev: user-space parallel port driver
[   17.200363] [fglrx] ATIF platform detected with notification ID: 0x81
[   17.378390] [fglrx] GART Table is not in FRAME_BUFFER range 
[   17.378536] [fglrx] Could not enable MSI; System prevented initialization
[   17.379018] [fglrx] Firegl kernel thread PID: 1284
[   17.379289] [fglrx] IRQ 18 Enabled
[   18.311325] wlan0: authenticate with 68:7f:74:bf:a2:68 (try 1)
[   18.313813] wlan0: authenticated
[   18.313836] wlan0: associate with 68:7f:74:bf:a2:68 (try 1)
[   18.318004] wlan0: RX AssocResp from 68:7f:74:bf:a2:68 (capab=0x431 status=0 aid=1)
[   18.318009] wlan0: associated
[   18.328151] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.534031] Intel AES-NI instructions are not detected.
[   18.536014] padlock: VIA PadLock not detected.
[   18.739613] [fglrx] Gart USWC size:548 M.
[   18.739617] [fglrx] Gart cacheable size:214 M.
[   18.739622] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   18.739624] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   18.911520] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   22.331005] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   23.426374] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   28.670067] wlan0: no IPv6 routers present
[   51.410072] lo: Disabled Privacy Extensions
[ 1556.935899] lo: Disabled Privacy Extensions
[ 1735.120300] lo: Disabled Privacy Extensions
[ 2126.903714] Adding 4140028k swap on /dev/sda6.  Priority:-1 extents:1 across:4140028k 
[ 2772.538915] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[ 2774.697199] tg3 0000:02:00.0: PME# enabled
[ 2774.697216] pcieport 0000:00:04.0: wake-up capability enabled by ACPI
[ 2774.736792] wlan0: deauthenticating from 68:7f:74:bf:a2:68 by local choice (reason=3)
[ 2774.777739] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2774.777745] cfg80211: Restoring regulatory settings
[ 2774.777748] cfg80211: Calling CRDA to update world regulatory domain
[ 2774.954627] cfg80211: World regulatory domain updated:
[ 2774.954636]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2774.954644]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2774.954651]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2774.954658]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2774.954663]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2774.954669]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2776.090393] PM: Syncing filesystems ... done.
[ 2776.094771] PM: Preparing system for mem sleep
[ 2776.094783] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 2776.110140] Freezing remaining freezable tasks ... (elapsed 0.02 seconds) done.
[ 2776.130170] PM: Entering mem sleep
[ 2776.130436] Suspending console(s) (use no_console_suspend to debug)
[ 2776.130908] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2776.145299] sd 0:0:0:0: [sda] Stopping disk
[ 2776.211037] ath9k 0000:08:00.0: PCI INT A disabled
[ 2776.211377] [fglrx] IRQ 18 Disabled
[ 2776.211401] [fglrx] Preparing suspend fglrx in kernel.
[ 2776.242326] ehci_hcd 0000:00:13.2: PCI INT B disabled
[ 2776.242359] ohci_hcd 0000:00:13.0: PCI INT A disabled
[ 2776.242396] ehci_hcd 0000:00:12.2: PCI INT B disabled
[ 2776.242426] ohci_hcd 0000:00:12.0: PCI INT A disabled
[ 2776.242861] [fglrx] Suspending fglrx in kernel completed.
[ 2776.242865] [fglrx] Power down the ASIC .
[ 2776.242926] fglrx_pci 0000:01:05.0: PCI INT A disabled
[ 2776.320137] HDA Intel 0000:01:05.1: PCI INT B disabled
[ 2776.320152] ACPI handle has no context!
[ 2776.340113] PM: suspend of drv:HDA Intel dev:0000:01:05.1 complete after 128.871 msecs
[ 2776.351024] HDA Intel 0000:00:14.2: PCI INT A disabled
[ 2776.370116] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 128.510 msecs
[ 2776.518492] PM: suspend of drv:sd dev:0:0:0:0 complete after 387.581 msecs
[ 2776.518504] PM: suspend of drv:scsi dev:target0:0:0 complete after 387.562 msecs
[ 2776.518510] PM: suspend of drv:scsi dev:host0 complete after 387.537 msecs
[ 2776.550191] PM: suspend of drv:ahci dev:0000:00:11.0 complete after 307.734 msecs
[ 2776.550202] PM: suspend of drv: dev:pci0000:00 complete after 307.627 msecs
[ 2776.550206] PM: suspend of devices complete after 419.621 msecs
[ 2776.550209] PM: suspend devices took 0.420 seconds
[ 2776.590168] PM: late suspend of devices complete after 39.952 msecs
[ 2776.590214] ACPI: Preparing to enter system sleep state S3
[ 2776.690179] PM: Saving platform NVS memory
[ 2776.738101] Disabling non-boot CPUs ...
[ 2776.738101] Back to C!
[ 2776.738101] PM: Restoring platform NVS memory
[ 2776.738101] ACPI: Waking up from system sleep state S3
[ 2776.738101] pcieport 0000:00:04.0: restoring config space at offset 0x7 (was 0x20005121, writing 0x5121)
[ 2776.738101] pcieport 0000:00:04.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 2776.738101] pcieport 0000:00:04.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2776.738101] pcieport 0000:00:05.0: restoring config space at offset 0x7 (was 0x1f1, writing 0x200001f1)
[ 2776.738101] pcieport 0000:00:05.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 2776.738101] pcieport 0000:00:05.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2776.738101] ahci 0000:00:11.0: restoring config space at offset 0x1 (was 0x2300003, writing 0x2300407)
[ 2776.750242] ehci_hcd 0000:00:12.2: BAR 0: set to [mem 0x92306500-0x923065ff] (PCI address [0x92306500-0x923065ff]
[ 2776.750269] ehci_hcd 0000:00:12.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00012)
[ 2776.770112] ehci_hcd 0000:00:13.2: BAR 0: set to [mem 0x92306400-0x923064ff] (PCI address [0x92306400-0x923064ff]
[ 2776.770141] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00012)
[ 2776.770291] HDA Intel 0000:01:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2776.770294] HDA Intel 0000:01:05.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
[ 2776.770415] ath9k 0000:08:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
[ 2776.770483] PM: early resume of devices complete after 31.060 msecs
[ 2776.770733] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2776.770751] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2776.770764] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2776.770779] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2776.770792] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2776.770837] fglrx_pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2776.770839] fglrx_pci 0000:01:05.0: setting latency timer to 64
[ 2776.774060] [fglrx] Power up the ASIC
[ 2776.774082] [fglrx] Preparing resume fglrx in kernel.
[ 2776.803886] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2776.803888] HDA Intel 0000:01:05.1: setting latency timer to 64
[ 2776.803937] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2776.803967] sd 0:0:0:0: [sda] Starting disk
[ 2776.807140] [fglrx] Resuming fglrx in kernel completed.
[ 2776.807300] [fglrx] IRQ 18 Enabled
[ 2776.910096] PM: resume of drv:usb dev:usb3 complete after 106.135 msecs
[ 2776.910108] PM: resume of drv:hub dev:3-0:1.0 complete after 106.149 msecs
[ 2776.910127] PM: resume of drv:usb dev:usb4 complete after 106.167 msecs
[ 2776.910132] PM: resume of drv:hub dev:4-0:1.0 complete after 106.171 msecs
[ 2776.950092] PM: resume of drv:usb dev:usb2 complete after 146.135 msecs
[ 2776.950103] PM: resume of drv:hub dev:2-0:1.0 complete after 146.148 msecs
[ 2776.971182] PM: resume of drv:usb dev:3-1 complete after 167.180 msecs
[ 2776.971193] PM: resume of drv:usbhid dev:3-1:1.0 complete after 167.074 msecs
[ 2776.971197] PM: resume of drv:usbhid dev:3-1:1.1 complete after 167.055 msecs
[ 2777.070094] usb 2-2: reset high speed USB device using ehci_hcd and address 3
[ 2777.229285] PM: resume of drv:usb dev:2-2 complete after 425.288 msecs
[ 2777.229295] PM: resume of drv:usb-storage dev:2-2:1.0 complete after 425.301 msecs
[ 2777.229301] PM: resume of drv:scsi dev:host2 complete after 425.305 msecs
[ 2777.229307] PM: resume of drv:scsi_host dev:host2 complete after 425.310 msecs
[ 2777.229311] PM: resume of drv:scsi dev:target2:0:0 complete after 425.164 msecs
[ 2777.229321] PM: resume of drv:sd dev:2:0:0:0 complete after 425.155 msecs
[ 2777.229327] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 425.011 msecs
[ 2777.340085] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[ 2777.350091] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2777.377483] ata2.00: configured for UDMA/100
[ 2777.528512] PM: resume of drv:usb dev:2-1 complete after 724.543 msecs
[ 2777.528524] PM: resume of drv:uvcvideo dev:2-1:1.0 complete after 724.557 msecs
[ 2777.528528] PM: resume of drv:uvcvideo dev:2-1:1.1 complete after 724.560 msecs
[ 2778.030204] PM: resume of drv:battery dev:PNP0C0A:00 complete after 1225.970 msecs
[ 2778.610090] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2778.861810] ata1.00: configured for UDMA/133
[ 2778.908648] PM: resume of drv:sd dev:0:0:0:0 complete after 2104.673 msecs
[ 2778.908659] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2104.670 msecs
[ 2778.908663] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 851.479 msecs
[ 2778.911601] PM: resume of devices complete after 2141.043 msecs
[ 2778.911712] PM: resume devices took 2.140 seconds
[ 2778.911737] PM: Finishing wakeup.
[ 2778.911739] Restarting tasks ... done.
[ 2778.922638] video LNXVIDEO:00: Restoring backlight state
[ 2779.408738] pcieport 0000:00:04.0: wake-up capability disabled by ACPI
[ 2779.408747] tg3 0000:02:00.0: PME# disabled
[ 2779.408807] tg3 0000:02:00.0: irq 43 for MSI/MSI-X
[ 2779.432228] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2779.533141] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2780.051665] tg3 0000:02:00.0: eth0: Link is down
[ 2781.824395] wlan0: authenticate with 68:7f:74:bf:a2:68 (try 1)
[ 2781.828246] wlan0: authenticated
[ 2781.828269] wlan0: associate with 68:7f:74:bf:a2:68 (try 1)
[ 2781.832433] wlan0: RX AssocResp from 68:7f:74:bf:a2:68 (capab=0x431 status=0 aid=1)
[ 2781.832438] wlan0: associated
[ 2781.846163] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2784.237265] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[ 2792.790027] wlan0: no IPv6 routers present
[ 2807.907506] lo: Disabled Privacy Extensions
[ 3583.078625] lo: Disabled Privacy Extensions
```

---

### Post by cowboydren on 2010-12-23
I also tried using GRUB to boot with the kernel that was originally installed, but I get some sort of mount error and it drops to Busybox instead of actually booting. I really hope this is some hdparm flag or something that I can change.

---

