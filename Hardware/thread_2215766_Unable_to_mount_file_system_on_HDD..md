---
title: "Unable to mount file system on HDD."
date: 2014-04-08
forum: Hardware
---

### Post by robbiejormerod on 2014-04-08
I've experianced a error with my instalation so am currently working from a live USB(unbuntu 12.04 lts). When I try to access my hard drive I get this error; 
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I really need to get to some files on this disk so any help would be brilliant.

---

### Post by sudodus on 2014-04-08
Please post the output of the following commands, when you have connected the HDD.

```
sudo parted -l
```
```
df
```

-o-

Is it possible that it complains about the live disk /dev/sdb rather than the internal HDD, which is probably /dev/sda?

Is it possible that there is a file system error or some bad sector on the HDD?

Have you checked the S.M.A.R.T. information (can be seen in the BIOS/UEFI menu system or with some utility program like

***smartctl*** that can be installed with

```
sudo apt-get install smartmontools
```

See ```
man smartcl
``` for details how to run it. A simple output is the overall health statement for /dev/sda

```
sudo smartctl -H /dev/sda
```

You get more details with the -a option

```
sudo smartctl -a /dev/sda
```

And you can check and repair the file system which is not mounted by

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number so typically /dev/sda1. Be warned, this command may take a long time, maybe hours, particularly if some errors are found and/or the drive is big.

---

### Post by robbiejormerod on 2014-04-08
Model: SanDisk Cruzer Pop (scsi)
Disk /dev/sda: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32        boot


Model: ATA ST3160211AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      159GB   160GB  1540MB  extended
 5      159GB   160GB  1540MB  logical   linux-swap(v1)


ubuntu@ubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             2063164   81684   1874984   5% /
udev              729792       4    729788   1% /dev
tmpfs             295672     860    294812   1% /run
/dev/sda1        7800304 3034012   4766292  39% /cdrom
/dev/loop0        714112  714112         0 100% /rofs
tmpfs             739172       8    739164   1% /tmp
none                5120       4      5116   1% /run/lock
none              739172      76    739096   1% /run/shm

---

### Post by robbiejormerod on 2014-04-08
I'll try your other suggestions now. TA

---

### Post by sudodus on 2014-04-08
> **robbiejormerod said:**
> ```
Model: SanDisk Cruzer Pop (scsi)
Disk /dev/sda: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32        boot


Model: ATA ST3160211AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      159GB   160GB  1540MB  extended
 5      159GB   160GB  1540MB  logical   linux-swap(v1)


ubuntu@ubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             2063164   81684   1874984   5% /
udev              729792       4    729788   1% /dev
tmpfs             295672     860    294812   1% /run
/dev/sda1        7800304 3034012   4766292  39% /cdrom
/dev/loop0        714112  714112         0 100% /rofs
tmpfs             739172       8    739164   1% /tmp
none                5120       4      5116   1% /run/lock
none              739172      76    739096   1% /run/shm
```

You were right, /dev/sdb1 is your Ubuntu partition (with the file system ext4)

---

### Post by sudodus on 2014-04-08
> **robbiejormerod said:**
> I'll try your other suggestions now. TA

That's a good idea, to check and if possible repair the partition and or file system.

After that you should try to mount the partition again (from the live drive, I think after rebooting, to get things set up correctly).

Good luck :-)

---

### Post by robbiejormerod on 2014-04-08
I've run the check and repair command and manged to get the file system mounted to recover my important files. So thanks for your help.
If I can just pick your brains again though, the original  error came about when I was having problems with my display driver, It was running really slowly so i changed to a properietary driver to see if that would fix it, then the system just would not boot up again. Any thoughts on what might be going on there. Thanks.
The graphics port is; Nividia geforce 6150
The original driver was X. Org X server - Nouveau display driver from xserver-xorg-video nouveau (open source)
I changed it to Nividia binary Xorg driver, kernal module and library from nividia-173-updates.
There are two other options in the menu, but all of them have been causing me problems.

---

### Post by sudodus on 2014-04-08
> **robbiejormerod said:**
> I've run the check and repair command and manged to get the file system mounted to recover my important files. So thanks for your help.

I'm happy to help :-)
> 
If I can just pick your brains again though, the original  error came about when I was having problems with my display driver, It was running really slowly so i changed to a properietary driver to see if that would fix it, then the system just would not boot up again. Any thoughts on what might be going on there. Thanks.

Yes it is possible that there was a 'hard reset', that corrupted some file, that is used during the boot process. A good alternative to just switching power off is

***alt SysRq*** **R E I S U B**

which gives you a chance to make a soft reset closing files in a controlled way. See this link

[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

> 
The graphics port is; Nividia geforce 6150
The original driver was X. Org X server - Nouveau display driver from xserver-xorg-video nouveau (open source)
I changed it to Nividia binary Xorg driver, kernal module and library from nividia-173-updates.
There are two other options in the menu, but all of them have been causing me problems.

I think you have tried what is reasonable to try, so continue with the open source ***nouveau*** driver. Maybe after several months you can try again, if there is a new proprietary driver that works, but do not hope too much, because the card is several years old (launched 2005 or 2006), and is probably not interesting enough for the manufacturer.

---

### Post by robbiejormerod on 2014-04-08
Thanks for that, the link is very interesting, I'll have a play around with it in the morning, time for a beer now though.
> **sudodus said:**
> :-)Maybe after several months you can try again, if there is a new proprietary driver that works, but do not hope too much, because the card is several years old (launched 2005 or 2006), and is probably not interesting enough for the manufacturer.
I've been putting off up grading, but I guess this is the computer's way of saying it's had enough.

---

