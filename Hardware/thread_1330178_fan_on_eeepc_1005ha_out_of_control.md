---
title: "fan on eeepc 1005ha out of control"
date: 2009-11-18
forum: Hardware
---

### Post by mabtifro2 on 2009-11-18
Im running ubuntu 9.10

the fan on this machine, once it gets started, doesnt slow down or stop. omg what a headache.  the cpu temperature, according to eeepct utility, is 49 C. sometimes it sounds like a jet engine, and even when i close all program and just let it sit, even in a cold room, the fan just spins and spins and never gives up. i have to put it to sleep and wake it up to get it to stop. what the hell can i do about this? it did it in 9.04 and is still doing it in 9.10

---

### Post by nixscripter on 2009-11-18
You might see if the computer is capable of dynamic CPU frequency scaling.

See if it will cool down after you run this:

```
sudo cpufreq-set -g powersave
```

That will make the CPU use minimal power all the time if it works.

Hope this helps.

---

### Post by tophatandy on 2009-12-15
curious as to what happened. I have the same computer but do not have a similar problem in the least. Mine is completely silent..

---

### Post by viper250 on 2009-12-15
the motor in your cooling fan is a form of stepper motor (if it has 3 wires)
and is controlled by an inductive pickup that is monitored by the cpu.if the temp increases then the cpu will step up the frequency thereby increasing the speed.
the fan should be fairly quiet during operation but you should hear the increase in airflow when fan speeds up.
you probably need a new fan (even some new fans have been found to be faulty)

---

### Post by mabtifro2 on 2011-01-11
> **tophatandy said:**
> curious as to what happened. I have the same computer but do not have a similar problem in the least. Mine is completely silent..

sorry i didnt see this message till now. the problem has been fixed, its been running perfectly for months i guess, to be honest i dont remember how i fixed it, i forgot it even had this problem till i saw this old post.

---

