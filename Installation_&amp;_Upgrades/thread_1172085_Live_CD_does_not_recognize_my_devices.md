---
title: "Live CD does not recognize my devices"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by Messyhair42 on 2009-05-28
I have been trying to downgrade Jaunty to Hardy for stability reasons and the partitioner included in the liveCD does not recognize either of my hard drives, even when the Jaunty drive is disconnected. I have tried this with Hardy and Jaunty LiveCD's as well as liveCD's for both Fedora 10 and Knoppix 6
I'm currently using the same computer with Intrepid on a 2nd hard drive and i can mount the Jaunty drive but file access is difficult. opening files is very hit and miss, copying is much the same, if i try to copy from Jaunty drive to Intrepid drive i get anywhere between 512kB and 50-60 MB copied before it gives me error messages. also if i unmount the drive i cannot remount it until i reboot. if i can't find a solution here i'm contacting my equipment mfgrs of the HD.

---

### Post by Richardcavell on 2009-05-28
Messyhair,

What sort of computer and hard drive setup do you have?

Do you have a program such as Partition Manager or GParted that can give us some output to show what your partitioning looks like?

Richard

---

### Post by Messyhair42 on 2009-05-28
I have a 160GB HD containing Intrepid with a single separate partition for swap and a 1TB HD with Jaunty. /, swap, /usr, /var, /temp, and /home are all separate partitions with /home being the majority. it is still possible for me to *boot* into Jaunty but it's not stable for more than a couple seconds. here is a screenshot from gparted of /dev/sda (Jaunty)
thanks for the help

---

### Post by Mark Phelps on 2009-05-28
Tell me the 1TB drive is NOT a Seagate, please!!  I've been using Seagates for years (back when they cost REAL bucks!) and was about to get a new 1TB drive when I read about the rash of drive failures on their 1TB and 1.5TB drives.  So, I went with WD instead -- and haven't had any problems.

If it's not the drive itself, presuming that it's a SATA drive, it could be the drivers.  I've been running SATA drives on a MS Windows box for a while and in the early days of Vista, I kept getting filesystem corruption, BSODs, and crashes -- until I got an updated controller driver from Nvidia and that fixed the problem.

Know that doesn't solve a Linux-based machine, but it still could be the problem.

---

### Post by Messyhair42 on 2009-05-28
It was one of the Seagate drives affected by bad firmware but i promptly updated it when the fix came out and haven't had the "bricking" problem that hit the series of drives. i was using Jaunty for a few weeks before it screwed up on me and windows XP on the drive for a few months before that. I'm wondering if it's the drive itself or if a format would set it right. i've given up on saving the data from the drive (i have backups of everything that was created before Jaunty install)
my next step will be to contact Seagate if that's what it comes to.

---

### Post by Messyhair42 on 2009-05-30
any advice in recovering the HD or OS, or should i just go to Seagate for support?

---

### Post by Mark Phelps on 2009-05-30
If Seagate is willing to replace the drive for free, I'd try that.  Won't hurt and might help.

---

