---
title: "dv6 partitioning help"
date: 2011-11-02
forum: Hardware
---

### Post by anku94 on 2011-11-02
Hi guys

I'm facing a few problems partitioning my HP dv6 6165tx. Specs - i7 2670M, Radeon 6770M, 750GB, 5400rpm HDD, 4GBx1 DDR3 RAM

The default partitioning scheme was (it's twisted, evil and nasty):-

1. 100MB Drive [Boot drive - system boots from here]
2. 700GB Drive [Windows installation]
3. 14 GB Drive [Recovery partition]
4. HP_TOOLS [100MB, BIOS update files are installed here, BIOS detects new files and automatically updates]

All these are primary partitions, and hence, I was unable to create new partitions for Linux. So, I deleted the HP_TOOLS partition, as it can be recreated and the software inside it can be re-installed (I backed it up anyway).

I shrinked the 700GB Windows Drive to 350GB. So, I had 350GB unpartitioned space and 100MB unpartitioned space from HP_TOOLS (these two didn't merge).

What I want to do now - create a 40GB Linux partition, 2-4GB swap partition and rest (310 GB) a NTFS/FAT32 partition (so that it can be accessed from both OSes). Can all these be thrown under ONE extended partition? My attempts at doing that were unsuccessful. (After I installed Linux, I again reached the limit of 4 primary partitions, and 310GB unallocated space couldn't be partitioned.)

Or is there any other alternative that meets my requirements? I don't want to delete the recovery drive as I find it highly convenient, and I don't trust optical disks (it allows me to create recovery media, but only once).

Thanks a lot

---

