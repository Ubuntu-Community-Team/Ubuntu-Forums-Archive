---
title: "Hard Drive Partitioning Problem on D610"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by seamustry on 2008-02-24
I'm installing Ubuntu as dual boot with Windows XP on my d610 laptop.

When I try to do the partition step in the installation, I specify how much space I want to partition, the installer works for a few minutes and give me error that for some reason hard drive can't be partitioned. I used the minimum space that it recommended to me. Can someone please help??

Thanks.

---

### Post by konungursvia on 2008-02-24
Did you define the new partition (or one of the new partitions) as "root"? This is represented by the slash (/). One must be root. If you can't see what I mean after trying the partition step again, go to windows, google "gparted iso" and download the ISO (disk image) for the program "GPartEd" (Gnome Graphical Partition Editor). You may also need to download "ISOburn" from Tucows to burn the disk image. Boot into gparted from the new gparted disk and do your partitioning there. Make sure you defragment the windows hard drive several times first! Defrag it untli it looks like there is lots of white space in one place on the disk data bar graphic. I suggest in Gparted making one partition root (/) about 10 GB and one "swap" about 2 GB.

---

