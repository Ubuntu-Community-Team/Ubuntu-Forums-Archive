---
title: "HP MediaSmart EX470 + 3TB Drives"
date: 2013-09-27
forum: Hardware
---

### Post by nAcDbhD on 2013-09-27
Hi all,

I've also posted this over on the MediaSmart Forums for those who may have seen that post, but thought I'd post here, as well. For those unfamiliar, the EX470 is a headless HP box with four drive bays and a basic hardware stack.

I was able to install Ubuntu 12.04 LTS onto the 1 TB (system) drive by way of installing it from another system, and transferring the drive into the EX470. Whenever I try and toss in a single 3 TB drive, though, the server refuses to respond to any sort of ping requests (which, by nature of it being headless, is the only way I can control it).

I've gathered that this isn't a hardware limitation - the server supposedly supports 3 TB drives with either Windows Home Server 2011, or Windows Server Essentials 2012 - which leads me to believe it's a driver limitation, since I *know* Ubuntu 12.04 supports 3 TB drives (I tested this on another machine).

Anyone have any ideas as to why Ubuntu may be sticking?

---

### Post by nAcDbhD on 2013-09-29
Quick self-bump. Anyone have some ideas?

---

### Post by randypfau on 2014-04-24
the same thing happens to me... I dont think it has anything to do with the size of the drive. I cannot add *ANY* hard drives to my other 3  front SATA Hard Drive slots. When I do... ubuntu doesnt detect them via hotswap, when I try reboot, It does not boot the filesystem on the HD in slot 1. I have to pull out the additional drives, and reboot again. After doing that I am able to ping and connect via ssh again... Im stumped.. Im led to believe it has somthing to do with the bios. or that 256 built in USB drive that the bios is hardwired to boot from.. Im doing everything headless without vga cables so its been interesting

---

