---
title: "Qtparted, Dell latitude x1, dual boot setup"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by Ultrashogun on 2006-11-17
My goal is to set up my latutude x1 as a dual boot, with windows XP and Ubuntu edgy eft. I started of booting with the rescue CD to use Qtparted and partition my drive. I wanted to partition my 40GB drive as follows: NTFS(17gb), ext3(15gb, swap(1gb), FAT32(7gb). The FAT32 is intended as a drive both systems can read.

My problem is the following, when I start Qtparted it displays the windows NTFS partition(40gb) and two other partitions that Im really not sure about. One partition is hidden, has nothing on it and is around 15gb large. The other partion is a virtual partition, 70 Mb large and is FAT16.

I seems that QTparted will only let me have 4 partitions, because after I designate three it becomes impossible to designate another, which is what is holding me back on installing Ubuntu.

Im not sure what the FAT16 partition does, I guess it has MSDOS for maintenance reasons. Im not sure if I should delete it, or how to delete it.

Any help greatly appreciated.

---

