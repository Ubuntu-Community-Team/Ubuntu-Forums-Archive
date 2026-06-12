---
title: "BIOS says 16 GB but ubantu only reconizes 1 GB (922 MB)"
date: 2016-06-12
forum: Hardware
---

### Post by vishnu11 on 2016-06-12
BIOS says 16 GB (installed 2X8 GB pcs) but Ubuntu recognizes only 922 MB.

As suggested in below, I cleaned connectors and reinstalled RAM pcs. 
[http://ubuntuforums.org/showthread.php?t=1808226](http://ubuntuforums.org/showthread.php?t=1808226)  

**uname -i** : output is **x86_64**

Below is '***lshw***' command snippet 

*-core[INDENT]        description: Motherboard
       physical id: 0
[/INDENT]
      *-memory
          [INDENT]description: System memory
          physical id: 0
          size: 922MiB
[/INDENT]
      *-cpu
          [INDENT]product: Intel(R) Core(TM) i5-4230U CPU @ 1.90GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp de tsc msr pae mce cx8 apic sep mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx x86-64 constant_tsc rep_good nopl nonstop_tsc eagerfpu pni pclmulqdq monitor est ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm ida arat epb pln pts dtherm fsgsbase bmi1 avx2 bmi2 erms xsaveopt
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0b
          width: 32 bits
          clock: 33MHz
[/INDENT]
 
Any pointers is appreciated !

---

### Post by ajgreeny on 2016-06-12
What does the command ```
free -m
``` show you?
If you're using ubuntu with the unity desktop I would expect 922MB of ram to mean the OS would run very slowly; how is yours doing speed-wise?

---

### Post by vishnu11 on 2016-06-12
> **ajgreeny said:**
> What does the command ```
free -m
``` show you?
If you're using ubuntu with the unity desktop I would expect 922MB of ram to mean the OS would run very slowly; how is yours doing speed-wise?

Thanks for replay 

for general browsing was fine but running a Android Studio Emulator results in Memory overflow    

free -m <response>

                  total       used       free     shared    buffers     cached
Mem:           922        684        237        137          6        249

---

### Post by ajgreeny on 2016-06-12
Is this a new computer and installation of the OS or did you have some other OS before that showed all 16GB?

Can you run memtest from the grub menu or is it a UEFI system where that will not work?  I suspect UEFI as it is probably a new machine but tell all please.

---

### Post by pqwoerituytrueiwoq on 2016-06-12
have you checked for a BIOS update?

---

