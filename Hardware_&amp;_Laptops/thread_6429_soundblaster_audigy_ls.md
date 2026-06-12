---
title: "soundblaster audigy ls"
date: 2004-11-28
forum: Hardware &amp; Laptops
---

### Post by sparky on 2004-11-28
Hi,
I have recently installed warty, and everything works well, except my soundcard, a soundblaster audigy ls.  The device manager recognizes that it is there, but that is all.  I attempted to run alsaconf as root, but it responds "command not found."  Is there a driver that I should try to install?

I would be grateful for any suggestions.

Thanks,
Sparky

---

### Post by FLeiXiuS on 2004-11-28
I would check your sound mixers in gnome before hand.  It may alread work, and hte alsaconf command may not be valid.  Plenty of possabilities...

---

### Post by sebast on 2004-11-28
[QUOTE=sparky]Hi,
I have recently installed warty, and everything works well, except my soundcard, a soundblaster audigy ls.  The device manager recognizes that it is there, but that is all.  I attempted to run alsaconf as root, but it responds "command not found."  Is there a driver that I should try to install?

I would be grateful for any suggestions.

Thanks,
Sparky[/QUOTE]

I have the same problem,

The problem is that the version of Alsa that comes with Warty (1.0.5a) doesn't have the driver for the Audigy LS. Alsa started to have it in version 1.0.6 (Alsa is now at 1.0.7).

Now, my problem is on installing a newer version of Alsa, for that see my thread at:
[http://ubuntuforums.org/showthread.php?t=6101](http://ubuntuforums.org/showthread.php?t=6101)

---

