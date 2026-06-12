---
title: "Looking for...."
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by Morfus on 2006-03-01
Belkin F5D6020 Linux drivers that will work in Ubunto.

Ubunto sees the PCMCIA card and sees it is a Belkin F5D6020, but needs a driver to properly configure it so I can browse the network.

Anyone know/seen a driver?

---

### Post by Brunellus on 2006-03-01
according to [this site](http://questier.com/howto.html#Belkin), that card uses the Atmel chipset, but may require the installation of firmware.  (note that while the site references Debian Sarge, it may be of relevance to you).

so try what they suggest and install the atmel firmware with

sudo apt-get install atmel-firmware

A quick Google also reveals that there are multiple versions of this same card.  Version 2 (printed on the back, apparently) is the one with the atmel chipset which should work.

---

### Post by Morfus on 2006-03-01
Excellent and thank you.

I was googling and found much of the same things, but wanted the opinion of older linux users, and i realize that the only way to find out, is to try.

Again thank you.

---

### Post by Brunellus on 2006-03-01
[QUOTE=Morfus]Excellent and thank you.

I was googling and found much of the same things, but wanted the opinion of older linux users, and i realize that the only way to find out, is to try.

Again thank you.[/QUOTE]
wlan support is the bane of the desktop linux user's existence.  The main lesson to learn is, in the future, try to buy hardware that is already known to work.

---

