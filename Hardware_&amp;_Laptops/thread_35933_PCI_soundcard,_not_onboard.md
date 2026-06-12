---
title: "PCI soundcard, not onboard"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by donkey on 2005-05-20
I just freshly installed Hoary.  Ubuntu picked up my nforce2 onboard sound instead of my soundcard.  [This trick](http://ubuntuforums.org/showthread.php?t=27186&highlight=install+soundcard) allows me to hear sound, but alsamixer still uses the onboard.  How do I make alsa switch to my other sound card? Thanks.

---

### Post by stevenyu on 2005-05-21
I found alsa soundtime will have the issue of not using the PCI soundcard when you have the on board enable, try disable the on board sound through BIOS setting if you are not going to use it anyway.

The other wasy is use the alsamixer and disable the on board sound and force the alsa to use the PCI soundcard :???:

---

