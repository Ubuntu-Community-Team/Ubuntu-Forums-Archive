---
title: "How to get rid of XP?"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by andrew_D14 on 2009-06-16
i just installed ubuntu and plan on keeping it since my windows xp is a counterfeit anyway. However, everytime i restart or turn on the computer, i have to press F12 to get to the boot menu and choose ubuntu otherwise it starts up windows xp. So how do i get rid of windows xp completely and run ubuntu only?

---

### Post by merlinus on 2009-06-16
Did you install ubuntu under windows, or on its own?  If the former, then you will have to reinstall it to its own partitions.  Select guided - use entire disk at the partitioning menu.

---

### Post by izizzle on 2009-06-16
^ +1

---

### Post by hayden92 on 2009-06-16
Hey Andrew,

If you installed Ubuntu on a seperate partition you will be able to just wipe your windows one and the GRUB bootloader should automatically boot you into Ubuntu by default. If you installed through WUBI, that's a different story.

P.S. I would use gparted on the LiveCD to repartition

Hope that helped!

Hayden

---

