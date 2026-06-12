---
title: "IDE drives shown as SCSI sda1, sdb1"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by bill45 on 2007-10-24
System P3 1Ghz 384GB RAM FF7.04 normal install never had a problem, runs all my media without fail etc. My IDE drives in old DELL are shown as sda1 and sdb1.   How can I correct this error?  I formatted the drive now known as sdb1 with ext3 file system and attempted to mount it.  System does see sdb1 mounted at media/disk.  How can I mount it permanently my /home/username folder? 

The error referenced in title bar occurred before I made attempt to mount 2nd drive.  I just noticed it while looking at the system monitor! 

Thanks 

Bill
Indy

---

### Post by simonn on 2007-10-24
> 
My IDE drives in old DELL are shown as sda1 and sdb1. How can I correct this error?


I had the same thing when I upgraded to Gutsy. Apparently IDE devices are now using the SCSI drivers which are better, apparently. It is nothing to get worried about and it is certainly not an error.

> 
How can I mount it permanently my /home/username folder? 


Use fstab:  [http://rute.2038bug.com/node22.html.gz#SECTION002270000000000000000](http://rute.2038bug.com/node22.html.gz#SECTION002270000000000000000)

Also, see man fstab.

---

### Post by bill45 on 2007-10-24
Thanks for examples page - Bill

---

