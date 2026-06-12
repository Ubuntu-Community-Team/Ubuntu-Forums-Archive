---
title: "Installing Ubuntu on 2nd Hard Drive"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by afarlow on 2009-03-15
I have 2 hard drives on my computer. The first one is 120 gigs and has Windows Professional with Linux swap to Suse. I have just bought a 2nd hard drive and want to load just Ubuntu on it. Within Windows and Partition Magic I created it to run ext2 and on the 2nd drive. Every time I try to install it, it locks up on me and fails. Does anyone have any ideas?

---

### Post by tommcd on 2009-03-15
Don't use Partition Magic in Windows to partition a drive for linux. Use a Parted Magic or GParted live CD:
[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Also, you should use the ext3 file system for jounaling support, unless you have a specific reason for wanting ext2. The Ubuntu installer should be able to partition the drive just fine though. 

And welcome to the Ubuntu forums!

---

### Post by afarlow on 2009-03-16
I downloaded and wrote to a CD this morning. I downloaded the partedmagic. I will see if it will format from that ISO. Thanks for your help. I will let you know how it turns out. Another question what is the difference between ext2 and ext3?

---

### Post by tommcd on 2009-03-17
> **afarlow said:**
>  Another question what is the difference between ext2 and ext3?
Ext3 has journaling support, while ext2 does not. What this means is  that if your system crashes, or the power goes out and you are not on a UPS battery backup, then the file system will 'remember' (for lack of a more technical word) all your operating system files and data.  So when you reboot your system and data will be just fine! The ext2 file system does not have this feature, so it is (theoretically)  more susceptible to data corruption due to crashes. 
It is sometimes said that ext2 is a bit faster than ext3; although in practice I don't think this is a significant difference from what I have read.
Ubuntu 9.04 will include ext4 support. So stay tuned...!

---

### Post by miltk on 2009-04-17
i want to dual boot. i have an old machine with windowsME, so this is

---

