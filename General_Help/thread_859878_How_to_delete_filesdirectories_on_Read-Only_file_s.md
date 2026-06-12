---
title: "How to delete files/directories on Read-Only file system"
date: 2008-07-15
forum: General Help
---

### Post by satimis on 2008-07-15
Hi folks,


Ubuntu 7.10


I have some files and directories on an USB flash pendrive.  I can't delele them because on read-only filesystem.


I tried;

$ sudo mount -o remount,rw /mnt/maindir
without result.


If run;
$ sudo mount -o remount,rw /dev/sdb1 ```

mount: you must specify the filesystem type

```
What filesystem I have to specify there?


I don't expect running;```

$ dd if=/dev/zero of=/dev/sdb1

```
to erase the pendrive completely.


Please shed  me some light.  TIA


B.R.
satimis

---

### Post by logos34 on 2008-07-15
try 

sudo mkdir /media/usb

sudo mount -t vfat -o rw /dev/sdb1 /media/usb

---

### Post by satimis on 2008-07-15
> **logos34 said:**
> try 

sudo mkdir /media/usb

sudo mount -t vfat -o rw /dev/sdb1 /media/usb
Hi logos34,


Thanks for your advice.


$ ls /media/```

cdrom  cdrom0  floppy  floppy0  sdb1  sdb2

```


$ sudo mount -t vfat -o rw /dev/sdb1 /media/sdb1/
No complaint


$ sudo rm -rf /media/sdb1/dir
......
rm: cannot remove `/media/sdb1/dir': Read-only file system


Still fails


B.R.
satimis

---

### Post by fyo on 2008-07-15
Might seem like a stupid question, but does your USB drive have a write-protect switch? You know, like SD cards and floppies?

---

### Post by satimis on 2008-07-15
> **fyo said:**
> Might seem like a stupid question, but does your USB drive have a write-protect switch? You know, like SD cards and floppies?
Hi fyo,


I can't find a hardware switch on the UBS Pendrive.  Those data were copied on it about 1~2 hours ago.


I ran;

$ sudo mount /dev/sdb1 /mnt

$ sudo mkdir /mnt/maindir

$ sudo cp /path/to/files /mnt/maindir

Warning popup saying coping the files as read only


$ sudo cp -r /path/to/dir-a /mnt/maindir
$ sudo cp -r /path/to/dir-b /mnt/maindir
etc.


I can remove all files copied on the pendrive.  But I can't remove the directories together with their files.


B.R.
satimis

---

### Post by fyo on 2008-07-15
> **satimis said:**
> I can remove all files copied on the pendrive.  But I can't remove the directories together with their files.

Sounds strange. Try chmod'ing them 666. Yes, sudo should work already, but...

Maybe also try mounting with sync and dirsync options?

Yes, I'm just throwing stuff at the wall at this point and hoping something sticks.

---

### Post by Dedoimedo on 2008-07-15
Hi,

You don't need comma after **remount**.
Try without it, see if this helps.

Then, try mounting it as FAT:

```
sudo mkdir /mnt/usb
sudo mount -t vfat -o rw /dev/xxx /mnt/usb
```

xxx is the usb device, which you can identify by typing:

```
sudo fdisk -l
```

After that, switch to the usb device (by using cd) and see the permissions on the files and the directories by using ls -la. What do you get?

Are you the owner? Are you using sticky bits?

Dedoimedo

---

### Post by satimis on 2008-07-15
> **Dedoimedo said:**
> Hi,

You don't need comma after **remount**.
Try without it, see if this helps.

Then, try mounting it as FAT:

```
sudo mkdir /mnt/usb
sudo mount -t vfat -o rw /dev/xxx /mnt/usb
```

xxx is the usb device, which you can identify by typing:

```
sudo fdisk -l
```

After that, switch to the usb device (by using cd) and see the permissions on the files and the directories by using ls -la. What do you get?

Are you the owner? Are you using sticky bits?


Hi Dedoimedo,


This USB pendrive looks quite strange to me.  I got it in a conference as gift from a multi-nation software company.  It has files on it introducing their products taking up 57M out of 1G.


After mount it with;```

$ sudo mount /dev/sdb1 /mnt
```
(I found /dev/sdb1 by runnint "fdisk -l")

I can copy files on it. They can be deleted later. 


If running```

$ cp -r /path/to/dir-A /mnt/

```
Directory including files can be copied on the pendrive.  But they can't be deleted later.


Then I followed logos34's advice trying to delete them but without result.


Later I found on running;
$ fdisk -l```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

```

The partition table seems gone.  


Therefore I ran
# fdisk /dev/sdb

to repartition the drive and afterwards ran;

# mkfs.ext2 -c /dev/sdb1
it went though w/o complaint


But I can't mount the pendrive

$ sudo mount -t ext2 /dev/sdb1 /media/sdb1/```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


Then I ran```

dmesg | tail

```


It asked me to run "e2fsck /dev/sdb1"

$ sudo e2fsck /dev/sdb1
```

....
Inode 421 has INDEX_FL flag set but is not a directory.
Clear HTree index<y>? 
......

```
It took long time to run without finish.  Therefore I manually exited it by pressing [Ctrl]+c


I don't know how to proceed further.  Nor I know what mistake I have committed.  Please advise.


TIA


B.R.
satimis

---

### Post by Dedoimedo on 2008-07-15
Hello,

Could it be a U3 thingie?

If so, you should download a U3 uninstaller (in Windows), remove the hidden partitions, reformat as fat32, then try this thing again.

BTW, don't pause commands in mid-run - it's not healthy. What was the "long time?"

Dedoimedo

P.S. Try fdisk again ... Unmount first! Remove ALL partitions. Unplug. Plug. Create new partition. Unplug. Plug. Format partition. Mount. Try writing / deleting ...

---

### Post by satimis on 2008-07-15
Hi Dedoimedo,


This is a very strange pendrive.  Performed following test-

Plug the pendrive


# fdisk -l```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       19457   156039345    5  Extended
/dev/sda5              32       19457   156039313+  8e  Linux LVM


Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

```


# fdisk /dev/sdb```

Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```

```

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1008, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-1008, default 1008): 
Using default value 1008

Command (m for help): p

Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1008     1031153   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```


# fdisk -l```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       19457   156039345    5  Extended
/dev/sda5              32       19457   156039313+  8e  Linux LVM

Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1008     1031153   83  Linux

```
It seems OK now


Unplug the pendrive.  Re-plug it.


# fdisk -l```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       19457   156039345    5  Extended
/dev/sda5              32       19457   156039313+  8e  Linux LVM

Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

Disk /dev/sdb doesn't contain a valid partition table

```
The partition table on the pendrive seems gone.  I repeated the steps 3 times with the same result.


If continue immediately after running "fdisk /dev/sdb"


# mkfs -c /dev/sdb1```

mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
129024 inodes, 257788 blocks
12889 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=264241152
8 block groups
32768 blocks per group, 32768 fragments per group
16128 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376

Checking for bad blocks (read-only test): done                                
Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 39 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```


# fdisk -l```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       19457   156039345    5  Extended
/dev/sda5              32       19457   156039313+  8e  Linux LVM

Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

Disk /dev/sdb doesn't contain a valid partition table

```


The partition table also gone.


> 
Could it be a U3 thingie?

If so, you should download a U3 uninstaller (in Windows), remove the hidden partitions, reformat as fat32, then try this thing again.

I don't know.  I suppose it would not be so complicate.  The pendrive contains files for advertising.


> 
BTW, don't pause commands in mid-run - it's not healthy. What was the "long time?"

Noted.

On running "sudo ext2fsck /dev/sdb" I continue pressing [Enter] to accept <y> for >15 minutes.  It seemed without end.


B.R.
satimis

---

### Post by Dedoimedo on 2008-07-15
Hello,

There seems to be a hidden partition on that thing. Let's try to think how we can find what it is and kill it.

Please install GParted, run it, then see what it tells you about the usb drive. Make sure to delete ALL partitions and delete the partition table.

If it does not help, boot from a GParted live CD and try again.

Cheers,
Dedoimedo

P.S. If this doesn't help, download the U3 uninstaller from Sandisk site, try killing the usb partitions in Windows ...

---

### Post by satimis on 2008-07-17
> **Dedoimedo said:**
> Hello,

There seems to be a hidden partition on that thing. Let's try to think how we can find what it is and kill it.

Please install GParted, run it, then see what it tells you about the usb drive. Make sure to delete ALL partitions and delete the partition table.

If it does not help, boot from a GParted live CD and try again.

Cheers,
Dedoimedo

P.S. If this doesn't help, download the U3 uninstaller from Sandisk site, try killing the usb partitions in Windows ...
Hi Dedoimedo,


Thanks for your advice.


Perfomed following test.


Turn on PC with the problematic USB pendrive plugged in.


On BIOS
disable SATA slot - to protect HD to be edited/erased accidentally


Boot the PC with GParted Live CD.  Scanning result;```


View Device Information;
Model
Size	1004.06 MiB
Path	/dev/sda

DiskLabelType	unrecognize
Head		255
Sectors/Track	63
Cylinders	128
Total Sectors	2056320

```


Device --> Create Partition Table
```

Create partition table on /dev/sda
Warning: This will erase all data on the entire disk /de/sda
Default is to create an msdos partitin table

```


--> Create


DiskLableType changed to;
msdos

other data remain unchanged


GParted --> Quit


Exit GParted and shutdown the PC


unplug the USB pendrive.  Plug it on another PC.



$ fdisk -l```


Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1008     1031153    6  FAT16

```


unplug and replug the pendrive several times to ensure it works without problem.


$ sudo mount /dev/sdb /mnt/```

mount: you must specify the filesystem type

```


$ sudo mkfs.vfat /dev/sdb```

mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sdb' (use -I if wanted)

```


$ sudo fdisk /dev/sdb```


Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1008, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-1008, default 1008): 
Using default value 1008

Command (m for help): p

Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders

Units = cylinders of 2046 * 512 = 1047552 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1008     1031153   83  Linux


Command (m for help): t
Selected partition 1
Hex code (type L to list codes): L

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot   
 1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data    
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access     
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor      
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT        
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep        
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT            
1c  Hidden W95 FAT3 75  PC/IX          
Hex code (type L to list codes): 6
Changed system type of partition 1 to 6 (FAT16)

Command (m for help): p

Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1008     1031153    6  FAT16

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.

```


$ fdisk -l```


Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1008     1031153    6  FAT16

```


unplug and replug the pendrive several times to ensure it works without problem.


$ sudo mount -t vfat /dev/sdb1 /media/sdb1```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


$ sudo mkfs.vfat /dev/sdb1```

mkfs.vfat 2.11 (12 Mar 2005)

```


$ fdisk -l```


Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

Disk /dev/sdb doesn't contain a valid partition table

```


Strangely I'm not allowed to format the pendrive.


The only Windows box I have is a very old WinXP.  I don't run it for sometimes.  Hoping that it still works.


Whether the U3 uninstaller is here?
[http://u3.sandisk.com/download/Download_no.asp#](http://u3.sandisk.com/download/Download_no.asp#)


Would the process be complicate?  Or the uninstaller has to be installed on WinXP.  Otherwise better for me to forget this funny pendrive.


B.R.
satimis

---

### Post by mc4man on 2008-07-17
the u3 uninstaller is here
[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)
I've only done it on windows, works fine
One of mine still has u3 - no problem using normally. The u3 partition itself is /dev/scdx, i can actually mount it but for no real purpose (locked, read only) other than 'curiosity'
>  doug@doug-desktop:~$ sudo mount /dev/scd2 /media/disk1
[sudo] password for doug: 
mount: block device /dev/scd2 is write-protected, mounting read-only

If it has a u3 partition you can find out by running
```
cat /etc/udev/rules.d/70-persistent-cd.rules
``` and it will be listed there (just in regards to u3, not the mass storage partition.

---

### Post by satimis on 2008-07-17
Hi mc4man,


Thanks for your advice and URL


$ fdisk -l```


Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

Disk /dev/sdb doesn't contain a valid partition table

```


$ sudo fdisk /dev/sdb```

Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1008, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-1008, default 1008): 
Using default value 1008

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 13: Permission denied.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```


$ fdisk -l```


Disk /dev/sdb: 1056 MB, 1056702464 bytes
33 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 2046 * 512 = 1047552 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1008     1031153   83  Linux

```


$ sudo mount /dev/sdb1 /media/sdb1```

mount: you must specify the filesystem type

```


I suspect maybe the pendrive itself having problem.  Usually immediately after running fdisk;

$ sudo mount /dev/sdb1 /mnt/
can mount it without assigning tag


> 
If it has a u3 partition you can find out by running
```
cat /etc/udev/rules.d/70-persistent-cd.rules
``` and it will be listed there (just in regards to u3, not the mass storage partition.

$ ls /etc/udev/rules.d/```

00-init.rules   40-permissions.rules      80-programs.rules  85-hwclock.rules   90-modprobe.rules
20-names.rules  60-symlinks.rules         85-alsa.rules      85-ifupdown.rules  99-udevmonitor.rules
25-iftab.rules  65-persistent-disk.rules  85-hdparm.rules    85-pcmcia.rules

```
70-persistent-cd.rules can't be found


B.R.
satimis

---

### Post by Dedoimedo on 2008-07-17
Hi,

Please try this software - from CD. See what it reports for that drive. Be careful when you use it, though, as you have the potential of accidentally screwing up partitions...

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Cheers,
Dedoimedo

P.S. Try GParted again, this time DELETE all from the disk, then CREATE both table AND the partition while booted in the live CD.

---

### Post by satimis on 2008-07-17
Hi Dedoimedo,


> 
Please try this software - from CD. See what it reports for that drive. Be careful when you use it, though, as you have the potential of accidentally screwing up partitions...

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Is there a liveCD version for this software?  Or booting up the PC with a liveCD and install it?

I won't install it on PC.  Only for curiosity I expect to find out what is the trick on the pendrive.  I don't expect creating problem on a Linux box here.


> 
P.S. Try GParted again, this time DELETE all from the disk, then CREATE both table AND the partition while booted in the live CD.
Yes, I'll try again running GParted.  Is there a function to erase the pendrive completely including all hidden files/directories?


Thanks


B.R.
satimis

---

### Post by Dedoimedo on 2008-07-17
Hi,

TestDisk has a live CD iso. Scroll down the page in the link I posted and you'll find it.

Can you erase all partitions with GParted? Hopefully. You can never know what may come up ... Theoretically, yes.

Dedoimedo

---

### Post by satimis on 2008-07-17
Hi Dedoimedo,


> 
TestDisk has a live CD iso. Scroll down the page in the link I posted and you'll find it.

On browsing your link I found following pages;

TestDisk on Live rescue CDs
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)


Index of [ftp://download.tuxfamily.org/gpartedlive/](ftp://download.tuxfamily.org/gpartedlive/)
[ftp://download.tuxfamily.org/gpartedlive/](ftp://download.tuxfamily.org/gpartedlive/)
```

TestDisk (but not always the latest version) is included on the following free rescue CD:
- GParted LiveCD 
...
etc.

```


But on that page the latest version of GParted LiveCD is gparted-livecd-0.3.4-11.iso


The version of gparted I'm using is 0.37.  I don't know whether TestDisk has been included?


> 
Can you erase all partitions with GParted? Hopefully. You can never know what may come up ... Theoretically, yes.

I'll test it again now.


B.R.
satimis

---

### Post by satimis on 2008-07-17
Hi Dedoimedo,


I can't resolve the finding on 2nd attempt.


Boot up the PC with GParted.  Select "Default"


Only 2 functions are available;

Device -> Create Partition Table ...
Partition --> New

Other functions greyout


Select
Partition --> New

Warning popup - erasing all data on the pendrive.

After scanning a while it comes to stop


Again select
Partition --> New

it popup "Create tne Partition" window```


Free Space Preceding (MiB):  0
New Size (MiB):   1004
Free Space Following (MiB)   0

Create as:   Primary Partition
Filesystem   ext2
Lable   Blank

[check] Round to cylinders

```

--> Add

```

Create Primary Partition # 1 (ext2, 1004.06 MiB) on /dev/sda

```

[1 operation pending]

-->  Apply
```

Applying pending operations

Completed Operations:
All operations successfully completed

```

--> Close

Scanning all devices again automatically.  Finally popup
```

/dev/sda1
1004.03 MiB

```


unplug the pendrive and plug it on another PC


$ fdisk -l```


Disk /dev/sdb: 1056 MB, 1056702464 bytes
255 heads, 63 sectors/track, 128 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         128     1028128+  83  Linux

```

Tried several times without change.


$ sudo mount -t ext2 /dev/sdb1 /media/sdb1```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


$ tail /var/log/syslog```

Jul 18 01:03:36 mail kernel: [ 8586.096432] sdb: assuming drive cache: write thr
ough
Jul 18 01:03:36 mail kernel: [ 8586.100794] SCSI device sdb: 2063872 512-byte hd
wr sectors (1057 MB)
Jul 18 01:03:36 mail kernel: [ 8586.102416] sdb: Write Protect is off
Jul 18 01:03:36 mail kernel: [ 8586.102420] sdb: Mode Sense: 0b 00 00 08
Jul 18 01:03:36 mail kernel: [ 8586.102423] sdb: assuming drive cache: write thr
ough
Jul 18 01:03:36 mail kernel: [ 8586.102427]  sdb: sdb1
Jul 18 01:03:36 mail kernel: [ 8586.104566] sd 12:0:0:0: Attached scsi removable
 disk sdb
Jul 18 01:03:36 mail kernel: [ 8586.104601] sd 12:0:0:0: Attached scsi generic s
g2 type 0
Jul 18 01:03:51 mail kernel: [ 8601.153740] init_special_inode: bogus i_mode (17
7777)
Jul 18 01:03:51 mail kernel: [ 8601.153815] EXT2-fs: corrupt root inode, run e2fsck

```


$ e2fsck /dev/sdb```

e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```


$ e2fsck -b 8193 /dev/sdb```

e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

$ e2fsck -b 8193 /dev/sdb1```

e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```


Don't know how to proceed further.


B.R.
satimis

---

### Post by satimis on 2008-07-17
Hi Hi Dedoimedo,


Finally I ran TestDisk and found 2 partitions on the pendrive
```

Disk /dev/hdc - 54 MB /52 MiB (RO)
Disk /dev/sda - 1055 MB / 1007 MiB

```

I suppose /dev/hdc is the hidden partition.  There is no HD connected on the PC with its connecting cable removed.


I can't delele /dev/hdc.  Neither can I write partition table on /dev/sda.  There is a warning popup;```

Write isn't available because the partition table type "None" have been selected

```


I can do nothing further.


B.R.
satimis

P.S. I can't understand the denotation of the supposed hidden partion is /dev/hdc ?

---

### Post by the_hardy_kid on 2008-07-17
Hit your pen drive VERY HARD with a hammer or other heavy object of your choosing...

(Don't actually do that...)

---

### Post by Dedoimedo on 2008-07-18
Hello,
Try to delete/format/repartition... that hdc ... if you can. Again with TestDisk. If it's hard-coded, then I suggest you buy / get another pendrive.
Dedoimedo

---

