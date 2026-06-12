---
title: "amd64 dual core can not enable hyperthreading"
date: 2009-02-04
forum: Hardware
---

### Post by maddocks on 2009-02-04
I have a hp tx1410us (a tx1000 derivative) and i have tried enabling hyperthreading by adding ht=on to the following line in menu.lst

# kopt=root=UUID=4c65d231-9d98-4077-bf77-13828f4a744a ro ht=on

and running update-grub. But it still shows only 2 processors in any program that i use to look. heres what cat /proc/cpuinfo shows

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-64
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1595.69
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-64
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1595.69
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

im running Intrepid Ibex 64bit version with kernel 2.6.27-11-generic x86_64

my bios does not have the option to enable or disable hyperthreading so i pray that isnt the problem. I have read sum people have had problems with acpi and apic on the tx1000 series but i have not. Any help would be greatly appreciated, thank you.

---

### Post by TheLions on 2009-02-04
you got AMD, it dosent support hyperthreading, only intel chips support it

[http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

---

### Post by maddocks on 2009-02-04
oops sorry i thought the HT in the cat /proc/cpuinfo stood for hyperthreading but it must mean hypertransport. again sorry

---

