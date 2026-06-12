---
title: "Flash problems in Firefox3.5 after upgrade to Karmic"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by alipangea on 2009-10-30
Hi,

Ubuntu Karmic x86_64, Firefox 3.5

after upgrading to Karmic, flash works only the first time I start Firefox. Upon restarting all I get is a white box.

I can get it to work again by 

* purging firefox-3.5
* removing ~/.mozilla 
* removing /etc/firefox*
* re-installing the firefox-3.5 package
* copying libflashplayer.so to ~/.mozilla/plugins, downloaded from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Edit: I've also tried with the firefox-3.0 package, with the same results. This time I downloaded flash 32-bit and installed it with dpkg --force-architecture.
Edit: Flash works fine in Opera

I'd be very grateful for any ideas

Thanks

Philip

---

### Post by alipangea on 2009-11-06
bump

---

