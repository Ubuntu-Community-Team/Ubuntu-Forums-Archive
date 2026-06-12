---
title: "Mounting NTFS Raid-0 Drives"
date: 2005-11-04
forum: General Help
---

### Post by 357Magnum on 2005-11-04
Hi, I was wondering if anyone can tell me how to get Ubuntu to auto mount my NTFS raid-0 drives on start-up? I tried to follow the instructions in Ubuntuguide.org but it doesn't work. I'm sure it's because of the RAID but I don't know what to do about it. 

When Ubuntu examines my partitions it lists my raid drives as sda-1 and sdb-1 and then it says "sdb-1 has no partition table" or something similar to that. Is there any way to do it with Raid?

Thx

---

### Post by mlomker on 2005-11-04
I'm not aware of any linux drivers that support NT's software RAID.  You could choose to break the mirror and mount one of the drives.

---

### Post by RAOF on 2005-11-04
Correct me if I'm wrong, but isnt raid-0 striping, not mirroring?  So breaking the mirror makes no sense?

Anyway, I think it depends upon how the drives came to be joined.  If they've been RAIDed together using NT's logical disc manager, I think you're out of luck.  The linux ntfs driver doesn't seem to support that, at all.

On the other hand, if the two drives are plugged into a cheap (software) raid controller, as may be found on many new motherboards, then you may be able to get something to read them (I've never tried, but I seem to remember someone having some degree of success).  Because the on-disc format changes from controller to controller, I'd suggest googling for the raid controller.

---

