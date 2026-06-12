---
title: "Need help fixing my DSDT"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by luksmann on 2008-01-12
Hello Guys!
As my laptop won't shutdown (and some minor problems which might be related to ACPI bug me) I've decided to try to fix DSDT.
I got as far as to recompiling the DSDT and recieving lots of errors...

Output: 
```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   323:             Method (_CST, 0, NotSerialized)
Warning  1086 -                        ^ Not all control paths return a value (_CST)

dsdt.dsl   323:             Method (_CST, 0, NotSerialized)
Warning  1079 -                        ^ Reserved method must return a value (_CST)

dsdt.dsl   483:             Method (_CST, 0, NotSerialized)
Warning  1086 -                        ^ Not all control paths return a value (_CST)

dsdt.dsl   483:             Method (_CST, 0, NotSerialized)
Warning  1079 -                        ^ Reserved method must return a value (_CST)

dsdt.dsl   488:                     Return (\_PR.CPU0._CST ())
Warning  1091 -                                          ^ Called method may not always return a value

dsdt.dsl  1179:             Method (_OSC, 5, NotSerialized)
Warning  1075 -                        ^ Reserved method has too many arguments (_OSC requires 4)

dsdt.dsl  1195:                             And (CAPB, 0xFFFFFFFC)
Warning  1104 -                                     ^ Result is not used, operator has no effect

dsdt.dsl  1937:                     Method (INCS, 1, NotSerialized)
Warning  1086 -                                ^ Not all control paths return a value (INCS)

dsdt.dsl  1984:                         Store (INCS (GDGS), Local1)
Warning  1091 -                                   ^ Called method may not always return a value

dsdt.dsl  1990:                             Store (INCS (Local1), Local1)
Warning  1091 -                                       ^ Called method may not always return a value

dsdt.dsl  4506:                     Method (_GTM, 0, NotSerialized)
Warning  1086 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  4506:                     Method (_GTM, 0, NotSerialized)
Warning  1079 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  4666:                         Method (_GTF, 0, NotSerialized)
Warning  1086 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  4666:                         Method (_GTF, 0, NotSerialized)
Warning  1079 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  4734:                         Method (_GTF, 0, NotSerialized)
Warning  1086 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  4734:                         Method (_GTF, 0, NotSerialized)
Warning  1079 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  4807:                     Method (_GTM, 0, NotSerialized)
Warning  1086 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  4807:                     Method (_GTM, 0, NotSerialized)
Warning  1079 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  4980:                         Method (_GTF, 0, NotSerialized)
Warning  1086 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  4980:                         Method (_GTF, 0, NotSerialized)
Warning  1079 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  5048:                         Method (_GTF, 0, NotSerialized)
Warning  1086 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  5048:                         Method (_GTF, 0, NotSerialized)
Warning  1079 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  5155:                     Method (_GTF, 0, NotSerialized)
Warning  1086 -                                ^ Not all control paths return a value (_GTF)

dsdt.dsl  5155:                     Method (_GTF, 0, NotSerialized)
Warning  1079 -                                ^ Reserved method must return a value (_GTF)

dsdt.dsl  5201:                     Method (_GTF, 0, NotSerialized)
Warning  1086 -                                ^ Not all control paths return a value (_GTF)

dsdt.dsl  5201:                     Method (_GTF, 0, NotSerialized)
Warning  1079 -                                ^ Reserved method must return a value (_GTF)

ASL Input:  dsdt.dsl - 5215 lines, 184449 bytes, 2105 keywords
AML Output: dsdt.aml - 19165 bytes 590 named objects 1515 executable opcodes

```

Link to DSDT pasted to pastebin.org
[DSDT @ Pastebin]("http://pastebin.org/15087")

I hope there's somebody out there who can help me!

Thanks a lot!
Greets, luksmann

---

