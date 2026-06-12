---
title: "Help! Failed to start X Server"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by lsutiger on 2007-06-06
I followed the instructions on [this page]("http://ubuntuforums.org/showthread.php?t=361136&highlight=ATI") and got as far as # 2 (uninstall all fglrx in synaptic) and now when I boot I get a "Failed to start X Server", along with Failed to load module "fglrx" module does not exist, 0)
No Drivers available
Fatal server error: no screens found.
I am now stuck at the command line...how do I get my screen back?
Thanx!

---

### Post by bated_breath on 2007-06-07
Can you not complete the rest of the steps from the command line?

---

### Post by taurus on 2007-06-07
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lsutiger on 2007-06-07
Thanx Taurus!

---

