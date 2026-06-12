---
title: "My Asus Eee Box is dual core??"
date: 2009-02-13
forum: Hardware
---

### Post by CaptSaltyJack on 2009-02-13
If I do cat /proc/cpuinfo, I get this:

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 xtpr lahf_lm
bogomips	: 3215.95
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 xtpr lahf_lm
bogomips	: 4746.13
clflush size	: 64
power management:

```

I have the Asus Eee Box B202, just bought it the other day.  Is this a dual core Atom N270??

---

### Post by kerry_s on 2009-02-13
i think it's hyper-threading.

---

### Post by jespdj on 2009-02-13
> **CaptSaltyJack said:**
> I have the Asus Eee Box B202, just bought it the other day.  Is this a dual core Atom N270??
There is no dual-core Atom N270 and your output clearly says:
> cpu cores	: 1
According to [the specs](http://processorfinder.intel.com/details.aspx?sSpec=SLB73) the N270 has hyper-threading, that's why you see two sets of output.

---

### Post by CaptSaltyJack on 2009-02-13
Ahh yes, I missed that detail.  Thanks!

---

