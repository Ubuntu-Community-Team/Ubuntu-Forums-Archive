---
title: "Config for XServer for Pavilion Laptop"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by Foxfyre on 2005-10-26
I installed Ubuntu 5.10 for the 32 bit processor on the laptop last night, but it didn't configure the XServer properly and I'm checking to see if anyone has any information on how I should go about configuring it for the HP Pavilion ze2000 laptop.

Thanks

---

### Post by xaque on 2005-11-02
I had the same problem. I think the solution is to install the fglrx driver. I'll try it tonight when I get home and let you know how it turned out.

---

### Post by xaque on 2005-11-03
Okay, well one thing I can tell you is *do not use the fglrx driver!* Now when I try and start X, the screen goes black and becomes completely unresponsive. I think a temporary solution is to run dpkg-reconfigure xserver-xorg and choose the vesa driver, that way you can at least get into X. Next on my list of things to try is installing the fglrx driver from ATI's website. Maybe that version will fix the problem.

---

### Post by drake on 2006-02-10
nm

---

