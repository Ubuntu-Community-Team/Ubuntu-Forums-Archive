---
title: "how to tell if CPU is 32 bit or 64 Bit"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by kystorms on 2007-09-09
I was hoping someone could tell me where I would look to find out if my CPU is a 32 bit or a 64 bit?
I am not well versed in how to find these details out so thank you for any help

---

### Post by rsambuca on 2007-09-09
Do you know what the cpu is called?  If so, then we can let you know.  Or the make and model of your computer?

---

### Post by kystorms on 2007-09-09
I do know my cpu is a asus A7V400-MX 
:-)

---

### Post by iAndrew on 2007-09-09
I'm pretty sure this is a 64 bit computer judging it from the processor (amd). I could be wrong, but I'm like 90% certain.

---

### Post by nonewmsgs on 2007-09-09
> **kystorms said:**
> I do know my cpu is a asus A7V400-MX 
:-)

that's a motherboard.  

```

sudo apt-get install cpuid

cpuid


```

now give us the output of that

---

### Post by kystorms on 2007-09-09
> **nonewmsgs said:**
> that's a motherboard.  

```

sudo apt-get install cpuid

cpuid


```

now give us the output of that

okay this is what i get ------

cpuid
 eax in    eax      ebx      ecx      edx
00000000 00000001 68747541 444d4163 69746e65
00000001 000006a0 00000000 00000000 0383fbff
80000000 80000008 68747541 444d4163 69746e65
80000001 000007a0 00000000 00000000 c1c3fbff
80000002 20444d41 6c687441 74286e6f 0020296d
80000003 00000000 00000000 00000000 00000000
80000004 00000000 00000000 00000000 00000000
80000005 0408ff08 ff20ff10 40020140 40020140
80000006 00000000 41004100 02008140 00000000
80000007 00000000 00000000 00000000 00000001
80000008 00002022 00000000 00000000 00000000

Vendor ID: "AuthenticAMD"; CPUID level 1

AMD-specific functions
Version 000006a0:
Family: 6 Model: 10 [Duron/Athlon model 10]

Standard feature flags 0383fbff:
Floating Point Unit
Virtual Mode Extensions
Debugging Extensions
Page Size Extensions
Time Stamp Counter (with RDTSC and CR4 disable bit)
Model Specific Registers with RDMSR & WRMSR
PAE - Page Address Extensions
Machine Check Exception
COMPXCHG8B Instruction
APIC
SYSCALL/SYSRET or SYSENTER/SYSEXIT instructions
MTRR - Memory Type Range Registers
Global paging extension
Machine Check Architecture
Conditional Move Instruction
PAT - Page Attribute Table
PSE-36 - Page Size Extensions
MMX instructions
FXSAVE/FXRSTOR
25 - reserved
Generation: 7 Model: 10
Extended feature flags c1c3fbff:
Floating Point Unit
Virtual Mode Extensions
Debugging Extensions
Page Size Extensions
Time Stamp Counter (with RDTSC and CR4 disable bit)
Model Specific Registers with RDMSR & WRMSR
PAE - Page Address Extensions
Machine Check Exception
COMPXCHG8B Instruction
APIC
SYSCALL/SYSRET or SYSENTER/SYSEXIT instructions
MTRR - Memory Type Range Registers
Global paging extension
Machine Check Architecture
Conditional Move Instruction
PAT - Page Attribute Table
PSE-36 - Page Size Extensions
AMD MMX Instruction Extensions
MMX instructions
FXSAVE/FXRSTOR
3DNow! Instruction Extensions
3DNow instructions

Processor name string: AMD Athlon(tm) 
L1 Cache Information:
2/4-MB Pages:
   Data TLB: associativity 4-way #entries 8
   Instruction TLB: associativity 255-way #entries 8
4-KB Pages:
   Data TLB: associativity 255-way #entries 32
   Instruction TLB: associativity 255-way #entries 16
L1 Data cache:
   size 64 KB associativity 2-way lines per tag 1 line size 64
L1 Instruction cache:
   size 64 KB associativity 2-way lines per tag 1 line size 64

L2 Cache Information:
2/4-MB Pages:
   Data TLB: associativity L2 off #entries 0
   Instruction TLB: associativity L2 off #entries 0
4-KB Pages:
   Data TLB: associativity Direct mapped #entries 0
   Instruction TLB: associativity Direct mapped #entries 0
   size 2 KB associativity L2 off lines per tag 129 line size 64

Advanced Power Management Feature Flags
Has temperature sensing diode
Maximum linear address: 32; maximum phys address 34
lisac@lisac-desktop:~$

---

### Post by rsambuca on 2007-09-09
32 bit

---

### Post by kystorms on 2007-09-09
many thanks
:-)

---

