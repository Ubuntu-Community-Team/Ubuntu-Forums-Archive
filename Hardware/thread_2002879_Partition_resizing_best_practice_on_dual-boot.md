---
title: "Partition resizing best practice on dual-boot?"
date: 2012-06-13
forum: Hardware
---

### Post by ChinaJustin on 2012-06-13
So this is only my second Linux/Ubuntu install, and I was really just trying out Lubuntu 12.04 on an old office computer to see how it ran.  I couldn't do a Live CD due to restricted internet connection issues here in China, so I had to do a full install with dual-boot against Windows XP.  I have four partitions on my 40GB hard drive: a 15GB Windows partition, and then three 5GB partitions for Lubuntu - one for the system, one for /home, and one for /swap.  What I'd like to do is shrink the XP partition and use the space for the system and /home partitions.

My question, then, is which would be better to shrink and resize the partitions: a third-party partitioning program in XP, GParted in Linux, or a GParted/other Live CD?

---

### Post by N0oki3 on 2012-06-13
gparted in linux or partition magic live cd. There isn't any diffrence after all

---

### Post by ChinaJustin on 2012-06-13
NOoki3: The only problem I found with using gparted while in Lubuntu was that when I shrunk the XP partition down and it created an unused partition, I couldn't increase the system partition to take advantage of the extra space that was next to it; it, obviously, wouldn't let me unmount it because it was in use, so I figured a live cd would address that issue... however, my download speeds here in mainland China can be horrible, and I haven't had the greatest of luck getting a working install CD working (took me three CD's before I got a decent burned iso).  But that's beside the point.  If I have to go that route, I will, was just trying to see if there was anyway to do it WITHOUT doing a live CD.

---

### Post by ahallubuntu on 2012-06-13
Windows Vista and Windows 7 both have built-in partition resizing, but XP does not.  A live CD is really the best way to go.  A Gparted live CD might be best for you because it should be a smaller download than a Ubuntu live CD:

[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

Note, in XP it might help to disable hibernation and disable your swap file (virtual memory), then defrag a few times before trying to resize the XP partition.  After the resize, turn the swap file back on and turn hibernation back on if you had it on before.  Because the virtual memory and hibernation files can be large, removing them can make defragmentation a lot easier.

---

