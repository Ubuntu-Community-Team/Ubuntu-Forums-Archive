---
title: "HELP! I think I may have bricked a hard drive (VFAT)"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by tryp2nite on 2006-10-31
I have a VFAT slave drive that is not accessible as of right now. It mounts fine, but when trying to browse the drive ( i.e. "ls /mount/path/"), it just hangs.

What happened was:

The drive was nearly 100% full and I believe I was downloading something and I may have started overwriting the drive.

I have analyzed the drive with TestDisk and it told me:


"Partition sector doesn't have the endmark 0xAA55"


Where do I go from here?

Please help guys!

---

### Post by David Corrales on 2006-10-31
What happens if you access it from GParted? Try a livecd? Also try **fsck.vfat** (with the HD unmounted).
I know you can write specific stuff with the **dd** utility but you gotta be -really- careful if you only want to overwrite an specific sector.

---

### Post by tryp2nite on 2006-10-31
> **David Corrales said:**
> What happens if you access it from GParted? Try a livecd? Also try **fsck.vfat** (with the HD unmounted).
I know you can write specific stuff with the **dd** utility but you gotta be -really- careful if you only want to overwrite an specific sector.

GParted definitely recognizes the partition, however it tells me:

"Unable to read the contents of this filesystem"



I also tried fsck.vfat on the drive/partition and 

> 
$ sudo fsck.vfat /dev/hdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
No root directory!


As for "dd"... I'm looking into that right now.


Anyone have any other suggestions?

---

### Post by tryp2nite on 2006-11-01
bump

---

### Post by tryp2nite on 2006-11-01
bump

---

