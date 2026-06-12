---
title: "Why two processor entries?"
date: 2008-07-31
forum: General Help
---

### Post by dvfreelancer on 2008-07-31
Okay, this might be a stupid question, but I thought this box was single CPU P4.  But when I check the hardware, it shows two processor entries.  When run cpuinfo I get this:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 5
cpu MHz         : 2400.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est tm2 cid cx16 xtpr lahf_lm
bogomips        : 6408.20
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 5
cpu MHz         : 2400.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est tm2 cid cx16 xtpr lahf_lm
bogomips        : 6402.27
clflush size    : 64

Why is it showing a processor 0 and 1?  On another machine, an older AMD 2600, all I see is CPU 0.  The output above says CPU cores 1, but why the dual entries?

---

### Post by PmDematagoda on 2008-07-31
If your P4 processor is Hyper-Threading capable and if Hyper-Threading is turned on, then the one P4 processor acts(only acts!) like a dual-core processor to the OS.

---

### Post by jonian_g on 2008-07-31
Are you sure what's in the box?
Saying Cpucore:1 doesn't mean that the motherboard doesn't support 2 cpus. It just says that the cpu has 1 core.

---

### Post by dvfreelancer on 2008-07-31
The equipment inventory says "single cpu" and all I can see in the case without shutting it down is a giant cpu fan.  Hard to tell just by looking sometimes, but there is only one of them.  

It's just the development server.  If it bothers me that much I'll just see what the bios has to say or pull the fan and just look.  This is all academic anyway, I'm just trying not to shut it down.  

Right now it looks like PmDematagoda may be correct.  It's a pretty zippy box which is what made me curious in the first place.  Of course, that could just be because it doesn't run Windows. :)  Oh, snap!

---

