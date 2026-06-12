---
title: "Poulsbo intel GMA500"
date: 2012-01-02
forum: Hardware
---

### Post by ATAQ on 2012-01-02
Hey all, my gf has a netbook with its graphics chipset based on the dreaded GMA 500 from Intel.
She wants to migrate to linux, although I am sketchy, because I dont know what the support is like nowadays for the GMA500, will it work on Xorg with acceleration, at least enough to watch a movie in VLC player and firefox, smooth scrolling. I generally stick to everything nVidia myself, but she already owns the netbook, so what ya gonna do

---

### Post by MoreOrLess on 2012-01-02
[http://www.phoronix.com/scan.php?page=news_item&px=MTAzNTE](http://www.phoronix.com/scan.php?page=news_item&px=MTAzNTE)

---

### Post by ATAQ on 2012-01-02
Has anybody got any real user experience on this?
Other than posting links

---

### Post by mikewhatever on 2012-01-04
I am a not so proud owner of a Dell Mini 10 with GMA500. It's been working for two years, better then I thought it would, and now has 10.04 installed - I like stability.
The GUI works and is responsive, Firefox scrolling is decent, flash works (p360), videos play OK - I use Totem and Mplayer, not VLC.

Intel has not provided any support worth mentioning, but the recent effort by Alan Cox, who's been working on an open source driver, looks promising in the long, ... long long run.

The two primary drivers to choose from are psb and EMGD.
Psb is old, no longer developed or maintained, but works well with 10.04 and supports hardware acceleration when using mplayer with vaapi, available through the PPA. EMGD is newer, and is available on 10.04 through 11.10, though performance is sluggish.
There is a messy wiki page with more info.

---

### Post by ATAQ on 2012-01-06
I managed to get the PSB driver installed under Debian 6, its working fairly decently and is well usable for her computer with what she uses it for, but it would wreck my head if I owned it, Then again when I buy a laptop or any thing computer wise, I generally only settle for nVidia. At least they support their products.

---

