---
title: "how many and type of partition i need"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by guidenhelp on 2009-11-03
hello friends,
i m using Samsung VM8000 laptop with is bit old one, i using 256 mb RAM and 80GB hdd. i had run Ubuntu 8.04 and then 9.04 successful but now i want to install 9.10. previously i was always install by default partition that is just one ext3 and one swap. i have install windows xp sp3 as well. So i used my disk like this.

 |-----NTFS 15gb----| |----free for ubuntu 15gb---| |--backup 50gb--|

some of my friends told me that i need some specific partition for my Ubuntu. so instead default how i made manual partition for ubuntu for better security and practice. 
thanks,

---

### Post by zvacet on 2009-11-03
I believe that your friend have in mind separate home partition.You have two options(maybe more but now I can think just about this two):

1.during install shrink your backup partition to make space for home partition.in that case you can give to root max 10GB and maybe same for home.

2. You are already have backup partition so maybe you can stay with just root and swap and do  backup of your home to backup partition.For that read [this.]("http://www.psychocats.net/ubuntu/backup") That way your settings and files will be safe on backup partition.

---

