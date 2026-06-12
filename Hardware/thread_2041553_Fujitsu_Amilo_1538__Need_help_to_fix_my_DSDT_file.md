---
title: "Fujitsu Amilo 1538 / Need help to fix my DSDT file"
date: 2012-08-12
forum: Hardware
---

### Post by bofphile on 2012-08-12
Hi,

I'm trying to fix the DSDT file for this laptop (because the CPU fan is constantly spinning at full speed even when the CPU is idle).

I followed the tutorial from this thread: [http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt]("http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt")

but now I'm stuck at this step because I don't really know how to correct these errors.
```
iasl -tc /home/turion/dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Oct 15 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

/home/turion/dsdt.dsl    81:     Method (\_WAK, 1, NotSerialized)
Warning  1081 -                              ^ Reserved method must return a value (Integer/Package required for _WAK)

/home/turion/dsdt.dsl   207:         Method (_L10, 0, NotSerialized)
Warning  1088 -                                 ^ Not all control paths return a value (_L10)

/home/turion/dsdt.dsl   585:                         0xFFF00000,         // Length
Error    4117 -          Length is larger than Min/Max window ^ 

/home/turion/dsdt.dsl  2861:                     Method (NVIF, 3, NotSerialized)
Warning  1088 -        Not all control paths return a value ^  (NVIF)

/home/turion/dsdt.dsl  4551:                 Store (\_SB.PCI0.LPC0.PMRD (0xFA), Local0)
Warning  1100 -                              Statement is unreachable ^ 

ASL Input:  /home/turion/dsdt.dsl - 4962 lines, 162828 bytes, 2300 keywords
Compilation complete. 1 Errors, 4 Warnings, 0 Remarks, 519 Optimizations
```

Thanks.

---

