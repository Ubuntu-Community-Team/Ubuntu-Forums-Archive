---
title: "Getting rid of windows"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by atliia on 2009-01-01
I am wondering how to get rid of the windows FAT32 partion and give the ubuntu partion the unallocated diskspace using Gpartioned.

---

### Post by oilchangeguy on 2009-01-01
> **atliia said:**
> I am wondering how to get rid of the windows FAT32 partion and give the ubuntu partion the unallocated diskspace using Gpartioned.

from gparted, highlight the partition in question. delete it, then highlight the ubuntu partition, locate the option to expand the partition. reboot, it's that simple.

---

