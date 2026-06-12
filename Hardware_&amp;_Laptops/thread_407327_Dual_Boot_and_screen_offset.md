---
title: "Dual Boot and screen offset"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by crisponions on 2007-04-12
I am dual booting XP and Ubuntu and am having problems with the screen being in the right position after I reboot.  It is offset about 6 inches when I change OS's.  Its a Dell LCD so I use the auto adjust setting on the monitor and it puts the screen back correctly, but its kind of annoying.  I am using the proprietary NVidia drivers on Ubuntu 6.10.  The LCD is set to use 1680x1050 at 60hz.  Is there something I can tweak in my xorg.conf to fix this?

Thanks!

---

### Post by Can+~ on 2007-10-16
This topic is pretty old I know.. but I have the same question.

My screen LG Flatron L1752S, 1280x1024 needed manual resolution adjusting in xorg.conf (Feisty Fawn 100% updated) for the screen resolution. But there is always a small blackspace. Luckily, the screen has a "Auto adjust" button to fix this issue, but when I switch to windows, I have to adjust it again.

It's not a big deal, but it should be nice to have both offsets correctly configured. What should I do? Edit the xorg.conf and add something like "offset"?

---

