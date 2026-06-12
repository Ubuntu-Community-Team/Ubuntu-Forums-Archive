---
title: "disabling devices, preventing modules from loadin"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by Zyphrexi on 2007-04-18
where and what is the file that indicates what modules are being loaded in ubuntu?

How can I prevent a device from being loaded by disabling the module?

---

### Post by justin99 on 2007-04-18
Here's an example of how to disable a kernel module by editing the modprobe.conf file.

[http://www.ducea.com/2006/06/01/disable-ipv6-module-on-default-kernels/](http://www.ducea.com/2006/06/01/disable-ipv6-module-on-default-kernels/)

You could also just rename the module in /lib/modules/<kernel version> so it can't be found. But this is kinda ugly.

---

### Post by yabbadabbadont on 2007-04-18
You can also blacklist modules by adding a, wait for it....  "blacklist modulename" entry to /etc/modprobe.d/blacklist  :D

---

### Post by Zyphrexi on 2007-04-18
thanks all

---

### Post by ahaslam on 2007-04-25
Hi, this has got me feeling like a n00b, it's so simple in Zenwalk, the entire list of modules was in a file called rc.modules and you just (un)comented the desired one(s). That file does not exist in Ubuntu & neither does the modprobe.conf mentioned in the above link. I do have have /etc/modules, however it only contains 3 irrelevant entrys.

Basicly I want to disable cpu scaling. The modules are shown in the kernel config but I can't find a reference to them:

> #
# CPU Frequency scaling
#
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=m
# CONFIG_CPU_FREQ_DEBUG is not set
CONFIG_CPU_FREQ_STAT=m
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=m
CONFIG_CPU_FREQ_GOV_USERSPACE=m
CONFIG_CPU_FREQ_GOV_ONDEMAND=m
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=m

#
# CPUFreq processor drivers
#
CONFIG_X86_POWERNOW_K8=m
CONFIG_X86_POWERNOW_K8_ACPI=y
# CONFIG_X86_SPEEDSTEP_CENTRINO is not set
CONFIG_X86_ACPI_CPUFREQ=m

I'd appreciate some further advice before I waste some time recompiling the kernel ;)

PS. the following blacklist didn't work:
> # stop cpu frequency scaling
blacklist acpi-cpufreq
blacklist powernow-k8

The modules are also not mentioned in the aliases file, though they do exist & operate :-k

---

