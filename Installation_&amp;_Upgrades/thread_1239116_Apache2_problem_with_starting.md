---
title: "Apache2 problem with starting"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by FnTm on 2009-08-13
Hi! 

I am running Ubuntu 9.04 And I ran into some problems.

I got fed up with Xampp and decided to install all I needed myself. And heres the problem. When I first installed apache2, it was running fine, but after reboot, it stopped working. Simply would not start. Can Anyone help me? Thanks!

---

### Post by JohnLau on 2009-08-13
Did you install it from the repository?
Try this
```
sudo apt-get install --reinstall apache2
```
then reboot.

John

---

