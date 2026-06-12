---
title: "device for hard drive partition not there."
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by azarhal on 2006-06-03
I have a problem with one of my hard drive.

Both fdisk and qtparted show all the device partitions info for my hda  but inside of /dev/ there's only hda and there's no /dev/hda1, /dev/hda2 and /dev/hda3.] ](*,) 

I can also format new partition on my hda with qtparted and once I reboot in XP, it see them (when they are in fat32).

hardward info:
this drive have problem.
hda : Maxtor 160 gb, 16mb cache.
hda1: ntfs Win XP - 40 gb -
hda2: ntfs "space" - 40 gb -
hda3: fat32  - 10 gb - 
rest is unformated.

This drive work correctly.
hdb: Western Digital - 40 gb -
hdb1: fat32 - 30 gb - To share stuff between Kubuntu and XP
reste is my linux installation (Kubuntu) - 10 gb - in all.

So, what might be causing the none existance of my hda partition inside the dev folder.

- Because it's not formated at 100%.
- Problem of hardware regconition.
- dumb user.
- others?

And how can it be solved?

Thanks for the future help.

---

### Post by azarhal on 2006-06-03
forgot to subscribe. :-|

---

### Post by azarhal on 2006-06-05
Ok, now i'm able to mount the partition, looks like linux don't like not totally formated hard drive...and that my boot sector on hda is somehow busted, despite the fact that Win XP don't complain about it.

---

