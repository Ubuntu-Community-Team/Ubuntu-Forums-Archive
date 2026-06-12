---
title: "Can't resize partition"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by 0wn3d on 2009-05-12
I'm trying to install Ubuntu (The latest version, its my first time w/ linux, but I'm pretty good w/ comps) and when I use the CD to install I don't have the 'Guided - Resize' option.  I also tried to run ubuntu w/ the live CD and I tried to use gparted on it and it also did not allow me to resize.  After installing dmraid gparted was able to detect my RAID array, but still would not let me resize.  I need to resize my XP installation which currently takes up my entire hard drive (I need to keep XP, I play lots of games and am not sure if I want to fully switch to linux).

After looking around I think that it has to do with my raid being fakeraid (its set up in RAID 1).  I need to know how to resize my XP NTFS partition so I can fit ubuntu, does anyone know how I can get this working?

---

### Post by jerrrys on 2009-05-12
it is recommend that the alternate cd and not the live cd be use when installing to a raid system...
however, since your just doing a mirror why not unplug #2 hdd and see if the live cd will then load...you might get lucky...

---

### Post by 0wn3d on 2009-05-12
> **jerrrys said:**
> it is recommend that the alternate cd and not the live cd be use when installing to a raid system...
however, since your just doing a mirror why not unplug #2 hdd and see if the live cd will then load...you might get lucky...

Will this affect my current XP installation?  I'm actually fine with getting rid of RAID, but I wasn't aware that you could just unplug a hard drive and start using a copy of XP installed on a raid array on one of the single hard drives.

---

### Post by jerrrys on 2009-05-12
your running raid 1 which means the second hdd is a clone of #1...this is your setup, right? so by unplugging the second drive, you will have a backup of xp, if anything goes wrong...

RAID 1 ([mirrored]("http://en.wikipedia.org/wiki/Mirror_%28computing%29") settings/disks) duplicates data across every disk in the array, providing full redundancy. Two (or more) disks each store exactly the same data, at the same time, and at all times. Data is not lost as long as one disk survives. Total capacity of the array equals the capacity of the smallest disk in the array. At any given instant, the contents of each disk in the array are identical to that of every other disk in the array.  [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

---

### Post by 0wn3d on 2009-05-12
Yep its RAID 1, so basically I can just remove the power from my 2nd HD?  Should I unplug it from the mobo (I'm just gonna leave it in the case so I assume removing the power shuld just be fine).  Is there anything I need to do after this?  I think I saw somewhere that the RAID setup thing will tell me to break the array, and then I have to disable RAID in the BIOS.  Is that it?

---

### Post by jerrrys on 2009-05-12
close, but no...if your going to turn off raid in bios, you do not need to unplug it...once you turn off raid you will then have two separate hdd's in your system...both will have identical copies of xp on them...being identical they may both try to boot, really dont know for sure...but for starters just turn off raid, then reboot, once again you should get lucky...if not just go ahead and unplug power to 2nd hdd...
and thats your backup for now...got to ask you...are you up to this, you have skills...in my case, im running a server and it a flip of a lever to disconnect an hdd...in your case, you got to go into yours to do this...if necessary...

---

### Post by 0wn3d on 2009-05-12
I can definitely get in my comp(it's easy w/ my case).  I'll try just disabling raid in my bios

---

### Post by jerrrys on 2009-05-12
dont forget to unplug the power cord...and ill be looking for a reply...good luck...

---

### Post by 0wn3d on 2009-05-12
Right now I'm on my itouch.  Just disabling raid didn't seem to work so my next move will be unpluging

---

### Post by jerrrys on 2009-05-12
sounds good...

---

### Post by 0wn3d on 2009-05-12
It is working so far!  Windows was able to start and I'm gonna try partitioning and instaliing ubuntu now

---

### Post by jerrrys on 2009-05-12
Noooo!!!

---

### Post by jerrrys on 2009-05-12
next do a windows defrag.....

---

### Post by 0wn3d on 2009-05-12
> **jerrrys said:**
> Noooo!!!



Don't worry.  I've ran defrag like 20 times today.  And twice just before my last shutdown.  I have at least 100gb (on the right side) out of my 320gb with nothing at all on it .

---

### Post by 0wn3d on 2009-05-12
Damit >< - I can't shrink the partition with the ubuntu installer and I can't use gparted either.  Gparted is telling me that I need to run a chkdsk, and I guess I'll do that (Even though I just ran one like 2 days ago...).

---

### Post by jerrrys on 2009-05-12
ok then...your on your way to an install...moving partitions can take hours, so be patient...and welcome to the forum!

you should be able to chose the shrink partition option from the live install. dont remember how its worded...

---

### Post by 0wn3d on 2009-05-12
Now when I was at like 20-30% on my install it gave me an error, something about either my disk drive having problems or my HD or that it was too hot.  I honestly don't think these are problems, my disk drive works fine and XP is fine on my HD.  I did the check for errors on the disk before and got none.  I'm gonna try again, but my partitions are kinda screwed up though ><

---

### Post by jerrrys on 2009-05-12
how bout just running from the live cd? not installing...

whats your system specs?

---

