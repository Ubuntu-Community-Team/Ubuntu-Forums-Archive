---
title: "Ubuntu not detecting all 3 cores"
date: 2008-09-08
forum: Hardware
---

### Post by gobeavs on 2008-09-08
I've got a Phenom X3 8450, but Ubuntu only seems to detect one of the cores. The system monitor only shows one CPU, and this is the output from cat /proc/cpuinfo (only one processor shown):

> processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 8450 Triple-Core Processor
stepping	: 3
cpu MHz		: 2100.149
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs ts ttp tm stc 100mhzsteps hwpstate
bogomips	: 4204.31
clflush size	: 64


But, lshw -C cpu shows this:

 >  *-cpu:0                 
       description: CPU
       product: AMD Phenom(tm) 8450 Triple-Core Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 3
       bus info: cpu@0
       version: 15.2.3
       slot: Socket AM2
       size: 2100MHz
       capacity: 2100MHz
       width: 64 bits
       clock: 200MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs ts ttp tm stc 100mhzsteps hwpstate
  *-cpu:1
       physical id: 4
       bus info: cpu@1
       version: 15.2.3
       size: 2100MHz
  *-cpu:2
       physical id: 5
       bus info: cpu@2
       version: 15.2.3
       size: 2100MHz


What is going on here? I'm using 32 bit Hardy, if that helps any. Thanks!

---

### Post by gobeavs on 2008-09-09
Bump? Anybody?

---

### Post by sjk44 on 2008-11-27
I am having a similar problem with AMD Quad core processor using Ubuntu 8.10.  Were you able to find a solution to your issue?  If so, can you please lead me in the right direction?  Thank you.

---

### Post by linux_tech on 2008-11-27
Have you tried this yet?
[http://ubuntuforums.org/showthread.php?t=928348](http://ubuntuforums.org/showthread.php?t=928348)

---

### Post by sjk44 on 2008-11-27
Thanks for the lead; I read the post but don't know what to do or learn as a result of reading it.  I'm very new to Ubuntu!  Only one core shows when I input cat /proc/cpuinfo:

stanleyk@shuttle:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9850 Quad-Core Processor
stepping	: 3
cpu MHz		: 2500.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs ts ttp tm stc 100mhzsteps hwpstate
bogomips	: 5005.02
clflush size	: 64

Do you have any idea what I should do next?  Thank you.

---

### Post by sjk44 on 2008-11-28
The problem of Ubuntu not recognizing the four cores of my AMD chip has apparently been resolved by the Linux kernal maintenance that I downloaded and applied today (11-28-2008).

Thank you.

---

