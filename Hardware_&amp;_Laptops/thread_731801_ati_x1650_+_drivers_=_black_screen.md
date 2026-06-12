---
title: "ati x1650 + drivers = black screen"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by pzdc on 2008-03-22
installed ubuntu 7.10 today
video card is ati x1650 agp

after installation there was a popup saying "your hardware can perform faster" or smt,
clicked on it, installed drivers, rebooted system and all I can see is black screen :(

I can see ubuntu logo during the booting, but thats it :(

tried to choose recovery option and it loaded up with console.

may somebody direct me of how to solve this?

---

### Post by jan quark on 2008-03-23
try to boot into recovery mode and run

```
sudo dpkg-reconfigure xserver-xorg
```
answer the questions and hopefully your setting will be normal

---

