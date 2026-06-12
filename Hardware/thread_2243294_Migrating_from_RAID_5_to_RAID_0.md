---
title: "Migrating from RAID 5 to RAID 0"
date: 2014-09-07
forum: Hardware
---

### Post by vbalbert on 2014-09-07
I've been informed that RAID 5 is pretty much useless these days and that nobody has any real success stories from recovering from problems with it.  That said, I've decided that I'd like to convert my 5 disc RAID 5 array to RAID 0 so I can have the full amount of space available for data.  I've not been able to decipher the documentation of mdadm to figure out how to do this.  Can anybody help me do this without loss of data?  I'm pretty unconcerned with the amount of time this will take.

---

### Post by Vladlenin5000 on 2014-09-07
Honestly, provided you have storage space outside the array, I would just backup the relevant data, rebuild the RAID and install again. But that's just me... Let's wait for other inputs/opinions.

---

### Post by weatherman2 on 2014-09-07
I agree.  Don't treat the original as a RAID - just copy everything off to another disk, then break the RAID and make a new RAID 0 if that's what you want.  Or (safer) build the new RAID 0 first then copy - but you'll need extra disks.

You should have a backup of your RAID somewhere else anyway, as RAID doesn't protect against file system corruption, accidental deletions, etc.

---

### Post by 1clue on 2014-09-07
Why raid0?  That's Russian roulette.  If any disk breaks you lose everything in all disks.

If all your data fits in raid5 then make the new array raid1.  At that point every disk holds identical data which is useful on its own.  Or go raid10, which is raid0 and raid1 combined.

---

