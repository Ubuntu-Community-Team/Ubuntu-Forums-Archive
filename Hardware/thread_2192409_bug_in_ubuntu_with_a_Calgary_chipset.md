---
title: "bug in ubuntu with a Calgary chipset"
date: 2013-12-07
forum: Hardware
---

### Post by cod2 on 2013-12-07
The error when I get 170-180 players on my minecraft server:
Dec  1 20:29:13 minecraft kernel: [83704.799017] Calgary: DMA error on Calgary PHB 0x6, 0x10010000@CSR 0x04000000@PLSSR
Dec  1 20:29:13 minecraft kernel: [83704.800002] [sched_delayed] sched: RT throttling activated
Dec  1 20:29:14 minecraft kernel: [83705.343754] Uhhuh. NMI received for unknown reason 25 on CPU 0.
Dec  1 20:29:14 minecraft kernel: [83705.343892] Do you have a strange power saving mode enabled?
Dec  1 20:29:14 minecraft kernel: [83705.344069] Dazed and confused, but trying to continue
Dec  1 20:29:23 minecraft kernel: [83714.784044] ------------[ cut here ]------------

[IMG]http://i.imgur.com/aRZOraq.png[/IMG]

---

### Post by Yellow Pasque on 2013-12-09
First, make sure your CPU is not overheating.

From some quick Googling, I think i might be happening because the minecraft server is hogging the CPU to the point where a critical system process has to turn off preemption or the system risks becoming unstable.

---

