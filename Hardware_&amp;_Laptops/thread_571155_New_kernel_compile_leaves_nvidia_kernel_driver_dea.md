---
title: "New kernel compile leaves nvidia kernel driver dead"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by T3h Ub3r K1tten on 2007-10-09
I've tried asking this on irc, but I seem to be getting drowned by all the other questions, so I'll try the forums:

I updated my kernel to 2.6.22-ck and it broke my nvidia driver, so I removed all traces of nvidia and tried installing it with the nvidia site drivers.
Seemed fine but x won't start because of this: 
```
$ sudo modprobe nvidia -v
install /sbin/lrm-video nvidia
FATAL: Error running install command for nvidia
```
All it says, and install /sbin/lrm-video nvidia returns an error code of 0 so it seems to be fine.
X when started just says the same thing, because it tries to modprobe as well.

Using a Geforce FX 5500, which worked fine before the upgrade.
This is Feisty btw.

Edit: Happy birthday to me. :P

---

