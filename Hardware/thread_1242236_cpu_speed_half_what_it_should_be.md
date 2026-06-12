---
title: "cpu speed half what it should be"
date: 2009-08-16
forum: Hardware
---

### Post by bootdoc on 2009-08-16
I am about to install JJ on a dell latitude D600.  
cat /proc/cpuinfo shows a pentium m 1.4 processor with a speed of 600Mgz.  I am running ubuntu off usb stick and man is it ever slow.  I have never seen a boot stick run this slow.  I read that the pentium M is made up of two 32 bit Pentium III procs with some P4 technology also built in.  cpuinfo only shows one processor.  I am guessing that one of the procs is bad.  Any ideas??

---

### Post by jkarcz on 2009-08-16
The 600mhz is Intel's speedstep.  I have a 1.7GHz and if I run something and cat the cpuinfo file, the speed does go up.

Running ubuntu from a USB is going to be slow.  The read/write speed usually isn't that great.

---

### Post by bootdoc on 2009-08-16
thanks for the reply.  I must say though that running ubuntu off of a usb stick has always been faster than CDROM.  It even runs faster the the native install on my machine.  

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 39
model name      : AMD Athlon(tm) 64 Processor 3700+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good pni lahf_lm
bogomips        : 2009.30
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

---

