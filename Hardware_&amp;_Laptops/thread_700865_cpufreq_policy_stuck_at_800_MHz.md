---
title: "cpufreq policy stuck at 800 MHz"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by Pridkett on 2008-02-18
I've got an IBM Thinkpad t43p with a 2.13GHz processor capable of speedstep.  If I leave the system plugged in all the time, it will happily change processor speed according to the load on the machine -- an indication that Speedstep is working fine.  If I take the machine on and off AC power, sometimes cpu frequency scaling will cease working, locking the processor at 800MHz.  I believe is that somehow the policy is getting stuck at 800MHz, here's what cpufreq-info says:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.13 GHz
  available frequency steps: 2.13 GHz, 1.87 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
```

I can try setting the speed through cpufreq-set or directly through the /sys interface, but it doesn't seem to actually do anything, I'm guessing it's because the policy has the maximum speed set to 800MHz.  So, is there anyway that I can override this policy?  Rebooting always fixes the problem too.

---

### Post by desktopfan on 2008-02-21
Same problem here, running archlinux.

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.70 GHz
  available frequency steps: 1.70 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, powersave, ondemand, performance
  current policy: frequency should be within 600 MHz and 600 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.

```

And it will not change even if I use cpufreq-set to manually select the speed.

---

### Post by Yellow Pasque on 2008-02-21
Do you folks have the cpufreq daemon loaded? (lsmod | grep cpu) Sometimes that will keep setting the policy for you according to /etc/cpufreqd.conf
You may have to edit that file if the cpufreq driver can't properly detect switching between AC and battery (or remove the cpufreq daemon from rc.conf in Arch). Also, make sure you set the maximum frequency before trying to set the speed, i.e.:
```
cpufreq-set -u 1700MHz
cpufreq-set -f 1700MHz
```

---

### Post by desktopfan on 2008-02-21
cpufreq daemon is loaded and the conf file is set for my max and min frequencys.

```
cpufreq_conservative     6664  1
cpufreq_powersave       1920  0
cpufreq_ondemand        7180  0
acpi_cpufreq           11420  0
freq_table              3984  2 cpufreq_ondemand,acpi_cpufreq
processor              29400  3 thermal,acpi_cpufreq

```

```
[peter@inspiron ~]$ cat /etc/conf.d/cpufreq
#configuration for cpufreq control

# valid governors:
#  ondemand, performance, powersave,
#  conservative, userspace
governor="conservative"

# valid suffixes: Hz, kHz (default), MHz, GHz, THz
min_freq="600MHz"
max_freq="1700MHz"

```

possible because Im using conservative instead of ondemand?

More testing needed I think

---

### Post by desktopfan on 2008-02-22
Managed to fix the problem.

I changed from the acpi_cpufreq module to the speedstep-centrino module
and everything is fine. Happily switches between AC and battery without 
getting stuck.

---

### Post by knj on 2008-03-19
How did you change what driver you are using? I am having the same bug on a HP HDX 9070EO with Core 2 Duo.

---

### Post by franestepona on 2008-03-25
Try:

```
sudo gedit /etc/default/cpufreqd
```

then locate the line:

```
CPUFREQ_CPU_MODULE=""
```

and change to:

```
CPUFREQ_CPU_MODULE="speedstep-centrino"
```

---

### Post by mk4umha on 2008-04-15
I don't even have this file.
sudo gedit /etc/default/cpufreqd

```
acpi_cpufreq           10632  1 
cpufreq_ondemand       10896  1 
cpufreq_userspace       6048  0 
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_stats           8160  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor              36232  2 acpi_cpufreq,thermal

```

my problem is that the cpu scales when i cold boot into linux without the AC power, once AC power is plugged in, it's still ondemand and scales, if I remove the AC, after that, it will stay stuck at 800MHZ even though it's still ondemand.

is there a way to fix this? I'm on a Dell D630 too.

---

### Post by mk4umha on 2008-04-15
I'm also using laptop mode to control cpu scaling, could that be the problem?

---

