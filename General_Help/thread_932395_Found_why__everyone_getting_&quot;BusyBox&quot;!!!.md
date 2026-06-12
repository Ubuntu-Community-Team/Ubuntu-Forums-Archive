---
title: "Found why  everyone getting &quot;BusyBox&quot;!!!!"
date: 2008-09-28
forum: General Help
---

### Post by sandbird on 2008-09-28
I forgot about it :)

I got "BusyBox" all the time and I changed C:\ubuntu\install\boot\grub\menu.lst to have "debug on". Then I run Wubi again and now I got a log file name "casper.log" which tell me that "/dev/scd0 can't be mount - no medium".

I have a SATA disk working on SATA mode and that's the problem. Linux is not supporting SATA disks on SATA mode (even on Windows it's pain to make it to work on SATA mode).

So both Wubi and Ubuntu is out for me.

---

### Post by BeauBridges on 2008-09-28
When you first boot Ubuntu, you press escape and run the selected "Run for ACPI problems" and it should work fine. That's what I did, and it works amazingly well.

---

### Post by SuperSonic4 on 2008-09-28
I've never really understood wubi, wouldn't it be more realistic to use the liveCD or to install on a new drive/partition?

---

### Post by sandbird on 2008-09-28
> **SuperSonic4 said:**
> I've never really understood wubi, wouldn't it be more realistic to use the liveCD or to install on a new drive/partition?

I wanted to see Compiz :)
Since that LiveCD not supporting Compiz (I already tried), VMWare installation working fine except for Compiz, and real installation require free disk space for partition and to be pro Linux guru to manage to install it because of the lack of drivers, then it only left me to check Wubi.

---

### Post by sandbird on 2008-09-28
> **BeauBridges said:**
> When you first boot Ubuntu, you press escape and run the selected "Run for ACPI problems" and it should work fine. That's what I did, and it works amazingly well.

It didn't worked for me.

---

### Post by ago on 2008-09-29
there should be a log called /casper.log, you can read it using the "less" command. post here any mount error. Note that (software) raid arrays and encrypted disks are not supported.

---

### Post by Crafty Kisses on 2008-09-29
Try booting back into Vista and shutting down properly and then boot back into Ubuntu and see if that works.

---

### Post by Arcadeoddie on 2008-09-30
I am having the same issue's... I believe it has something to do with my hard drives sitting in a raid0 configuration.

Tried everything so far except: "Run for ACPI problems"  option. I will try this once home this afternoon.

---

### Post by ago on 2008-10-02
> **Arcadeoddie said:**
> I am having the same issue's... I believe it has something to do with my hard drives sitting in a raid0 configuration.

Tried everything so far except: "Run for ACPI problems"  option. I will try this once home this afternoon.

For (software) raid 0 you have to use Wubi 8.10. [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)
Wubi 8.04 will not work.

---

### Post by HDave on 2008-10-03
I just had this problem as well.  For me, booting into Windows and doing a proper shutdown solved the problem.

Apparently, Ubuntu won't mount the drive if it is flagged by Windows as being in an inconsistent state.  I would like to see Wubi set up fstab such that the mount would be "forced".  Is this possible?

---

### Post by ago on 2008-10-03
> **HDave said:**
> 
Apparently, Ubuntu won't mount the drive if it is flagged by Windows as being in an inconsistent state.  I would like to see Wubi set up fstab such that the mount would be "forced".  Is this possible?

Not going to happen, too dangerous.

Ideally we should get an fsck for ntfs at some stage or at least a consistency check, so that the dirty flag can be ignored selectively if no problem is identified.

---

