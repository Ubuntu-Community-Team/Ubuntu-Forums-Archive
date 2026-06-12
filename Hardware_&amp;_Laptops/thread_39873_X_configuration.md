---
title: "X configuration"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by jmelton on 2005-06-06
Hi,

I've just installed Ubuntu and so far all the software I've tried seems to work.  One big problem, though: X is only using about 1/3 of the screen.  I tried re-setting the screen resolution, but I was only given one option: 640x480 (presumably the setting that it's on).  Where is the X configuration file located, and what should I do to it (assuming that changing that file is what I need to do)?  I don't see anything that looks like the right file anywhere in the /etc/X11 directory.  Thanks!  I'm running a Dell Inspiron 1100 laptop, which uses an Intel 82845 display card and the i810 driver; I think the screen is 14 inches.

Jeff Melton

---

### Post by der_kaiser on 2005-06-06
Try editing this file : /etc/X11/xorg.conf

There is a Screen section on it. Try to change your resolution there.

Good luck!

---

### Post by jmelton on 2005-06-06
[QUOTE=der_kaiser]Try editing this file : /etc/X11/xorg.conf

There is a Screen section on it. Try to change your resolution there.

Good luck![/QUOTE]
 I did succeed in finding the file right after I posted the message, but when I got rid of everything except 1024x768, it still displayed the same small screen and still gave me only the choice of 640x480!  Maybe the problem is with something other than the X configuration file, but I'm not sure what.  Any ideas would be enormously appreciated!

---

### Post by crane on 2005-06-06
Check and make sure your monitor settings are correct in xorg.cong
(HorzSync and VertSync)

Alot of time, these rates are not set to monitor specs.

---

### Post by jmelton on 2005-06-06
Yeah, that's exactly what the problem was!  Thanks.  Very strange that dexconf would just leave that information out of the configuration file it set up.


[QUOTE=crane]Check and make sure your monitor settings are correct in xorg.cong
(HorzSync and VertSync)

Alot of time, these rates are not set to monitor specs.[/QUOTE]

---

### Post by andlinux21 on 2005-06-06
***[FONT=Comic Sans MS]During the install I picked the resolutions I wanted and then did sudo gedit and found the config file for X11 and changed the depth from 24 to 16 and it worked for me.[/FONT]***

---

