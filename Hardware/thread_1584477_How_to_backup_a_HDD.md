---
title: "How to backup a HDD"
date: 2010-09-29
forum: Hardware
---

### Post by BogdanMare on 2010-09-29
Hi people,

As I am new to this forum and also to the "linux world" (I have about 2 months of succesfull, "study-hard", pleasureful linux experience - Ubuntu 10.04 distro).
I just finished installing a mail and web server and after almost 2 weeks spent on configuring it to work right I want to make sure I wont have to do it again ).

I heard a couple of things about this "dd" command and I what to be sure I got it right. 
First of all, let me explain what I have and what I want to do with what I have 
- I have one 320 GB HDD which containes the linux OS + email&web servers
- I have another 80GB HDD which containes some data (dont know what exactly)
- I want to copy the contents of the 320 GB HDD (out of which maybe 30-40 GB is being used) to the 80 GB HDD. This means an EXACT replica of the OS with the settings for the servers, etc.
- I will connect the two HDD on SATA and boot-up ubuntu from a live CD and from there run "dd", right?!

Now for the questions 
- Can the 80GB HDD be used in this case or do I need at least a 320 GB HDD (same as the original HDD containing the OS)?
- Does the 80GB HDD have to "clean" (Unllocated space), or will "dd" erase all data from the 80GB HDD and replace it with the contents of the 320 GB HDD?

If you have any other sugestions please tell me 

Thanks in advanced! :)

---

### Post by rtomakov on 2010-09-29
The easiest way: use ghost4linux (g4l). You can download it as bootable .iso, it supports both local and network backup. Very similar as nortoh ghost, it creates compressed images of all disk or disk partition.

---

### Post by prshah on 2010-09-29
> **BogdanMare said:**
> 
- I want to copy the contents of the 320 GB HDD (out of which maybe 30-40 GB is being used) to the 80 GB HDD.

- Can the 80GB HDD be used in this case or do I need at least a 320 GB HDD (same as the original HDD containing the OS)?
- Does the 80GB HDD have to "clean" (Unllocated space), or will "dd" erase all data from the 80GB HDD and replace it with the contents of the 320 GB HDD?

"dd" is not suitable for this purpose. Use a partition backup tool such as partimage.

if you want to use "dd", you will need same or larger size HDD as the HDD you want to backup, irrespective of used space.

"dd" will erase everything on the target drive. The backup drive will be replicated, down to every byte.

I STRONGLY recommend that you use partimage instead of "dd". It will do exactly the job you want and is very easy to use.

---

### Post by dirty_harry on 2010-09-29
I use clonezilla... because partimage does not support ext4 as far as I know!

> **[COLOR=#3333ff]Features of Clonezilla[/COLOR]**

 
[LIST]
[*]Free (GPL) Software.
[*]Filesystem supported: (1) ext2, ext3, [COLOR=red]ext4[/COLOR], reiserfs, reiser4, xfs, jfs of GNU/Linux, (2) FAT, NTFS of MS Windows, (3) [COLOR=red]HFS+[/COLOR] of Mac OS, (4) [COLOR=red]UFS[/COLOR] of FreeBSD, NetBSD, and OpenBSD, and (5) [COLOR=red]VMFS[/COLOR]  of VMWare ESX. Therefore you can clone GNU/Linux, MS windows,  Intel-based Mac OS, and FreeBSD, NetBSD, and OpenBSD, no matter it's  32-bit (x86) or 64-bit (x86-64) OS. For these file systems, only used  blocks in partition are saved and restored. For unsupported file system,  sector-to-sector copy is done by dd in Clonezilla.
[*][COLOR=red]LVM2[/COLOR] (LVM version 1 is not) under GNU/Linux is supported.
[*]Grub (version 1 and [COLOR=red]version 2[/COLOR]) is supported.
[*][COLOR=red]Multicast[/COLOR] is supported in Clonezilla  SE, which is suitable for massively clone. You can also remotely use it  to save or restore a bunch of computers if PXE and Wake-on-LAN are  supported in your clients.
[*]Based on [Partclone]("http://partclone.org/") (default), [ Partimage]("http://www.partimage.org/") (optional), [ntfsclone]("http://www.linux-ntfs.org/")  (optional), or dd to image or clone a partition. However, Clonezilla,  containing some other programs, can save and restore not only  partitions, but also a whole disk.
[*]By using another free software [drbl-winroll]("http://drbl-winroll.sourceforge.net/"), which is also developed by us, the hostname, group, and SID of cloned MS windows machine can be automatically changed.
[/LIST]
live-cd @ **[http://clonezilla.org/](http://clonezilla.org/)**

---

