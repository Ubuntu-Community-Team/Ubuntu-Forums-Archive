---
title: "Fix pwarningsDSDT with acer aspire 7720"
date: 2010-09-01
forum: Hardware
---

### Post by MartinoM on 2010-09-01
Can someone help me to fix warnings with my DSDT?

```
martino@martino-laptop:~/Scrivania/DSDT$ iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  6841:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  6841:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  7001:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  7001:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  7069:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  7069:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  7142:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  7142:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  7316:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  7316:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  7384:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  7384:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  7491:                     Method (_GTF, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTF)

dsdt.dsl  7491:                     Method (_GTF, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTF)

dsdt.dsl  7537:                     Method (_GTF, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTF)

dsdt.dsl  7537:                     Method (_GTF, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTF)

dsdt.dsl  7848:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7911:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7915:                         Name (_T_1, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_1)

dsdt.dsl  7949:                         Name (_T_2, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_2)

dsdt.dsl  7983:                 Method (OEMN, 0, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (OEMN)

dsdt.dsl  8013:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  8193:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  8205:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl  8350:                         Name (_T_2, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_2)

dsdt.dsl  8565:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  8618:                 Method (_WED, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (_WED)

dsdt.dsl  8618:                 Method (_WED, 1, NotSerialized)
Warning  1080 -                            ^ Reserved method must return a value (_WED)

dsdt.dsl  8624:                             Return (OEMN ())
Warning  1092 -                                        ^ Called method may not always return a value

dsdt.dsl  8662:                 Method (WMBD, 3, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WMBD)

ASL Input:  dsdt.dsl - 8834 lines, 327825 bytes, 3822 keywords
AML Output: dsdt.aml - 32998 bytes, 929 named objects, 2893 executable opcodes

Compilation complete. 0 Errors, 21 Warnings, 9 Remarks, 934 Optimizations

```

---

### Post by MartinoM on 2010-09-05
Bump!

---

