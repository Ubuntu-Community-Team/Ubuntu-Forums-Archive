---
title: "hide onboard raid drives completely?"
date: 2008-09-27
forum: General Help
---

### Post by bsh on 2008-09-27
hello
i have 4 hard disk in my pc, 2 of them (sata drives) are configured as raid0 using the onboard raid (nforce4ultra), the third one (sata) is a a single drive (not part of any raid arrays), and the fourth one is an ide drive (no raid).

ubuntu is on the ide drive.

i have windows xp installed onto the "hradware" raid array.

the problem is, ubuntu doesn't recognize the array as raid (i don't even want to!), but as two separate drives, and when the kernel loads, it keeps displaying error messages that the drives are unknown, filesystem unknown, etc. and later, when the system is running, i get tons of error messages in syslog, about the drives aren't responding and what not.

i just want to completely hide the two drives from ubuntu, at the kernel level, so it doesn't even try to use them, and to avoid it to touch anything on the two drives.

is this somehow possible?

afaik, grub can only hide partitions, and that's not what i want to do.

---

