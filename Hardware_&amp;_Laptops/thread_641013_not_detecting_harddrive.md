---
title: "not detecting harddrive"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by psykotrol on 2007-12-14
I just installed ubuntu (again) on my primary harddrive, after a failed attempt to install windows xp. but its not detecting my secondary at all. it detected it on the live cd, but I couldnt access it. 

please at least respond to this thread, as nobody did the last one, and thats what got me here in the first place. :(

---

### Post by taurus on 2007-12-14
Sounds like you need to mount the second harddrive before you can access it.  Open a terminal and post the outputs of these two commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
cat /etc/fstab
```

---

### Post by ectospasm on 2007-12-14
What isn't being recognized?  Does fdisk see the secondary HDD?  If so, have you managed to put a filesystem on it?  If so, does /etc/fstab contain an entry for it?  If so, have you tried mounting it?

I would think I need more detail to solve this problem...

---

### Post by psykotrol on 2007-12-15
this is what I get for /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=54e999b4-3d0f-4022-b8df-06128e5a8176 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=34ee3975-8bbb-4fc4-9256-6ffbb6e36a47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

and this is what I get for fdisk

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb20bb20b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19457   156288321    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris
/dev/sda6               1       18701   150215688   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03610360

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19451   156240126    7  HPFS/NTFS


a few times when I booted, it said it had errors and needed to "force check" or something.

I recently reformatted drive "c:" in an attempt to install windows, but it didnt work because I couldnt install it on it anyway... said it wasnt a windows compatible partition or something. the drive I cant access I guess would be called drive "d:"

its recognizing my external usb harddrive.

also, it shows I have 3 cd drives (cdrom, cdrom0, cdrom1) when I go under /filesystem/media/ and I know I only have 2, one cd drive and one dvd drive.

---

### Post by taurus on 2007-12-15
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

---

### Post by psykotrol on 2007-12-15
I got to

sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

and this was the reply:

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by taurus on 2007-12-15
You said you reformatted /dev/sdb1!  What filesystem does it use now?  Post

```
sudo fdisk -l
```

---

### Post by psykotrol on 2007-12-15
I reformatted with the xp cd, I noticed something was weird because the drives werent in order.. it was like F: then D: then C: or something.

I reformatted what it said was c:

when I got into the recovery console, I did the general

```
format c: /fs:ntfs
```

I know I shouldnt have, but I tinkered with the partitions

It said it wasnt a windows compatible partition, so I deleted it, and created a new (raw) one of the same size, but it STILL said it wasnt windows compatible.

heres the results for fdisk:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb20bb20b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19457   156288321    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris
/dev/sda6               1       18701   150215688   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03610360

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19451   156240126    7  HPFS/NTFS

```

---

### Post by taurus on 2007-12-15
Looks like you have two internal harddrives and don't have windows on it, only Ubuntu.  Then, why would you want to format the second harddrive, /dev/sdb1, to ntfs filesystem?  Why not use Linux native filesystem like ext3.

---

### Post by psykotrol on 2007-12-15
I tried to install windows on my pc first (as suggested) then install ubuntu after windows is installed, so I formatted my c: drive to get rid of ubuntu, to install windows, but it didnt work because it (windows installer) said the drive was not windows compatible.

I then gave up because I didnt want to install it on my d: drive, cuz it had a lot of information I didnt want to lose, and proceeded to reinstall ubuntu on drive c:

I noticed that the d: drive was recognized on the livecd, but I couldnt access it, after installing ubuntu, it did not show d: at all.

I didnt reformat drive d:, I reformatted drive c:

I dont know wtf happened, I installed windows in the same process I always have, but this time it was not able to install to drive c: at all, because allegedly it was not a windows compatible partition.

lol did ubuntu rename c: to d:, or something?

and, for my n00b understanding:

/dev/sda1 is c:
/dev/sdb1 is d:

correct?

---

### Post by taurus on 2007-12-15
The best way is to boot with Ubuntu LiveCD if you have one handy.  Then, use gparted (System -> Administration) and remove all the partitions on your first harddrive.  Now, format that one large partition/drive as fat32/vfat.  Reboot and replace Ubuntu LiveCD with your windows CD.  Windows should be able to detect and install on the first harddrive now.

---

### Post by ectospasm on 2007-12-15
> **psykotrol said:**
> 

and, for my n00b understanding:

/dev/sda1 is c:
/dev/sdb1 is d:

correct?

Not necessarily.  If you've got multiple partitions on /dev/sda, it will be different.  Using an fdisk output you had earlier (you may have wiped this partition table), it would look like this:

/dev/sda1  C:
/dev/sda2  D:
/dev/sda5  E:
/dev/sda6  F:

/dev/sdb1  G:

And even then it may be different, because if I remember correctly Windows doesn't assign a letter to partitions it doesn't recognize.  Also, IIRC, Windows doesn't like not being the first partition.  If I wanted to install Windows, I always install it with no other HDD, so it sees itself as the first drive (C:).  You can move it to another position afterwards, just tell GRUB where it is and Windows usually doesn't complain...

---

### Post by psykotrol on 2007-12-22
okay before I do any of that stuff, I have screenshots from gparted, if that would be useful. I really dont want to format sdb because I have a lot of information on it that I cant lose.

is there a way to detect it without it losing all the info?

[img]http://img444.imageshack.us/img444/305/screenshotdevsdbgpartedig4.png[/img]
[img]http://img413.imageshack.us/img413/1593/screenshotinformationabjg9.png[/img]

---

### Post by psykotrol on 2007-12-22
Im trying to figure out if I should delete the linux-swap partition?

would somebody at least answer me?

---

