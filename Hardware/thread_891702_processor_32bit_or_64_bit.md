---
title: "processor 32bit or 64 bit?"
date: 2008-08-16
forum: Hardware
---

### Post by broncodriver on 2008-08-16
Can anyone tell me if this processor is 32 or 64 bit?

cpu family      : 15
model           : 4
model name      : Mobile Intel(R) Pentium(R) 4 CPU 3.33GHz
stepping        : 1
cpu MHz         : 3333.637
cache size      : 1024 KB
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
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est tm2 cid xtpr
bogomips        : 6667.53
clflush size    : 64

---

### Post by broncodriver on 2008-08-16
I think I found it. 32 bit

let me know if anyone finds otherwise

---

### Post by ljonesj on 2008-08-16
ok do u know if its prescott or cedar mill if its cedar mill its has the 64 bit instruction set

---

### Post by mschmoelzer on 2008-08-16
> **broncodriver said:**
> 
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est tm2 cid xtpr

Should be a 32 bit CPU. For a 64 bit CPU, /proc/cpuinfo would show the "lm" (Long Mode) flag.

---

