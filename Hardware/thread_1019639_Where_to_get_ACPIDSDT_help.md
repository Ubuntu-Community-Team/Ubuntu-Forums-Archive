---
title: "Where to get ACPI/DSDT help?"
date: 2008-12-23
forum: Hardware
---

### Post by 67GTA on 2008-12-23
I have rebuilt the DSDT for my HP dv6815nr laptop so it has 0 errors, 0 warnings, and 1131 optimizations. Thermal is now recognized, and I no longer have to hold down a button to get the progress bar to move at boot. I have done the same for my HP m8100n desktop, but 6 warnings remain. It ran fine before, but now suspend works! I can't find any references to fix the other 6 warnings. Where can I go to get help with the 6 remaining warnings for my desktop, and maybe submit the DSDT for my laptop? The ACPI webpage doesn't have a bug tracker or forums. I have downloaded and read through the ACPI specs from the ACPI website, but there are no references to T2U, 0r U2T.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/shawnr/dsdt.dsl  2071:                         Store (U2T (Local3), DMA0)
Warning  1091 -   Called method may not always return a value ^ 

/home/shawnr/dsdt.dsl  2092:                         Store (U2T (Local3), DMA1)
Warning  1091 -   Called method may not always return a value ^ 

/home/shawnr/dsdt.dsl  2111:                 Method (U2T, 1, NotSerialized)
Warning  1086 -   Not all control paths return a value ^  (U2T_)

/home/shawnr/dsdt.dsl  2149:                 Method (T2U, 1, NotSerialized)
Warning  1086 -   Not all control paths return a value ^  (T2U_)

/home/shawnr/dsdt.dsl  2276:                         ShiftLeft (T2U (DMA0), 0x08, Local2)
Warning  1091 -       Called method may not always return a value ^ 

/home/shawnr/dsdt.dsl  2293:                         Or (0xC0, T2U (DMA1), Local2)
Warning  1091 - Called method may not always return a value ^ 

ASL Input:  /home/shawnr/dsdt.dsl - 6219 lines, 194888 bytes, 2423 keywords
AML Output: /home/shawnr/dsdt.aml - 21035 bytes 837 named objects 1586 executable opcodes

Compilation complete. 0 Errors, 6 Warnings, 0 Remarks, 660 Optimizations
```

---

