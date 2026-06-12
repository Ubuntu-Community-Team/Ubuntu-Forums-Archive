---
title: "i915 driver problem: grainy display"
date: 2009-08-22
forum: Hardware
---

### Post by Muppy on 2009-08-22
Hi,

I have installed a fresh copy of Jaunty 9.04 Desktop i386 (32-bit) edition on an ASUS W3H00A (same as Z63A). However, the display driver for the Intel i915 seems to be very buggy. I followed the following tutorial:
[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582"), tried the "safe" setup, then the "optimum" setup with the 2.6.31_rc7 kernel, which I have got from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/"). All to no avail. The display shows the attached picture (except the top-right corner where I have wiped out the name...). It really looks this grainy, there's nothing wrong with the picture here. It already starts at the login screen: the screen itself shows perfectly nice (no black spots), but the entered text in the login/password box is this grainy.

I have also downloaded the latest drivers from [http://intellinuxgraphics.org/2009Q2.html]("http://intellinuxgraphics.org/2009Q2.html"), compiled them (with configure --prefix=/usr) and installed them, but nothing changed.

Does anyone know what's wrong with it? Really weird! I have been searching the net for so many hours now but I haven't got a clue what's wrong here. It's pretty urgent, I have to return this laptop in seven hours and it should be fully working... Any (quick) reply is appreciated!

The following data are retrieved from this machine:

lspci -vvnn:
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1882]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1882]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fbe00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at b800 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at fbdc0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1882]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at fbe80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:10c3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fbdb8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag+ RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+
			Slot #  1, PowerLimit 0.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0100c  Data: 4159
	Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device [0000:0000]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:10e7]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at a400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:10e7]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at a800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:10e7]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at b000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:10e7]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at b400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:10e7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fbdb7c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
	I/O behind bridge: 0000d000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 0000000020000000-0000000025ffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device [0000:0000]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 04) (prog-if 80 [Master])
	Subsystem: ASUSTeK Computer Inc. Device [1043:10e7]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ffa0 [size=16]
	Capabilities: [70] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:10e7]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 0
	Region 4: I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)
	Subsystem: ASUSTeK Computer Inc. Device [1043:173c]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (5750ns min, 7750ns max), Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fbffc000 (32-bit, non-prefetchable) [size=16K]
	Region 1: I/O ports at d800 [size=256]
	Expansion ROM at 24000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data <?>
	Kernel driver in use: skge
	Kernel modules: skge

02:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1967]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fbf00000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 28000000-2bfff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	BridgeCtl: Parity+ SERR+ ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1967]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 1000ns max)
	Interrupt: pin B routed to IRQ 16
	Region 0: Memory at fbffb000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME+
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1967]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fbffb800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

02:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 08)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1967]
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 5
	Region 0: Memory at fbffbc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-

02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
	Subsystem: Intel Corporation Device [8086:2701]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 6000ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fbffa000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

```

xorg.conf:
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option  "Tiling"        "false"
        Driver  "intel"
        Option          "ModeDebug" "true"
        Option          "DRI"   "true"
EndSection

```

/var/log/Xorg.0.log:
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux britflex 2.6.31-020631rc7-generic #020631rc7 SMP Sat Aug 22 09:51:01 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 22 19:22:40 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 4, Mem @ 0xfbe00000/524288, 0xd0000000/268435456, 0xfbdc0000/262144, I/O @ 0x0000b800/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 2.7.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, IGD_GM, IGD_G, 965G, G35,
        965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile Intel® GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) intel(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "uxa"
(**) intel(0): Option "DRI" "true"
(**) intel(0): Option "ModeDebug" "true"
(**) intel(0): Option "Tiling" "false"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) intel(0): Chipset: "915GM"
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(II) intel(0): Resizable framebuffer: available (0 4)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): Output VGA1 using monitor section Configured Monitor
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): Output TV1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 114  Serial#: 0
(II) intel(0): Year: 2004  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.310 greenY: 0.560
(II) intel(0): blueX: 0.149 blueY: 0.130   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  305 x 183 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 823 v_border: 0
(II) intel(0):  B140EW01V1
(II) intel(0):  B140EW01V1
(II) intel(0): Monitor name: B140EW01V1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff0006af140100000000
(II) intel(0):  010e0103802114780a055097574f8f26
(II) intel(0):  21505400000001010101010101010101
(II) intel(0):  010101010101c61b00a0500037301070
(II) intel(0):  130031b710000018000000fe00423134
(II) intel(0):  304557303156310a2020000000fe0042
(II) intel(0):  3134304557303156310a2020000000fc
(II) intel(0):  00423134304557303156310a20200014
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x768"x60.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output TV1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1280x768
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) Loading sub module "dri2"
(II) LoadModule: "dri2"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri2.so
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling disabled
(==) intel(0): VideoRam: 4194303 KB
(II) intel(0): Attempting memory allocation with untiled buffers.
(II) intel(0): Untiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0xffff4fff: DRI memory manager (4194260 kB)
(II) intel(0): 0x00000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x00000000:            start of memory manager
(II) intel(0): 0x04800000-0x04bbffff: front buffer (3840 kB)
(II) intel(0): 0x04600000-0x04609fff: HW cursors (40 kB)
(II) intel(0): 0xffff5000:            end of memory manager
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(WW) intel(0): Option "EXAOptimizeMigration" is not used
(WW) intel(0): Option "MigrationHeuristic" is not used
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 305 x 183
(II) config/hal: Adding input device Asus Laptop extra buttons
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 2.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(**) Asus Laptop extra buttons: always reports core events
(**) Asus Laptop extra buttons: Device: "/dev/input/event7"
(II) Asus Laptop extra buttons: Found keys
(II) Asus Laptop extra buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Asus Laptop extra buttons: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Asus Laptop extra buttons: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Asus Laptop extra buttons: xkb_layout: "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.99.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event10"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(WW) SynPS/2 Synaptics TouchPad: priv->synpara->movement_bottom_edge NOT AVAILABLE.
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 114  Serial#: 0
(II) intel(0): Year: 2004  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.310 greenY: 0.560
(II) intel(0): blueX: 0.149 blueY: 0.130   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  305 x 183 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 823 v_border: 0
(II) intel(0):  B140EW01V1
(II) intel(0):  B140EW01V1
(II) intel(0): Monitor name: B140EW01V1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff0006af140100000000
(II) intel(0):  010e0103802114780a055097574f8f26
(II) intel(0):  21505400000001010101010101010101
(II) intel(0):  010101010101c61b00a0500037301070
(II) intel(0):  130031b710000018000000fe00423134
(II) intel(0):  304557303156310a2020000000fe0042
(II) intel(0):  3134304557303156310a2020000000fc
(II) intel(0):  00423134304557303156310a20200014
(II) intel(0): EDID vendor "AUO", prod id 276
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x768"x0.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x768"x60.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 114  Serial#: 0
(II) intel(0): Year: 2004  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.310 greenY: 0.560
(II) intel(0): blueX: 0.149 blueY: 0.130   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  305 x 183 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 823 v_border: 0
(II) intel(0):  B140EW01V1
(II) intel(0):  B140EW01V1
(II) intel(0): Monitor name: B140EW01V1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff0006af140100000000
(II) intel(0):  010e0103802114780a055097574f8f26
(II) intel(0):  21505400000001010101010101010101
(II) intel(0):  010101010101c61b00a0500037301070
(II) intel(0):  130031b710000018000000fe00423134
(II) intel(0):  304557303156310a2020000000fe0042
(II) intel(0):  3134304557303156310a2020000000fc
(II) intel(0):  00423134304557303156310a20200014
(II) intel(0): EDID vendor "AUO", prod id 276
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x768"x0.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x768"x60.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 114  Serial#: 0
(II) intel(0): Year: 2004  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.310 greenY: 0.560
(II) intel(0): blueX: 0.149 blueY: 0.130   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  305 x 183 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 823 v_border: 0
(II) intel(0):  B140EW01V1
(II) intel(0):  B140EW01V1
(II) intel(0): Monitor name: B140EW01V1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff0006af140100000000
(II) intel(0):  010e0103802114780a055097574f8f26
(II) intel(0):  21505400000001010101010101010101
(II) intel(0):  010101010101c61b00a0500037301070
(II) intel(0):  130031b710000018000000fe00423134
(II) intel(0):  304557303156310a2020000000fe0042
(II) intel(0):  3134304557303156310a2020000000fc
(II) intel(0):  00423134304557303156310a20200014
(II) intel(0): EDID vendor "AUO", prod id 276
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x768"x0.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x768"x60.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 114  Serial#: 0
(II) intel(0): Year: 2004  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.310 greenY: 0.560
(II) intel(0): blueX: 0.149 blueY: 0.130   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  305 x 183 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 823 v_border: 0
(II) intel(0):  B140EW01V1
(II) intel(0):  B140EW01V1
(II) intel(0): Monitor name: B140EW01V1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff0006af140100000000
(II) intel(0):  010e0103802114780a055097574f8f26
(II) intel(0):  21505400000001010101010101010101
(II) intel(0):  010101010101c61b00a0500037301070
(II) intel(0):  130031b710000018000000fe00423134
(II) intel(0):  304557303156310a2020000000fe0042
(II) intel(0):  3134304557303156310a2020000000fc
(II) intel(0):  00423134304557303156310a20200014
(II) intel(0): EDID vendor "AUO", prod id 276
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x768"x0.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x768"x60.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 114  Serial#: 0
(II) intel(0): Year: 2004  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 20
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.310 greenY: 0.560
(II) intel(0): blueX: 0.149 blueY: 0.130   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  305 x 183 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1408 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 823 v_border: 0
(II) intel(0):  B140EW01V1
(II) intel(0):  B140EW01V1
(II) intel(0): Monitor name: B140EW01V1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff0006af140100000000
(II) intel(0):  010e0103802114780a055097574f8f26
(II) intel(0):  21505400000001010101010101010101
(II) intel(0):  010101010101c61b00a0500037301070
(II) intel(0):  130031b710000018000000fe00423134
(II) intel(0):  304557303156310a2020000000fe0042
(II) intel(0):  3134304557303156310a2020000000fc
(II) intel(0):  00423134304557303156310a20200014
(II) intel(0): EDID vendor "AUO", prod id 276
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x768"x0.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x768"x60.0   71.10  1280 1296 1408 1440  768 769 772 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID for output TV1

```

lsmod:
```

Module                  Size  Used by
binfmt_misc             8228  1 
ppdev                   6688  0 
bridge                 48272  0 
stp                     2240  1 bridge
bnep                   12284  2 
lp                      8964  0 
parport                35596  2 ppdev,lp
joydev                 10560  0 
snd_hda_codec_realtek   204864  1 
snd_hda_intel          28488  0 
snd_hda_codec          77084  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            40544  0 
snd_mixer_oss          16924  1 snd_pcm_oss
snd_pcm                78048  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2784  0 
snd_seq_oss            29312  0 
pcmcia                 37192  0 
snd_seq_midi            6464  0 
i915                  223144  1 
snd_rawmidi            21920  1 snd_seq_midi
snd_seq_midi_event      6876  2 snd_seq_oss,snd_seq_midi
drm                   159712  2 i915
snd_seq                49968  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22340  2 snd_pcm,snd_seq
snd_seq_device          7016  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           24200  1 
rsrc_nonstatic         11388  1 yenta_socket
i2c_algo_bit            5792  1 i915
iTCO_wdt               11072  0 
iTCO_vendor_support     3904  1 iTCO_wdt
psmouse                56884  0 
sdhci_pci               7292  0 
sdhci                  18656  1 sdhci_pci
ipw2200               143976  0 
libipw                 43628  1 ipw2200
irda                  189468  0 
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  20148  1 i915
asus_laptop            18072  0 
snd                    59332  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7456  1 snd
snd_page_alloc          9092  2 snd_hda_intel,snd_pcm
serio_raw               5472  0 
pcspkr                  2364  0 
lib80211                6464  2 ipw2200,libipw
crc_ccitt               1852  1 irda
intel_agp              26716  1 
output                  2780  1 video
led_class               4128  2 sdhci,asus_laptop
agpgart                35852  2 drm,intel_agp
ohci1394               31372  0 
ieee1394               89220  1 ohci1394
skge                   39980  0 

```

Thanks so much for your help! I'm pretty desperate right now...

---

