---
title: "(Pythonic) Optimizing Startup Time"
date: 2009-05-17
forum: Hardware
---

### Post by ayoung on 2009-05-17
Recently, I've been observing a significant (~1 minute) standstill in the orange Ubuntu (8.10) progress bar during startup.  So, I cobbled together the following Python script to read dmesg and tell me what steps are taking the longest:

```
#!/usr/bin/env python
import os, re

os.system('sudo dmesg > d.txt')
f=open('d.txt')
d=f.readlines()
f.close()
r=re.compile('^\[[\s]*(?P<time>\d+\.\d+)\]')
event=0
t1=0
speed=[]
for l in d:
    s=r.split(l)
    t2=float(s[1])
    dt=t2-t1
    dsc=s[2]
    speed.append([dt,event,t2,dsc])
    event+=1
    t1=t2
speed.sort()
speed.reverse()
print "   dt = t2-t1   |   event   |   time   |   description"
for i in range(10):
    print speed[i]
os.system('rm d.txt')
```

The winner, so to speak, clocking in at a duration of over 70 seconds, is "NET: Registered protocol family 10".  (Second place takes 18 seconds.)  I tried googling this event, but couldn't find any clarification to 1) what it achieves and 2) what may be causing the delay.  Of course, my approach is based on the assumption that all time-consuming offenders will be conveniently logged in dmesg.

Not to complain about Ubuntu's lightning-fast startup time, but there's always room for improvement, right?

---

### Post by coffeeaddict22 on 2009-05-17
There's a prettier and possibly better diagnostic tool around.  Have a look at bootchart; it's in the repositories and you can grab it through Synaptic Package manager.  Might help some more.  And if you aren't needing the LTS, upgrading to 9.04 and adding ext 4 (yeah, OK, so I'm a sad bunny with no important files to lose sleep over :-) ) halved my boot time easily

---

