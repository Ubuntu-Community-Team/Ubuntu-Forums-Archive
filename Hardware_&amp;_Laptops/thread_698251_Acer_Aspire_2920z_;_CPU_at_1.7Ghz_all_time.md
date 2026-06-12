---
title: "Acer Aspire 2920z ; CPU at 1.7Ghz all time"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by ZardoZ84 on 2008-02-16
Hello. Few time ago, i bought a Acer Aspire 2920z notebook. I installed Ubuntu 7.10 without any problems .. even Wifi runs very well (thanks to ndiswrapper). But a bit ago, i installed gkrellm and i see that the speed of my CPU are all time at 1.7 Ghz ... not get more slower when it must. And this eat the battery much faster (And 1 h, when the battery should long 4 hours!)
 
The CPU is a Pentium Dual-Core, which Speepstep technology. 

I try to install powersave to control the CPU speed and using it to change to "Dynamic" mode and "powersave" mode .... nothing, the CPU is all time at 1,7Ghz. Even i try cpufreq-select , and nothing 

/proc/cpuinfo :
[INDENT]
    processor       : 0
    vendor_id       : GenuineIntel
    cpu family      : 6
    model           : 15
    model name      : Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz
    stepping        : 13
    cpu MHz         : 1729.275
    cache size      : 1024 KB
    physical id     : 0
    siblings        : 2
    core id         : 0
    cpu cores       : 2
    fdiv_bug        : no
    hlt_bug         : no
    f00f_bug        : no
    coma_bug        : no
    fpu             : yes
    fpu_exception   : yes
    cpuid level     : 10
    wp              : yes
    flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
    bogomips        : 3462.25
    clflush size    : 64[/INDENT]

I try to load the nodule speedstep_centrino (which sudo), i get this :

[INDENT]
    FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device[/INDENT]

---

### Post by 444 on 2008-02-16
The module is called acpi-cpufreq.

---

### Post by ZardoZ84 on 2008-02-17
I( load these module, and not works ... powersave say that speedstepping not is supported.

---

### Post by Yellow Pasque on 2008-02-17
Please run:
```
cpufreq-info
dmesg | grep speedstep
```

Off-topic: does /proc/cpuinfo show your other core (processor: 1)?

---

### Post by ZardoZ84 on 2008-02-18
/proc/cpuinfo show my other core :P

cpufreq-info :
[INDENT]cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 800 MHz and 1.73 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 800 MHz and 1.73 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.[/INDENT]


dmesg | grep speedstep show nothing

---

### Post by Yellow Pasque on 2008-02-18
Obviously, your CPU is not stuck on 1.7 GHz.
> The governor "powersave" may decide which speed to use within this range.
current CPU frequency is 800 MHz.

Try this for a less conservative frequency governor:
```
sudo cpufreq-set -g ondemand
```

---

### Post by Yellow Pasque on 2008-02-18
Ah, I see you already tried cpufreq-set, but are having problems with gkrellm. Was the above result of cpuinfo from after you uninstalled gkrellm?

---

### Post by ZardoZ84 on 2008-02-19
Cool .. I now see that a previus post that i said not there is ... Ok so i should rewrite it.

> 

I( load these module, and not works ... powersave say that speedstepping not is supported.


It's interesting, i installed cpufrequtils, and it show me that the CPU are running at 800Mhz when a Gkrellm plugin show me that the CPU are at 1700. Later, i put on the Gnome panel applet that show the CPU frecuency, and it show me that the CPU are working at 800. Even in /proc/cpuinfo show me that are at 800 Mhz. More ... even i see that if a put charge on the cpu (via cpuburn), the CPU frecuency changes quickly to 1,7 Ghz in the applet, cpufrequtils and in /prco/cpuinfo. Looks that CPU speed plugin of Gkrell not are working very well which this hardware ( I have a desktop pc wich a Athlon X2, and in this case this plugin works well).



I not uninstalled gkrellm or his plugin (but i deactivate that plugin). These cpuinfo result was which gkrell working.

However looks that the battery charged time not are too long, 2 hours ...( so looks that ACPI-cpufreq are working, before  was around a 1 hour), when the battery life in Vista are around 3~4 hours .... I trying to apply some tips of "lesswats" page to see if really works.

---

### Post by ZardoZ84 on 2008-02-21
I find this : 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120759](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120759)

Looks that there a problem speedstep-centrino module which this version of Kernel and/or is that speedstep-centrino is deprecated

---

