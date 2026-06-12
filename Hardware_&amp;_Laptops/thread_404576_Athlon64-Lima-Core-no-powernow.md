---
title: "Athlon64-Lima-Core-no-powernow"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by hphobbit on 2007-04-08
Problem: powernow not installing:
Ubuntu drapper-drake 386. 
CPU: Athlon64, 3800+, 1 core, 65nm, 45 Watt, Lima-Core.
Mainboard: Asrock AM2, NFORCE3-250: chipset revision 162, AGP.
BIOS: cool and quiet enabled. 
in "dmesg": powernow-k8: Processor cpuid 70ff1 not supported
in "cpuinfo": flags: fpu vme de pse tsc msr pae mce cx8 apic
                  sep mtrr pge mca cmov pat pse36 clflush
                  mmx fxsr sse sse2 syscall nx mmxext fxsr_opt
                  lm 3dnowext 3dnow pni cx16 lahf_lm
iin "cpuid":
Advanced Power Management Feature Flags
Has temperature sensing diode
Supports Frequency ID control
Supports Voltage ID control.

---

### Post by pd77 on 2007-05-17
Same problem here. Looks like the Lima core cpuid isn't listed in the powernow-k8 module yet.

[http://bugzilla.kernel.org/show_bug.cgi?id=8423](http://bugzilla.kernel.org/show_bug.cgi?id=8423)

---

