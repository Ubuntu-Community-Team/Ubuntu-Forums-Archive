---
title: "Ubuntu Server 8.10 wont boot after install on HP ProLiant ML110 G5...RAID? SATA?"
date: 2009-03-11
forum: Hardware
---

### Post by o891 on 2009-03-11
Hi guys,

I just received a new HP ProLiant ML110 G5 Server with the specs as seen on this page: [LINK]("http://h10010.www1.hp.com/wwpc/ch/de/sm/WF06b/15351-15351-241434-3328424-3328424-3577708-3840859.html")

After booting the system from the Ubuntu 8.10 Server (32bit) CD I was able to partition one of the drives (although it has two drives) and install. For other users: don't worry about the partition bar being stuck at 33%, it is not stuck, the partitioning just takes a bit of time.

Now the problem is that after the end of the installation and ejecting the disk, when I try to boot the system it just ends up with a black screen and the blinking cursor. It seems like it cannot find the hardrive...

The HP Embedded RAID Setup Utility doesnt find any drives either. The system uses the HP Smart Array E200i/128 MB BBWC Controller and it seems like it doesnt find a drive to boot from.

In the BIOS, under Harddisk Configuration is does no show any SATA ports being used, apart for SATA Port 5 which is set to CD-ROM.

Has anyone encountered this problem before?? Please post anything that seems remotely similar or any tipps suggestions of what I could try...

I used to Install CD to get to a shell, but I cant find any of the drives there either... Maybe it has something to do with the installer not installing GRUB right? Or into the right location...?

Thanks for any help!!
Oliver

---

### Post by feenster on 2009-04-15
Hi,
We are having exactly the same problem, with the same server/software. Did you get this fixed?

Cheers,
   Matt

---

### Post by gtfourdreams on 2009-04-22
Try 8.04 LTS. On my Proliant DL380G3, 8.10 installed fine for me, but at boot time I had issues also. It would hang after about 10-15 seconds into the boot. I don't know how to fix it, but 8.04 works fine for me.

DL380 G3 has a SmartArray 5 if that makes a difference.

otherwise, if you have time, someone should be the guinea pig for 9.04. let us know if that one works. :P

---

### Post by feenster on 2009-04-22
Hi,
Thanks for the reply. We got our problem sorted in the end.

It seems an earlier install failed, but left 2 extra partitions on the disk. We ran the installer again and they didn't get removed (for whatever reason, maybe user error). After a third install, the partitions were removed and the install went fine. We now have a working server :-)

Matt

---

