---
title: "Asus a6000 unable to install edgy"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by t.rei on 2006-11-10
Hi,
I have some trouble. I was going to install Ubuntu on my ASUS a6000 laptop. However, after booting the Xserver wont be anything but a blank screen. And the console is totaly bungled. Its all kinds of greenish and purplish dots.
Is there any guide I'm missing? Any hint, any clue?

Thx in advance

---

### Post by AlePetrucci on 2006-11-10
I had that problem too.
u need to start the live cd without the splash option (to do it press f6 to change the boot option). 
after the boot proces has completed u won't see anything but now u have access to a console (ctrl+alt+f2). change in xorg.conf the driver from ati to  vesa and restart gdm.

i hope u understood the process, my english is a bit confuse :)

---

### Post by t.rei on 2006-11-11
Ok, got it. I'm highly disappointed by this turn of things though. Dapper install was flawless. I had the whole beryl thing running smoothly and everything set up. Dist-upgrade after release and I am stuck in using winslow for now. :/

---

