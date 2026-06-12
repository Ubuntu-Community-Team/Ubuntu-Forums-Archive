---
title: "extra spaces in firefox"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by sanderd17 on 2009-04-09
Hi, 
a few days ago I had changed my firefox profiles. And now firefox shows about three spaces if there should be one. It happens always and even in the menu's of firefox, it also happens with epiphany and abrowser but not with thunderbird or seamonkey. I've seen a similar bug on launchpad ([https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/193108]("https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/193108")) but it didn't help me, they said to uninstall pango-graphite but I hadn't installed it. I've tried to reinstall all gecko related things but it didn't make any difference.

I use ubuntu 8.10, 64 bit version.

If anyone could help me, I would be very pleased.

I've attached a screenshot bellow.

---

### Post by utnubuuser on 2009-04-10
Have you tried > sudo apt-get remove firefox --purgethen a reinstall?

---

### Post by sanderd17 on 2009-04-11
I'm sorry, it didn't work. I think it has something to do with gecko but I don't know in witch package the problem is.

---

### Post by sanderd17 on 2010-01-15
OK, it was the google toolbar dooing this. Removed it and the spaces where normal.

---

