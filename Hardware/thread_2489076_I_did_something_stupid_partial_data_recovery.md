---
title: "I did something stupid/ partial data recovery?"
date: 2023-07-17
forum: Hardware
---

### Post by johnzbesko on 2023-07-17
A disk in a Raid 1 volume went bad. I attempted to copy/diskimage from the good drive to a new empty drive. I inadvertently started copying the empty drive to the good drive, realized my error and stopped the operation well before it finished. (Both drives are 1TB.) Is there anything I can try to salvage any of the data on the not-so-good-anymore drive?

---

### Post by TheFu on 2023-07-18
"anything?"  Sure.  "Anything practical", probably not.

There are many different types of RAID, so which RAID subsystem was being used might help.  In general, you shouldn't manually copy anything when trying to add a replacement disk into a RAID array.  Use the RAID software to "synch" data and let the RAID software decide which direction that needs to happen. 

This is another example of why we always say that RAID never replaces the need for backups.  RAID solves 2 issues.  Backups solve 101 - 1001 issues, including a corrupted RAID.  If you don't have excellent backups, then you don't have any business using RAID.

---

