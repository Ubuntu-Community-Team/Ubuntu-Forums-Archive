---
title: "Increase screen refresh rate?"
date: 2008-12-29
forum: Hardware
---

### Post by Hydrothrax on 2008-12-29
Hello,

I run Ubuntu 8.10 64-bit system on a Toshiba Satellite A215-S5837, with an ATI Raedon x1200 graphics card. I would like to increase the screen refresh rate above 60Hz, but it won't let me. How can I do this? And with my system, is it even possible?

---

### Post by Maddman on 2008-12-29
You need to edit the /etc/X11/xorg.conf file to do this.  [Here's](http://www.linuxforums.org/forum/linux-desktop-x-windows/40987-xorg-how-set-refresh-rate-100hz.html) an example of how to do this.

Be careful and make sure you know what you're doing!  If you set the refresh rate to one your monitor can't handle, you could damage your monitor.  If the other settings aren't right, your display may not work.  Be sure to save your existing xorg.conf file so you can put it back if it doesn't work.

You'll have to do a little research to figure out the settings you need, but xorg.conf is where the changes are made.

---

