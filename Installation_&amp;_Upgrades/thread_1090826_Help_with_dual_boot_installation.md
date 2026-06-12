---
title: "Help with dual boot installation"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by HeretikSaint on 2009-03-08
I was running wubi for a while and decided I wanted more space dedicated for Ubuntu so I am attempting to dual boot with Windows Vista.  The problem is that no matter what I do, I cannot resize the windows partition enough to give ubuntu the space I want it to have.  I have a 320gig hard drive and I want to give windows about a 56% and ubuntu a 44% of the hard drive.  Vista's disk management wouldn't work, vista's command line partitioner wouldn't work, so I tried burning ubuntu to a cd and doing it that way.  Well I keep trying to resize the partition through ubuntu's utility and it just says
```
Resize operation failure
An error occurred while writing the changes to the storage devices.
The resize operation has been aborted.

```

This is the third different strategy I've tried to no avail.  Can anyone give me any ideas?

---

### Post by Mark Phelps on 2009-03-08
Hope you have a Vista backup because trying Linux resizing utilities on Vista OS partitions again and again is a surefire way to corrupt the Vista OS.

The Vista Disk Management utility is primitive, at best, but there are some workarounds.  See the following link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

If you keep trying to force it (the Vista resizing), you'll break it.  Hope you have a Vista DVD lying around so you can boot into Startup Repair to get Vista back working.

---

### Post by HeretikSaint on 2009-03-08
> **Mark Phelps said:**
> Hope you have a Vista backup because trying Linux resizing utilities on Vista OS partitions again and again is a surefire way to corrupt the Vista OS.

The Vista Disk Management utility is primitive, at best, but there are some workarounds.  See the following link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

If you keep trying to force it (the Vista resizing), you'll break it.  Hope you have a Vista DVD lying around so you can boot into Startup Repair to get Vista back working.

Nope.  I do not have the DVD lying around.  It is 1000 miles away (i left it with family when I moved from Maryland to Florida).  Honestly, I'm about to wipe out Vista out of frustration.  I'll check out the link you gave.

>  	
Re: Help with dual boot installation
This might sound silly but I know *windows has dynamic disks and basic disks. How is the current partition formatted under vista?

If its dynamic I dont believe you can do what you want to do but if its basic you should be able to repartition. You can revert back to basic from dynamic but PLEASE BE CAUTIOUS. Read up on the differences and if it relates to your situation. last thing you want to do is lose any critical data. You might want to backup anything important prior to this. 
Actually I checked, my Vista partition is on a basic disk and not a dynamic one.

---

### Post by HeretikSaint on 2009-03-08
This is really irritating.  It shouldn't be this difficult to resize a partition.  Windows would be gone if I didn't have so much on that OS already.  Does anyone know if PartionMagic would do the job?

---

### Post by Neo_The_User on 2009-03-08
try gparted or cfdisk (or if you want to enjoy the hassle, fdisk)

---

### Post by HeretikSaint on 2009-03-08
> **Neo_The_User said:**
> try gparted or cfdisk (or if you want to enjoy the hassle, fdisk)
The problem with those is that I will definitely need a vista disk to repair the windows volume.  I don't have the disk.  It got misplaced during my recent move.

---

