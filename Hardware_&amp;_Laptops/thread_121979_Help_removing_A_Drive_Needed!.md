---
title: "Help removing A: Drive Needed!"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by kudu on 2006-01-26
My A: drive (floppy drive) died. Actually it never worked from day 1, but it decided to suddenly make a continuos loud obnoxious humming noise so I removed the offending appendage altogether. However, since I installed ubuntu with it plugged in it is officially listed as onboard my PC.

My question is how do I tell ubuntu it is no longer installed ? I want to remove it completely from my ubuntu installation. All traces must go !

Help appreciated.

Regards,
kudu...out

---

### Post by az on 2006-01-26
Remove it from your fstab

/etc/fstab

look for the /dev/fd0 entry.

---

### Post by kudu on 2006-01-26
Merci boucoup Azz, much appreciated.

Regards,
kudu

---

