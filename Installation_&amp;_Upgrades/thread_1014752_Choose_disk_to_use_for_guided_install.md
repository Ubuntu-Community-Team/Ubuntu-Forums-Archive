---
title: "Choose disk to use for guided install?"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Housewife on 2008-12-18
Hi, I'm pretty new around here, and am running into a snag when trying to install ubuntu 8.1 on my machine (alongside winxp).

I have 2 sata drives in my machine; a 150gig and a 640gig.  The 150 has windows on it, and I want to split it down the middle and throw ubuntu on the other half.  The 640gig I want to keep strictly for storage.

When I first ran the install CD, the 150 was listed as sdb1, and the 640 was listed as sda1.  The guided install defaulted to sda1 (the 640), and I couldnt find an option to use sdb1 instead.  

I swapped the sata cables going to each drive, which did turn the 150 into sda1, and the 640 into sdb1, which I thought would solve all my problems, but the installer still wants to guided partition the 640 gig (which is now sdb1)!  Is it just trying to partition the largest drive in my system?  Am I missing something simple that lets me use the other drive (not completely format the other drive, as that is an option, I just want to guided partition it)?

I hope I got that across well, kind of hard to describe.  If anyone could help me out, I'd appriciate it!

---

### Post by Pumalite on 2008-12-18
If you have Vista; allocate space for Ubuntu with Vista's partitioner first. If you have XP; you can use Gparted. In any case is better to go 'Manual' and pick the drives/partitions by yourself
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Housewife on 2008-12-18
Ok, looks like I'm gonna have to go manual then.  Thanks for the info!

Just in case though, does anyone know why its trying to force me to partition my larger hard drive with the guided install?  One thing that concerns me, is when I was trying to get the large drive to be sdb, and the small drive sda, when I first swapped their sata cables and rebooted, I got an error.  It seemed that my system was by default looking to my larger drive (which was sda) for the bootloader, and when I swapped the cables, and that larger drive was now sdb, it wasnt finding any bootloader on my smaller drive.  (damn, that was confusing).  I fixed this by putting the sata cables back to how there were, booting into xp, running VistaBootPro and installing legacy (xp) bootloader to all hard drives.  Now when I swapped my sata cables, everything booted up fine, but I just dont know why its looking (I imagine its still looking at least) at my larger hard drive for the bootloader, even though its now sdB.

I'm sorry, I doubt that makes any sense at all...  I'll just figure out how to manually partition my drives and give it a go :P

---

### Post by presence1960 on 2008-12-18
Housewife, I have 2 hard drives also. An IDE and a Sata. I just went to the manual install and set up the drive I wanted. You will have more flexibility in choosing the size of the Linux and swap partitions and you may even have unallocated space left over if you desire another partition on that drive which you can later format to the file system of your choice with GParted.

---

### Post by Housewife on 2008-12-18
Right on, looks like the general consensus is to go with the manual install, I'll go ahead and go that route.  Thanks again

---

