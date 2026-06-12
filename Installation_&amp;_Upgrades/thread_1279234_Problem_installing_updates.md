---
title: "Problem installing updates"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by SavageHenry on 2009-09-30
Hi, I ran the update manager this morning and received the following error message,

 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I am completely new to ubuntu and linux in general and have no idea how to fix this, if anyone can help please and thanks.

---

### Post by ajgreeny on 2009-09-30
Open a terminal and run ```
sudo dpkg --configure -a
``` as the error message says, then ```
sudo apt-get update
``` and finally ```
sudo apt-get upgrade
```

---

