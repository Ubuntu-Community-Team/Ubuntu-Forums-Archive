---
title: "Help getting Firewire working"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by theophile on 2008-01-11
Okay, I have  a Dell Inspiron 1501 notebook with a PCI-express slot (instead of PCMCIA). I have a PCIE firewire card. I insert it and boot the machine. It shows up as being present:

```
02:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=68
        Memory behind bridge: c0200000-c02fffff
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/4 Enable-
        Capabilities: [80] Subsystem: Unknown device 5678:1234
        Capabilities: [90] Express PCI/PCI-X Bridge IRQ 0

03:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev 01) (prog-if 10 [OHCI])
        Subsystem: Unknown device 5678:1234
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0204000 (32-bit, non-prefetchable) [size=2K]
        Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
```

I can load the raw1394 module:
```
[  234.866297] ieee1394: raw1394: /dev/raw1394 device initialized
```

However, when I plug my camcorder in, kino doesn't see it, even when running kino as root. It also doesn't register on the camcorder that "DV" connection is present. I can use this camcorder on my Gentoo desktop just fine, but not here. I think it might be a hardware thing and I need help tracking it down.

---

### Post by theophile on 2008-01-17
bump

---

