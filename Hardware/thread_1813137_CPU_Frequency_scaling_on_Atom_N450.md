---
title: "CPU Frequency scaling on Atom N450"
date: 2011-07-27
forum: Hardware
---

### Post by marcio_mi on 2011-07-27
Dear all,
in the neverending battle to get more juice out of my battery, I realized that there is maybe something wrong in the frequency scaling of my atom n450. Here' the output of cpufreq-info

```
miccoli@netbook-N230:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1000 MHz - 1.67 GHz
  available frequency steps: 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.
  cpufreq stats: 1.67 GHz:38.57%, 1.33 GHz:3.67%, 1000 MHz:57.76%  (23882)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 1000 MHz - 1.67 GHz
  available frequency steps: 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 1.67 GHz:35.08%, 1.33 GHz:3.47%, 1000 MHz:61.45%  (23580)

```

I thought that lowest frequency state was 800MHz on the atom N450. If you have an atom N450, can you please check and report the output of cpufreq-info? thanks a lot buddies. Any other suggestion is welcome :P

P.S. there is another thread that speaks of this issues: 
[http://ubuntuforums.org/archive/index.php/t-1431982.html](http://ubuntuforums.org/archive/index.php/t-1431982.html)

however the workarounds there do not work for me. The first one because even by modifying the  /etc/laptop mode/conf.d/cpufreq.conf file, I cannot set a value lower then 1000MHz. The second one because I cannot even find the file cpufreqd.conf

---

### Post by marcio_mi on 2011-07-28
no help from google this time...

Any idea on how I could insert a new frequency scaling step at 800MHz? also, really, please let me know if your atom cpu has different frequency scaling.

cheers

---

