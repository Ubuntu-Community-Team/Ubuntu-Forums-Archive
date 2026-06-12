---
title: "I want to Uninstall Ubuntu on USB HDD that doesnt have anyother OS"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by tjeremiah on 2009-03-04
I want to uninstall ubuntu on a USB HDD that doesnt have another OS on it and also when I go into my regular HDD that has windows, it doesnt recognize the USB HDD so I cant remove it from there. I also dont have a LIVE CD nor a Windows CD. I need help removing Ubuntu inside Ubuntu.:(

---

### Post by Gen2ly on 2009-03-04
tjeremiah, 

A good tool to use is fdisk.  Be warned though fdisk is a very powerful tool.  Make sure you know the kernel device name for the drive, type "fdisk -l" to see available partitions and then "fdisk /dev/sda" (or whatever that hard drive is).  Fdisk is pretty easy to use, d - deletes, a - adds.  So delete the Ubuntu partition and add a new one.  w - writes, q - quits.  If you want to add another linux distro you can format the net partition with mkfs.ext3 (or whatever type of partitioning format you want) /dev/sda1.  Or if you're don't want to use command lines tools install gparted.

---

### Post by tjeremiah on 2009-03-04
> **Dirk.R.Gently said:**
> tjeremiah, 

A good tool to use is fdisk.  Be warned though fdisk is a very powerful tool.  Make sure you know the kernel device name for the drive, type "fdisk -l" to see available partitions and then "fdisk /dev/sda" (or whatever that hard drive is).  Fdisk is pretty easy to use, d - deletes, a - adds.  So delete the Ubuntu partition and add a new one.  w - writes, q - quits.  If you want to add another linux distro you can format the net partition with mkfs.ext3 (or whatever type of partitioning format you want) /dev/sda1.  Or if you're don't want to use command lines tools install gparted.

how do I enter all of this and where?

---

### Post by cariboo on 2009-03-05
If you go to XP disk management tolls you should be able to clear out the partition. It will say the partition  is unrecognizable, so you should be able to delete it and repartition.

Jim

---

### Post by tjeremiah on 2009-03-05
> **cariboo907 said:**
> If you go to XP disk management tolls you should be able to clear out the partition. It will say the partition  is unrecognizable, so you should be able to delete it and repartition.

Jim

the HDD only has one OS and that Ubuntu. I dont have windows on it to do that. I tried hooking up the HDD via USB on a computer that has windows but its as if it isnt there.

---

### Post by zvacet on 2009-03-05
When you start your comp do you see GRUB and whitch OS is first if you do?If it is Ubuntu then you can use [this]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe") method.For unistalling Ubuntu you will need [Gparted live CD.]("http://gparted.sourceforge.net/")

---

### Post by bubwitmaingay on 2009-03-06
MS Windows cannot identify ext2 or ext3 partition ID (Linux Partition System), thus your HDD will not open in windows. The best thing to do is use GParted, fdisk or cfdisk in Linux then change your partition ID to FAT32 or FAT16. These partition IDs can now be identified by windows. 8)

---

### Post by tjeremiah on 2009-03-06
> **bubwitmaingay said:**
> MS Windows cannot identify ext2 or ext3 partition ID (Linux Partition System), thus your HDD will not open in windows. The best thing to do is use GParted, fdisk or cfdisk in Linux then change your partition ID to FAT32 or FAT16. These partition IDs can now be identified by windows. 8)

thanks. Ive give it a go and let you know if things went smoothly.

---

### Post by tjeremiah on 2009-03-06
thanks everyone , got it to work :D

---

