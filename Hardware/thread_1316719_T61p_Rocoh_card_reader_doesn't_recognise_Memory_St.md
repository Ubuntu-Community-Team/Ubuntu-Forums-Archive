---
title: "T61p Rocoh card reader doesn't recognise Memory Stick Duo"
date: 2009-11-06
forum: Hardware
---

### Post by ferreter007 on 2009-11-06
Hi there,

I Beta tested Karmic after upgrading from Jaunty and have come across a problem. 

I have a Lenovo T61p with a Ricoh card reader. This recognises SD cards but doesn nothing when presented with a Memory Stick Duo (or Memory Stick PRO Duo in a Duo adaptor). 

Nothing changes in /dev/ and I know the card reader is picked up as this is the output from lspci

```

15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
    Subsystem: Lenovo Device [17aa:20c6]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f8100000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
    Memory window 0: f4000000-f7fff000 (prefetchable)
    Memory window 1: c0000000-c3fff000
    I/O window 0: 00008000-000080ff
    I/O window 1: 00008400-000084ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
    Subsystem: Lenovo Device [17aa:20c8]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at f8101000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

15:00.3 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

15:00.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)
    Subsystem: Lenovo Device [17aa:20ca]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 11
    Region 0: Memory at f8101800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11)
    Subsystem: Lenovo Device [17aa:20cb]
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 11
    Region 0: Memory at f8101c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

```

Anybody have any ideas what I can do?

Thanks guys.

---

### Post by 73ckn797 on 2009-11-06
I had the same problem since 8.04. You will need to get a USB adapter for a SD memory stick. I used a Sony camera and that was the only way to read the Duo memory card.

---

### Post by ferreter007 on 2009-11-06
I can read SD cards fine. Might try using a camera with cable instead then.

---

### Post by 73ckn797 on 2009-11-06
> **ferreter007 said:**
> I can read SD cards fine. Might try using a camera with cable instead then.

The cable should work but the adapter is very easy also and won't cost very much at all.

---

