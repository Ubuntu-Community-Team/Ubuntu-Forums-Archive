---
title: "Pentium 4M (SL726) not supported by cpufreq?"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by bendowling on 2006-01-05
Hi,

I have a Pentium 4M running in my desktop, it's a mobile processor though so I though it might be better to post this on the laptop forum. My problem is that I cannot get it to run at it's full 3.06GHz, only the power saving mode of 1.6GHz.

Whenever I try to install a cpufreq module I get a No device error. I've tried all of the speedstep modules and the acpi one, but they all give the same error, no device found. The processor I have is an SL726 ([http://processorfinder.intel.com/scripts/details.asp?sSpec=SL726)](http://processorfinder.intel.com/scripts/details.asp?sSpec=SL726)). For some reason it identifies itself as a "Genuine Intel(R) CPU 3.06GHz" and not a mobile P4. Having done some searching on this I found that the speedstep-lib module does some checking on the cpuid, so I edited that module and recompiled the kernel and still no luck. When I try to install the p4-clockmod module it does now say 'P4M device found...should use speedstep-ich instead' before bailing out, but still gives the same result in the end.

Here is my /proc/cpuinfo output
[FONT="Courier New"]
bmd@nemesis:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Genuine Intel(R) CPU 3.06GHz
stepping        : 9
cpu MHz         : 1600.365
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 3153.92
[/FONT]

Does anyone have any ideas on how I could get this to run at 3.06GHz? 
Thanks in advance,

Ben

---

### Post by 23meg on 2006-01-05
Is powernowd running? Try killing it with ```
sudo killall powernowd
``` if it's running and see if the speed jumps to full.

---

### Post by bendowling on 2006-01-06
No it's not running, that's the problem - I can't get it to run because I can't get any drivers installed to control the processor speed. It defaults to the slower 1.6GHz, and I need the drivers to tell it to run at the full 3.06GHz.

If I try to run powernowd it just tells me that cpu frequency scaling is not available.

---

