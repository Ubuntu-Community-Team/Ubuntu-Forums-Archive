---
title: "My internal card reader not working on Feisty Compaq Presariov V3217AU"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by Dew922 on 2007-08-12
This is a part of lspci -v
> 03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at c3100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at c3100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: medium devsel, IRQ 10
        Memory at c3101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: medium devsel, IRQ 10
        Memory at c3101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

When I insert my mmc card to slot it is nothing happen no message in dmesg
I already try many method such as
apt-get install ivman
modprobe sd_mod
modprobe scsi_mod
modprobe mmc_core
modprobe mmoc_block
modprobe tifm_core ...

But it doesn't help me to solve that problem.
Some one help me please.
Thank you.

---

