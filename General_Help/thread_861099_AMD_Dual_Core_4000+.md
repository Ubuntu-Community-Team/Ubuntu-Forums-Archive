---
title: "AMD Dual Core 4000+"
date: 2008-07-16
forum: General Help
---

### Post by Ultima88 on 2008-07-16
Hi. Im new to ubuntu and recently just installed ubuntu into my pc. i noticed it running very slowly and after some searching in the net, i found this command "cat /proc/cpuinfo". i tried it and notice that even though im using a dual core processor, it only states 1 core. In system monitor, it only shows 1 core and it is usually 100%. Im currently using Ubuntu 8.04 x86. How do i "activate" the second core? Please explain in simple terms as im new to ubuntu and dont understand what is root user etc. lol. thanks



ctyc@xUltimAx-PC1:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping	: 1
cpu MHz		: 1800.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1    <======= Why is this 1?
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips	: 3719.08
clflush size	: 64

---

### Post by Habbit on 2008-07-16
Does it show only one "processor" entry or maybe two entries (processor:0 and processor:1) with one core each? I have a Core 2 Duo T8100 and it shows as two processors.

---

### Post by Ultima88 on 2008-07-16
Do you mean this?

[[IMG]http://img225.imageshack.us/img225/3601/75035757xo9.th.jpg[/IMG]](http://img225.imageshack.us/my.php?image=75035757xo9.jpg)

notice the usuage is usually 100%. i am not running any cpu-intensive things.

---

### Post by Habbit on 2008-07-16
Hmm... I meant the /proc/cpuinfo output, but I noticed that even when my CPU shows as two "processor" entries, it notices them as two cores in the same physical CPU: ```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping        : 6
cpu MHz         : 800.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida
bogomips        : 4194.83
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping        : 6
cpu MHz         : 800.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida
bogomips        : 4189.56
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

It would be strange, but maybe you have disabled the second core in the BIOS or the motherboard. WRT the 100% usage, run the "top" program and look at what's eating the CPU.

---

