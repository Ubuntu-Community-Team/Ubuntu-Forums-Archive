---
title: "recovering files from dd-based backup"
date: 2008-09-23
forum: General Help
---

### Post by akadruid on 2008-09-23
Hi all,

I have a full drive backup of a friends computer for which I used dd, while running from an ubuntu live cd, and gzipped the output and copied it over to my computer (running 8.04).

Now the backed up disk has died, and I plan to restore the backup onto a new disk when it arrives, but we really need to get a couple of files from the backup now.

The backed up drive was 120GB, and I have more than that spare on my 8.04 machine - is there some way I could safely restore the dd backup to my disk to get at those files? e.g. create a new partition or something using gparted?  I only have the one disk (/dev/sda1/) and I really can't afford to accidently overwrite it or anything...!

Thanks in advance!

aka

---

### Post by roaldz on 2008-09-23
Maybe it is possible to gunzip it, and try to mount it. I'm not sure it works.

---

