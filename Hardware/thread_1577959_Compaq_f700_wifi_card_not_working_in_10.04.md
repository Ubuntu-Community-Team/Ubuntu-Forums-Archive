---
title: "Compaq f700 wifi card not working in 10.04"
date: 2010-09-19
forum: Hardware
---

### Post by ubun7n00b on 2010-09-19
ok i have a compaq f700 laptop (restating the obvious) and recently the wifi chip stopped working. when I try hardware drivers it won't even show up. the switch that you slide is stuck on orange . If i leave my computer alone with the lid closed maybe it will work but as soon as I turn off my computer it will stop working.

---

### Post by XandR on 2010-11-01
Me too!
I have a Presario F700 (GW457LA#ABM) and my WiFi card is not working since I updated to 10.04.


I think the problem is the hotplug of the Mini-PCI port.
I get it working once during a kernel update (two months ago).
Comparing the dmesg, the only difference I found is:

```
[    0.208867] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.208870] pci 0000:00:03.0:   IO window: 0x5000-0x5fff
[    0.208873] pci 0000:00:03.0:   MEM window: 0xb8000000-0xbbffffff
[    0.208875] pci 0000:00:03.0:   PREFETCH window: 0x000000d0200000-0x000000d03fffff

```

```
[    0.208872] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.208874] pci 0000:00:03.0:   IO window: disabled
[    0.208877] pci 0000:00:03.0:   MEM window: 0xb8000000-0xbbffffff                                                                         
[    0.208879] pci 0000:00:03.0:   PREFETCH window: disabled
...
[   16.538202] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.538207] Disabling lock debugging due to kernel taint
[   16.557320] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 19
[   16.557342] wl 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, high) -> IRQ 19
[   16.664253] eth1: Broadcom BCM4311 802.11 Hybrid Wireless Controller 5.60.48.36

```

The  bridge to the Mini-PCI to my WiFi card was disabled on the boot when the wifi card loaded...
This was the first time the new kernel version booted.

I do not understand this really, I just found this difference when checking the logs after the only time it worked.

Please, if somebody has any idea of how to solve it!

---

