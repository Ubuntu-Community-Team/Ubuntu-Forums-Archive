---
title: "update manager and synaptic package manager failed"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by mail.vipinaggarwal on 2009-05-02
Update manager and synaptic manager has failed on my desktop running ubuntu 8.01. I am new to ubuntu and cant handle this error. The error is


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


How to run ´dpkg --configure -a´

Please help

---

### Post by tommcd on 2009-05-02
> **mail.vipinaggarwal said:**
> 
How to run ´dpkg --configure -a´

Open a terminal (applications > accessories > terminal) and run:
```
sudo dpkg  --configure -a
```
Make sure synaptic and update manager are not running when you do this.

---

### Post by mail.vipinaggarwal on 2009-05-02
Thanks man! M really grateful to u...Now everything is working fine...

---

