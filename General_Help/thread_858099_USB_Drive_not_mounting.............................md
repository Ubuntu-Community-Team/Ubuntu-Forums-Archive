---
title: "USB Drive not mounting...............................help...."
date: 2008-07-13
forum: General Help
---

### Post by bijeeshvs on 2008-07-13
Whenever i plug a usb (pen drive) drive to my system it doesnt mount and says "invalid mount option when attempting to mount the volume". Gparted, says to mount it to cdrom and can mount on cdrom but cannot create files even as root ...............

i tried a few things with no success, whose output is presented here..

```
surya@surya-desktop:~$ sudo fsck /dev/sdb
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

surya@surya-desktop:~$ sudo fsck /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 0 files, 0/62735 clusters
surya@surya-desktop:~$ sudo pmount -w /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

surya@surya-desktop:~$ dmesg | tail
[ 9461.689429]  sdb: sdb1
[ 9464.102960] sd 7:0:0:0: [sdb] 2015231 512-byte hardware sectors (1032 MB)
[ 9464.103763] sd 7:0:0:0: [sdb] Write Protect is off
[ 9464.103771] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 9464.103773] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 9464.103780]  sdb: sdb1
[ 9493.520419] UDF-fs: No partition found (1)
[ 9493.563522] ISOFS: Unable to identify CD-ROM format.
[ 9751.211641] UDF-fs: No partition found (1)
[ 9751.254470] ISOFS: Unable to identify CD-ROM format.

```

if you can figure it out, please help.........................

---

### Post by hal10000 on 2008-07-13
is there any data on your pendrive?
If not, then you should simply delete the partition(s) on this drive and create a new one with gparted (if your going to use it under linux **and** windows, then create a fat32 partition, if you will only use it under linux, then you may create an ext2 partition.
If you have data on the drive that should not be lost, then you may try to use the [COLOR="Red"]testdisk[/COLOR] utility (install it with [COLOR="Red"]sudo apt-get install testdisk[/COLOR])
if you have further problems with the drive, then you should post the output of the command [COLOR="Red"]sudo fdisk -l[/COLOR]

---

### Post by bijeeshvs on 2008-07-13
> **hal10000 said:**
> is there any data on your pendrive?
If not, then you should simply delete the partition(s) on this drive and create a new one with gparted (if your going to use it under linux **and** windows, then create a fat32 partition, if you will only use it under linux, then you may create an ext2 partition.
If you have data on the drive that should not be lost, then you may try to use the [COLOR="Red"]testdisk[/COLOR] utility (install it with [COLOR="Red"]sudo apt-get install testdisk[/COLOR])
if you have further problems with the drive, then you should post the output of the command [COLOR="Red"]sudo fdisk -l[/COLOR]

i have partitioned and formatted it with gparted and fdisk , both didnt helped and its the same story with my another thumb drive...................

---

### Post by tech0007 on 2008-07-13
What filesystem did u put on it? ext2?vfat?

Plug it in. Then do: 
'sudo mkdir /media/data'
'sudo mount -t [filesystem] -o rw,defaults /dev/sdb1 /media/data'

post the output of 'tail /var/log/messages'

---

### Post by bijeeshvs on 2008-07-14
here is the output.....................
> 
Jul 14 21:39:43 surya-desktop kernel: [ 2132.299199] usb 5-4: configuration #1 chosen from 1 choice
Jul 14 21:39:43 surya-desktop kernel: [ 2132.299594] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 14 21:39:48 surya-desktop kernel: [ 2137.570661] scsi 5:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
Jul 14 21:39:48 surya-desktop kernel: [ 2137.571977] sd 5:0:0:0: [sdc] 2015231 512-byte hardware sectors (1032 MB)
Jul 14 21:39:48 surya-desktop kernel: [ 2137.572596] sd 5:0:0:0: [sdc] Write Protect is off
Jul 14 21:39:48 surya-desktop kernel: [ 2137.575848] sd 5:0:0:0: [sdc] 2015231 512-byte hardware sectors (1032 MB)
Jul 14 21:39:48 surya-desktop kernel: [ 2137.576478] sd 5:0:0:0: [sdc] Write Protect is off
Jul 14 21:39:48 surya-desktop kernel: [ 2137.576497]  sdc: sdc1
Jul 14 21:39:48 surya-desktop kernel: [ 2137.685347] sd 5:0:0:0: [sdc] Attached SCSI removable disk
Jul 14 21:39:48 surya-desktop kernel: [ 2137.685410] sd 5:0:0:0: Attached scsi generic sg3 type 0


now i have mounted it and with root account i am able to write to it, but the drive is not mounted otherwise..........

---

