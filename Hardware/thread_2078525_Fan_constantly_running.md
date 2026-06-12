---
title: "Fan constantly running"
date: 2012-10-31
forum: Hardware
---

### Post by evilbrent on 2012-10-31
I've noticed the fan constantly running on my AMD Athlon(tm) X4 620 Processor. I've tried to find out the temp using ```
lm-sensor
```, and from Hardware Sensors Monitor, but they both say "no sensors found".

I ran ```
sudo sensors-detect
``` and it does say 

> AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')

but then:

> Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

So now I've gone to that page and I see the driver that I want and I don't know what to do. How do I install [the driver]("http://khali.linux-fr.org/devel/misc/k10temp/")?

I'm guessing this is a hardware problem - and what I'm first going to do is pull the box out and open it up and see if it's full of fluff - but it's worrying me that I can't find the temp senesors, I'm thinking that maybe the fan is running constantly because the computer can't find the sensors either??

Any help would be appreciated.

---

### Post by 2F4U on 2012-10-31
> So now I've gone to that page and I see the driver that I want and I don't know what to do. How do I install [the driver]("http://khali.linux-fr.org/devel/misc/k10temp/")?

Maybe this helps:

[http://ubuntuforums.org/showthread.php?t=1287819](http://ubuntuforums.org/showthread.php?t=1287819)

---

### Post by evilbrent on 2012-10-31
> **2F4U said:**
> Maybe this helps:

[http://ubuntuforums.org/showthread.php?t=1287819](http://ubuntuforums.org/showthread.php?t=1287819)

Booyah.

That was EXACTLY what I was looking for.

Cheers!

---

