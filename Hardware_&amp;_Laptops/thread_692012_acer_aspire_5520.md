---
title: "acer aspire 5520"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by pacco on 2008-02-09
I can't seem to get my card reader to work, how would i get it to work?

---

### Post by bobyy on 2008-02-09
Hy ...try with this:
> 
$sudo modprobe tifm_core
$sudo modprobe tifm_sd

and the SD card shows up

adding:

tifm_core
tifm_sd

to /etc/modules will have them load at boot

good luck.!!

---

