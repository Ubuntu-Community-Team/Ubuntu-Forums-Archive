---
title: "powernowd stopped working after some update..."
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by Franko30 on 2007-05-25
Hi,

I use a fresh install of 7.04 on my Nexoc ([www.nexoc.de](www.nexoc.de)) Osiris S609II laptop.

Everything worked fine (and out of the box) until yesterday:

powernowd complains that CPU-Frequency-Scaling is not possible - but it worked fine until the day before yesterday, so I guess it was one of the automatic updates.

Reinstalling and restarting powernowd delivers the following error:

```
/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
 * CPU frequency scaling not supported
```

Did anybody encounter similar problems? I only became aware of this error because I always run the panel applet monitoring the CPU frequency. Otherwise I might have attributed the running CPU-fan to the hot weather...

Cheers

Franko30

---

### Post by wilk on 2007-05-26
I'm experiencing exactly the same problem, no idea how to fix it though.

---

### Post by IntuitiveNipple on 2007-05-26
As you're reasonably sure this occurred after an automatic update, check the history in Synaptic   and report the upgraded packages here.

Start Synaptic, choose File > History. Expand the calendar tree and select dates in turn. You're looking for any entry that says:

**Upgraded the following packages:**

---

### Post by Franko30 on 2007-05-27
Hi,

thanks for pointing me to the Synaptics history - I was completely clueless on this feature...

Well, the only updates before the error occured were

> libsmbclient (3.0.24-2ubuntu1.1) to 3.0.24-2ubuntu1.2
samba-common (3.0.24-2ubuntu1.1) to 3.0.24-2ubuntu1.2
smbclient (3.0.24-2ubuntu1.1) to 3.0.24-2ubuntu1.2
smbfs (3.0.24-2ubuntu1.1) to 3.0.24-2ubuntu1.2
vim-common (1:7.0-164+1ubuntu7) to 1:7.0-164+1ubuntu7.1
vim-tiny (1:7.0-164+1ubuntu7) to 1:7.0-164+1ubuntu7.1


and

> linux-restricted-modules-common (2.6.20.5-15.20) to 2.6.20.5-16.28

I guess none of these are frequency-scaling-relevant...

Completely removing powernowd (with configuration files) didn't help. Other frequency-scaling tools like cpufrequtils also complain that my processor does not support frequency scaling - but it does.

I guess I'll have to reinstall and see what happens.

Cheers

Franko30

---

### Post by wilk on 2007-05-27
I discovered that I can start powernowd if the powernow-k8 module is loaded.

---

