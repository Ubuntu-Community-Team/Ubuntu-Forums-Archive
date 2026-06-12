---
title: "does Dapper use both cores of my Core Duo ?"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by syxbit on 2006-06-10
In windows when looking at processes, you see both CPU's, and if only one application is going, you can only be at 50% cpu usage max.
i have a feeling this isn't the case with dapper, as there's no intel driver
right ?

---

### Post by syxbit on 2006-06-10
i just checked here
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
and it mentions using a different kernel depending.
i.e. a 64 bit kernel, or an smp kernel for dual core support
i'm gonna install the smp kernel tonight

---

### Post by jjcv on 2006-06-10
cat /proc/cpuinfo

will tell you how many CPUs are running.  You should two.

You need to install the i686 kernel to enable both cpus

---

### Post by siriusnova on 2006-06-10
actually i think he needs to install i686-smp to use both cores

---

### Post by web250 on 2006-06-10
```
sudo apt-get install linux-686-smp
```

---

