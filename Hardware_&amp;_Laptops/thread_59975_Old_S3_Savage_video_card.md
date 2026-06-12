---
title: "Old S3 Savage video card"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by ltracy on 2005-08-26
Ubuntu installed on my old desktop with no problems, however the detected card is using the stock ubuntu S3 ProSavage DDR driver (savage).  This is fine resolution wise, but I am only getting like 120 FPS with glxgears.  This seems like it is WAY too slow, and I was wondering if there is a fix for this.

---

### Post by nad on 2005-08-26
[http://www.x.org/X11R6.8.2/doc/savage.4.html](http://www.x.org/X11R6.8.2/doc/savage.4.html)
The default option is to enable acceleration, so, I don't see any hope here.

Development is however continuing:
[http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html)
[http://www.research-labs.net/library/video/h07txt-twisterDRI.txt](http://www.research-labs.net/library/video/h07txt-twisterDRI.txt)

This has always been a problem with the open source drivers. There is just not enough time, manpower and information to make them acceptable to gamers. The reason that so many currently use adapters from nVidia and ATI with the proprietary drivers.

Speaking of proprietary drivers, there may be one available for your card, but you will have to pay for it. It is probably more worthwhile to simply acquire a modern card.

---

### Post by moopere on 2005-08-26
[QUOTE=ltracy]Ubuntu installed on my old desktop with no problems, however the detected card is using the stock ubuntu S3 ProSavage DDR driver (savage).  This is fine resolution wise, but I am only getting like 120 FPS with glxgears.  This seems like it is WAY too slow, and I was wondering if there is a fix for this.[/QUOTE]

What makes you think that 120FPS is too slow?  

glxgears is notorious for being inaccurate so I wouldn't get too concerned unless you know for sure that your card is underperforming.

Cheers,
Craig

---

