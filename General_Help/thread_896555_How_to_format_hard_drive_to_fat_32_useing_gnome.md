---
title: "How to format hard drive to fat 32 useing gnome"
date: 2008-08-21
forum: General Help
---

### Post by phazer_34 on 2008-08-21
Ok, I LOVE! ubuntu no way am i going to get rid of it, but i want windoze back for 2 reasons: iTunes and my printer suport, so i back up my hard drive, puting windows back on there and partiong and re-install ubuntu.

Ok, heres my problem Gparted for some reason wont let me format to fat32 (Witch i want fat32 for a couple reasons i can't explain) nor will it let me partion it at all, everything is grayed out.  i have a 550 gig harddrive thats in ext3 form with just ubuntu on it, i have xp disk and ubuntu disk. so please help me here!.

EDIT:I noticed i typed "Gnome" instead of gparted sory :P)

---

### Post by drs305 on 2008-08-21
It sounds like your partitions are still mounted.  You can't run gparted on a mounted partition. To perform operations on the root partition or other partitions which the system won't let you unmount you have to use either the liveCD or something like systemrescuecd.

The latter has lots of good apps on it and you can download it from [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

Another mistake sometimes made in gparted is not selecting a partition to work on. Remember to select a partition in the top section - it should be highlighted with dashes if it's been selected.

---

### Post by phazer_34 on 2008-08-21
Thanks for the speedy rely!, il try the live cd and post feedback.

---

