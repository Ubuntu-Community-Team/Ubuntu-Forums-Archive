---
title: "cpufreqd with toshiba tecra 8000"
date: 2004-11-23
forum: Hardware &amp; Laptops
---

### Post by buellman on 2004-11-23
hi!

i try to get my notebook working with cpufreqd but dmesg shows me something like: no cpufreq interface found. ok... that seems to be a problem with my kernel? i use the stock ubuntu-kernel 2.6.8-3-1-686. 

how can i find out witch of the following modules should have been loaded:

CONFIG_X86_POWERNOW_K6=m
CONFIG_X86_POWERNOW_K7=m
CONFIG_X86_POWERNOW_K8=m
CONFIG_X86_GX_SUSPMOD=m
CONFIG_X86_SPEEDSTEP_CENTRINO=m
CONFIG_X86_SPEEDSTEP_CENTRINO_TABLE=y
CONFIG_X86_SPEEDSTEP_CENTRINO_ACPI=y
CONFIG_X86_SPEEDSTEP_ICH=m
CONFIG_X86_SPEEDSTEP_SMI=m
CONFIG_X86_P4_CLOCKMOD=m
CONFIG_X86_SPEEDSTEP_LIB=m
CONFIG_X86_SPEEDSTEP_RELAXED_CAP_CHECK=y
CONFIG_X86_LONGRUN=m
CONFIG_X86_LONGHAUL=m

i mean there is everything compiled as module so it must be something different. do i have to add some other "features" by compiling the kernel by myself or should the stock 686-kernel work just as it is and i do something different wrong?

any ideas?

greets. buellman

ps: martin@lightning:~ $ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 5
model name : Pentium II (Deschutes)
stepping : 2
cpu MHz : 120.111
cache size : 512 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips : 163.32

the cpu steped down. i dont know why because cpufreqd could not work because of the "no cpufreq interface found"-thing or am i wrong? my notebook was low on battery before it steped down... but after plugin in the ac it doesnt step up again :-/ very mystic to me... i dont understand the whole thing.

---

### Post by Magneto on 2004-11-23
[QUOTE=buellman]hi!


the cpu steped down. i dont know why because cpufreqd could not work because of the "no cpufreq interface found"-thing or am i wrong? my notebook was low on battery before it steped down... but after plugin in the ac it doesnt step up again :-/ very mystic to me... i dont understand the whole thing.[/QUOTE]
 u have a P2?  I know 10 of those modules won't work for it and I didnt know you could use cpufreqd with that old a processor

---

### Post by buellman on 2004-11-23
hi!

yep... its a pentium 2. you don't think i could get this damn cpufreqd to work? hmmm... that would not be so good but at least it would also not be a problem :-)
i wonder if cpufreqd would help me anyways... i mean 266mhz or 120mhz... should not help to have longer battery-time... maybe it would be cooler. who knows? :-)

i'm happy enough that my notebook works with ubuntu without to much problems. sound was a bit hard but in the end it works :-)

good night. buellman

---

