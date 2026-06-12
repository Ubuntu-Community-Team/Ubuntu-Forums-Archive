---
title: "any good system tools like 'cpuid' is for windows?"
date: 2008-11-08
forum: General Help
---

### Post by ShirishAg75 on 2008-11-08
Hi all, 
 I have been looking to find out my cpu (which family it is Williamnette, Prescott and stuff like that -based on the codenames given but haven't found a good tool which links to the same) . This information is there in programs like 'cpuid' in windows. 

This is the info. I get when I try 'hwinfo' as well as the 'cpuid' program in GNU/Linux Ubuntu

```

hwinfo --cpu
01: None 00.0: 10103 CPU                                        
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 15.1.2 "Intel(R) Pentium(R) 4 CPU 1.80GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,up,pebs,bts
  Clock: 1804 MHz
  BogoMips: 3608.17
  Cache: 256 kb
  Units/Processor: 1
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```Now for cpuid 

```

$ cpuid
 eax in    eax      ebx      ecx      edx
00000000 00000002 756e6547 6c65746e 49656e69
00000001 00000f12 00010808 00000000 3febfbff
00000002 665b5001 00000000 00000000 007a7040
80000000 80000004 00000000 00000000 00000000
80000001 00000000 00000000 00000000 00000000
80000002 20202020 20202020 20202020 6e492020
80000003 286c6574 50202952 69746e65 52286d75
80000004 20342029 20555043 30382e31 007a4847

Vendor ID: "GenuineIntel"; CPUID level 2

Intel-specific functions:
Version 00000f12:
Type 0 - Original OEM
Family 15 - Pentium 4
Extended family 0
Model 1 - 
Stepping 2
Reserved 0

Brand index: 8 [Intel Pentium 4 processor]
Extended brand string: "              Intel(R) Pentium(R) 4 CPU 1.80GHz"
CLFLUSH instruction cache line size: 8
Hyper threading siblings: 1

Feature flags 3febfbff:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
PAE    Physical Address Extension
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
APIC   On-chip Advanced Programmable Interrupt Controller present and enabled
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
PSE-36 36-bit Page Size Extension
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
SS     Self Snoop
HT     Hyper Threading
TM     Thermal monitor

TLB and cache info:
50: Instruction TLB: 4KB and 2MB or 4MB pages, 64 entries
5b: Data TLB: 4KB and 4MB pages, 64 entries
66: 1st-level data cache: 8KB, 4-way set assoc, 64 byte line size
40: No 2nd-level cache, or if 2nd-level cache exists, no 3rd-level cache
70: Trace cache: 12K-micro-op, 4-way set assoc
7a: 2nd-level cache: 256KB, 8-way set assoc, sectored, 64 byte line size

```

---

### Post by lisati on 2008-11-08
The following yields some potentially interesting information about your system from within the terminal, including CPU information:
```
sudo dmidecode | less
```

---

### Post by Blues- on 2008-11-11
For detailed memory information .. such as ram speed, banks , etc.
Use ..
```
sudo dmidecode --type 17
```

---

