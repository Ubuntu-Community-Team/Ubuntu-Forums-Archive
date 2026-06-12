---
title: "Wireless Network on Startup"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by grj on 2005-07-24
I cannot get my wireless to connect on startup. After logging
in if I type sudo dhclient3, it works fine. Below is my 
interfaces file:
auto lo
iface lo inet loopback

mapping hotplug
script grep
map ath0

wireless-mode managed
wireless-essid any

My card is a D-Link DWL-G650

Thanks,

grj

---

### Post by gmc on 2005-07-25
Ummm, aren't you missing the following lines?

iface ath0 inet dhcp
auto ath0

G.

---

### Post by ssck on 2005-07-26
[QUOTE=grj]I cannot get my wireless to connect on startup. After logging
in if I type sudo dhclient3, it works fine. Below is my 
interfaces file:
auto lo
iface lo inet loopback

mapping hotplug
script grep
map ath0

wireless-mode managed
wireless-essid any

My card is a D-Link DWL-G650

Thanks,

grj[/QUOTE]


alternatively you could use gtkwifi

---

