---
title: "Anybody succeed installing ATI drivers on a MacBook Pro?"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by Nasiom on 2006-12-14
Hello World,

I've been trying and reading and trying and reading more to get the ATI drivers working in a MacBook Pro 15" (2Ghz with ATI Radeon Mobility X1600) with absolutely no luck at all. ](*,) 

I've followed instructions here and on the wiki.unbuntu.com/MacBookPro page. I get NO compilation error, everything seems OK... as soon as I reboot I get a serie of blue pixels accross the screen when it reaches about 95-98% of loading (horizontaly - right under the ubuntu progress bar) and then a flickering green one appears and that's it :-k 

If I boot in recovery mode and restore xorg.conf from the backup and reboot , everything is fine but of course I'm stuck at 1024x768 with no acceleration at all...

Looking at the xorg.conf file that was modify by the process doesn't reveal anything about the X1600. So I tried and added the strings manually as seen in another place - no luck! 

I've also gone and download the latest drivers from ati-amd and redone the whole exercise (compile-install-configure...) and still!

Has anybody succeeded in making this work?

I really need this to work.... please please

:confused:

---

### Post by Nasiom on 2006-12-15
OK persistance is everything.

:KS  Got IT...  When downloading the drivers from ati-amd site, make sure you download the Radeon Mobility X1600 drivers as opposed to the Radeon X1600 as per all the posts here are pointing to.

Now everything is fine but audio and built-in isight camera. (but this is secondary to me)

Cool triple boot machine now!

:-D

---

