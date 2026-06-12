---
title: "Hard drive issues"
date: 2010-08-06
forum: Hardware
---

### Post by Dj TweeX on 2010-08-06
ok so i accidentally screwed up the partition table on my hard drive like twice in a row. so i couldn't recover it. i used ddrescue to make an image of the drive. the only problem is i cant mount the image cause it doesn't have a partition table. but the data is still there!!!
Can anyone please help me?!?!
any info you need just ask!
Gabe R.

---

### Post by gallifrey on 2010-08-06
Have you tried Gparted? It can delete whatever is on there, and create a new partition table. If you can't boot, there is a bootable version.

---

### Post by Dj TweeX on 2010-08-09
i should be more specific. i need to rebuild the partition table. so the data could be accessed...

---

### Post by Dj TweeX on 2010-08-11
bump please.

---

### Post by linux18 on 2010-08-11
so you have an iso or img of the data?

---

### Post by Fludizz on 2010-08-11
Recreating the partition table is going to be tricky... You'll either need to have a very intelligent recovery program or you need to know exactly at which blocks which partition starts and where they end.

You could try to use a data recovery program to recover data from the 'lost partitions' and write that data to a backup disk. Then format the drive and create the partitions again and restore the recovered data to them, that's probably the easiest way to do this as far as I know (never had this problem).

---

