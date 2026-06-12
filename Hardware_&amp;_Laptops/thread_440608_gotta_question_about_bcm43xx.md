---
title: "gotta question about bcm43xx?"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by summey on 2007-05-11
ok the bcm43xx driver dosnt work only when i do 
sudo modprobe bcm43xx

then my wifi works but when i restart it dosnt work and i have to do the command over again each time any one have an  idea to just get this to work with out having to modprobe each time?

---

### Post by Rescue9 on 2007-05-12
Wow... yours works out of box!?!?! Count your blessings. I had to blacklist the bcm43xx driver and use ndiswrapper for the windoze one.

If it's as simple as modprobing the card... simply add bcm43xx to your /etc/modules (Think that is... I'm on windoze) file so that it gets loaded on boot.

---

