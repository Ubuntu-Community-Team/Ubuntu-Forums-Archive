---
title: "Hard drive multiple bad sectors"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Cereal_Killer on 2009-10-31
Just installed 9.10 on a 160 gig Samsung laptop drive.  Upon everything installing properly, and getting to the main screen, I got the notification that the hard drive has multiple bad sectors.  I've tried doing the self-tests a few times, but it keeps saying this.  Does this mean that my hard drive is going bad?  Am I going to have to get a new hard drive?

---

### Post by cubsfan53 on 2009-10-31
I had this as well but when I ran Karmic as a live disk.  I dual boot with XP on an HP NC800 laptop, 40GB HDD.  Just this week fsck ran its usual check and showed no problems. If i recall the total bad sectors was about 39K?? My xp partition is 10.7GB.  after the warning Karmic continued to boot up and I used it successfully for an hour or so. Know this doesn't answer your query, just to let you know someone else also had it. I'll be looking at this more tomorrow.

Cubs Fan

---

### Post by Mark Phelps on 2009-10-31
While this is being billed as a "feature" in Karmic, it appears that it reports LOTS of false positives.  If you run fsck for Linux partitions, and chkdsk for MS Windows partitions, and are NOT getting errors, you can safely ignore the false positives that Karmic is presenting.

---

### Post by Herman on 2009-11-01
The Linux 'badblocks' command normally give a pretty good idea how good or bad your hard disk in, in my opinion. You might run it on one partition at a time if you like, as it takes a while.
```
sudo badblocks -sv /dev/sda2 >> badblocks.report
```That should print a file with a list of badblocks in it, if it does, probably it's time to look at replacing your hard disk. If it produces and empty file you're okay.

---

### Post by newbie2 on 2009-11-03
> **Herman said:**
> The Linux 'badblocks' command normally give a pretty good idea how good or bad your hard disk in, in my opinion. You might run it on one partition at a time if you like, as it takes a while.
```
sudo badblocks -sv /dev/sda2 >> badblocks.report
```That should print a file with a list of badblocks in it, if it does, probably it's time to look at replacing your hard disk. If it produces and empty file you're okay.
I upgraded,and i too got the notification that the hard drive has multiple bad sectors.
Copypasted ```
sudo badblocks -sv /dev/sda2 >> badblocks.report
```
in terminal, and it returned 0(zero) bad sectors...
:rolleyes:

---

### Post by Mark Phelps on 2009-11-03
> **newbie2 said:**
>  ... ```
sudo badblocks -sv /dev/sda2 >> badblocks.report
```
in terminal, and it returned 0(zero) bad sectors...
:rolleyes:

This is what I mean by "false positives" -- 9.10 reporting bad blocks while badblocks reports the partition as OK.

---

### Post by Kokopelli on 2009-11-03
Disk utilities may be giving false positives but doing a read only check of a single partition of a disk is not the way to validate it.  This is actually horrifically misleading.  It is like pulling the trigger on a revolver 5 times and assuming the revolver is empty.  Chances are you are correct, but it is not proof.

First of all reallocated sectors generally occur on a failure to write, not read.  If there is a failure to read generally they are put in a pending status.  Second, especially for dual boot setups, there are multiple partitions.  Bad blocks can be in any partition and would be indicative of a failing drive.  At the least consider using a non destructive write pass and perform it on **all** partitions on the drive.  Also consider using the manufacturer specific tools for validating the disk.  Finally badblocks should not detect reallocated sectors handled by SMART.  That is the point of SMART, it reassigns the sector at the firmware level.  By the time it shows up on chkdsk surface scans or badblocks the time to replace the drive has passed.

A drive can have reallocated sectors and still be fine.  No bad sectors is obviously preferable but the time to be alarmed is when the reallocated sector count is steadily increasing or has already exceeded threshold on SMART.

Again, I agree that disk-utility is giving out false positives. However, if you are truly concerned about the stability of your drive, running badblocks in read only mode on a single partition is not the way to ensure it is ok.  If you want more information read the wikipedia article on S.M.A.R.T. **and** the referenced articles out on the web.  Especially pertinent is the paper from google on hard drive failure analysis.

---

### Post by presence1960 on 2009-11-03
> **Cereal_Killer said:**
> Just installed 9.10 on a 160 gig Samsung laptop drive.  Upon everything installing properly, and getting to the main screen, I got the notification that the hard drive has multiple bad sectors.  I've tried doing the self-tests a few times, but it keeps saying this.  Does this mean that my hard drive is going bad?  Am I going to have to get a new hard drive?

I had the same problem. I went to my hard disk manufacturer's web site and downloaded their disk checking utility. Turns out the disk is fine, but 9.10 keeps saying it has over 240 bad sectors. BTW I downloaded the bootable version of the disk checker.

You can turn off the disk check in 9.10 by going Preferences > Startup Applications. Uncheck disk notifications.

---

### Post by newbie2 on 2009-11-03
> **Kokopelli said:**
> Disk utilities may be giving false positives but doing a read only check of a single partition of a disk is not the way to validate it.  This is actually horrifically misleading.  It is like pulling the trigger on a revolver 5 times and assuming the revolver is empty.  Chances are you are correct, but it is not proof.

First of all reallocated sectors generally occur on a failure to write, not read.  If there is a failure to read generally they are put in a pending status.  Second, especially for dual boot setups, there are multiple partitions.  Bad blocks can be in any partition and would be indicative of a failing drive.  At the least consider using a non destructive write pass and perform it on **all** partitions on the drive.  Also consider using the manufacturer specific tools for validating the disk.  Finally badblocks should not detect reallocated sectors handled by SMART.  That is the point of SMART, it reassigns the sector at the firmware level.  By the time it shows up on chkdsk surface scans or badblocks the time to replace the drive has passed.

A drive can have reallocated sectors and still be fine.  No bad sectors is obviously preferable but the time to be alarmed is when the reallocated sector count is steadily increasing or has already exceeded threshold on SMART.

Again, I agree that disk-utility is giving out false positives. However, if you are truly concerned about the stability of your drive, running badblocks in read only mode on a single partition is not the way to ensure it is ok.  If you want more information read the wikipedia article on S.M.A.R.T. **and** the referenced articles out on the web.  Especially pertinent is the paper from google on hard drive failure analysis.
Thanks for the advice Kokopelli, i looked up the [wikipedia article on S.M.A.R.T.]("http://en.wikipedia.org/wiki/S.M.A.R.T.") ... i think i consider to buy me another laptop drive ...me thinks :-k

---

