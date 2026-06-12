---
title: "Wireless adapter problems Oneiric 11.10"
date: 2011-10-20
forum: Hardware
---

### Post by Pharod on 2011-10-20
Hello everyone,

I just installed Ubuntu (32 bits) Oneiric Ocelot 11.10 on my home machine. It's the first time running Linux on it, and my wireless connection is really slow (sometimes it doesn't do anything). It is basically unusable.

I've been searching for a fix all over the place, but can't find one.

I have a D-Link wireless adapter DWL-G520 rev. B, and if it helps, this is the output of running lspci -vvv

```
04:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
	Subsystem: D-Link System Inc AirPlus DWL-G520 Wireless PCI Adapter (rev. B)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at e3000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k
```

Please let me know if you need any more info that can help to find a fix.

Thanks!

---

