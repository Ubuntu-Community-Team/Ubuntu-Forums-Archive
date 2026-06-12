---
title: "Laptop Screen Won't Go Off with 10.04"
date: 2010-08-06
forum: Hardware
---

### Post by chris1379 on 2010-08-06
This is on a Sony Vaio PCG-F580K with Ubuntu 10.04. When I set my Power Management to "Put display to sleep when inactive for" a length of time, the screen doesn't go off like it should. I can make it go off with the command: ```
xset dpms force off
``` but it comes back on in a few seconds. If I give the command a few times it will eventually stay off. After that it will automatically go off too. Power Management works fine in Windows and earlier versions of Ubuntu.

---

### Post by chris1379 on 2010-08-19
I found the answer. It has to do with the bug at [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/539515](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/539515)
I disabled the floppy disk in the BIOS and it's all back to normal.

---

