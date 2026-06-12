---
title: "RAID vs backups"
date: 2008-10-18
forum: General Help
---

### Post by trakie on 2008-10-18
So i have 4 hard drives overall (2x500 and 2x750) and i would like to use the spare two as backups for the active 2 (so the spare 500 would back up the active 500, etc..).  to complicate matters i have a mythbuntu box which houses the spare 500gb (i could move it back to my main computer at the cost of an SATA dvd drive).

my question is whether i should be looking into backup (such as simple backup config in the admin menu) or a RAID 1 (and then software or hardware?)

any other thoughts that might be pertinent to my situation would be appreciated as well.

thanks

---

### Post by DGortze380 on 2008-10-18
> **trakie said:**
> So i have 4 hard drives overall (2x500 and 2x750) and i would like to use the spare two as backups for the active 2 (so the spare 500 would back up the active 500, etc..).  to complicate matters i have a mythbuntu box which houses the spare 500gb (i could move it back to my main computer at the cost of an SATA dvd drive).

my question is whether i should be looking into backup (such as simple backup config in the admin menu) or a RAID 1 (and then software or hardware?)

any other thoughts that might be pertinent to my situation would be appreciated as well.

thanks

RAID is not a backup. Period. End of story.

RAID will not protect you from yourself, one simple example.
rm -rf ... used often to delete directories... run in the wrong location deletes EVERYTHING. (in the case of RAID, deletes everything on both drives).
Hackers, virus, incorrect program installs, running incorrect scripts as root, are all situations in which your RAID, instead of providing you a clean back up, would provide you with 2 bad copies of your data.

This is not to say that you can't back-up to an internal drive. Look into rsync. Maybe a simple script to mount you backup drive, run rsync, then unmount the drive.

---

### Post by nlinecomputers on 2008-10-18
Raid also doesn't protect you from physical disasters.   

Spill coffee on your computer and you can fry the entire unit RAID, backups, everything.  A backup should be a removable device that you can unplug from your computer.  If possible have more then one backup unit and store one offsite.  If you home burns down you still have your data some place else.

The only thing RAID is good for is to protect against hard drive failure.  It is the first line of defense not the only line of defense.

---

### Post by fjgaude on 2008-10-19
I use raid5 for speed and protection against hard drive failure. I also use three backups of important data, one is online, another is near-line, and the last is off-line.

---

