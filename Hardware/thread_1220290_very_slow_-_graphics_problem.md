---
title: "very slow - graphics problem?"
date: 2009-07-22
forum: Hardware
---

### Post by gatorbrit on 2009-07-22
My system is getting slower and slower.  Firefox crawls.   It usually gets worse after I have been going for a while.  A reboot helps a bit.   Other apps are slow to load.  For example nautilus is very slow to refresh.

I wonder if it is my video set up.  I am running the following video card - I got this info from doing..

```
glxgears -info
```


```

GL_RENDERER   = GeForce4 MX 440 with AGP8X/PCI/SSE2
GL_VERSION    = 1.5.8 NVIDIA 96.43.10
GL_VENDOR     = NVIDIA Corporation

```

When running glxgears, I get about 700 FPS which seems low.

I am also running dual monitors.

Typing ```
top
``` reveals no hidden processes sucking up CPU time.


ANy suggestions?

---

### Post by dlmarti on 2009-07-22
If you cpu is not being throttled, and top doesn't show anything eating the cpu cycles, and free shows plenty of memory, then its just perception.

---

### Post by dlmarti on 2009-07-22
btw : dmidecode | grep "Current\ Speed" | head -n 1

will show the current speed of your processor.

---

### Post by gatorbrit on 2009-07-22
> **dlmarti said:**
> If you cpu is not being throttled, and top doesn't show anything eating the cpu cycles, and free shows plenty of memory, then its just perception.

Its not perception - moving from one app to another is slower and moving from one tab in firefox to another is also slow.   

I was wondering whether my graphics chip memory was choking.

---

### Post by gatorbrit on 2009-07-22
> **dlmarti said:**
> btw : dmidecode | grep "Current\ Speed" | head -n 1

will show the current speed of your processor.

I'll check this - thks.

---

### Post by gatorbrit on 2009-07-23
OK, one thing I did was reduce the resolution to 16 from 24.  That seemed to help somewhat.

---

