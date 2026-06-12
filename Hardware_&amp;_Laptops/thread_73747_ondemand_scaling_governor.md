---
title: "ondemand scaling governor"
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by websavages on 2005-10-09
How can I configure it so that when I boot up my laptop my scaling governor is set to ondemand. 

Cheers ws

---

### Post by heimo on 2005-10-09
I have no experience using this setting, but editing /etc/sysfs.conf file should do it - use a line like:
```
devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
```

---

