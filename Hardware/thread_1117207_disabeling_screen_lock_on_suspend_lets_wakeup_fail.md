---
title: "disabeling screen lock on suspend lets wakeup fail"
date: 2009-04-05
forum: Hardware
---

### Post by phorminx on 2009-04-05
When I disable the screen lock on suspend (gnome-power-manager), the wakeup will fail the first time I try it (for lenovo x300 running ubuntu 8.10):

When I wake up the computer after suspend, it will immediately suspend again. Then when I wake it up a second time, it stays awake as expected.
This problem exists only if "Lock screen on suspend" is disabled. No such problem exists if "Lock screen on suspend" is enabled.

All this looks like an odd timing issue. Is there some other setting that should be changed to fix this?

Thanks!

---

### Post by bb2b on 2009-04-22
I confirm exactly same problem

---

### Post by ohiomoto on 2009-04-22
[http://ubuntuforums.org/showthread.php?t=1130461](http://ubuntuforums.org/showthread.php?t=1130461)

---

