---
title: "Ubuntu freezes before log on screen comes, fresh installation"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by ufarooq on 2009-03-08
I have installed Ubuntu 8.10 i386 but after successful installation I am not able to lag on because Ubuntu freezes before log on screen comes, sometimes log on screen comes but i cannot type user name because my keyboard and mouse does not work.:(
I am using Dell gx270, 2.4 GHz, 764 mb Ram.
Please help me.

---

### Post by sanus|art on 2009-03-08
Try to type "startx" (without quotes) after the login. 
If not - 'cd /tmp' + 'ls -a' + find something like ".X0.lock", then remove that file (type 'sudo rm /tmp/X0.lock' or whatever it is named and after removal type 'startx'.

---

