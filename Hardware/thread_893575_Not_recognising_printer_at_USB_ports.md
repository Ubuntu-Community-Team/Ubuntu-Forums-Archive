---
title: "Not recognising printer at USB ports"
date: 2008-08-18
forum: Hardware
---

### Post by voteforpedro on 2008-08-18
I'm trying to install my HP PSC 1210 USB printer on Ubuntu Server (Hardy Heron) using the hplip driver.

I'm not at the computer right now so I can't copy and paste anything but here's what I've tried so far:

*hp-setup*

Detects the printer as HP 1200 series;
Can install and set queue name;
Says it's printing test page but nothing prints off.

*lsusb*

Four "devices", nothing connected on each. Tried all four ports. Now if I plug in my N95 phone, it says "Nokia something-or-other", which confirms USB ports are working properly.

*dmesg*

Plug printer in and no messages are displayed in dmesg. Plug phone in and it updates correctly and displays message once disconnected. Reports nothing when I plug printer into same USB port.

USB cable works properly. In fact, I have Hardy desktop on my desktop PC and I just plugged in the HP printer for the first time and it detected it and I can print to it... odd.

Any thoughts?

---

### Post by timcredible on 2008-08-18
you don't need to do anything to setup that printer in 8.04, just boot the pc with the printer plugged in and turned on, and the system will setup your printer and your scanner automatically.

---

