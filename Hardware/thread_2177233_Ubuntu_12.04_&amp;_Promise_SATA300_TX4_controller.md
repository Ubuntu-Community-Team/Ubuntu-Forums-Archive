---
title: "Ubuntu 12.04 &amp; Promise SATA300 TX4 controller"
date: 2013-09-27
forum: Hardware
---

### Post by alienprdkt on 2013-09-27
I have read that this is suppose to work out of box and I cant figure out how that is possible?

Anyways downloaded source for driver. Upon make I get this:
```
/pdc-ulsata2# make
Makefile:57: *** Linux kernel source not configured - missing config.h.  Stop.
```
also have tried this:
```
/pdc-ulsata2# lsmod|grep -i promise 
sata_promise           18003  0 

```
it recognizes the card but how can i get it to detect hard drives attached to it?

Please help,
thanks in advance

---

