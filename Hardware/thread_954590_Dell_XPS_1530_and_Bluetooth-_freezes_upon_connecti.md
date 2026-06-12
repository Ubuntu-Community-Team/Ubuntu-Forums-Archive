---
title: "Dell XPS 1530 and Bluetooth- freezes upon connection"
date: 2008-10-21
forum: Hardware
---

### Post by the2ndgenesis on 2008-10-21
Hey guys, just made a fresh install of Hardy on my brand new Dell XPS 1530. Everything seems to work OK, now that I've installed the applicable nVidia driver through Envy and the restricted Broadcom wireless driver through Synaptic. There is, however, one notable exception to this successful trend.

I've tried to use GNOME's Bluetooth applet to connect to my phone multiple times, and almost every time I try the computer freezes in its tracks once the connection is made, and the Caps and Scroll Lock LEDs are left flashing as I'm forced to hard-restart. I have no idea why this is happening, but I'm pretty sure it's got something to do with the Broadcom driver screwing something up after the connection with the phone is established.

Could anyone help me to indicate the source of this problem and perhaps find a workaround/solution to it? Any help would be HUGELY appreciated; I'd hate to have to boot into Vista (ugh) every time I want to interact with my phone...

---

### Post by Gausian on 2008-10-21
why did you use envy to install the drivers?  mine were automatically detected after installing.

---

### Post by the2ndgenesis on 2008-10-21
> **Gausian said:**
> why did you use envy to install the drivers?  mine were automatically detected after installing.

Simply put, I wasn't as lucky as you were. This had been an issue for other users of my particular card besides me... installing the default driver through Synaptic replaced the desktop with a totally blank screen upon booting, and that obviously was no good.

After a few hours of researching and LiveCD abusing, I decided to give envy a try and presto! It installed flawlessly and everything worked (and still works). It makes me wonder whether it'd be better to install the Broadcom driver again using the Windows version and a third party program (the name of it is slipping my mind) rather than the (proposed) Synaptic alternative...

---

### Post by the2ndgenesis on 2008-10-22
Shameless bump...

---

### Post by the2ndgenesis on 2008-10-25
Final bump before I let this thread sink into the black abyss.

Throw me a bone, guys...

---

### Post by rampras on 2008-12-08
Try the solution mentioned here:
[http://www.megalinux.net/solution-dell-xps-m1530-ubuntu-810-system-freeze-issue/](http://www.megalinux.net/solution-dell-xps-m1530-ubuntu-810-system-freeze-issue/)

I had the same problem, and this solved the issue.

---

