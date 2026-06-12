---
title: "Ubuntu corrupts flash drives"
date: 2017-06-29
forum: Hardware
---

### Post by gabolein on 2017-06-29
So somehow I've sticked three flashdrives into my tower PC that runs Ubuntu and after a while they didnt show anymore. Upon plugging them into my Windows laptop it said they required a format. Does anyone have any advice?

---

### Post by Autodave on 2017-06-29
13 machines running Xubuntu and a handful of USB sticks: USB 2 & 3, 1/2 G to 64 G and never a problem with any of them.

Either you got a bunch of bad sticks or perhaps the power supply in that tower is putting out the wrong voltage to them.  A motherboard could possibly cause that, but would be very rare.

---

### Post by gabolein on 2017-06-29
Umm the sticks were working fine and in two years I never had issues with the motherboard. On one of the sticks I had a bootable Ubuntu and that one is impossible to reformat somehow (tried gparted, can't create a primary partition). 
If it helps: before being corrupted a stick rejected anything I put on it cause it was read only. I used that stick before and it worked just fine.

---

### Post by C.S.Cameron on 2017-06-30
Sticks made with Startup Disk Creator end up formatted ISO9660. This can be hard to format normally.
Mkusb has a wipe function that can renew a flash drive quickly.

[https://help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by yancek on 2017-06-30
If you have an iso on a usb stick, it is read-only by design and if you cannot manage to format it you can either use a variation of the 'dd' command to overwrite or create a new partition table from GParted under the Device tab.  Make sure you have the correct device so you don't delete/overwrite your OS.

---

### Post by gabolein on 2017-06-30
> **C.S.Cameron said:**
> Sticks made with Startup Disk Creator end up formatted ISO9660. This can be hard to format normally.
Mkusb has a wipe function that can renew a flash drive quickly.

[https://help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

I used it, wiped it, and it's still unable to create a partition table

```
Error: /dev/sdd: unrecognised disk label
mkfs.fat 3.0.28 (2015-05-16)
/dev/sdd1: No such file or directory
 Failed :-( 
  mk_msdos: could not create MSDOS partition table and FAT file system 
Wait 5 seconds and a little more ...
Error: /dev/sdd: unrecognised disk label
Model: TDK LoR TF10 (scsi)
Disk /dev/sdd: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown

```

---

### Post by Kris_M on 2017-06-30
> **gabolein said:**
> So somehow I've sticked three flashdrives into my tower PC that runs Ubuntu and after a while they didnt show anymore. Upon plugging them into my Windows laptop it said they required a format. Does anyone have any advice?

I would suggest that they are no longer MBR or GPT. I would recommend you offline boot to GPARTED(probably on a thumb drive), with the wayward usbs (one at a time) also plugged in, and create either GPT or MBR on it and then create a formatted partition of whatever you want - probably FAT32. I have done this with USB flash drives and SDcars through a reader. - this is particularly when you use a SDcard as internal extended storage on a phone, and then later decide to use it as external storage. Yes you will lose anything on them.

---

