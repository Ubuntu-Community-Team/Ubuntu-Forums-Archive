---
title: "Problem with DSDT"
date: 2008-10-10
forum: Hardware
---

### Post by ground21 on 2008-10-10
I have a FS Amilo Pro V2030 laptop. My fan is working all the time. So I'm fighting with DSDT. Here is the problem:
iasl -tc DSDT.dsl command prints this output:

```

root@kuba-laptop:~# iasl -tc DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

DSDT.dsl   188:     Method (\_WAK, 1, NotSerialized)
Warning  1079 -                 ^ Reserved method must return a value (_WAK)

DSDT.dsl  2531:         ^^THRM.SFAN (Zero)
Error    4063 -                   ^ Object not found or not accessible from scope (^^THRM.SFAN)

DSDT.dsl  2535:         ^^THRM.SFAN (One)
Error    4063 -                   ^ Object not found or not accessible from scope (^^THRM.SFAN)

DSDT.dsl  2539:         ^^THRM.SFAN (0x02)
Error    4063 -                   ^ Object not found or not accessible from scope (^^THRM.SFAN)

DSDT.dsl  2543:         ^^THRM.SFAN (0x03)
Error    4063 -                   ^ Object not found or not accessible from scope (^^THRM.SFAN)

ASL Input:  DSDT.dsl - 3569 lines, 123834 bytes, 1714 keywords
Compilation complete. 4 Errors, 1 Warnings, 0 Remarks, 548 Optimizations
```

And I see no .aml file... 
What is wrong with my dsl file? I have changed only Device (FAN) section ([http://ubuntuforums.org/showthread.php?t=482900]("http://ubuntuforums.org/showthread.php?t=482900"))

---

### Post by ground21 on 2008-10-14
This is my DSDT.dsl file:
```
/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20061109
 *
 * Disassembly of DSDT.dat, Fri Oct 10 13:54:39 2008
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x00003FCB (16331)
 *     Revision         0x01
 *     OEM ID           "FIC   "
 *     OEM Table ID     "LM7R    "
 *     OEM Revision     0x06040000 (100925440)
 *     Creator ID       "MSFT"
 *     Creator Revision 0x0100000E (16777230)
 */
DefinitionBlock ("DSDT.aml", "DSDT", 1, "FIC   ", "LM7R    ", 0x06040000)
{
    Scope (\_PR)
    {
        Processor (CPU0, 0x00, 0x00004010, 0x06) {}
    }

    Scope (\)
    {
        Name (PICF, 0x00)
        Method (_PIC, 1, NotSerialized)
        {
            Store (Arg0, PICF)
        }
    }

    Name (_S0, Package (0x02)
    {
        0x00, 
        0x00
    })
    Name (_S3, Package (0x02)
    {
        0x01, 
        0x01
    })
    Name (_S4, Package (0x02)
    {
        0x02, 
        0x02
    })
    Name (_S5, Package (0x02)
    {
        0x02, 
        0x02
    })
    Scope (\_SB)
    {
        Name (OSTB, Ones)
        OperationRegion (OSTY, SystemMemory, 0x4BEB8F4C, 0x00000001)
        Field (OSTY, AnyAcc, NoLock, Preserve)
        {
            TPOS,   8
        }

        Method (OSTP, 0, NotSerialized)
        {
            If (LEqual (^OSTB, Ones))
            {
                If (CondRefOf (\_OSI, Local0))
                {
                    If (\_OSI ("Windows 2001"))
                    {
                        Store (0x08, ^OSTB)
                        Store (0x08, ^TPOS)
                    }
                    Else
                    {
                        Store (0x00, ^OSTB)
                        Store (0x00, ^TPOS)
                    }
                }
                Else
                {
                    If (CondRefOf (\_OS, Local0))
                    {
                        If (^SEQL (\_OS, "Microsoft Windows"))
                        {
                            Store (0x01, ^OSTB)
                            Store (0x01, ^TPOS)
                        }
                        Else
                        {
                            If (^SEQL (\_OS, "Microsoft WindowsME: Millennium Edition"))
                            {
                                Store (0x02, ^OSTB)
                                Store (0x02, ^TPOS)
                            }
                            Else
                            {
                                If (^SEQL (\_OS, "Microsoft Windows NT"))
                                {
                                    Store (0x04, ^OSTB)
                                    Store (0x04, ^TPOS)
                                }
                                Else
                                {
                                    Store (0x00, ^OSTB)
                                    Store (0x00, ^TPOS)
                                }
                            }
                        }
                    }
                    Else
                    {
                        Store (0x00, ^OSTB)
                        Store (0x00, ^TPOS)
                    }
                }
            }

            Return (^OSTB)
        }

        Method (SEQL, 2, Serialized)
        {
            Store (SizeOf (Arg0), Local0)
            Store (SizeOf (Arg1), Local1)
            If (LNotEqual (Local0, Local1))
            {
                Return (Zero)
            }

            Name (BUF0, Buffer (Local0) {})
            Store (Arg0, BUF0)
            Name (BUF1, Buffer (Local0) {})
            Store (Arg1, BUF1)
            Store (Zero, Local2)
            While (LLess (Local2, Local0))
            {
                Store (DerefOf (Index (BUF0, Local2)), Local3)
                Store (DerefOf (Index (BUF1, Local2)), Local4)
                If (LNotEqual (Local3, Local4))
                {
                    Return (Zero)
                }

                Increment (Local2)
            }

            Return (One)
        }
    }

    Method (\_PTS, 1, NotSerialized)
    {
        \_SB.Z000 (0xA0)
        SFAN (0x03)
        If (LEqual (Arg0, 0x03))
        {
            Store (Zero, \_SB.PCI0.PIB.GPSU)
            Or (\_SB.PCI0.PIB.PMRD (0xE0), 0x01, Local5)
            \_SB.PCI0.PIB.PMWT (0xE0, Local5)
            And (\_SB.PCI0.PIB.PMRD (0xB5), 0x01, Local1)
            If (Local1)
            {
                Or (\_SB.PCI0.PIB.PMRD (0xB7), 0x01, Local7)
                \_SB.PCI0.PIB.PMWT (0xB7, Local7)
            }
        }

        If (LEqual (Arg0, 0x04))
        {
            Store (Zero, \_SB.PCI0.PIB.THEN)
            \_SB.Z000 (0xA8)
        }

        If (LEqual (Arg0, 0x05))
        {
            Or (\_SB.PCI0.PIB.PMRD (0xB5), 0x20, Local0)
            \_SB.PCI0.PIB.PMWT (0xB5, Local0)
            \_SB.Z000 (0xA7)
        }

        CLTH (0x00)
        And (\_SB.PCI0.PIB.PMRD (0xB5), 0xE7, Local0)
        \_SB.PCI0.PIB.PMWT (0xB5, Local0)
        Store (Arg0, \_SB.PCI0.PIB.Z001)
    }

    Method (\_WAK, 1, NotSerialized)
    {
        If (LEqual (Arg0, 0x03))
        {
            \_SB.Z000 (0xA1)
            Or (\_SB.PCI0.PIB.PMRD (0xB5), 0x18, Local0)
            \_SB.PCI0.PIB.PMWT (0xB5, Local0)
            And (\_SB.PCI0.PIB.PMRD (0xB7), 0xFE, Local7)
            \_SB.PCI0.PIB.PMWT (0xB7, Local7)
            And (\_SB.PCI0.PIB.PMRD (0xE0), 0xFE, Local5)
            \_SB.PCI0.PIB.PMWT (0xE0, Local5)
        }

        If (LEqual (Arg0, 0x04))
        {
            \_TZ.PFAN._ON ()
            Notify (\_SB.PCI0, 0x80)
            Notify (\_SB.PWRB, 0x02)
        }

        CLTH (0x0C)
        Store (0xA0, Local1)
        Add (Local1, Arg0, Local1)
        Store (Local1, \_SB.PCI0.PIB.Z001)
    }

    Scope (_GPE)
    {
        Mutex (GLCK, 0x00)
        Method (_L01, 0, NotSerialized)
        {
            Acquire (\_GPE.GLCK, 0xFFFF)
            Store (\_SB.PCI0.PIB.PMRD (0xAB), Local0)
            Store (\_SB.PCI0.PIB.PMRD (0xAF), Local4)
            And (Local4, 0x04, Local7)
            If (LNotEqual (Local7, Zero))
            {
                \_SB.PCI0.PIB.PMMW (0x01E8, 0x00)
            }

            If (LGreaterEqual (Local4, 0x01))
            {
                Store (\_SB.PCI0.PIB.PMRD (0xE7), Local4)
                Store (0x01, Local2)
                Store (0x00, Local7)
                While (Local2)
                {
                    Store (DerefOf (Index (\_TZ.THRM.HILM, Local7)), Local6)
                    If (LGreater (Local6, Local4))
                    {
                        \_SB.PCI0.PIB.PMWT (0xE5, DerefOf (Index (\_TZ.THRM.LOLM, Local7)))
                        \_SB.PCI0.PIB.PMWT (0xE4, DerefOf (Index (\_TZ.THRM.HILM, Local7)))
                        Store (0x00, Local2)
                    }

                    SFAN (DerefOf (Index (\_TZ.THRM.FANS, Local7)))
                    Notify (\_TZ.THRM, 0x80)
                    If (LGreater (Increment (Local7), 0x03))
                    {
                        Break
                    }
                }

                And (\_SB.PCI0.PIB.PMRD (0xAD), 0xFE, Local5)
                \_SB.PCI0.PIB.PMWT (0xAD, Local5)
                \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
                And (\_SB.PCI0.PIB.PMRD (0xAE), 0xFE, Local5)
                \_SB.PCI0.PIB.PMWT (0xAE, Local5)
                \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
                And (\_SB.PCI0.PIB.PMRD (0xAF), 0xFC, Local5)
                \_SB.PCI0.PIB.PMWT (0xAF, Local5)
                \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
            }

            If (And (Local0, 0x01, Local3))
            {
                Notify (\_SB.ACAD, 0x80)
                And (\_SB.PCI0.PIB.PMRD (0xAB), 0xFE, Local2)
                \_SB.PCI0.PIB.PMWT (0xAB, Local2)
                \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
                \_SB.Z000 (0xA6)
            }

            If (And (Local0, 0x02, Local3))
            {
                Notify (\_SB.ACAD, 0x80)
                Store (\_SB.PCI0.PIB.PMRD (0xA1), Local1)
                Store (\_SB.PCI0.PIB.PMRD (0xF1), Local4)
                If (LNotEqual (And (Local1, 0x01, Local3), And (Local4, 0x01, 
                    Local5)))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local6)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local6)
                    Notify (\_SB.BAT0, 0x81)
                }

                If (LNotEqual (And (Local1, 0x02, Local3), And (Local4, 0x02, 
                    Local5)))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local6)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local6)
                    Notify (\_SB.BAT0, 0x80)
                }

                If (LNotEqual (And (Local1, 0x04, Local3), And (Local4, 0x04, 
                    Local5)))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local6)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local6)
                    Notify (\_SB.BAT0, 0x80)
                }

                If (LNotEqual (And (Local1, 0x08, Local3), And (Local4, 0x08, 
                    Local5)))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local6)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local6)
                    Notify (\_SB.BAT0, 0x80)
                }

                If (LNotEqual (And (Local1, 0x10, Local3), And (Local4, 0x10, 
                    Local5)))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local6)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local6)
                    Notify (\_SB.BAT0, 0x80)
                }

                If (LNotEqual (And (Local1, 0x20, Local3), And (Local4, 0x20, 
                    Local5)))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local6)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local6)
                    Notify (\_SB.BAT0, 0x80)
                }

                If (LNotEqual (And (Local1, 0x40, Local3), And (Local4, 0x40, 
                    Local5)))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local6)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local6)
                    Notify (\_SB.BAT0, 0x80)
                }

                If (LNotEqual (And (Local1, 0x80, Local3), And (Local4, 0x80, 
                    Local5)))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local6)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local6)
                    Notify (\_SB.BAT0, 0x80)
                }

                And (\_SB.PCI0.PIB.PMRD (0xAB), 0xFD, Local2)
                \_SB.PCI0.PIB.PMWT (0xAB, Local2)
                \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
            }

            Release (\_GPE.GLCK)
        }

        Method (_L03, 0, NotSerialized)
        {
            Notify (\_SB.PCI0, 0x02)
            Notify (\_SB.PWRB, 0x02)
        }

        Method (_L04, 0, NotSerialized)
        {
            If (LEqual (\_SB.PCI0.PPB.VGA.SWIT, 0x00))
            {
                Or (\_SB.PCI0.PIB.PMRD (0xFF), 0xC0, Local2)
                \_SB.PCI0.PIB.PMWT (0xFF, Local2)
            }

            Acquire (\_GPE.GLCK, 0xFFFF)
            \_SB.Z000 (0xA4)
            Release (\_GPE.GLCK)
            And (\_SB.PCI0.PIB.PMRD (0xFF), 0x30, Local2)
            ShiftRight (Local2, 0x04, Local2)
            If (Local2)
            {
                And (Local2, 0x01, Local1)
                Store (Local1, \_SB.PCI0.PPB.VGA.CRTA)
                ShiftRight (Local2, 0x01, Local2)
                And (Local2, 0x01, Local1)
                Store (Local1, \_SB.PCI0.PPB.VGA.LCDA)
                Notify (\_SB.PCI0.PPB.VGA, 0x80)
            }

            And (\_SB.PCI0.PIB.PMRD (0xFF), 0x0F, Local2)
            \_SB.PCI0.PIB.PMWT (0xFF, Local2)
        }

        Method (_L05, 0, NotSerialized)
        {
            Notify (\_SB.PCI0, 0x02)
        }

        Method (_L08, 0, NotSerialized)
        {
            Acquire (\_GPE.GLCK, 0xFFFF)
            Store (\_SB.PCI0.PIB.PMRD (0xA8), Local0)
            Store (\_SB.PCI0.PIB.PMRD (0xA9), Local1)
            Store (\_SB.PCI0.PIB.PMRD (0xAA), Local2)
            If (And (Local0, 0x80, Local3))
            {
                And (\_SB.PCI0.PIB.PMRD (0xA8), 0x7F, Local7)
                \_SB.PCI0.PIB.PMWT (0xA8, Local7)
                \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
            }

            If (And (Local0, 0x40, Local3))
            {
                And (\_SB.PCI0.PIB.PMRD (0xA8), 0xBF, Local7)
                \_SB.PCI0.PIB.PMWT (0xA8, Local7)
                \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
            }

            If (And (Local0, 0x01, Local3))
            {
                Store (0x01, \_SB.LID.LIDF)
                Notify (\_SB.LID, 0x80)
                Store (\_SB.PCI0.PIB.PMRD (0xB8), Local4)
                Store (\_SB.PCI0.PIB.PMRD (0xB7), Local5)
                And (Local4, 0xFE, Local4)
                \_SB.PCI0.PIB.PMWT (0xB8, Local4)
                If (And (\_SB.PCI0.PIB.PMRD (0xB5), 0x01))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xB7), Local7)
                    And (Local7, 0xFE, Local7)
                    \_SB.PCI0.PIB.PMWT (0xB7, Local7)
                    Store (0x01, \_SB.LID.LIDF)
                }
                Else
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xB7), Local7)
                    Or (Local7, 0x01, Local7)
                    \_SB.PCI0.PIB.PMWT (0xB7, Local7)
                    Store (0x00, \_SB.LID.LIDF)
                }

                Store (\_SB.PCI0.PIB.PMRD (0xA8), Local6)
                And (Local6, 0xFE, Local6)
                \_SB.PCI0.PIB.PMWT (0xA8, Local6)
                \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
                Or (Local4, 0x01, Local4)
                \_SB.PCI0.PIB.PMWT (0xB8, Local4)
                Notify (\_SB.LID, 0x80)
            }

            And (\_SB.PCI0.PIB.PMRD (0xAC), 0xEF, Local7)
            \_SB.PCI0.PIB.PMWT (0xAC, Local7)
            \_SB.PCI0.PIB.PMWT (0xF0, 0x00)
            Release (\_GPE.GLCK)
        }

        Method (_L0B, 0, NotSerialized)
        {
            Notify (\_SB.PCI0, 0x02)
        }

        Method (_L0D, 0, NotSerialized)
        {
            Notify (\_SB.PCI0, 0x02)
            Notify (\_SB.PWRB, 0x02)
        }

        Method (_L0E, 0, NotSerialized)
        {
        }
    }

    OperationRegion (VGAM, SystemMemory, 0x000C0002, 0x01)
    Field (VGAM, ByteAcc, NoLock, Preserve)
    {
        VGA1,   8
    }

    Scope (\_SB)
    {
        OperationRegion (PSIB, SystemIO, 0x0000FE00, 0x00000002)
        Field (PSIB, AnyAcc, NoLock, Preserve)
        {
            SMIC,   8
        }

        OperationRegion (PSCB, SystemMemory, 0x4BEB8EBC, 0x00000090)
        Field (PSCB, AnyAcc, NoLock, Preserve)
        {
            BCMD,   8, 
            DID,    32, 
            INF,    1024
        }
    }

    Name (FWSO, "FWSO")
    Name (_PSC, 0x00)
    Method (_PS0, 0, NotSerialized)
    {
        Store (_PSC, Local0)
        Store (0x00, _PSC)
        If (LEqual (Local0, 0x03))
        {
            Store (0x01, \_SB.INF)
            While (\_SB.INF)
            {
                Store (0x20, \_SB.BCMD)
                Store (Zero, \_SB.SMIC)
                If (LAnd (LEqual (\_SB.INF, 0x01), LGreaterEqual (\_SB.OSTB, 0x04)))
                {
                    Sleep (0x01F4)
                }
            }
        }
    }

    Method (_PS3, 0, NotSerialized)
    {
        Store (0x03, _PSC)
    }

    Scope (\_SB)
    {
        Device (PWRB)
        {
            Name (_HID, EisaId ("PNP0C0C"))
        }

        Device (LID)
        {
            Name (_HID, EisaId ("PNP0C0D"))
            Name (LIDF, 0x01)
            Method (_LID, 0, NotSerialized)
            {
                Return (LIDF)
            }

            Name (_PRW, Package (0x02)
            {
                0x08, 
                0x03
            })
        }

        Device (PCI0)
        {
            Name (_HID, EisaId ("PNP0A03"))
            Name (_ADR, 0x00)
            Name (_BBN, 0x00)
            Method (_INI, 0, NotSerialized)
            {
                \_SB.OSTP ()
            }

            Method (_S3D, 0, NotSerialized)
            {
                Return (0x02)
            }

            Device (NBF3)
            {
                Name (_ADR, 0x03)
                OperationRegion (NBF3, PCI_Config, 0x00, 0x0100)
                Field (NBF3, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x82), 
                    SH82,   8, 
                    SH83,   8, 
                            Offset (0x88), 
                    EADD,   8
                }
            }

            Device (NBF5)
            {
                Name (_ADR, 0x05)
                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0B)
                }
            }

            Device (NBF7)
            {
                Name (_ADR, 0x07)
                OperationRegion (NBF7, PCI_Config, 0x00, 0x0100)
                Field (NBF7, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x47), 
                        ,   2, 
                    VLNK,   1
                }
            }

            Method (_STA, 0, NotSerialized)
            {
                Return (0x0F)
            }

            Name (CRES, ResourceTemplate ()
            {
                WordBusNumber (ResourceProducer, MinFixed, MaxFixed, PosDecode,
                    0x0000,             // Granularity
                    0x0000,             // Range Minimum
                    0x00FF,             // Range Maximum
                    0x0000,             // Translation Offset
                    0x0100,             // Length
                    ,, )
                IO (Decode16,
                    0x0CF8,             // Range Minimum
                    0x0CF8,             // Range Maximum
                    0x01,               // Alignment
                    0x08,               // Length
                    )
                WordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x0000,             // Granularity
                    0x0000,             // Range Minimum
                    0x0CF7,             // Range Maximum
                    0x0000,             // Translation Offset
                    0x0CF8,             // Length
                    ,, , TypeStatic)
                WordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x0000,             // Granularity
                    0x0D00,             // Range Minimum
                    0xFFFF,             // Range Maximum
                    0x0000,             // Translation Offset
                    0xF300,             // Length
                    ,, , TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00100000,         // Range Minimum
                    0xFFF7FFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0xFFF00000,         // Length
                    ,, _Y00, AddressRangeMemory, TypeStatic)
            })
            Method (_CRS, 0, NotSerialized)
            {
                CreateDWordField (CRES, \_SB.PCI0._Y00._MIN, TCMM)
                CreateDWordField (CRES, \_SB.PCI0._Y00._LEN, TOMM)
                Multiply (\_SB.PCI0.NBF3.EADD, 0x01000000, Local1)
                Store (Local1, TCMM)
                Subtract (0xFFE80000, Local1, TOMM)
                Return (CRES)
            }

            Name (_PRT, Package (0x1A)
            {
                Package (0x04)
                {
                    0x0001FFFF, 
                    0x00, 
                    0x00, 
                    0x10
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x01, 
                    0x00, 
                    0x11
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x0001FFFF, 
                    0x03, 
                    0x00, 
                    0x13
                }, 

                Package (0x04)
                {
                    0x000FFFFF, 
                    0x00, 
                    0x00, 
                    0x14
                }, 

                Package (0x04)
                {
                    0x000FFFFF, 
                    0x01, 
                    0x00, 
                    0x14
                }, 

                Package (0x04)
                {
                    0x000FFFFF, 
                    0x02, 
                    0x00, 
                    0x14
                }, 

                Package (0x04)
                {
                    0x000FFFFF, 
                    0x03, 
                    0x00, 
                    0x14
                }, 

                Package (0x04)
                {
                    0x0010FFFF, 
                    0x00, 
                    \_SB.PCI0.PIB.ALKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0010FFFF, 
                    0x01, 
                    \_SB.PCI0.PIB.ALKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0010FFFF, 
                    0x02, 
                    \_SB.PCI0.PIB.ALKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0010FFFF, 
                    0x03, 
                    \_SB.PCI0.PIB.ALKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0011FFFF, 
                    0x00, 
                    \_SB.PCI0.PIB.ALKA, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0011FFFF, 
                    0x01, 
                    \_SB.PCI0.PIB.ALKB, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0011FFFF, 
                    0x02, 
                    \_SB.PCI0.PIB.ALKC, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0011FFFF, 
                    0x03, 
                    \_SB.PCI0.PIB.ALKD, 
                    0x00
                }, 

                Package (0x04)
                {
                    0x0006FFFF, 
                    0x00, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x0006FFFF, 
                    0x01, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x0006FFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x000CFFFF, 
                    0x00, 
                    0x00, 
                    0x13
                }, 

                Package (0x04)
                {
                    0x000CFFFF, 
                    0x01, 
                    0x00, 
                    0x11
                }, 

                Package (0x04)
                {
                    0x000CFFFF, 
                    0x02, 
                    0x00, 
                    0x12
                }, 

                Package (0x04)
                {
                    0x0012FFFF, 
                    0x00, 
                    0x00, 
                    0x17
                }, 

                Package (0x04)
                {
                    0x0012FFFF, 
                    0x01, 
                    0x00, 
                    0x17
                }, 

                Package (0x04)
                {
                    0x0012FFFF, 
                    0x02, 
                    0x00, 
                    0x17
                }, 

                Package (0x04)
                {
                    0x0012FFFF, 
                    0x03, 
                    0x00, 
                    0x17
                }
            })
            Device (PIB)
            {
                Name (_ADR, 0x00110000)
                OperationRegion (IRQR, PCI_Config, 0x00, 0x0100)
                Field (IRQR, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x10), 
                        ,   4, 
                    THEN,   1, 
                            Offset (0x44), 
                    PIRE,   4, 
                    PIRF,   4, 
                    PIRG,   4, 
                    PIRH,   4, 
                            Offset (0x50), 
                    ESB4,   1, 
                    ESB5,   1, 
                    ESB3,   1, 
                    Z002,   1, 
                    ESB1,   1, 
                    ESB2,   1, 
                    AC97,   1, 
                    MC97,   1, 
                        ,   4, 
                    ELAN,   1, 
                        ,   4, 
                    ESBD,   1, 
                            Offset (0x55), 
                        ,   4, 
                    PIRA,   4, 
                    PIRB,   4, 
                    PIRC,   4, 
                        ,   4, 
                    PIRD,   4, 
                            Offset (0x5B), 
                        ,   1, 
                    EINT,   1, 
                            Offset (0x88), 
                    PMBS,   16, 
                            Offset (0x94), 
                        ,   4, 
                    GPSU,   1, 
                    SUSC,   1, 
                    STRP,   1, 
                            Offset (0x95), 
                    USBW,   1, 
                            Offset (0xD0), 
                    SMBS,   16, 
                    SMBC,   1
                }

                OperationRegion (PMIO, SystemIO, 0x4000, 0x50)
                Field (PMIO, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x2A), 
                    PACT,   1, 
                            Offset (0x2F), 
                    Z003,   8
                }

                OperationRegion (Z004, SystemIO, 0x80, 0x01)
                Field (Z004, ByteAcc, NoLock, Preserve)
                {
                    Z001,   8
                }

                Device (ALKA)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x05)
                    Name (_PRS, ResourceTemplate ()
                    {
                        Interrupt (ResourceConsumer, Level, ActiveLow, Shared, ,, )
                        {
                            0x00000010,
                            0x00000011,
                            0x00000012,
                            0x00000013,
                            0x00000014,
                            0x00000015,
                            0x00000016,
                            0x00000017,
                        }
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        And (PIRA, 0xF0, Local0)
                        If (LEqual (Local0, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        And (PIRA, 0x0F, PIRA)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFA, ResourceTemplate ()
                        {
                            Interrupt (ResourceConsumer, Level, ActiveLow, Shared, ,, _Y01)
                            {
                                0x00000000,
                            }
                        })
                        CreateWordField (BUFA, \_SB.PCI0.PIB.ALKA._CRS._Y01._INT, IRAI)
                        Store (\_SB.PCI0.PIB.PIRA, IRAI)
                        Return (BUFA)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                    }
                }

                Device (ALKB)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x06)
                    Name (_PRS, ResourceTemplate ()
                    {
                        Interrupt (ResourceConsumer, Level, ActiveLow, Shared, ,, )
                        {
                            0x00000010,
                            0x00000011,
                            0x00000012,
                            0x00000013,
                            0x00000014,
                            0x00000015,
                            0x00000016,
                            0x00000017,
                        }
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        And (PIRB, 0xF0, Local0)
                        If (LEqual (Local0, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        And (PIRB, 0x0F, PIRB)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFB, ResourceTemplate ()
                        {
                            Interrupt (ResourceConsumer, Level, ActiveLow, Shared, ,, _Y02)
                            {
                                0x00000000,
                            }
                        })
                        CreateWordField (BUFB, \_SB.PCI0.PIB.ALKB._CRS._Y02._INT, IRBI)
                        Store (\_SB.PCI0.PIB.PIRB, IRBI)
                        Return (BUFB)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                    }
                }

                Device (ALKC)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x07)
                    Name (_PRS, ResourceTemplate ()
                    {
                        Interrupt (ResourceConsumer, Level, ActiveLow, Shared, ,, )
                        {
                            0x00000016,
                        }
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        And (PIRC, 0xF0, Local0)
                        If (LEqual (Local0, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        And (PIRC, 0x0F, PIRC)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFC, ResourceTemplate ()
                        {
                            Interrupt (ResourceConsumer, Level, ActiveLow, Shared, ,, _Y03)
                            {
                                0x00000000,
                            }
                        })
                        CreateWordField (BUFC, \_SB.PCI0.PIB.ALKC._CRS._Y03._INT, IRCI)
                        Store (\_SB.PCI0.PIB.PIRC, IRCI)
                        Return (BUFC)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                    }
                }

                Device (ALKD)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x08)
                    Name (_PRS, ResourceTemplate ()
                    {
                        Interrupt (ResourceConsumer, Level, ActiveLow, Shared, ,, )
                        {
                            0x00000015,
                        }
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        And (PIRD, 0xF0, Local0)
                        If (LEqual (Local0, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        And (PIRD, 0x0F, PIRD)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFD, ResourceTemplate ()
                        {
                            Interrupt (ResourceConsumer, Level, ActiveLow, Shared, ,, _Y04)
                            {
                                0x00000000,
                            }
                        })
                        CreateWordField (BUFD, \_SB.PCI0.PIB.ALKD._CRS._Y04._INT, IRDI)
                        Store (\_SB.PCI0.PIB.PIRD, IRDI)
                        Return (BUFD)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                    }
                }

                Device (LNKA)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x01)
                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {3,9,10,11,12}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (Zero, \_SB.PCI0.PIB.PIRA)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.PIB.PIRA, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFA, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y05)
                                {}
                        })
                        CreateByteField (BUFA, \_SB.PCI0.PIB.LNKA._CRS._Y05._INT, IRA1)
                        CreateByteField (BUFA, 0x02, IRA2)
                        Store (\_SB.PCI0.PIB.PIRA, Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            If (LGreater (Local0, 0x07))
                            {
                                Subtract (Local0, 0x08, Local0)
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRA2)
                            }
                            Else
                            {
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRA1)
                            }
                        }

                        Return (BUFA)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x01, IRA1)
                        CreateByteField (Arg0, 0x02, IRA2)
                        If (LGreater (IRA2, Zero))
                        {
                            FindSetLeftBit (IRA2, Local0)
                            Decrement (Local0)
                            Add (Local0, 0x08, Local0)
                        }
                        Else
                        {
                            FindSetLeftBit (IRA1, Local0)
                            Decrement (Local0)
                        }

                        Store (Local0, \_SB.PCI0.PIB.PIRA)
                    }
                }

                Device (LNKB)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x02)
                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {3,9,10,11,12}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (Zero, \_SB.PCI0.PIB.PIRB)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.PIB.PIRB, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFB, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y06)
                                {}
                        })
                        CreateByteField (BUFB, \_SB.PCI0.PIB.LNKB._CRS._Y06._INT, IRB1)
                        CreateByteField (BUFB, 0x02, IRB2)
                        Store (\_SB.PCI0.PIB.PIRB, Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            If (LGreater (Local0, 0x07))
                            {
                                Subtract (Local0, 0x08, Local0)
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRB2)
                            }
                            Else
                            {
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRB1)
                            }
                        }

                        Return (BUFB)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x01, IRB1)
                        CreateByteField (Arg0, 0x02, IRB2)
                        If (LGreater (IRB2, Zero))
                        {
                            FindSetLeftBit (IRB2, Local0)
                            Decrement (Local0)
                            Add (Local0, 0x08, Local0)
                        }
                        Else
                        {
                            FindSetLeftBit (IRB1, Local0)
                            Decrement (Local0)
                        }

                        Store (Local0, \_SB.PCI0.PIB.PIRB)
                    }
                }

                Device (LNKC)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x03)
                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {3,9,10,11,12}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (Zero, \_SB.PCI0.PIB.PIRC)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.PIB.PIRC, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFC, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y07)
                                {}
                        })
                        CreateByteField (BUFC, \_SB.PCI0.PIB.LNKC._CRS._Y07._INT, IRC1)
                        CreateByteField (BUFC, 0x02, IRC2)
                        Store (\_SB.PCI0.PIB.PIRC, Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            If (LGreater (Local0, 0x07))
                            {
                                Subtract (Local0, 0x08, Local0)
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRC2)
                            }
                            Else
                            {
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRC1)
                            }
                        }

                        Return (BUFC)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x01, IRC1)
                        CreateByteField (Arg0, 0x02, IRC2)
                        If (LGreater (IRC2, Zero))
                        {
                            FindSetLeftBit (IRC2, Local0)
                            Decrement (Local0)
                            Add (Local0, 0x08, Local0)
                        }
                        Else
                        {
                            FindSetLeftBit (IRC1, Local0)
                            Decrement (Local0)
                        }

                        Store (Local0, \_SB.PCI0.PIB.PIRC)
                    }
                }

                Device (LNKD)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x04)
                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {3,9,10,11,12}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (Zero, \_SB.PCI0.PIB.PIRD)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.PIB.PIRD, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFD, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y08)
                                {}
                        })
                        CreateByteField (BUFD, \_SB.PCI0.PIB.LNKD._CRS._Y08._INT, IRD1)
                        CreateByteField (BUFD, 0x02, IRD2)
                        Store (\_SB.PCI0.PIB.PIRD, Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            If (LGreater (Local0, 0x07))
                            {
                                Subtract (Local0, 0x08, Local2)
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local2, Local3)
                                Store (Local3, IRD2)
                            }
                            Else
                            {
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, Local2)
                                Store (Local2, IRD1)
                            }
                        }

                        Return (BUFD)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x01, IRD1)
                        CreateByteField (Arg0, 0x02, IRD2)
                        If (LGreater (IRD2, Zero))
                        {
                            FindSetLeftBit (IRD2, Local0)
                            Decrement (Local0)
                            Add (Local0, 0x08, Local0)
                        }
                        Else
                        {
                            FindSetLeftBit (IRD1, Local0)
                            Decrement (Local0)
                        }

                        Store (Local0, \_SB.PCI0.PIB.PIRD)
                    }
                }

                Device (LNKE)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x01)
                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {3,9,10,11,12}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (Zero, \_SB.PCI0.PIB.PIRE)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.PIB.PIRE, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFE, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y09)
                                {}
                        })
                        CreateByteField (BUFE, \_SB.PCI0.PIB.LNKE._CRS._Y09._INT, IRE1)
                        CreateByteField (BUFE, 0x02, IRE2)
                        Store (\_SB.PCI0.PIB.PIRE, Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            If (LGreater (Local0, 0x07))
                            {
                                Subtract (Local0, 0x08, Local0)
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRE2)
                            }
                            Else
                            {
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRE1)
                            }
                        }

                        Return (BUFE)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x01, IRE1)
                        CreateByteField (Arg0, 0x02, IRE2)
                        If (LGreater (IRE2, Zero))
                        {
                            FindSetLeftBit (IRE2, Local0)
                            Decrement (Local0)
                            Add (Local0, 0x08, Local0)
                        }
                        Else
                        {
                            FindSetLeftBit (IRE1, Local0)
                            Decrement (Local0)
                        }

                        Store (Local0, \_SB.PCI0.PIB.PIRE)
                    }
                }

                Device (LNKF)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x02)
                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {3,9,10,11,12}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (Zero, \_SB.PCI0.PIB.PIRF)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.PIB.PIRF, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFF, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y0A)
                                {}
                        })
                        CreateByteField (BUFF, \_SB.PCI0.PIB.LNKF._CRS._Y0A._INT, IRF1)
                        CreateByteField (BUFF, 0x02, IRF2)
                        Store (\_SB.PCI0.PIB.PIRF, Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            If (LGreater (Local0, 0x07))
                            {
                                Subtract (Local0, 0x08, Local0)
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRF2)
                            }
                            Else
                            {
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRF1)
                            }
                        }

                        Return (BUFF)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x01, IRF1)
                        CreateByteField (Arg0, 0x02, IRF2)
                        If (LGreater (IRF2, Zero))
                        {
                            FindSetLeftBit (IRF2, Local0)
                            Decrement (Local0)
                            Add (Local0, 0x08, Local0)
                        }
                        Else
                        {
                            FindSetLeftBit (IRF1, Local0)
                            Decrement (Local0)
                        }

                        Store (Local0, \_SB.PCI0.PIB.PIRF)
                    }
                }

                Device (LNKG)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x03)
                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {3,9,10,11,12}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (Zero, \_SB.PCI0.PIB.PIRG)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.PIB.PIRG, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFG, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y0B)
                                {}
                        })
                        CreateByteField (BUFG, \_SB.PCI0.PIB.LNKG._CRS._Y0B._INT, IRG1)
                        CreateByteField (BUFG, 0x02, IRG2)
                        Store (\_SB.PCI0.PIB.PIRG, Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            If (LGreater (Local0, 0x07))
                            {
                                Subtract (Local0, 0x08, Local0)
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRG2)
                            }
                            Else
                            {
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, IRG1)
                            }
                        }

                        Return (BUFG)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x01, IRG1)
                        CreateByteField (Arg0, 0x02, IRG2)
                        If (LGreater (IRG2, Zero))
                        {
                            FindSetLeftBit (IRG2, Local0)
                            Decrement (Local0)
                            Add (Local0, 0x08, Local0)
                        }
                        Else
                        {
                            FindSetLeftBit (IRG1, Local0)
                            Decrement (Local0)
                        }

                        Store (Local0, \_SB.PCI0.PIB.PIRG)
                    }
                }

                Device (LNKH)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x04)
                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {3,9,10,11,12}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (Zero, \_SB.PCI0.PIB.PIRH)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.PIB.PIRH, 0x00))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BUFH, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y0C)
                                {}
                        })
                        CreateByteField (BUFH, \_SB.PCI0.PIB.LNKH._CRS._Y0C._INT, IRH1)
                        CreateByteField (BUFH, 0x02, IRH2)
                        Store (\_SB.PCI0.PIB.PIRH, Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            If (LGreater (Local0, 0x07))
                            {
                                Subtract (Local0, 0x08, Local2)
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local2, Local3)
                                Store (Local3, IRH2)
                            }
                            Else
                            {
                                Store (0x01, Local1)
                                ShiftLeft (Local1, Local0, Local2)
                                Store (Local2, IRH1)
                            }
                        }

                        Return (BUFH)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x01, IRH1)
                        CreateByteField (Arg0, 0x02, IRH2)
                        If (LGreater (IRH2, Zero))
                        {
                            FindSetLeftBit (IRH2, Local0)
                            Decrement (Local0)
                            Add (Local0, 0x08, Local0)
                        }
                        Else
                        {
                            FindSetLeftBit (IRH1, Local0)
                            Decrement (Local0)
                        }

                        Store (Local0, \_SB.PCI0.PIB.PIRH)
                    }
                }

                Device (DMA1)
                {
                    Name (_HID, EisaId ("PNP0200"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        DMA (Compatibility, BusMaster, Transfer8, )
                            {4}
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x0081,             // Range Minimum
                            0x0081,             // Range Maximum
                            0x01,               // Alignment
                            0x0F,               // Length
                            )
                        IO (Decode16,
                            0x00C0,             // Range Minimum
                            0x00C0,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }
                }

                Device (RTC)
                {
                    Name (_HID, EisaId ("PNP0B00"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x06,               // Length
                            )
                        IRQNoFlags ()
                            {8}
                    })
                }

                Device (PIC)
                {
                    Name (_HID, EisaId ("PNP0000"))
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0020,             // Range Minimum
                            0x0020,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A0,             // Range Minimum
                            0x00A0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IRQNoFlags ()
                            {2}
                    })
                }

                Device (COPR)
                {
                    Name (_HID, EisaId ("PNP0C04"))
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x00F0,             // Range Minimum
                            0x00F0,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IRQNoFlags ()
                            {13}
                    })
                }

                Device (TMR)
                {
                    Name (_HID, EisaId ("PNP0100"))
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0040,             // Range Minimum
                            0x0040,             // Range Maximum
                            0x01,               // Alignment
                            0x04,               // Length
                            )
                        IO (Decode16,
                            0x0050,             // Range Minimum
                            0x0050,             // Range Maximum
                            0x10,               // Alignment
                            0x04,               // Length
                            )
                        IRQNoFlags ()
                            {0}
                    })
                }

                Device (SPKR)
                {
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Name (_HID, EisaId ("PNP0800"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0061,             // Range Minimum
                            0x0061,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                    })
                }

                Device (MEM)
                {
                    Name (_HID, EisaId ("PNP0C01"))
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadWrite,
                            0x00000000,         // Address Base
                            0x000A0000,         // Address Length
                            )
                        Memory32Fixed (ReadOnly,
                            0x000E0000,         // Address Base
                            0x00020000,         // Address Length
                            )
                        Memory32Fixed (ReadOnly,
                            0xFEE00000,         // Address Base
                            0x00001000,         // Address Length
                            )
                        Memory32Fixed (ReadOnly,
                            0xFFF80000,         // Address Base
                            0x00080000,         // Address Length
                            )
                        Memory32Fixed (ReadOnly,
                            0xFFB80000,         // Address Base
                            0x00080000,         // Address Length
                            )
                    })
                }

                Device (SYSR)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        If (\_SB.PCI0.PIB.SMBC)
                        {
                            Name (RSR2, ResourceTemplate ()
                            {
                                IO (Decode16,
                                    0x0061,             // Range Minimum
                                    0x0061,             // Range Maximum
                                    0x01,               // Alignment
                                    0x03,               // Length
                                    )
                                IO (Decode16,
                                    0x0065,             // Range Minimum
                                    0x0065,             // Range Maximum
                                    0x01,               // Alignment
                                    0x0B,               // Length
                                    )
                                IO (Decode16,
                                    0x0080,             // Range Minimum
                                    0x0080,             // Range Maximum
                                    0x01,               // Alignment
                                    0x01,               // Length
                                    )
                                IO (Decode16,
                                    0x0092,             // Range Minimum
                                    0x0092,             // Range Maximum
                                    0x01,               // Alignment
                                    0x01,               // Length
                                    )
                                IO (Decode16,
                                    0x00A8,             // Range Minimum
                                    0x00A8,             // Range Maximum
                                    0x01,               // Alignment
                                    0x02,               // Length
                                    )
                                IO (Decode16,
                                    0x04D0,             // Range Minimum
                                    0x04D0,             // Range Maximum
                                    0x01,               // Alignment
                                    0x02,               // Length
                                    )
                                IO (Decode16,
                                    0xFE10,             // Range Minimum
                                    0xFE10,             // Range Maximum
                                    0x01,               // Alignment
                                    0x02,               // Length
                                    )
                                IO (Decode16,
                                    0xFE00,             // Range Minimum
                                    0xFE00,             // Range Maximum
                                    0x01,               // Alignment
                                    0x01,               // Length
                                    )
                                IO (Decode16,
                                    0x4000,             // Range Minimum
                                    0x4000,             // Range Maximum
                                    0x01,               // Alignment
                                    0x80,               // Length
                                    _Y0D)
                                IO (Decode16,
                                    0x4100,             // Range Minimum
                                    0x4100,             // Range Maximum
                                    0x01,               // Alignment
                                    0x20,               // Length
                                    _Y0E)
                            })
                            CreateWordField (RSR2, \_SB.PCI0.PIB.SYSR._CRS._Y0D._MIN, PMMI)
                            CreateWordField (RSR2, \_SB.PCI0.PIB.SYSR._CRS._Y0D._MAX, PMMA)
                            CreateWordField (RSR2, \_SB.PCI0.PIB.SYSR._CRS._Y0E._MIN, SMMI)
                            CreateWordField (RSR2, \_SB.PCI0.PIB.SYSR._CRS._Y0E._MAX, SMMA)
                            And (\_SB.PCI0.PIB.PMBS, 0xFFFE, PMMI)
                            Store (PMMI, PMMA)
                            And (\_SB.PCI0.PIB.SMBS, 0xFFF0, SMMI)
                            Store (SMMI, SMMA)
                            Return (RSR2)
                        }
                        Else
                        {
                            Name (RSR1, ResourceTemplate ()
                            {
                                IO (Decode16,
                                    0x0061,             // Range Minimum
                                    0x0061,             // Range Maximum
                                    0x01,               // Alignment
                                    0x03,               // Length
                                    )
                                IO (Decode16,
                                    0x0065,             // Range Minimum
                                    0x0065,             // Range Maximum
                                    0x01,               // Alignment
                                    0x0B,               // Length
                                    )
                                IO (Decode16,
                                    0x0080,             // Range Minimum
                                    0x0080,             // Range Maximum
                                    0x01,               // Alignment
                                    0x01,               // Length
                                    )
                                IO (Decode16,
                                    0x0092,             // Range Minimum
                                    0x0092,             // Range Maximum
                                    0x01,               // Alignment
                                    0x01,               // Length
                                    )
                                IO (Decode16,
                                    0x00A8,             // Range Minimum
                                    0x00A8,             // Range Maximum
                                    0x01,               // Alignment
                                    0x02,               // Length
                                    )
                                IO (Decode16,
                                    0x04D0,             // Range Minimum
                                    0x04D0,             // Range Maximum
                                    0x01,               // Alignment
                                    0x02,               // Length
                                    )
                                IO (Decode16,
                                    0xFE10,             // Range Minimum
                                    0xFE10,             // Range Maximum
                                    0x01,               // Alignment
                                    0x02,               // Length
                                    )
                                IO (Decode16,
                                    0xFE00,             // Range Minimum
                                    0xFE00,             // Range Maximum
                                    0x01,               // Alignment
                                    0x01,               // Length
                                    )
                                IO (Decode16,
                                    0x4000,             // Range Minimum
                                    0x4000,             // Range Maximum
                                    0x01,               // Alignment
                                    0x80,               // Length
                                    _Y0F)
                            })
                            CreateWordField (RSR1, \_SB.PCI0.PIB.SYSR._CRS._Y0F._MIN, IOMI)
                            CreateWordField (RSR1, \_SB.PCI0.PIB.SYSR._CRS._Y0F._MAX, IOMA)
                            And (\_SB.PCI0.PIB.PMBS, 0xFFFE, IOMI)
                            Store (IOMI, IOMA)
                            Return (RSR1)
                        }
                    }
                }

                Device (PS2M)
                {
                    Name (_HID, EisaId ("PNP0F13"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IRQNoFlags ()
                            {12}
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }
                }

                Device (PS2K)
                {
                    Name (_HID, EisaId ("PNP0303"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0060,             // Range Minimum
                            0x0060,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0064,             // Range Minimum
                            0x0064,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQNoFlags ()
                            {1}
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }
                }

                OperationRegion (PMIF, SystemIO, 0x68, 0x08)
                Field (PMIF, ByteAcc, NoLock, Preserve)
                {
                    PMUD,   8, 
                            Offset (0x04), 
                    PMUC,   8, 
                            Offset (0x08)
                }

                Mutex (ELCK, 0x00)
                Method (WIBF, 0, NotSerialized)
                {
                    Store (0x0009FFFF, Local6)
                    Noop
                    Noop
                    Store (PMUC, Local2)
                    And (Local2, 0x22, Local2)
                    If (And (Local2, 0x20, Local3))
                    {
                        Return (0x01)
                    }

                    And (Local2, 0x02, Local2)
                    While (LAnd (LNotEqual (Local2, 0x00), LNotEqual (Local6, 0x00)))
                    {
                        Noop
                        Noop
                        Store (PMUC, Local2)
                        Decrement (Local6)
                        If (And (Local2, 0x20, Local3))
                        {
                            Return (0x01)
                        }

                        And (Local2, 0x02, Local2)
                    }

                    Return (0x00)
                }

                Method (WOBF, 0, NotSerialized)
                {
                    Store (0x009FFFFF, Local6)
                    Noop
                    Noop
                    Store (PMUC, Local3)
                    And (Local3, 0x21, Local3)
                    If (And (Local3, 0x20, Local2))
                    {
                        Return (0x01)
                    }

                    While (LAnd (LEqual (Local3, 0x00), LNotEqual (Local6, 0x00)))
                    {
                        Noop
                        Noop
                        Store (PMUC, Local3)
                        And (Local3, 0x21, Local3)
                        If (And (Local3, 0x20, Local2))
                        {
                            Return (0x01)
                        }

                        Decrement (Local6)
                    }

                    Return (0x00)
                }

                Method (RCMD, 2, NotSerialized)
                {
                    Store (Arg0, Local0)
                    Store (Arg1, Local1)
                    Store (Local0, PMUC)
                    Noop
                    Noop
                    Noop
                    Noop
                    Noop
                    Noop
                    Noop
                    Noop
                    Noop
                    Noop
                    If (WIBF ())
                    {
                        Return (0x01)
                    }

                    Store (Local1, PMUD)
                    If (WOBF ())
                    {
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (WCMD, 2, NotSerialized)
                {
                    Store (Arg0, Local0)
                    Store (Arg1, Local1)
                    Store (Local0, PMUC)
                    If (WIBF ())
                    {
                        Return (0x01)
                    }

                    Store (Local1, PMUD)
                    If (WIBF ())
                    {
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (PMRD, 1, NotSerialized)
                {
                    Acquire (ELCK, 0xFFFF)
                    Store (Zero, EDFG)
                    Store (0x14, RECT)
                    While (LAnd (LEqual (EDFG, 0x00), LNotEqual (RECT, 0x00)))
                    {
                        Store (Arg0, Local0)
                        Store (0x03E8, Local6)
                        Store (PMUC, Local1)
                        And (Local1, 0x13, Local1)
                        While (LAnd (LNotEqual (Local1, 0x00), LNotEqual (Local6, 0x00)))
                        {
                            Sleep (0x02)
                            Store (PMUC, Local1)
                            And (Local1, 0x13, Local1)
                            If (And (Local1, 0x01, Local2))
                            {
                                Store (PMUD, Local3)
                            }

                            Decrement (Local6)
                        }

                        While (RCMD (0x80, Local0))
                        {
                            Noop
                            Noop
                            Store (PMUC, Local5)
                            If (And (Local5, 0x01, Local2))
                            {
                                Store (PMUD, Local5)
                            }
                        }

                        Store (0x07D0, Local6)
                        Store (PMUC, Local1)
                        And (Local1, 0x10, Local1)
                        While (LAnd (LNotEqual (Local1, 0x00), LNotEqual (Local6, 0x00)))
                        {
                            Noop
                            Noop
                            Store (PMUC, Local1)
                            And (Local1, 0x10, Local1)
                            Decrement (Local6)
                        }

                        Store (PMUC, Local1)
                        And (Local1, 0x20, Local1)
                        If (LEqual (Local1, 0x00))
                        {
                            Store (One, EDFG)
                        }

                        Decrement (RECT)
                    }

                    Store (PMUD, Local4)
                    Release (ELCK)
                    Return (Local4)
                }

                Method (PMWT, 2, NotSerialized)
                {
                    Acquire (ELCK, 0xFFFF)
                    Store (Zero, EDFG)
                    Store (0x14, RECT)
                    While (LAnd (LEqual (EDFG, 0x00), LNotEqual (RECT, 0x00)))
                    {
                        Store (Arg0, Local0)
                        Store (0x03E8, Local6)
                        Store (PMUC, Local1)
                        And (Local1, 0x13, Local1)
                        While (LAnd (LNotEqual (Local1, 0x00), LNotEqual (Local6, 0x00)))
                        {
                            Sleep (0x01)
                            Store (PMUC, Local1)
                            And (Local1, 0x13, Local1)
                            Decrement (Local6)
                        }

                        While (WCMD (0x81, Local0))
                        {
                            Noop
                            Noop
                            Store (PMUC, Local5)
                            If (And (Local5, 0x01, Local2))
                            {
                                Store (PMUD, Local5)
                            }
                        }

                        Store (Arg1, PMUD)
                        Store (0x07D0, Local6)
                        Store (PMUC, Local1)
                        And (Local1, 0x12, Local1)
                        While (LAnd (LNotEqual (Local1, 0x00), LNotEqual (Local6, 0x00)))
                        {
                            Store (0x00, ED)
                            Noop
                            Noop
                            Store (0x00, ED)
                            Store (PMUC, Local1)
                            And (Local1, 0x12, Local1)
                            Decrement (Local6)
                        }

                        Store (PMUC, Local1)
                        And (Local1, 0x20, Local1)
                        If (LEqual (Local1, 0x00))
                        {
                            Store (One, EDFG)
                        }

                        Decrement (RECT)
                    }

                    Release (ELCK)
                }

                Method (PMMW, 2, NotSerialized)
                {
                    Store (Arg0, Local0)
                    Store (Arg1, Local1)
                    And (Local0, 0xFF, Local2)
                    And (Local0, 0xFF00, Local3)
                    ShiftRight (Local3, 0x08, Local3)
                    Add (Local2, Local3, Local4)
                    Add (Local4, 0xC1, Local4)
                    Add (Local4, Local1, Local7)
                    And (Local7, 0xFF, Local7)
                    PMWR (0x043F, Local7)
                    PMWR (Local0, Local1)
                }

                Method (PMWR, 2, NotSerialized)
                {
                    Acquire (ELCK, 0xFFFF)
                    Store (Zero, EDFG)
                    Store (0x14, RECT)
                    While (LAnd (LEqual (EDFG, 0x00), LNotEqual (RECT, 0x00)))
                    {
                        Store (0x03E8, Local6)
                        Store (PMUC, Local1)
                        And (Local1, 0x13, Local1)
                        While (LAnd (LNotEqual (Local1, 0x00), LNotEqual (Local6, 0x00)))
                        {
                            Sleep (0x01)
                            Store (PMUC, Local1)
                            And (Local1, 0x13, Local1)
                            Decrement (Local6)
                        }

                        Store (Arg0, Local0)
                        While (WCM2 (0xC1, Local0))
                        {
                            Store (0x00, ED)
                            Noop
                            Noop
                            Store (0x00, ED)
                            Store (PMUC, Local5)
                            If (And (Local5, 0x01, Local2))
                            {
                                Store (PMUD, Local5)
                            }
                        }

                        Store (Arg1, PMUD)
                        Store (0x07D0, Local6)
                        Store (PMUC, Local1)
                        And (Local1, 0x12, Local1)
                        While (LAnd (LNotEqual (Local1, 0x00), LNotEqual (Local6, 0x00)))
                        {
                            Store (0x00, ED)
                            Noop
                            Noop
                            Store (0x00, ED)
                            Store (PMUC, Local1)
                            And (Local1, 0x12, Local1)
                            Decrement (Local6)
                        }

                        Store (PMUC, Local1)
                        And (Local1, 0x20, Local1)
                        If (LEqual (Local1, 0x00))
                        {
                            Store (One, EDFG)
                        }

                        Decrement (RECT)
                    }

                    Release (ELCK)
                }

                Method (WCM2, 2, NotSerialized)
                {
                    Store (Arg0, Local0)
                    Store (Arg1, Local1)
                    Store (Arg1, Local2)
                    And (Local1, 0xFF, Local1)
                    And (Local2, 0xFF00, Local2)
                    ShiftRight (Local2, 0x08, Local2)
                    Store (Local0, PMUC)
                    If (WIBF ())
                    {
                        Return (0x01)
                    }

                    Store (Local2, PMUD)
                    If (WIBF ())
                    {
                        Return (0x01)
                    }

                    Store (Local1, PMUD)
                    If (WIBF ())
                    {
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Name (EDFG, 0x00)
                Name (RECT, 0x00)
                OperationRegion (DELY, SystemIO, 0xED, 0x01)
                Field (DELY, ByteAcc, NoLock, Preserve)
                {
                    ED,     8
                }

                Method (SMST, 0, NotSerialized)
                {
                    Store (0x10, Local6)
                    Store (PMRD (0x70), Local0)
                    While (LAnd (LNotEqual (Local0, 0x00), LNotEqual (Local6, 0x00)))
                    {
                        Sleep (0x05)
                        Store (PMRD (0x70), Local0)
                        Decrement (Local6)
                    }

                    Store (0x10, Local6)
                    Store (PMRD (0x71), Local1)
                    While (LAnd (LNotEqual (Local1, 0x80), LNotEqual (Local6, 0x00)))
                    {
                        Sleep (0x05)
                        Store (PMRD (0x71), Local1)
                        Decrement (Local6)
                    }
                }

                Method (SMWT, 3, NotSerialized)
                {
                    Acquire (ELCK, 0xFFFF)
                    Store (0x06, Local6)
                    Store (Arg0, Local0)
                    Store (Arg1, Local1)
                    Store (Arg2, Local2)
                    While (LNotEqual (Local6, 0x00))
                    {
                        PMWT (0x71, 0x00)
                        PMWT (0x72, Local0)
                        PMWT (0x73, Local1)
                        PMWT (0x74, Local2)
                        PMWT (0x70, 0x06)
                        SMST ()
                        Decrement (Local6)
                    }

                    Release (ELCK)
                }

                Method (SMWD, 4, NotSerialized)
                {
                    Acquire (ELCK, 0xFFFF)
                    Store (0x06, Local6)
                    Store (Arg0, Local0)
                    Store (Arg1, Local1)
                    Store (Arg2, Local2)
                    Store (Arg3, Local3)
                    While (LNotEqual (Local6, 0x00))
                    {
                        PMWT (0x71, 0x00)
                        PMWT (0x72, Local0)
                        PMWT (0x73, Local1)
                        PMWT (0x74, Local2)
                        PMWT (0x75, Local3)
                        PMWT (0x70, 0x08)
                        SMST ()
                        Decrement (Local6)
                    }

                    Release (ELCK)
                }
            }

            Scope (_TZ)
            {
                PowerResource (PFAN, 0x00, 0x0000)
                {
                    Method (_ON, 0, NotSerialized)
                    {
                        Or (\_SB.PCI0.PIB.PMRD (0xFE), 0x04, Local0)
                        \_SB.PCI0.PIB.PMWT (0xFF, Local0)
                        \_SB.PCI0.PIB.PMWT (0xE5, DerefOf (Index (\_TZ.THRM.LOLM, 0x01)))
                        \_SB.PCI0.PIB.PMWT (0xE4, DerefOf (Index (\_TZ.THRM.HILM, 0x01)))
                        SFAN (0x01)
                    }

                    Method (_OFF, 0, NotSerialized)
                    {
                        And (\_SB.PCI0.PIB.PMRD (0xFF), 0xFB, Local0)
                        \_SB.PCI0.PIB.PMWT (0xFF, Local0)
                        \_SB.PCI0.PIB.PMWT (0xE5, DerefOf (Index (\_TZ.THRM.LOLM, 0x00)))
                        \_SB.PCI0.PIB.PMWT (0xE4, DerefOf (Index (\_TZ.THRM.HILM, 0x00)))
                        SFAN (0x00)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        And (\_SB.PCI0.PIB.PMRD (0xFF), 0x04, Local7)
                        ShiftRight (Local7, 0x01, Local7)
                        Return (Local7)
                    }
                }

		Device (FAN)
		{
		Name (_HID, EisaId ("PNP0C0B"))
		Name (_PSC, Zero)
		Method (_PS0, 0, NotSerialized)
		{
		^^THRM.SFAN (Zero)
		}
		Method (_PS1, 0, NotSerialized)
		{
		^^THRM.SFAN (One)
		}
		Method (_PS2, 0, NotSerialized)
		{
		^^THRM.SFAN (0x02)
		}
		Method (_PS3, 0, NotSerialized)
		{
		^^THRM.SFAN (0x03)
		}
		}

                ThermalZone (THRM)
                {
                    Name (CRTV, 0x6E)
                    Name (COLM, 0x00)
                    Name (HILM, Package (0x04)
                    {
                        0x37, 
                        0x41, 
                        0x5A, 
                        0x6E
                    })
                    Name (LOLM, Package (0x04)
                    {
                        0x00, 
                        0x30, 
                        0x3C, 
                        0x50
                    })
                    Name (FANS, Package (0x04)
                    {
                        0x00, 
                        0x01, 
                        0x02, 
                        0x02
                    })
                    Name (TERR, 0x00)
                    Method (_AC0, 0, Serialized)
                    {
                        Add (0x3C, 0x0111, Local0)
                        Multiply (Local0, 0x0A, Local0)
                        Return (Local0)
                    }

                    Name (_AL0, Package (0x01)
                    {
                        FAN
                    })
                    Method (_PSV, 0, NotSerialized)
                    {
                        Add (0x4E, 0x0111, Local0)
                        Multiply (Local0, 0x0A, Local0)
                        Return (Local0)
                    }

                    Name (_PSL, Package (0x01)
                    {
                        \_PR.CPU0
                    })
                    Method (_CRT, 0, NotSerialized)
                    {
                        Add (CRTV, 0x0111, Local0)
                        Multiply (Local0, 0x0A, Local0)
                        Return (Local0)
                    }

                    Method (_SCP, 1, NotSerialized)
                    {
                        Store (0x6E, CRTV)
                        \_SB.PCI0.PIB.PMWT (0xE8, 0x6E)
                        \_SB.PCI0.PIB.PMWT (0xE6, 0x0C)
                        Store (Arg0, COLM)
                    }

                    Method (_TMP, 0, NotSerialized)
                    {
                        If (\_TZ.THRM.TERR)
                        {
                            Return (0x0F8C)
                        }
                        Else
                        {
                            Store (\_SB.PCI0.PIB.PMRD (0xE7), Local0)
                            If (LGreaterEqual (Local0, 0x80))
                            {
                                Store (0x0A, Local0)
                            }

                            Multiply (Local0, 0x0A, Local0)
                            Add (Local0, 0x0AAA, Local0)
                            If (LEqual (Local0, 0x0AAA))
                            {
                                Return (0x0B72)
                            }
                            Else
                            {
                                Return (Local0)
                            }

                            Return (Local0)
                        }
                    }

                    Name (_TC1, 0x03)
                    Name (_TC2, 0x01)
                    Name (_TSP, 0x50)
                }
            }

            Name (REGT, Package (0x15)
            {
                0x10, 
                0x20, 
                0x21, 
                0x22, 
                0x23, 
                0x33, 
                0x34, 
                0x35, 
                0x36, 
                0x37, 
                0x47, 
                0x48, 
                0x49, 
                0x4A, 
                0x4B, 
                0x4C, 
                0x5C, 
                0x5D, 
                0x5E, 
                0x5F, 
                0x6F
            })
            Name (DMTT, Package (0x07)
            {
                0x0F, 
                0x14, 
                0x1E, 
                0x2D, 
                0x3C, 
                0x4B, 
                0x78
            })
            Name (PIOT, Package (0x07)
            {
                0x0258, 
                0x017F, 
                0xF0, 
                0xB4, 
                0x78, 
                0x5A, 
                0x00
            })
            Device (IDE)
            {
                Name (_ADR, 0x000F0001)
                OperationRegion (PCI, PCI_Config, 0x48, 0x60)
                Field (PCI, DWordAcc, NoLock, Preserve)
                {
                    SDR1,   8, 
                    SDR0,   8, 
                    PDR1,   8, 
                    PDR0,   8, 
                    SDST,   4, 
                    PDST,   4, 
                            Offset (0x08), 
                    UDMS,   16, 
                    UDMP,   16
                }

                Name (Z005, 0x00)
                Name (Z006, 0x00)
                Method (_PS3, 0, NotSerialized)
                {
                    And (^UDMP, 0x10, ^Z005)
                    And (^UDMS, 0x10, ^Z006)
                }

                Method (_PS0, 0, NotSerialized)
                {
                    If (^Z005)
                    {
                        Or (^UDMP, ^Z005, Local0)
                        Or (Local0, ShiftLeft (^Z005, 0x08), ^UDMP)
                    }

                    If (^Z006)
                    {
                        Or (^UDMS, ^Z006, Local0)
                        Or (Local0, ShiftLeft (^Z006, 0x08), ^UDMS)
                    }
                }

                Method (GIDX, 1, NotSerialized)
                {
                    If (LEqual (Arg0, 0x00))
                    {
                        Store (0x00, Local1)
                    }
                    Else
                    {
                        If (LEqual (Arg0, 0x0E))
                        {
                            Store (0x06, Local1)
                        }
                        Else
                        {
                            Add (ShiftRight (Arg0, 0x01), 0x01, Local1)
                        }
                    }

                    Return (Local1)
                }

                Method (RIDX, 1, NotSerialized)
                {
                    Store (0x00, Local0)
                    While (NAnd (LLess (Local0, 0x07), LEqual (DerefOf (Index (^^DMTT, Local0
                        )), Arg0)))
                    {
                        Increment (Local0)
                    }

                    If (Local0)
                    {
                        If (LGreater (Local0, 0x06))
                        {
                            Store (0x0E, Local0)
                        }
                        Else
                        {
                            Subtract (ShiftLeft (Local0, 0x01), 0x01, Local0)
                            If (LNotEqual (Local0, 0x01))
                            {
                                Decrement (Local0)
                            }
                        }
                    }

                    Return (Local0)
                }

                Method (GTM, 3, NotSerialized)
                {
                    Store (Buffer (0x14) {}, Local0)
                    CreateDWordField (Local0, 0x00, PIO0)
                    CreateDWordField (Local0, 0x04, DMA0)
                    CreateDWordField (Local0, 0x08, PIO1)
                    CreateDWordField (Local0, 0x0C, DMA1)
                    CreateDWordField (Local0, 0x10, FLAG)
                    Store (Zero, FLAG)
                    Or (FLAG, 0x10, FLAG)
                    Add (And (Arg1, 0x0F), ShiftRight (Arg1, 0x04), Local1)
                    Add (Local1, 0x02, Local1)
                    Multiply (Local1, 0x1E, PIO0)
                    Or (FLAG, 0x02, FLAG)
                    Add (And (Arg2, 0x0F), ShiftRight (Arg2, 0x04), Local1)
                    Add (Local1, 0x02, Local1)
                    Multiply (Local1, 0x1E, PIO1)
                    Or (FLAG, 0x08, FLAG)
                    And (Arg0, 0x0F, Local1)
                    If (And (Arg0, 0xE0))
                    {
                        Or (FLAG, 0x04, FLAG)
                        Store (^GIDX (Local1), Local1)
                    }
                    Else
                    {
                        Store (0x06, Local1)
                    }

                    Store (DerefOf (Index (^^DMTT, Local1)), DMA1)
                    ShiftRight (And (Arg0, 0x0F00), 0x08, Local1)
                    If (And (Arg0, 0xE000))
                    {
                        Or (FLAG, 0x01, FLAG)
                        Store (^GIDX (Local1), Local1)
                    }
                    Else
                    {
                        Store (0x06, Local1)
                    }

                    Store (DerefOf (Index (^^DMTT, Local1)), DMA0)
                    Return (Local0)
                }

                Method (STM, 3, NotSerialized)
                {
                    Store (Buffer (0x05) {}, Local7)
                    CreateWordField (Local7, 0x00, UDMT)
                    CreateWordField (Local7, 0x02, PIOT)
                    CreateByteField (Local7, 0x04, R4CT)
                    CreateDWordField (Arg0, 0x00, PIO0)
                    CreateDWordField (Arg0, 0x04, DMA0)
                    CreateDWordField (Arg0, 0x08, PIO1)
                    CreateDWordField (Arg0, 0x0C, DMA1)
                    CreateDWordField (Arg0, 0x10, FLAG)
                    Store (FLAG, Local4)
                    Store (0x0E0E, Local1)
                    If (And (Local4, 0x01))
                    {
                        And (Local1, 0x0F, Local1)
                        Store (^RIDX (DMA0), Local3)
                        Or (Local3, 0xE0, Local3)
                        Or (ShiftLeft (Local3, 0x08), Local1, Local1)
                    }

                    If (And (Local4, 0x04))
                    {
                        And (Local1, 0xFF00, Local1)
                        Store (^RIDX (DMA1), Local3)
                        Or (Local3, 0xE0, Local3)
                        Or (Local3, Local1, Local1)
                    }

                    Store (Local1, UDMT)
                    Store (0x0A, Local2)
                    If (And (Local4, 0x02))
                    {
                        Divide (PIO0, 0x1E, , Local3)
                        Subtract (Local3, 0x03, Local3)
                        If (LLess (Local3, 0x0C))
                        {
                            And (Local2, 0x03, Local2)
                            Or (Local2, 0x04, Local2)
                        }

                        Store (ShiftLeft (DerefOf (Index (^^REGT, Local3)), 0x08), Local6)
                    }
                    Else
                    {
                        Store (0x00, Local6)
                    }

                    If (And (Local4, 0x08))
                    {
                        Divide (PIO1, 0x1E, , Local3)
                        Subtract (Local3, 0x03, Local3)
                        If (LLess (Local3, 0x0C))
                        {
                            And (Local2, 0x0C, Local2)
                            Or (Local2, 0x01, Local2)
                        }

                        Store (DerefOf (Index (^^REGT, Local3)), Local6)
                    }
                    Else
                    {
                        Store (And (Local6, 0xFF00), Local6)
                    }

                    Store (Local2, R4CT)
                    Store (Local6, PIOT)
                    Return (Local7)
                }

                Method (GTF, 3, NotSerialized)
                {
                    If (Arg2)
                    {
                        Store (Buffer (0x07)
                            {
                                0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                            }, Local7)
                    }
                    Else
                    {
                        Store (Buffer (0x07)
                            {
                                0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                            }, Local7)
                    }

                    CreateByteField (Local7, 0x01, MODE)
                    Add (And (Arg0, 0x0F), ShiftRight (Arg0, 0x04), Local1)
                    Add (Local1, 0x02, Local1)
                    Multiply (Local1, 0x1E, Local0)
                    Store (Match (^^PIOT, MLT, Local0, MTR, 0x00, 0x00), Local1)
                    If (Local1)
                    {
                        Decrement (Local1)
                    }

                    If (And (Arg1, 0xE0))
                    {
                        Store (^GIDX (And (Arg1, 0x0F)), Local0)
                        If (LGreater (Local0, 0x06))
                        {
                            Store (0x00, Local0)
                        }
                        Else
                        {
                            Subtract (0x06, Local0, Local0)
                        }

                        Or (Local0, 0x40, MODE)
                    }
                    Else
                    {
                        Or (Local1, 0x08, MODE)
                    }

                    Concatenate (Local7, Local7, Local6)
                    Or (Local1, 0x08, MODE)
                    Concatenate (Local6, Local7, Local5)
                    Return (Local5)
                }

                Device (PRIM)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store ("GTM - Primary Controller", Debug)
                        Store (^^GTM (^^UDMP, ^^PDR0, ^^PDR1), Local0)
                        Return (Local0)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store ("STM - Primary Controller", Debug)
                        Store (^^STM (Arg0, Arg1, Arg2), Local0)
                        CreateWordField (Local0, 0x00, UDMA)
                        CreateWordField (Local0, 0x02, PIOM)
                        CreateByteField (Local0, 0x04, ADST)
                        Store (Or (UDMA, And (^^UDMP, 0x1010)), ^^UDMP)
                        Store (And (PIOM, 0xFF), Local1)
                        If (Local1)
                        {
                            Store (Local1, ^^PDR1)
                        }

                        ShiftRight (PIOM, 0x08, Local1)
                        If (Local1)
                        {
                            Store (Local1, ^^PDR0)
                        }

                        Store (ADST, ^^PDST)
                    }

                    Device (MAST)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store ("GTF - Primary Master", Debug)
                            ShiftRight (^^^UDMP, 0x08, Local0)
                            Store (^^^GTF (^^^PDR0, Local0, 0x01), Local0)
                            Return (Local0)
                        }
                    }
                }

                Device (SECN)
                {
                    Name (_ADR, 0x01)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Store ("GTM - Secondary Controller", Debug)
                        Store (^^GTM (^^UDMS, ^^SDR0, ^^SDR1), Local0)
                        Return (Local0)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store ("STM - Secondary Controller", Debug)
                        Store (^^STM (Arg0, Arg1, Arg2), Local0)
                        CreateWordField (Local0, 0x00, DMAS)
                        CreateWordField (Local0, 0x02, PIOS)
                        CreateByteField (Local0, 0x04, ADSS)
                        Store (Or (DMAS, And (^^UDMS, 0x1010)), ^^UDMS)
                        And (PIOS, 0xFF, Local1)
                        If (Local1)
                        {
                            Store (Local1, ^^SDR1)
                        }

                        ShiftRight (PIOS, 0x08, Local1)
                        If (Local1)
                        {
                            Store (Local1, ^^SDR0)
                        }

                        Store (ADSS, ^^SDST)
                    }

                    Device (MAST)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Store ("GTF - Secondary Master", Debug)
                            ShiftRight (^^^UDMS, 0x08, Local0)
                            Store (^^^GTF (^^^SDR0, Local0, 0x01), Local0)
                            Return (Local0)
                        }
                    }
                }
            }

            Device (AUDI)
            {
                Name (_ADR, 0x00110005)
                OperationRegion (SB75, PCI_Config, 0x00, 0x80)
                Field (SB75, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x2C), 
                    AD2C,   32, 
                            Offset (0x3C), 
                    ACIR,   4, 
                            Offset (0x42), 
                        ,   5, 
                    Z007,   1
                }

                Method (_STA, 0, NotSerialized)
                {
                    Return (0x0F)
                }

                Name (Z008, 0x00)
                Method (_PS0, 0, NotSerialized)
                {
                    If (LEqual (^AD2C, 0x00))
                    {
                        Store (0x01, ^Z007)
                        Store (Z008, ^AD2C)
                        Store (0x00, ^Z007)
                    }
                    Else
                    {
                        Store (^AD2C, Z008)
                    }
                }

                Method (_PS3, 0, NotSerialized)
                {
                    Store (^AD2C, Z008)
                }
            }

            Device (MODM)
            {
                Name (_ADR, 0x00110006)
                OperationRegion (SB76, PCI_Config, 0x00, 0x80)
                Field (SB76, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x2C), 
                    MD2C,   32, 
                            Offset (0x3C), 
                    MCIR,   4, 
                            Offset (0x44), 
                        ,   4, 
                    Z009,   1
                }

                Method (_STA, 0, NotSerialized)
                {
                    If (\_SB.PCI0.PIB.MC97)
                    {
                        Return (0x00)
                    }
                    Else
                    {
                        Return (0x0F)
                    }
                }

                Name (Z008, 0x00)
                Method (_PS0, 0, NotSerialized)
                {
                    If (LEqual (^MD2C, 0x00))
                    {
                        Store (0x01, ^Z009)
                        Store (Z008, ^MD2C)
                        Store (0x00, ^Z009)
                    }
                    Else
                    {
                        Store (^MD2C, Z008)
                    }
                }

                Method (_PS3, 0, NotSerialized)
                {
                    Store (^MD2C, Z008)
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x04
                })
            }

            Device (PPB)
            {
                Name (_ADR, 0x00010000)
                Device (VGA)
                {
                    Name (_ADR, 0x00)
                    Name (SWIT, 0x01)
                    Name (CRTA, 0x01)
                    Name (LCDA, 0x01)
                    Method (_INI, 0, NotSerialized)
                    {
                        Store (One, \_SB.PCI0.PPB.VGA.CRTA)
                        Store (One, \_SB.PCI0.PPB.VGA.LCDA)
                        Notify (\_SB.PCI0.PPB.VGA, 0x80)
                        Sleep (0xC8)
                    }

                    Method (_PS0, 0, NotSerialized)
                    {
                    }

                    Method (_PS3, 0, NotSerialized)
                    {
                    }

                    Method (_DOS, 1, NotSerialized)
                    {
                        Store (Arg0, SWIT)
                    }

                    Method (_DOD, 0, NotSerialized)
                    {
                        Return (Package (0x02)
                        {
                            0x00010100, 
                            0x00010110
                        })
                    }

                    Device (CRT)
                    {
                        Name (_ADR, 0x0100)
                        Method (_DCS, 0, NotSerialized)
                        {
                            If (CRTA)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x1D)
                            }
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (CRTA)
                            {
                                Return (0x01)
                            }
                            Else
                            {
                                Return (0x00)
                            }
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }

                    Device (LCD)
                    {
                        Name (_ADR, 0x0110)
                        Method (_DCS, 0, NotSerialized)
                        {
                            If (LCDA)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x1D)
                            }
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (LCDA)
                            {
                                Return (0x01)
                            }
                            Else
                            {
                                Return (0x00)
                            }
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }
                }
            }

            Device (Z00A)
            {
                Name (_ADR, 0x00120000)
                Name (_PRW, Package (0x02)
                {
                    0x03, 
                    0x03
                })
            }
        }

        Mutex (VSMX, 0x00)
        Method (Z000, 1, Serialized)
        {
            Acquire (VSMX, 0xFFFF)
            Store (Arg0, \_SB.PCI0.PIB.Z003)
            Release (VSMX)
        }

        Name (\ACON, 0x01)
        Mutex (PSMX, 0x00)
        Device (ACAD)
        {
            Name (_HID, "ACPI0003")
            Name (_PCL, Package (0x01)
            {
                \_SB
            })
            Name (INIT, 0x01)
            Name (ACFG, 0x00)
            Method (_PSR, 0, NotSerialized)
            {
                Acquire (PSMX, 0xFFFF)
                And (0x01, \_SB.PCI0.PIB.PMRD (0xA0), Local0)
                Store (Local0, ACFG)
                Store (Local0, INIT)
                Release (PSMX)
                Return (ACFG)
            }

            Method (_STA, 0, NotSerialized)
            {
                Return (0x0F)
            }
        }

        Device (BAT0)
        {
            Name (_HID, EisaId ("PNP0C0A"))
            Name (_UID, 0x01)
            Method (_STA, 0, NotSerialized)
            {
                Acquire (PSMX, 0xFFFF)
                And (\_SB.PCI0.PIB.PMRD (0xA1), 0x01, Local0)
                Store (Local0, FSTA)
                Release (PSMX)
                If (LEqual (Local0, 0x00))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x1F)
                }
            }

            Method (_BIF, 0, NotSerialized)
            {
                And (\_SB.PCI0.PIB.PMRD (0xA1), 0x01, Local0)
                If (Local0)
                {
                    UPBI ()
                }
                Else
                {
                    IVBI ()
                    IVBS ()
                }

                Store (Zero, FBIF)
                Return (PBIF)
            }

            Method (_BST, 0, NotSerialized)
            {
                UPBS ()
                Return (PBST)
            }

            Method (IVBI, 0, NotSerialized)
            {
                Store (0xFFFFFFFF, Index (PBIF, 0x01))
                Store (0xFFFFFFFF, Index (PBIF, 0x02))
                Store (0xFFFFFFFF, Index (PBIF, 0x04))
                Store ("Bad", Index (PBIF, 0x09))
                Store ("Bad", Index (PBIF, 0x0A))
                Store ("Bad", Index (PBIF, 0x0B))
                Store ("Bad", Index (PBIF, 0x0C))
                Store (One, FBIF)
            }

            Method (IVBS, 0, NotSerialized)
            {
                Store (Zero, Index (PBST, 0x00))
                Store (0xFFFFFFFF, Index (PBST, 0x01))
                Store (0xFFFFFFFF, Index (PBST, 0x02))
                Store (0xFFFFFFFF, Index (PBST, 0x03))
                Store (One, \_SB.BAT0.FSTA)
            }

            Method (UPBI, 0, NotSerialized)
            {
                Acquire (PSMX, 0xFFFF)
                Store (\_SB.PCI0.PIB.PMRD (0x00), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x01), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local0, Local2, Local3)
                Store (Local3, Index (PBIF, 0x00))
                Store (\_SB.PCI0.PIB.PMRD (0x02), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x03), Local1)
                Store (\_SB.PCI0.PIB.PMRD (0x49), Local2)
                Multiply (Local1, 0x0100, Local3)
                Multiply (Local2, 0x00010000, Local4)
                Or (Local3, Local0, Local5)
                Or (Local4, Local5, Local6)
                Store (Local6, Index (PBIF, 0x01))
                Store (\_SB.PCI0.PIB.PMRD (0x04), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x05), Local1)
                Store (\_SB.PCI0.PIB.PMRD (0x4A), Local2)
                Multiply (Local1, 0x0100, Local3)
                Multiply (Local2, 0x00010000, Local4)
                Or (Local3, Local0, Local5)
                Or (Local4, Local5, Local6)
                Store (Local6, Index (PBIF, 0x02))
                Store (\_SB.PCI0.PIB.PMRD (0x06), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x07), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local2, Local0, Local3)
                Store (Local3, Index (PBIF, 0x03))
                Store (\_SB.PCI0.PIB.PMRD (0x08), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x09), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local2, Local0, Local3)
                Store (Local3, Index (PBIF, 0x04))
                Divide (Local6, Local3, , Local7)
                Store (0x026A, Index (PBIF, 0x05))
                Store (0x0135, Index (PBIF, 0x05))
                Store (\_SB.PCI0.PIB.PMRD (0x0E), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x0F), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local2, Local0, Local3)
                Store (Local3, Index (PBIF, 0x07))
                Store (\_SB.PCI0.PIB.PMRD (0x10), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x11), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local2, Local0, Local3)
                Store (Local3, Index (PBIF, 0x08))
                If (LEqual (\_SB.PCI0.PIB.PMRD (0x18), 0x06))
                {
                    If (LGreater (\_SB.PCI0.PIB.PMRD (0x02), 0x70))
                    {
                        Store ("SOL-LMXXML6", Index (PBIF, 0x09))
                    }
                    Else
                    {
                        Store ("SOL-LMXXML3", Index (PBIF, 0x09))
                    }

                    Store ("SOLE ", Index (PBIF, 0x0C))
                }
                Else
                {
                    If (LGreater (\_SB.PCI0.PIB.PMRD (0x02), 0x70))
                    {
                        Store ("SMP-LMXXSS6", Index (PBIF, 0x09))
                    }
                    Else
                    {
                        Store ("SMP-LMXXSS3", Index (PBIF, 0x09))
                    }

                    Store ("SMP ", Index (PBIF, 0x0C))
                }

                Store ("Lion", Index (PBIF, 0x0B))
                Release (PSMX)
                Return (PBIF)
            }

            Method (UPBS, 0, NotSerialized)
            {
                Acquire (PSMX, 0xFFFF)
                Store (\_SB.PCI0.PIB.PMRD (0x1A), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x1B), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local2, Local0, Local3)
                Store (Local3, Index (PBST, 0x00))
                Store (\_SB.PCI0.PIB.PMRD (0x1C), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x1D), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local2, Local0, Local3)
                Store (Local3, Index (PBST, 0x01))
                Store (\_SB.PCI0.PIB.PMRD (0x1E), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x1F), Local1)
                Store (\_SB.PCI0.PIB.PMRD (0x4B), Local2)
                Multiply (Local1, 0x0100, Local3)
                Multiply (Local2, 0x00010000, Local4)
                Or (Local3, Local0, Local5)
                Or (Local4, Local5, Local6)
                Store (\_SB.PCI0.PIB.PMRD (0x10), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x11), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local2, Local0, Local3)
                Multiply (Local3, 0x02, Local3)
                Divide (Local6, Local3, Local0, Local6)
                Multiply (Local6, Local3, Local6)
                Store (Local6, Index (PBST, 0x02))
                Store (\_SB.PCI0.PIB.PMRD (0x20), Local0)
                Store (\_SB.PCI0.PIB.PMRD (0x21), Local1)
                Multiply (Local1, 0x0100, Local2)
                Or (Local2, Local0, Local3)
                Store (Local3, Index (PBST, 0x03))
                Release (PSMX)
                Return (PBST)
            }

            Method (_BTP, 1, NotSerialized)
            {
                Acquire (PSMX, 0xFFFF)
                Store (\_SB.PCI0.PIB.PMRD (0xB2), Local0)
                And (Local0, 0x7F, Local0)
                \_SB.PCI0.PIB.PMWT (0xB2, Local0)
                Store (Arg0, Local0)
                Store (Local0, Local6)
                And (Local0, 0xFF, Local1)
                \_SB.PCI0.PIB.PMWT (0x22, Local1)
                Store (Local6, Local0)
                And (Local0, 0xFF00, Local1)
                ShiftRight (Local1, 0x08, Local2)
                \_SB.PCI0.PIB.PMWT (0x23, Local2)
                Store (Local6, Local0)
                And (Local0, 0x00FF0000, Local1)
                ShiftRight (Local1, 0x10, Local2)
                \_SB.PCI0.PIB.PMWT (0x4C, Local2)
                Store (\_SB.PCI0.PIB.PMRD (0xF1), Local3)
                If (And (Local3, 0x80, Local3))
                {
                    Store (\_SB.PCI0.PIB.PMRD (0xA1), Local4)
                    \_SB.PCI0.PIB.PMWT (0xF1, Local4)
                }

                Store (\_SB.PCI0.PIB.PMRD (0xB2), Local0)
                Or (Local0, 0x80, Local0)
                \_SB.PCI0.PIB.PMWT (0xB2, Local0)
                Release (PSMX)
            }

            Name (_PCL, Package (0x01)
            {
                \_SB
            })
            Name (FBIF, 0x01)
            Name (FSTA, 0x01)
            Name (GGFG, 0x00)
            Name (PBIF, Package (0x0D)
            {
                0x01, 
                0x78, 
                0x64, 
                0x01, 
                0x2580, 
                0x05, 
                0x05, 
                0x01, 
                0x01, 
                "", 
                "", 
                "", 
                ""
            })
            Name (PBST, Package (0x04)
            {
                0x01, 
                0x78, 
                0x64, 
                0x2580
            })
            Name (PSTA, 0x1F)
        }
    }

    Method (CLTH, 1, NotSerialized)
    {
        \_SB.PCI0.PIB.PMWT (0xE6, Arg0)
        If (LGreater (Arg0, 0x00))
        {
            \_SB.PCI0.PIB.PMWT (0xAD, 0x00)
        }
        Else
        {
            And (\_SB.PCI0.PIB.PMRD (0xAD), 0xFE, Local5)
            \_SB.PCI0.PIB.PMWT (0xAD, Local5)
            And (\_SB.PCI0.PIB.PMRD (0xAF), 0xFC, Local5)
            \_SB.PCI0.PIB.PMWT (0xAF, Local5)
            \_SB.PCI0.PIB.PMWT (0xA8, 0x00)
            \_SB.PCI0.PIB.PMWT (0xA9, 0x00)
            \_SB.PCI0.PIB.PMWT (0xAA, 0x00)
            \_SB.PCI0.PIB.PMWT (0xAB, 0x00)
            \_SB.PCI0.PIB.PMWT (0xAC, 0x00)
            \_SB.PCI0.PIB.PMWT (0xAD, 0x00)
        }

        \_SB.PCI0.PIB.PMWT (0xAE, 0x00)
        \_SB.PCI0.PIB.PMWT (0xAF, 0x00)
    }

    Method (SFAN, 1, NotSerialized)
    {
        And (\_SB.PCI0.PIB.PMRD (0xFF), 0xF8, Local0)
        Or (Local0, Arg0, Local0)
        If (Arg0)
        {
            Or (Local0, 0x04, Local0)
        }

        \_SB.PCI0.PIB.PMWT (0xFF, Local0)
        \_SB.Z000 (0xA5)
    }
}


```

---

