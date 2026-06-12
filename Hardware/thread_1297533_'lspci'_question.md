---
title: "'lspci' question"
date: 2009-10-21
forum: Hardware
---

### Post by flyinggreg on 2009-10-21
I am trying to get better performance on a desktop with Jaunty so I can run Flightgear.  It's a 2.8GHz, 768Mb DDR with a 82845G/GL/GE video processor.

I have read the issues with Intel video drivers with xorg and have been trying to get the frame rates up (>3 fps) in Flightgear - they are ~14-16 fps on penguin racer.

So...I have been looking at the 'lspci -vvnn' dump and was wondering if xorg is getting confused (or am I confused).  Here's the part I have a question about:

```
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)
	Subsystem: IBM Device [1014:0267]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 88000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>
	Kernel modules: intelfb
```

The question I have, does it appear there is 2 occurrences for the same video processor but using different memory allocations and drivers????  To me it appears there is 1 occurrence for an allocation of 256-Mb (which I set in BIOS), and another for 128-Mb.  I reading this correct?????

I am thinking this might have to do with my LOW fps in Flightgear.

---

