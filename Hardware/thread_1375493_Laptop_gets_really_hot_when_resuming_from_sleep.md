---
title: "Laptop gets really hot when resuming from sleep"
date: 2010-01-07
forum: Hardware
---

### Post by pac-man on 2010-01-07
Hey guys, I've got a problem I've experienced sometimes: my laptop gets really hot when I wake it up after being suspended to RAM. Curious things happen along with this heat problem: the battery icon on the taskbar shows a red X and says "battery not installed" (when the battery is actually installed and with good charge) and the system temperature widget doesn't move from 27 celsius degrees, when normally it shows 48 degrees and it's obvious that when I get this problem the actual temperature is way above 48 celsius.

I got windows 7 in the other partition and it works pretty good, never had this problem in windows.

My system specs:

Compaq presario c769us
2gigs RAM
Intel Pentium dual core
Kubuntu 9.10 

Any ideas on what could I do? Thanks :P

---

### Post by derekmbarnes on 2010-01-08
Welcome to the club; seems everyone with a laptop is having overheating problems. At this point it looks like it might be an issue with the current Linux kernel (2.6.31-xx), since users who downgrade to earlier versions (e.g., 2.6.28-xx) report "fixing" the issue by doing so.

We're working on the problem. (Filing bug reports is confusing.) In the meantime, install GKrellM System Monitor to keep track of your hardware performance, and set up a fan in front of the cooling vent if possible.

---

### Post by pac-man on 2010-01-08
And what are the features I will lose with the downgrade?

---

### Post by derekmbarnes on 2010-01-10
I don't recommend trying the downgrade. Development is aware of the problem and trying to get it fixed:

[http://bugzilla.kernel.org/show_bug.cgi?id=14695](http://bugzilla.kernel.org/show_bug.cgi?id=14695)

---

### Post by pratik_narain on 2010-06-17
is this issue resolved in newer kernels in kubuntu lucid? I'm getting temp about 61 deg c on my dell inspiron 1545 laptop and unlike karmic cpu fans do not run periodically to decrease this temp(it happened in karmic). Also, Is this temp normal or too high for the laptop.(room temp is well above 35 deg c)

---

