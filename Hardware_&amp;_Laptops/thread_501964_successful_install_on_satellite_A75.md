---
title: "successful install on satellite A75"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by happygoodluck on 2007-07-16
Posting this as a quick solution in case you have similar issues. I was trying to install from the live CD. Observed:
- Seemed to run the install, then got to orange screen, and hung there forever
Investigation:
- Ubuntu FAQ said minimum RAM is 256 MB
- Toshiba Satellite has fixed 256 MB installed
- ran Ubuntu memory test, it said 191 MB installed
- check Windows->System Info, it said 192 MB memory installed
Action:
- run to CompUSA, bought 1 GB RAM and install
Result:
- got past that orange screen in the beginning

Point:
Perhaps something as simple as not enough memory is preventing the LiveCD for running through its install process for you. I never would have thought this was enough of an issue to derail the install, but hot dog am I ever glad this got me some progress!!

Specs: Toshiba A75-1253
Before RAM = 256 internal
After RAM = 256 internal, 1 GB in the memory slot

---

### Post by happygoodluck on 2007-07-16
Then it had problems on partitioning the drive. Since I intended to wipe this drive (eg: format the drive, celan the drive, delete everything from the drive), I stuck in my Win 2000 CD. It found my drive, and I gave it the ok to delete the old partition.

After that, my Ubuntu live CD had no problem partitioning the drive and installing.

---

### Post by wolfen69 on 2007-07-16
next time consider using the alternate cd for install. good for machines with low ram.

---

