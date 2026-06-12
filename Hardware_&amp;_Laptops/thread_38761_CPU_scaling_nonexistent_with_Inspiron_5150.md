---
title: "CPU scaling nonexistent with Inspiron 5150"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by Emrysk on 2005-06-01
I am running Hoary Hedgehog on my Dell Inspiron 5150, and the other day I noticed that /sys/devices/system/cpu contains two directories "cpu0" and "cpu1," but both are empty.  I'm going to be travelling soon, so this isn't good news.  

When powernowd starts, I get the following...

```
emrys@cloudy:/sys/devices/system/cpu$ sudo /etc/init.d/powernowd start
Password:
This processor "Mobile Intel(R) Pentium(R) 4 CPU 3.20GHz" is known _not_ to support power-saving.
 * Starting powernowd...
 * CPU frequency scaling not supported                                   [ ok ]
```

That's not good.  CPU scaling should be supported.  According to [http://www.finnie.org/linux-dell-5150/](http://www.finnie.org/linux-dell-5150/), it's supported with the 2.4 kernel in Gentoo.  (Though he doesn't specify which Gentoo kernel he uses.)

Oh, and CPU *throttling* works just fine.  Any ideas?

---

