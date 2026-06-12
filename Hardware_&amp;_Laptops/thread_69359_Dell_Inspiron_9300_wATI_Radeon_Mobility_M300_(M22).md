---
title: "Dell Inspiron 9300 w/ATI Radeon Mobility M300 (M22)"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by ph8 on 2005-09-26
Hi there,

I know this has been asked many times before but many of the threads are old.

I have a Dell Inspiron 9300 w/ATI Radeon Mobility M300 (M22) graphics card.

I found a guide on the wiki about enabling my hardware acceleration so i've apt-got the following:

xorg-driver-fglrx - Video driver for ATI graphics accelerators
xorg-driver-fglrx-dev - Video driver for ATI graphics accelerators (devel files)
fglrx-control - Control panel for the ATI graphics accelerators

I've then edited my xorg.conf and changed the graphics device driver to "fglrx"

I've noticed no difference in performance, the laptop still can't handle the most elementary of openGL screensavers

My worry is that the card is to new, fglrx-control shows card type as 'unknown' (even though it is right in xorg.conf) - if it is unknown is there no way anyone can think of of getting it to work? It works perfectly with windows </bitterness>

I really really need some help with this if someone would be so kind, please don't link to other threads unless you KNOW they will help me - as i've said - i've asked a lot and received lots of wrong answers :D

Hopefully this thread will be the last I have to post with this question -  Hope so!!! :cool: 


Henri

---

### Post by mlomker on 2005-09-26
Your card is not supported by the fglrx driver--it is about one generation too old.

There's an [open-source project]("http://dri.freedesktop.org/wiki/FrontPage") that has a driver for the card but it has to be compiled/installed.

---

### Post by ph8 on 2005-09-27
The card's too old?! it should be the latest..

---

### Post by ph8 on 2005-09-27
Correction, it turns out I have an X300 and it was detected incorrectly

---

### Post by mlomker on 2005-09-27
[QUOTE=ph8]The card's too old?! it should be the latest..[/QUOTE]

Perhaps it's the latest for your model from Dell, but it is not the latest ATI mobile chipset.  Dell is a conservative company and goes with older cards.  If you want the latest gear then you usually have to pay about 30% more and go with a system builder (aka white box, or gamer laptop).

My machine has the latest for amd64, which is the mobility 9700 Pro.  The latest on Intel boxes is now the pci-express-based x300.

Here's the [supported card]("http://www2.ati.com/drivers/linux/linux_8.16.20.html") list for fglrx.

---

### Post by ph8 on 2005-09-27
[QUOTE=ph8]Correction, it turns out I have an X300 and it was detected incorrectly[/QUOTE]

And it appears, the linux proprietary drivers support this (thanks for linkage) - i'll let you know how it works out

---

### Post by mlomker on 2005-09-27
I wrote a [how-to]("http://www.ubuntuforums.org/showthread.php?t=65276") as well.  If you are running Breezy the included drivers should work.  The drivers that came with Hoary are older than your card, so all bets are off on that.

---

### Post by ph8 on 2005-09-27
Can i dist upgrade to breezy now or is it well beyond desktop-usable at the moment?

---

### Post by mlomker on 2005-09-27
[QUOTE=ph8]Can i dist upgrade to breezy now or is it well beyond desktop-usable at the moment?[/QUOTE]

That's open to debate.  I tried it a few weeks ago and went back.  dist-upgrades generally fail because certain /etc files are incompatible and the dist-upgrade won't overwrite them (xorg.conf being a prime offender).  You could get it going but if you use your machine for work...

---

### Post by ph8 on 2005-09-27
I don't yet - i will do in a couple of weeks so it's probably best to do it now, i'll do that then try your howto,

thanks

---

