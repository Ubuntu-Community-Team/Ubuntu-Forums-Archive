---
title: "cant detect usb flash drives"
date: 2013-09-16
forum: Hardware
---

### Post by david98 on 2013-09-16
Hi i recently re-installed ubuntu 12.04 on my samsung np270e laptop. Since i re-installed i can't seem to access my usb flash drives. i previously had no problem detecting them but i had to reinstall because i wanted to delete windows 8 and use the partition.

---

### Post by sudodus on 2013-09-16
Have you updated/upgraded Ubuntu so that all packages are up to date?

Are other things working properly in the newly installed Ubuntu 12.04?

What about the install media? If you installed from a USB drive, can't you see that one?

---

### Post by david98 on 2013-09-16
Everything but the usb's seem to be working fine. I've already updated. And i used a live dvd to install on the hdd

---

### Post by sudodus on 2013-09-16
Can you see the USB drives with

```
lsusb
```
or
```
sudo parted -l
```

Please post the output of these commands within code tags (mark and click the # icon at the top of the editing window).

---

### Post by david98 on 2013-09-16
lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0c45:64e0 Microdia 
Bus 002 Device 003: ID 0781:556b SanDisk Corp.

---

### Post by sudodus on 2013-09-16
So Sandisk device is detected. Is it a USB pendrive?

What is seen by

```
sudo parted -l
```
and if problems
```
sudo fdisk -lu
```

---

### Post by david98 on 2013-09-16
sudo parted -l
[sudo] password for dave: 
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   262GB  262GB   primary   ntfs
 3      262GB   500GB  238GB   extended
 5      262GB   494GB  232GB   logical   ext4
 6      494GB   500GB  6128MB  logical   linux-swap(v1)




Model: SanDisk Cruzer Edge (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End  Size  Type  File system  Flags




Model: Multiple Card Reader (scsi)
Disk /dev/sdc: 2003MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End  Size  Type  File system  Flags




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label         





 sudo parted -l
[sudo] password for dave: 
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   262GB  262GB   primary   ntfs
 3      262GB   500GB  238GB   extended
 5      262GB   494GB  232GB   logical   ext4
 6      494GB   500GB  6128MB  logical   linux-swap(v1)




Model: SanDisk Cruzer Edge (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End  Size  Type  File system  Flags




Model: Multiple Card Reader (scsi)
Disk /dev/sdc: 2003MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End  Size  Type  File system  Flags




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  


dave@dave-300E5EV-300E4EV-270E5EV-270E4EV:~$ sudo fdisk -lu


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xdd49c7c1


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   512002047   255897600    7  HPFS/NTFS/exFAT
/dev/sda3       512004094   976771071   232383489    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       512004096   964800511   226398208   83  Linux
/dev/sda6       964802560   976771071     5984256   82  Linux swap / Solaris


Disk /dev/sdb: 8004 MB, 8004304896 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbd76c5f9


   Device Boot      Start         End      Blocks   Id  System


Disk /dev/sdc: 2002 MB, 2002780160 bytes
62 heads, 62 sectors/track, 1017 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System

---

### Post by sudodus on 2013-09-16
Something is wrong. No partitions are visible on

Model: SanDisk Cruzer Edge (scsi)
Disk /dev/sdb: 8004MB

and 

Model: Multiple Card Reader (scsi)
Disk /dev/sdc: 2003MB

Only the drive info. I guess there are partitions (with data), that you could see before. Can you check in another computer or with another version of Ubuntu or Windows or Mac OS?

Is it really Ubuntu 12.04? It should be very reliable nowadays, more than one year after the release.

---

### Post by david98 on 2013-09-16
windows 7 not detecting the sandisk 8gb. t's detecting the 2 gb sd card but wont let me open or format it. and yes definitely 12.04 going to see if a live disk will detect it

---

### Post by sudodus on 2013-09-16
Probably something is wrong with the pendrive. Maybe also with the sd card.

It is very important to ***unmount*** external drives before unplugging, hard disk drives as well as flash drives. It corresponds to 'safe removal' in Windows. The procedure is to finish writing whatever is scheduled to be written, and then making the drive unavailable for further read/write operations.

---

### Post by david98 on 2013-09-16
yeah i think i totally corrupt both drives while wiping a partition of my hdd managed to recover some of the data but the drives are useless now never mind

---

### Post by sudodus on 2013-09-16
What you can try is wiping the first megabyte with dd, [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")
and then try to make a partition table and file systems with ***gparted***.

---

### Post by david98 on 2013-09-17
Thank's for the advice got both drives working with gparted. You've been very helpful.

---

### Post by sudodus on 2013-09-17
You are welcome :-)

And finally, please mark this thread as SOLVED, see [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

