---
title: "HP Pavillion XT963 Lock-Up Hard"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by mwheeler@pittstate.edu on 2005-06-28
Hello all. I've installed ubuntu on several computers and the hardware support out of the box is nothing less than astonishing. However, I tried to install it on one computer, a HP Pavillion XT963, and whenever the X-Server starts, the computer locks up and I have to hold down the power button for 10 secs to shut it off.

I've tried reinstalling, but that didn't seem to fix the problem.

If I boot into "recovery mode", I can get a console and poke around. I looked at the xorg config file, but nothing seemed out of the ordinary. I also tried doing a **dpkg-reconfigure xserver-xorg** , but I'm still having the same problem.

I believe it's using the i810 drivers. Anybody have any ideas?

---

### Post by sonny on 2005-06-28
Have you tried to start the x session while you're in recovery mode?

> code:
startx
I don't think that will help but you can give it a shot.

---

### Post by mwheeler@pittstate.edu on 2005-06-28
When I hit Ctrl-D to log out of the recovery session, it immediately tries to start a X session.. It locks up when that happens too.

---

