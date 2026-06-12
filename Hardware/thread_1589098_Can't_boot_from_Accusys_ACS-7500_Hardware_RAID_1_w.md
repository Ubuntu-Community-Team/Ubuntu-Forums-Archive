---
title: "Can't boot from Accusys ACS-7500 Hardware RAID 1 with HotSwap in Ubuntu 10"
date: 2010-10-05
forum: Hardware
---

### Post by styelz on 2010-10-05
I am unable to boot from my Accusys hardware raid unit.
I detects and works fine from the 10.04 Live CD and installs ok but drops into BusyBox with a drive timeout.

cat /proc/modules shows pata_amd is used 0 times.
blkid  shows nothing.

I can remove the drive from the Raid unit and boot fine from it.
This only started to happen since upgrading to 10.04. all previous versions of Ubuntu worked fine.

Any help ?

---

### Post by styelz on 2010-10-11
I had the same issue on 10.10 beta also, installing 10.10rc today fixed my raid problem.

Thanks!

---

