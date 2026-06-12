---
title: "detect new graphics card?"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by cameran on 2007-11-26
hello,

i purchased a new video card for my girlfriend and it will be arriving this week.  she's getting an nvidia 7800GS, upgrading from a 7600GS.  how do i get my xorg to "redetect" or reconfigure to fully utilize the new card when i install it?  she's already using the restricted nvidia drivers and this new card is primarily for gaming.

thanks in advance,

cameran

---

### Post by PmDematagoda on 2007-11-26
Since there isn't much of an upgrade on the video card, I do not think that reconfiguration is necessary. But incase you do:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

should suffice.

---

### Post by cameran on 2007-11-26
thank you!!

ok, so that command will essentially "reconfigure" xorg to take advantage of the new card, correct?

also, in the event that i have a major graphics card update myself sometime next year, would i use the same command to reconfigure xorg when there's a major graphics card upgrade?

thanks in advance,

cameran

---

### Post by PmDematagoda on 2007-11-26
That command is useful when you only changed the VGA card a little, not in terms of changing brands such as from ATi to Nvidia or a big jump from say a 6200 to a 8800. If you made a major change in the video card then you will have to completely reconfigure the xserver using:-

```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by cameran on 2007-11-26
ok - thanks a lot for the help!  i will try it out this weekend and hopefully everything will work out fine.

thanks again, i really appreciate the help (and i know my girlfriend will too)!

cameran

---

