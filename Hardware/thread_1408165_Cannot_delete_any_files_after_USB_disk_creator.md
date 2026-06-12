---
title: "Cannot delete any files after USB disk creator"
date: 2010-02-16
forum: Hardware
---

### Post by Michael577 on 2010-02-16
HELP!! My new usb drive (PNY 4GB the small one) not a hard drive won't let me delete the files because of a read-only after a USB startup disk creator failer! I've tryed to format it using gparted as root but it gave me a Input/Output error. Please help me out I need it for school tomorrow! ](*,)
 By the way, the source of thismess sems to be casper and the ldlinux.sys.

---

### Post by pi/roman on 2010-02-16
You could try fdisk from terminal.
```
sudo fdisk -l
```
to find the path to your drive then
```
sudo fdisk path_to_your_drive
```
then press d to delete the partition on the drive and press n to make a new one and you will need to choose the file system for it

---

### Post by Michael577 on 2010-02-16
umm.. I did it and now I'm confused with this 

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
e
Partition number (1-4): 1
First cylinder (1-1018, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-1018, default 1018): 
Using default value 1018

Command (m for help): 


Is this right?

---

### Post by pi/roman on 2010-02-16
yes you can press p now to check your partition and press t to change the file system type.  And when you are ready press w to write it then the changes will take effect. then you may need to run partprobe to make your computer recognize the changes.

---

### Post by Michael577 on 2010-02-16
I tryed it again and got this 

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): dc
Selected partition 1

Command (m for help): nc
Command action
   e   extended
   p   primary partition (1-4)
p1
Partition number (1-4): 1-4
First cylinder (1-1018, default 1): 1018

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

Error closing file
michael@michael-desktop:~$

---

### Post by pi/roman on 2010-02-16
I wasn't sure what there error meant so i searched for it and came up with this page: [http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html](http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html)
It looks like if you use partprobe and then run mkfs on the drive it may fix it.
so for instance you could make a fat32 filesystem by
sudo mkfs.vfat -I path_to_drive

---

### Post by Michael577 on 2010-02-16
Ok I re-re did it 

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
e
Partition number (1-4): 1
First cylinder (1-1018, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-1018, default 1018): 
Using default value 1018

Command (m for help): p

Disk /dev/sdg: 4040 MB, 4040724480 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0x000cbcfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        1018     3944719    5  Extended

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): l

 0  Empty           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 1  FAT12           39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 2  XENIX root      3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 3  XENIX usr       40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 4  FAT16 <32M      41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 5  Extended        42  SFS             86  NTFS volume set da  Non-FS data    
 6  FAT16           4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 7  HPFS/NTFS       4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 8  AIX             4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 9  AIX bootable    50  OnTrack DM      93  Amoeba          e1  DOS access     
 a  OS/2 Boot Manag 51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 b  W95 FAT32       52  CP/M            9f  BSD/OS          e4  SpeedStor      
 c  W95 FAT32 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 e  W95 FAT16 (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  GPT            
 f  W95 Ext'd (LBA) 55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
10  OPUS            56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
11  Hidden FAT12    5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
12  Compaq diagnost 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
14  Hidden FAT16 <3 63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
16  Hidden FAT16    64  Novell Netware  af  HFS / HFS+      fb  VMware VMFS    
17  Hidden HPFS/NTF 65  Novell Netware  b7  BSDI fs         fc  VMware VMKCORE 
18  AST SmartSleep  70  DiskSecure Mult b8  BSDI swap       fd  Linux raid auto
1b  Hidden W95 FAT3 75  PC/IX           bb  Boot Wizard hid fe  LANstep        
1c  Hidden W95 FAT3 80  Old Minix       be  Solaris boot    ff  BBT            
1e  Hidden W95 FAT1
Hex code (type L to list codes): c
You cannot change a partition into an extended one or vice versa
Delete it first.

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.

and nothing changed! The file still refuses to be deleted! and whats partprobe and how do you activate it?

---

### Post by pi/roman on 2010-02-16
just type partprobe in the terminal and hit enter and hopefullly it look like the drive should be operable then

---

### Post by Michael577 on 2010-02-16
no luck... it's still there and it keeps on saying cannot delete because a read only file system

---

### Post by pi/roman on 2010-02-16
You could try cleaning it with this command
```
sudo dd if=/dev/zero of=/dev/sdz bs=1k count=16k
```where /dev/sdz is the path to your drive
then write a new filesystem to it:
```
sudo mkfs.vfat -I path_to_drive
```

---

### Post by Michael577 on 2010-02-16
Ok I got this 

michael@michael-desktop:~$ sudo dd if=/dev/zero of=/dev/sdg bs=1k count=16k
16384+0 records in
16384+0 records out
16777216 bytes (17 MB) copied, 2.08852 s, 8.0 MB/s
michael@michael-desktop:~$ sudo mkfs.vfat -I /dev/sdg
mkfs.vfat 3.0.3 (18 May 2009)
mkfs.vfat: unable to open /dev/sdg
michael@michael-desktop:~$

---

### Post by Michael577 on 2010-02-16
nothing changed at all

---

### Post by pi/roman on 2010-02-16
Maybe this drive has some kind of hardcore write protection on it. You could try palimpsest disk utility under system / administration. It would probably give the same results as gparted.

---

### Post by pi/roman on 2010-02-16
Or maybe try zeroing the whole drive which might take a while.[FONT=monospace]
[/FONT]```
dd if=/dev/zero of=/dev/sdg
```[FONT=monospace]

[/FONT]

---

### Post by Michael577 on 2010-02-16
I've heard of that does it show the progress of it or it just sits thier?

---

### Post by pi/roman on 2010-02-16
Its the same thing as the other command you already ran except the other one only did the first 16 mb.

---

### Post by Michael577 on 2010-02-16
k' then I'll try that.... do I need to un mount the drive first?

---

### Post by pi/roman on 2010-02-16
Yes the drive should be unmounted.

---

### Post by Michael577 on 2010-02-16
k' going to do it now I'll post the result

---

### Post by Michael577 on 2010-02-16
quick Q' will the thing report back the result after it's done?

---

### Post by dE_logics on 2010-02-16
It's a typical flash storage failure.

Get your warranty replacement.

Burn the data to a DVD for the mean time. And always stay away from Kingston.


Also -- notice that that whatever files that you copy to your drive might get corrupt...to see this fill the pendrive with a large file and check out it's md5sum. The original and the copied file should have the same checksum.

---

