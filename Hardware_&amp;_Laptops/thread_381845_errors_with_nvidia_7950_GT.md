---
title: "errors with nvidia 7950 GT"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by immerohnegott on 2007-03-11
OK, i've been running my desktop on an ATi X1600 PRO and decided it didn't quite have enough juice (plus I was tired of ATi's shoddy linux support).   I just bought and installed a BFG-manufactured Nvidia 7950 GT card, totally forgetting to reset my xorg.conf beforehand.
Went into recovery mode, reconfigured xorg { $ dpkg-reconfigure -phigh xserver-xorg } and set the card to run vesa (it isn't recognized by xorg automatically, just says generic video card).

GDM runs ok under vesa, but I like to have hardware acceleration.   Went to install the nvidia driver from their site, and was greeted with an error stating I can't run the install while running X.

Ok. Rebooted into recovery terminal again, ran the install, and upon reboot my X server isn't working.

Bleh.   

Should also mention that I'm running in 64-bit..

Help, anyone?


PS, card is kosher. Works beautifully under WinXP.

---

