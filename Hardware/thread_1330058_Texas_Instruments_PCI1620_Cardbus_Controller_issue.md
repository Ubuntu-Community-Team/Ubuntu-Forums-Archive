---
title: "Texas Instruments PCI1620 Cardbus Controller issues..."
date: 2009-11-18
forum: Hardware
---

### Post by atirox on 2009-11-18
I have a Compaq Presario R3055CA laptop, which has a built-in 5 in 1 card reader. The card reader is controlled by a Texas Instruments PCI1620 Cardbus controller chip. For whatever reason, it will not detect any cards inserted into the card reader. I do know that the card reader works, as I can use it in Windows just fine.

Here is what "lspci -v | less" says about it...

```

02:04.0
CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
Subsystem: Hewlett-Packard Company Device 006b
Flags: bus master, medium devsel, latency 168, IRQ 17
Memory at e8209000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
Memory window 0: 2c000000-2ffff000 (prefetchable)
Memory window 1: 38000000-3bfff000
I/O window 0: 0000a800-0000a8ff
I/O window 1: 0000ac00-0000acff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket


02:04.1 
CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
Subsystem: Hewlett-Packard Company Device 006b
Flags: bus master, medium devsel, latency 168, IRQ 16
Memory at e820a000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=02, secondary=04, subordinate=07, sec-latency=176
Memory window 0: 30000000-33fff000 (prefetchable)
Memory window 1: 3c000000-3ffff000
I/O window 0: 00001400-000014ff
I/O window 1: 00001800-000018ff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket

02:04.2
System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
Subsystem: Hewlett-Packard Company Device 006b
Flags: bus master, medium devsel, latency 64
I/O ports at a400 [size=64]
Capabilities: [44] Power Management version 2

```

How do I get it to recognize any card inserted into it?

---

