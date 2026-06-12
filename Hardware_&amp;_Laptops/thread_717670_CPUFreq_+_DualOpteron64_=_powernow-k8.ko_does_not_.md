---
title: "CPUFreq + DualOpteron64 = powernow-k8.ko does not want to load"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by sheen on 2008-03-07
Hi all,

I'm on Gutsy with a Dual Opteron 64 ( k8 ) on DFI Nforce4 UltraD, I'm trying to use Cpufreq-utils.
Cool and Quiet is enabled in Bios (latest Bios), I've read the wiki about cpufreq-utils but modprobe does not work.

Here it is my output :

> 
sheen@Ubuntu:~$ uname -a
Linux Ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
> sheen@Ubuntu:~$ cat /proc/cpuinfo | grep model
processor       : 0
model name      : Dual Core AMD Opteron(tm) Processor 165
processor       : 1
model name      : Dual Core AMD Opteron(tm) Processor 165


> 
sheen@Ubuntu:~$  lsmod | grep cpu
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand


> 
sheen@Ubuntu:~$ cpufreq-info 
Check CPU 0 :
  No cpufreq drivers known for this CPU
Check CPU 1 :
  No cpufreq drivers known for this CPU


> 
sheen@Ubuntu:~$ dmesg | grep powernow
[   37.876000] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 165    processors (version 2.00.00)
[   37.876000] powernow-k8: MP systems not supported by PSB BIOS structure
[   37.876000] powernow-k8: MP systems not supported by PSB BIOS structure
[  127.024000] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 165    processors (version 2.00.00)
[  127.024000] powernow-k8: MP systems not supported by PSB BIOS structure
[  127.024000] powernow-k8: MP systems not supported by PSB BIOS structure
[  409.176000] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 165    processors (version 2.00.00)
[  409.176000] powernow-k8: MP systems not supported by PSB BIOS structure
[  409.176000] powernow-k8: MP systems not supported by PSB BIOS structure
[ 1214.072000] powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 165    processors (version 2.00.00)
[ 1214.072000] powernow-k8: MP systems not supported by PSB BIOS structure
[ 1214.072000] powernow-k8: MP systems not supported by PSB BIOS structure


> 
sheen@Ubuntu:~$ sudo modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device

                                  
> 
sheen@Ubuntu:~$ locate powernow-k8.ko
/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko



It appears there is a similar bug on a different kernel : [https://launchpad.net/linux/+bug/33116](https://launchpad.net/linux/+bug/33116)


Please help me, I don't know what I can do =(

---

### Post by Crabstick on 2008-05-27
Hi,

I had the same issues with powernow. I have Gigabyte GA-M55S board with Athlon X2 3800+ and 64-bit Ubuntu server 8.04 (2.6.24 kernel). I'm used to run my machine overclocked so didn't remember to reset my BIOS settings before installing the distribution. I got that same "not supported by BIOS" error.

When I reset my overclocking settings to all default values (FSB, HT-link, memory settings) powernowd and all related modules started working like a charm.

Anyone running with custom clock settings in BIOS, revert to default values and try again.

BR,
Ville

---

