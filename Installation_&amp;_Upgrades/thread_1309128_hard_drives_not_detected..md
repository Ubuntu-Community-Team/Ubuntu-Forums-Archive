---
title: "hard drives not detected."
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by mafia_emu on 2009-11-01
Trying to install Karmic (x64) and it will the partitioner will only detect one out of four of my hard disks.
It can mount all my hard disks on the live cd. So why can't the partitioner see them.
Is there another way I can go about installing.
All help greatly appreciated.

---

### Post by emacdonald on 2009-11-01
I have a similar problem. I have stripped the PC back to a single CD drive and a single sata drive. I boot up on the Cd image, Parted running on its own can see the sata drive, but when it comes up during the 9.10 install phase the drive is not detected.

I know the sata drive is ok, I have installed 9.04 on it without difficulty.
I have also run the WD Diagnostics programs on it and it passes with flying colours. I have also tried it on a different sata port!

The other three drives I have on the PC are detected correctly, one which is the original system drive.(I want to do a fresh install on a clean drive and import all the bits and bobs over from the older system drive!).
I could use one of these drives.

But that is not the point. 

Why does this drive not work?

BTW its a Western Digital WD2500KS model

Is this a common issue? Am I wasting my time?

---

### Post by emacdonald on 2009-11-01
May have something to do with this, looks like it is being picked up as part of a Raid array. How do I boot with nodmraid option?

Nov  1 09:59:56 ubuntu activate-dmraid: Serial ATA RAID disk(s) detected. If this was bad, boot with 'nodmraid'.
Nov  1 09:59:56 ubuntu activate-dmraid: Enabling dmraid support.
Nov  1 09:59:56 ubuntu dmraid-activate: ERROR: Raid set sil_ahaiafbiabca is degraded. Not activating
Nov  1 09:59:57 ubuntu kernel: [  199.860527] end_request: I/O error, dev fd0, sector 0
Nov  1 09:59:57 ubuntu dmraid-activate: ERROR: Raid set sil_ahaiafbiabca is degraded. Not activating
Nov  1 09:59:57 ubuntu kernel: [  199.888535] end_request: I/O error, dev fd0, sector 0
Nov  1 09:59:57 ubuntu ubiquity[3709]: switched to page partman
Nov  1 09:59:57 ubuntu ubiquity[3709]: switched to page partman
Nov  1 10:17:01 ubuntu CRON[5341]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by emacdonald on 2009-11-01
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

F6 set to nodmraid. 

I will let you know if it succeeds.

---

### Post by emacdonald on 2009-11-01
Nah didn't work.

---

### Post by qwerta001 on 2009-11-01
> **emacdonald said:**
> Nah didn't work.
Hi there!
I went through all this yesterday - reading through the forum, it looks like a common problem. Indeed, before the official release, this disk recognition issue was flagged repeatedly, but they (Canonical) did nothing about it.
Apparently, they have a laudable, but flawed, policy of sticking to release dates come what may. Of course, if they discover a problem late in the day, they feel they still have to release it even if it doesn't work!
I'm going to wait a week or two, and if it isn't fixed I'll have to go elsewhere.
This is sad, as I was really looking forward to this, to replace Vista.

---

### Post by emacdonald on 2009-11-01
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054) is the bug in question!

If you go into Synaptic, search for "dmraid" remove it completely, then do the install. it looks fine, the disc is now detected.


I do not know how well it will boot etc. after I have installed, but no doubt we will see..

It is a bit of a PITA!

Wouldn't be so bad, but my modern motherboard only has one P-IDE connector other wise I could bypass this problem by installing an IDE drive! ;)

---

### Post by emacdonald on 2009-11-01
Looks like everything installed ok... :p

Checking in Synaptic, dmraid is not selected/installed. It just looks like it is a problem with the live cd, perhaps.
But the original reason for going down this route was a problem with the upgrade where I lost sight of a Sata drive.

Let's see how how the recovery of all the drives goes over the next few days.

---

### Post by alexanderbow on 2012-01-08
Btw, for anyone who comes across this thread; Still an issue when installing 10.04 (Lucid) 32 bit (x86). Ancient IDE 30 Gb Seagate w/ Dell Optiplex 260? Gparted, fdisk, and smartmontools recognize the HDD fine.

removing dmraid makes it instantly pop up! have yet to install given im friggin tired. Ill post an update if any relating issues come about.

Thanks; you the man emacdonald!

---

### Post by nothingspecial on 2012-01-08
Please do not bump old threads to the top. If you have a question, make a new thread of your own.

Closed.

---

