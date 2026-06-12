---
title: "drive format hangs at 33% during install"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by DaveRowell on 2009-04-11
... with EITHER 8.04 or 8.10 alternate install CD's.  CD's checksums have been verified.  They hang in the same way at the same point!

System is an older Dell L933r with a 10 GB drive and 384 MB RAM.  Hey, it was free!  About half is left for Win ME with remainder for Ubuntu.  I'm trying to use 384 MB for swap and around 4.2 GB for /.

I've tried Guided partitioning which sets up an extended partition with logical / and swap partitions.  Hangs at 33% formatting /.

I've tried Manual partitioning as above.  I've tried manual partitioning with primary drives for swap and /.  I've tried swap first and / second as well as / first and swap second.  If swap is first it is formatted(?) quickly and never hangs.  In all cases the system hangs at 33% formatting /.

Any guidance would be appreciated

---

### Post by inobe on 2009-04-11
i can think of anything but three things..

1) sounds like some sort of power management kicking in.

2) ubuntu seems awfully heavy for that machine.

3) the disk could have errors on it.

boot up with a floppy and run scandisk or some disk utility.

for power move the mouse once in a wile to prevent power management.

heavy meaning xubuntu is light weight compared assuming you want some performance.

---

### Post by DaveRowell on 2009-04-12
Thanks, Inobe

I'm becoming convinced that this is a RAM problem - so lets let the thread die.

Interestingly, on a new 8.10 install that I did on another machine today the progress bar remained at 33% for way too long then finished in a flash!  I wonder what's happening at that point in the installer????

Dave Rowell

---

### Post by Sef on 2009-04-12
>  I'm becoming convinced that this is a RAM problem - so lets let the thread die.

On the Ubuntu disk is [memtest86]("http://memtest86.com").   Let it run overnight to check your ram.

---

### Post by inobe on 2009-04-12
> **DaveRowell said:**
> Thanks, Inobe
Interestingly, on a new 8.10 install that I did on another machine today the progress bar remained at 33% for way too long then finished in a flash!  I wonder what's happening at that point in the installer????
Dave Rowell


the installer dialog should say what it's doing at that point, also check the activity light for the hard drive, if it's blinking something is installing.

---

