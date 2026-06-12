---
title: "Uninstall opera browser"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by timreed on 2009-01-17
Help.. I recently installed Opera Browser and I can uninstall it. I tried ti delete the opera files but there seems to be a lock on them. Wont let me delete them. What kind of program has no uninstall..help

---

### Post by taurus on 2009-01-17
How did you install it?  Did you install it from synaptic, add/remove, apt-get/aptitude, or dpkg?  If you installed it with dpkg command, you can uninstall it with **sudo dpkg -r filename** as well.

p.s.  Double post, [http://ubuntuforums.org/showthread.php?t=1042090](http://ubuntuforums.org/showthread.php?t=1042090).

---

### Post by thezood on 2009-01-17
> **timreed said:**
> Help.. I recently installed Opera Browser and I can uninstall it. I tried ti delete the opera files but there seems to be a lock on them. Wont let me delete them. What kind of program has no uninstall..help

If you compiled Opera from source with 'make', you could probably uninstall it by navigating to the source directory and type:
```

sudo make uninstall

```

---

