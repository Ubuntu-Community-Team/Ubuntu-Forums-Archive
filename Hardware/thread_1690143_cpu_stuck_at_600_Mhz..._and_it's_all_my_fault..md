---
title: "cpu stuck at 600 Mhz... and it's all my fault."
date: 2011-02-17
forum: Hardware
---

### Post by wcampbell on 2011-02-17
I messed it up, then I made it worse.

After a couple of years of trouble free usership, I decided that the occasional loud fan noise, and short battery life was worth messing with.  I installed CPU freq and found that when I went on battery, my Latitude D800 would just sit at 600MHz.  At some point, I removed cpufreq and installed PowernowD, thinking that would be easier to configure correctly.  I was wrong again.

My goal is to just get back to good ole 1.7Ghz.  with or without cpufreq, with or without powernowd.  

So here is current state:  Cpufreq is installed again.  when I first boot, it runs at 1.7GHz, but eventually drops to 600MHz and stays there.  I think the "policy" is why, but have no idea how to change that:

warren@warren-laptop:~$ cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 600 MHz - 1.70 GHz
  available frequency steps: 1.70 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 600 MHz and 600 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.
  cpufreq stats: 1.70 GHz:6.46%, 1.40 GHz:0.13%, 1.20 GHz:0.10%, 1000 MHz:0.14%, 800 MHz:0.18%, 600 MHz:92.99%  (5012)
warren@warren-laptop:~$ 


Also, the min and max scaling both show 600Mhz, any attempt I make to change these, even as root, return permissions errors:

root@warren-laptop:/sys/devices/system/cpu/cpu0/cpufreq# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
600000

I've googled like crazy, but there are so many different scenarios that are similar but not exactly the same and nothing I seem to do makes a difference.

Any help, advice, or witchcraft would be greatly appreciated.

---

### Post by mikewhatever on 2011-02-17
It looks like you need to use cpufreq-set and modify the max cpu frequency the governor can select, which is currently stuck at 600MHz.

```
cpufreq-set --max 1700000
```

---

### Post by wcampbell on 2011-02-18
Thanks much for your help.

Tried that, and no error is returned, but as you can see below, cpufreq-info still reports min and max both as 600MHz, and that's where it stays:


warren@warren-laptop:~$ sudo cpufreq-set --max 1700000
warren@warren-laptop:~$ cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 600 MHz - 1.70 GHz
  available frequency steps: 1.70 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 600 MHz and 600 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.
  cpufreq stats: 1.70 GHz:0.02%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:0.00%, 800 MHz:0.00%, 600 MHz:99.98%  (1)
warren@warren-laptop:~$

---

### Post by wcampbell on 2011-02-18
one more piece of info- not sure if this is relevant, but figured I'd throw it out here.  Some googling lead me to look at /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq.  Currently it is 600000.  I try to increase that and I get a permissions error.  When I try to do it as root, I get "Bad file descriptor".

---

### Post by wcampbell on 2011-02-18
one more piece of info:  when I shut it down for a while, and then bring it up, at first it runs at 1.7GHz, but as soon as I remove the power cable it goes straight to 600Mhz... doesnt come backup to 1.7Ghz no matter what I do.

---

### Post by wcampbell on 2011-02-18
I figured it out from another thread!  This worked for me:


Code:

sudo gedit /etc/default/cpufreqd

then locate the line:

Code:

CPUFREQ_CPU_MODULE=""

and change to:

Code:

CPUFREQ_CPU_MODULE="speedstep-centrino"

---

### Post by mikewhatever on 2011-02-18
Hm..., what about /etc/cpufreqd.conf?  It has policy settings for governors, including min/max frequencies.

---

