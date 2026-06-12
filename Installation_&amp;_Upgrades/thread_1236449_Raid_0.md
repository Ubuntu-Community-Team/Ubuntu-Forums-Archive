---
title: "Raid 0"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by SuperMiguel on 2009-08-10
Im currently have ubuntu installed and im using mdraid on raid 0, basically i have a 100mb partition for /boot, and a raid 0 (mdraid using 3 drives). This is my home system, and i want it to run fast. is there a better way to do it with what i have? note my mobo has a fake raid. but alot of people say that i should avoid using dm-raid.. any reason why?

Thanks

---

### Post by ronparent on 2009-08-10
The primary reason for using dmraid is if you need to access your raids from both ubuntu and windows. Otherwise there doesn't appear to be a compelling reasont for using either one in preference to the other. With a raid 0 especially there are compelling reasons for ba good backup scheme. Primarily because the data is striped over the raid drives, a loss of one drive will effectively cause you loss of all data on all drives (over which the data is striped).

---

### Post by SuperMiguel on 2009-08-10
well with dm raid i will be able to install everything on my raid 0. with mdraid i have to make a separate unraided partition for my /boot. Which slows down the system a bit, i dont need to share data to a windows part, since i dont have one.. For performance only, will dm raid be faster than md-raid??

---

