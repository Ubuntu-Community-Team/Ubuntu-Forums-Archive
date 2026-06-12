---
title: "Marvell Wifi RTL8101e Not Working 10.10"
date: 2011-05-11
forum: Hardware
---

### Post by srose11 on 2011-05-11
I have Ubuntu 10.10 with several working kernels from 2.6.36 to.38. *** ALL 64 BIT ***.

Everything Works Great except Wifi, which I cannot get to work.

Apparently the drivers are in the kernel.

Here is the output for lspci the Ethernet Adapter(s) part...

Please let me know of any solutions...

08:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
	Subsystem: Marvell Technology Group Ltd. Device 2a08
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
	Region 1: Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Device 0566
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 43
	Region 0: I/O ports at a000 [size=256]
	Region 2: Memory at f0300000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at ffce0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

---

