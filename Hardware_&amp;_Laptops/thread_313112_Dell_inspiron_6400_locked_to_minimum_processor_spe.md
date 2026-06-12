---
title: "Dell inspiron 6400 locked to minimum processor speed"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by parkejr on 2006-12-05
Hi,

I've been running Edgy for some time on my Dell Inspiron 6400. I've installed i8kutils, and seem to be able to control fan speed effectively. I'm using the generic kernel at the moment, and while I haven't bothered to work out if it successful, I'm happy enough with the speed. But I have an issue with booting up:

If I boot the system up from cold (i.e. about 10-15 degrees C ambient temperature) it locks to the minimum processor speed at boot, and takes ages to come up to the log in window. The fan is also permanently on at maximum. I8kutils reports the temperature to be about 10 degrees all the time.

If I shutdown and restart, the system comes up successfully at a much faster speed, no fans, and temperature seems to be about 25 degrees. I can't reproduce the problem until I've switched off and the laptop has had a chance to cool to about 10 degrees again, but it happens everytime.

Has anyone else experienced this? the fan comes on at the grub menu, so I suspect the problem is in a BIOS setting, but it doesn't happen when I boot to windows, so perhaps windows is compensating for something that EDGY isn't?

Any suggestions on where to begin with this?

Thanks,

Jeff.

---

### Post by parkejr on 2006-12-06
anyone? I've reimaged with FC6 and the problem is gone, but I'd prefer an ubuntu solution...

---

