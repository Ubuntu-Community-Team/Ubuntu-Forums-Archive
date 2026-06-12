---
title: "3D Accel on an intel vid card"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by tylersontag on 2007-01-11
I was installing beryl on my computer, and had a bit of trouble.   For some reason sudo wasn't pulling enough weight to access all the libraries, but when i upgraded myself to a superuser with sudo su, i got beryl installed fine.

Anyway, in my quest to figure out why i couldn't install beryl, i thought my video driver might have been out of date an thus causing the problem (with the installation i know, was prolly not the best place to be looking) and in the process i think i might have installed an ATI type driver.  specifically xorg-driver-fglrx.   

the reason why i think this is that i know when i first ran into trouble installing beryl i ran

```
glxinfo | grep direct
```

it returned: direct rendering: Yes.

but now, after i finally got it installed and it crashes on startup, that same line returns No.

im pretty sure 3d acceleration being off is what makes beryl crash my desktop.  is there anyway to hardcode./brute force direct rendering back on? or any other helpfull tips that could be passed my way?

---

