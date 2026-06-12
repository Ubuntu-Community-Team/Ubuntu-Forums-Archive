---
title: "Maunally Mounting HDD"
date: 2015-05-16
forum: Hardware
---

### Post by jordan40 on 2015-05-16
Hello so I am trying to manually mount my failing Windows 8.1 HDD on ubuntu computer so I can copy and keep the files (duh), 
ubuntu recognizes it as /dev/sdb but doesn't mount it automatically bc its a windows and windows 8.1 goes into hibernate instead of shutdown 
blah blah blah can't boot it to run a "shutdown -s -t -000" batch file, here's what iv'e tried so far in ubuntu to manually boot.

sudo mkdir /media/newhdd (to make a spot to mount the drive to)

sudo mount /dev/sdb /media/newhdd  (to mount the hdd to /media/newhdd)

but then I don't know what to do after that bc I get this error


*mount: you must specify the filesystem type*

woop woop

---

### Post by 1yan on 2015-05-16
[COLOR=#000000]How about:

sudo mount /dev/sdb /media/newhdd [/COLOR][COLOR=#000000]-t ntfs[/COLOR]

---

### Post by SeijiSensei on 2015-05-16
"/dev/sdb" refers to the entire drive.  Filesystems are located in "partitions" on those drives; those are what you would mount.

First, list the partitions on the device with this:
```
sudo fdisk -l /dev/sdb
```
You'll get results that will look something like this:
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfb4ac0b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    48383999    24088576   1b  Hidden W95 FAT32
/dev/sda3        48384000   829790207   390703104    7  HPFS/NTFS/exFAT
/dev/sda4       829792254  1953523711   561865729    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       829792256  1415727103   292967424   83  Linux
/dev/sda6      1415729152  1447727103    15998976   82  Linux swap / Solaris
/dev/sda7      1447729152  1953523711   252897280   83  Linux

```
My Windows partition is stored in /dev/sda3.  I would mount that with
```
sudo mount /dev/sda3 /media/newhdd
```
Now you can just navigate to /media/newhdd and do what you need to do.

Linux routinely detects the type of filesystem automatically these days.  I rarely need to use "-t type" any more.

---

### Post by oldfred on 2015-05-16
If it is Windows 8, you may have gpt partitioning if you UEFI boot.
then you need to use parted or gdisk to list partitions, not fdisk.

The Linux NTFS driver will not mount NTFS partitions that need chkdsk or are hibernated to prevent you from damaging partition beyond what chkdsk may then be able to fix.

And if Windows 8 you must always have the fast startup or hibernation off if dual booting. Even if dual booting two Windows.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

