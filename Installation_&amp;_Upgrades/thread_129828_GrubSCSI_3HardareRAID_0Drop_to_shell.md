---
title: "Grub/SCSI_3/HardareRAID_0/Drop to shell"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by foodcoman on 2006-02-14
Grub fails to hand off after Uncompressing Linux and Loading....Please wait.

The Hardware is a Compaq Proliant DL380 with a Compaq SCSI RAID controller with 6 drives.  RAID_0 currently, I have tried RAID_5 also.

After, Loading Please wait....
/dev/cdrom: open failed: no medium found  (PS I can boot CD to the install screen should I choose to put it in at this point)
Unable to find volume group "Ubuntu"
Alert! /dev/mapper/Ubuntu-root does not exist.  Dropping to a shell!

I have installed with or without LVM  example: I let LVM install /dev/ida/c0d0 #1 ext #5 swap

Installs Grub to (HD0)  After reboot I get the above.

Any tips would be appreciated.  :-k

---

### Post by foodcoman on 2006-02-14
Testing this thread to see if it works for me.

[http://ubuntuforums.org/showthread.php?t=82466&highlight=proliant+dl380](http://ubuntuforums.org/showthread.php?t=82466&highlight=proliant+dl380)

---

### Post by foodcoman on 2006-02-14
The above forum update worked like a charm once you figure out exact location and syntax.... I think for the benefit of others I will clean it up give credit to original author unless he wants to do it.

---

