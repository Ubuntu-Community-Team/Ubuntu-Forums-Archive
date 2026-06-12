---
title: "Sony Memory Stick reader not mounted"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by McGragger on 2008-01-30
Nothing is mounted when I insert my memory stick in to my sony vgn-fs770 laptop. I see this using the tail command ...

[B]Jan 30 22:51:42 vaio kernel: [50901.816000] tifm_core: MemoryStick card detected in socket 0:1
Jan 30 22:51:42 vaio kernel: [50901.820000] tifm_ms: Unknown symbol tifm_has_ms_pif[/B]

I see this information about the card reader ...

[B]06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
        Subsystem: Sony Corporation Unknown device 8190
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 57 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 21
        Region 0: Memory at b0105000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
[/B]

Anyone have any ideas?

---

