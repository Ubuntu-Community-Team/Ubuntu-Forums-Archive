---
title: "4 bad sectors"
date: 2012-12-12
forum: Hardware
---

### Post by dagring on 2012-12-12
I have opened Ubuntu disk tool and one of my disks have bad sectors. I have run fsck, but the bad sectors are not repaired. Should I be worried and try something else to repair the disk?

----------
Dag R

---

### Post by ahallubuntu on 2012-12-12
> **dagring said:**
> I have opened Ubuntu disk tool and one of my disks have bad sectors. I have run fsck, but the bad sectors are not repaired. Should I be worried and try something else to repair the disk?

You'd need to be more specific.  "Bad sectors" can mean more than one thing.  If they are "Reallocated Sectors" (sectors that have already failed and been replaced with spares by the hard drive firmware), you don't have to do anything else.  The drive firmware has already taken care of it.  But if they are "Pending Sectors," that is bad news - that means the drive can't read those four sectors and you are looking at potential catastrophic failure: data loss, computer freezes, etc.

Check the current S.M.A.R.T. status - look at the Attributes in GSmartControl, something you can install in Ubuntu.  In the Attributes tab, look for any Attributes that are highlighted in Red.

Four Reallocated Sectors is not terrible news but is a warning: WATCH your drive.  Monitor the S.M.A.R.T. status.  Backup your important files often (you should be doing that anyway, of course).  A few reallocated sectors on an older drive is not alarming but it the number increases, eventually you'll need to replace the drive.  Modern drives do have spare sectors but not an unlimited number; eventually, the drive will run out of spares and then the drive is junk.

---

### Post by dannyboy79 on 2012-12-12
i just had to dump a 1TB drive from seagate that was only 2 years old. it had 367 bad sectors and the number was crawling upward as I kept writing to it. if there's important data on it, store it elsewhere and keep an eye on it, if the bad sector count rises at all, get rid of it.

---

### Post by dagring on 2012-12-13
Thanx for the replies. The sectors were allocated, not pending. I will keep an eye on the disk.

----
Dag R

---

