---
title: "External Harddrive"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by Sobriquet on 2007-08-15
Okay so basically now I have most things up and running after recently installing Ubuntu. One of the things that still isn't right though is that my External Hard drive isn't recognised automatically and I am unsure on what I had to do to get it to show up. 

I have a Seagate External Harddrive, im not sure the size 320GB I think and im pretty sure in Vista it said it was FAT32 or something similar.

I read some other threads and found a few commands into the terminal, when I typed 
```
lsusb
```
it does show up.

Ive read in other threads about people mounting it manually which im assuming is what I have to do?

Thanks for your help :)

---

### Post by barisy on 2007-08-15
Welcome to the club :lolflag: i've been tryin' to find the solution since monday :) anyway you may search the term USB mount and you can read what i've done so far may be it can work on your Ubuntu ..
Good Luck buddy ..

---

### Post by Sobriquet on 2007-08-15
> **barisy said:**
> Welcome to the club :lolflag: i've been tryin' to find the solution since monday :) anyway you may search the term USB mount and you can read what i've done so far may be it can work on your Ubuntu ..
Good Luck buddy ..

Thanks for the tip I will do now.

The things ive managed to fix with the help of this forum so far are:

-Dualbooting Ubuntu with Vista
-Getting my internet up and running
-Getting flash for my AMD64 version of Ubuntu

To go now I have just

-pick up my ext HDD
-maybe install Nvidia drivers but thats no biggy

---

### Post by vanadium on 2007-08-15
USB drives should be automatically mounted under /media when you plug them in. However, indeed, try to see if you can mount it manually. Do a search for howto's on mounting but basically it ammounts to

* creating a mount mount: sudo mkdir /media/mymountpoint
* mounting your partition there: sudo mount /dev/sdc1 /media/mymountpoint

supposing your partition is named /dev/sdc1 and you want to mount it under /media/mountpoint

sudo fdisk -l

will list all the partitions that your system recognized (wether mounted or not). It will reveal the name of the partition you want to mount (if the system recognises it).

mount

will list all that's currently mounted.

---

### Post by Sobriquet on 2007-08-15
> **vanadium said:**
> USB drives should be automatically mounted under /media when you plug them in. However, indeed, try to see if you can mount it manually. Do a search for howto's on mounting but basically it ammounts to

* creating a mount mount: sudo mkdir /media/mymountpoint
* mounting your partition there: sudo mount /dev/sdc1 /media/mymountpoint

supposing your partition is named /dev/sdc1 and you want to mount it under /media/mountpoint

sudo fdisk -l

will list all the partitions that your system recognized (wether mounted or not). It will reveal the name of the partition you want to mount (if the system recognises it).

mount

will list all that's currently mounted.

What sort of thing would I put instead of "mymountpoint" ?

---

### Post by XTREEM|RAGE on 2007-08-15
Wel to use our external hdd you first need to remove it from the windows os. Have you done that?

---

### Post by Sobriquet on 2007-08-15
> **XTREEM|RAGE said:**
> Wel to use our external hdd you first need to remove it from the windows os. Have you done that?

What do you mean remove it from Windows? It plugs in through USB, I can detach it whenever I want :confused:

---

