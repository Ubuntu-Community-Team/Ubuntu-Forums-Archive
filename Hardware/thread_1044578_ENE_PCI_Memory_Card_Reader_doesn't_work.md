---
title: "ENE PCI Memory Card Reader doesn't work"
date: 2009-01-19
forum: Hardware
---

### Post by ioozef on 2009-01-19
As title says. The memory card reader is the only thing I didn't manage to get working on Ubuntu (8.10) on my Compal HEL80 laptop. It's shown in lspci:
```
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```
so Ubuntu detects the reader, but when I insert a card nothing happens, there are no new entries in /dev.
How can I make the card reader work?

---

### Post by phil989 on 2009-04-16
> **ioozef said:**
> As title says. The memory card reader is the only thing I didn't manage to get working on Ubuntu (8.10) on my Compal HEL80 laptop. It's shown in lspci:
```
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```
so Ubuntu detects the reader, but when I insert a card nothing happens, there are no new entries in /dev.
How can I make the card reader work?

I think i'm having the same problem:

```
lspci -vvnn

02:04.0 CardBus bridge [0607]: ENE Technology Inc CB-710/2/4 Cardbus Controller [1524:1411]
	Subsystem: Acer Incorporated [ALI] Device [1025:0065]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e8202000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 0000a800-0000a8ff
	I/O window 1: 0000ac00-0000acff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530]
	Subsystem: Acer Incorporated [ALI] Device [1025:0065]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (250ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at e8200c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:0065]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 18000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at e8201000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

02:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520]
	Subsystem: Acer Incorporated [ALI] Device [1025:0065]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (250ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at e8201400 (32-bit, non-prefetchable) [size=128]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-


```

Post the output of 'lspci -vvnn', I think someone has had some luck with similar hardware.  Launchpad link: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303844](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303844)

---

