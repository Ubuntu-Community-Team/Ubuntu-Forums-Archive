---
title: "Srinidhi SA"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by sasrinidhi on 2009-06-15
I have installed UBUNTU 8.10 Desktop Edition by partitioning my hard disk .
Whenever I try to play audio on my PC , a window opens up prompting to install media plugins. When I try to install media plugin ,a error message is displayed as 

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]
I had earlier installed the same version in WUBI mode.There it worked perfectly well.

Please help correct this problem.

---

### Post by zvacet on 2009-06-15
First go to the system>admin>software sources and check all except source under Ubuntu software and first two under update tab.Reload.If you still have problems type in terminal

```
sudo dpkg --configure -a
```

---

### Post by sasrinidhi on 2009-06-16
Thanks a lot......... I got it corrected ..:p.........

Could you briefly explain the function of the command you specified in your reply?

---

### Post by zvacet on 2009-06-16
It is command for all unconfigured and unpacked packages to configure.You will find more if you in terminal type

```
man dpkg
```

---

