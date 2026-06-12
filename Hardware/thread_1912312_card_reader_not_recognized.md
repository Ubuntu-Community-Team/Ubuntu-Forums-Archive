---
title: "card reader not recognized"
date: 2012-01-20
forum: Hardware
---

### Post by davethewave83 on 2012-01-20
In Ubuntu 10.04 Lucid Lynx 
I put my xD card into the card reader of my Acer extensa 4420
but it never shows up. even in disc utility:confused:

```
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 0123
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 20
	Memory at fc403000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0b, secondary=0c, subordinate=0d, sec-latency=176
	Memory window 0: f0000000-f3fff000 (prefetchable)
	Memory window 1: f4800000-f4bff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0123
	Flags: bus master, slow devsel, latency 64, IRQ 20
	Memory at fc402800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 0123
	Flags: slow devsel, IRQ 11
	Memory at fc400000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2

0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 0123
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fc401000 (32-bit, non-prefetchable) [size=4K]
	Memory at fc402000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [60] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394


```

I think that's it. Appears to have a driver working it, could it be my card that is dead?

---

### Post by davethewave83 on 2012-01-20
Someone loaned me a USB 2.0 xD drive, I put my card in it and plugged it into USB and it worked, it can read it. So I think it's a driver problem in Ubuntu, not running my card reader

---

