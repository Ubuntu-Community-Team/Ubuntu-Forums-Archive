---
title: "cpufreq Celeron 550 2.0GHz on Hardy"
date: 2008-05-30
forum: Hardware
---

### Post by m-a-c on 2008-05-30
Hi!
I have an Acer TravelMate 5320 laptop with Intel Celeron 550 on 2.0 GHz and cpu scalling just won't work. I tried to load many modules but none of them doesn't work. Please help...Thanks!
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 22
model name	: Intel(R) Celeron(R) CPU          550  @ 2.00GHz
stepping	: 1
cpu MHz		: 1995.324
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3994.63
clflush size	: 64

---

### Post by stchman on 2008-05-30
> **m-a-c said:**
> Hi!
I have an Acer TravelMate 5320 laptop with Intel Celeron 550 on 2.0 GHz and cpu scalling just won't work. I tried to load many modules but none of them doesn't work. Please help...Thanks!
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 22
model name	: Intel(R) Celeron(R) CPU          550  @ 2.00GHz
stepping	: 1
cpu MHz		: 1995.324
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3994.63
clflush size	: 64

I don't believe the Celeron processors support frequency scaling.  I had a Celeron M 430 1.73GHz in my previous laptop and it did not support frequency scaling.

---

### Post by stream303 on 2008-05-30
While I'm not certain about the Celerons, I can say that on my G5 PPC box, the default powernowd doesn't seem to work, so I uninstalled it and installed *cpudyn* instead as a replacement.  Scaling works for me now..

---

### Post by stchman on 2008-05-30
> **stream303 said:**
> While I'm not certain about the Celerons, I can say that on my G5 PPC box, the default powernowd doesn't seem to work, so I uninstalled it and installed *cpudyn* instead as a replacement.  Scaling works for me now..

Here is a list from my experience of processors that support frequency scaling on the fly.

Athlon 64 (all makes)
Pentium D
Core Solo
Core Duo
Core 2 Duo

There may be more.

---

### Post by Private_Ops on 2008-05-30
> **stchman said:**
> 

Athlon 64 (all makes)


There may be more.

Does that include Opterons? (On the Desktop)

---

### Post by stchman on 2008-05-30
> **Private_Ops said:**
> Does that include Opterons? (On the Desktop)

I cannot say, the list of processors I have are ones that I have actually used.  I have never used an Opteron.

Easiest way is to boot up a LiveCD on an Opteron machine and se if it does.

---

### Post by miestrâ on 2008-05-31
Frequency scaling works on Celeron if you add "p4_clockmod" to your /etc/modules file.

---

### Post by m-a-c on 2008-06-02
> **miestrâ said:**
> Frequency scaling works on Celeron if you add "p4_clockmod" to your /etc/modules file.

I've tried that and it doesn't work...
Any more ideas?

---

### Post by BlueSkyNIS on 2008-06-02
I think celeron doesn't support spufreq. I looked at [http://processorfinder.intel.com/details.aspx?sSpec=SLA2E]("http://processorfinder.intel.com/details.aspx?sSpec=SLA2E") and also at [Intel Celeron M Processor on 65 nm process datasheet]("http://download.intel.com/design/mobile/datashts/31272604.pdf"), page 23, all other fields are marked RESERVED so it looks like it doesn't support it

---

