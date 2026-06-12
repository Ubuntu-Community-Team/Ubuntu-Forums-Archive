---
title: "nvidia proprietary driver on dell inspiron 5150"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by mabster on 2006-01-08
I followed the instructions from here:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

At the point where the instructions say to restart X-Windows, the screen went black and I could hear my CPU fan going full-ball (until the computer eventually just switched off with an overheat warning on the next boot.

Anyone had this one before?

---

### Post by Thirsteh on 2006-01-08
Seems awkard, and shouldn't happen. Boot your computer and see if your card's fan is running at all, or if you even have one. If you don't or it's not running, I recommend purcashing another fan maybe? ;)

If you do have a fan and it's running properly, switch "nvidia" back to "nv" in xorg.conf if possible and try to run some hardware diagnostics of sorts if possible.

---

### Post by mo_x on 2006-01-08
What card do you have?

---

### Post by mabster on 2006-01-09
I switched back to the nv driver and everything runs as it was before.  What hardware diagonstics are there to run (I'm a newbie ; ) ?

I'm using a nvidia geforce go fx 5200.

---

### Post by mo_x on 2006-01-09
You could post /etc/X11/xorg.conf and /var/log/Xorg.0.log using the nvidia driver after the problem occured.

---

