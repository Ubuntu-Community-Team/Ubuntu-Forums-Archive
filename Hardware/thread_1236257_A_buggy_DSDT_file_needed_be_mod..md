---
title: "A buggy DSDT file needed be mod."
date: 2009-08-10
forum: Hardware
---

### Post by kidalive on 2009-08-10
Greetings 

I installed Ubuntu 9.04 and the brightness control still not working. I wanna fix it through the DSDT method. But I found a lot of error while compiling the .DSL file into .AML file. Any hope to correct `em? I`m a green-hand of this operation. So I`m asking pros to help me figure out a way to correct these errors. Welcome to try.  :P

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20080926 [Oct  4 2008]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

ACPI Error (nsaccess-0530): ACPI path has too many parent prefixes (^) - reached beyond root node [20080926]

Maximum error count (200) exceeded
./dsdt_fixed.txt    24:     External (^CPU0._PPC)
Error    4014 -          From ACPI CA Subsystem ^  (AE_NOT_FOUND Failure from lookup %s
)

./dsdt_fixed.txt    27:     Mutex (MUTX, 0x00)
Error    4063 - Object does not exist ^  (MUTX)

./dsdt_fixed.txt    28:     OperationRegion (CMS2, SystemIO, 0x72, 0x02)
Error    4063 -           Object does not exist ^  (CMS2)

./dsdt_fixed.txt    29:     Field (CMS2, ByteAcc, NoLock, Preserve)
Error    4063 - Object does not exist ^  (CMS2)

./dsdt_fixed.txt    31:         INDX,   8, 
Error    4063 -                    ^ Object does not exist (INDX)

./dsdt_fixed.txt    32:         DATA,   8
Error    4063 -                    ^ Object does not exist (DATA)

./dsdt_fixed.txt    35:     IndexField (INDX, DATA, ByteAcc, NoLock, Preserve)
Error    4063 -      Object does not exist ^  (INDX)

./dsdt_fixed.txt    35:     IndexField (INDX, DATA, ByteAcc, NoLock, Preserve)
Error    4063 -            Object does not exist ^  (DATA)

./dsdt_fixed.txt    38:         LBLM,   1, 
Error    4063 -                    ^ Object does not exist (LBLM)

./dsdt_fixed.txt    40:         USWU,   1, 
Error    4063 -                    ^ Object does not exist (USWU)

./dsdt_fixed.txt    42:         LCDL,   3, 
Error    4063 -                    ^ Object does not exist (LCDL)

./dsdt_fixed.txt    44:         S4FG,   1
Error    4063 -                    ^ Object does not exist (S4FG)

./dsdt_fixed.txt    47:     OperationRegion (PRT0, SystemIO, 0x80, 0x04)
Error    4063 -           Object does not exist ^  (PRT0)

./dsdt_fixed.txt    48:     Field (PRT0, DWordAcc, Lock, Preserve)
Error    4063 - Object does not exist ^  (PRT0)

./dsdt_fixed.txt    50:         P80H,   32
Error    4063 -                    ^ Object does not exist (P80H)

./dsdt_fixed.txt    53:     Method (P8XH, 2, Serialized)
Error    4063 -  Object does not exist ^  (P8XH)

./dsdt_fixed.txt    57:             Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
Error    4063 -                  Object does not exist ^  (P80D)

./dsdt_fixed.txt    57:             Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
Error    4063 -                                            Object does not exist ^  (P80D)

./dsdt_fixed.txt    62:             Store (Or (And (P80D, 0xFFFF00FF), ShiftLeft (Arg1, 0x08)
Error    4063 -                  Object does not exist ^  (P80D)

./dsdt_fixed.txt    63:                 ), P80D)
Error    4063 -         Object does not exist ^  (P80D)

./dsdt_fixed.txt    68:             Store (Or (And (P80D, 0xFF00FFFF), ShiftLeft (Arg1, 0x10)
Error    4063 -                  Object does not exist ^  (P80D)

./dsdt_fixed.txt    69:                 ), P80D)
Error    4063 -         Object does not exist ^  (P80D)

./dsdt_fixed.txt    74:             Store (Or (And (P80D, 0x00FFFFFF), ShiftLeft (Arg1, 0x18)
Error    4063 -                  Object does not exist ^  (P80D)

./dsdt_fixed.txt    75:                 ), P80D)
Error    4063 -         Object does not exist ^  (P80D)

./dsdt_fixed.txt    78:         Store (P80D, P80H)
Error    4063 -     Object does not exist ^  (P80D)

./dsdt_fixed.txt    78:         Store (P80D, P80H)
Error    4063 -           Object does not exist ^  (P80H)

./dsdt_fixed.txt    81:     Method (_PIC, 1, NotSerialized)
Error    4063 -  Object does not exist ^  (_PIC)

./dsdt_fixed.txt    83:         Store (Arg0, GPIC)
Error    4063 -           Object does not exist ^  (GPIC)

./dsdt_fixed.txt    86:     Method (_PTS, 1, NotSerialized)
Error    4063 -  Object does not exist ^  (_PTS)

./dsdt_fixed.txt    88:         Store (Zero, P80D)
Error    4063 -           Object does not exist ^  (P80D)

./dsdt_fixed.txt    89:         P8XH (Zero, Arg0)
Error    4063 -                    ^ Object does not exist (P8XH)

./dsdt_fixed.txt    92:             Store (Zero, \_SB.PCI0.LPCB.EC0.XSEC)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.XSEC)

./dsdt_fixed.txt    93:             Store (Zero, \_SB.PCI0.LPCB.EC0.SLMS)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.SLMS)

./dsdt_fixed.txt    94:             Store (One, S4FG)
Error    4063 -              Object does not exist ^  (S4FG)

./dsdt_fixed.txt    99:             Store (Zero, \_SB.PCI0.LPCB.EC0.XSEC)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.XSEC)

./dsdt_fixed.txt   104:             Store (One, \_SB.PCI0.LPCB.EC0.S3FG)
Error    4063 -                                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0.S3FG)

./dsdt_fixed.txt   108:     Method (_WAK, 1, NotSerialized)
Error    4063 -  Object does not exist ^  (_WAK)

./dsdt_fixed.txt   110:         P8XH (One, 0xAB)
Error    4063 -                    ^ Object does not exist (P8XH)

./dsdt_fixed.txt   115:                 If (LAnd (And (CFGD, 0xF0), LEqual (OSYS, 0x07D1)))
Error    4063 -                                          Object does not exist ^  (OSYS)

./dsdt_fixed.txt   117:                     TRAP (0x3D)
Error    4063 -          Object does not exist ^  (TRAP)

./dsdt_fixed.txt   122:         If (LEqual (RP1D, Zero))
Error    4063 -          Object does not exist ^  (RP1D)

./dsdt_fixed.txt   124:             Notify (\_SB.PCI0.RP01, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP01)

./dsdt_fixed.txt   127:         If (LEqual (RP2D, Zero))
Error    4063 -          Object does not exist ^  (RP2D)

./dsdt_fixed.txt   129:             Notify (\_SB.PCI0.RP02, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP02)

./dsdt_fixed.txt   132:         If (LEqual (RP3D, Zero))
Error    4063 -          Object does not exist ^  (RP3D)

./dsdt_fixed.txt   134:             Notify (\_SB.PCI0.RP03, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP03)

./dsdt_fixed.txt   137:         If (LEqual (RP4D, Zero))
Error    4063 -          Object does not exist ^  (RP4D)

./dsdt_fixed.txt   139:             Notify (\_SB.PCI0.RP04, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP04)

./dsdt_fixed.txt   142:         If (LEqual (RP5D, Zero))
Error    4063 -          Object does not exist ^  (RP5D)

./dsdt_fixed.txt   144:             Notify (\_SB.PCI0.RP05, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP05)

./dsdt_fixed.txt   147:         If (LEqual (RP6D, Zero))
Error    4063 -          Object does not exist ^  (RP6D)

./dsdt_fixed.txt   149:             Notify (\_SB.PCI0.RP06, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP06)

./dsdt_fixed.txt   152:         \_SB.PCI0.LPCB.EC0._REG (0x03, One)
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0._REG)

./dsdt_fixed.txt   155:             If (PCIW)
Error    4063 -      Object does not exist ^  (PCIW)

./dsdt_fixed.txt   157:                 Notify (\_SB.PWRB, 0x02)
Error    4063 -                   Object does not exist ^  (\_SB.PWRB)

./dsdt_fixed.txt   163:             Notify (\_SB.PWRB, 0x02)
Error    4063 -               Object does not exist ^  (\_SB.PWRB)

./dsdt_fixed.txt   166:         \_PR.RPPC ()
Error    4063 -   Object does not exist ^  (\_PR.RPPC)

./dsdt_fixed.txt   167:         Store (Zero, \_SB.PCI0.LPCB.EC0.APST)
Error    4063 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.APST)

./dsdt_fixed.txt   168:         Store (Zero, \_SB.PCI0.LPCB.EC0.APTH)
Error    4063 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.APTH)

./dsdt_fixed.txt   169:         \_SB.PCI0.LPCB.EC0._Q07 ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0._Q07)

./dsdt_fixed.txt   170:         P8XH (Zero, 0xCD)
Error    4063 -                    ^ Object does not exist (P8XH)

./dsdt_fixed.txt   178:     Method (GETB, 3, Serialized)
Error    4063 -  Object does not exist ^  (GETB)

./dsdt_fixed.txt   182:         CreateField (Arg2, Local0, Local1, TBF3)
Error    4063 -           Object does not exist ^  (TBF3)

./dsdt_fixed.txt   183:         Return (TBF3)
Error    4063 -      Object does not exist ^  (TBF3)

./dsdt_fixed.txt   186:     Method (PNOT, 0, Serialized)
Error    4063 -  Object does not exist ^  (PNOT)

./dsdt_fixed.txt   188:         If (MPEN)
Error    4063 -  Object does not exist ^  (MPEN)

./dsdt_fixed.txt   192:                 Notify (\_PR.CPU0, 0x80)
Error    4063 -                   Object does not exist ^  (\_PR.CPU0)

./dsdt_fixed.txt   196:                     Notify (\_PR.CPU0, 0x81)
Error    4063 -                       Object does not exist ^  (\_PR.CPU0)

./dsdt_fixed.txt   202:                 Notify (\_PR.CPU1, 0x80)
Error    4063 -                   Object does not exist ^  (\_PR.CPU1)

./dsdt_fixed.txt   206:                     Notify (\_PR.CPU1, 0x81)
Error    4063 -                       Object does not exist ^  (\_PR.CPU1)

./dsdt_fixed.txt   212:             Notify (\_PR.CPU0, 0x80)
Error    4063 -               Object does not exist ^  (\_PR.CPU0)

./dsdt_fixed.txt   214:             Notify (\_PR.CPU0, 0x81)
Error    4063 -               Object does not exist ^  (\_PR.CPU0)

./dsdt_fixed.txt   218:     Method (TRAP, 1, Serialized)
Error    4063 -  Object does not exist ^  (TRAP)

./dsdt_fixed.txt   220:         Store (Arg0, SMIF)
Error    4063 -           Object does not exist ^  (SMIF)

./dsdt_fixed.txt   221:         Store (Zero, TRP0)
Error    4063 -           Object does not exist ^  (TRP0)

./dsdt_fixed.txt   222:         Return (SMIF)
Error    4063 -      Object does not exist ^  (SMIF)

./dsdt_fixed.txt   227:         Method (_INI, 0, NotSerialized)
Error    4063 -      Object does not exist ^  (_INI)

./dsdt_fixed.txt   229:             Store (0x07D0, OSYS)
Error    4063 -                 Object does not exist ^  (OSYS)

./dsdt_fixed.txt   234:                     Store (One, LINX)
Error    4063 -                      Object does not exist ^  (LINX)

./dsdt_fixed.txt   239:                     Store (0x07D1, OSYS)
Error    4063 -                         Object does not exist ^  (OSYS)

./dsdt_fixed.txt   244:                     Store (0x07D1, OSYS)
Error    4063 -                         Object does not exist ^  (OSYS)

./dsdt_fixed.txt   249:                     Store (0x07D2, OSYS)
Error    4063 -                         Object does not exist ^  (OSYS)

./dsdt_fixed.txt   254:                     Store (0x07D6, OSYS)
Error    4063 -                         Object does not exist ^  (OSYS)

./dsdt_fixed.txt   260:     OperationRegion (GNVS, SystemMemory, 0x7F6DEDBC, 0x0100)
Error    4063 -           Object does not exist ^  (GNVS)

./dsdt_fixed.txt   261:     Field (GNVS, AnyAcc, Lock, Preserve)
Error    4063 - Object does not exist ^  (GNVS)

./dsdt_fixed.txt   263:         OSYS,   16, 
Error    4063 -                    ^ Object does not exist (OSYS)

./dsdt_fixed.txt   264:         SMIF,   8, 
Error    4063 -                    ^ Object does not exist (SMIF)

./dsdt_fixed.txt   265:         PRM0,   8, 
Error    4063 -                    ^ Object does not exist (PRM0)

./dsdt_fixed.txt   266:         PRM1,   8, 
Error    4063 -                    ^ Object does not exist (PRM1)

./dsdt_fixed.txt   267:         SCIF,   8, 
Error    4063 -                    ^ Object does not exist (SCIF)

./dsdt_fixed.txt   268:         PRM2,   8, 
Error    4063 -                    ^ Object does not exist (PRM2)

./dsdt_fixed.txt   269:         PRM3,   8, 
Error    4063 -                    ^ Object does not exist (PRM3)

./dsdt_fixed.txt   270:         LCKF,   8, 
Error    4063 -                    ^ Object does not exist (LCKF)

./dsdt_fixed.txt   271:         PRM4,   8, 
Error    4063 -                    ^ Object does not exist (PRM4)

./dsdt_fixed.txt   272:         PRM5,   8, 
Error    4063 -                    ^ Object does not exist (PRM5)

./dsdt_fixed.txt   273:         P80D,   32, 
Error    4063 -                    ^ Object does not exist (P80D)

./dsdt_fixed.txt   274:         LIDS,   8, 
Error    4063 -                    ^ Object does not exist (LIDS)

./dsdt_fixed.txt   275:         PWRS,   8, 
Error    4063 -                    ^ Object does not exist (PWRS)

./dsdt_fixed.txt   276:         DBGS,   8, 
Error    4063 -                    ^ Object does not exist (DBGS)

./dsdt_fixed.txt   277:         LINX,   8, 
Error    4063 -                    ^ Object does not exist (LINX)

./dsdt_fixed.txt   279:         ACT1,   8, 
Error    4063 -                    ^ Object does not exist (ACT1)

./dsdt_fixed.txt   280:         ACTT,   8, 
Error    4063 -                    ^ Object does not exist (ACTT)

./dsdt_fixed.txt   281:         PSVT,   8, 
Error    4063 -                    ^ Object does not exist (PSVT)

./dsdt_fixed.txt   282:         TC1V,   8, 
Error    4063 -                    ^ Object does not exist (TC1V)

./dsdt_fixed.txt   283:         TC2V,   8, 
Error    4063 -                    ^ Object does not exist (TC2V)

./dsdt_fixed.txt   284:         TSPV,   8, 
Error    4063 -                    ^ Object does not exist (TSPV)

./dsdt_fixed.txt   285:         CRTT,   8, 
Error    4063 -                    ^ Object does not exist (CRTT)

./dsdt_fixed.txt   286:         DTSE,   8, 
Error    4063 -                    ^ Object does not exist (DTSE)

./dsdt_fixed.txt   287:         DTS1,   8, 
Error    4063 -                    ^ Object does not exist (DTS1)

./dsdt_fixed.txt   288:         DTS2,   8, 
Error    4063 -                    ^ Object does not exist (DTS2)

./dsdt_fixed.txt   290:         APIC,   8, 
Error    4063 -                    ^ Object does not exist (APIC)

./dsdt_fixed.txt   291:         MPEN,   8, 
Error    4063 -                    ^ Object does not exist (MPEN)

./dsdt_fixed.txt   292:         PCP0,   8, 
Error    4063 -                    ^ Object does not exist (PCP0)

./dsdt_fixed.txt   293:         PCP1,   8, 
Error    4063 -                    ^ Object does not exist (PCP1)

./dsdt_fixed.txt   294:         PPCM,   8, 
Error    4063 -                    ^ Object does not exist (PPCM)

./dsdt_fixed.txt   297:         IGDS,   8, 
Error    4063 -                    ^ Object does not exist (IGDS)

./dsdt_fixed.txt   298:         TLST,   8, 
Error    4063 -                    ^ Object does not exist (TLST)

./dsdt_fixed.txt   299:         CADL,   8, 
Error    4063 -                    ^ Object does not exist (CADL)

./dsdt_fixed.txt   300:         PADL,   8, 
Error    4063 -                    ^ Object does not exist (PADL)

./dsdt_fixed.txt   301:         CSTE,   16, 
Error    4063 -                    ^ Object does not exist (CSTE)

./dsdt_fixed.txt   302:         NSTE,   16, 
Error    4063 -                    ^ Object does not exist (NSTE)

./dsdt_fixed.txt   303:         SSTE,   16, 
Error    4063 -                    ^ Object does not exist (SSTE)

./dsdt_fixed.txt   304:         NDID,   8, 
Error    4063 -                    ^ Object does not exist (NDID)

./dsdt_fixed.txt   305:         DID1,   32, 
Error    4063 -                    ^ Object does not exist (DID1)

./dsdt_fixed.txt   306:         DID2,   32, 
Error    4063 -                    ^ Object does not exist (DID2)

./dsdt_fixed.txt   307:         DID3,   32, 
Error    4063 -                    ^ Object does not exist (DID3)

./dsdt_fixed.txt   308:         DID4,   32, 
Error    4063 -                    ^ Object does not exist (DID4)

./dsdt_fixed.txt   309:         DID5,   32, 
Error    4063 -                    ^ Object does not exist (DID5)

./dsdt_fixed.txt   311:         BLCS,   8, 
Error    4063 -                    ^ Object does not exist (BLCS)

./dsdt_fixed.txt   312:         BRTL,   8, 
Error    4063 -                    ^ Object does not exist (BRTL)

./dsdt_fixed.txt   313:         ALSE,   8, 
Error    4063 -                    ^ Object does not exist (ALSE)

./dsdt_fixed.txt   314:         ALAF,   8, 
Error    4063 -                    ^ Object does not exist (ALAF)

./dsdt_fixed.txt   315:         LLOW,   8, 
Error    4063 -                    ^ Object does not exist (LLOW)

./dsdt_fixed.txt   316:         LHIH,   8, 
Error    4063 -                    ^ Object does not exist (LHIH)

./dsdt_fixed.txt   318:         EMAE,   8, 
Error    4063 -                    ^ Object does not exist (EMAE)

./dsdt_fixed.txt   319:         EMAP,   16, 
Error    4063 -                    ^ Object does not exist (EMAP)

./dsdt_fixed.txt   320:         EMAL,   16, 
Error    4063 -                    ^ Object does not exist (EMAL)

./dsdt_fixed.txt   322:         MEFE,   8, 
Error    4063 -                    ^ Object does not exist (MEFE)

./dsdt_fixed.txt   324:         TPMP,   8, 
Error    4063 -                    ^ Object does not exist (TPMP)

./dsdt_fixed.txt   325:         TPME,   8, 
Error    4063 -                    ^ Object does not exist (TPME)

./dsdt_fixed.txt   327:         GTF0,   56, 
Error    4063 -                    ^ Object does not exist (GTF0)

./dsdt_fixed.txt   328:         GTF2,   56, 
Error    4063 -                    ^ Object does not exist (GTF2)

./dsdt_fixed.txt   329:         IDEM,   8, 
Error    4063 -                    ^ Object does not exist (IDEM)

./dsdt_fixed.txt   330:         GTF1,   56, 
Error    4063 -                    ^ Object does not exist (GTF1)

./dsdt_fixed.txt   332:         ASLB,   32, 
Error    4063 -                    ^ Object does not exist (ASLB)

./dsdt_fixed.txt   333:         IBTT,   8, 
Error    4063 -                    ^ Object does not exist (IBTT)

./dsdt_fixed.txt   334:         IPAT,   8, 
Error    4063 -                    ^ Object does not exist (IPAT)

./dsdt_fixed.txt   335:         ITVF,   8, 
Error    4063 -                    ^ Object does not exist (ITVF)

./dsdt_fixed.txt   336:         ITVM,   8, 
Error    4063 -                    ^ Object does not exist (ITVM)

./dsdt_fixed.txt   337:         IPSC,   8, 
Error    4063 -                    ^ Object does not exist (IPSC)

./dsdt_fixed.txt   338:         IBLC,   8, 
Error    4063 -                    ^ Object does not exist (IBLC)

./dsdt_fixed.txt   339:         IBIA,   8, 
Error    4063 -                    ^ Object does not exist (IBIA)

./dsdt_fixed.txt   340:         ISSC,   8, 
Error    4063 -                    ^ Object does not exist (ISSC)

./dsdt_fixed.txt   341:         I409,   8, 
Error    4063 -                    ^ Object does not exist (I409)

./dsdt_fixed.txt   342:         I509,   8, 
Error    4063 -                    ^ Object does not exist (I509)

./dsdt_fixed.txt   343:         I609,   8, 
Error    4063 -                    ^ Object does not exist (I609)

./dsdt_fixed.txt   344:         I709,   8, 
Error    4063 -                    ^ Object does not exist (I709)

./dsdt_fixed.txt   345:         IDMM,   8, 
Error    4063 -                    ^ Object does not exist (IDMM)

./dsdt_fixed.txt   346:         IDMS,   8, 
Error    4063 -                    ^ Object does not exist (IDMS)

./dsdt_fixed.txt   347:         IF1E,   8, 
Error    4063 -                    ^ Object does not exist (IF1E)

./dsdt_fixed.txt   348:         HVCO,   8, 
Error    4063 -                    ^ Object does not exist (HVCO)

./dsdt_fixed.txt   349:         NXD1,   32, 
Error    4063 -                    ^ Object does not exist (NXD1)

./dsdt_fixed.txt   350:         NXD2,   32, 
Error    4063 -                    ^ Object does not exist (NXD2)

./dsdt_fixed.txt   351:         NXD3,   32, 
Error    4063 -                    ^ Object does not exist (NXD3)

./dsdt_fixed.txt   352:         NXD4,   32, 
Error    4063 -                    ^ Object does not exist (NXD4)

./dsdt_fixed.txt   353:         NXD5,   32, 
Error    4063 -                    ^ Object does not exist (NXD5)

./dsdt_fixed.txt   354:         NXD6,   32, 
Error    4063 -                    ^ Object does not exist (NXD6)

./dsdt_fixed.txt   355:         NXD7,   32, 
Error    4063 -                    ^ Object does not exist (NXD7)

./dsdt_fixed.txt   356:         NXD8,   32
Error    4063 -                    ^ Object does not exist (NXD8)

./dsdt_fixed.txt   359:     Name (DSEN, One)
Error    4063 -                      ^ Object does not exist (DSEN)

./dsdt_fixed.txt   360:     Name (ECON, Zero)
Error    4063 -                      ^ Object does not exist (ECON)

./dsdt_fixed.txt   361:     Name (GPIC, Zero)
Error    4063 -                      ^ Object does not exist (GPIC)

./dsdt_fixed.txt   362:     Name (CTYP, Zero)
Error    4063 -                      ^ Object does not exist (CTYP)

./dsdt_fixed.txt   363:     Name (L01C, Zero)
Error    4063 -                      ^ Object does not exist (L01C)

./dsdt_fixed.txt   364:     Name (VFN0, Zero)
Error    4063 -                      ^ Object does not exist (VFN0)

./dsdt_fixed.txt   365:     Name (VFN1, Zero)
Error    4063 -                      ^ Object does not exist (VFN1)

./dsdt_fixed.txt   368:         Method (_L01, 0, NotSerialized)
Error    4063 -      Object does not exist ^  (_L01)

./dsdt_fixed.txt   370:             Add (L01C, One, L01C)
Error    4063 -       Object does not exist ^  (L01C)

./dsdt_fixed.txt   370:             Add (L01C, One, L01C)
Error    4063 -                  Object does not exist ^  (L01C)

./dsdt_fixed.txt   371:             P8XH (Zero, One)
Error    4063 -  Object does not exist ^  (P8XH)

./dsdt_fixed.txt   372:             P8XH (One, L01C)
Error    4063 -  Object does not exist ^  (P8XH)

./dsdt_fixed.txt   372:             P8XH (One, L01C)
Error    4063 -             Object does not exist ^  (L01C)

./dsdt_fixed.txt   373:             If (LAnd (LEqual (RP1D, Zero), \_SB.PCI0.RP01.HPSX))
Error    4063 -                    Object does not exist ^  (RP1D)

./dsdt_fixed.txt   373:             If (LAnd (LEqual (RP1D, Zero), \_SB.PCI0.RP01.HPSX))
Error    4063 -                                                Object does not exist ^  (\_SB.PCI0.RP01.HPSX)

./dsdt_fixed.txt   376:                 If (\_SB.PCI0.RP01.PDCX)
Error    4063 -                         Object does not exist ^  (\_SB.PCI0.RP01.PDCX)

./dsdt_fixed.txt   378:                     Store (One, \_SB.PCI0.RP01.PDCX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP01.PDCX)

./dsdt_fixed.txt   379:                     Store (One, \_SB.PCI0.RP01.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP01.HPSX)

./dsdt_fixed.txt   380:                     Notify (\_SB.PCI0.RP01, Zero)
Error    4063 -                            Object does not exist ^  (\_SB.PCI0.RP01)

./dsdt_fixed.txt   384:                     Store (One, \_SB.PCI0.RP01.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP01.HPSX)

./dsdt_fixed.txt   388:             If (LAnd (LEqual (RP2D, Zero), \_SB.PCI0.RP02.HPSX))
Error    4063 -                    Object does not exist ^  (RP2D)

./dsdt_fixed.txt   388:             If (LAnd (LEqual (RP2D, Zero), \_SB.PCI0.RP02.HPSX))
Error    4063 -                                                Object does not exist ^  (\_SB.PCI0.RP02.HPSX)

./dsdt_fixed.txt   391:                 If (\_SB.PCI0.RP02.PDCX)
Error    4063 -                         Object does not exist ^  (\_SB.PCI0.RP02.PDCX)

./dsdt_fixed.txt   393:                     Store (One, \_SB.PCI0.RP02.PDCX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP02.PDCX)

./dsdt_fixed.txt   394:                     Store (One, \_SB.PCI0.RP02.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP02.HPSX)

./dsdt_fixed.txt   395:                     Notify (\_SB.PCI0.RP02, Zero)
Error    4063 -                            Object does not exist ^  (\_SB.PCI0.RP02)

./dsdt_fixed.txt   399:                     Store (One, \_SB.PCI0.RP02.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP02.HPSX)

./dsdt_fixed.txt   403:             If (LAnd (LEqual (RP3D, Zero), \_SB.PCI0.RP03.HPSX))
Error    4063 -                    Object does not exist ^  (RP3D)

./dsdt_fixed.txt   403:             If (LAnd (LEqual (RP3D, Zero), \_SB.PCI0.RP03.HPSX))
Error    4063 -                                                Object does not exist ^  (\_SB.PCI0.RP03.HPSX)

./dsdt_fixed.txt   406:                 If (\_SB.PCI0.RP03.PDCX)
Error    4063 -                         Object does not exist ^  (\_SB.PCI0.RP03.PDCX)

./dsdt_fixed.txt   408:                     Store (One, \_SB.PCI0.RP03.PDCX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP03.PDCX)

./dsdt_fixed.txt   409:                     Store (One, \_SB.PCI0.RP03.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP03.HPSX)

./dsdt_fixed.txt  4008:                         Return (Package (0x00) {})
Remark   5071 -                Effective AML package length is zero ^ 


Maximum error count (200) exceeded
ASL Input:  ./dsdt_fixed.txt - 6346 lines, 212590 bytes, 2447 keywords
Compilation complete. 201 Errors, 0 Warnings, 1 Remarks, 4 Optimizations

```

---

### Post by sergiom99 on 2009-08-10
Talk to the DSDT magician:
[http://ubuntuforums.org/showthread.php?t=1036051&page=24](http://ubuntuforums.org/showthread.php?t=1036051&page=24)

---

### Post by kidalive on 2009-08-11
> **sergiom99 said:**
> Talk to the DSDT magician:
[http://ubuntuforums.org/showthread.php?t=1036051&page=24](http://ubuntuforums.org/showthread.php?t=1036051&page=24)

I already did. How long will it take?

---

### Post by sergiom99 on 2009-08-11
Since he does it for free and willing to help, we cannot ask him for much, can't we?

I'm glad he's been helping people for several months touching our DSDT files.

---

