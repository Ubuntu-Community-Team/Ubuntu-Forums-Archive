---
title: "Problems with bcm43xx"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by drascus on 2007-09-23
I have a Broadcom wireless card and got it running with fw-cutter program. It has been humming away without incident for a while. Lately however my connection will just die for no reason. Sometimes the wirless card will shut off for no reason. I did a fresh install and set everything back up. however the problem persists. Does anyone know how I might go about resolving this?
~Mike~

---

### Post by arranmc182 on 2007-11-19
try going to [http://linuxwireless.org/](http://linuxwireless.org/) and downloading the Linux wirless drivers from there they worked 100% for me and works a lot better than ndiswrapper as it puts the drivers right in to the mian kernel and its all verry simple to install.

here is just some of the drivers u will get

b43/b43legacy (Broadcom chips)
ath5k (Atheros devices)
adm8211 (ADMtek devices)
madwifi (Atheros devices)
p54 (Intersil chips)

and there are even more drivers built in all you have to do us install it and linux will detect what driver is needed if you have compatable hardware

---

