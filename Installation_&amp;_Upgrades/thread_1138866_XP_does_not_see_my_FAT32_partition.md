---
title: "XP does not see my FAT32 partition"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Lovok on 2009-04-26
Here is my setup : 

/dev/sda1 : XP (NTFS)

/dev/sdb1 : /media/disk (FAT32)
/dev/sdb2 : / (ext4)
/dev/sdb3 : /home (ext4)
/dev/sdb4 : swap

I did the partitions during a fresh install of 9.04. When I am booted in XP, I can't see my FAT32 partition. 
I read elsewhere on the forum that this is a bug with GParted, but I also rewrote the partition table using cfdisk. I chose Win FAT32, not Win FAT32 (LBA).

Is it possible for this set up to work, or should I set the FAT32 partition on my XP hard drive ?

Thanks.

---

