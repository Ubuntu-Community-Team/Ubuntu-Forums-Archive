---
title: "I have a triplecore 2.1ghz, cat/cpu says 1050mhz?"
date: 2009-11-08
forum: Hardware
---

### Post by binskipy2u on 2009-11-08
what gives.. here's the output for:

cat /proc/cpuinfo

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : AMD Phenom(tm) 8450 Triple-Core Processor
stepping        : 3                                        
cpu MHz         : 1050.000                                 
cache size      : 512 KB                                   
physical id     : 0                                        
siblings        : 3                                        
core id         : 1                                        
cpu cores       : 3                                        
apicid          : 1                                        
initial apicid  : 1                                        
fpu             : yes                                      
fpu_exception   : yes                                      
cpuid level     : 5                                        
wp              : yes                                      
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                   
bogomips        : 4200.37                                                                                             
TLB size        : 1024 4K pages                                                                                       
clflush size    : 64                                                                                                  
cache_alignment : 64                                                                                                  
address sizes   : 48 bits physical, 48 bits virtual                                                                   
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                  

processor       : 2
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 2
model name      : AMD Phenom(tm) 8450 Triple-Core Processor
stepping        : 3
cpu MHz         : 1050.000
cache size      : 512 KB
physical id     : 0
siblings        : 3
core id         : 2
cpu cores       : 3
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips        : 4200.26
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate



1. why does it only say 1050? (in ubuntu w/ubuntu tweak, it said the proper amount of ghz)
2. why does it only list 2 processors? when I have 3
3. should I be worried?
just wondering..

---

### Post by D-Sider on 2009-11-08
That pretty normal for 2 cores, but I'm not sure about 3.  For example, on my 2.16 Ghz Core2 Duo laptop, Windows and Linux both report 2 core with a clock speed of 1080 Mhz. Multiply that by 2 and you get the 2.16 Ghz.

So your 1050Mhz x 2 would make sense on 2 cores...

---

### Post by darkshadow on 2009-11-08
One strange thing is that is is supposed to start counting at 0 but yours is at 1 did you not scroll up enough when reading the output.

---

### Post by shazbut on 2009-11-08
1.  Cool'n Quiet is enabled, so if the cores are idle they will throttle back MHz/voltage to save energy/heat.  Load them up and run cat /proc/cpuinfo and you will see different numbers.
2.  The first core should be processor 0, so my guess is it scrolled off the screen...
3.  Not at all ;)

---

### Post by binskipy2u on 2009-11-08
yeah, i re-ran it.. there was a zero..
thanks, i googled some more.. and did the "current speed" command.. and it was 2100mhz..

thanks for the info

---

