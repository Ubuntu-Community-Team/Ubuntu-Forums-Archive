---
title: "error, please help"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by zurielist on 2009-01-22
I can't download from my update manager. I am a novice with computers.
Error Message. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2009-01-22
Close the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by zurielist on 2009-01-22
Thanks a lot. I am going to try that now.

---

### Post by zurielist on 2009-01-22
I worked like a charm. Thanks again.

---

