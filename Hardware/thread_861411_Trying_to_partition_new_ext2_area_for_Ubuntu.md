---
title: "Trying to partition new ext2 area for Ubuntu"
date: 2008-07-16
forum: Hardware
---

### Post by Mecharuva on 2008-07-16
So, I have two hard drives, an 80GB Master, and a 320GB Slave.
I've partitioned 20GB of the Master for Linux to use, no problems, and another 2GB for a Linux Swap, also no problem.
I decided I wanted more space for Linux to play in, so I wanted to use 100GB of the Slave for this.
So I boot an 8.04 Live CD, start GPartEd, and set up 100GB on the Slave as an ext2 Primary drive.
I've done this over and over, and I always get this result:
(Taken from Properties of it)
Name:  disk
Type:  folder
Contents:  1 item, with size 16.0KB (some contents unreadable)
Location:  /media
Volume:  107.4GB Media
Free Space:  94.2GB
Modified:  Wed 16 Jul 2008 02:47:21 PM EDT
I have no idea how to fix it.
I just want it so I can try out some games under Wine.

---

### Post by logos34 on 2008-07-17
You don't have to boot the live cd to partition and format another disk.  Only when you're resizing root do you need to do so (because it cannot be mounted).  But in this case you could run gparted from root.

I don;t see anything wrong except that something is taking up ~13 gb.  Maybe that's the space reserved for root/admin.  The one item may be a lost+found folder

It's mounting by default at /media/disk.  You can change that so it automounts at a specific place every boot:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

