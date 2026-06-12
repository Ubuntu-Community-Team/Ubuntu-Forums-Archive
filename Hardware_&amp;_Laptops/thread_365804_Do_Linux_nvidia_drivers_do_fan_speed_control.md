---
title: "Do Linux nvidia drivers do fan speed control?"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by CaptSaltyJack on 2007-02-20
Let me explain briefly.  In WinXP, with the nvidia drivers, there's fan control.  By default, out of the box, my eVGA 7900GT card's fan blows at full speed (noisy).  So when I'm booting up and I'm in the BIOS.. it's at full speed and loud.  Once Windows loads up (and the drivers kick in), the fan goes almost completely silent.  It stays that way until I load up something 3D intensive.. basically it runs the fan as needed.

Do the Linux nvidia drivers do this?  I really do need to know, because I'd like to upgrade to maybe a 6600 card... but if that fan is going to be blowing at full speed the whole time, I'm not interested.

Thanks!

---

### Post by aidanr on 2007-02-20
i'm 99% sure my 6800 does this (don't want to reboot right now to check)
by the way, wouldn't a 6600 be a downgrade :-s ?

edit:// or of course it could be for another machine :roll:

---

### Post by Magnes on 2007-02-20
CaptSaltyJack, maybe the fan speed is regulated automaticly (by the graphic card itself - not need for drivers to do it) by the GPU core temperature? It would be wiser.

---

### Post by Rotarychainsaw on 2007-02-20
Yes, the nvidia driver slows the fan down.

---

### Post by CaptSaltyJack on 2007-02-20
Nope Magnes.. it's software controlled by the drivers for sure.  Because whenever I'm not in Windows (like in the BIOS), the fan is running full speed.

Oh and sorry I wasn';t clear.. the 7900GT is in my Windows box, for gaming.  My current Linux box has a 6200LE (bleh).  But that might be good enough.. we'll see.  It sucks to have to exit Beryl before running OpenGL games because Beryl hogs all the GPU time.  I think a more powerful 3D card would fix that.

BTW, thanks for confirming this for me!

---

### Post by JackTrust on 2008-06-22
I'm going to give this a shot.  Sounds promising.

[http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)

---

