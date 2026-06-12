---
title: "nVidia 7900GS and drivers"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by Terracotta on 2007-04-22
Hye,
Recently I changed my videocard (a 6800) which worked perfectly in (k)ubuntu with the official nvidia drivers (the one in the repos and the one from the nvidia site), the new one is a 7900GS and every time I install the drivers in the same way as I did for the 6800 the screen just goes blank when I enable it in xorg.conf. When the driver is set back to "nv" things work, well 2D things do. Does anyone know how to solve it, or should I post a bug report at nvidia's site? (they claim that this chip is supported).

---

### Post by archerzz on 2007-04-22
> **Terracotta said:**
> Hye,
Recently I changed my videocard (a 6800) which worked perfectly in (k)ubuntu with the official nvidia drivers (the one in the repos and the one from the nvidia site), the new one is a 7900GS and every time I install the drivers in the same way as I did for the 6800 the screen just goes blank when I enable it in xorg.conf. When the driver is set back to "nv" things work, well 2D things do. Does anyone know how to solve it, or should I post a bug report at nvidia's site? (they claim that this chip is supported).

You'd better post the error log here. There could be many reasons to cause the screen blank.:)

---

### Post by Terracotta on 2007-04-22
> **archerzz said:**
> You'd better post the error log here. There could be many reasons to cause the screen blank.:)
where can I find the error log? when i do: sudo kdm, the screen goes blank, but no error message pops up. I then can do: sudo killall kdm and change the xorg.conf file and everything's fine again.

---

### Post by dreadlord_chris on 2007-04-22
> **Terracotta said:**
> where can I find the error log?

/var/log/Xorg.0.log

---

### Post by fwojciec on 2007-04-22
nvidia-glx-new works fine with this card on Feisty, though I had to do dpkg-reconfigure xserver-xorg when I switched from the older driver.  The Linux support for this card seems to be less than perfect, for some reason, but I've always been able to get it to work in the end...

---

