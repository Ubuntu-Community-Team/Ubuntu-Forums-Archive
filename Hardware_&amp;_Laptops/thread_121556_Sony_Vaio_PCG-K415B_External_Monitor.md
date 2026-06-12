---
title: "Sony Vaio PCG-K415B External Monitor"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by edal on 2006-01-25
Anybody know how to use an external monitor with this laptop? None of my function keys work but any solution including file hacks would be welcome.

Ed Almos

---

### Post by stangbang on 2006-01-25
This has a ATI graphics card in it correct? I would try installing the xorg-driver-fglrx and fglrx-control packages. I am not sure if it supports the video card you have, but it may still work. Also you will need to edit your xorg.conf file so that it uses the fglrx driver for video.

---

