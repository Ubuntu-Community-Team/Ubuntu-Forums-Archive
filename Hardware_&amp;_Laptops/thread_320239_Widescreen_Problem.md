---
title: "Widescreen Problem"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by sauyeeluo on 2006-12-17
I have been having a problem getting Xorg to play nicely with my new monitor. 

THe monitor is a SOYO 15.4" widscreen monitor. Video Adapter is MSI gefore4 MX. 

1280 x 800
83.5 mhz dot clock
83.5 hz vsync
49.7 khz hsync
-/+ synce polarity

Xorg only recognizes this monitor as 1280x768 despite any changes i have made to xorg.conf. 

the KDE gui (which i shouldn't rely on) lists the monitor as a generic flat screen of 1280x800, but is running it in 1280x768 mode.  inserting the proper modeline for this monitor did not solve the problem.

any suggestions?

---

### Post by pjman on 2006-12-18
I don't know if this will help you but....

I just installed Ubuntu on my Compaq nc6400 laptop that has a widescreen LCD. I had to install the 915resolution package in order to get 1280x800 resolution to work. It's talked about here: [http://hpwiki.cactii.net/hpwiki/NC6400](http://hpwiki.cactii.net/hpwiki/NC6400)

Again, I'm not sure if this applies to your SOYO monitor.

---

