---
title: "usb stick not recognized in standalone dvd player"
date: 2008-08-20
forum: Hardware
---

### Post by b-llwyd on 2008-08-20
I have a sandisk micro cruzer 4GiB that used to work fine in my standalone dvd player (dvr), but I had to use the usb stick in a rescue operation for my netbook wherein it was formatted as ext2. Well, now I want it back to its former state, but nothing I throw at the stick will make it readable in the dvr.

I have used cfdisk to change partition type from Fat16, to W95 Fat16 (lba), Fat32, win 95 Fat32, etc. And I've been trying to format the usb stick with mkfs.vfat and mkfs.msdos, but to no avail! Is there a magic trick to making this work in linux? I'm a full-time linux user and would not like to borrow my girlfriends winxp if i don't have to. You know what I mean :) I'm sure a formatting from within winxp will do the trick in no-time, as a last resort.

Do I have to mkfs.vfat with some secret switches? sectors/cylinders, etc?

thank you!

---

### Post by b-llwyd on 2008-08-25
Ok, I formatted it in windows XP, but it still doesn't work. Most likely because of my fiddling with its partitions (cfdisk). Does anyone have one of these? SanDisk Cruzer Micro 4GB, and can you tell me what partition type it is? (cfdisk /dev/sdX, when mounted) Bootable partition? Size? Are there two partitions?

---

### Post by b-llwyd on 2008-09-16
Ok, it turned out the usb stick had a mini partition that i couldnt see from linux, for some reason. once i used the sandisk program from within windows, i could choose to remove the hidden partition and make it into a normal usb stick. fat32 on it, and everything is now ok!

---

