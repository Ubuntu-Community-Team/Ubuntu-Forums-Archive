---
title: "Canon Canoscan 3000ex"
date: 2013-06-13
forum: Hardware
---

### Post by philpense on 2013-06-13
Have a legacy Canon scanner used on a Vista machine but now might like to try it  on a Lubuntu machine.  Do any of the Ubuntu contributors make drivers?  Just a thought.  Hoping for a reply.

---

### Post by Bucky Ball on 2013-06-13
*Thread moved to **Hardware**.*

Would help if you added Ubuntu release, model of printer and perhaps changed the name to include them. 

Grab the model number and do a search on the interwebs for:

canon 'your model' ubuntu 'your release number'

You might start here:

[https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon)

Good luck and let us know what you find. I just did a search on what you provided and got:

[http://www.dogpile.com/search/web?fcoid=417&fcop=topnav&fpid=27&q=legacy+Canon+scanner+ubuntu&ql=](http://www.dogpile.com/search/web?fcoid=417&fcop=topnav&fpid=27&q=legacy+Canon+scanner+ubuntu&ql=)

---

### Post by philpense on 2013-06-13
Greetings: Much thanks for the timely reply.  It is the Canon canoscan 3000ex.  I will try the suggested links.  Phil Pense

---

### Post by Cheesemill on 2013-06-13
Unfortunately I don't think you're going to have any luck.

The [SANE]("http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON") database lists your scanner as unsupported, and Canon don't provide Linux drivers for it either.

---

### Post by aikishugyo on 2013-06-13
I think you should post to the SANE mailing list. There are many many Canon scanners that have initial support and need testing.
Most of these use Genesys chips, and the genesys backend supports plenty of chips used in various scanners. But each scanners front-end chip and related chips differ so require tuning of the driver.
Please post there and see what can be done.

---

### Post by Bucky Ball on 2013-06-13
Canon never been that well supported (or should I say, have never played real nice with Linux users). ;)

---

### Post by pdc on 2013-06-15
> Canon never been that well supported (or should I say, have never played real nice with Linux users)

......it continues to fascinate me that folks make such statements ..................................I don't think the facts support such beliefs............. it is a curious linux thing that one must condemn canon to be part of the group ..............

---

