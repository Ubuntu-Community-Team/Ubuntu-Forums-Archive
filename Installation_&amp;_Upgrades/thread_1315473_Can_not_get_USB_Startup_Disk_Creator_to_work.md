---
title: "Can not get USB Startup Disk Creator to work"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2009-11-05
I have Ubuntu 9.10 Netbook Remix burned to a CD and I have a Kingston 2 GiB flash drive.  The flash drive held UNR 8.10 which I removed to make space for UNR 9.10. 

When I run "USB Startup Disk Creator", I get a notice saying "Unable to determine the partition number". I ge no choice in how to define a partition number for the flash drive.

So I am asking for help.

---

### Post by Mighty_Joe on 2009-11-05
Fire up the Partition Editor ([http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")), create a new "msdos" partition table (the USB Creator will not work without one), then create a new FAT32 partition.

---

### Post by jlh68 on 2009-11-05
More info:  UNR 8.10 flash drive was screwed up (and still is)  I got out a _new_ 2GiB flash drive and I was able to load onto it Ubuntu Netbook Remix 9.10.  I will later, after backing up all my data on my netbook, try to do a clean install of UNR 9.10 on my Acer One netbook.

Now to get the old flash drive straightened out so it will be usable for file storage.

---

### Post by jlh68 on 2009-11-05
Well Mighty_Joe, as you can see I used a new flash drive and got it to work.  I was playing with GParted prior to reading your post, but I did go and set it up as FAT32 and I believe it is now restored to a usable device.  I will be able to use it for file transfers between computers and storage of files.

Thanks for your help.

---

