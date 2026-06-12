---
title: "newbie question: HDD space"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by krusbjorn on 2005-03-05
Mornin'

I just installed a second hard drive into my comp, and eventually understood how to partition it and mount it (im totally new to linux). at the moment, it's just mounted at /home/johannes/test since i really havent figured out where i want it yet. 

on to the question: the HDD is 120gb, but when i rightclick the test folder in nautilus and check free space, it says 114.5gb. 

the partition i made is 'primary'. although, i read somewhere that if i added an additional HDD, i should make an extended partition. i tried to make an extended partition (hdb1) but then i couldnt mount it, the error message was something like "are you sure you're not trying to mount an extended partition?". so i google some more, and found out that partitions 1-4 are reserved for the primary partitions, meaningi should make an extended partition hdb5. but in fdisk, i could only choose 1-4, even if i was creating an extended partition. so i just made a primary partition and hoped for the best.

anyways, does anyone know if its the partition thing or something else i have done, is the problem here? or is this just how it should be? 

btw, the partition is using reiserfs.

thanks for your help!
 -johannes

---

### Post by alastair on 2005-03-05
Making it primary is fine. The partition types are per disks i.e. 4 primary PER disk only.

So one primary on hdb is OK.

The disk space difference is normal - filesystem overhead (and the disk manufacturer giving max. theoretical).

If you want to se the partitions only :

fdisk -l /dev/hdb

---

### Post by krusbjorn on 2005-03-05
thanks :D

---

### Post by kafton on 2005-03-05
If you make an extended partition you cannot mount it or even write to it. You have to make logical partitions in the extended partition. Logical partitions start from 5 and go on up. That way you can break a very large drive into smaller pieces to keep data separate.

Ed

---

