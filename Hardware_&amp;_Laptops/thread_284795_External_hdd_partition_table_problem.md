---
title: "External hdd partition table problem"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by stoommans on 2006-10-26
Hi,

I recently bought a Scythe kama connect scups-1000 to transfer data 
from an old IDE drive via USB to my computer. It's just a IDE--> USB interface. When i attach an older ~850 mb drive to it, Ubuntu recognizes the drive, and even shows it in the System->administration->Disks tool. However, it can't/doesn't read the partition table. sudo fdisk -l also gives something like "partition table doesn't exist"

The drive itself functions perfectly, in another pc it was the boot drive, and win98 still boots from it.

So, any ideas how i read the partition from the disk?
The disk is mounted as /dev/sda, and is partitioned as 1 850 mb large fat32 partition.

Thanks in advance,

~Stoom~

---

