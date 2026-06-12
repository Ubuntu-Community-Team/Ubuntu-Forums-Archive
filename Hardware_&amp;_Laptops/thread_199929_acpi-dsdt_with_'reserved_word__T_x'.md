---
title: "acpi-dsdt with 'reserved word _T_x'"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by sysrq1 on 2006-06-19
Hello,

i have a acer wlmi 5652 with ubuntu 6.06 and i am trying to repair my acpi dsdt with the intel ASL compiler.
At the beginning i have got about 16 errors, now only 8 errors after google'ing for some hours.

There is still a error-message i dont understand and i dont know what to do. Here my problem:

When i try to compile my dsdt.dsl, the following errors occur:

>>>>>>>>>>>>>>>>>>>>
daniel@daniel-laptop:~$ iasl -sa dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20051216 [Jan  9 2006]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

No back ptr to Op: type 8
No back ptr to Op: type 8
No back ptr to Op: type 8
No back ptr to Op: type 8
No back ptr to Op: type 8
dsdt.dsl  1068:                 Name (_T_0, Zero)
Error    1080 -     Use of reserved word ^  (_T_0)

dsdt.dsl  1073:                     Store (Local0, _T_1)
Error    1065 - Object not accessible from this scope ^  (_T_1)

dsdt.dsl  1074:                     If (LEqual (_T_1, 0x04))
Error    1065 -                                    ^ Object not accessible from this scope (_T_1)

dsdt.dsl  1080:                         If (LEqual (_T_1, 0x05))
Error    1065 -  Object not accessible from this scope ^  (_T_1)

dsdt.dsl  1086:                             If (LEqual (_T_1, 0x06))
Error    1065 -      Object not accessible from this scope ^  (_T_1)

dsdt.dsl  1092:                                 If (LEqual (_T_1, 0x07))
Error    1065 -          Object not accessible from this scope ^  (_T_1)

dsdt.dsl  1106:                     Name (_T_2, Zero)
Error    1080 -         Use of reserved word ^  (_T_2)

dsdt.dsl  1145:                     Name (_T_3, Zero)
Error    1080 -         Use of reserved word ^  (_T_3)

dsdt.dsl  1168:             Method (Z002, 0, NotSerialized)
Warning  2085 -                        ^ Not all control paths return a value (Z002)

dsdt.dsl  1189:                 Name (_T_0, Zero)
Error    1080 -     Use of reserved word ^  (_T_0)

dsdt.dsl  1328:                 Name (_T_0, Zero)
Error    1080 -     Use of reserved word ^  (_T_0)

dsdt.dsl  1340:                         Name (_T_1, Zero)
Error    1080 -             Use of reserved word ^  (_T_1)

dsdt.dsl  1471:                     Name (_T_2, Zero)
Error    1080 -         Use of reserved word ^  (_T_2)

dsdt.dsl  1621:             Name (_WDG, Buffer (0xDC)
Warning  2096 -                      ^ Unknown reserved name (_WDG)

dsdt.dsl  1684:             Method (_WED, 1, NotSerialized)
Warning  2085 -                        ^ Not all control paths return a value (_WED)

dsdt.dsl  1684:             Method (_WED, 1, NotSerialized)
Warning  2096 -  Unknown reserved name ^  (_WED)

dsdt.dsl  1690:                         Return (Z002 ())
Warning  2090 -                                    ^ Called method may not always return a value

dsdt.dsl  1727:             Method (WMBD, 3, NotSerialized)
Warning  2085 -                        ^ Not all control paths return a value (WMBD)

ASL Input:  dsdt.dsl - 6591 lines, 238577 bytes, 2598 keywords
Compilation complete. 12 Errors, 6 Warnings, 0 Remarks, 4 Optimizations
<<<<<<<<<<<<<<<<<<<<

I dont understand the 'Use of reserved word ^  (_T_x)' error. I have try to find a specification and found it on p://www.acpi.info/DOWNLOADS/ACPIspec30.pdf. At page 449 is the section '17.2.1.1 _T_x Reserved Object Names', which says, that names with the prefix _T_ are for internal use for the ASL compiler; it has to be be declared with a 'Name(_T_x, value)'.

In my dsdt.dsl the command is used correct: 'Name (_T_0, Zero)'. But why the compiler throw a error? I dont understand this.

Hope anyone here got the required experience for my Problem.

---

### Post by thesoothsayer on 2007-06-10
Bump. Does anyone know the answer to this?
Thanks.

---

