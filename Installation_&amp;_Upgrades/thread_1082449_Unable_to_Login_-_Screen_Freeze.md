---
title: "Unable to Login - Screen Freeze"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by happy_pig on 2009-02-27
Just upgraded to Jaunty.
With system determined parameters I am now unable to get past login screen. I start typing my login name and the screen freezes. Also if I select the sessions it gives a white box with nothing inside it. Have to use power key to turn computer off.

I have tried adding Driver ¨vesa" to the xorg.conf and this allows me to login to GDM but then the screen is offset way to the left.

I am guessing it is something to do with xorg but am stumped how to proceed.
Thanks in advance

---

### Post by Søren Holm on 2009-03-01
Sometimes I have the same problem. It is only related to new used with a clean home directory. If I start Xorg manually, and also start startkde manually it is possible to login.

---

