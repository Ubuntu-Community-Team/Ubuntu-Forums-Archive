---
title: "is something wrong with my partitions?"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by graigsmith on 2005-05-07
i did fdisk -l and it printed this.

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         973     7815591   83  Linux
/dev/hda2             974        9729    70332570    5  Extended
/dev/hda5            9487        9729     1951897+  82  Linux swap / Solaris
/dev/hda6             974        9485    68372577   83  Linux

**Partition table entries are not in disk order** 

not in disk order? what does that mean?

---

### Post by Xian on 2005-05-07
> 
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         973     7815591   83  Linux
/dev/hda2             974        9729    70332570    5  Extended
/dev/hda5            9487        9729     1951897+  82  Linux swap / Solaris
/dev/hda6             974        9485    68372577   83  Linux

**Partition table entries are not in disk order** 

not in disk order? what does that mean?
See where hda6 starts at 974 and ends at 9485? And then note where hda5 begins at 9487. So, in disk placement order hda6 actually resides ahead of hda5. Fdisk is listing the partitions in numeric order but is letting you know that the disk order is different.

---

### Post by graigsmith on 2005-05-07
[QUOTE=Xian]See where hda6 starts at 974 and ends at 9485? And then note where hda5 begins at 9487. So, in disk placement order hda6 actually resides ahead of hda5. Fdisk is listing the partitions in numeric order but is letting you know that the disk order is different.[/QUOTE]
 so thats not a bad thing?

---

### Post by Xian on 2005-05-07
AFAIK your system will run fine on that scheme. 
The message in fdisk is informational.

---

### Post by crane on 2005-05-07
[QUOTE=graigsmith]so thats not a bad thing?[/QUOTE]

You just need to put an "out of order" sticked on you monitor. :-P 

LOL just joking !

You shouldn't have any problems as far as I can see either. I think I did the same thing a while back on my test computer.

---

