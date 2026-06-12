---
title: "DSDT for Asus X56Tr"
date: 2010-09-08
forum: Hardware
---

### Post by jobv on 2010-09-08
Hello everybody!
 
 I'm trying to fix the DSDT table for my Asus X56Tr (Ubuntu 10.04).
 
 I'm not an expert and this is quiet hard for me. I reached a dead point:
  ```

giovanni@X56T:~/less$ iasl -tc DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

DSDT.dsl  2532:                                 Not (Local3)
Warning  1105 -                                           ^ Result is not used, operator has no effect

DSDT.dsl  2589:                                 Not (Local3)
Warning  1105 -                                           ^ Result is not used, operator has no effect

DSDT.dsl  2646:                                 Not (Local3)
Warning  1105 -                                           ^ Result is not used, operator has no effect

DSDT.dsl  2703:                                 Not (Local3)
Warning  1105 -                                           ^ Result is not used, operator has no effect

DSDT.dsl  2760:                                 Not (Local3)
Warning  1105 -                                           ^ Result is not used, operator has no effect

DSDT.dsl  2817:                                 Not (Local3)
Warning  1105 -                                           ^ Result is not used, operator has no effect

DSDT.dsl  2874:                                 Not (Local3)
Warning  1105 -                                           ^ Result is not used, operator has no effect

DSDT.dsl  3069:                 If (LEqual (STCL, 0x0101))
Error    4095 -                  ^ syntax error, unexpected PARSEOP_IF

DSDT.dsl  3609:                         CreateDWordField (CRS, \_SB.PCI0.SBRG.HPET._Y02._BAS, HPT)
Error    4063 -                                                      Object does not exist ^  (\_SB.PCI0.SBRG.HPET._Y02._BAS)

DSDT.dsl  3636:                         CreateDWordField (CRS, \_SB.PCI0.PCIE._Y03._BAS, BAS1)
Error    4063 -                                                 Object does not exist ^  (\_SB.PCI0.PCIE._Y03._BAS)

DSDT.dsl  3637:                         CreateDWordField (CRS, \_SB.PCI0.PCIE._Y03._LEN, LEN1)
Error    4063 -                                                 Object does not exist ^  (\_SB.PCI0.PCIE._Y03._LEN)

DSDT.dsl  3675:                             CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y04._LEN, ML01)
Error    4063 -                                                          Object does not exist ^  (\_SB.PCI0.SBRG.OMSC._Y04._LEN)

DSDT.dsl  3676:                             CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y04._BAS, MB01)
Error    4063 -                                                          Object does not exist ^  (\_SB.PCI0.SBRG.OMSC._Y04._BAS)

DSDT.dsl  3677:                             CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y05._LEN, ML02)
Error    4063 -                                                          Object does not exist ^  (\_SB.PCI0.SBRG.OMSC._Y05._LEN)

DSDT.dsl  3678:                             CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y05._BAS, MB02)
Error    4063 -                                                          Object does not exist ^  (\_SB.PCI0.SBRG.OMSC._Y05._BAS)

DSDT.dsl  3718:                         CreateDWordField (CRS, \_SB.RMEM._Y06._BAS, BAS1)
Error    4063 -                                            Object does not exist ^  (\_SB.RMEM._Y06._BAS)

DSDT.dsl  3719:                         CreateDWordField (CRS, \_SB.RMEM._Y06._LEN, LEN1)
Error    4063 -                                            Object does not exist ^  (\_SB.RMEM._Y06._LEN)

DSDT.dsl  3720:                         CreateDWordField (CRS, \_SB.RMEM._Y07._BAS, BAS2)
Error    4063 -                                            Object does not exist ^  (\_SB.RMEM._Y07._BAS)

DSDT.dsl  3721:                         CreateDWordField (CRS, \_SB.RMEM._Y07._LEN, LEN2)
Error    4063 -                                            Object does not exist ^  (\_SB.RMEM._Y07._LEN)

DSDT.dsl  3722:                         CreateDWordField (CRS, \_SB.RMEM._Y08._LEN, LEN3)
Error    4063 -                                            Object does not exist ^  (\_SB.RMEM._Y08._LEN)

DSDT.dsl  3723:                         CreateDWordField (CRS, \_SB.RMEM._Y09._BAS, BAS4)
Error    4063 -                                            Object does not exist ^  (\_SB.RMEM._Y09._BAS)

DSDT.dsl  3724:                         CreateDWordField (CRS, \_SB.RMEM._Y09._LEN, LEN4)
Error    4063 -                                            Object does not exist ^  (\_SB.RMEM._Y09._LEN)

DSDT.dsl  4008:                         CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0A._MIN, GP00)
Error    4063 -                                                     Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0A._MIN)

DSDT.dsl  4009:                         CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0A._MAX, GP01)
Error    4063 -                                                     Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0A._MAX)

DSDT.dsl  4010:                         CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y0A._LEN, GP0L)
Error    4063 -                                                     Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0A._LEN)

DSDT.dsl  4016:                             CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0B._MIN, GP10)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0B._MIN)

DSDT.dsl  4017:                             CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0B._MAX, GP11)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0B._MAX)

DSDT.dsl  4018:                             CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y0B._LEN, GP1L)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0B._LEN)

DSDT.dsl  4022:                             CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0C._MIN, GPB0)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0C._MIN)

DSDT.dsl  4023:                             CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0C._MAX, GPB1)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0C._MAX)

DSDT.dsl  4024:                             CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y0C._LEN, GPBL)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0C._LEN)

DSDT.dsl  4032:                             CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0D._MIN, GP20)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0D._MIN)

DSDT.dsl  4033:                             CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0D._MAX, GP21)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0D._MAX)

DSDT.dsl  4034:                             CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y0D._LEN, GP2L)
Error    4063 -                                                         Object does not exist ^  (\_SB.PCI0.SBRG.RMSC._Y0D._LEN)

DSDT.dsl  4476:                         Return (NXTD)
Warning  1099 -           Statement is unreachable ^ 

DSDT.dsl  4555:     Scope      B1PN,   16, 
Error    4095 -         ^ syntax error, unexpected PARSEOP_SCOPE, expecting $end

ASL Input:  DSDT.dsl - 11953 lines, 339828 bytes, 1623 keywords
Compilation complete. 28 Errors, 8 Warnings, 0 Remarks, 22 Optimizations

```Now I'm trying to fix the first error (no Warning) but I don't undsteand where the problem is. 

 I attach the original DSDT table and the DSDT table fixed by me.
 
 Thank you very much!

---

