---
title: "what does this mean?"
date: 2009-05-08
forum: Hardware
---

### Post by timremy on 2009-05-08
please help


May  9 06:32:51 tim-laptop kernel: [ 2295.880077] ata1: SATA link down (SStatus 0 SControl 300)
May  9 06:32:51 tim-laptop kernel: [ 2295.880104] ata1: EH complete
May  9 06:32:51 tim-laptop kernel: [ 2295.881581] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
May  9 06:32:51 tim-laptop kernel: [ 2295.881599] ata1: irq_stat 0x00000040, connection status changed
May  9 06:32:51 tim-laptop kernel: [ 2295.881607] ata1: SError: { CommWake DevExch }
May  9 06:32:51 tim-laptop kernel: [ 2295.881623] ata1: hard resetting link

this started after an upgrade to ubuntu 9.04 and is stll here after re-installing
ubuntu 8.10.

thank you

timremy

---

### Post by timremy on 2009-05-13
this was fixed by re-installing ubuntu 8.10 only using the kernal, 2.6.27-7-generic.

timremy

---

### Post by timremy on 2009-05-14
let me re-state the above commit.

1. i did a re-format using gparted
2. i re-loaded the os from start. a clean install.
3. all upgrades took and as usual, ubuntu came through.

alot of mistakes are my fault not the system..

timremy

---

