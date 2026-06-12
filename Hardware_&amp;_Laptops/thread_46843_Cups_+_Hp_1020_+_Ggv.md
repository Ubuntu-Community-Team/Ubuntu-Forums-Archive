---
title: "Cups + Hp 1020 + Ggv"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by Ferran on 2005-07-06
I've just upgraded from Warty through a fresh install (I tried upgrading and such, but ended up trying some Breezer thingies and...). I'm trying to make an HP Laserjet 1020 work. Now, it sort of does but it hangs the usb seriously after about 40 pages. I'm using an up-to-date cups with modifications from [http://support.ideainformatica.com/hplj1020/](http://support.ideainformatica.com/hplj1020/)  (and, now, maybe some ppds from Breezer).
OTOH, while we're at it: gdm-Circle of friends in Hoary has 3 or 5 people? Preview says one thing, but GDM says another.
Thanks.

[INDENT]$ sudo usb_printerid /dev/usb/lp0
Error: Device or resource busy: can't open '/dev/usb/lp0'
[/INDENT]

---

### Post by Ferran on 2005-07-07
I've been checking further. There are troubles with USB handling. There's a process that so far has worked for me to unblock the printer w/o a system reset:

a) Hold job & halt printer (via [http://localhost:631](http://localhost:631) ; you'll need to have cupsys added to group shadow --and restart cupsys-- if you want to act through http-cups)
b) Turn printer off
c) Unplug USB
d) Turn printer on
e) Plug USB
f) Update firmware
e) Start printer & release job

It's quite sensitive to changes. For instance, Pluggintg USB before turning printer on seems to block the system again.

---

