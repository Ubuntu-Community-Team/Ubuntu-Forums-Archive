---
title: "Gparted won't see partition"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by sjvega on 2009-11-07
Hi, I just installed Win7, on a blank hard drive, and i was trying to install Ubuntu 9.10.
So I opened Gparted on the livecd to adjust the partitions, and I saw, that there was nothing there (it was completly blank), but it still lets me open the partion created with windows, it's like gparted doesn't see the Win7 partition.
There's something i'm missing?, because it seems pretty strange to me.
Thanks in advance.

---

### Post by sjvega on 2009-11-07
*bump
I've reinstalled Windows, but still no partition shows up, gparted tells me the problem is with the table which is in GPT, but in Windows says its fully MBR, and boots ok...

---

### Post by kyuubi777 on 2009-11-07
i had the exact same thing happen to me...using gparted under live cd as well as inside of the 9.10 os that apparently wasn't on the hdd... i posted about this but haven't gotten a response yet... 
link to my comment :  [http://ohioloco.ubuntuforums.org/showthread.php?p=8254429#post8254429](http://ohioloco.ubuntuforums.org/showthread.php?p=8254429#post8254429)

since then i have gotten rid of my win. partition and am now tri booting 9.04 kde 4.3 / 9.10 gnome / and sabayon 5.0 kde 4.0 ... i installed sabayon to kick the win. out and it used disk utility.. that actually figured out my hdd formatting and and just read me errors when i tried to config. my hdd (it did complete each action i told it to, it just read errors) and as soon as i got rid of the win. partition gparted showed proper hdd config. while installing 9.04 on my last partition...

so my recommendation to you would probably be to ax windows briefly and reinstall it, or use a live cd where the partitioner is Disk utility...(i believe that was the one used by my sabayon disk (could have been parted magic or something else as well)). comment back with any info (esp. if you find some random 1KB partition or around that amount.. that is also something i found during this strange issue... hope i was of some help

---

### Post by sjvega on 2009-11-07
Yea, my disk utility in the livecd shows the correct distribution of disks (sorry but no 1KB partitons), and from the livecd I can access the info there, but even so, gparted shows all unallocated, and when running from the console it says it maybe a GPT partition table or might been damaged, but when i boot Windows (boots OK), the disk says that the table is MBR....
Just to get things even stranger, I have another disk, which shows in gparted just fine, with an old Vista installation.

---

### Post by sjvega on 2009-11-08
*bump
Don't know what else to try...

---

### Post by Deicider on 2009-11-08
i too can't see the linux partitions only windows's

---

### Post by sjvega on 2009-11-08
Ok, from i have been reading the problem is that, the disk was originally partitioned in GPT, but when i installed Win, It uses MBR, so the both tables exists in the disk, and Gparted reads only the GPT, which is empty. There is a way for to delete the GPT table, or update it from the MBR, without losing the data?

---

### Post by sjvega on 2009-11-08
Ok,so far haven't found any way to change the table without losing data. So I'll install Ubuntu on the other disk, but the thing is that I don't know if GRUB will see the Windows partition... 
Can someone give a hand here to tell if this will run, and more importantly, how?

---

### Post by Deicider on 2009-11-09
we're doomed =(

---

### Post by theozzlives on 2009-11-09
7 uses two partitions, one reserved for the system and C:. Resize C: using Disk Management in Windows. Then boot the live CD and install Ubuntu on the free space you created with Disk Management.

---

### Post by wilee-nilee on 2009-11-09
I had this unallocated happen to me today when I deleted the recovery of XP to have my Student upgrade be within the upgrade license. I just did a custom fresh install of W7 and set the partition for 60 gigs and left the other 100 gigs open for karmic and when I checked with gparted from the live CD W7 was there and the open space.

---

