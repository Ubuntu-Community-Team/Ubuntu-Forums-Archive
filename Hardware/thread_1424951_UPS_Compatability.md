---
title: "UPS Compatability"
date: 2010-03-08
forum: Hardware
---

### Post by Magma828 on 2010-03-08
I'm thinking of getting a UPS for my ubuntu machine, but I would like it to be fully compatible and turn off the computer cleanly (and maybe even run some scripts!) when the power goes out.

What would you guys suggest? I'm looking at play.com because I've bought stuff from there before without problems and I've got an account etc..

I think these are all the UPS's they have:
http://www.play.com/HOME/HOME/6-/Search.html?searchstring=ups&searchtype=PCSH&searchsource=2&searchfilters=s{ups}%2bc{420}%2b

This one looks interesting:
[http://www.play.com/PC/PCs/4-/12083085/APC-BE550G-UK-Power-Saving-Back-UPS-ES-550VA-UPS-With-8-Outlets/Product.html](http://www.play.com/PC/PCs/4-/12083085/APC-BE550G-UK-Power-Saving-Back-UPS-ES-550VA-UPS-With-8-Outlets/Product.html)

My budget is preferably less than £60 but I'll pay up to £75 if it's worth it.

---

### Post by blur xc on 2010-03-08
Check out [apcupsd]("http://www.apcupsd.com/")-


BM

---

### Post by Magma828 on 2010-03-08
> **blur xc said:**
> Check out [apcupsd]("http://www.apcupsd.com/")-


BM

Ok looks good. I don't really know how UPS's work though. Would I just connect the UPS with USB and apcupsd would handle everything? My server is basically a normal desktop computer without a keyboard, mouse, monitor etc.

---

### Post by blur xc on 2010-03-08
> **Magma828 said:**
> Ok looks good. I don't really know how UPS's work though. Would I just connect the UPS with USB and apcupsd would handle everything? My server is basically a normal desktop computer without a keyboard, mouse, monitor etc.

I'm no expert, but I think that's how it works.  BTW, I was having a hard time setting mine up- but it turned out I was issuing the commands w/o using sudo.  You need root privileges to mess with it.

Good luck.

BM

---

