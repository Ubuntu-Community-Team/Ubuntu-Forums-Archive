---
title: "HD spindown even after workaround"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by NSDragon on 2007-11-04
Hello, I'm on Gutsy and I'm one of those people that was affected by the HD spindown "bug". I'm still relatively new to Linux, having switched only about two months ago.

I followed the various workarounds (with -B 254 and -S either 0 or 60) in order to prevent the HD from spinning down so often, and at first glance they've worked nicely.

My problem, however, is that apparently after some time (not sure how long exactly, but it's no less than 20 hours or so) the spindowns return without me doing anything to change the hdparm settings, and when trying to reset them with hdparm, it doesn't work and the frequent spindowns remain. These happen every 30 seconds or so.

This bothers me because as far as I can tell, after some time, my hdparm settings and workarounds are ignored,  thus my HD's Load cycle keeps going up (it's up to about 402,500, and at least I'd like the HD to last until I can get a replacement) and only after rebooting the system goes back to normal.

Any insight on this? I'm using an Inspiron 5160, if this is of any relevance.

---

### Post by SaihtamRent on 2007-11-04
What is the brand of your hard drive ?

If it is an hitachi one, you may want to use 

[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

for changing the APM setting directly on the hard drive :
Download  Feature Tool iso Image, burn it, boot with it, 
change the APM setting (see the PDF help document on the above page)

It worked nicely for me. 

If it is'nt an hitachi, go to [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
I don't know what it's worth, you may want to give it a try. 

Cheers.

---

