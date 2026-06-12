---
title: "[SOLVED] can't mount usb drive"
date: 2008-10-28
forum: General Help
---

### Post by jmd9qs on 2008-10-28
hi,

after trying to install the slackware iso onto my usb drive (to install slack on my laptop w/no cd-drive), i apparently messed up the drive somehow. i can't find it w/ fdisk or df, and it will not auto-mount. weird thing is, Windoze sees the drive no-prob! what else should i be trying here so i am again able to use my drive?

---

### Post by didac on 2008-10-29
Plug it and look at messages in 

    dmesg | tail

Try to mount it manually. Something like

sudo mount /dev/sdc1

dmesg tells you partitions letter -- sdc1 or sdd2, whatever

---

### Post by jmd9qs on 2008-10-29
ok, i ran ```
dmesg | tail
``` after plugging in the drive, here's the output:


```
jmd9qs@jmd9qs-desktop:~$ dmesg | tail
[80818.625707] sd 9:0:0:0: [sdg] Write Protect is off
[80818.625709] sd 9:0:0:0: [sdg] Mode Sense: 03 00 00 00
[80818.625711] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[80818.626849] sd 9:0:0:0: [sdg] 7987200 512-byte hardware sectors (4089 MB)
[80818.627119] sd 9:0:0:0: [sdg] Write Protect is off
[80818.627121] sd 9:0:0:0: [sdg] Mode Sense: 03 00 00 00
[80818.627122] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[80818.627125]  sdg: unknown partition table
[80818.681155] sd 9:0:0:0: [sdg] Attached SCSI removable disk
[80818.681189] sd 9:0:0:0: Attached scsi generic sg7 type 0
```

obviously the 'unknown partition table' is my problem... how can i fix this?

---

### Post by Bob535 on 2008-10-29
have you tried using "gparted"
Its a partitioning program, should be able to reformat and fix the problems...

sudo apt-get install gparted

then it should be in applications > system tools

---

### Post by jmd9qs on 2008-10-29
ok, got gparted (i had qparted but it wouldn't show me the drive; gparted did right after start-up...weird).... since this is a larger drive (3.8GB) what kind of filesystem should i partition it to?

---

### Post by jmd9qs on 2008-10-30
waited too long... had to try it.

so i formatted the usb as a fat-32 (i think that's what it was before)

it wouldn't let me mount it with ```
sudo mount /dev/sdg1
``` so i tried ```
sudo mount -a
```... here was the output:
```
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

what is the problem here?

---

### Post by didac on 2008-10-30
Now that you have reformatted it, when inserting the usb drive do a dmesg | tail again to get the partition letters. mount -a mounts all the partitions in your /etc/fstab but not hotplugged devices (that I know)

/dev/sda1 is the first partition in your hard disk, whatever it is. But it's not likely to be your usb drive. I don't know the problem with sda1. Maybe you can post the contents of /etc/fstab and the results of 

    sudo fdisk -l

Last thing: if the usb had important data you can get testdisk to recover as much as you can.

---

### Post by jmd9qs on 2008-10-30
thanks, drive is even auto-mounting now w/ no further trouble. ```
dmesg | tail
``` produces good results. i appreciate all the help.

jmd9qs

---

