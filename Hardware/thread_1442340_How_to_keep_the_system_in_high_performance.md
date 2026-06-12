---
title: "How to keep the system in high performance"
date: 2010-03-29
forum: Hardware
---

### Post by Dracirate on 2010-03-29
How to keep the system in high performance always because every time i shut down - reboot my laptop automatically change to - on demand -

Thank in advance.

---

### Post by Fafler on 2010-03-30
Add

```
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

to your /etc/rc.local anywhere between the #!/bin/sh -e and exit 0 lines.

---

### Post by Dracirate on 2010-03-30
> **Fafler said:**
> Add

```
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```to your /etc/rc.local anywhere between the #!/bin/sh -e and exit 0 lines.

Thank you buddy :D

---

### Post by jmate24 on 2010-03-30
thanx. i have been looking everywhere for that.

---

