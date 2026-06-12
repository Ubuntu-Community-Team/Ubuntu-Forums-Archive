---
title: "[SOLVED] hardrive mount point varies on each boot-up"
date: 2008-10-17
forum: Hardware
---

### Post by amalafrida on 2008-10-17
2 harddrives in my system, running Gibbon
/dev/sda & /dev/sdb
/etc/fstab calls for mount /dev/sda /mnt/datadisk

after first boot:
fdisk -l | grep '^Disk' yields:
Disk /dev/sda: 160 GB
Disk /dev/sdb: 320 GB

after next boot, they are reversed
fdisk . . .  yields:
Disk /dev/sda: 320 GB
Disk /dev/sdb: 160 GB

HOWEVER . . . 
boot with RescueCD,
fdisk -l | grep '^Disk' yields:
Disk /dev/hdb 160 GB
Disk /dev/sda 320 GB
this report is consistent on each bootup 

with regular bootup, one time the harddrive comes up as /dev/sda and is successfully mounted,
next boot up, drive appears as /dev/sdb and, of course, is not mounted

what's going on?

I'm puzzled why regular operation reports sda & sdb, while RescueCD reports: hdb & sda

I've checked /dev and there is no /hdb device listed on regular bootup

thanks in advance for any help you might offer

---

### Post by jerome1232 on 2008-10-17
As far as hd vs sd goes, a the linux kernel use to refer to pata devices as hdX and sata/scsi devices as sdX, recently it treats them all the same.

To solve the issue with fstab and devices spuriously changing between sda and sdb, refer to them by uuid instead.

use blkid to get a listing of devices and their uuid. The uuid will stay constant no matter how much flip flopping the devices do. If you format a drive or resize it, the uuid will change however.

```
sudo blkid
```

---

### Post by amalafrida on 2008-10-17
Great!  2 boots and the UUIDs remain the same.

What should an fstab line look like using UUIDs instead of 
/dev/sda1 /mnt/data

UUID=xxxxxxxxx /mnt/data ext3 ???????????

---

### Post by jerome1232 on 2008-10-17
Exactly the same just replace /dev/sda1 with UUID=jlsdgoobly-gookjklfslak;

I always put a comment in the fstab so that it's like this

#/dev/sda1
UUID=goobly-gook-foobarjkl;jk;k;jkkljkl;jklkl;j /mnt/mountpoint ext3 (then use whatever options where there before)

---

### Post by amalafrida on 2008-10-17
Hyper-cool.  Reboot is perfect!  Thanks a bunch.  Merci beaucoup!

1,333 posts since Dec 2007?????????!!!!!!!!!!

Man, you must eat and sleep Ubuntu . . . in addition to drinking it!

Your solution was right on point.  Saved me a bit of time and head-scratching.

Ciao . . . from Robert way across in Mississippi

even plugged another UUID into .bashrc for auto mount and umount for my backup data disk function . . . smooth as Camembert cheese!

Thanks again!

---

### Post by sisco311 on 2008-10-17
Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by jerome1232 on 2008-10-17
> **amalafrida said:**
> 
Man, you must eat and sleep Ubuntu . . . in addition to drinking it!


Lol, not really. I do like troubleshooting and will come here in my spare time though. :) (Which since I got laid off is alot of time recently)

---

