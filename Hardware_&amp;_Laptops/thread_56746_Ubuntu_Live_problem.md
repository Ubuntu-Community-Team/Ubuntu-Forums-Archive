---
title: "Ubuntu Live problem?"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by ecbrown on 2005-08-13
Hello, I'm trying to use a Ubuntu live CD to see if my WIndows HD has died on me.
Tried the normal mounting procedures (mount -t ntfs /dev/hda1 /tmp) but that didn't work.  

I then went to the /dev directory, did a MAKEDEV hda1, and was told "I don't know how to make hda1" by the script.

so I tried lsmod to see what I COULD do, hda isn't one of them.


Unless I'm missing something HUGE, how do I mount this fs?


ecb

---

