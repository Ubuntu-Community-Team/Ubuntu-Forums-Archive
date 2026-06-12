---
title: "32 or 64bit processor?"
date: 2011-10-03
forum: Hardware
---

### Post by Azyx on 2011-10-03
I have a Dual-Core E5200 @ 2.5GHz.

```
Azyx@Intel:~$ cpuid
 eax in    eax      ebx      ecx      edx
00000000 0000000a 756e6547 6c65746e 49656e69
00000001 00010676 00020800 0000e39d bfebfbff
00000002 05b0b101 005657f0 00000000 2cb4307d
00000003 00000000 00000000 00000000 00000000
00000004 00000000 00000000 00000000 00000000
00000005 00000040 00000040 00000003 00022220
00000006 00000001 00000002 00000001 00000000
00000007 00000000 00000000 00000000 00000000
00000008 00000400 00000000 00000000 00000000
00000009 00000000 00000000 00000000 00000000
0000000a 07280202 00000000 00000000 00000503
80000000 80000008 00000000 00000000 00000000
80000001 00000000 00000000 00000001 20100000
80000002 746e6550 286d7569 44202952 2d6c6175
80000003 65726f43 50432020 20202055 45202020
80000004 30303235 20402020 30352e32 007a4847
80000005 00000000 00000000 00000000 00000000
80000006 00000000 00000000 08006040 00000000
80000007 00000000 00000000 00000000 00000000
80000008 00003024 00000000 00000000 00000000

Vendor ID: "GenuineIntel"; CPUID level 10

Intel-specific functions:
Version 00010676:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 7 - Pentium III/Pentium III Xeon - external L2 cache
Stepping 6
Reserved 4

Extended brand string: "Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz"
CLFLUSH instruction cache line size: 8
Hyper threading siblings: 2

Feature flags bfebfbff:
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
31     reserved

TLB and cache info:
b1: unknown TLB/cache descriptor
b0: unknown TLB/cache descriptor
05: unknown TLB/cache descriptor
f0: unknown TLB/cache descriptor
57: unknown TLB/cache descriptor
56: unknown TLB/cache descriptor
7d: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
b4: unknown TLB/cache descriptor
2c: unknown TLB/cache descriptor
Processor serial: 0001-0676-0000-0000-0000-0000
Azyx@Intel:~$ 
```
Do I need to change anything in BIOS?

/Cheers

---

### Post by haqking on 2011-10-03
> **Azyx said:**
> I have a Dual-Core E5200 @ 2.5GHz.

```
Azyx@Intel:~$ cpuid
 eax in    eax      ebx      ecx      edx
00000000 0000000a 756e6547 6c65746e 49656e69
00000001 00010676 00020800 0000e39d bfebfbff
00000002 05b0b101 005657f0 00000000 2cb4307d
00000003 00000000 00000000 00000000 00000000
00000004 00000000 00000000 00000000 00000000
00000005 00000040 00000040 00000003 00022220
00000006 00000001 00000002 00000001 00000000
00000007 00000000 00000000 00000000 00000000
00000008 00000400 00000000 00000000 00000000
00000009 00000000 00000000 00000000 00000000
0000000a 07280202 00000000 00000000 00000503
80000000 80000008 00000000 00000000 00000000
80000001 00000000 00000000 00000001 20100000
80000002 746e6550 286d7569 44202952 2d6c6175
80000003 65726f43 50432020 20202055 45202020
80000004 30303235 20402020 30352e32 007a4847
80000005 00000000 00000000 00000000 00000000
80000006 00000000 00000000 08006040 00000000
80000007 00000000 00000000 00000000 00000000
80000008 00003024 00000000 00000000 00000000

Vendor ID: "GenuineIntel"; CPUID level 10

Intel-specific functions:
Version 00010676:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 7 - Pentium III/Pentium III Xeon - external L2 cache
Stepping 6
Reserved 4

Extended brand string: "Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz"
CLFLUSH instruction cache line size: 8
Hyper threading siblings: 2

Feature flags bfebfbff:
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
31     reserved

TLB and cache info:
b1: unknown TLB/cache descriptor
b0: unknown TLB/cache descriptor
05: unknown TLB/cache descriptor
f0: unknown TLB/cache descriptor
57: unknown TLB/cache descriptor
56: unknown TLB/cache descriptor
7d: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
b4: unknown TLB/cache descriptor
2c: unknown TLB/cache descriptor
Processor serial: 0001-0676-0000-0000-0000-0000
Azyx@Intel:~$ 
```
Do I need to change anything in BIOS?

/Cheers

Do you need to change anything to do what ? I cant see that you have asked a question ?

---

### Post by Azyx on 2011-10-03
> **haqking said:**
> Do you need to change anything to do what ? I cant see that you have asked a question ?

Is the processor able to run 64-bit operating-system, and If it does, do I need to change anything in BIOS? i tried for a copple of years ago to run Ubuntu-64 but it did'nt boot....

---

### Post by haqking on 2011-10-03
> **Azyx said:**
> Is the processor able to run 64-bit operating-system, and If it does, do I need to change anything in BIOS? i tried for a copple of years ago to run Ubuntu-64 but it did'nt boot....

post output from following:

```
grep flags /proc/cpuinfo
```

---

### Post by Azyx on 2011-10-03
> **haqking said:**
> post output from following:

```
grep flags /proc/cpuinfo
```

```
$ grep flags /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm


```

---

### Post by diasf on 2011-10-03
[http://ark.intel.com/products/37212/Intel-Pentium-Processor-E5200-(2M-Cache-2_50-GHz-800-MHz-FSB)]("http://ark.intel.com/products/37212/Intel-Pentium-Processor-E5200-%282M-Cache-2_50-GHz-800-MHz-FSB%29")

---

### Post by haqking on 2011-10-03
> **Azyx said:**
> ```
$ grep flags /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm


```

The LM flag in that output indicates long mode so yes should support x64.

To be 100% certain download the x64 live CD and test it without installing.

---

### Post by scorp123 on 2011-10-03
> **Azyx said:**
> ```
$ grep flags /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **[COLOR="Red"]lm[/COLOR]** constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **[COLOR="Red"]lm[/COLOR]** constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm


``` "lm" = Long Mode = 64-bit.

That is a 64-bit CPU.

---

### Post by Azyx on 2011-10-03
> **haqking said:**
> The LM flag in that output indicates long mode so yes should support x64.

To be 100% certain download the x64 live CD and test it without installing.

Thanx. /Cheers

---

### Post by haqking on 2011-10-03
> **Azyx said:**
> Thanx. /Cheers

no worries you are welcome.

---

