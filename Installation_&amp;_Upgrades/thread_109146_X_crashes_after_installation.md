---
title: "X crashes after installation"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by conai on 2005-12-27
I've installed Ubuntu 5.10 on my Asus A6B00R laptop, I chose the default installation. After installing it prompted me that X could not be loaded due to a problem in the configuration. Can you pleas help me?

---

### Post by Imexius on 2005-12-27
There has been several replies to this type of problem. try adding Option    "noaccel" to your /etc/X11/xorg.conf under BusID. use sudo pico /etc/X11/xorg.conf to access your xorg.conf

---

### Post by kingsidy on 2005-12-27
can you specify which graphic card is in your computer?

---

### Post by conai on 2005-12-27
tnx! ill try it.. sorry I new to this forum...

---

### Post by conai on 2005-12-27
ATI Radeon 200M

---

### Post by conai on 2005-12-27
the Option "noaccel" works!! Gee Tnx! But do u have time to explain how this works?? If not well thanks a lot..

---

