---
title: "Save Ubuntu 8.10 settings to a USB drive."
date: 2008-10-30
forum: General Help
---

### Post by chris122380 on 2008-10-30
How can I save settings to a USB drive with out installing ubuntu to a USB drive. I would just like to use the USB drive to store my Ubuntu 8.10 settings as the drive isn't big enough to install Ubuntu. I can use the Ubuntu Live CD but would like to save it's settings to the USB drive. How do I do that?

---

### Post by C.S.Cameron on 2008-10-30
You can format the USB drive to ext3 and label the partition as home-rw.
Plug in the flash drive, then when you first boot the Live CD hit F6 then type "(space)persistent".
This will put your home folder on the flash drive and you can save settings.
You can also add an ext3 partition labeled casper-rw to the flash, this should save your downloaded applications, but does not always work.

---

### Post by chris122380 on 2008-10-30
Has to be a Linux Partition then and can't be a Fat32? How do I create a Label in Linux?

---

### Post by C.S.Cameron on 2008-10-30
I have not had luck with FAT32 persistent partitions.
When using gparted you will find a space at the bottom of the page called Label.
Or you should be able to right click the partition and select Label.
I use the gparted live CD as gparted on the Ubuntu Live CD or in Ubuntu does not like naming a partition casper-rw.
The Live CD is ok with labeling a partition home-rw, if all you need is a persistent home.

---

### Post by jshx87 on 2008-11-06
what is the minumin size for this partion? can i still save data on the flash drive?  im using a laptop with a fried hard drive.  havent gotten the time to buy a new one.  id like to be able to run the livecd and have my own settings and store some of the patches/addons.

---

### Post by shodai100 on 2009-07-12
> **jshx87 said:**
> what is the minumin size for this partion? can i still save data on the flash drive?  im using a laptop with a fried hard drive.  havent gotten the time to buy a new one.  id like to be able to run the livecd and have my own settings and store some of the patches/addons. I would put at least 1GB. I would add more if possible.

---

