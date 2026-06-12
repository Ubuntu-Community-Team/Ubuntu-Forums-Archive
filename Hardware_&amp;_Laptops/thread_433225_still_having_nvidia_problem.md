---
title: "still having nvidia problem"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by Zyphrexi on 2007-05-04
when X starts, it loads
/lib/linux-restricted-modules/2.6.20-15-generic/nvidia

instead of
/usr/lib/xorg/modules/drivers/nvidia_drv.so

any ideas?

---

### Post by phidia on 2007-05-04
you could try opening /etc/default/linux-restricted-modules-common
and adding the modules you don't want to load to the line
Disabled_MODULES=""
Not sure if that's the best way but it might work.

---

### Post by Zyphrexi on 2007-05-08
it almost looks as if nv no longer exists. I tried loading that in my /etc/X11/xorg.conf to no avail just to check it out.

This nvidia thing is still confusing the hell out of me.

I've also thought about plugging in a script I wrote into rc.local, not sure how to do that yet though. Researching...

---

