---
title: "gparted and XP"
date: 2008-07-22
forum: General Help
---

### Post by Paul Earland on 2008-07-22
Wanting to remove XP. Have gone into gparted which comes up with these partitions on my hard drive. NTFS, EXT3, Extended, Linux Swap, FAT32 and Unallocated. Do I just remove NTFS, want to keep FAT32 as this is where my work is stored.
Thanks.
Paul

---

### Post by tmetzcc325 on 2008-07-22
If you are sure that there is nothing on your NTFS partition that you want to keep, you can delete that partition.  Then, you can edit the grub menu to remove the option to boot into XP at /boot/grub/menu.list.

---

