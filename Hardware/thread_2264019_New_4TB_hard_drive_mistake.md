---
title: "New 4TB hard drive mistake"
date: 2015-02-04
forum: Hardware
---

### Post by marrjam on 2015-02-04
I just received a new hard drive and booted a Lubuntu Live CD to format it (NTFS GPT data drive, not the boot drive).  While still using the Lubuntu Live CD I transfered video files from several backup drives (Lubuntu was acting wonky, don't know why).  When done I reformatted and reinstalled Lubuntu on my SSD drive (not the 4TB drive, which is a GPT data drive).  Now I get the following message when I click on icon of the drive in the file manager from a Mint Live CD (get the same message from a Lubuntu Live CD.

Error mounting /dev/sda2 at /media/mint/Video 3: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda2" "/media/mint/Video 3"' exited with non-zero exit status 12: NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

and instead of one drive showing in the file manager I get 2 drives (the same name "Video 3)

When I boot into GParted it shows the 4TB drive as it should be, 1 drive, 72% full.  I hooked up the 4TB to a Sabrent USB 3.0 to SATA drive adapter to my windows machine and minitool partition manager wouldn't recognize it.

GPT partition table????  Trying to tell me there are 2 drives instead of one???  Attached is a screen shot from Mint Live DVD.  460 Movies on the drive I'd like to save.  If you could help or point me in the right direction I'd be eternally grateful.  Thanks Mark

---

### Post by papibe on 2015-02-04
Hi marrjam.

shouldn't your ssd be /dev/sda, and the other one /dev/sdb?

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
sudo fdisk -l

sudo gdisk -l /dev/sda

sudo gdisk -l /dev/sdb

```
Regards.

---

### Post by marrjam on 2015-02-04
Thanks for the quick reply papibe,  your right, the should be in the order you listed, but I went about transfering files in a convuluted way because I was having difficulties with Lubuntu when I installed my new 4TB HD and decided to transfer the files from the two 2TB drives from a live cd (both 2TB drives were MBR) after formatting from the live CD.  After the transfer of all the files and changed the two 2TB drives to GPT, then reinstalled Lubuntu on the ssd while the other 3 drives where unhooked so I wouldn't "mess them up".  Then plugged them in after the fresh install. and the confusion began for hard drives/boot drive/ and me.

s@server:~$ sudo fdisk -l
[sudo] password for s: 

Disk /dev/sda: 3.7 TiB, 4000785948160 bytes, 7814035055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2052474d

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  ?       6579571 1924427647 1917848077 914.5G 70 DiskSecure Multi-Boot
/dev/sda2  ?    1953251627 3771827541 1818575915 867.2G 43 unknown
/dev/sda3  ?     225735265  225735274         10     5K 72 unknown
/dev/sda4       2642411520 2642463409      51890  25.3M  0 Empty

Partition 2 does not start on physical sector boundary.

Partition 3 does not start on physical sector boundary.

Partition 4 does not start on physical sector boundary.


Partition table entries are not in disk order.
Disk /dev/sdb: 1.8 TiB, 2000397852160 bytes, 3907027055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 09481A60-DB1B-48FC-A00E-BD2B53FCF418

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 3907026943 3907024896  1.8T Microsoft basic data

Disk /dev/sdc: 1.8 TiB, 2000397852160 bytes, 3907027055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 83607160-5296-47C7-A6BE-E526617BFB8E

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 3907026943 3907024896  1.8T Microsoft basic data

Disk /dev/sdd: 58.7 GiB, 63021981184 bytes, 123089807 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x844a6741

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdd1  *     2048 123087985 123085938 58.7G 83 Linux

s@server:~$ sudo gdisk -l /dev/sda
sudo: gdisk: command not found
s@server:~$ sudo gdisk -l /sdb
sudo: gdisk: command not found

---

### Post by papibe on 2015-02-04
Thanks.

Unfortunately gdisk is not installed. Could you install it and run the last commands again?
```
sudo apt-get install gdisk

sudo gdisk -l /dev/sda

sudo gdisk -l /dev/sdb
```
Regards.

---

### Post by marrjam on 2015-02-05
Sorry, here it is:

GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Exact type match not found for type code 7000; assigning type code for
'Linux filesystem'
Exact type match not found for type code 4300; assigning type code for
'Linux filesystem'
Exact type match not found for type code 7200; assigning type code for
'Linux filesystem'
Disk /dev/sda: 7814035055 sectors, 3.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4F02D4C4-310A-4514-805F-56BCAE1A87FB
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7814035021
Partitions will be aligned on 8-sector boundaries
Total free space is 4077610996 sectors (1.9 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1         6579571      1924427647   914.5 GiB   8300  Linux filesystem
   2      1953251627      3771827541   867.2 GiB   8300  Linux filesystem
   3       225735265       225735274   5.0 KiB     8300  Linux filesystem
s@server:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 3907027055 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 09481A60-DB1B-48FC-A00E-BD2B53FCF418
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907027021
Partitions will be aligned on 2048-sector boundaries
Total free space is 2092 sectors (1.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      3907026943   1.8 TiB     0700  
s@server:~$

---

### Post by oldfred on 2015-02-05
Did you perhaps format drive not partitions on new 4TB drive? Then it becomes a SuperFloppy and will not mount normally? You may be able to mount like a floppy drive, but no way to convert to partitions.
Fdisk showed "funny" partitions as if random data is in partition table. Or just your data written where partition table normally is. And then gdisk converted to gpt but made standard partitions.

---

### Post by Gazzamit on 2015-11-28
[COLOR=#111111][FONT=Ubuntu]Late reply but just found this out and thought it may help others.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]There are no partitions as suspected. They are an attempt by fdisk to read partition info where there is none - there's just data there being misinterpreted instead. Data may have been copied to a disk that was formatted but not ever partitioned.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To mount entired non-partitioned disk:[/FONT][/COLOR]

sudo mkdir /mnt/test
sudo chmod 755 /mnt/test
mount -t ntfs /dev/sda /mnt/test
[COLOR=#111111][FONT=Ubuntu](NOT: mount -t ntfs /dev/sda1 /mnt/test)[/FONT][/COLOR]

---

