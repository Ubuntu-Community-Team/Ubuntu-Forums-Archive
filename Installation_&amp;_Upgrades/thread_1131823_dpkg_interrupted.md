---
title: "dpkg interrupted"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by Exhaust Manifold on 2009-04-21
I have ubuntu 8.10 and everything was going dandy until a few days ago. Now every time I try to update or download software I get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I opened the "terminal" program and typed in 'dpkg --configure -a' and it said: "requested operation requires superuser privilege"

What does the error mean and how can I fix it? And how does one acquire "superuser privilege"?

---

### Post by Partyboi2 on 2009-04-21
Hi, you need to put sudo in front of the command to get admin rights so it would be
```
sudo dpkg --configure -a
```

sudo allows you to gain admin rights temporarily to preform the action

---

### Post by Exhaust Manifold on 2009-04-21
Thanx problem sorted

---

