---
title: "not detecting RAID"
date: 2010-11-05
forum: Hardware
---

### Post by creatureofthedark on 2010-11-05
i have just got a tyan transport GT20 (yes is nice and old) i have it setup with a raid 5 and 3 500GB HDDs....


when i try and install any OS it dosent seem to detect the HDD yet the raid controller seas that everything is ok....

iv tired smoothwall and ubuntu server 10.10 nether seem to work....

any ideas?

---

### Post by TSJason on 2010-11-05
I know that support for nforce raid is generally poor. Is there a boot utility that you can run to create the array and initialize it, or is this just a bios setting that toggles between "raid" and "normal" modes? You might be better off setting the drives to normal mode (or ATA mode - what have you) and going the software raid direction.

---

### Post by creatureofthedark on 2010-11-05
i have used the boot utility to configure and initialize the array and as far as it was consirned it all works well.... but the ubuntu doesn't see it.... i will look at how to bypass the raid controller and see if that works.. i don't actually need a raid but when i take it off the raid controller complains during boot

---

### Post by creatureofthedark on 2010-11-05
yup that did the trick..... how come i dident think of that before..... chears dude!!!

---

