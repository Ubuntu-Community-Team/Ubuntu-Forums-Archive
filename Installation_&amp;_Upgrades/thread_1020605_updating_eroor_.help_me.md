---
title: "updating eroor .help me"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by binoye on 2008-12-24
when i trying to install updates i get this error message,how can fix it? i am a beginner linux user so please help me



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2008-12-24
Close down the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by majabl on 2008-12-24
I was having the same problem (which your solution fixed - thanks!).  What's likely to have caused it, and how do I prevent it from happening again?

---

### Post by taurus on 2008-12-24
> **majabl said:**
> I was having the same problem (which your solution fixed - thanks!).  What's likely to have caused it, and how do I prevent it from happening again?

You probably cancelled either update-manager or synaptic before it completed so you have to run that command to fix the broken packages.

---

### Post by binoye on 2008-12-25
> **taurus said:**
> Close down the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

Thank you buddy,and wish you a happy prosperous x' mas and new year

---

