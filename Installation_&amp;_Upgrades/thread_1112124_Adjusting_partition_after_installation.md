---
title: "Adjusting partition after installation"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by photogenius_uk on 2009-03-31
I've installed Ubuntu and partitioned my hard disc during normal installation into partitions to enable me to still use Vista.
I'm pretty new to all computer manipulation but can anyone explain how I can now adjust the size of the Ubuntu partition as I have allocated too much of my disc to it.  Please make your answer easy to understand and to use if you're going to give my instructions!  Thanks.

---

### Post by logos34 on 2009-03-31
You'll need to boot the ubuntu live cd and use gparted there, since / cannot be mounted during resize. (System>admin>partition editor)

these links should walk you thru it:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

good luck

---

### Post by Linoobius on 2009-03-31
photogenius,

You cannot make changes to a mounted partition so you will have to reboot from the ubuntu live CD (select the option to try without any changes to your computer), once booted open a command window and type gparted this will launch the partition editor. Once the GUI loads, click on your ubuntu partition to select it and then right click on it to display the context menu which will give you option to resize the partition. Adjust the size to your pleasure and then do the same for the widows partion to grow it into the space you just freed up. Once you have everything looking right, click the Apply button at the top. This can take a while as either all of your ubuntu data or all of your windows data will have to be moved depending upon which partition was first on the disk. It should go without saying but... make sure to back up any critical data prior to mucking around with your partition table. You never know, if something happens to get hosed, at least you won't be totally out of luck.

I see logos34 just beat me to the punch and provided some excellent links so just make mine a ditto...

Linoobius

---

