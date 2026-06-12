---
title: "Lenovo W520 Sees only 24 GB of RAM out of 32 GB"
date: 2012-06-18
forum: Hardware
---

### Post by DBQ on 2012-06-18
Hi everybody.

I have been running Ubuntu 12.0 on W520 and loving it.

Recently, I have ordered two 16 GB RAM modules to upgrade my system to 32 GB.

After adding the modules, the laptop sees only 24 GB of 32 GB (both in Ubuntu and in BIOS).  I tried removing the native modules (each 4GB), but it did no good.  What I am I doing wrong?

Thank You!

---

### Post by typhoon_tip on 2012-06-19
> **DBQ said:**
> ...the laptop sees only 24 GB of 32 GB (**both in Ubuntu and in BIOS**).

... that's because the **motherboard** of that model can only handle maximum 24 GB ! You can check with a command, it will report the max expansion possible:

```
sudo dmidecode --type memory
```

... and post the output here.

---

