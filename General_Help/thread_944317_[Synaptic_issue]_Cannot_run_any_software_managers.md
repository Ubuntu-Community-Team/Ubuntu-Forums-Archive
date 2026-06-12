---
title: "[Synaptic issue] Cannot run any software managers"
date: 2008-10-11
forum: General Help
---

### Post by archellions on 2008-10-11
When i try to run synaptic or any other software manager, i get an error, the error reads:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I have tried a few things, but i cant seem to fix the issue. Please advise me on what to do. I appreciate any help you guys can give me. Ubuntu has been a wonderful experience and so far this has been my only issue.

---

### Post by plucky on 2008-10-11
> **archellions said:**
> When i try to run synaptic or any other software manager, i get an error, the error reads:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I have tried a few things, but i cant seem to fix the issue. Please advise me on what to do. I appreciate any help you guys can give me. Ubuntu has been a wonderful experience and so far this has been my only issue.

Open a terminal **Applications > Accessories > Terminal** and ```
sudo dpkg --configure -a
``` should fix your problem

Good Luck

---

### Post by Kevbert on 2008-10-11
It may be worth running
```
sudo apt-get install -f
```
to repair any damaged packages after you've run the command in the previous post. It may also be worth running
```
df -h
```
to see if any drives/directories are full as this problem can be caused by a full directory.

---

