---
title: "Help removing windows  and repartitioning"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by cmdrtebok on 2009-04-29
I would like to install Jaunty fresh and ditch my windows partition. Ideally my my 500 GB hard drive would be partitioned in 2 with Ubuntu over a 20 or so GB partition and the rest for media storage. Over the years installing various things on a dell I have many other partitions sda1-6 including ones I don't even use... like the Dell recovery partition. Will simply formatting the hard drive remove all the partition table so I can start from square one? Will this affect GRUB or my boot record? Do I need to manually make a swap partition?

thanks

---

### Post by ahbart on 2009-04-29
It could be wise to backup these dell partitions containing the recovery files. If you ever want to be able to reinstall the original software or if you ever want to sell. Or do you have a recovery dvd also? 
If you made a backup of your data a clean install and deleting every partition would be best. 
I would choose:
/ 20 gb
/home  rest excluding:
swap (1,5x memory in your pc)
Ubuntu will install grub on /dev/sda.

---

