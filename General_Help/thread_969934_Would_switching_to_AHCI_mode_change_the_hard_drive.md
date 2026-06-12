---
title: "Would switching to AHCI mode change the hard drive ID?"
date: 2008-11-03
forum: General Help
---

### Post by Roasted on 2008-11-03
I have 4 hard drives.

500gb
500gb
250gb
250gb

sda = 500
sdb = 250
sdc = 500
sdd = 250

I switched to AHCI mode, and I realized my drives changed. Now it's...

sda = 500
sdb = 500
sdc = 250
sdd = 250

I noticed this when my backup drive for the samba network (the first 250gb drive, which was originally on sdb) was copying data over it shouldn't have. I noticed it had taken on a different device ID. 

Would switching to AHCI mode have caused this? Cause uh, that's all I changed... I'm glad I caught it, otherwise I would have had some problems recovering my data!

---

### Post by rbmorse on 2008-11-03
I don't know the answer to your specific question, but the situation you describe is the reason we are being encouraged to adopt the practice of using a partition's UUID as its identifier in fstab rather than the familiar /dev/sdXY notation.

---

### Post by Roasted on 2008-11-03
> **rbmorse said:**
> I don't know the answer to your specific question, but the situation you describe is the reason we are being encouraged to adopt the practice of using a partition's UUID as its identifier in fstab rather than the familiar /dev/sdXY notation.

Are you referring to "disk identifier"??

```

jason@jason-intrepid:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16771676

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650        7776     1020127+  82  Linux swap / Solaris
/dev/sda3            7777        9816    16386300   83  Linux
/dev/sda4            9817       60801   409537012+  83  Linux


```

How would that work?

Instead of:

Sudo mount /dev/sdb1 /media/storage

It would be...

Sudo mount 0x16771676 /media/storage

??

---

### Post by dcstar on 2008-11-03
There are **hundreds** of posts already on how to correctly mount volumes using UUIDs or Volume labels, please look at these.

---

### Post by Roasted on 2008-11-03
> **dcstar said:**
> There are **hundreds** of posts already on how to correctly mount volumes using UUIDs or Volume labels, please look at these.

Hey yeah, cause I've been searching ever since I made my last post and haven't found any yet.

---

### Post by dcstar on 2008-11-03
> **Roasted said:**
> Hey yeah, cause I've been searching ever since I made my last post and haven't found any yet.

Apart from these forums, here is one that may be of use:

[http://linux.byexamples.com/archives/321/fstab-with-uuid/](http://linux.byexamples.com/archives/321/fstab-with-uuid/)

---

### Post by Roasted on 2008-11-03
.......

Okay, so... I run blkid /dev/partitioninquestion and I get the UUID.

So, how do I mount it then? That link didn't tell me anything in particular I wanted to know. I want to know how to mount drives to directories based on UUID. Not how to auto-mount with fstab.

I tried something like this...

sudo mount UUID="b2354e40-cd24-41eb-b41b-0aadc9933166" SEC_TYPE="ext2" TYPE="ext3" /media/localbackup 

But it recommended I read the man page. I skimmed the 800 some page manual but I didn't see anything regarding UUID.

---

### Post by Roasted on 2008-11-03
All right, instead of messing with a script to mount the drives, I just decided to do fstab.

Here's what I got, which is the best I could follow to the guides I googled. Yet, I just restarted, and the drives didn't auto-mount.

What's wrong with it?


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ab1ec851-8bb9-4a63-b045-ba7e2fc4b444 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=e94a403e-832a-45c3-b3ae-b1b19025c945 /home           ext3    relatime        0       2
# /dev/sda2
UUID=10b66b98-07bc-4b41-acc5-3f12c86d1d9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/sdb1 
UUID=b2354e40-cd24-41eb-b41b-0aadc9933166 /media/localbackup	ext3	0	1

#/dev/sdc1 
UUID=772764b7-e571-4897-ba6d-ded412a5e814 /media/storage	ext3	0	1

#/dev/sdd1 
UUID=b862f78f-4fcc-4d41-9d64-b7534da2dc84 /media/storagebackup	ext3	0	1
```

The partitions in question are the bottom 3 listed.
sdb1 = 500gb = /media/localbackup
sdc1 = 250gb = /media/storage
sdd1 = 250gb = /media/storagebackup

EDIT - and quite frankly, if there's an easier way to do this, for the love of God please tell me. I find it to be a hassle to edit this file and do all of this research when ALL I WANT is for 3 drives to auto-mount. I'm even in IT and this is a headache.

---

### Post by Roasted on 2008-11-03
After some other researching, I noticed some people had some differences in their fstab. Basically, I added "defaults" and changed 0 1 to 0 0. I don't know what it did... but maybe somebody can explain it!

I just restarted and my 3 drives (each with 1 ext3 partition spanning across the entire drive) mounted to their designated shares.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                 proc         defaults                    0  0  
# /dev/sda3
UUID=ab1ec851-8bb9-4a63-b045-ba7e2fc4b444  /                     ext3         relatime,errors=remount-ro  0  1  
# /dev/sda4
UUID=e94a403e-832a-45c3-b3ae-b1b19025c945  /home                 ext3         relatime                    0  2  
# /dev/sda2
UUID=10b66b98-07bc-4b41-acc5-3f12c86d1d9a  none                  swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0         udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd1                                  /media/cdrom1         udf,iso9660  user,noauto,exec,utf8       0  0  

#/dev/sdb1 
UUID=b2354e40-cd24-41eb-b41b-0aadc9933166  /media/localbackup    ext3         defaults                    0  0  

#/dev/sdc1 
UUID=772764b7-e571-4897-ba6d-ded412a5e814  /media/storage        ext3         defaults                    0  0  

#/dev/sdd1 
UUID=b862f78f-4fcc-4d41-9d64-b7534da2dc84  /media/storagebackup  ext3         defaults                    0  0  
```

---

