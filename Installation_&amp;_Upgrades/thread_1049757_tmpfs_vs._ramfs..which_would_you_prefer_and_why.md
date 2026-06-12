---
title: "tmpfs vs. ramfs..which would you prefer and why?"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by bosworthy on 2009-01-24
tmpfs vs. ramfs..which would you prefer and why?
:)

---

### Post by ajmorris on 2009-01-25
hi there,
I use tmpfs for one simple reason. Data in tmpfs can be swapped out, data in ramfs, can not. I need my swap space, so i use tmpfs. Another valid reason for preferring tmpfs, is that glibc explicitly depends on it to pass it's checks.
These are the 2 main reasons, that these days, standard distros enable tmpfs by default.


AJ

---

### Post by bosworthy on 2009-01-29
Thanks AJ

---

