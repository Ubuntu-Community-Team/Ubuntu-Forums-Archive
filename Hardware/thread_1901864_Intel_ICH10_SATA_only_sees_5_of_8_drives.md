---
title: "Intel ICH10 SATA only sees 5 of 8 drives"
date: 2011-12-29
forum: Hardware
---

### Post by DantePasquale on 2011-12-29
Hi, I've been working with the tech support guys that i bought this workstation/server through and have reached a problem. I'll attach the lspci -vv output, but the gist of the problem is that if I set the BIOS to show the drives as IDE the OS sees 5 drives, plus the cd-rom. If I set it to AHCI and use the native BIOS driver then it sees the same thing even though it reports the controller as AHCI and uses the AHCI driver. I don't have the lspci for that as I can only get it to boot from the cd-rom, not from the hard drives in AHCI mode!

Any ideas?
```


spci -vv -s 00:1f.2
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Super Micro Computer Inc Device 0100
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at a000 [size=8]
	Region 1: I/O ports at 9c00 [size=4]
	Region 2: I/O ports at 9880 [size=8]
	Region 3: I/O ports at 9800 [size=4]
	Region 4: I/O ports at 9480 [size=16]
	Region 5: I/O ports at 9400 [size=16]
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ata_piix

```
```

sudo lspci -vv -s 00:1f.5
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 (prog-if 85 [Master SecO PriO])
	Subsystem: Super Micro Computer Inc Device 0100
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 9000 [size=8]
	Region 1: I/O ports at 8c00 [size=4]
	Region 2: I/O ports at 8880 [size=8]
	Region 3: I/O ports at 8800 [size=4]
	Region 4: I/O ports at 8480 [size=16]
	Region 5: I/O ports at 8400 [size=16]
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ata_piix

```
```

sudo lspci -vv -s 05:00.0
05:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
	Subsystem: JMicron Technology Corp. JMB368 IDE controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 256 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at d400 [size=8]
	Region 1: I/O ports at dc00 [size=4]
	Region 2: I/O ports at d880 [size=8]
	Region 3: I/O ports at d800 [size=4]
	Region 4: I/O ports at d480 [size=16]
	Expansion ROM at fbdf0000 [disabled] [size=64K]
	Capabilities: [68] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Express (v1) Legacy Endpoint, MSI 01
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 unlimited, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [70] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

```

Linux inferno.cocoanet.us 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:33:45 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

