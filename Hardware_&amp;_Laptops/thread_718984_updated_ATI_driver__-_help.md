---
title: "updated ATI driver  - help"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by phoenix5002 on 2008-03-08
I'm getting some wierd results.

With the driver I originally had the one Ubuntu gave me upon install had 3d acceleration, I found this by typing:
**glxinfo | grep rendering**
output:
***direct rendering: Yes***

and when I ran glxgears it ran the program nice and smoothly and I would get about 280FPS.

So, then I updated my video card ("Radeon IGP 345M", laptop) and now when I check for direct rendering it says No.  But the wierd thing is when I run glxgears It runs sooooo slow, it looks like a slide show, but the wierd part is that I get an even higher frame rate than the first one, I get like 300FPS, but it sure as hell doesn't look like 300FPS.

anyway, any ideas how to get direct rendering with the new driver?

---

