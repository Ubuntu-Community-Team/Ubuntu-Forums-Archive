---
title: "Was my sony vaio shipped with the wrong cpu?"
date: 2011-04-06
forum: Hardware
---

### Post by linuxisgoed on 2011-04-06
I have bought a a laptop with the following cpu specifications :
**[SIZE=3]Sony EE3Z0E/BQ AMD Phenom II Triple-Core Processor P840 [/SIZE]**

 
ChipsetIntel AMD M880G
L2 cache1.5 MB
Processor clock speed 1900 MHz
Processor familyAMD Phenom II
Processor modelP840
more details available here: 
[http://www.saverstore.com/productinfo/product.aspx?d=1&product_id=20068477&rw=y](http://www.saverstore.com/productinfo/product.aspx?d=1&product_id=20068477&rw=y)
The side of the box confirms 1.9GHz


The problem is when I check in the terminal it says I have a 800Mhz processor !! 

Could they  be adding the three cpu's speed's together  (3x.800) ?? it does not give me 1.9GHz 

details below , any suggestions ?
ps: running 10:10 32 bit edition , 64 bit gave me audio problems



-VPCEE3Z0E:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 5
model name    : AMD Phenom(tm) II P840 Triple-Core Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 3
core id        : 0
cpu cores    : 3
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips    : 3790.67
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 5
model name    : AMD Phenom(tm) II P840 Triple-Core Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 3
core id        : 1
cpu cores    : 3
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips    : 3790.51
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 5
model name    : AMD Phenom(tm) II P840 Triple-Core Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 3
core id        : 2
cpu cores    : 3
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips    : 3790.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by searchfgold6789 on 2011-04-06
Could be. See what ```
sudo lshw
``` says.

---

### Post by coffeecat on 2011-04-06
The 800MHz you see from cpuinfo is because the processor wasn't under load and because of dynamic frequency scaling:

[http://en.wikipedia.org/wiki/Dynamic_frequency_scaling](http://en.wikipedia.org/wiki/Dynamic_frequency_scaling)

Start a CPU-intensive process and then try 'cat /proc/cpuinfo' again. With this AMD Athlon II Dual-Core M300 powered laptop I get 800MHz from cpuinfo when the CPU is not under load and 2000MHz when it is.

---

### Post by linuxisgoed on 2011-04-06
sudo lshw :
  *-cpu
          description: CPU
          product: AMD Phenom(tm) II P840 Triple-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 6
          bus info: cpu@0
          version: 15.5.3
          serial: N/A
          slot: N/A
          size: 800MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 200MHz

so happy days, you saved me the embarrassment of phoning Sony and telling them they shipped my laptop with the wrong cpu -dyamic frequency scaling. I won't forget that :)

---

