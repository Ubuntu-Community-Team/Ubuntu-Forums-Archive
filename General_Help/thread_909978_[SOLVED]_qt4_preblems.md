---
title: "[SOLVED] qt4 preblems"
date: 2008-09-04
forum: General Help
---

### Post by Ershess on 2008-09-04
I solved this problem, and google "told" me that i was not 1st with it, but there was no solution. So:

Error when starting applications:
pthread_mutex_lock.c:87: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.

and all qt4 apps are not working.

Solution:
sudo apt-get remove libqt4-network
sudo apt-get remove libqtcore4

and all will be fine again. 
if not - also reinstall with Sytaptic all apps with "qt". If any app can't be reinstalled with error - apt-get remove it.

---

