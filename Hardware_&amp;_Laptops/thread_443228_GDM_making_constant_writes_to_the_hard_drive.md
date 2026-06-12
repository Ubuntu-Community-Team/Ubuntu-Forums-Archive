---
title: "GDM making constant writes to the hard drive?"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Megatog615 on 2007-05-14
I have settings for hdparm to spin down the hard drive to save power for my laptop. Recently I noticed GDM is trying to make writes to the hard drive almost 5 times a minute.

I figured it was GDM since I ran htop to figure out if a process was changing from "sleep" to "running", at the same time the hard drive was spinning up to make a write. It turns out it was this process:
```
/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
```

---

### Post by Megatog615 on 2007-05-16
*bump*

---

### Post by Megatog615 on 2007-05-17
*BUMP* again...

---

