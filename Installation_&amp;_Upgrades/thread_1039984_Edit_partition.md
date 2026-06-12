---
title: "Edit partition"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by meddyliol on 2009-01-15
Hi, I am a complete newby to Linux, I have tried various different ones but am having a problem with installing Ubuntu 11.1 on my Vaio Laptop. It runs OK from the disk its the hard drive installation that's the problem. When I get the screen to prepare partitions which I have to do manually because for the time being I need to dual boot into Windows XP, the 'Use As' gives me various options such as 'Ext3 journaling file system' etc which do I choose? The other problem is the 'Mount point', again there are several choices such as '/', '/boot' etc. Again, which one do I choose?

Any help would be appreciated.

Thanks

Brian :guitar:

---

### Post by Bucky Ball on 2009-01-15
Okay, you need:

/
/home
/swap

... as a basic setup. Make them all ext3 except the swap partition, which needs to be set as 'swap' and will deal with itself.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

[B]                                 [B]On the last link, go to the section heading: Start of the partitioning stage of the install

Naturally, avoid going anywhere near your ntfs partitions if you want to keep them.
[/B][/B]

---

### Post by meddyliol on 2009-01-15
Thanks for the info Bucky Ball. The two links are very useful although I haven't had a good butchers at them yet. Am in the process of installing now so will see what happens.

Cheers blue

Brian ):P

---

### Post by meddyliol on 2009-01-16
I decided to download and install Ubuntu 8.04 which I installed and I must say I am very impressed with it. For me it is the best of the bunch (so far). 

Cheers me dears

Brian :guitar:

---

### Post by Bucky Ball on 2009-01-16
No problems. Enjoy!

---

