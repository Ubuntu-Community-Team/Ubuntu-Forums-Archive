---
title: "Ubuntu 9.10 not seeing both cores"
date: 2009-11-25
forum: Hardware
---

### Post by cepost on 2009-11-25
I'm very new to Ubuntu and Linux in general. I've installed 32 bit Ubuntu with gnome and compiz as my host system and also running VMware with an XP virtual machine. All works fine except that Ubuntu is only showing one core of my dual core processor. Any ideas as to what the problem is?

processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 23
model name : Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
stepping : 10
cpu MHz : 3000.183
cache size : 6144 KB
physical id : 0
siblings : 1
core id : 0
cpu cores : 1
apicid : 0
initial apicid : 0
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips : 6000.36
clflush size : 64
power management:

---

### Post by falconindy on 2009-11-25
What's the output of:
```
cat /sys/devices/system/cpu/{present,online,offline,possible}
```

---

### Post by cepost on 2009-11-27
cpost@cpost-desktop:~$ cat /sys/devices/system/cpu/{present,online,offline,possible}
0
0
1-7
0


I'm guessing 

present = 0
online = 0
offline = 1-7
possible = 0

This is an Intel dual core processor .. When I was running just windows XP on this system previously it saw both cores .. Ubuntu for some reason does not.
Any help would be greatly appreciated since I'm new to Ubuntu and really don't have a clue where to start to look for answers.

---

