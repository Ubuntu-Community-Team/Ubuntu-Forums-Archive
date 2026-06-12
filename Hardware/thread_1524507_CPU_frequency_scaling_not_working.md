---
title: "CPU frequency scaling not working"
date: 2010-07-05
forum: Hardware
---

### Post by ascagnel on 2010-07-05
I have an older laptop, a Dell Precision M60, that I'd like to use in headless for a few light tasks (shared print server for 3 people, SSH server, and a testbed for web development).  Currently, its running Ubuntu Server 9.10 (32-bit).

The CPU frequency is stuck on its highest (2.00GHz), and I'm concerned that, since the laptop will be closed and stored out of the way, the speed will create too much heat and damage the hardware.  2.00GHz also pulls a lot of power unnecessarily.  How would I go about setting the CPU frequency to 600MHz (its lowest throttle)?  "sudo cpufreq-set -f 600000" and "sudo cpufreq-set -g powersave" don't do anything.

**Output of /proc/cpuinfo**
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 2.00GHz
stepping        : 6
cpu MHz         : 2000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips        : 3996.64
clflush size    : 64
power management:

**Output of cpufreq-info:**
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.00 GHz and 2.00 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
  cpufreq stats: 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:0.00%, 800 MHz:0.00%, 600 MHz:0.00%  (1560)

---

