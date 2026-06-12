---
title: "Lost processor"
date: 2008-08-31
forum: Hardware
---

### Post by Frogling on 2008-08-31
I bought a computer about a year ago ( less I think ) and quickly installed Ubuntu on it.  I am currently running 8.04.  Things were going well for a while, things were fast, pretty and productive.  Recently however it has stopped recognizing one of my processors ( I have a AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ )

cat /proc/cpuinfo returns 

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping	: 1
cpu MHz		: 2100.000
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
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips	: 4332.58
clflush size	: 64
```

I guess I am posting this to see if this ( hopefully ) is a software problem rather then a broken cpu.  Anyone have any ideas?

---

### Post by hoarycripple on 2008-08-31
Are you using the SMP kernel? 

Check the output of:

```
uname -a
```

---

### Post by Frogling on 2008-08-31
uname -a
Linux frogling-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

---

