---
title: "Stop Ubuntu from re-installing ds2490.ko every kernel upgrade"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by Noob Programmer on 2009-08-20
I was wondering if it is possible to stop Ubuntu from installing the module ds2490.ko every time there is a new kernel upgrade. This way I don't have to remove it every time I do an update.

---

### Post by lemming465 on 2009-08-26
Would creating a file /etc/modprobe.d/blacklist-local.conf containing *install ds2490 /bin/true* do what you want?

---

