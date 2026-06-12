---
title: "Dual Core processor support"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by andkuh on 2007-06-02
Hi,

I know that this question has been answered before, but I have tried all the solutions and my kernel seems to be the right version and so on.

I have a Sony Vaio VGN-SZ1HP laptop, which has a Centrino Duo (Dual Core) Processor in it. When I installed Ubuntu 7.04, I got the dual core processor recognized as 2 processors (which it should be). However, I noticed yesterday that the processor is now recognized as a single processor. 

The response from the command uname -a is : Linux anku-laptop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

which indicates a SMP-aware kernel. However the response from cat /proc/cpuinfo is : 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1667.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pni monitor vmx est tm2 xtpr
bogomips        : 3337.49
clflush size    : 64


Which indicates just one core.

I know that this has worked earlier. I don't know when things changed, however I did install the new kernel image released the other week and I think that it stopped working then. I have also tried to boot back to the older kernel image, with the same results.

Does anyone know any solution to this problem. I would like to get both cores recognized by Linux.

Best regards,

Andréas

---

### Post by andkuh on 2007-06-04
Apparently it is the hardware that has changed itself. I cannot see both cores in windows either. However, the system seems to see both processors with Intel tools in windows. This is strange.

---

### Post by andkuh on 2007-06-04
Strangely enough, all I had to do was to reset my bios. Don't really understand that one. However, it was not an error in Ubuntu :)

---

