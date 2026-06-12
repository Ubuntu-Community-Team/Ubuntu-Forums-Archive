---
title: "Gutsy installation goes fine - Vista gets ruined on Asus F3Sv"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by theseeker on 2007-09-05
I gave Kubuntu Gutsy Tribe 5 a try on my new laptop, the Asus F3Sv. 
There are minor problems, like bluetooth not working, as well as trouble with the nvidia card driver, but other than that it runs smoothly. I don't have the faintest idea of whether this is primarily an Ubuntu or Vista problem, but I'll have to ask for your kind help here!

THE PROBLEM

I installed Gutsy through the alternate install CD, where I partitioned the unused space I had previously created with windows partitioner by resizing the Vista partition. So, the existing partitions are now: Recovery partition, VistaOS partition, reiserfs partition (root - primary), swap (logical), ext3 (/home - logical).

I proceed with the installation, everything goes fine and I get a running Kubuntu Gutsy Tribe 5. BUT, when I choose to load Windows Vista through Grub, I only get to the Vista splash screen (without login name/password area present) and then it crashes, giving me the attached image with the huge ERROR window, and of course a headache. I only get a mouse cursor, without being able to close the window or do anything else but hard shutdown! 

I tried to use the ASUS Recovery CD, but the results are the same. So please, help me shed some light on this, as I need dual booting!!!

---

### Post by theseeker on 2007-09-06
I managed to solve the issue at last. Here is what I did, in case someone runs into the same problem. I acknowledge that the best solution is to throw away vista completely, but I still need them. 
Anyway here it goes:
I downloaded the gparted LiveCD and started erasing partitions -except the recovery one. Then created a new ntfs partition and ran Vista recovery DVD. The installation was smooth but the old grub installation persisted (broken of course) on the MBR, so I installed Kubuntu Tribe 5 on top, and everything was fine! I only had to modify /boot/grub/menu.lst a bit to point it at the correct Vista partition (hd0,1).

The only question that still runs through my head, is what if someone doesn't want to reinstall a linux distro? How does he repair the MBR, since the recovery CD doesn't offer a "recovery console" to use a command like fixmbr?
I guess the only answer would be either to send it to Asus, or install grub only, and fix it to load Vista quietly. Any ideas?

---

### Post by vacman1 on 2007-09-06
probably over my head here, but what about using a boot manager application...cant remember the name of any ... other than grub?  thought about trying this myself next time i install ubuntu.

[http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10716910.html?tag=lst-0-2](http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10716910.html?tag=lst-0-2)

there it is... this is an actual OS (with live cd) ... haven't tried this yet, but here's the info;

Publisher's description of Parted Magic LiveCD 
 view larger From Partedmagic: 
Optimized at approximately 30MB, the Parted Magic LiveCD OS employs core programs of GParted and Parted to handle partitioning tasks with ease, while featuring other useful programs (e.g. Partition Image, TestDisk, fdisk, sfdisk, dd, and ddrescue) and an excellent set of documentation to benefit the user. An extensive collection of fileystem tools are also included, as Parted Magic supports the following: aufs, ext2, ext3, ext4, fat16, fat32, hfs, hfs+, jfs, linux-swap, ntfs, ocfs2, reiserfs, reiser4, xfs, and zfs. 

Version 1.8 is updated with: Linux-2.6.22, parted-1.8.7, ntfsprogs-200702071432 (with Windows Vista support), ntfs-3g-1.710, and GParted-0.3.4.

---

### Post by vacman1 on 2007-09-06
This might help :)

[http://www.download.com/MbrFix/3000-2094_4-10485991.html?tag=lst-0-1](http://www.download.com/MbrFix/3000-2094_4-10485991.html?tag=lst-0-1)


Publisher's description of MbrFix 
 view larger From Systemintegrasjon: 
Tool to fix or create Master Boot Record (MBR) on hard disks (supports Windows PE). Supported commands: display drive information, drive size in MB as return value, display partition information, save MBR and partitions to file, restore MBR and partitions from file, update MBR code to W2K/XP/2003, delete partitions in MBR, read disk signature from MBR, write disk signature from MBR, generate disk signature in MBR, read state from byte 0x1b0 in MBR, write state to byte 0x1b0 in MBR, get volume information for partition.

---

### Post by illy on 2007-09-10
Hi,

I had the exact same problem. {couldnt get any linux distros other than gutsy to run}. The way i Fixed it/got vista back {gaming only} was got hold of a windows vista disk and used the mbr fix that everyone talks about in the recovery console. reformatted the mbr and then used a recover image i made after i installed all my preferred software set the way i wanted it. i suppose at this point the asus recovery discs would also work.

Anyway hopefully one day the f3sv will run linux in a dual boot config. Hope this helps.

Cheers Illy.

---

