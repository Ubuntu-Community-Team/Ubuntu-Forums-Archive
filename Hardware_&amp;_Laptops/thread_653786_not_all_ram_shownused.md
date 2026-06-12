---
title: "not all ram shown/used"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by superaktieboy on 2007-12-30
Hey guys..

im having a weird problem which is just found out:
when i was running XP i used to have a 512MB ram, while still on xp i upgraded that to 1.5GB (bought a 1GB ram) on XP this works wel, and it shows that i have 1.5GB installed.
now i have dualbooted Ubuntu for quite a while, and just today i found out that the RAM doesn't work proper (i think), coz System Monitor only shows 512 MB RAM while it should be 1.5GB ram.. while on  XP it does say 1.5GB!

can anyone help me?


greeetzz

---

### Post by taurus on 2007-12-30
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
free
```
Maybe you should run the memtest at the GRUB menu.

---

### Post by superaktieboy on 2008-01-01
this is the output i get
```
             total       used       free     shared    buffers     cached
Mem:       1555864     574304     981560          0      14296     281732
-/+ buffers/cache:     278276    1277588
Swap:       265064          0     265064
```

and how do i run the memtest in the grub menu (infact what is the grub menu?)

edit: weird, this time i went to system monitor and it shows 1.5GB how come?

---

