---
title: "Gutsy freezing on boot... keyboard flashes"
date: 2008-11-15
forum: General Help
---

### Post by gschoppe on 2008-11-15
gutsy froze on me today, no mouse motion, no keyboard input... after a few seconds, the caps lock and scroll lock buttons started flashing, then went solid, with no ability to alter their state... I tried a fsck just in case, but the disks (one standard install partition, two drives spanned by an lvm) seem to be ok... on reboot, the system freezes a couple of seconds after loading the desktop,... same as above.



any ideas?

---

### Post by gschoppe on 2008-11-16
ok, so I know its a kernel panic (damn) now, how do I get at the system log (from live cd) to figure out what's causing it?


still crashing on every reboot (i'm thinking power supply is giving insufficient current, but that's a wild guess based on its 550W rating and my 2 HDDs and embedded LCD, but if so, why now?)


any help appreciated.

---

### Post by gschoppe on 2008-11-17
new kernel (8.10 install) seemed to fix it

---

