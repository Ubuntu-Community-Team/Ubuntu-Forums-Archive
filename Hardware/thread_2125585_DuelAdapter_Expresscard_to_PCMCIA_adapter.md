---
title: "DuelAdapter Expresscard to PCMCIA adapter"
date: 2013-03-14
forum: Hardware
---

### Post by ckblackm on 2013-03-14
Hello,

I have a DuelAdapter Expresscard to PCMCIA adapter that I'd like to get working with Linux.

My system: Asus M50VM laptop (Intel Core Duo P8400, 4GB ram, Nvidia 9600M GS) running Ubuntu 10.04 LTS

uname -a:
Linux ckblackm-laptop 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux

The adapter plugs into the expresscard slot and allows the use of legacy PCCard/PCMCIA cards.  It has a switch on the bottom that's
for A: MacOS and B: WinXP.  The switch in position B seems to do nothing, but if left in A, I get the following results.


lspci:
04:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)

dmesg:
[17548.818787] pciehp 0000:00:1c.2:pcie04: Card present on Slot(0)
[17548.950279] pci 0000:04:00.0: supports D1 D2
[17548.950471] pci 0000:04:00.0: bridge io port: [0x00-0xfff]
[17548.950482] pci 0000:04:00.0: bridge 32bit mmio: [0x000000-0x0fffff]
[17548.950500] pci 0000:04:00.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[17548.950531] pci 0000:04:00.0: PCI bridge, secondary bus 0000:05
[17548.950536] pci 0000:04:00.0:   IO window: disabled
[17548.950548] pci 0000:04:00.0:   MEM window: disabled
[17548.950558] pci 0000:04:00.0:   PREFETCH window: disabled
[17548.950597] pci 0000:04:00.0: setting latency timer to 64
[17548.984869] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4


The results don't seem to change if I put anything (or not) in the pcmcia slot of the adapter.  Any ideas on getting this to work?  It would make
transferring to/from my legacy pcmcia flash ram cards much easier.  Thanks.

---

