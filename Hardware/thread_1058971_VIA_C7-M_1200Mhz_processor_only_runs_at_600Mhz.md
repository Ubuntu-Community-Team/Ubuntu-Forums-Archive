---
title: "VIA C7-M 1200Mhz processor only runs at 600Mhz"
date: 2009-02-03
forum: Hardware
---

### Post by geoffrian on 2009-02-03
I am running Ubuntu 8.10 on my Sylvania gNetbook.  It runs a little slow.  Here is the output of cat /proc/cpuinfo.

processor	: 0
vendor_id	: CentaurHauls
cpu family	: 6
model		: 13
model name	: VIA C7-M Processor 1200MHz
stepping	: 0
**cpu MHz		: 599.981**
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx up pni est tm2 xtpr rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
bogomips	: 1199.96
clflush size	: 64
power management:

---

### Post by geoffrian on 2009-02-03
I've tested the computer on gOS which is based on Ubuntu, DSL, and SUSE and all say 599.900Mhz so I think it is a kernel issue.  I do not own Windows (now do I want to) so I can not test that to see what it says.  DSL uses the 2.4.31 kernel which is years old so I am not sure where to look for more info.  No one else with a VIA issue?  --Ryan

---

### Post by willreed on 2009-02-04
yep same here. I haven't found any easy answers to this.

---

### Post by geoffrian on 2009-02-07
Found the solution.  Go to this site and follow the instructions:

[http://forum.netbookuser.com/viewtopic.php?id=668](http://forum.netbookuser.com/viewtopic.php?id=668)

-Ryan

---

