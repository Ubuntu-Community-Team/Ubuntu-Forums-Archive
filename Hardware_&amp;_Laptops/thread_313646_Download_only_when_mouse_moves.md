---
title: "Download only when mouse moves"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by MadEagle on 2006-12-06
Hi!

I am new to Ubuntu but seasoned to Linux and I have a very weird problem.

I am running Ubuntu 6.10 with latest updates. Now whenever I try to download a file the program (firefox, system updater etc.) just sits there and does nothing UNLESS I move my mouse. Then it downloads stuff. This is the same for a wget session in a terminal window. On command line without X net access doesn't work at all. This is almost as if the network adapter and the USB hub share the same interrupt or something.

I am totally at a loss here. ](*,) Any ideas?

MadEagle

---

### Post by zgornel on 2006-12-06
You can check irq's by typing *lshw* although I doubt this is the problem. After entering X, do ALT+CTRL+F1, login, then type *wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.19.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.19.tar.bz2)* and see if it works as a test.

---

