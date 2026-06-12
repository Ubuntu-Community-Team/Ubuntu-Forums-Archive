---
title: "Windows + Ubuntu"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by headbuster on 2009-11-04
Hello all
I want to ask you some questions so I can be sure that what I am doing is OK.
I want to reinstall my windows and I am thinking of installing ubuntu too. I have installed ubuntu once before but after tweaking my hd so it had space for it. But now I am doing a clean install:

First windows and than ubuntu. So my questions...
My hd is 150 gb. I will make 40GB drive for windows and a 70gb drive for my stuff ( disk C: windows disk D: games...) and I will leave unpartitioned space 40 gb for ubuntu >> After I have installed and configured windows I will than try to install ubuntu. DO I have to make some separations to the 40gb space because once I tried to install Open Suse and it wanted to separate the drive to 15843658 pieces...
Another question. What about the drivers?
I have nvidia9800gt and Intel Pentium D (asus p5pl2)
Do I have to install something?

Thats for now. Thanks in advance :)

---

### Post by kyuubi777 on 2009-11-04
that's fine, and yes, order of boot should be linux last to preserve grub BL.
i would recommend making two swap partitions adding up to between 1/2 your ram space - 1x ram space at the end of the hdd map

---

### Post by headbuster on 2009-11-04
> **kyuubi777 said:**
> 
i would recommend making two swap partitions adding up to between 1/2 your ram space - 1x ram space at the end of the hdd map

I couldn't understand this part 
(sorry but I am new to ubuntu)

---

### Post by kyuubi777 on 2009-11-04
during the installation process u will come across the partitioner and it will allow you a few options.. for you, you will need to specify partitions manually- when you choose this select the free space w/ your cursor and click new.. then choose the type of partition (select linux-swap) and select the location (end).. i made just one @ 1GB.. once this is done, then select the empty space left.. 39GB or whatever and create a partition using ext4 file system and that should be it (make sure to chose "format" option - although it should automatically select when you choose to make the ext4 partition... ubuntu will then install on that partition when u click next  (also, mount point must be set to "/" w/out quotes.. not sure how new you are so i am giving excessive info :D)

and you will get generic drivers upon boot. (work like magic)  should work fine for your system

---

### Post by headbuster on 2009-11-04
Ahhh that's more like it :) !
Thank you very much! I will start now :P

---

### Post by kyuubi777 on 2009-11-04
hope it goes well, comment back w/ the results later :)

---

