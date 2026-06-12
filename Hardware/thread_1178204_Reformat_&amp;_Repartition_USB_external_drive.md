---
title: "Reformat &amp; Repartition USB external drive"
date: 2009-06-04
forum: Hardware
---

### Post by mangoes on 2009-06-04
Hi all,

Just got a 1Tb Astone USB external eSATA drive, currently formatted in NTFS.

There are actually 2 main questions:

1) I have to manually mount it using commands like
 ntfs-3g /dev/sdf1 /media/debigusbdisk
, since ubuntu can't mount it automatically (Ibex). Any suggestion for successful auto-mounting? 

2) Planning to reformat it into a couple of partitions, mainly ext3/4 for linux backup and a tiny weeny NTFS/Fat32 for windows backup. What program would you recommend (gparted,fdisk etc) and is there anything I should be cautious about?  Always very nervous when partitioning disks. 

Thanks
ps: for the linux partition, should I stick to ext3 or would you recommend ext4? I heard it's faster but maybe not backward compatible.

---

### Post by bol0 on 2009-06-04
I've got positive experience with GParted, never failed me so far. I even resized the partitions with the data on them and that went ok as well. For backup partitions I would go for ext3 for Linux and FAT32 for Win as you don't need NTFS for backup. FAT32 is also readable/writable form Linux while NTFS rather readable only.

---

