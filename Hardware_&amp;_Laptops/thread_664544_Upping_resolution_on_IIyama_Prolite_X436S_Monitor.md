---
title: "Upping resolution on IIyama Prolite X436S Monitor"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by yawnster on 2008-01-11
Howdy guys,

I recently aquired an IIyama ProLite X436S monitor to replace an aging CRT, now the card I have is rather old, I am running Xubuntu gutsy, but it will go higher than 800x600.. I believe to 1280x1024.. And the screen will also as my brother used to use it at 1280x1024 I believe..

The card I have is listed as this from lspci...
> 01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

When I look in the xorg.conf file the resolution modes are listed but it is just not finding them.. When I use the new screen & graphics tool, there is not a driver listed for this model and the generic lcd settings seem not to take..

Anyone have any ideas?

Thanks, Alex Latchford.

---

### Post by taurus on 2008-01-11
What driver do you use for your graphic card?  Have you tried to install nvidia driver for it?  You can try reconfiguring your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

