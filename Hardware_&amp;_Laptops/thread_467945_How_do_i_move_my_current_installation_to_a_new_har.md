---
title: "How do i move my current installation to a new hard disk?"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by padmanabh on 2007-06-08
I'm in a situation here....
I have WD 80 GB HDD (IDE) which has My XP and Kubuntu feisty on it right now.
I have a new 250 GB Seagate SATA HDD. Now I want to move my current XP and Kubuntu installations to SATA drive and use the 80 GB drive as portable drive.

How do i do this?. Some people told me I have to use Norton Ghost or some Disk Image creation utility for this ...what is that?...how do i use it?

---

### Post by chewearn on 2007-06-08
When I need to clone my linux partition, I always used the gparted livecd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Only thing to keep in mind is, you need to reinstall grub onto the new harddisk.

But I don't have a dual boot situation right now; not sure whether gparted will handle Windows XP partition.

In the past, I cloned Windows XP using DriveImage XML:
[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)

---

### Post by padmanabh on 2007-06-09
OK ....One part is done....I cloned the whole HDD using HDClone.
Now the new SATA HDD is my primary master and old one is secondary master.
When I run gparted from kubuntu....i can see all my previous partitions plus 160 GB of free space....**but i cannot see my old HDD partitions.**
I guess that means I am booting successfully through SATA now....also, in XP i see all the previous drives plus the exact copies produced by cloning.

Th Q is now...should i go live with the SATA HDD and format my old HDD altogether because i want to use it as portable HDD....or should i keep it just in case some thing messes up?

---

### Post by chewearn on 2007-06-10
Normally, I just kept my old cloned HD; but that's because I have a couple spare of HD lying around.  It is always wise to have a backup.

But if you are tight on space, it will be better to use the old HD as data backup; those important files you simply can't loose.  The OS can always be rebuilt (except it is a hassle each time).

---

### Post by padmanabh on 2007-06-10
Hmm Thanks....I have 1-2 GB left in the old drive...guess i shouldn't format it unless i need to transfer something really big....

---

