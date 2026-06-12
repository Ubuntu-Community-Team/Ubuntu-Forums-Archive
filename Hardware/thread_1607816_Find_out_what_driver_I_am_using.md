---
title: "Find out what driver I am using"
date: 2010-10-28
forum: Hardware
---

### Post by Robert Buckmaster on 2010-10-28
Is there a way of finding what driver I am using for wifi so that I may copy it to another Linux operating system and use it there?

---

### Post by linux-hack on 2010-10-28
Take a look at this :[http://www.cyberciti.biz/faq/linux-find-wireless-driver-chipset/](http://www.cyberciti.biz/faq/linux-find-wireless-driver-chipset/)

---

### Post by Yellow Pasque on 2010-10-28
```
sudo lshw -C network
```
Copying the drver itself probably won't work unless you're running the exact same kernel version, and if that's the case, I doubt it would be necessary.

---

