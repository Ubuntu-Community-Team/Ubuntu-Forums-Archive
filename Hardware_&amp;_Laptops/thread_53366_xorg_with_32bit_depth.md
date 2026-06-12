---
title: "xorg with 32bit depth"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by rwabel on 2005-07-31
I'm wondering it it's possible to set up xorg to 32bit instead of 26 or 24bit. I'm using Nvidida driver from Ubuntu.
The problem is that gaming in 24bit is not working well, in 16bit it's working fine, but videos, images and also games look bad then.

---

### Post by nemnivus on 2005-07-31
24 Bit is what most games call 32bit.  The extra 8 bits comes from the alpha channel, so when you're in 24bit in X it's the equivalent of 32bit in Windows.

---

### Post by rwabel on 2005-07-31
[QUOTE=nemnivus]24 Bit is what most games call 32bit.  The extra 8 bits comes from the alpha channel, so when you're in 24bit in X it's the equivalent of 32bit in Windows.[/QUOTE]
 I've seen on some forums that people put 32 instead of 24. Well if that's not possible I've no luck! 24 slows than tremendous my FPS.

---

### Post by nemnivus on 2005-07-31
You're just running something that's too much for your video card then, it all depends on your setup.

---

### Post by rwabel on 2005-08-01
[QUOTE=nemnivus]You're just running something that's too much for your video card then, it all depends on your setup.[/QUOTE]
 can't be, I've a Nvidia 66600GT. Under WIndows it's working fine

---

### Post by heimo on 2005-08-01
Try running glxgears and compare the performance to others on this forum. Some drivers do accept 32 in configuration file, but it still doesn't make any difference to 24 as far as I know.

Maybe the Nvidia driver installation wasn't successfull? Do you have "nvidia" in the device->driver section of /etc/X11/xorg.conf? Check that in modules section you have glx, and glcore and dri are disabled (commented out).

---

### Post by rwabel on 2005-08-04
[QUOTE=heimo]Try running glxgears and compare the performance to others on this forum. Some drivers do accept 32 in configuration file, but it still doesn't make any difference to 24 as far as I know.

Maybe the Nvidia driver installation wasn't successfull? Do you have "nvidia" in the device->driver section of /etc/X11/xorg.conf? Check that in modules section you have glx, and glcore and dri are disabled (commented out).[/QUOTE]
 I do have the ubuntu nvidia drivers and have the nvidia stuff init. I thought glx should be enabled, glcore and dri must be disabled. Are you sure about disabling glx?

I was hoping that with 32 I would have similar FPS rate than with 16.

---

