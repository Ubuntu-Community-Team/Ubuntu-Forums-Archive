---
title: "dmraid (&amp; kpartx) - SB8xx und SB9xx - RAID1 (GPT &amp; &gt;2TB) supported?"
date: 2012-09-18
forum: Hardware
---

### Post by ghost_zero on 2012-09-18
Hello,

i am thinking about buying a new main board and as I am using my RAID in a dual boot setup with Windows (though I am mostly in Ubuntu but not all the times),
I wanted to know if mainboards with SB9xx and SB8xx chips are supported by dmraid to provide support for RAID1 disks.
And if so, if I get support for GPT and > 2TB partitions when using kpartx (which I believe is default under Ubuntu 12.04 to activate disks?)?
It doesn't have to be the system partition, I only requre RAID for data partitions.

Also, one other question:
Is it possible to set one or two ports to RAID ACHI (not IDE) mode on the SB8xx or SB9xx and keep the rest in RAID mode. I am aksing because my system disk would be a SSD and I believe when in RAID (controller) the TRIM command won't get passed through (at least in Windows).
If not, I would need a mainboard with two SATA controllers - where I can use the second for AHCI mode only (and it would need to be a good controller - well in AHCI mode it should, however, definitely work fine under Linux).

---

