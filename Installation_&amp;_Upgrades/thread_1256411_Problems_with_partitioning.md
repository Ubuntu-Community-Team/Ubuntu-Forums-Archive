---
title: "Problems with partitioning"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by skibum3027 on 2009-09-02
I was trying to install ubuntu alongside windows vista on a friend's Dell XPS laptop. I attempted to shrink the vista partition, but the progress bar never left 0%, even after a long period of time. After eventually giving up, I cancelled the installation and attempted to reboot the computer. Vista now fails to load. Upon an attempted recovery, it fails to detect the operating system. However, recovery mode still sees C:\ as a location, but associates a size a 0 B with the drive. The live CD is no longer willing to attempt resizing the partition. After all of this, my friend informed me he still has data on the drive he needs. How can I restore vista to working condition/ recover the data? I have the windows and driver disks available if they are needed.

I tried googling the problem, but only found the suggestion of swapping out the hard disk and using it as a slave drive in another machine. I don't know if that method works, but it seems erroneous since I have no other machine that can accept his hard drive.

Thanks for any help.

---

### Post by Partyboi2 on 2009-09-03
When you boot a Ubuntu live cd are you able to mount the vista partition and see the data?

---

### Post by Mark Phelps on 2009-09-03
> **skibum3027 said:**
>  ... How can I restore vista to working condition/ recover the data? I have the windows and driver disks available if they are needed.

You boot from the Vista DVD and run Startup Repair repeatedly until it no longer finds any problems to repair.  

And next time, do NOT try to use the Ubuntu installer to shrink Vista; use the Vista Disk Management utility.

---

### Post by Bartender on 2009-09-03
> **skibum3027 said:**
> I have the windows and driver disks available if they are needed.

Maybe someone who has a similar Dell can help.  You say you have the "windows" disk, but it's highly unlikely that it's a genuine Vista disc.  It's a Dell Recovery Disc, right?

I've never been completely clear on this.  I've always thought that recovery discs don't typically have the "Repair" function.  Thought they just wipe the HDD and start over.  But it seems that some recovery discs do have Repair functions built into them.

So this is something that you need to be sure about.  If you have a Dell Recovery Disc, and if it does not Repair but just reinstalls, then that disc will wipe your friend's data.

Until you know for sure what the Dell Recovery Disc does, it'd be safer to try and access the data from another PC.  You say you have no PC to put the notebook HDD into.  Are you sure?  A notebook HDD will plug into the SATA cable connections inside a modern desktop PC.

What about a dock?  There's a pretty wide selection of HDD docks that will accept a desktop or notebook HDD.  You pop the notebook HDD into the dock, plug the dock into a PC, and start it all up.  Windows won't run from the dock because it won't recognize its environment (trust me, I've tried) but you should be able to at least access the data.

---

