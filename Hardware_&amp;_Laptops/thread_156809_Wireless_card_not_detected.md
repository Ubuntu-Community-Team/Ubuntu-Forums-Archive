---
title: "Wireless card not detected"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by wagdog on 2006-04-07
I installed an AirLink AWLH4030 (chosen because it's listed as 'works out of the box') but Breezy doesn't seem to recognize it.  It doesn't show under System>Administration>Networking although my hardwired ethernet card does.

I'm thinking this has to be an easy fix because when I boot from the live disk the  card automatically shows up as ath0 and works just fine.

Any ideas as to how I can get my installed Breezy to detect this card?

Thanks!

---

### Post by wagdog on 2006-04-08
Is there someway to force hardware detection/setup on reboot (like what the live cd does)?

---

### Post by hajk on 2006-04-08
Yes, it is an easy fix! Your card has an Atheros chip (judging from the ath0 interface), so you must install the madwifi driver for it. This driver is contained in the linux-restricted-mudules package, choose the one that matches the installed kernel (this is important). Find out about the kernel by giving the command
"uname -r" in a terminal. The driver will be installed automatically once the card is recognized (on boot or on insertion). Then you can configure the interface, but you already know how to do that from the live-CD (you could try System -> Administration -> Networking). 

Have fun!

---

### Post by wagdog on 2006-04-08
Thanks hajk, that did the trick!  
The one other 'gotcha' I encountered was I had to disable my wired ethernet card before the wireless would talk to the router.  Just unplugging the wire was not sufficient.

---

### Post by hajk on 2006-04-08
The wired eth0 could also be active (should you so wish), but there can only be one default route, either eth0 or ath0... there should be no uncertainty for the kernel as to where to send packets. Anyway, glad that it works.:-D

---

