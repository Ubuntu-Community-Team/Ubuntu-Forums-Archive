---
title: "Gateway E265M Laptop No boot with Fiesty Fawn"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by cwhill on 2007-06-27
OK so I have a nice new shiny Gateway 265M begging for an operating system other than Vista. I didn't even bother to fire up the stock install of windows on there as I have no intention of using it. So I drop my Fiesty Fawn CD in to start clean. Shortly after boot I get pimped by a "can't access tty: job control turned off" message. I tried starting in safe graphics mode same error. I also tried adding "noacpi noapic" as kernel options. At least here a get a bit further until I am just left staring a a blinking cursor with no error message.
I know there isn't much to go on here but does anyone have any thoughts??

---

### Post by cwhill on 2007-06-28
Interesting find. I can boot the laptop with 6.06 LTS CD fine. I working from the Live CD now. I may try and do the install with this CD then upgrade? Probably won't be that easy though. There must be others having similar errors with these laptops.

---

### Post by cwhill on 2007-06-29
I was able to resolve this problema s well as the next problem I was going to have but didn't realize it. This laptop had the ATI 2300 HD card in it. X will fail to start even after you get around the "Can't Access TTY" error. I was able to use the alternate installer and do a text based install. For other having this problem and if you have an ATI card with X failing to load see the link below. This all worked perfectly as outlined to do.

[http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/](http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/)

---

### Post by cwhill on 2007-06-29
I was able to resolve this problema s well as the next problem I was going to have but didn't realize it. This laptop had the ATI 2300 HD card in it. X will fail to start even after you get around the "Can't Access TTY" error. I was able to use the alternate installer and do a text based install. For other having this problem and if you have an ATI card with X failing to load see the link below. This all worked perfectly as outlined to do.

[http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/](http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/)

---

