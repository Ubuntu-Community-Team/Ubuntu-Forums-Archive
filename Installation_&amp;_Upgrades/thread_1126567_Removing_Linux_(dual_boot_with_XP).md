---
title: "Removing Linux (dual boot with XP)"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by blackriven on 2009-04-15
The title says it all. How do I return to having only XP? (Installed Ubuntu 8.something)

---

### Post by scragar on 2009-04-15
If you still have your windows install disk it's really easy.

First boot from a liveCD, launch Gparted. Delete the ubuntu partition, swap partition and extended partition around them, in that order.

Put the boot flag back on windows.

Restart, use the windows install disk.

At the first chance you get enter it's recovery mode, from that command line type:
```
fixmbr
```

Reboot without any disk in the drive.

---

### Post by Therion on 2009-04-15
**Executive Summary Version:**

Boot your system using a Parted Magic LiveCD.
Delete the existing ext3 and swap partitions.
Resize the NTFS partition to reclaim the space.
Set NTFS partition as your bootable partition.

---

### Post by blackriven on 2009-04-15
> **scragar said:**
> 
First boot from a liveCD, launch Gparted.

You mean the Ubuntu liveCD?

---

### Post by MysticGold04 on 2009-04-15
Yep.

---

### Post by scragar on 2009-04-15
> **blackriven said:**
> You mean the Ubuntu liveCD?

Most liveCDs will come with a partition editor of some kind, I'm rather fond of using the Xubuntu liveCD, but whatever liveCD you have around should work.

---

### Post by blackriven on 2009-04-18
I did as was instructed, but the extended partition is refusing to go away. I searched the web and found this post: [http://ubuntuforums.org/showthread.php?t=937289](http://ubuntuforums.org/showthread.php?t=937289)
and tried the liveCD for GParted, but for some reason it will not boot from it. 

Nevertheless, I suddenly remembered that I actually installed Ubuntu on the secondary drive, so I used the Windows XP CD to fix the boot tables (terminology?) and now Windows is booting normally. 

Now I need to reclaim those lost partitions and get rid of the extended one. I have no problem completely reformatting the secondary drive if necessary since it's not really used for anything important. 
How can this be achieved?

---

### Post by blackriven on 2009-04-18
OK update: turns out there's only one disc and it was simply partitioned into two- C and D- before I installed Ubuntu on it. (This is not my computer, which is why I don't remember all the details). 

I figured out how to merge the Linux partition into partition D using GParted, and now there's just C, D, and that extended partition wrapping D. Am I correct in assuming that this partition is simply what divides the disc into two? Or is it space I can reclaim by freeing it? If so, how?

---

