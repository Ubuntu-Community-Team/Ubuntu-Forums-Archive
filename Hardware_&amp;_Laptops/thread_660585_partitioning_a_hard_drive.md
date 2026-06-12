---
title: "partitioning a hard drive"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by siriusblack711 on 2008-01-06
i have a hard drive with 2 main partitions. first one is drive C with 80 GB of space and the second drive D has 10 GB of space. i want to divide drive C so that it now has 65 GB of space and a new partition of 15 GB is created. but when i select drive C now create new partition option is unavailable in partition magic 8. so i thought will resizing the partition achieve the same purpose? NOTE: the C drive is the first drive. it is not the right-most drive(D) available.

---

### Post by logos34 on 2008-01-06
Defrag C: a few times and run chkdsk (w/repair option).  Then use gparted on the ubuntu live install cd (system>admin>gnome part. editor) to shrink c: down by 15gb.  Create new ext3 or just go straight into installation and choose 'guided' install on largest continuous free space.

---

