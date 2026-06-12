---
title: "Clone 2TB to 4TB"
date: 2017-08-04
forum: Hardware
---

### Post by vhinz on 2017-08-04
Hi,

I have an Ubuntu (14.04 server) system with 2TB HDD which I would like to upgrade to 4TB HDD.  Using Acronis, it successfully cloned the drive but still have retained the 2TB.  

Using GParted LiveCD, I was able to unlock and tried to extend the LVM partition but is getting an error on which I think related to MBR to GPT conversion.  Still using GParted, trying to convert msdos to gpt but it might delete the data.

Even after converting to GPT (with a blank disk) then re-clone again, I was back to square 1.

Is there any way I can do this easily?  Step by step guide would be nice :D

Thanks in advance.

---

### Post by mastablasta on 2017-08-04
what is on the drive? data? if so then you could probably just copy it all ot new drive rather than clone

i think MBR supports only up to 2 GB or close to that. if you clone you also clone the MBR so ofcourse you have the same issue as first time.

---

### Post by oldfred on 2017-08-04
You cannot clone from MBR to gpt.
But if you cloned as MBR, you converted 4TB drive back to 2TB. And  cannot have both drives connected at same time when you reboot as you  would have duplicate UUIDs which is not allowed.

Often then easier just to reinstall Ubuntu and copy your data from /home. If a server you may need to copy other server related folders in / depending on what applications like data base or web applications you have installed.

I would suggest partitioning new drive as gpt and use cp -a to copy data.

---

### Post by vhinz on 2017-08-05
I was afraid of going that route (copy all).  The drive is a backup of an old Ubuntu/Zimbra server we had.  The backup was on a newer Ubuntu - Zimbra combination but I had some configurations set-up which I'm not sure I can re-do.  I'm also afraid that the IM part of Zimbra (Zextras) would be gone.

---

### Post by mastablasta on 2017-08-07
in that case clone the 2 GB drive and then create another 2 GB partition on 4 GB drive. then use symlinks to connect the two.

if you go the copy data way, you should be able to can copy configurations just fine and it should work as the original one. i had a USB stick with server OS die on me (ajenti + RAID1 + owncloud) and the backup image i had was not good. but luckilly i managed to pull the config files out of the compressed backup image. so what i did then was a a new install to a new USB stick and then i moved the configuration files to new drive (overwriting the default ones). now we are back where we were.

---

### Post by oldfred on 2017-08-07
You cannot clone to 4TB drive & create another 2TB partition with MBR.
You could clone, convert to gpt, add bios_grub partition which would be required for grub to reinstall on gpt and then resize or add additional gpt partitions.

Normally if you clone to a new drive and keep old drive, you also have to manually change UUIDs of all partitions on one drive or the other as duplicates are not allowed.  If you want drive you change UUIDs on, you have to reinstall grub, edit fstab and perhaps a few more places update install with the new UUIDs. Why I normally suggest new install and copy data.

---

