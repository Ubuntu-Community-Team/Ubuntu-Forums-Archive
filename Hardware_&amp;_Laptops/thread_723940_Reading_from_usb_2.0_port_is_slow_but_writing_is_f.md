---
title: "Reading from usb 2.0 port is slow but writing is fast."
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by jktla on 2008-03-14
I have old IBM thinkpad laptop, and I installed PCMCIA usb 2.0 card to it. When I install usb 2.0 device(memory stick or external HDD) to usb 2.0 port I get very slow read speed about 800KB/s, but writing to devices is fast, about 10MB/s. 

sync option is not used in mounting.

Usb devices are recognized right as usb 2.0 ehci devices.

Does anyone have this same problem? How can I make reading faster?

-jktla

---

### Post by jktla on 2008-03-15
I have Ubuntu 7.10.

This problem is strange, because reading is slow and writing fast.

Can anybody help? 

-jktla

---

### Post by kennylam on 2008-04-13
I am suffering from this problem too...

Ubuntu Server 7.1.0

My PC is Dell Lattude Cpt C400GT
Celeron 400
128M RAM
BIOS verson A14, ACPI supported

with VIA Cardbus USB 2.0 card installed 
```
06:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 22, IRQ 11
        Memory at 2c000000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1800 [size=32]
        Capabilities: [80] Power Management version 2

06:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 22, IRQ 11
        Memory at 2c000100 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1820 [size=32]
        Capabilities: [80] Power Management version 2

06:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 22, IRQ 11
        Memory at 2c000200 (32-bit, non-prefetchable) [size=256]
        Memory at 2c000300 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

```

The cardbus slot is fast enough because I can get 12MB/s upstream/downstream speed from a 3Com 3cCFE575BT

---

