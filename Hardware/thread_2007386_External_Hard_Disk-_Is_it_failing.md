---
title: "External Hard Disk- Is it failing?"
date: 2012-06-20
forum: Hardware
---

### Post by fantab on 2012-06-20
My External Hard Disk, 1 TB  was slow in its response than normal. So I used Disk Utility SMART DATA to see what's up.

There are two issues (I have posted Screenshots below), 
[LIST=1]
[*]Bad Sectors
[*]Airflow temperature
[/LIST]

Does the forum think that the External Hard Disk is failing? Is there a way to fix these issues? Or should I get myself a new one? 

This EHD is full with DATA and has no space left on it.

---

### Post by ahallubuntu on 2012-06-20
It's definitely running hot.  If the casing has poor ventilation, that wouldn't be surprising.  However, opinions differ on whether running hot occasionally is bad for a drive.  Google had a study (they use many thousands of hard drives in their servers) that showed that hard drive heat wasn't as bad for the life of a drive as had been previously assumed.  Google's server farms are apparently a bit unconventional and run servers hotter than conventional wisdom suggests is good.  But cooling is very expensive...

The reallocated sector number is worrisome but not necessarily catastrophic.  If the drive is a few years old and has had a lot of use, a few reallocated sectors is not that unusual.  That means a few sectors have failed and were replaced with spares.  Eventually if sectors keep failing and are replaced, the drive will run out of spares.  You don't have to stop using the drive today, but I would keep an eye on it.

Spare sectors may not be in the same part of the drive as the originals, so that could slow the drive access down.

With any hard drive, you need to assume it will fail sooner or later, perhaps without warning, and HAVE REGULAR BACKUPS on separate devices.  Anyone with important data on only a single hard drive is foolish not to have a backup second drive.  I've replaced too many failed hard drives that were completely dead and their owners unable to get back their data to think it can't happen to me.  My strategy is to have at least two copies of all my data (perhaps three copies) on separate devices.  If I have a 1TB backup drive, I'd have an identical drive that is synced to the original regularly.  Or, rotate which one is the "primary" to even the wear.

---

### Post by mscout2004 on 2012-06-20
I would have to agree with ahallubuntu would not be relying on that disk as my primary back-up as it does look to be headed out the door if it is full and used a lot.

---

### Post by fantab on 2012-06-21
Thank you guys,

The External HDD in question is Three years old and has been full ever since, it carries my media. The good thing is that its still under Warranty. So, I will replace it.. (if I can). But before that I want to know if the Bad Sectors can be repaired? If yes how? and can anything be done about the "drive running hot"?

---

### Post by ahallubuntu on 2012-06-21
As I noted, the drive's firmware has already marked the bad sectors as "do not use" and has re-allocated spare sectors to replace them.

Those bad sectors can't be repaired, but as  of now all drive sectors are working because spare sectors have replaced the bad ones.

If it were me, I would replace the drive under warranty and hope the new drive runs cooler.  Otherwise, the best way to improve the cooling would be to try to remove the drive from its case (may be difficult).  It may simply be a poor design.

Just make sure if you send your drive back to be replaced you have COPIED all of it to another drive!  I would also erase everything on a drive I send back under warranty, if possible.

---

### Post by fantab on 2012-06-21
> **ahallubuntu said:**
> As I noted, the drive's firmware has already marked the bad sectors as "do not use" and has re-allocated spare sectors to replace them.

Those bad sectors can't be repaired, but as  of now all drive sectors are working because spare sectors have replaced the bad ones.

If it were me, I would replace the drive under warranty and hope the new drive runs cooler.  Otherwise, the best way to improve the cooling would be to try to remove the drive from its case (may be difficult).  It may simply be a poor design.

Just make sure if you send your drive back to be replaced you have COPIED all of it to another drive!  I would also erase everything on a drive I send back under warranty, if possible.

Off course I will BACK UP all my Media to safety before Replacing.. and I will erase it. Thanks again for the clarifications.

---

### Post by David Andersson on 2012-06-21
> **ahallubuntu said:**
> 
The reallocated sector number is worrisome but not necessarily catastrophic.  If the drive is a few years old and has had a lot of use, a few reallocated sectors is not that unusual.  That means a few sectors have failed and were replaced with spares.  Eventually if sectors keep failing and are replaced, the drive will run out of spares.  You don't have to stop using the drive today, but I would keep an eye on it.


If a bad block is discovered during *write*, it is replaced with a spare block, and everything is fine, for now. If a bad block is discovered during *read*, the data that was in that sector is esentially lost. If it was fil system info, it might be recovered automatically or by a file system check, but if it was data inside a file, there will be an ioerror and the data is lost.

So when bad blocks begin to appear, I would not use the disk to anything important. If you can deduce that all bad blocks are located in a specific small area, you can re-format and mark all blocks around that area as bad, and *hope* the rest of the disk will be fine for a long time (after fixing the cooling). But in this case, if warranty is still valid, replacement is likely the best option.

---

