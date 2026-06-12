---
title: "Ubuntu 9.04 Promise Fasttrak tx2650 woes..."
date: 2009-05-13
forum: Hardware
---

### Post by reznorio on 2009-05-13
Hi,

I installed a SAS controller pci-e 1x card and 2x146gig 15K SAS drives. I installed Vista on the first JBOD drive flawlessly (needed to input vista driver when at install from cd that came with it) and wanted to install Ubuntu 9.04 on the second.

That's where the problems began.

I've downloaded the t3sas source from promise and managed to compile it on a liveCD after reading up on peoples' compilation errors. I can now modprobe it but fdisk shows no disks whatsoever???

What's weird is ubuntu looked like it found it properly before any of this but I still can't see the disks. Both are configured in the promise bios as standard JBODs (3-1 and 4-1). Nothing fancy.

Can someone help me?

thanks in advance.

lspci -vv -nn

34:00.0 RAID bus controller [0104]: Promise Technology, Inc. PDC42819 [FastTrak TX2650/TX4650] [105a:3f20]
	Subsystem: Promise Technology, Inc. Device [105a:3f21]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 1200 [size=128]
	Region 2: I/O ports at 1100 [size=256]
	Region 3: Memory at fb022000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at fb000000 (32-bit, non-prefetchable) [size=128K]
	Region 5: Memory at fb020000 (32-bit, non-prefetchable) [size=8K]
	[virtual] Expansion ROM at fb400000 [disabled] [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: t3sas

---

