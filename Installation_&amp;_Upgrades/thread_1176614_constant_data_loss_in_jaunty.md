---
title: "constant data loss in jaunty"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by freakyruft on 2009-06-02
strange problem:
I installed jaunty (after an upgrade from intrepid has failed), the installation finished - all went ok, until it says: remove cd and press enter to reboot. After I hit enter the system haltet, I turned power off, on again and the system seemed to work fine for a few days. Then strange things began to happen:
files get lost, totally random files. Some files from my Desktop, some configuration files, parts of my home directory, more and more applications began to crash because of segmentation fault (even apt, firefox, bash, etc.). But only files from one of my two linux (ext3) Partitions, the fat and ntfs partitions work just fine, data is save there. FSCK "fixed" errors on every reboot (I was dropped to shell saying I should start it) deleting some more files.
At that Time I thought of problems with the file system or a dieing hard disk (although the disk is new). I checked the drive several times using all checking tools ultimate boot cd offers (including vendor's tool) - so I think the drive is just fine.
formatting and reinstallation didn't work either.
Then I thought of a problem with ext3 - I formatted using xfs, reinstalled and the system worked for two days. Then it began to beep at shutdown and x-server crashed, document viewer crashed, etc.
checked the syslog, no failed shutdowns etc. till all got messed up.

does anyone know what I'm doing wrong?

if it helps, here the output of "fdisk -l":
```

Platte /dev/sda: 320.0 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00065ea3

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528       19581   104856255    7  HPFS/NTFS
/dev/sda3           19582       23497    31455270   83  Linux
/dev/sda4           23498       38913   123829020    5  Erweiterte
/dev/sda5           23498       24280     6289416   82  Linux Swap / Solaris
/dev/sda6           24281       25585    10482381   83  Linux
/dev/sda7           25586       38913   107057128+   b  W95 FAT32


```thank you

---

### Post by cariboo on 2009-06-02
Even though the drive is new, they can still fail, from everything you have reported, it still sounds like the drive is failing. If it is still under warranty, you should be able to get it replaced fairly quickly.

---

### Post by freakyruft on 2009-06-02
Thank you for your quick reply.
Yes, I thought of that, but no low-level checking tool reported any failure of the drive. And why are only the two linux partitions failing and non of the others? But the linux partitions this hard?
And yes, I got warranty, so I'll get it replaced, but at the moment I don't think this solves my problem.
I thought of another possibility: Is it possible that Ubuntu can't unmount the partitions on shutdown cleanly for any reason? If so, how can I find out?

---

### Post by freakyruft on 2009-06-04
got a new hard drive yesterday, rolled out dd image and - guess what - same problem happened today.
wtf am I doing wrong?
Learned today: It does not matter if I shut down or not, my data got wasted right before my eyes, I could watch it disappear while working - so definetely no hardware problem and no unclean-shutdown-problem.
Does anyone have another idea?
If it helps anything, here's my fstab (perhaps somthing wrong there?):

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=5e68b433-ca32-4b90-b56d-41e35bb2b63d /               xfs     relatime        0       0
# /home was on /dev/sda6 during installation
UUID=8ed1450f-1c8a-4fe9-9ec6-6af1a0035a2a /home           xfs     relatime        0       0
# /media/Daten was on /dev/sda7 during installation
UUID=723F-1E14  /media/Daten    vfat    utf8,umask=000,gid=1000,uid=1000 0       0
# /media/VistaGames was on /dev/sda2 during installation
UUID=31757DB7442E099E /media/VistaGames ntfs    defaults,nls=utf8,umask=000,gid=1000,uid=1000 0       0
# /media/VistaWork was on /dev/sda1 during installation
UUID=0B22A51809BC3E14 /media/VistaWork ntfs    defaults,nls=utf8,umask=000,gid=1000,uid=1000 0       0
# swap was on /dev/sda5 during installation
UUID=fc0f0e15-2fc2-4b9a-ba53-ace059985db5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

