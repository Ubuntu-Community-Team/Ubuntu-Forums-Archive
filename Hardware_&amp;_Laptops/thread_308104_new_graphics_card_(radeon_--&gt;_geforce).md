---
title: "new graphics card (radeon --&gt; geforce)"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by muszek on 2006-11-27
Hi,

I finally have an opportunity to ditch ATI (my girlfriend got a laptop and doesn't need her desktop anymore, so I took her graphics card...).  Anyways, right now I have Radeon 9000 Pro and fglrx drivers from repositories.  I don't really know what this new card is... I just checked my computer --> hardware manager (sadly, she needs AutoCAD and has to stay on Windows) and it said "NVIDIA GeForce MX/MX 400" in the description field.

Is there anything special that I have to do before I switching cards and installing nvidia drivers?

Should I worry about anything and anticipate some problems?

Thanks in advance for your answers.

---

### Post by taurus on 2006-11-27
X probably won't start now but you can reconfigure it with

```
sudo dpkg-reconfigure xserver-xorg
```
And once you get X up and running again, install a nvidia driver for it.

---

