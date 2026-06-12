---
title: "Video flickering above 70Hz"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by amklinux on 2006-04-27
Hi.

I'm being puzzled by a wicked problem: my video screen flickers (mostly on left upper and right lower corners) above 70Hz, in any resolution. My machine is a Dell Optiplex GX240, with an ATI Rage Pro 128 video card. I tried two different  17" monitor models: Sony E200 and Samsung Syncmaster 753DFX. I tried to set up the frequencies on xorg.conf, but it really didn't help.

Thanks for any help.

amklinux

---

### Post by taurus on 2006-04-27
Make sure you have the right horizontal and vertical refreshing rates in /etc/X11/xorg.conf!

---

### Post by amklinux on 2006-04-28
Yeah, I did that for both monitors: got the Horiz/Vert frequency in the web and inserted them in xorg.conf. But it didn't help anyway. But thanks for you help.

amklinux

---

