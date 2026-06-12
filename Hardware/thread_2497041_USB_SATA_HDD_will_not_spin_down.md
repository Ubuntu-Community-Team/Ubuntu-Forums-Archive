---
title: "USB SATA HDD will not spin down"
date: 2024-04-21
forum: Hardware
---

### Post by leejenon on 2024-04-21
Hi,

Could you help me please with getting the timeout/spin-down status of my SATA drive?

And also setting this too. I have tried - 

```
sudo hdparm -I /dev/sdd | grep level
```

..but it does not display anything.

Thanks, Lee

---

### Post by leejenon on 2024-04-22
Resolved - disk limitation.

---

