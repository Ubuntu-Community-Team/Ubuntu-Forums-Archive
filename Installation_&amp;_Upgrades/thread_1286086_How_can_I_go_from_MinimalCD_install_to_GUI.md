---
title: "How can I go from MinimalCD install to GUI?"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by jimfl on 2009-10-08
After three failures with installing Ubuntu 9.04 (one from my own downloaded and burned CD and two from CD's included in Ubuntu books), I finally got the MinimalCD to download, burn, and successfully install. 

However, I now have just a command line, which I don't know anything about. How can I get from here to a full, normal GUI version?

Thanks!

---

### Post by wojox on 2009-10-08
```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by jimfl on 2009-10-08
Thanks VERY MUCH, Wojox. :smile: Those commands worked. But after the download and install, I'm still back at the command line prompt. What command will switch me to the GUI?

---

### Post by jeremyswalker on 2009-10-08
Try to see if you can start with:
```
sudo /etc/init.d/gdm start
```

---

### Post by SkyNet2029 on 2009-10-08
the gui is not really the issue here....
you could issue a
```
startx
```
from the command line to fire up the xserver

---

### Post by jimfl on 2009-10-09
Thank you jeremyswalker and SkyNet2029!  I am now happily GUIfied.

---

