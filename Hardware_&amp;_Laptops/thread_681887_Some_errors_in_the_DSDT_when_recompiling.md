---
title: "Some errors in the DSDT when recompiling"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by _Stevie_ on 2008-01-29
hi all,

im just trying to fix my dsdt on a fsc amilo xa1526 notebook on gutsy.
when recompiling the dsdt [http://ubuntuusers.de/paste/31886/](http://ubuntuusers.de/paste/31886/)
 i get 5 errors.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl    81:     Method (\_WAK, 1, NotSerialized)
Warning  1079 -                 ^ Reserved method must return a value (_WAK)

dsdt.dsl   212:         Method (_L10, 0, NotSerialized)
Warning  1086 -                    ^ Not all control paths return a value (_L10)

dsdt.dsl  2880:                     Method (NVIF, 3, NotSerialized)
Warning  1086 -                                ^ Not all control paths return a value (NVIF)

dsdt.dsl  3061:                     Method (_EJ0, 0, NotSerialized)
Warning  1076 -                                ^ Reserved method has too few arguments (_EJ0 requires 1)

dsdt.dsl  4525:                 Store (\_SB.PCI0.LPC0.PMRD (0xFA), Local0)
Warning  1098 -                 Statement is unreachable ^ 

ASL Input:  dsdt.dsl - 4938 lines, 162275 bytes, 2302 keywords
AML Output: dsdt.aml - 17627 bytes 582 named objects 1720 executable opcodes

Compilation complete. 0 Errors, 5 Warnings, 0 Remarks, 529 Optimizations
```

one i could already solve the 1st one by adding 
```
Return(Package(0x02){0x00, 0x00}) 

```

to the last line in the function.
but i could need some help with the rest of the problems :confused:


greets,

stevie

---

