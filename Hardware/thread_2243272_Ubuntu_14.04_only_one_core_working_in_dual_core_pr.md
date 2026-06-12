---
title: "Ubuntu 14.04 only one core working in dual core processor"
date: 2014-09-07
forum: Hardware
---

### Post by Dean Coffey on 2014-09-07
Thanks in advance for any assistance I receive.

I have a Dell Vostro 200 desktop computer with an Intel E2160 @ 1.8 GHz processor, which is dual core. However, System Monitor only indicates one core is being used, as does cat /proc/cpuinfo if I'm reading it correctly:

dean@neuromancer:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
stepping    : 13
microcode    : 0xa1
cpu MHz        : 1800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
bogomips    : 3590.97
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

From my limited knowledge, the kernel seems to be appropriate for this processor:

dean@neuromancer:~$ uname -a
Linux neuromancer 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

However, if I execute dmesg | grep "smp", I receive the following, which I'm sure is where the issue lies or is at least related:

dean@neuromancer:~$ dmesg | grep "smp"
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.076625] smpboot: CPU0: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz (fam: 06, model: 0f, stepping: 0d)
[    5.804156] smpboot: CPU1: Not responding
[    5.804173] smpboot: Total of 1 processors activated (3590.97 BogoMIPS)
[    0.016000] Kernel panic - not syncing: smp_callin: CPU1 started up but did not get a callout!

This is a clean install of Ubuntu 14.04 from an image I downloaded shortly after its release.  While using the disc live, both cores show as being operational.  Also, to the best of my knowledge, the settings in my BIOS should be correct.

If any other information is needed to resolve this issue, please let me know. I will gladly provide any info I am able tol.

Any help with this issue will be greatly appreciated. I have been attempting to find a solution on my own, but I am not having much luck searching the forums--the amount of information is overwhelming, and often unrelated. I'm certain this is due to my poor choice of search terms.  :(

---

### Post by weatherman2 on 2014-09-07
Although it seems to make little sense (I would need to see an explanation broken down to understand it), several people with the error message "smpboot: CPU1: Not responding" mention that unplugging a certain USB device solved the problem.  Here for example:

[https://bbs.archlinux.org/viewtopic.php?id=159268](https://bbs.archlinux.org/viewtopic.php?id=159268)

You might try that.  Or even try juggling which USB devices are plugged into which ports.  (Do you have a USB hub?)

You might also see if Dell has a newer BIOS available for this computer.  Installing the BIOS without Windows may not be simple, however, and not recommended unless you really know what you are doing.  (You can "brick" a computer with a bad BIOS flash, so it's slightly risky.)  If you can still boot Windows, a BIOS update should be routine provided you download the correct BIOS update file.

---

### Post by ibjsb4 on 2014-09-07
> **weatherman2 said:**
> Although it seems to make little sense (I would need to see an explanation broken down to understand it), several people with the error message "smpboot: CPU1: Not responding" mention that unplugging a certain USB device solved the problem.
That could explain the two hotplug cpus.
Here is what I get on a two core setup.
```
uname -a
Linux u14 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
```
dmesg | grep "smp"
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.067457] smpboot: CPU0: Intel(R) Xeon(R) CPU           X5650  @ 2.67GHz (fam: 06, model: 2c, stepping: 02)
[    0.079570] smpboot: Total of 2 processors activated (10646.96 BogoMIPS)
```

---

### Post by Dean Coffey on 2014-09-07
> **weatherman2 said:**
> Although it seems to make little sense (I would need to see an explanation broken down to understand it), several people with the error message "smpboot: CPU1: Not responding" mention that unplugging a certain USB device solved the problem.  Here for example:

[https://bbs.archlinux.org/viewtopic.php?id=159268](https://bbs.archlinux.org/viewtopic.php?id=159268)

You might try that.  Or even try juggling which USB devices are plugged into which ports.  (Do you have a USB hub?)

We have a winner--thank you!

I unplugged all of my USB devices (none of which was a hub), except for my Logitech trackball that has never given me problems, and rebooted. Using the trackball I logged into guest account and checked system monitor. It showed both cores working normally. Being suspcious of my keyboard, I plugged in all other USB devices *except* my keyboard and repeated the reboot. Still both cores working. Finally, I plugged in the keyboard and rebooted--only one core, and the boot process took a noticeably longer period of time to complete.

So, as a temporary workaround, I unplugged my keyboard, rebooted, and waited until I reached the login prompt, then plugged in the keyboard. Both cores working, and everything seems fine.  :D

Thank you very much weatherman2, your help is greatly appreciated.

---

### Post by weatherman2 on 2014-09-07
No problem.  I hate little nagging problems like this.

You might try again later after a few kernel updates - or when 14.04.2 comes out (newer kernel version) try that as well.

---

