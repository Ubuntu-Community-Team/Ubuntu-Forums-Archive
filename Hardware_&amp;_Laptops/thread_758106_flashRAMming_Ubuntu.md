---
title: "flashRAMming Ubuntu"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by yanom on 2008-04-17
I know it is possible on Windoze Vista to plug in a USB flashdrive/camera memory card and make the computer treat it as RAM. Is that possible on Ubuntu

---

### Post by kerry_s on 2008-04-17
sure you can make the usb swap, but why bother, you'll just ware out the usb faster.

how much ram do you have that your worrying about this?
did you make a swap partion when you installed?

linux is not window's and uses ram differently, the more ram used the better the performance on a linux system. that means it's caching/buffering your most used programs for quicker use, cause ram is faster than hd.

---

### Post by yanom on 2008-04-17
Yes I do have a swap

I don't care if I ware out the USB, it's an spare dive i'm not using.

---

### Post by kutjara on 2008-04-17
> **kerry_s said:**
> sure you can make the usb swap, but why bother, you'll just ware out the usb faster.

how much ram do you have that your worrying about this?
did you make a swap partion when you installed?

linux is not window's and uses ram differently, the more ram used the better the performance on a linux system. that means it's caching/buffering your most used programs for quicker use, cause ram is faster than hd.

Vista's ReadyBoost is a bit different from simply shoving swap onto a USB. It's used in combination with SuperFetch to put the data you use most onto the USB, where it will be more quickly available. The speed benefits of ReadyBoost are only partly to do with Flash memory's faster access times, and partly to do with the way SuperFetch allocates data. It's quite a useful feature on relatively low-memory systems (which, with Vista, means anything with less than a terabyte of RAM), but I'm honestly not sure that it would be much use with Linux, which is far more efficient in its use of system resources.

---

### Post by yanom on 2008-04-18
RAM is a really big problem on my computer

---

### Post by sdennie on 2008-04-19
> **yanom said:**
> RAM is a really big problem on my computer

It would be useful to know how much RAM you have, what you use the machine for and how you determined that RAM is a problem on your machine.  The output of "free -m" would be useful as well.

---

