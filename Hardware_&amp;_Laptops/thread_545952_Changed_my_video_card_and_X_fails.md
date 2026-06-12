---
title: "Changed my video card and X fails"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by mindtrick on 2007-09-08
I got rid of my troublesome ATI card and got a new Nvidia chipset card. I'm dual booting Ubuntu/XP. XP boots OK but Ubuntu fails to start X. 
What do I need to do?

---

### Post by callan79 on 2007-09-08
> **mindtrick said:**
> I got rid of my troublesome ATI card and got a new Nvidia chipset card. I'm dual booting Ubuntu/XP. XP boots OK but Ubuntu fails to start X. 
What do I need to do?

Howdy,

I was hoping to broaden my knowlesge by reading this threat, but looks like I'm the first to respond.

I guess first thing I'd do is attempt to reconfigure X to use the correct nvidia driver. I gather you can get into a terminal, so try this :

```
sudo dpkg-reconfigure xserver-xorg
```

In the Video section, just choose NV or NVIDIA as the driver and see what happens. If all goes bad, do it again and choose the VESA driver, but I'd say that NVIDIA should be fine.

Good luck!
Callan

---

### Post by mindtrick on 2007-09-08
Thank you mate! That solved it.

---

