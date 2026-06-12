---
title: "Drive in RAID 10 setup dead - What to do?"
date: 2013-01-23
forum: Hardware
---

### Post by OMGthatsCrAZy on 2013-01-23
Hi everyone,

I am running a homemade NAS using Ubuntu 10.04.  I have 4 2TB hard drives in a RAID 10 setup - a stripe of mirrors. 

Yesterday when accessing the data remotely, I got an I/O device error.  When I logged into the machine and checked the disk utility, the RAID array state says "DEGRADED" and one of the drives' SMART status says "DISK FAILURE IMMINENT". One of the other disks has a few bad sectors, but its status is green and the other two drives are fine. Is it normal that I can't access any of the data in its current state? I feel like I should be able to access at least half but no transfers work from the RAID array.

How do I recover from this without losing any data? I called Western Digital and they are sending me a replacement drive in advance.  Is it as easy as removing the failing drive and connected the new drive, then rebuilding the array? I have had trouble finding a good easy guide on Google and I don't want to lose this data - I am using RAID for a reason.

---

### Post by OMGthatsCrAZy on 2013-01-24
Bump, sorry.  Am I in the wrong section?

---

### Post by ahallubuntu on 2013-01-24
I'm sorry, I haven't used RAID in a long time, so I'm not ignoring you, but I don't have any helpful advice for you.

---

### Post by steeldriver on 2013-01-24
I know enough to be dangerous - but not enough to feel confident about advising you

Assuming it's mdadm soft raid, then I *think* that if the device has not already failed, the steps are (a) mark it as failed (b) remove it (c) add the new device - see

[http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/)

However there are a couple of *real* raid experts around here - I would wait for their input

---

### Post by OMGthatsCrAZy on 2013-01-24
> **steeldriver said:**
> I know enough to be dangerous - but not enough to feel confident about advising you

Assuming it's mdadm soft raid, then I *think* that if the device has not already failed, the steps are (a) mark it as failed (b) remove it (c) add the new device - see

[http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/)

However there are a couple of *real* raid experts around here - I would wait for their input
Thanks bud, I'll take a look at this and give it a shot.  WD is sending me a new drive so I can replace it.

ahallubuntu - Thanks.

---

### Post by ahallubuntu on 2013-01-24
I setup a RAID 1 years ago with mdadm and didn't quite know what I was doing.  I had an ext3 file system corruption and didn't quite know how to deal with it in the array.  Fortunately, I had a (mostly) complete backup separate from the array, so I just dumped it.

RAID only protects against hard drive failure, not filesystem corruption, accidental deletion, etc.  And as you can see, it's not completely easy to replace failing RAID drives (it shouldn't be hard to replace them if you know how to use them, which I don't, obviously).  The point is, having a separate backup from your RAID is really important, too.

---

### Post by CharlesA on 2013-01-24
The easiest thing to do is to pull the drive out that is going out and replacing it and then letting the software rebuild the array. Because it is a RAID 10 - you will lose one of the mirrored sets, so it would need to rebuild the whole thing after you replace the bad drive.

+1 to ahallubuntu. RAID isn't a replacement for a good backup plan.

In my case, I have a hardware RAID card and software, not mdadm, so I can just swap out the drive and tell it to rebuild. I do not know if you need to do anything special with mdadm.

---

### Post by SaturnusDJ on 2013-01-25
The array should still be accessible if only one drive failed.

---

### Post by OMGthatsCrAZy on 2013-01-28
UPDATE:

The server is back to normal and healthy. Thanks for your help everyone.  What I did to fix this was:

-Restarted the computer and reassembled the array.  Finally after doing that, the array was accessible even without that 4th drive.

> sudo mdadm --stop /dev/md0/
sudo mdadm --assemble --force /dev/md0 /dev/sd[bcde]1

-I backed up everything onto another machine.

-I set the drive to "failed" status and removed it from the array:

> sudo mdadm /dev/md0 --fail /dev/sdd1 --remove /dev/sdd1

-I then shut down the machine, replaced the failed drive with a new drive and turned it back on and added the new drive:

> sudo mdadm --add /dev/md0 /dev/sdd

This worked for me and was pretty simple. I thought someone might find this helpful if they are in the same boat and cant access their data even though only 1 drive died.

---

