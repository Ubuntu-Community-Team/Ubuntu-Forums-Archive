---
title: "cpu info"
date: 2012-06-26
forum: Hardware
---

### Post by mrmoreland on 2012-06-26
[COLOR=black][FONT=Tahoma]Hi there, [/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]I&#8217;m looking for confirmation on what architecture my CPU is, whether its 32bit or 64bit..[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]After looking at various utils, I&#8217;m still confused, I believe it to be a P4 dual core, 64bit, with 32bit OS installed, can some one please confirm?[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]uname -a shows:[/FONT][/COLOR]
[FONT=Tahoma][COLOR=black]Linux Ubuntu 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 athlon i386 GNU/Linux[/COLOR][/FONT]
 
[COLOR=black][FONT=Tahoma]-----------------------------------------------------[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]lscpu shows:[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Architecture: i686[/FONT][/COLOR]
[FONT=Tahoma][COLOR=black]CPU op-mode(s): 32-bit, 64-bit[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]Byte Order: Little Endian[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]CPU(s): 2[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]On-line CPU(s) list: 0,1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]Thread(s) per core: 1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]Core(s) per socket: 2[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]Socket(s): 1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]Vendor ID: AuthenticAMD[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]CPU family: 20[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]Model: 1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]Stepping: 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]CPU MHz: 800.000[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]BogoMIPS: 3199.90[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]Virtualisation: AMD-V[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]L1d cache: 32K[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]L1i cache: 32K[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]L2 cache: 512K[/COLOR][/FONT]
 
[COLOR=black][FONT=Tahoma]-----------------------------------------------------[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]cat /proc/cpuinfo shows[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]processor : 0[/FONT][/COLOR]
[FONT=Tahoma][COLOR=black]vendor_id : AuthenticAMD[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cpu family : 20[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]model : 1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]model name : AMD E-350 Processor[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]stepping : 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]microcode : 0x5000028[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cpu MHz : 800.000[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cache size : 512 KB[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]physical id : 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]siblings : 2[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]core id : 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cpu cores : 2[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]apicid : 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]initial apicid : 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]fdiv_bug : no[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]hlt_bug : no[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]f00f_bug : no[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]coma_bug : no[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]fpu : yes[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]fpu_exception : yes[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cpuid level : 6[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]wp : yes[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]bogomips : 3199.83[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]clflush size : 64[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cache_alignment : 64[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]address sizes : 36 bits physical, 48 bits virtual[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]power management: ts ttp tm stc 100mhzsteps hwpstate[/COLOR][/FONT]
[COLOR=black][FONT=Tahoma]processor : 1[/FONT][/COLOR]
[FONT=Tahoma][COLOR=black]vendor_id : AuthenticAMD[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cpu family : 20[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]model : 1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]model name : AMD E-350 Processor[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]stepping : 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]microcode : 0x5000028[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cpu MHz : 1600.000[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cache size : 512 KB[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]physical id : 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]siblings : 2[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]core id : 1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cpu cores : 2[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]apicid : 1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]initial apicid : 1[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]fdiv_bug : no[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]hlt_bug : no[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]f00f_bug : no[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]coma_bug : no[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]fpu : yes[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]fpu_exception : yes[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cpuid level : 6[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]wp : yes[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]bogomips : 3199.90[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]clflush size : 64[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]cache_alignment : 64[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]address sizes : 36 bits physical, 48 bits virtual[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]power management: ts ttp tm stc 100mhzsteps hwpstate[/COLOR][/FONT]
 
[COLOR=black][FONT=Tahoma]Thanks[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]Ian[/FONT][/COLOR]

---

### Post by sudodus on 2012-06-26
uname -a shows:
 Linux Ubuntu 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 athlon i386 GNU/Linux

(32-bit system with pae to manage lots of ram)

cat /proc/cpuinfo shows
model name : AMD E-350 Processor
cpu cores : 2
clflush size : 64
cache_alignment : 64

(It is not a P4, It's an AMD E-350. I think this is 64-bit architecture)

I use ```
sudo lshw -class cpu
``` to print the cpu specs. Try that to confirm by posting the output of this command!

---

### Post by drmrgd on 2012-06-26
The uname -a will just tell you about the kernel, but not about the actual CPU.  I believe you're running a 32-bit kernel here.

Looking at the cpuinfo, though, the fact that see 'lm' in the flags section indicates "Long Mode", which is indicative of a 64-bit processor.

---

### Post by mrmoreland on 2012-06-26
Hi thans for the replies, 
 
lshw -class cpu shows....

  *-cpu:0
       description: CPU
       product: AMD E-350 Processor
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 4
       bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
       version: 15.1.0
       serial: To Be Filled By O.E.M.
       slot: CPU 1
       size: 1600MHz
       capacity: 1600MHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter cpufreq
       configuration: cores=2 enabledcores=2
  *-cpu:1
       physical id: 1
       bus info: [EMAIL="cpu@1"]cpu@1[/EMAIL]
       version: 15.1.0
       size: 1600MHz
       capacity: 1600MHz
       capabilities: cpufreq

Thanks
 
Ian

---

### Post by sudodus on 2012-06-26
> **mrmoreland said:**
> Hi thans for the replies, 
 
lshw -class cpu shows....

  *-cpu:0
       description: CPU
       product: AMD E-350 Processor
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 4
       bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
       version: 15.1.0
       serial: To Be Filled By O.E.M.
       slot: CPU 1
       size: 1600MHz
       capacity: 1600MHz
       [COLOR="Red"]width: 64 bits[/COLOR]
       clock: 100MHz
       capabilities: [COLOR="red"]x86-64[/COLOR] boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter cpufreq
       configuration: cores=2 enabledcores=2
  *-cpu:1
...
Yes it is a 64-bit computer, so you can run both 32-bit Ubuntu and 64-bit Ubuntu :-)

---

### Post by mrmoreland on 2012-06-26
OK, thank you for your help.. back to the ubuntu downloads this time double checking the iso i download......
 
Cheers :)

---

### Post by sudodus on 2012-06-26
You are welcome :-)

and please click **Thread Tools** at the top of this page to mark this thread as SOLVED.

---

