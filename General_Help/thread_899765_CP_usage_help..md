---
title: "CP usage help."
date: 2008-08-24
forum: General Help
---

### Post by treehouse on 2008-08-24
I have a failed drive I'm recovering with the freezer method (so time is of the essence while copying). I have part of it already recovered, and I'm trying to copy everything within a huge folder that hasn't already been copied as fast as I can.

So I'm trying to take all original folders and files from /media/disk/thisfolder/(allthecontents) and put them in /hdb/thisfolder/(allthecontents). I'm not sure what syntax to use.

Is this correct?

cp -pru /media/disk/thisfolder /hdb/thisfolder

do I use wildcards at the end?

---

### Post by eggdeng on 2008-08-24
Assuming /hdb is a top-level folder, this is OK. (Partitions are usually mounted under /media though.) No need for wildcards.

---

### Post by treehouse on 2008-08-24
Awesome, thanks, and yeah, I have /dev/hdb1 mounted to /hdb.

---

