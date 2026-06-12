---
title: "How best to partition my disk?"
date: 2008-07-23
forum: General Help
---

### Post by rtg20 on 2008-07-23
Hi, I am about to install Ubuntu Linux onto my desktop, having fallen out with Windows Vista...

However I plan to use Windows XP in a virtual machine, so I can use Photoshop etc. for  my photography.

i was wondering if someone could advise how best I should partition my hard disk? I don't know much about partitioning for Linux. The drive is around 110 GB in size altogether.

thanks for the help,

Richard

---

### Post by Habbit on 2008-07-23
With so much space available, you'll probably want to have a separate /home (user data) partition, so you have an easier time backing up and/or at reinstalls (if ever needed). If you don't have any other particular needs (i.e. separate mythtv or p2p partition), this should fit you:

/dev/sda1: primary, 150M, ext2 or ext3, /boot
/dev/sda2: extended - rest of the space
/dev/sda5: logical, 10G, ext3, /
/dev/sda6: logical, 2G, swap
/dev/sda7: logical, 98G, whatever FS you like, /home

On filesystems for the /home partition: I use ReiserFS, but this requires that you have a stable system (i.e. not a lot of power outages, etc), because ReiserFS is not the most resilient to physical corruption - after some six months and ~10 power outages, I had to rebuild tree and lost one (10 GB video) file. Ext3 is more tried, but slower sometimes. JFS is more CPU-friendly, while XFS performs very well with big files (i.e. mythtv, video editiong, etc.).

On swap: if you have more than 2GiB of memory you should not need it unless you do memory-hungry tasks (DB hosting, AV edition), but it's always good to have some if you don't want an untimely meeting with OOM-killer

---

### Post by rtg20 on 2008-07-23
thanks for the reply. let me see if I understand this. /sda5, 6 and 7 fit inside /sda2, right...?

/sda5 will hold things like the software to run the desktop...?

and /home is where I put my stuff...?

Would I install the Virtual Box software I want to use ([http://www.virtualbox.org/](http://www.virtualbox.org/)) on /sda5...?

Can i just use NTFS on /home, to keep the virtual Windows install happy...? Or should i create another, smaller NTFS partition.

thanks,

Richard

---

### Post by Habbit on 2008-07-23
Yes, sda5+ all go into sda2.
Yes, /home is where all the users' home directories are created and where all their personal data is stored. Apart from their mounted folders in /media, they usually have readonly access to the rest of the filesystem hierarchy.

Most likely, yes: the VirtualBox program files would go into a directory within the root partition, like /usr or /opt. Definitely not in /home, though the virtual machine data _will_ probably be saved in /home.

You _could_ use NTFS for /home, since there is a readwrite NTFS driver for Linux (ntfs-3g) and it's included with Ubuntu by default, but iIrc, you'd lose any form of user-level security because ntfs-3g does not use the NTFS security features. Usually, virtual machines' disks are a big file in the host filesystem, not a disk/partition of their own. Thus, you don't need to worry about that.

---

### Post by rtg20 on 2008-07-23
thanks for the reply. this is more of a virtualbox question, but maybe you are familiar with it. if i want to open say a photo using Photoshop under XP Pro under VirtualBox, would I need to move the photo to an NTFS partition first...? so Windows could read it...?

if so, maybe I should have a separate /home partition that was NTFS and another /home partition in ext3 (or ext2...?) for everything else...?

thanks!

---

### Post by Habbit on 2008-07-23
I'm not familiar with VirtualBox itself, but I've user other virtualization apps like VMWare, Bochs and QEMU; and in all of them the virtual machine disk is a file in the host machine filesystem, like "/home/user/My Machines/Windows XP Pro/xppro.img". Moreover, they usually do not have direct access to the host disks and partitions, so you should not create any kind of additional partition.

Most VM software establish a virtual network between the guest and the host machines: you could use that to transfer files. Additionally some VM apps offer some "shared folders" feature which you could also use.

---

### Post by rtg20 on 2008-07-24
thanks for the help!

---

