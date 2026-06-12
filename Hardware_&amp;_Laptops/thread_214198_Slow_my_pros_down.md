---
title: "Slow my pros down"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by shazbot on 2006-07-12
hello

am running a MSI mega book 270 with a AMD 64 Turon, this goes thru the battery in about 40 mins so I need to slow it down, 

The CPU Frequency montitor says that scaling is unupported, and this cannot be done

Is this right or is there a work around

Am running dapper with latest kernel 

Thanks

---

### Post by MrHorus on 2006-07-12
```
sudo cpufreq -g powersave
```

That will use the powersave governor for CPU scaling.

That should work.

---

### Post by shazbot on 2006-07-12
sudo: cpufreq: command not found


didn't work :(

---

