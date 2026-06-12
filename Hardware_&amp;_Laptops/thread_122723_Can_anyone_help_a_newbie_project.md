---
title: "Can anyone help a newbie project?"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by JesCed on 2006-01-28
Hi, all

I'm running ubuntu 5.10 on a Dell Inspiron 6000, and up to now everything seems to be working fine, especially for my needs. However, I am going to be giving a presentation soon and in preparation for this, I tried to view the presentation beforehand. On connecting the multimedia projector, however, I get a persistent "no signal" message. I know the problem is that the VGA output isn't enabled (the laptop dual boot into WinXP, and had the same issue there, but on enabling the output everything workeed OK), but I haven't been able to find just where I can actually enable the VGA in ubuntu. Can anyone give me a hand here?

---

### Post by inhetep on 2006-01-28
What type of grafic card do you have?
If it is an ati look for

```
 /usr/X11R6/bin/fireglcontrolpanel
```

There should be a similar thing for nvidia.


Also check if the modes in your xorg.conf are supported by the projector.

---

