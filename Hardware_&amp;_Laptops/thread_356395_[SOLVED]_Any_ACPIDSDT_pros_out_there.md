---
title: "[SOLVED] Any ACPI/DSDT pros out there?"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by beneedict on 2007-02-08
Hi!
There is a new BIOS for the nx6325 notebook out there!!! (F.06)
Works great!!!
Still I checked the DSDT table with the most up to date IASL tools from Intel (releasedate: 9th of november) and a "./iasl -sa dsdt.dsl" results in following output:
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [Feb  7 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2087:                         Method (_BCQ, 0, Serialized)
Warning  1097 -              Unknown reserved name ^  (_BCQ)

dsdt.dsl  9532:                         If (LEqual (C2EA (0x00), 0x01))
Warning  1091 -                                        ^ Called method may not always return a value

dsdt.dsl  9556:                         If (LEqual (C2EA (0x01), 0x01))
Warning  1091 -                                        ^ Called method may not always return a value

dsdt.dsl 10453:             Method (C2EA, 1, NotSerialized)
Warning  1086 -                        ^ Not all control paths return a value (C2EA)

ASL Input:  dsdt.dsl - 13238 lines, 492707 bytes, 6366 keywords
AML Output: /home/****/dsdt.aml - 60051 bytes 1116 named objects 5250 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 2075 Optimizations
```

The whole [dsdt.dsl can be found here]("http://beneedict.be.funpic.de/files/dsdt.dsl").

The BCQ method seems to be something for Windows Vista (screen brightness control) and if I cut it out the method the dsdt.dsl compiles without this particular warning. Same for the 1091 errors. I deleted the whole If-Else blocks they include and the dsdt compiled without them. but the last thing seems to be more difficult. The problem in general seems to be the C2EA variable.
I am asking for that, because my computer works perfectly fine but after a reboot the thermal ACPI seems to be broken and the ventilation won't work any more. So I thought it could be caused by a broken DSDT?

---

### Post by beneedict on 2007-07-25
This error is nothing to worry about, as far as I know now. and there is a new firmware version!!!

---

