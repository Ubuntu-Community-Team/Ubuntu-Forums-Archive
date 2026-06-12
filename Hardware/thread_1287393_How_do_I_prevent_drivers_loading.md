---
title: "How do I prevent drivers loading?"
date: 2009-10-10
forum: Hardware
---

### Post by David Samuels on 2009-10-10
I may have acquired a rogue driver (I don't know how) which prevents my keyboard and mouse/trackpad from functioning so I can't even log in at startup.

Can anyone advise me how to look at the list of drivers and their loading sequence so that I can do some controlled experimentation and find out what's going wrong? If not, I guess I'll have to re-install from the CD :(

---

### Post by IcarusR on 2009-10-10
Why do you say 
> I may have acquired a rogue driver 

Modues can be prevented from loading by blacklisting them in /etc/modprobe.d/blacklist

To see a list of loaded modules & what they are used by 
```
lsmod
```

---

### Post by David Samuels on 2009-10-12
I suspect a rogue driver because, at the point at which my login screen is presented, neither keyboard nor mouse are working. I know they're not broken because they work when booting into recovery mode or from the live CD.

As far as lsmod is concerned, I could use it if I could log in! I can boot into a root prompy and run lsmod from there but I don't imagine the modules in use would be exactly the same as when a login screen was presented.

Is there a way of starting the GUI from a prompt?

---

### Post by IcarusR on 2009-10-12
```
startx
``` 
Should start window manager from prompt.

What version of Ubuntu are you running ??

---

### Post by David Samuels on 2009-10-13
> **icarusr said:**
> what version of ubuntu are you running ??
9.04

---

