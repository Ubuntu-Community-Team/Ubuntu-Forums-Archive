---
title: "Partitions problem"
date: 2011-04-29
forum: Hardware
---

### Post by Sevenarth on 2011-04-29
Hi,
are months and months what i'm searching for solution on my problem with gparted....
When i try to install Ubuntu, the partition manager doesn't recognize the partition table of my HD, saying "unallocated " and the error "Can't have a partition outside the disk!". I don't wanna format my hd.
Today i've downloaded Ubuntu 11.04 and i've installed it with Wubi, but after the GRUB i got "No root file system is defined!". I don't understand :(

Now i'm with Ubuntu 11.04 Live CD.

GParted screen: [http://i52.tinypic.com/2usiwco.png](http://i52.tinypic.com/2usiwco.png)

fdisk -l:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       59115   474737813+   7  HPFS/NTFS
/dev/sda3           59115       60802    13552001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

By searching the Wubi error i got boot info too:
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       949473279 sectors, but according to the info from 
                       fdisk, it has 949475626 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       27090943 sectors, but according to the info from 
                       fdisk, it has 27104001 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   949,682,474   949,475,627   7 HPFS/NTFS
/dev/sda3         949,680,128   976,784,129    27,104,002   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3
/dev/sda3 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E24499CC4499A3B7                       ntfs       SYSTEM                        
/dev/sda2        EEFCAE51FCAE143D                       ntfs       HP                            
/dev/sda3        3A28FC5028FC0C9F                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf Thanks. Sorry, for my bad english, but i'm a italian student :D

---

### Post by oldfred on 2011-04-29
This hightlights the issue.

/dev/sda2 overlaps with /dev/sda3
/dev/sda3 ends after the last sector of /dev/sda

If you look at the sectors you will see that the numbers overlap and the last sector of sda3 is greater than that reported as the size of the drive.

Fixing last sector is straight forward as you cannot have data beyond end of drive. But the overlap could cause an issue if you have data from one or the other partition written into that same space. Of course only one can have real data, but which one? Usually data starts at the beginning, but no guarantees.

First back up current table even though it is wrong, just so you can go back. Copy to another device. You should have good backups of any data on your system also.
sudo sfdisk -d /dev/sdc > parts.txt

Fixparts - Repair broken partition tables
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Sevenarth on 2011-04-29
Thanks very much. I post results when it finishes

> root@ubuntu:/home/ubuntu# fixparts /dev/sda
FixParts 0.7.1

Loading MBR data from /dev/sda

**Problem: MBR partitions 2 and 3 overlap!**

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x1549F232
MBR partitions:

                                                   
Number  Boot     Start Sector     End Sector      Status       Can Be Logical              Can Be Primary        Code
   1                 *                   2048              206847            primary         Y                                         Y                                   0x07
   2                       206848             949682474        primary                                                       Y                                   0x07

MBR command (? for help): 
And now, how to fix partitions?

---

### Post by srs5694 on 2011-04-29
I'm the author of FixParts, and IIRC, I coded it to discard primary or logical partitions that extend beyond the end of the disk. It also discards the smaller of two partitions that overlap one another. Thus, if you use FixParts on the disk, it's likely to throw away /dev/sda3.

That disk is very badly messed up. The safest recovery procedure is to buy a new disk and use a Windows file-level (not filesystem-level) tool to clone the current disk to the new disk, then either swap the disks or wipe the first disk's partitions and clone it back. Alternatively, you could back up the disk to some other medium (tape, a stack of DVDs, etc.), wipe the current disk, and restore the backup.

If you attempt to repair the disk directly, there's a risk of making things even worse. One hopeful sign is that the Boot Info Script is reporting a discrepancy between the partition sizes and the filesystem sizes on /dev/sda2 and /dev/sda3. Partitions are just descriptions of sets of contiguous disk sectors. Filesystems reside inside partitions, but filesystems contain their own sizing information, so a filesystem can be smaller than a partition, and that seems to be the case here. Thus, in theory, you should be able to repair the problem using sfdisk in Linux (you can use your WUBI install, if it boots; an Ubuntu install disc in "live CD" mode; or something like [PartedMagic](http://partedmagic.com/)):


[list=1]
[*]Boot Linux and launch a Terminal window.
[*]Type "sudo sfdisk -d /dev/sda > parts.txt"
[*]Copy parts.txt to a USB flash drive, floppy disk, or other removable disk. This copy is your insurance policy against problems.
[*]Open the original parts.txt in a text editor such as gedit.
[*]Reduce the "size" value for /dev/sda2 by 2347 sectors (to 949473279, if the Boot Info Script output is accurate).
[*]Reduce the "size" value for /dev/sda3 by 13058 sectors (to 27090943, if the Boot Info Script output is accurate).
[*]Save your changed parts.txt file.
[*]Type "sudo sfdisk -f /dev/sda < parts.txt" (referring to the changed parts.txt file) to write the changes back to the disk.
[*]Reboot into Windows.
[*]Run Windows CHKDSK on both /dev/sda2 and /dev/sda3 (/dev/sda2 is probably C:, but I have no idea what /dev/sda3's identifier would be in Windows). I'm not positive, but Windows might want to reboot during this process, perhaps for each partition.
[*]Try booting Linux again and running GParted.
[/list]


With any luck, this will fix the problem; but if the Boot Info Script output is bad or if you make a mistake when editing the size values, this could end up making matters even worse. Hence, I *strongly* recommend you make a complete backup before you try this!

---

### Post by srs5694 on 2011-04-29
Sevenart, your last post (#3) appeared after I began typing my earlier reply (#4). As I suspected, FixParts has discarded your /dev/sda3, so you should *not* use it for recovery. If you type "w" in FixParts, it'll make matters worse by deleting your /dev/sda3.

---

### Post by Sevenarth on 2011-04-29
thanks for answer :D
Howewer, the my pc (with hd) is a HP Pavilion p6310it and the three partitions were not made by me but by Hewlett-Packard. In first partition there's SYSTEM the boot loader of Windows 7 located in /dev/sda2 which have the OS and all my datas (about 400 GB, but 100gb can be deleted because are only recorded videos) and the three partition is FACTORY_IMAGE where's located the Windows 7 Installer edited by HP which make system recovery and backups (one time was helpful).

I've a unused external HD, a WD My Passport Essential 500GB, which have only a movie in bluray (30gb) and all western digital utils.

What do i do?

---

### Post by srs5694 on 2011-04-29
Sevenarth, your new information doesn't change anything in my analysis or change my recommendations from post #4.

---

### Post by Sevenarth on 2011-04-29
ok thanks :D
Howewer i did the chkdsk with windows more times but he doesn't see errors. I do the procedure now :D


Ehm...[http://i54.tinypic.com/2rqlqol.png](http://i54.tinypic.com/2rqlqol.png)

Translate:
> C:\Users\Luca>chkdsk
The file system is NTFS.
The volume label is HP.

Warning! Parameter F not specified
CHKDSK run in read-only mode.

File verify in progress (phase 1 of 3)...
 3 percent completed (record of files processed: 296449 of 878336)
The record (128, "") of file segment record 321052 is damaged.
 878336 record of file processed.
File verify completed.
1253 record of big files processed.

Found error. Unable to continue CHKDSK in read-only mode.




Okk... resolved! Now GParted recognize the hd, now i've installed ubuntu :D Thanks very much!

---

### Post by bodhi.zazen on 2011-04-29
Thread closed at OP request
[http://ubuntuforums.org/showthread.php?t=1743608](http://ubuntuforums.org/showthread.php?t=1743608)

---

### Post by Elfy on 2011-04-29
PS - if anyone else looks you'll not be able read that thread link... (staff onlylink)

@Sevenarth - in future you can finf a Thread Solved button in all of your threads so can mark thread yourself.

---

