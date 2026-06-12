---
title: "Changed GPU's, don't have a GUI (I do have a terminal)"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by TROGDOR42 on 2006-01-15
I had this crap ATi graphics card and I bought a sick new nVidia for better Linux support, but now whenever I boot into Ubuntu I get a load of Xorg errors and it sends me to a command line.  I hear you can fix anything with the Linux terminal, so can anybody help?

P.S. I can't reinstall Ubuntu, my CD drive's busted.

---

### Post by nvez on 2006-01-15
[QUOTE=TROGDOR42][...] I get a load of Xorg errors and it sends me to a command line.  I hear you can fix anything with the Linux terminal, so can anybody help? [...][/QUOTE]

Well, for the record, simply saying that It doesn't work doesn't help us, maybe if you did tell us what are the errors, that would help.

---

### Post by proxess on 2006-01-15
I suggest you try:
 sudo apt-get install nvidia-glx

then:
 sudo dpkg-reconfigure xserver-xorg and configure it for the nVidia drivers.

---

