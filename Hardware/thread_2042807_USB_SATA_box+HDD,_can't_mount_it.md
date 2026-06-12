---
title: "USB SATA box+HDD, can't mount it"
date: 2012-08-15
forum: Hardware
---

### Post by djibdjib on 2012-08-15
Hello,

I've a problem which seems simple but I can't fix it.
I've an external hdd USB box Advance BX-3706SI with a Western Digital Caviar Green (WD20EARX)HDD in it.
I formatted  the hard drive with an ext4 1.7TB partition and a small 512MB swap partition.
When I turn the box on, the ext4 a partition isn't automatically mounted.
However, the box is detected:

```
$ lsusb
Bus 001 Device 007: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
```
The partitions are also detected, but not mounted:

```
$ sudo fdisk -l
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488378646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0008e52d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1         6763365  3905979839  2711964012   83  Linux
/dev/sdd2      3905979840  3907024064     4176900   82  Linux swap / Solaris
```

I tried to manually mount the ext4 partition, but I get the following message:
```
$ sudo mount -t ext4 /dev/sdd1 /media/mountPoint
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Does anyone has an idea about how to mount this partition correctly?

Here is the dmesg output:
```
$ dmesg | tail
[ 3086.146506] sd 5:0:0:0: [sdd] No Caching mode page present
[ 3086.146517] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[ 3086.147403]  sdd: sdd1 sdd2
[ 3086.147415] sdd: partition table partially beyond EOD, truncated
[ 3086.147427] sdd: p1 size 31193731800 extends beyond EOD, truncated
[ 3086.147606] sdd: p2 start 31247838720 is beyond EOD, truncated
[ 3086.150693] sd 5:0:0:0: [sdd] 488378646 4096-byte logical blocks: (2.00 TB/1.81 TiB)
[ 3086.152880] sd 5:0:0:0: [sdd] No Caching mode page present
[ 3086.152894] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[ 3086.152903] sd 5:0:0:0: [sdd] Attached SCSI disk
```
Thank you in advance for your help...

++

---

### Post by oldfred on 2012-08-15
Not sure exactly what the issue is. I have seem similar issues with some of the new 4K drives like yours. Not sure if fdisk works correctly. Try posting this:

sudo parted /dev/sdd unit s print

> Sector size (logical/physical): 4096 bytes / 4096 bytes

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by djibdjib on 2012-08-15
My system is configured in french so the terminal gives me error messages in french. Hope my approx. translation helps...
```
$ sudo parted /dev/sdd unit s print
Avertissement: La taille des secteurs logiques pour le périphérique /dev/sdd est
4096. Tous les modules de GNU Parted ne supportent pas cela pour l'instant :
fonction EXPERIMENTALE.

Erreur: La partition ne peut pas être en dehors du disque ! 
```
It says that "the size of logical sectors is 4096. It is an experimental function and all GNU parted modules don't support it.
Error: the partition can't be off the hard drive."
I've never heard about it, I'll read your links tomorrow, it seems interesting.
++

---

### Post by oldfred on 2012-08-15
My French is not exactly very good. I had two years of High School French taught by a Greek Mademoiselle starting in 1960. I am lucky just to remember I had that class back then much less what ever was in the class. :)

---

### Post by djibdjib on 2012-08-16
Hi oldfred,

I carefully read your links and it was interesting despite I did not understand everything.
Here is the provided command result, in english:
```
$ sudo parted /dev/sdd unit s print
Error: can't have a partition outside the disk
```
As  far as understand the yur links, aligning sectors would induce a gain  in my hard drive performances, but a drive with misaligned sectors seems  to be mountable, which is not my case.
Anyway, I will align my partitions with sectors tonight.
Can you also explain the error message above?

Regards,

J-B

---

### Post by oldfred on 2012-08-16
If drive is MBR, which it looks like as fdisk did show partitions.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

2GB is the maximum you can use MBR with, then larger drives have to use gpt. But Windows will only boot from a gpt drive if you have the newer UEFI not older BIOS. I have gpt on a 160GB drive just to learn about gpt and on my newish SSD. But neither of those have Windows. I had to shutdown my XP as it does not easily work with AHCI and AHCI is needed for the SSD. So my old XP drive is not really used now. Just to test I also used gpt on a 16GB flash drive and did a full install of Ubuntu.

If an external drive which will never boot Windows anyway, you may want to consider using gpt. Windows will read data from a gpt partitioned drive.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by djibdjib on 2012-08-16
Indeed, as I'm not planning to boot on this drive with Windows, I'll go with GPT.
And The hard drive is new, I then can erase the partition table and create a new one.
However, parted doesn't seem to support 4096 logical sector size yet, which other partitionning tool can I use?
Is there any other GUI partitionning tool? Or at least easy to use command line partitionning tool?

Additional question, is there a partition format supported by linux, mac and windows and supporting big files (several GB?)
I'll mainly use this hard drive under linux (on a Raspberry Pi with OpenELEC), I was thinking of using an ext4 partition as main partition with a small NTFS partition to put a .exe allowing windows to mount ext4 partitions and finally a small swap partition, to help the small Raspberry Pi 246MB SDRAM.
What do think about?

Good evening and thank you for yout help!

J-B

---

### Post by oldfred on 2012-08-16
I have used gparted to format my gpt drives, but they are not 4K drives. The author of gdisk is the one who wrote the links on 4K drives, so you might try gdisk.

gdisk is in the Ubuntu repository so you can down load it.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)
The emergency disks that include GPT fdisk are:
    * SystemRescueCd
    * PartedMagic 

If you might ever boot from the drive, you may want to add either an efi partition or bios_grub partition for booting. The efi partition has to be first so it becomes difficult to add later and does not have to be large so it does not really take any space.

This is my standard partition suggestion:
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

If you only have 256K of RAM you really only need 512KB of swap. Full Ubuntu will not run in that little of RAM, but server with maybe a lightweight gui might or possibly Lubuntu.

I do not know what works with Macs. I thought it was FAT, but FAT does not support large files over 4GB and does not have a journal, so it can be difficult to repair if a larger partition. For Windows & Linux, we normally suggest NTFS.

---

### Post by mad gamer on 2012-08-17
According to one review I saw at newegg the WD20EARX isn't working well with external enclosures so maybe its more of a compatabilty issue with the chip in the enclosure. I have a 4K drive (Seagate Barracuda ST2000DM001) and enclosure (Vantex NexStar HX SuperSpeed) on the way so hopefully it will work with my xubuntu install.

This might help [http://linuxconfig.org/linux-wd-ears-advanced-format](http://linuxconfig.org/linux-wd-ears-advanced-format)

---

