---
title: "why is /media in PRUNEPATHS in /etc/updatedb.conf"
date: 2008-11-30
forum: General Help
---

### Post by Awareness on 2008-11-30
I noticed /media in in updatedb.conf in the PRUNEPATHS by default and I wonder why...

(PRUNEPATHS="/tmp /var/spool /media")

Who wouldn't want all his disk indexes by default... is there some kind of problem if I do so? coz i do want all my disks indexed...

Plus the partitions only mount when i click on them... this could be a problem, couldnt it?

---

### Post by Elfy on 2008-12-23
Hi - I wasn't sure of the answer to this so I did it.

I would assume that if a disk wasn't permanently mounted it could cause some issues, my disks are mounted permanently with fstab.

After 3 weeks I've not seen anything untoward here.

That doesn't mean that others wouldn't though.

---

### Post by Awareness on 2009-01-25
I assume is ok then... ill mount then in fstab too :) thanks

---

### Post by sdennie on 2009-01-25
Things in /media are generally auto-mounted on insertion via udev so, they are considered transient mount points.  For most people, it doesn't make much sense to include /media results in the output of "locate" because they aren't using permanent media via /media.  If you are using permanent media then you may want to setup /etc/fstab to mount it in /mnt/whatever or somewhere else.  Or, you can remove that prune path and let it be indexed.  There should be no harmful side effects to do the latter except that your information from "locate" may not always be accurate.

---

