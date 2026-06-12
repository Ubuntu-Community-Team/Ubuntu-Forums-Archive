---
title: "unable to mount USB disk"
date: 2016-05-23
forum: Hardware
---

### Post by l736k on 2016-05-23
Hi, i've recently unmounted a 3.5" HDD from a NAS because of its OS wasn't responding anymore. Now, i'm trying to mount it on my Ubuntu 16.04 through a USB/SATA interface but i'm receiving the following error:

```
Error mounting /dev/sdb4 at  /media/L736K/1dab8a30-92b8-45ba-b301-1984dd290df9: Command-line `mount  -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb4"  "/media/L736K/1dab8a30-92b8-45ba-b301-1984dd290df9"' exited with  non-zero exit status 32: mount: wrong fs type, bad option, bad  superblock on /dev/sdb4,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

Can someone please help me? I need to recover all the data from it and unfortunately i'm quite a neophyte of Linux systems :(

---

### Post by ajgreeny on 2016-05-23
What filesystem is the drive formatted to; is it from a mac by any chance and therefore hfs+, or might it be formatted to exfat?
Maybe you just need another installed package to mount it.

What is the output of terminal command ```
sudo parted -l
```

---

### Post by l736k on 2016-05-23
Thanks for your help. Here's the output of that command:

```
Model: WDC WD20 EZRX-00D8PB0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 3      15,7MB  528MB   513MB                primary  msftdata
 1      528MB   2576MB  2048MB  ext3         primary  raid
 2      2576MB  4624MB  2048MB  ext3         primary  raid
 4      4624MB  2000GB  1996GB  ext4         primary  msftdata
```

Of course data are on the 4th partition (it's a 2TB HDD)

---

### Post by ajgreeny on 2016-05-24
Are you using a command to mount it or just clicking on the icon in your file-manager?

Is the disk part of the raid array or not involved in that?  I have no knowledge of using or managing raid so can not help if that is the situation.

---

### Post by l736k on 2016-05-24
the error i posted comes from the click on the icon in the file manager, but even if i try to mount it via the shell i'm getting a similar error:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb4,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

in the NAS there was only this disk so it is not part of any raid

---

### Post by ajgreeny on 2016-05-24
Sorry, no idea about the answer to this problem.
Why does the disk have partitions with raid flags if it is not in some way related to a raid array? As I say, I do not know raid at all.

Are you sure the disk is still working properly?  Does the Disks utility in Ubuntu give you any clues if you look in that?

---

### Post by l736k on 2016-05-25
As per the error message, i guess the problem is a spoiled file system or superblock...i don't know how i can fix this (but i know this is possible)

---

### Post by l736k on 2016-05-28
anybody who might help with this problem?

---

### Post by coffeecat on 2016-05-28
What is the make and model of your NAS ? Some home-type NAS devices use single disc raid setups simply to make things difficult in the situation you find yourself in. IMHO.

It should be possible to mount the drive and recover data but you need make and model to find appropriate instructions.

---

### Post by sudodus on 2016-05-28
**1.** If it is very important data, I suggest that you get another drive, clone this drive to that drive and do the repair job on that drive. You can use ***ddrescue*** for the cloning. If you can risk losing the data, skip directly to the next step.

**2.** Then on the cloned copy, I would suggest that you use ***e2fsck*** to try to repair the file system:

```
sudo e2fsck -cf /dev/sdb4
```

if the drive is still recognized as /dev/sdb.

**3.** If still no luck, I suggest that you try with ***testdisk***.

**4.** If still no luck, I suggest that you try with ***photorec***.

***Link:*** [Repair the partition table and file system](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

***Edit:*** But first of all, as coffeecat writes, try to find out as much as possible about the NAS system. It should help recovering the data.

---

### Post by l736k on 2016-05-28
> **coffeecat said:**
> What is the make and model of your NAS ? Some home-type NAS devices use single disc raid setups simply to make things difficult in the situation you find yourself in. IMHO.

It should be possible to mount the drive and recover data but you need make and model to find appropriate instructions.

It's a WD My Book Live Duo 2TB

---

### Post by l736k on 2016-05-28
> **sudodus said:**
> **1.** If it is very important data, I suggest that you get another drive, clone this drive to that drive and do the repair job on that drive. You can use ***ddrescue*** for the cloning. If you can risk losing the data, skip directly to the next step.

**2.** Then on the cloned copy, I would suggest that you use ***e2fsck*** to try to repair the file system:

```
sudo e2fsck -cf /dev/sdb4
```

if the drive is still recognized as /dev/sdb.

**3.** If still no luck, I suggest that you try with ***testdisk***.

**4.** If still no luck, I suggest that you try with ***photorec***.

***Link:*** [Repair the partition table and file system]("http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986")

***Edit:*** But first of all, as coffeecat writes, try to find out as much as possible about the NAS system. It should help recovering the data.

Thanks, i'm trying to clone the disk with this command:
```
ddrescue -d /dev/sdb4 /media/L736K/Maxtor/data/WD_recovery/WDImage.img /media/L736K/Maxtor/data/WD_recovery/WDImage.logfile
```
but i'm getting this error:
```
ddrescue: Can't open input file: Permission denied
```
am i missing something?

---

### Post by sudodus on 2016-05-28
Try with superuser permissions:

```
sudo ddrescue ...
```

I would clone the whole drive /dev/sdb, not only partition #4, but both ways are possible.

---

### Post by l736k on 2016-05-29
My bad! As i said i'm a noob unfortunately...

Ok, i started to clone the sdb (not only sdb4). Then i'll try the next steps you suggested and let you know. Thanks for the moment!

---

