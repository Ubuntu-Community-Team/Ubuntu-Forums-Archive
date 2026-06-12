---
title: "Sorry, you probably get this all the time"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by theironbadger on 2006-02-21
I am new to Linux, I am trying to put Ubuntu on a Toshiba M30 laptop.  My problem is getting it to work with GRUB for a dual boot XP system.  I partitioned with Partition Magic, and made sure that it didn't set the windows partition to hidden.  When I install GRUB to the MBR windows doesn't like it and after trying to go back it tells me that autochk is not found and resets.
  I managed to fix this problem last time by formatting the master boot record and then setting the windows partition to active manually.  I was hoping that someonw could explain to me how to make the GRUB work with XP, I have found many articles but most of the time they don't tell you how to fix it or tell you to do something I have no clue about.

  Thanks.

---

### Post by orev on 2006-02-21
I realize this is not really what your asking....but:

Why did you use Partition Magic?  The ubuntu installer will set up the partitions (to whatever size you want) and get the GRUB boot loader going with no setup.

From your post, it is not really clear to me if you are able to boot into Windows, but if you can, and it were me, I would work toward undoing the changes you made with Partition Magic and/or changing the Windows partition to the whole disk, and then using the partitioner in the ubuntu installer - it works great!

---

### Post by theironbadger on 2006-02-21
doesn't really solve the problem with the grub....
It is partitioned well enough to work, but won't.


I finally got into windows by destroying the linux  partition.

---

### Post by theironbadger on 2006-02-21
ok, I installed and partitioned from the cd.  I have no clue why, but it seems to magically have fixed the problem and now it works.  I don't know why.  I don't know about it being great, but it works.  I would rather it was more clear.

Now I just have to fix my touchpad.

---

