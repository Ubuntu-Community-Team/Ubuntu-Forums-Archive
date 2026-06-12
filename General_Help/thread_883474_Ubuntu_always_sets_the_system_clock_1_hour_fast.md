---
title: "Ubuntu always sets the system clock 1 hour fast"
date: 2008-08-08
forum: General Help
---

### Post by Optical on 2008-08-08
Whenever I start up Ubuntu it has always set my system clock one hour fast. When I boot up into windows the clock is always fast until I reset it or the it syncs with the internet server. Changing the timezone has no effect, and changing the clock manually doesn't solve the problem either (it just sets it self back to one hour fast on reboot), how to I set the clock to run properly?

---

### Post by p_quarles on 2008-08-08
Try running
```
sudo dpkg-reconfigure tzdata
```
and choose the correct settings. If that doesn't fix things even following the next reboot, post back here and we'll look deeper into the issue. But, basically, that's the first thing to try.;

---

### Post by Optical on 2008-08-08
That appears to have worked. I think it was really that I just kept choosing cities that were 1 hour ahead of where I live, until I sat there and googled what time it was in all of those cities. I wish it would have just given me that options of "Central Time, Eastern Time etc..." but at least it's fixed now. Thanks!

---

### Post by Hillryank on 2009-05-02
I was having the same problem, this helped. Thanks.

---

