---
title: "dual monitor set up leads to &quot;safe graphics mode&quot; bumble."
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by Master-of-None on 2008-03-21
Alright. I attempted to set up a second monitor with my Laptop. It worked fine ***_ONCE_*** yet my laptop monitor was at reduced(640x320?) resolution. So I attempted to correct it. Now, my monitor doesn't output, and Ubuntu refuses to start up in anything but "Safe Graphics Mode."

How do I fix the "safe graphics mode" problem? and how do I get Ubuntu to make my laptop's monitor display in currect resolution later on?

---

### Post by teaker1s on 2008-03-23
if you have tried everything else
```
sudo dpkg-reconfigure xserver-xorg
``` in recovery mode and alter settings.

Have you checked that you are running a hz that both monitors can handle?
plus you haven't said what graphics card and driver you have.

---

