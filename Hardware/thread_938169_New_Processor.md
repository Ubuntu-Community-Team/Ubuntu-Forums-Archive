---
title: "New Processor"
date: 2008-10-04
forum: Hardware
---

### Post by brianhoglan on 2008-10-04
I'm not sure if this is a stupid question or not, but I am wondering what I need to do if I want to upgrade my processor.  Currently I have an AMD Athlon 64 X2 Dual Core.  I am thinking about upgrading to a Quad-Core Phenom.  Can I just swap out the processor or do I need to rebuild the kernel?  I have the 64bit distro installed currently.  Here's some info from the computer:

> 
cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2045.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2045.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps


and

> 
brian@brian-desktop:~$ uname -a
Linux brian-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux



Thanks for your help

---

### Post by lian1238 on 2008-10-04
I don't think your laptop was built for a quad core...

---

### Post by cariboo on 2008-10-04
You didn't mention what type of motherboard you have, but check with the manufacturers web site to see if you mothrboard is compatible with a quad core cpu.

After looking at your output of cat /proc/cpuinfo, are you running some sort of throttling software, or are you underclocking your cpu? That looks mighty slow for an AMD 5600+ cpu. Here is a snippet from my 3800+

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 2009.140
cache size	: 512 KB
```

Jim

---

### Post by brianhoglan on 2008-10-04
I have a Gigabyte GA-NA69GM-S2H motherboard.  As far as throttling/underclocking, I don't believe so.  I am running BOINC, and I am going to look into that and see if it might be throttling somehow, but I haven't purposely done anything.

---

### Post by lian1238 on 2008-10-04
**cat /proc/cpuinfo** produces different output depending on the current state of the CPU.

---

### Post by brianhoglan on 2008-10-05
Ok, so after looking around, I'm not finding a whole lot... How can I tell if I am somehow throttling/underclocking?

---

### Post by TheLions on 2008-10-05
> **cariboo907 said:**
> You didn't mention what type of motherboard you have, but check with the manufacturers web site to see if you mothrboard is compatible with a quad core cpu.

After looking at your output of cat /proc/cpuinfo, are you running some sort of throttling software, or are you underclocking your cpu? That looks mighty slow for an AMD 5600+ cpu. Here is a snippet from my 3800+

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 2009.140
cache size	: 512 KB
```

Jim

he is having Cool&quiet enabled

@brianhoglan

is this your mainboard:
[http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=2579](http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=2579) ???

if it is, before installing new CPU update your BIOS and everthing should be fine.

---

### Post by brianhoglan on 2008-10-06
Oh thank you!  I missed that setting in the BIOS.  I turned it off, now here is what I get:
> 
brian@brian-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping	: 2
cpu MHz		: 2906.611
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 5933.24
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping	: 2
cpu MHz		: 2906.611
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 5813.18
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

So now it's working so much better, I didn't even have to re-flash it.  So again, thanks for your help.


Brian

---

### Post by TheLions on 2008-10-07
before installing QuadCore you should flash your BIOS

---

### Post by brianhoglan on 2008-10-07
Ok, and then after it's installed do I need to do anything different in the OS?  Specifically, will I need to rebuild my kernel?  I just know that Windows tends to get a little wonky when hardware gets changed.

---

### Post by TheLions on 2008-10-07
you don't need to do anything to OS

---

