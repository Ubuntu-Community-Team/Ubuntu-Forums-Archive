---
title: "Failing at Partitioning"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by jwilcox746 on 2009-05-03
Hey All,
 
I'm trying to install Ubuntu on a Dell server; PE860. I'm having nothing but trouble. I'm using the onboard SATA controller, has 1GB ram. I've tried installing 6.06, 8.04, 8.10 all with the same error; "failed at step: Install Base Image". 
 
I've tried the following HDD's, WD160GB, WD250GB, WD1TB and an WD80GB. The only way I can get the install to work is if I do a basic / and Swap partition. Installation fails if I try to setup the following partitions; 10GB /var/run, 10GB /var/lock, 10GB /dev, 10GB /dev/shm and a 150GB /data.
 
It's as if the number of partitions, or the size of them is somehow hitting a hard limit, but I cant find anything documented that would prove this. I'm using a EXT3 file system on them, with the default block size, that wouldn't seem to be an issue.
 
Just as a side note, I had the exact same trouble on a Dell SC440 as well. Any input at all would be helpful.

---

### Post by JK3mp on 2009-05-03
Are you installing server version of ubuntu? And i don't think your HDD would have anything to do with it ;). Try just the default setup routine.

---

### Post by Moop on 2009-05-03
You're limited to four primary partitions and may be running up against that limit. You could try creating logical partitions inside a extended partition. 

I'm assuming you have a good reason for wanting those partions, if not then I'd just use the standard setup or maybe a separate home and data partition.

---

