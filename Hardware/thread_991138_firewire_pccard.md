---
title: "firewire pccard"
date: 2008-11-23
forum: Hardware
---

### Post by SignoreCitizen on 2008-11-23
I installed xubuntu on a laptop that was previously running FreeBSD. I have an external hard drive (Wd MyBook) formated as UFS connected to a pccard. The card is recognized with lspci -vvv

03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46) (prog-if 10)
	Subsystem: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 64 (8000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at 2c000000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at d000 [size=128]
	Region 2: Memory at 2c000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

but I never see any drive in /dev. I would think that it would show up there.

Am I doing something wrong.

Thanks in advance for any help.

---

