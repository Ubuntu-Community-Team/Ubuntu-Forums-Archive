---
title: "Setting up new partition"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by ellalan on 2009-01-06
I am going to try installing windows7 beta and I need some help regarding the partitioning.
These are my specs:
OS: Ubuntu Hardy Heron
HDD: 160GB
RAM: 2GB
Graphics:GeForce6150SE nForce430
I would like to allocate 50GB for the windows partition,could someone please guide me how to do this.

---

### Post by Tim Sharitt on 2009-01-06
I would suggest using gparted from a live cd. Once you have booted to the live cd desk top, goto System > Preferences > Partition Editor. Shrink whatever partion you choose,or if you have un partitioned pace just use it, and create a new partition.

Besure to backup any important data before doing this. It shouldn't mess anything up, but it is possible and you can't be too carefull.

---

### Post by zvacet on 2009-01-06
From your post it is look that you dedicated entire HDD to Ubuntu.Did you make separate home partition?If you didn´t now is good time to do it since you will go to repartition your HDD.Follow [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.

Second shrink 50Gb and format it as NTFS.That way you will not be confused witch partition to use when you go to install Windows.After windows install you will have to [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by ellalan on 2009-01-14
Thank you guys for the help. Sorry for the late reply,I have been busy setting up this W7 thingy.

---

