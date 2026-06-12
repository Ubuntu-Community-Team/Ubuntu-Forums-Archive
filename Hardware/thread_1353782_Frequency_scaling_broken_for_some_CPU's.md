---
title: "Frequency scaling broken for some CPU's?"
date: 2009-12-13
forum: Hardware
---

### Post by Ivo_Wever on 2009-12-13
Judging from bug reports and other forum threads, it seems that frequency scaling support is broken for some CPU's. The issue is not easy to understand, as some things have changed over the last few kernel releases and much of the advice is therefore not relevant anymore. For instance, when searching for these kinds of issues, there is much talk about kernel modules that should be loaded, but in the current Karmic kernel, these have been incorporated in the kernel and should thus be available automatically.

My issue: I have an Intel E6300 CPU and no frequency scaling support. The cpufreq packages are installed, but as cpufreq-info says:

analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

This isn't strange, because the required entries in /sys, like /sys/devices/system/cpu/cpu0/cpufreq, are simply not there. However, these should have been created by the kernel, when detecting the CPU and noting it is capable of frequency scaling. However, I have not been able to find bug reports indicating that either Ubuntu or the linux kernel devs are aware of this fact. It seems everyone blames it on the few people reporting the issue and that's that. Can someone verify that this is indeed a widespread problem? Is it being looked into and are there relevant bugreports that I've overlooked, or should I start one, either at Ubuntu or over at the linux kernel bugs?

---

### Post by Ivo_Wever on 2009-12-14
OK, the problem was that ACPI wasn't enabled automatically and required acpi=force as a boot parameter.

---

