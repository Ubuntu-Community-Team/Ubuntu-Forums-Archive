---
title: "CPU Frequency"
date: 2010-03-30
forum: Hardware
---

### Post by nmyrick on 2010-03-30
My CPU frequency sticks to 800Mhz when restarting my computer.  I would like to set the default to be 100%, which is 1.46Ghz.  Is there any way to do this?  I have an Acer 4720z laptop with an Intel Pentium Dual Core T2310 processor.

I have CPU Frequency Scaling Monitor 2.28.0 installed on my panel. When I set the frequency to "performance" or "1.46 Ghz, it works fine until I restart my computer.  Then it goes back to "On Demand" setting, which ranges from 800Mhz to 1.46Ghz.

Thanks,
nmyrick

---

### Post by wojox on 2010-03-30
```
gksudo gedit /etc/init.d/ondemand
```

Change **echo -n ondemand > $CPUFREQ** to **echo -n performance > $CPUFREQ**

---

### Post by nmyrick on 2010-03-30
Thank you Wojox, that worked.

---

### Post by wojox on 2010-03-30
Welcome ;)

---

