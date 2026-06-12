---
title: "CPU min frequency same as max when booting up"
date: 2008-05-30
forum: Hardware
---

### Post by mojones on 2008-05-30
Hi, 

On a thinkpad X61t with a dual-core CPU (Intel Core 2 Duo CPU L7500 (1.60 GHz) ), cpufreq gives the following after booting up:

```
$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, ondemand, conservative, powersave, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, ondemand, conservative, powersave, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
```

Obviously, because the min speed is the same as the max, the ondemand governor cannot change the speed and it stays stuck at 1.60 Ghz.  If I use cpufreq-set to set the correct minimum speed, it works fine:

```
$ sudo cpufreq-set -d 800
$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, ondemand, conservative, powersave, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, ondemand, conservative, powersave, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

```

And the cpu speed is correctly regulated.  What is causing the min speed to be incorrectly set?

---

### Post by mojones on 2008-05-30
A further problem; even after I've manually set the correct min speed, after a period of time it will get set back to 1.60 GHz - I'm guessing there must be some daemon process that is changing it.

---

### Post by sdennie on 2008-05-30
powernowd is probably responsible for changing it unless you've made any other changes.  I once had a problem similar to this (actually, the opposite in that my CPU was stuck at lowest frequency while on ondemand).  One thing you could try (it may make no difference) is to change the governor and then change it back to ondemand:

```

sudo sh -c "echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

```

---

### Post by mojones on 2008-05-30
I'm not sure whether I have powernowd installed:

```
$ sudo apt-get remove powernowd
[sudo] password for martin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package powernowd is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

However:

```
$ locate powernowd
/etc/default/powernowd
/etc/init.d/powernowd
/etc/init.d/powernowd.early
/etc/rc1.d/K20powernowd
/etc/rc2.d/S10powernowd.early
/etc/rc2.d/S20powernowd
/etc/rc3.d/S20powernowd
/etc/rc4.d/S20powernowd
/etc/rc5.d/S20powernowd
/var/lib/dpkg/info/powernowd.list
/var/lib/dpkg/info/powernowd.postrm

```

.. not sure what's going on.

---

### Post by sdennie on 2008-05-30
Did you previously remove powernowd or install something that removes it?  On my machine, if I uninstall it, it does odd things to my machine (like setting the machine to max).  Did you try those command I wrote about resetting the governor?  powernowd probably isn't strictly needed if you are using the acpi-cpufreq kernel module.  Or, you could just re-install it with:

```

sudo apt-get install powernowd

```

(Note: It's normal to have all that /etc and /var stuff laying around if you previously had powernowd installed and removed it without using --purge).

Edit:
What a convoluted post.  Try the previous post fixes, if not, try to re-install powernowd.

---

### Post by mojones on 2008-05-30
Resetting the governor, didn't have any effect; I'll try reinstalling powernowd and see what happens.

---

### Post by stream303 on 2008-05-30
In my situation, I found powernowd unresponsive, and just uninstalled it and used *cpudyn* instead.  Bingo.

---

