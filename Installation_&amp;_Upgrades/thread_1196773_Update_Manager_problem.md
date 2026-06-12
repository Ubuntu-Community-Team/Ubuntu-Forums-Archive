---
title: "Update Manager problem"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by raj727 on 2009-06-25
I recently upgraded to 9.04.  I added several software packages following the guide on an ubuntu help site.  The only software that didn't seem to install was google earth.

I tried to used update manager to install some updates but got the following error message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I know I have to run some commands in terminal, but I'm not sure which ones.  Could someone tell me what those commands would be?

---

### Post by philcamlin on 2009-06-25
try and run this :)

sudo dpkg --configure -a

i had that error once too i was like wtf and then it got fixed when i ran that :popcorn::popcorn::popcorn:

---

