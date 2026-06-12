---
title: "Intel Core 2 Dual Under-Clocked w/ Ubuntu"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by Czar on 2007-09-15
So I have a 2.66GHz ( 333*8 ) Intel C2D.  Over-clocked to 3.00GHz ( 375*8 ).

Ubuntu....  

```

$ cat /proc/cpuinfo 
processor       : 0
*snip*
cpu MHz         : 2000.000

processor       : 1
*snip*
cpu MHz         : 2000.000

```

Bleh, so I set-up CPU Frequency Scaling (which, btw, works `out of the box` Vs. other distros) and I can toggle between ondemand or full 2.66Ghz... yet where is my 3GHz?  

**Why or What is capping me?  **

I popped in PCLinuxOS & Sayabon LiveCD and both report the proper cpu MHz (3000) yet the scaling is off or something else is broken...  lmao.

Note:  I've tried tampering w/ the /sys/devices/system/cpu/cpu* stuff and the only thing that happened was a broke cpu scaling till reboot.

ty.

---

### Post by Czar on 2007-09-15
More notes....

$cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2667000 2000000 

$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand powersave userspace performance

---

### Post by EXCiD3 on 2007-09-15
Which version of Ubuntu are you using and what kernel?

---

### Post by Czar on 2007-09-15
> **EXCiD3 said:**
> Which version of Ubuntu are you using and what kernel?

$uname -r
2.6.20-16-generic

$ cat /proc/version
Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007

Version of Ubuntu?  I dunno what version it is considered, I imagine you could tag it as 'current' so what ever that might be atm.  (sudo aptitude upgrade;aptitude dist-upgrade).

Ty.

---

### Post by eggdeng on 2007-09-15
```
lsb_release -a
``` will give you the version.

---

### Post by Czar on 2007-09-15
> **eggdeng said:**
> ```
lsb_release -a
``` will give you the version.


Thanks!

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

---

