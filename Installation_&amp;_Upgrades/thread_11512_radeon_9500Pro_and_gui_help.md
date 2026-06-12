---
title: "radeon 9500Pro and gui help"
date: 2005-01-17
forum: Installation &amp; Upgrades
---

### Post by Thuun on 2005-01-17
ive just installed ubuntu on my system. 

my problem is that i cant come into the gui. it says :" grafical user interface could not be loaded". 

what should i do to come into the gui. 

i have tried to do something in xf86config, but i did not know what i shuold type to get it to work. help me please  :-k 

my system : 

2700+ 
9500pro 
512 mb pc 2700 ram

---

### Post by runenes on 2005-01-17
type:
```

cat /var/log/XFree86.0.log | grep EE
cat /var/log/XFree86.0.log | grep WW

```

And post the result, also post your /etc/X11/XF86Config-4 file.

---

### Post by Thuun on 2005-01-18
okay and then `you can tell me what to do ?

---

### Post by runenes on 2005-01-18
Maybe, maybe not, but the chance that someone else can help you is much greater. Your original question isn't all that detailed, specific etc, but if your problem is related to the X server, then those logs/files will probably clue you/us/me in on the real problem.

---

