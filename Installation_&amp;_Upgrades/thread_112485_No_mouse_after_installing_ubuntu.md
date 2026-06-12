---
title: "No mouse after installing ubuntu"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by Mcjensen on 2006-01-04
Hi, Any ideas on why my mouse wont work after installing ubuntu on second hard drive. Mouse works fine on windows 2000 when I boot into the first hard drive, Mikkel

---

### Post by Lord Illidan on 2006-01-04
[quote=Mcjensen]Hi, Any ideas on why my mouse wont work after installing ubuntu on second hard drive. Mouse works fine on windows 2000 when I boot into the first hard drive, Mikkel[/quote]

Give us some more data:

1. What is the make of your mouse? Is it ps2 or usb?
2. Give us your /etc/X11/xorg.conf
```
sudo gedit /etc/X11/xorg.conf
``` in a terminal, and copy and paste it here. Don't touch it though.

---

### Post by Mcjensen on 2006-01-04
Ok Thanks, I got it working by switchinbg to a usb mouse. My old one was a Ps2...it seems otheres here have had the same problem.
Mikkel

---

### Post by Lord Illidan on 2006-01-04
Good for you.

---

