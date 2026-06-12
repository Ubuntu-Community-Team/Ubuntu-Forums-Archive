---
title: "command to find cpu voltage"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by gauthamnaggg on 2008-02-27
Hello all,

 Is there any command to find the cpu voltage other than sensors command ?. Currently I am using ubuntu 7.04 and  2.6.20-15 kernel.

  :guitar:

---

### Post by Yellow Pasque on 2008-02-27
No, you need the sensor working or you could look in your BIOS if it has a hardware monitor to see an actual reading.

You could also guess what the core voltage is set to if you know what kind of processor you have and what frequency scaling it's using (if any).
```
cat /proc/cpuinfo
cpufreq-info
```

---

