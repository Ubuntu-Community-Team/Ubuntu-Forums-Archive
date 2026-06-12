---
title: "Hardy install unable to handle second IDE diskdrive"
date: 2008-08-28
forum: Hardware
---

### Post by superbiskit on 2008-08-28
[I thought I posted part of this once before, but I haven't been able to find it]

I've been running Ubuntu since "Dapper", and for most of that time I've had two or three IDE drives inside the box (IDE0 Master, IDE0 Slave, IDE1 Slave), with my CD on IDE1 Master so I can boot from it.  Prior to Hardy, this was never a problem.

Then, my primary disk went bad, and the secondary isn't big enough to do anything worthwhile (only!! 8-Gib).  Fortunately, or so I thought, a friend had a 160GB drive he no longer needed and I got a bargain price.

I installed it, and tried the Hardy install CD.  The partitioner could only find one drive -- the 8Gib one.

Over several days, I played games with jumpers and disk positions.  The only thing that worked was to use only the one drive.  If a second disk was anywhere in the box, I got persistent IO errors, or I found the machine couldn't find the big disk.

One kind soul, I think it was here, opined that Master/Slave IDE combinations are a known problem.  If so, it's a problem that's new since changing to PATA-disguised-as-SCSI.  To establish that this is the case, some of my experiments involved using the Dapper install disk, which calls IDE what it is.  That allows me, at least, to format both disks and install an (0ld) system to them.  Booting into that system, however, is problematical.

Would someone please elaborate on issues involved in having more than one IDE drive running??

TIA

---

### Post by nicedude on 2008-08-29
I have my data storage system with 2 IDE drives and 3 sata drives ( 2 slots are hotswapable pullouts and I have 7 such drives in holders that I can insert into these bays ) and all works fine here without any problems. One thing I would recommend is that when you go to install an OS just unplug all but one drive that you want to install to and then after the install is complete that is when I hook up any other drives in the system.

If you think you know what you changed to make it stop working you could also just change that back.

---

### Post by superbiskit on 2008-09-01
> **nicedude said:**
> If you think you know what you changed to make it stop working you could also just change that back.
Sigh!  Originally, what changed was my drive.  I took out one that had gone belly-up and put in a new-to-me one I had bought from a friend.  From there, sad to say, there aint no going back.

Your post looks like good news, because I will want to go to a second drive at some point.

However, having seen IO problems when I put in a second drive, I'm getting very suspicious I need a BIOS update.  That's pretty thin ice.

---

