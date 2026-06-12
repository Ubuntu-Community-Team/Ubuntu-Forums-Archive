---
title: "dual core only one"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by mouseboyx on 2007-05-29
Im pretty sure that xubuntu 7.04 is only using one of my cores because when my cpu monitor says its maxed out its only half way up the graph.

---

### Post by madmetal on 2007-05-30
> **mouseboyx said:**
> Im pretty sure that xubuntu 7.04 is only using one of my cores because when my cpu monitor says its maxed out its only half way up the graph.

what does apper with
cat /proc/cpuinfo
and
dmesg|grep Processor

?

UAResolved.

---

### Post by psusi on 2007-05-30
> **mouseboyx said:**
> Im pretty sure that xubuntu 7.04 is only using one of my cores because when my cpu monitor says its maxed out its only half way up the graph.

Yes, this is normal.  You only have a single threaded program that is trying to use the cpu, so it can only use one of them, and the other one is idle, giving 50% total utilization.

---

### Post by eggdeng on 2007-05-30
You should be able to see both cpus separately on the resources tab of the System monitor. If not, check your kernel version ```
uname -r
```You need to have the i686 version. More info at [http://ubuntuforums.org/showthread.php?t=277400](http://ubuntuforums.org/showthread.php?t=277400)

---

