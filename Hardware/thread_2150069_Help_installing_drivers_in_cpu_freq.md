---
title: "Help installing drivers in cpu freq"
date: 2013-05-30
forum: Hardware
---

### Post by Vman96 on 2013-05-30
I just successfully installed cpu freq on my computer, however I can't set a governor.  When I type cpufreq-info i get ```
vincent@vincent-1201N:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.

```

As you can see, it doesn't have a driver installed, but I am clueless on how to accomplish that. :confused:

My processor is a 1.60 GHz dual-core Intel Atom and I am running Xubuntu 12.04

---

