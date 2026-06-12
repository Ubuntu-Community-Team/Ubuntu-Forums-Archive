---
title: "[SOLVED] Please help. dpkg interrupted"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by thnikk on 2009-07-18
I really hope im not posting in the wrong section, but I desperately need help. Every time I try to install anything, I get this. ```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```Please, if anyone could help me out it would be greatly appreciated. Sorry, I am a complete noob with this.

---

### Post by ibutho on 2009-07-18
Hi and welcome to the forum.
Go to Applications -> Accessories -> Terminal and enter
```
sudo dpkg --configure -a
```

---

### Post by raymondh on 2009-07-18
what happens when you type (in terminal)

```
sudo dpkg --configure -a
```

then ...

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by thnikk on 2009-07-18
Thanks a lot :D all working perfectly now

---

### Post by raymondh on 2009-07-18
> **thnikk said:**
> Thanks a lot :D all working perfectly now

Congratulations and welcome.

---

