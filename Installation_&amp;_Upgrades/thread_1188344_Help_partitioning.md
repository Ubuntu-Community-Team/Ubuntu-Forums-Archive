---
title: "Help partitioning?"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by kttyshadow5 on 2009-06-15
So I installed the Ubuntu 9.04 ISO on a CD, and booted from the CD and started running the installer. My installation guide told me to look for an option called "guided" partition but I didn't find any option in the 9.04 installer. I only found "Wipe Drive" or "Create Partition", or something to that effect. So I tried to resize the partition from my Windows install. However, it wouldn't allow me to, even though I ENSURED that I had 20 GB free on my HD before starting the install. So basically, can I resize my Windows partition to make room for an Ubuntu partition? Or do I need to get an external HD and or wipe my drive?


*NOTE* Right now I am in the .... Trial per say mode of Ubuntu, wherever it is you get to by "Exiting" the installation. However, I could return to Windows at this point if necessary.

---

### Post by brncao on 2009-06-15
You cannot shrink Windows at will (you'll be very limited to a shrink point) while you're in it because there are stuff at the end of the partition that's preventing it. You'll need to get off windows first before you can shrink it.
 
Boot into the LiveCD and in System>administration, click Partition Editor (Gparted). You can shrink windows from there. I think the tool is self explanatory, plus it's miles better than Windows's Disk Mangement.
 
Once you've shrunk windows to a desired size, you can install Ubuntu. I'd recommend installing it manually as you get to adjust how big the partition(s) you want it to be and what partitions you want to mount it as. We can help you plan your partitions if you need the help.

---

### Post by Mark Phelps on 2009-06-15
If you're running Vista, do NOT use Gparted, or any other Linux utility, to shrink the OS partition.  Doing so runs the risk of corrupting the partition such that it will not then reboot.  That can only be fixed (some of the time) by booting into a Vista DVD and running Startup Repair repeatedly until it finds no more problems to fix.

If you're running XP, you should be OK, but be sure to backup important files before you shrink the partition.

---

### Post by merlinus on 2009-06-15
Also be sure to delete temp and other unneeded files and defrag before shrinking windows.

---

### Post by presence1960 on 2009-06-15
> **merlinus said:**
> Also be sure to delete temp and other unneeded files and defrag before shrinking windows.

+1

**Defrag windows: most important operation prior to resizing a windows partition. If not done the resize will fail or result in data corruption or loss.**

---

