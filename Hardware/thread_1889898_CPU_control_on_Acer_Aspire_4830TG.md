---
title: "CPU control on Acer Aspire 4830TG"
date: 2011-12-02
forum: Hardware
---

### Post by Loki84 on 2011-12-02
Hi,

I have an Acer Aspire TimelineX 4830TG (Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz) with Ubuntu 11.10 64bit, 3.0.0-13-generic.

Unfortunately I have a heating problem. It seems that all 4 CPUs are running on full speed all the time.

cpufreq-info tells me that the governor changes to "ondemand", as it should be. Also it tells me
[PHP]cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.70 GHz
  available frequency steps: 2.70 GHz, 2.70 GHz, 2.20 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.70 GHz and 2.70 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.70 GHz.
  cpufreq stats: 2.70 GHz:99.62%, 2.70 GHz:0.00%, 2.20 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.01%, 1.20 GHz:0.01%, 1000 MHz:0.01%, 800 MHz:0.34%  (44)
[/PHP][B]
current policy: frequency should be within 2.70 GHz and 2.70 GHz.[/B]
I am able to switch the governor, but it tells me anyway that the frequency should be 2.70GHz.

Can you please help me?

---

### Post by Loki84 on 2011-12-07
[https://bugs.launchpad.net/ubuntu/+bug/901232](https://bugs.launchpad.net/ubuntu/+bug/901232)

---

### Post by BC59 on 2011-12-07
Here is a workaround of the bug:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

