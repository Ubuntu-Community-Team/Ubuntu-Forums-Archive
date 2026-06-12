---
title: "Intel T9300 is not scalable in 8.1"
date: 2008-12-29
forum: Hardware
---

### Post by mahmoodn on 2008-12-29
Hi,
I have installed ubuntu 8.1 desktop on my HP pavilion dv27775ee which has Intel T9300 2.5Ghz (penryn). The problem is cpufreqd does not support my processor so I am not able to scale its frequency. Here is the out put of "cpu-info":
```
root@laptop:~/Tools# cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

```

---

