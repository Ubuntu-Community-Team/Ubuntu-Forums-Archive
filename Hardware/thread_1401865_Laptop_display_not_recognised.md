---
title: "Laptop display not recognised"
date: 2010-02-08
forum: Hardware
---

### Post by semperlinux on 2010-02-08
Hi Forum,

Hardware - Acer Aspire 7740G Laptop with 17.3" 16:9 LCD display.
OS - Ubuntu 9.10

When I check in System/Preferences/Display, the picture of the display has the word 'UNKNOWN' on it.

Is there some way I can set Ubuntu to recognise this as a Laptop LCD ?

Many thanks
semperlinux

---

### Post by Cabs21 on 2010-02-08
your graphics card driver might not be up to date to handle your display and just names it unknown.  Did you try configuring or detecting displays?

---

### Post by semperlinux on 2010-02-08
Thanks for the reply Cabs21.

I have a thread running on the graphics card problem at 
[http://ubuntuforums.org/showthread.php?t=1400863](http://ubuntuforums.org/showthread.php?t=1400863).

Although they may seem to be related, I think display detection and graphics adapter detection are separate processes in Ubuntu boot up.

There must be some way of configuring the display / monitor type but I can't find it in Ubuntu (9.10).

---

### Post by pi/roman on 2010-02-08
The display adapter and monitor can both be configured through xorg.conf.  I made a guide on it [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8795200")

---

### Post by semperlinux on 2010-02-08
Thanks for the reply pi/roman

Problem is, I have very little info about the graphics card or the display to start making a new xorg.conf file.

The card is so new AMD don't have it on their website.

Your guide looks pretty useful - good chance I'll end up using it !

---

