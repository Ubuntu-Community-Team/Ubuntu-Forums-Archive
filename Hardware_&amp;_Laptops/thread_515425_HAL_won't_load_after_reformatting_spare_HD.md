---
title: "HAL won't load after reformatting spare HD"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by oldmanstan on 2007-08-02
I formatted an extra hard drive that used to be a primary hard drive, in other words I used gparted to make it one big ext3 partition (deleted each of the partitions then created new one).

after I did this, I restarted the window manager (ctl-alt-back) and now I get an error message as gnome starts that HAL can't load.

how do I fix this?  didn't think it would get cranky at me for reformatting a drive :)

UPDATE:

ok, so I figured rebooting might solve the problem, it did for some reason.  now the question is, what caused the issue and how do i keep from breaking it next time? (i HATE rebooting)

thanks!

---

### Post by kidders on 2007-08-03
Hi there,

You probably upset hal (and who knows how many other things) by recreating fewer partitions than you deleted, thus invalidating some device nodes in /dev, so unexpected things happened when hal tried to access them. It's not really advisable to play with a partition table without rebooting ... or at least re-probing your partition tables.

Does that sound like a reasonable explanation?

---

### Post by oldmanstan on 2007-08-04
excellent, and completely logical... i should be more careful not to upset hal

thanks!

---

### Post by kidders on 2007-08-04
No worries. :-)
Glad I could help.

---

