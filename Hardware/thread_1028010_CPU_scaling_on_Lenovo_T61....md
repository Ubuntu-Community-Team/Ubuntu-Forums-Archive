---
title: "CPU scaling on Lenovo T61..."
date: 2009-01-02
forum: Hardware
---

### Post by mariner09 on 2009-01-02
It would seem that the latest kernels do not play well with CPU scaling.  I'm currently running 2.6.27-10-generic on my T61 with an Intel T7300 CPU.  Powernowd would just generate an error on boot and tell me the CPU did not support scaling.  cpufreqd loads and cpufreq-info tells me some details, but the applet does not allow any changes to the profile or speeds.

Anyone have any ideas or suggestions???

---

### Post by mariner09 on 2009-01-02
Call me silly...

I did not have linux-backports-modules installed for the 2.6.27-10-generic kernel and that's why powernowd was not working.

Go figure...

---

