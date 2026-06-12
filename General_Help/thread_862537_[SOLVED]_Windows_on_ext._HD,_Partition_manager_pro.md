---
title: "[SOLVED] Windows on ext. HD, Partition manager problems?"
date: 2008-07-17
forum: General Help
---

### Post by kovankerckhoven on 2008-07-17
Hi everyone :)

For gaming purposes, I want to install windows XP on a small partition on my 320 GB HD. When  I tried installing it through the windows boot CD, it said I needed to copy some files to the internal HD to install, and that it couldnt copy those files because the internal HD (Filled up with Ubuntu Hardy) doesn't have a format supported by Windows or something...

Thus, I downloaded and installed (sudo apt-get install) gparted, as it seemed to be the best partition manager for Linux :) When I open gparted (both from command line, with sudo; or from System->...->Partition Manager)
it won't let me edit or expand any of the partitions( from either internal or external HD.)

Any help would be appreciated :lolflag:

---

### Post by dracayr on 2008-07-17
of course it won't let you change a mounted partition. You have to use the ubuntu liveCD and run gparted from there (System&#8594;Administration&#8594;partition editor)

dracayr

---

### Post by unutbu on 2008-07-17
You can't modify mounted partitions. Boot from the Ubuntu LiveCD, and open GParted from there.

---

### Post by kovankerckhoven on 2008-07-17
But on my Live CD there isn't any gparted installed... Can I just install it and use the program without rebooting?

---

### Post by kovankerckhoven on 2008-07-17
Done... I unmounted ext. HD and did it with Gparted. Thx everyone :)

---

