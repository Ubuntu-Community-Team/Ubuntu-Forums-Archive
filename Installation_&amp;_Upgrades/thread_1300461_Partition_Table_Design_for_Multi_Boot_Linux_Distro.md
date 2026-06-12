---
title: "Partition Table Design for Multi Boot Linux Distro, using Grub bootloader"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by meka4996 on 2009-10-25
##Updated on 22 May 2010 for Win XP behavior
Partition Table Design/Scheme/Planning for Multi Boot Many/Multiple Linux Distro, Windows OS, or Mac, using Grub bootloader[GRUB 0.97 Legacy]
check your existing partition table:
$ sudo fdisk -l

This is my partition table design on paper![the spaces are not shown, sorry]
Name,FileSys,MountPoint,Size, Linux form, Grub form
Winxp       NTFS  na   200MB   /dev/sda1   (hd0,0)
Ubuntu      ext3  /     15GB   /dev/sda2   (hd0,1)
LinuxMint   ext3  /     10GB   /dev/sda3   (hd0,2)
Extended    ext3  na           /dev/sda4   (hd0,3)  
## All the partitions above are primary partitions.
## All the partitions below are logical partitions.
Bootloader1 ext3  na   200MB   /dev/sda5   (hd0,4)  
Backup      ext3  na   200MB   /dev/sda6   (hd0,5)
 
Winxp       ntfs  na    10GB   /dev/sda7   (hd0,6)
MacOSX      hfsplus na  10GB   /dev/sda8   (hd0,7)
DistroY     ext3  /     10GB   /dev/sda9   (hd0,8)

Data1       ext3  na    15GB   /dev/sda10  (hd0,9)
Data2       ext3  na    15GB   /dev/sda11  (hd0,10)
Data3       ext3  na    15GB   /dev/sda12  (hd0,11)

Ext4        ext4  na    1GB    /dev/sda13  (hd0,12)
NTFS        ntfs  na    1GB    /dev/sda14  (hd0,13)
FAT32       fat32 na    1GB    /dev/sda15  (hd0,14)
Swap        swap  swap  1GB    /dev/sda16  (hd0,15) 

##Note, the small partiiton at the beginning is for WinXP, because it will install some small booting files on partition 1 whether you like it or not... but you can still install the rest in any other logical partitions.


----------== original post
Make the partition table on paper first
## 15GB for Ubuntu because my vitualization[VirtualBox] alone takes 4GB
## For faster Linux operations, install Ubuntu in the front[low numbered cylinders]

## Reserve Primary 1 to 3 for Windows OS or BSD..., Linux can pick any other partitions to install

## NO shared /boot partition!!! each distro is installed into each / partition, and the distro's bootloader[Grub or Lilo] is installed into that partition as well at the same time, for easy chainloader Multi boot

## NO shared /home partition! Use Data_sdaX partitions!
      Make [keyboard] shortcuts inside every distro's /home

## One main bootloader partition[5 BM/distro], see reference below...


Before making changes to partition table...
## Make sure the NTFS drive is not too fragmented if resizing it
## BACK UP THE BOOTLOADER MENU and ALL DATA!!!
## Boot from a Live CD for partitioning, NOT from an HDD installed distro! Unmount the HD or USB that you want to partition 
## fdisk is more reliable then GParted


When installing a new distro...
## Do not allow any distro to format any partition during it's installation. Tell it to use the already existing partition that you have created already.

## when installing a new distro, just specify swap partition, / partition, and also set the distro's bootloader to be installed into that / partition[Not MBR!!!]

When adding another distro or upgrading existing distro...
## Just install the new distro (instead of upgrading) as many times as you'd like into its own / partition for a clean install(upgrade). Easy!
## No hacker distro is installed, unless you put a password on Grub!

see more details at ...
Moving from Dual Boot to Multi boot [Dedicated GRUB Partition]
[http://ubuntuforums.org/showthread.php?t=1169648](http://ubuntuforums.org/showthread.php?t=1169648)

Install Ubuntu in the front[low numbered cylinders]
[https://help.ubuntu.com/community/WindowsDualBoot#Disadvantage%20of%20Installing%20Ubuntu%20after%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Disadvantage%20of%20Installing%20Ubuntu%20after%20Windows)

HowTo: Partitioning Basics
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

New HOWTO: Linux Partition HOWTO
[http://linuxplanet.com/linuxplanet/tutorials/3174/5/](http://linuxplanet.com/linuxplanet/tutorials/3174/5/)
Partitioning Windows and Ubuntu
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

GRUB Page
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

swap partition size
[http://tldp.org/HOWTO/Partition/requirements.html](http://tldp.org/HOWTO/Partition/requirements.html) 

A Short Guide to Partitioning a Hard Drive for a Linux System
[http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System](http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System)

JustLinux Web Forums, by saikee, 
A grub menu booting 100+ systems of Dos, Windows, Linux, BSD
[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

How to install and boot 145 operating systems in a PC.
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Just booting tips
[http://www.justlinux.com/forum/showthread.php?t=144294](http://www.justlinux.com/forum/showthread.php?t=144294)

How to use Grub2 to boot Linux manually
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)

How can a Linux user multi boot a new additional Linux?
[http://www.justlinux.com/forum/showthread.php?s=&threadid=134658](http://www.justlinux.com/forum/showthread.php?s=&threadid=134658)

A lazy way to increase multi-booting in Linux
[http://forums.pcper.com/showthread.php?t=401513](http://forums.pcper.com/showthread.php?t=401513)

How to Multi-boot (Maintain more then 2 OS)
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

GRUB bootloader - Full tutorial 
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

Multiple-booting Guide by Ghosh
[http://www.faqs.org/docs/win_bsd/introduction.htm](http://www.faqs.org/docs/win_bsd/introduction.htm)

Multi Distribution Boot Howto
[http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto](http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto)

Making a Dedicated Grub Partition
[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

Note: Say if you delete partition (hd0,2), then the UUID of partition (hd0,3), (hd0,4), (hd0,5),..., and UUID of swap partition will change, plus (hd0,3) will change to (hd0,2)..., causing boot errors.
So either you only resize partitions, or edit the sub menu menu.lst, ok?

To find UUID: ```
$ sudo blkid 
```

Thanks for above articles.
Any suggestions/corrections welcome

---

### Post by meka4996 on 2010-05-22
##Updated on 22 May 2010 for Win XP behaviour. See original post.

---

