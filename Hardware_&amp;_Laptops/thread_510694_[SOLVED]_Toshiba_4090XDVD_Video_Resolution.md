---
title: "[SOLVED] Toshiba 4090XDVD Video Resolution"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by 2thmdathome on 2007-07-26
Toshiba Satellite 4090XDVD, Celeron 400, Ubuntu 7.04 (Feisty Fawn).  Video is Cyber 9525 by Trident Microsystems.  The only display options are 800x600  and 640x480.  This does not fill the screen.  The manual says this card is capable of 1040x768. How do I reset this??

---

### Post by 2thmdathome on 2007-07-29
I was able to fix.  Found a similar post for the same video card on Toshiba 4100.  My only error was not using "save  as" after editing the file. Otherwise post was good.
Thanks problem resolved

---

### Post by Arnau2008 on 2008-07-14
I have Xubuntu 8.04 and had the same Toshiba 4090XDVD video resolution and screen size problem.
Could not find the 4100 post mentioned here, but after a while (2 hours!) I found the solution at the following link:

[http://ubuntuforums.org/showthread.php?t=59438](http://ubuntuforums.org/showthread.php?t=59438)

(Change DefaultDepth from 24 to 16 in /etc/X11/xorg.conf. Then enter ctrl-alt-backspace to reboot X)

---

