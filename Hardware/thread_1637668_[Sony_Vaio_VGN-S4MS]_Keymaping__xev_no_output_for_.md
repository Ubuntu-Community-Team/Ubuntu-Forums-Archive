---
title: "[Sony Vaio VGN-S4M/S] Keymaping / xev no output for FN keys"
date: 2010-12-04
forum: Hardware
---

### Post by majster on 2010-12-04
Hi!

Iv been googling for a while with no luck. that's why decide to open new topic.

Problem is with keymaping my FN key on my laptop sony vaio VGN-S4M/s. Im trying to map FN keys correctly, so I fallow this HOW TO: [help.ubuntu.com/community/LaptopSpecialKeys]("https://help.ubuntu.com/community/LaptopSpecialKeys")
and get stacked on very first step.
when i run:
```
$xev
```I get nice output for almost all keys expect:
FN+F2 (MUTE)
FN+F3 (VOL DOWN)
FN+F4 (VOL UP)
FN+F5 (BRIGH DOWN)
FN+F6 (BRIGH UP)
FN+F7 (TV-OUT SWITCH)
FN+F12 (SLEEP)
FN+INSERT (PAUSE)
FN+DELETE (BREAK)
SN1 
SN2

however those FN keys works:
FN+UP_ARROW (PAGE_UP)
FN+DOWN_ARROW (PAGE_DOWN)
FN+LEFT_ARROW (HOME)
FN+RIGHT_ARROW (END)
FN+NUM_LOCK (SCROLL_LOCK) ( got scan-code but isnt mapped correctly )

I also tried:
```
$lshal -m 
```no output



```
$acpi_listen
```no output



```
$showkey -s
$showkey -k
```no output




There is out put of $acpidump:
```
/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20090521
 *
 * Disassembly of DSDT.aml, Sat Dec  4 16:55:26 2010
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x0000447B (17531)
 *     Revision         0x01 **** ACPI 1.0, no 64-bit math support
 *     Checksum         0x11
 *     OEM ID           "Sony"
 *     OEM Table ID     "V0"
 *     OEM Revision     0x20050304 (537199364)
 *     Compiler ID      "PTL "
 *     Compiler Version 0x0100000E (16777230)
 */
DefinitionBlock ("DSDT.aml", "DSDT", 1, "Sony", "V0", 0x20050304)
{
    OperationRegion (PRT0, SystemIO, 0x80, 0x04)
    Field (PRT0, DWordAcc, Lock, Preserve)
    {
        P80H,   32
    }

    OperationRegion (IO_T, SystemIO, 0x0800, 0x10)
    Field (IO_T, ByteAcc, NoLock, Preserve)
    {
                Offset (0x02), 
                Offset (0x04), 
                Offset (0x06), 
                Offset (0x08), 
        TRP0,   8, 
                Offset (0x0A), 
                Offset (0x0B), 
                Offset (0x0C), 
                Offset (0x0D), 
                Offset (0x0E), 
                Offset (0x0F), 
                Offset (0x10)
    }

    OperationRegion (GPIO, SystemIO, 0x1180, 0x3C)
    Field (GPIO, ByteAcc, NoLock, Preserve)
    {
        GU00,   8, 
        GU01,   8, 
        GU02,   8, 
        GU03,   8, 
        GIO0,   8, 
        GIO1,   8, 
        GIO2,   8, 
        GIO3,   8, 
                Offset (0x0C), 
        GL00,   8, 
        GL01,   8, 
            ,   5, 
        GP21,   1, 
                Offset (0x0F), 
        GL03,   8, 
                Offset (0x18), 
        GB00,   8, 
        GB01,   8, 
        GB02,   8, 
        GB03,   8, 
                Offset (0x2C), 
        GIV0,   8, 
        GIV1,   8, 
        GIV2,   8, 
        GIV3,   8, 
        GU04,   8, 
        GU05,   8, 
        GU06,   8, 
        GU07,   8, 
        GIO4,   8, 
        GIO5,   8, 
        GIO6,   8, 
        GIO7,   8, 
        GL04,   8, 
        GL05,   8, 
        GL06,   8, 
        GL07,   8
    }

    OperationRegion (MNVS, SystemMemory, 0x7FE9D9F7, 0x0100)
    Field (MNVS, AnyAcc, Lock, Preserve)
    {
        OSYS,   16, 
        SMIF,   8, 
        PRM0,   8, 
        PRM1,   8, 
        SCIF,   8, 
        PRM2,   8, 
        PRM3,   8, 
        LCKF,   8, 
        PRM4,   8, 
        PRM5,   8, 
        P80D,   32, 
        LIDS,   8, 
        DBGS,   8, 
                Offset (0x14), 
                Offset (0x1E), 
                Offset (0x28), 
        APIC,   8, 
        CPUL,   8, 
        CPUH,   8, 
        GV3E,   8, 
        HTTE,   8, 
        WTHT,   8, 
                Offset (0x32), 
                Offset (0x3C), 
        IGDS,   8, 
        TLST,   8, 
        CADL,   8, 
        PADL,   8, 
        CSTE,   16, 
        NSTE,   16, 
        SSTE,   16, 
        NDID,   8, 
        DID1,   32, 
        DID2,   32, 
        DID3,   32, 
        DID4,   32, 
        DID5,   32, 
                Offset (0x67), 
        BLCS,   8, 
        BRTL,   8, 
        ALSE,   8, 
        ALAF,   8, 
        LLOW,   8, 
        LHIH,   8, 
                Offset (0x6E), 
        EMAE,   8, 
        EMAP,   16, 
        EMAL,   16, 
                Offset (0x78), 
        D400,   8, 
                Offset (0x82), 
        GTF0,   56, 
        GTF2,   56, 
        IDEM,   8
    }

    OperationRegion (RCRB, SystemMemory, 0xF0008000, 0x4000)
    Field (RCRB, DWordAcc, Lock, Preserve)
    {
                Offset (0x1000), 
                Offset (0x3000), 
                Offset (0x3404), 
        HPAS,   2, 
            ,   5, 
        HPAE,   1, 
                Offset (0x3418), 
            ,   1, 
        PATD,   1, 
        SATD,   1, 
        SMBD,   1, 
        AZAD,   1, 
        A97D,   1, 
        RP1D,   1, 
        RP2D,   1, 
        RP3D,   1, 
        RP4D,   1
    }

    Mutex (MUTX, 0x00)
    Name (_S0, Package (0x03)
    {
        0x00, 
        0x00, 
        0x00
    })
    Name (_S3, Package (0x03)
    {
        0x05, 
        0x05, 
        0x00
    })
    Name (_S4, Package (0x03)
    {
        0x06, 
        0x06, 
        0x00
    })
    Name (_S5, Package (0x03)
    {
        0x07, 
        0x07, 
        0x00
    })
    Scope (\_PR)
    {
        Processor (CPU0, 0x00, 0x00001010, 0x06) {}
        Processor (CPU1, 0x01, 0x00001010, 0x06) {}
    }

    Name (\DSEN, 0x01)
    Name (\AODV, 0x00)
    Name (\CADD, 0x00)
    Name (\PADD, 0x00)
    Name (\ECON, 0x00)
    Name (\GPIC, 0x00)
    Name (\CTYP, 0x00)
    Method (\_PIC, 1, NotSerialized)
    {
        Store (Arg0, GPIC)
    }

    Method (_PTS, 1, NotSerialized)
    {
        If (LEqual (Arg0, 0x03))
        {
            Store (\_SB.PCI0.LPCB.SPIC._CRS (), \_SB.PCI0.LPCB.SPIC.SSRC)
        }

        If (LEqual (Arg0, 0x04))
        {
            Store (\_SB.PCI0.LPCB.SPIC._CRS (), \_SB.PCI0.LPCB.SPIC.SSRC)
            PHSB (0xA2, \_SB.OSTB)
        }
    }

    Method (_WAK, 1, NotSerialized)
    {
        \_SB.NCPU ()
        If (LEqual (Arg0, 0x03))
        {
            \_SB.PCI0.LPCB.SPIC._SRS (\_SB.PCI0.LPCB.SPIC.SSRC)
            If (LNot (\_SB.PCI0.LPCB.EC0.WAKI))
            {
                Notify (\_SB.PWRB, 0x02)
            }
        }

        If (LEqual (Arg0, 0x04))
        {
            \_SB.PCI0.LPCB.SPIC._SRS (\_SB.PCI0.LPCB.SPIC.SSRC)
            PHSB (0xA3, \_SB.OSTB)
            Notify (\_SB.PWRB, 0x02)
        }

        If (LEqual (\_SB.PCI0.LPCB.EC0.BAT1._STA (), 0x1F))
        {
            Notify (\_SB.PCI0.LPCB.EC0.BAT1, 0x81)
        }

        Return (Package (0x02)
        {
            0x00, 
            0x00
        })
    }

    Scope (\_SB)
    {
        Name (OSTB, Ones)
        OperationRegion (OSTY, SystemMemory, 0x7FEADAF7, 0x00000001)
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
                    If (\_OSI ("Windows 2001.1"))
                    {
                        Store (0x20, ^OSTB)
                        Store (0x20, ^TPOS)
                    }
                    Else
                    {
                        If (\_OSI ("Windows 2001 SP1"))
                        {
                            Store (0x10, ^OSTB)
                            Store (0x10, ^TPOS)
                        }
                        Else
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

    Name (\L01C, 0x00)
    Scope (\_GPE)
    {
        Mutex (GLOK, 0x00)
        Method (_L03, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB1, 0x02)
        }

        Method (_L04, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB2, 0x02)
        }

        Method (_L05, 0, NotSerialized)
        {
            If (AZAD)
            {
                Notify (\_SB.PCI0.MODM, 0x02)
            }
            Else
            {
                Notify (\_SB.PCI0.AZAL, 0x02)
            }
        }

        Method (_L07, 0, NotSerialized)
        {
            Store (0x20, \_SB.PCI0.SBUS.HSTS)
        }

        Method (_L0B, 0, NotSerialized)
        {
            If (LGreaterEqual (\_SB.OSTB, 0x08))
            {
                Acquire (GLOK, 0xFFFF)
                Sleep (0x64)
                Notify (\_SB.PCI0.PCIB.CRD0, 0x02)
                Sleep (0x64)
                Release (GLOK)
                Notify (\_SB.PCI0.PCIB, 0x02)
            }
            Else
            {
                Notify (\_SB.PCI0.PCIB, 0x02)
            }
        }

        Method (_L0C, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB3, 0x02)
        }

        Method (_L0D, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB7, 0x02)
        }

        Method (_L0E, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB4, 0x02)
        }

        Method (_L1D, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.LPCB.EC0, 0x02)
        }
    }

    OperationRegion (SMI0, SystemMemory, 0x7FEADAF8, 0x00000415)
    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
        BCMD,   8, 
        DID,    32, 
        INFO,   4096
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        INFB,   8
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        INFD,   32
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        SXBF,   8320
    }

    Field (SMI0, AnyAcc, NoLock, Preserve)
    {
                Offset (0x05), 
        INF1,   8, 
        INF2,   8
    }

    OperationRegion (SMI1, SystemIO, 0x0000FE00, 0x00000002)
    Field (SMI1, AnyAcc, NoLock, Preserve)
    {
        SMIC,   8
    }

    Mutex (MPHS, 0x00)
    Method (PHS0, 1, NotSerialized)
    {
        Store (Arg0, BCMD)
        Store (Zero, SMIC)
        While (LEqual (BCMD, Arg0)) {}
        Store (0x00, BCMD)
    }

    Method (PHS, 1, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (0x00, DID)
        PHS0 (Arg0)
        Store (INFD, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PHSD, 2, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (0x00, DID)
        Store (Arg1, INFD)
        PHS0 (Arg0)
        Store (INFD, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PHSW, 3, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (0x00, DID)
        Store (Arg1, INF1)
        Store (Arg2, INF2)
        PHS0 (Arg0)
        Store (INFB, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PHSB, 2, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (0x00, DID)
        Store (Arg1, INFB)
        PHS0 (Arg0)
        Store (INFB, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PSCS, 1, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Arg0, DID)
        PHS0 (0x00)
        Store (INFO, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PSSS, 2, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Arg0, DID)
        Store (Arg1, INFO)
        PHS0 (0x01)
        Release (MPHS)
    }

    Method (PSPS, 1, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Arg0, DID)
        PHS0 (0x02)
        Store (INFO, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Method (PSDI, 1, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Arg0, DID)
        PHS0 (0x03)
        Release (MPHS)
    }

    Method (PSST, 1, Serialized)
    {
        Acquire (MPHS, 0xFFFF)
        Store (Arg0, DID)
        PHS0 (0x04)
        Store (INFB, Local0)
        Release (MPHS)
        Return (Local0)
    }

    Scope (\_TZ)
    {
        ThermalZone (ATF0)
        {
            Method (KELV, 1, NotSerialized)
            {
                Store (Arg0, Local0)
                Multiply (Local0, 0x0A, Local0)
                Add (Local0, 0x0AAB, Local0)
                Return (Local0)
            }

            Method (_TMP, 0, NotSerialized)
            {
                If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                {
                    Store (PHSD (0xD4, 0xC0), Local1)
                }
                Else
                {
                    Store (\_SB.PCI0.LPCB.EC0.A1TP, Local1)
                }

                ShiftRight (Local1, 0x08, Local0)
                If (LGreater (Local0, 0x80))
                {
                    Sleep (0x32)
                    If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                    {
                        Store (PHSD (0xD4, 0xC0), Local1)
                    }
                    Else
                    {
                        Store (\_SB.PCI0.LPCB.EC0.A1TP, Local1)
                    }

                    ShiftRight (Local1, 0x08, Local0)
                }

                Return (KELV (Local0))
            }

            Method (_PSV, 0, NotSerialized)
            {
                If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                {
                    Store (PHSD (0xD4, 0xC4), Local1)
                }
                Else
                {
                    Store (\_SB.PCI0.LPCB.EC0.A1PT, Local1)
                }

                ShiftRight (Local1, 0x08, Local0)
                Return (KELV (Local0))
            }

            Name (_PSL, Package (0x01)
            {
                \_PR.CPU0
            })
            Method (_CRT, 0, NotSerialized)
            {
                If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                {
                    Store (PHSD (0xD4, 0xC6), Local1)
                }
                Else
                {
                    Store (\_SB.PCI0.LPCB.EC0.A1CT, Local1)
                }

                ShiftRight (Local1, 0x08, Local0)
                Return (KELV (Local0))
            }

            Name (_TC1, 0x01)
            Name (_TC2, 0x02)
            Name (_TSP, 0x32)
        }
    }

    Method (GETP, 1, Serialized)
    {
        If (LEqual (And (Arg0, 0x09), 0x00))
        {
            Return (0xFFFFFFFF)
        }

        If (LEqual (And (Arg0, 0x09), 0x08))
        {
            Return (0x0384)
        }

        ShiftRight (And (Arg0, 0x0300), 0x08, Local0)
        ShiftRight (And (Arg0, 0x3000), 0x0C, Local1)
        Return (Multiply (0x1E, Subtract (0x09, Add (Local0, Local1))
            ))
    }

    Method (GDMA, 5, Serialized)
    {
        If (Arg0)
        {
            If (LAnd (Arg1, Arg4))
            {
                Return (0x14)
            }

            If (LAnd (Arg2, Arg4))
            {
                Return (Multiply (Subtract (0x04, Arg3), 0x0F))
            }

            Return (Multiply (Subtract (0x04, Arg3), 0x1E))
        }

        Return (0xFFFFFFFF)
    }

    Method (GETT, 1, Serialized)
    {
        Return (Multiply (0x1E, Subtract (0x09, Add (And (ShiftRight (Arg0, 0x02
            ), 0x03), And (Arg0, 0x03)))))
    }

    Method (GETF, 3, Serialized)
    {
        Name (TMPF, 0x00)
        If (Arg0)
        {
            Or (TMPF, 0x01, TMPF)
        }

        If (And (Arg2, 0x02))
        {
            Or (TMPF, 0x02, TMPF)
        }

        If (Arg1)
        {
            Or (TMPF, 0x04, TMPF)
        }

        If (And (Arg2, 0x20))
        {
            Or (TMPF, 0x08, TMPF)
        }

        If (And (Arg2, 0x4000))
        {
            Or (TMPF, 0x10, TMPF)
        }

        Return (TMPF)
    }

    Method (SETP, 3, Serialized)
    {
        If (LGreater (Arg0, 0xF0))
        {
            Return (0x08)
        }
        Else
        {
            If (And (Arg1, 0x02))
            {
                If (LAnd (LLessEqual (Arg0, 0x78), And (Arg2, 0x02)))
                {
                    Return (0x2301)
                }

                If (LAnd (LLessEqual (Arg0, 0xB4), And (Arg2, 0x01)))
                {
                    Return (0x2101)
                }
            }

            Return (0x1001)
        }
    }

    Method (SDMA, 1, Serialized)
    {
        If (LLessEqual (Arg0, 0x14))
        {
            Return (0x01)
        }

        If (LLessEqual (Arg0, 0x1E))
        {
            Return (0x02)
        }

        If (LLessEqual (Arg0, 0x2D))
        {
            Return (0x01)
        }

        If (LLessEqual (Arg0, 0x3C))
        {
            Return (0x02)
        }

        If (LLessEqual (Arg0, 0x5A))
        {
            Return (0x01)
        }

        Return (0x00)
    }

    Method (SETT, 3, Serialized)
    {
        If (And (Arg1, 0x02))
        {
            If (LAnd (LLessEqual (Arg0, 0x78), And (Arg2, 0x02)))
            {
                Return (0x0B)
            }

            If (LAnd (LLessEqual (Arg0, 0xB4), And (Arg2, 0x01)))
            {
                Return (0x09)
            }
        }

        Return (0x04)
    }

    Method (P8XH, 2, Serialized)
    {
    }

    Scope (\_SB)
    {
        Device (LID0)
        {
            Name (_HID, EisaId ("PNP0C0D"))
            Method (_LID, 0, NotSerialized)
            {
                If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                {
                    And (PHSB (0xD4, 0x82), 0x04, Local0)
                }
                Else
                {
                    Store (\_SB.PCI0.LPCB.EC0.LIDS, Local0)
                }

                Return (Local0)
            }
        }

        Device (PWRB)
        {
            Name (_HID, EisaId ("PNP0C0C"))
            Name (_PRW, Package (0x02)
            {
                0x1D, 
                0x04
            })
        }

        Mutex (PLOK, 0x00)
        Method (NCPU, 0, NotSerialized)
        {
            Acquire (PLOK, 0xFFFF)
            Notify (\_PR.CPU0, 0x80)
            Sleep (0x64)
            Notify (\_PR.CPU0, 0x81)
            Release (PLOK)
        }

        Device (PCI0)
        {
            Method (_INI, 0, NotSerialized)
            {
                \_SB.OSTP ()
            }

            Method (_S1D, 0, NotSerialized)
            {
                Return (0x02)
            }

            Method (_S3D, 0, NotSerialized)
            {
                Return (0x02)
            }

            Method (_S4D, 0, NotSerialized)
            {
                Return (0x02)
            }

            Name (_HID, EisaId ("PNP0A08"))
            Name (_CID, EisaId ("PNP0A03"))
            Name (_ADR, 0x00)
            Name (_BBN, 0x00)
            OperationRegion (HBUS, PCI_Config, 0x40, 0xC0)
            Field (HBUS, DWordAcc, NoLock, Preserve)
            {
                        Offset (0x50), 
                    ,   4, 
                PM0H,   2, 
                        Offset (0x51), 
                PM1L,   2, 
                    ,   2, 
                PM1H,   2, 
                        Offset (0x52), 
                PM2L,   2, 
                    ,   2, 
                PM2H,   2, 
                        Offset (0x53), 
                PM3L,   2, 
                    ,   2, 
                PM3H,   2, 
                        Offset (0x54), 
                PM4L,   2, 
                    ,   2, 
                PM4H,   2, 
                        Offset (0x55), 
                PM5L,   2, 
                    ,   2, 
                PM5H,   2, 
                        Offset (0x56), 
                PM6L,   2, 
                    ,   2, 
                PM6H,   2, 
                        Offset (0x57), 
                    ,   7, 
                HENA,   1, 
                        Offset (0x5C), 
                    ,   3, 
                TOUD,   5
            }

            Name (BUF0, ResourceTemplate ()
            {
                WordBusNumber (ResourceProducer, MinFixed, MaxFixed, PosDecode,
                    0x0000,             // Granularity
                    0x0000,             // Range Minimum
                    0x00FF,             // Range Maximum
                    0x0000,             // Translation Offset
                    0x0100,             // Length
                    0x00,, )
                DWordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0x00000CF7,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000CF8,         // Length
                    0x00,, , TypeStatic)
                IO (Decode16,
                    0x0CF8,             // Range Minimum
                    0x0CF8,             // Range Maximum
                    0x01,               // Alignment
                    0x08,               // Length
                    )
                DWordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x00000000,         // Granularity
                    0x00000D00,         // Range Minimum
                    0x0000FFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x0000F300,         // Length
                    0x00,, , TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000A0000,         // Range Minimum
                    0x000BFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00020000,         // Length
                    0x00,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C0000,         // Range Minimum
                    0x000C3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y00, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C4000,         // Range Minimum
                    0x000C7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y01, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C8000,         // Range Minimum
                    0x000CBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y02, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000CC000,         // Range Minimum
                    0x000CFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y03, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D0000,         // Range Minimum
                    0x000D3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y04, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D4000,         // Range Minimum
                    0x000D7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y05, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D8000,         // Range Minimum
                    0x000DBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y06, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000DC000,         // Range Minimum
                    0x000DFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y07, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E0000,         // Range Minimum
                    0x000E3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y08, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E4000,         // Range Minimum
                    0x000E7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y09, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E8000,         // Range Minimum
                    0x000EBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y0A, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000EC000,         // Range Minimum
                    0x000EFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    0x00,, _Y0B, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000F0000,         // Range Minimum
                    0x000FFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00010000,         // Length
                    0x00,, _Y0C, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0xFEBFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    0x00,, _Y0D, AddressRangeMemory, TypeStatic)
            })
            Method (_CRS, 0, Serialized)
            {
                If (PM1L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y00._LEN, C0LN)
                    Store (Zero, C0LN)
                }

                If (LEqual (PM1L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y00._RW, C0RW)
                    Store (Zero, C0RW)
                }

                If (PM1H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y01._LEN, C4LN)
                    Store (Zero, C4LN)
                }

                If (LEqual (PM1H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y01._RW, C4RW)
                    Store (Zero, C4RW)
                }

                If (PM2L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y02._LEN, C8LN)
                    Store (Zero, C8LN)
                }

                If (LEqual (PM2L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y02._RW, C8RW)
                    Store (Zero, C8RW)
                }

                If (PM2H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y03._LEN, CCLN)
                    Store (Zero, CCLN)
                }

                If (LEqual (PM2H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y03._RW, CCRW)
                    Store (Zero, CCRW)
                }

                If (PM3L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y04._LEN, D0LN)
                    Store (Zero, D0LN)
                }

                If (LEqual (PM3L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y04._RW, D0RW)
                    Store (Zero, D0RW)
                }

                If (PM3H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y05._LEN, D4LN)
                    Store (Zero, D4LN)
                }

                If (LEqual (PM3H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y05._RW, D4RW)
                    Store (Zero, D4RW)
                }

                If (PM4L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y06._LEN, D8LN)
                    Store (Zero, D8LN)
                }

                If (LEqual (PM4L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y06._RW, D8RW)
                    Store (Zero, D8RW)
                }

                If (PM4H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y07._LEN, DCLN)
                    Store (Zero, DCLN)
                }

                If (LEqual (PM4H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y07._RW, DCRW)
                    Store (Zero, DCRW)
                }

                If (PM5L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y08._LEN, E0LN)
                    Store (Zero, E0LN)
                }

                If (LEqual (PM5L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y08._RW, E0RW)
                    Store (Zero, E0RW)
                }

                If (PM5H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y09._LEN, E4LN)
                    Store (Zero, E4LN)
                }

                If (LEqual (PM5H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y09._RW, E4RW)
                    Store (Zero, E4RW)
                }

                If (PM6L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0A._LEN, E8LN)
                    Store (Zero, E8LN)
                }

                If (LEqual (PM6L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0A._RW, E8RW)
                    Store (Zero, E8RW)
                }

                If (PM6H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0B._LEN, ECLN)
                    Store (Zero, ECLN)
                }

                If (LEqual (PM6H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0B._RW, ECRW)
                    Store (Zero, ECRW)
                }

                If (PM0H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0C._LEN, F0LN)
                    Store (Zero, F0LN)
                }

                If (LEqual (PM0H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0C._RW, F0RW)
                    Store (Zero, F0RW)
                }

                CreateDWordField (BUF0, \_SB.PCI0._Y0D._MIN, M1MN)
                CreateDWordField (BUF0, \_SB.PCI0._Y0D._MAX, M1MX)
                CreateDWordField (BUF0, \_SB.PCI0._Y0D._LEN, M1LN)
                ShiftLeft (TOUD, 0x1B, M1MN)
                Add (Subtract (M1MX, M1MN), 0x01, M1LN)
                Return (BUF0)
            }

            Method (_PRT, 0, NotSerialized)
            {
                If (GPIC)
                {
                    Return (Package (0x0F)
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
                            0x0002FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0007FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x001BFFFF, 
                            0x00, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x00, 
                            0x00, 
                            0x14
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x01, 
                            0x00, 
                            0x15
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x02, 
                            0x00, 
                            0x16
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x03, 
                            0x00, 
                            0x17
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x00, 
                            0x00, 
                            0x11
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x01, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x02, 
                            0x00, 
                            0x15
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x03, 
                            0x00, 
                            0x17
                        }, 

                        Package (0x04)
                        {
                            0x001EFFFF, 
                            0x00, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001EFFFF, 
                            0x01, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x01, 
                            0x00, 
                            0x12
                        }
                    })
                }
                Else
                {
                    Return (Package (0x0F)
                    {
                        Package (0x04)
                        {
                            0x0001FFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0002FFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0007FFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001BFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKE, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKF, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x02, 
                            \_SB.PCI0.LPCB.LNKG, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x03, 
                            \_SB.PCI0.LPCB.LNKH, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKB, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x02, 
                            \_SB.PCI0.LPCB.LNKF, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x03, 
                            \_SB.PCI0.LPCB.LNKH, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001EFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001EFFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKC, 
                            0x00
                        }
                    })
                }
            }

            Device (PDRC)
            {
                Name (_HID, EisaId ("PNP0C02"))
                Name (_UID, 0x01)
                Name (_CRS, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0xE0000000,         // Address Base
                        0x10000000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xF0000000,         // Address Base
                        0x00004000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xF0004000,         // Address Base
                        0x00001000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xF0005000,         // Address Base
                        0x00001000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xF0008000,         // Address Base
                        0x00004000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED20000,         // Address Base
                        0x00070000,         // Address Length
                        )
                })
            }

            Device (PEGP)
            {
                Name (_ADR, 0x00010000)
                Method (_PRT, 0, NotSerialized)
                {
                    If (\GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x13
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKB, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKC, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKD, 
                                0x00
                            }
                        })
                    }
                }

                Device (NGFX)
                {
                    Name (_ADR, 0x00)
                    Method (_DOS, 1, NotSerialized)
                    {
                        Store (And (Arg0, 0x03), DSEN)
                        If (LEqual (DSEN, 0x00))
                        {
                            Store (0x00, AODV)
                        }
                    }

                    Method (_DOD, 0, NotSerialized)
                    {
                        Return (Package (0x04)
                        {
                            0x0100, 
                            0x0118, 
                            0x0200, 
                            0x0111
                        })
                    }

                    Device (LCD)
                    {
                        Name (_ADR, 0x0118)
                        Method (_DCS, 0, NotSerialized)
                        {
                            Store (0x0D, Local0)
                            Store (PHS (0xA5), Local1)
                            If (And (Local1, ShiftLeft (0x01, 0x08)))
                            {
                                Or (Local0, 0x10, Local0)
                            }

                            If (And (Local1, 0x01))
                            {
                                Or (Local0, 0x02, Local0)
                            }

                            Return (Local0)
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (And (AODV, 0x01))
                            {
                                Return (0x01)
                            }

                            Return (0x00)
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }

                    Device (CRT)
                    {
                        Name (_ADR, 0x0100)
                        Method (_DCS, 0, NotSerialized)
                        {
                            Store (0x0D, Local0)
                            Store (PHS (0xA5), Local1)
                            If (And (Local1, ShiftLeft (0x02, 0x08)))
                            {
                                Or (Local0, 0x10, Local0)
                            }

                            If (And (Local1, 0x02))
                            {
                                Or (Local0, 0x02, Local0)
                            }

                            Return (Local0)
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (And (AODV, 0x02))
                            {
                                Return (0x01)
                            }

                            Return (0x00)
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }

                    Device (TV)
                    {
                        Name (_ADR, 0x0200)
                        Method (_DCS, 0, NotSerialized)
                        {
                            Store (0x0D, Local0)
                            Store (PHS (0xA5), Local1)
                            If (And (Local1, ShiftLeft (0x04, 0x08)))
                            {
                                Or (Local0, 0x10, Local0)
                            }

                            If (And (Local1, 0x04))
                            {
                                Or (Local0, 0x02, Local0)
                            }

                            Return (Local0)
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (And (AODV, 0x04))
                            {
                                Return (0x01)
                            }

                            Return (0x00)
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }

                    Device (DVI)
                    {
                        Name (_ADR, 0x0111)
                        Method (_DCS, 0, NotSerialized)
                        {
                            Store (0x0D, Local0)
                            Store (PHS (0xA5), Local1)
                            If (And (Local1, ShiftLeft (0x08, 0x08)))
                            {
                                Or (Local0, 0x10, Local0)
                            }

                            If (And (Local1, 0x08))
                            {
                                Or (Local0, 0x02, Local0)
                            }

                            Return (Local0)
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (And (AODV, 0x08))
                            {
                                Return (0x01)
                            }

                            Return (0x00)
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }
                }
            }

            Device (GFX0)
            {
                Name (_ADR, 0x00020000)
                OperationRegion (VNVS, SystemMemory, 0x7FE9DAF7, 0x00010000)
                Field (VNVS, AnyAcc, Lock, Preserve)
                {
                    VBF1,   262144, 
                    VBF2,   262144
                }

                Method (_DOS, 1, NotSerialized)
                {
                    Store (And (Arg0, 0x03), DSEN)
                    If (LEqual (DSEN, 0x00))
                    {
                        Store (0x00, AODV)
                    }
                }

                Method (_DOD, 0, NotSerialized)
                {
                    Name (TMP, Package (0x04)
                    {
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF
                    })
                    Store (DID1, Index (TMP, 0x00))
                    Store (DID2, Index (TMP, 0x01))
                    Store (DID3, Index (TMP, 0x02))
                    Store (DID4, Index (TMP, 0x03))
                    Return (TMP)
                }

                Method (_ROM, 2, NotSerialized)
                {
                    If (LGreaterEqual (Arg0, 0x8000))
                    {
                        Return (GETB (Subtract (Arg0, 0x8000), Arg1, VBF2))
                    }

                    If (LGreater (Add (Arg0, Arg1), 0x8000))
                    {
                        Subtract (0x8000, Arg0, Local0)
                        Subtract (Arg1, Local0, Local1)
                        Store (GETB (Arg0, Local0, VBF1), Local3)
                        Store (GETB (0x00, Local1, VBF2), Local4)
                        Concatenate (Local3, Local4, Local5)
                        Return (Local5)
                    }

                    Return (GETB (Arg0, Arg1, VBF1))
                }

                Device (LCD)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID4))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        If (And (PHS (0xA5), ShiftLeft (0x01, 0x10)))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (AODV, 0x01))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                    }
                }

                Device (CRT)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID1))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        If (And (PHS (0xA5), ShiftLeft (0x02, 0x10)))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (AODV, 0x02))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                    }
                }

                Device (TV)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID2))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        If (And (PHS (0xA5), ShiftLeft (0x04, 0x10)))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (AODV, 0x04))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                    }
                }

                Device (DVI)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID3))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        If (And (PHS (0xA5), ShiftLeft (0x08, 0x10)))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (AODV, 0x08))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                    }
                }

                Method (GETB, 3, Serialized)
                {
                    Multiply (Arg0, 0x08, Local0)
                    Multiply (Arg1, 0x08, Local1)
                    CreateField (Arg2, Local0, Local1, TBF3)
                    Return (TBF3)
                }
            }

            Device (AZAL)
            {
                Name (_ADR, 0x001B0000)
            }

            Device (USB1)
            {
                Name (_ADR, 0x001D0000)
                OperationRegion (U1CS, PCI_Config, 0xC4, 0x04)
                Field (U1CS, DWordAcc, NoLock, Preserve)
                {
                    U1EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x03, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U1EN)
                    }
                    Else
                    {
                        Store (0x00, U1EN)
                    }
                }

                Method (_S1D, 0, NotSerialized)
                {
                    If (LEqual (\_SB.OSTB, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x01)
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB2)
            {
                Name (_ADR, 0x001D0001)
                OperationRegion (U2CS, PCI_Config, 0xC4, 0x04)
                Field (U2CS, DWordAcc, NoLock, Preserve)
                {
                    U2EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x04, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U2EN)
                    }
                    Else
                    {
                        Store (0x00, U2EN)
                    }
                }

                Method (_S1D, 0, NotSerialized)
                {
                    If (LEqual (\_SB.OSTB, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x01)
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB3)
            {
                Name (_ADR, 0x001D0002)
                OperationRegion (U2CS, PCI_Config, 0xC4, 0x04)
                Field (U2CS, DWordAcc, NoLock, Preserve)
                {
                    U3EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x0C, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U3EN)
                    }
                    Else
                    {
                        Store (0x00, U3EN)
                    }
                }

                Method (_S1D, 0, NotSerialized)
                {
                    If (LEqual (\_SB.OSTB, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x01)
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB4)
            {
                Name (_ADR, 0x001D0003)
                OperationRegion (U4CS, PCI_Config, 0xC4, 0x04)
                Field (U4CS, DWordAcc, NoLock, Preserve)
                {
                    U4EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x0E, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U4EN)
                    }
                    Else
                    {
                        Store (0x00, U4EN)
                    }
                }

                Method (_S1D, 0, NotSerialized)
                {
                    If (LEqual (\_SB.OSTB, 0x02))
                    {
                        Return (0x02)
                    }

                    Return (0x01)
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB7)
            {
                Name (_ADR, 0x001D0007)
                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x03
                })
            }

            Device (PCIB)
            {
                Name (_ADR, 0x001E0000)
                Device (LANC)
                {
                    Name (_ADR, 0x00080000)
                    Name (_PRW, Package (0x02)
                    {
                        0x0B, 
                        0x03
                    })
                }

                Device (WLAN)
                {
                    Name (_ADR, 0x000B0000)
                    Name (_PSC, 0x00)
                    Method (_PS0, 0, NotSerialized)
                    {
                        Store (0x00, _PSC)
                    }

                    Method (_PS3, 0, NotSerialized)
                    {
                        Store (0x03, _PSC)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }
                }

                Device (CRD0)
                {
                    Name (_ADR, 0x00050000)
                    OperationRegion (CCRD, PCI_Config, 0x00, 0xE4)
                    Field (CCRD, DWordAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        CD04,   32, 
                                Offset (0x3E), 
                        CD3E,   32, 
                                Offset (0x44), 
                        CD44,   32
                    }

                    Method (_INI, 0, NotSerialized)
                    {
                        Store (Zero, CD44)
                    }

                    Name (_PSC, 0x00)
                    Method (_PS0, 0, NotSerialized)
                    {
                        Store (0x00, _PSC)
                    }

                    Method (_PS3, 0, NotSerialized)
                    {
                        Store (0x03, _PSC)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }
                }

                Device (SD94)
                {
                    Name (_ADR, 0x00050002)
                }

                Device (MMST)
                {
                    Name (_ADR, 0x00050003)
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (GPIC)
                    {
                        Return (Package (0x0A)
                        {
                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x00, 
                                0x00, 
                                0x14
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x01, 
                                0x00, 
                                0x15
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x02, 
                                0x00, 
                                0x16
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x03, 
                                0x00, 
                                0x17
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x00, 
                                0x00, 
                                0x15
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x01, 
                                0x00, 
                                0x17
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x02, 
                                0x00, 
                                0x14
                            }, 

                            Package (0x04)
                            {
                                0x000BFFFF, 
                                0x00, 
                                0x00, 
                                0x16
                            }, 

                            Package (0x04)
                            {
                                0x000BFFFF, 
                                0x01, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0x0008FFFF, 
                                0x00, 
                                0x00, 
                                0x14
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x0A)
                        {
                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKE, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKF, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKG, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKH, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKF, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKH, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKE, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x000BFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKG, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x000BFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0008FFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKE, 
                                0x00
                            }
                        })
                    }
                }
            }

            Device (AUD0)
            {
                Name (_ADR, 0x001E0002)
            }

            Device (MODM)
            {
                Name (_ADR, 0x001E0003)
            }

            Device (LPCB)
            {
                Name (_ADR, 0x001F0000)
                OperationRegion (LPC0, PCI_Config, 0x40, 0xC0)
                Field (LPC0, AnyAcc, NoLock, Preserve)
                {
                            Offset (0x20), 
                    PARC,   8, 
                    PBRC,   8, 
                    PCRC,   8, 
                    PDRC,   8, 
                            Offset (0x28), 
                    PERC,   8, 
                    PFRC,   8, 
                    PGRC,   8, 
                    PHRC,   8, 
                            Offset (0x40), 
                    IOD0,   8, 
                    IOD1,   8, 
                    IOD2,   8, 
                    IOD3,   8, 
                    GID1,   16, 
                            Offset (0x48), 
                    GID2,   16, 
                            Offset (0x6D), 
                    MISC,   8
                }

                Device (LNKA)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x01)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PARC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {10}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLA, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y0E)
                                {}
                        })
                        CreateWordField (RTLA, \_SB.PCI0.LPCB.LNKA._CRS._Y0E._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PARC, 0x0F), IRQ0)
                        Return (RTLA)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PARC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PARC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKB)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x02)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PBRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {10}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLB, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y0F)
                                {}
                        })
                        CreateWordField (RTLB, \_SB.PCI0.LPCB.LNKB._CRS._Y0F._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PBRC, 0x0F), IRQ0)
                        Return (RTLB)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PBRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PBRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKC)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x03)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PCRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {10}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLC, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y10)
                                {}
                        })
                        CreateWordField (RTLC, \_SB.PCI0.LPCB.LNKC._CRS._Y10._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PCRC, 0x0F), IRQ0)
                        Return (RTLC)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PCRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PCRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKD)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x04)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PDRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {10}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLD, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y11)
                                {}
                        })
                        CreateWordField (RTLD, \_SB.PCI0.LPCB.LNKD._CRS._Y11._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PDRC, 0x0F), IRQ0)
                        Return (RTLD)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PDRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PDRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKE)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x05)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PERC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {10}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLE, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y12)
                                {}
                        })
                        CreateWordField (RTLE, \_SB.PCI0.LPCB.LNKE._CRS._Y12._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PERC, 0x0F), IRQ0)
                        Return (RTLE)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PERC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PERC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKF)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x06)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PFRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {10}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLF, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y13)
                                {}
                        })
                        CreateWordField (RTLF, \_SB.PCI0.LPCB.LNKF._CRS._Y13._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PFRC, 0x0F), IRQ0)
                        Return (RTLF)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PFRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PFRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKG)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x07)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PGRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {10}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLG, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y14)
                                {}
                        })
                        CreateWordField (RTLG, \_SB.PCI0.LPCB.LNKG._CRS._Y14._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PGRC, 0x0F), IRQ0)
                        Return (RTLG)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PGRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PGRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKH)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x08)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PHRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {10}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLH, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y15)
                                {}
                        })
                        CreateWordField (RTLH, \_SB.PCI0.LPCB.LNKH._CRS._Y15._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PHRC, 0x0F), IRQ0)
                        Return (RTLH)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PHRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PHRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (DMAC)
                {
                    Name (_HID, EisaId ("PNP0200"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        IO (Decode16,
                            0x0081,             // Range Minimum
                            0x0081,             // Range Maximum
                            0x01,               // Alignment
                            0x11,               // Length
                            )
                        IO (Decode16,
                            0x0093,             // Range Minimum
                            0x0093,             // Range Maximum
                            0x01,               // Alignment
                            0x0D,               // Length
                            )
                        IO (Decode16,
                            0x00C0,             // Range Minimum
                            0x00C0,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        DMA (Compatibility, NotBusMaster, Transfer8_16, )
                            {4}
                    })
                }

                Device (FWHD)
                {
                    Name (_HID, EisaId ("INT0800"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0xFF000000,         // Address Base
                            0x01000000,         // Address Length
                            )
                    })
                }

                Device (HPET)
                {
                    Name (_HID, EisaId ("PNP0103"))
                    Name (BUF0, ResourceTemplate ()
                    {
                        IRQNoFlags ()
                            {0}
                        IRQNoFlags ()
                            {8}
                        Memory32Fixed (ReadOnly,
                            0xFED00000,         // Address Base
                            0x00000400,         // Address Length
                            _Y16)
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LGreaterEqual (\_SB.OSTB, 0x08))
                        {
                            If (HPAE)
                            {
                                Return (0x0F)
                            }
                        }
                        Else
                        {
                            If (HPAE)
                            {
                                Return (0x0B)
                            }
                        }

                        Return (0x00)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        If (HPAE)
                        {
                            CreateDWordField (BUF0, \_SB.PCI0.LPCB.HPET._Y16._BAS, HPT0)
                            If (LEqual (HPAS, 0x01))
                            {
                                Store (0xFED01000, HPT0)
                            }

                            If (LEqual (HPAS, 0x02))
                            {
                                Store (0xFED02000, HPT0)
                            }

                            If (LEqual (HPAS, 0x03))
                            {
                                Store (0xFED03000, HPT0)
                            }
                        }

                        Return (BUF0)
                    }
                }

                Device (IPIC)
                {
                    Name (_HID, EisaId ("PNP0000"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0020,             // Range Minimum
                            0x0020,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0024,             // Range Minimum
                            0x0024,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0028,             // Range Minimum
                            0x0028,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x002C,             // Range Minimum
                            0x002C,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0030,             // Range Minimum
                            0x0030,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0034,             // Range Minimum
                            0x0034,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0038,             // Range Minimum
                            0x0038,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x003C,             // Range Minimum
                            0x003C,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A0,             // Range Minimum
                            0x00A0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A4,             // Range Minimum
                            0x00A4,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A8,             // Range Minimum
                            0x00A8,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00AC,             // Range Minimum
                            0x00AC,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B0,             // Range Minimum
                            0x00B0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B4,             // Range Minimum
                            0x00B4,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B8,             // Range Minimum
                            0x00B8,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00BC,             // Range Minimum
                            0x00BC,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x04D0,             // Range Minimum
                            0x04D0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IRQNoFlags ()
                            {2}
                    })
                }

                Device (MATH)
                {
                    Name (_HID, EisaId ("PNP0C04"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x00F0,             // Range Minimum
                            0x00F0,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQNoFlags ()
                            {13}
                    })
                }

                Device (MBD0)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x02)
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x002E,             // Range Minimum
                            0x002E,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x004E,             // Range Minimum
                            0x004E,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0061,             // Range Minimum
                            0x0061,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0063,             // Range Minimum
                            0x0063,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0065,             // Range Minimum
                            0x0065,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0067,             // Range Minimum
                            0x0067,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
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
                            0x00B2,             // Range Minimum
                            0x00B2,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0680,             // Range Minimum
                            0x0680,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x0800,             // Range Minimum
                            0x0800,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x1000,             // Range Minimum
                            0x1000,             // Range Maximum
                            0x01,               // Alignment
                            0x80,               // Length
                            )
                        IO (Decode16,
                            0x1180,             // Range Minimum
                            0x1180,             // Range Maximum
                            0x01,               // Alignment
                            0x40,               // Length
                            )
                        IO (Decode16,
                            0xFE00,             // Range Minimum
                            0xFE00,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        Memory32Fixed (ReadWrite,
                            0xD000C000,         // Address Base
                            0x00004000,         // Address Length
                            )
                    })
                }

                Device (MBD1)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x02)
                    Name (_CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadWrite,
                            0xFEC00000,         // Address Base
                            0x00001000,         // Address Length
                            )
                        Memory32Fixed (ReadWrite,
                            0xFEE00000,         // Address Base
                            0x00001000,         // Address Length
                            )
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LLessEqual (\_SB.OSTB, 0x02))
                        {
                            If (LOr (GPIC, HTTE))
                            {
                                Return (0x0B)
                            }
                        }

                        Return (0x00)
                    }
                }

                Device (RTC)
                {
                    Name (_HID, EisaId ("PNP0B00"))
                    Name (BUF0, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x08,               // Length
                            )
                    })
                    Name (BUF1, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x08,               // Length
                            )
                        IRQNoFlags ()
                            {8}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        If (HPAE)
                        {
                            Return (BUF0)
                        }

                        Return (BUF1)
                    }
                }

                Device (TIMR)
                {
                    Name (_HID, EisaId ("PNP0100"))
                    Name (BUF0, ResourceTemplate ()
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
                    })
                    Name (BUF1, ResourceTemplate ()
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
                    Method (_CRS, 0, Serialized)
                    {
                        If (HPAE)
                        {
                            Return (BUF0)
                        }

                        Return (BUF1)
                    }
                }

                Device (EC0)
                {
                    Name (_HID, EisaId ("PNP0C09"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0062,             // Range Minimum
                            0x0062,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0066,             // Range Minimum
                            0x0066,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                    })
                    Name (_GPE, 0x17)
                    Name (ECOK, 0x00)
                    Method (_REG, 2, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x03))
                        {
                            Store (Arg1, ECOK)
                        }
                    }

                    Name (_PRW, Package (0x02)
                    {
                        0x1D, 
                        0x05
                    })
                    OperationRegion (ECR, EmbeddedControl, 0x00, 0xFF)
                    Field (ECR, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x80), 
                        MPBP,   1, 
                        MPBD,   1, 
                        DOKD,   1, 
                        DFBP,   1, 
                                Offset (0x81), 
                        BT1A,   1, 
                        BT2A,   1, 
                        ACAT,   1, 
                                Offset (0x82), 
                        PWRB,   1, 
                        JOGB,   1, 
                        LIDS,   1, 
                                Offset (0x83), 
                        BT1P,   1, 
                        BT2P,   1, 
                                Offset (0x84), 
                        B1ST,   8, 
                        B2ST,   8, 
                                Offset (0x90), 
                        MASK,   8, 
                        BT1S,   1, 
                        BT2S,   1, 
                                Offset (0x92), 
                        BT1W,   1, 
                        BT2W,   1, 
                                Offset (0x93), 
                        FAN0,   8, 
                            ,   7, 
                        IRST,   1, 
                        PHYO,   1, 
                                Offset (0x96), 
                        BRIT,   8, 
                        CONT,   8, 
                        SNDU,   1, 
                        SNDD,   1, 
                                Offset (0x99), 
                        SMDM,   1, 
                                Offset (0x9A), 
                                Offset (0x9B), 
                        SIRQ,   8, 
                        SLOB,   8, 
                        SHIB,   8, 
                        MPWR,   1, 
                        WAKI,   1, 
                                Offset (0x9F), 
                                Offset (0xA0), 
                        B1RC,   16, 
                        B1AB,   16, 
                        B1AC,   16, 
                        B1VO,   16, 
                        B2RC,   16, 
                        B2AB,   16, 
                        B2AC,   16, 
                        B2VO,   16, 
                        B1DC,   16, 
                        B1LF,   16, 
                        B1DV,   16, 
                        B1DL,   16, 
                        B2DC,   16, 
                        B2LF,   16, 
                        B2DV,   16, 
                        B2DL,   16, 
                        A1TP,   16, 
                        A1AT,   16, 
                        A1PT,   16, 
                        A1CT,   16, 
                        A2TP,   16, 
                        A2AT,   16, 
                        A2PT,   16, 
                        A2CT,   16
                    }

                    Method (_Q50, 0, NotSerialized)
                    {
                        Notify (ACAD, 0x80)
                        \_SB.NCPU ()
                    }

                    Method (_Q51, 0, NotSerialized)
                    {
                        If (BT1A)
                        {
                            Notify (BAT1, 0x00)
                        }
                        Else
                        {
                            Notify (BAT1, 0x01)
                        }

                        Notify (BAT1, 0x80)
                    }

                    Method (_Q53, 0, NotSerialized)
                    {
                        Store ("_Q53:Battery Selection", Debug)
                    }

                    Method (_Q58, 0, NotSerialized)
                    {
                        Store ("_Q58:ATF temperature trip point changd", Debug)
                        Notify (\_TZ.ATF0, 0x81)
                    }

                    Method (_Q5F, 0, NotSerialized)
                    {
                        Store ("_Q5F:ATF temperature reaches trip point", Debug)
                        Notify (\_TZ.ATF0, 0x80)
                    }

                    Method (_Q60, 0, NotSerialized)
                    {
                        Notify (\_SB.PWRB, 0x80)
                    }

                    Method (_Q66, 0, NotSerialized)
                    {
                        Notify (\_SB.LID0, 0x80)
                    }

                    Device (BAT1)
                    {
                        Name (_HID, EisaId ("PNP0C0A"))
                        Name (_UID, 0x01)
                        Name (_PCL, Package (0x01)
                        {
                            \_SB
                        })
                        Name (BATI, Package (0x0D)
                        {
                            0x00, 
                            0x9650, 
                            0x9650, 
                            0x00, 
                            0x39D0, 
                            0x00, 
                            0x78, 
                            0x00, 
                            0x0A, 
                            "", 
                            "", 
                            "LION", 
                            "Sony Corp."
                        })
                        Name (BATS, Package (0x04)
                        {
                            0x02, 
                            0xFFFFFFFF, 
                            0x0D7A, 
                            0x3840
                        })
                        Method (_STA, 0, NotSerialized)
                        {
                            If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                            {
                                And (PHSD (0xD4, 0x80), 0x0100, Local1)
                            }
                            Else
                            {
                                Store (BT1A, Local1)
                            }

                            If (Local1)
                            {
                                Store (0x1F, Local0)
                            }
                            Else
                            {
                                Store (0x0F, Local0)
                            }

                            Return (Local0)
                        }

                        Method (_BIF, 0, NotSerialized)
                        {
                            If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                            {
                                Store (PHSD (0xD4, 0xB0), Local0)
                                Store (PHSD (0xD4, 0xB2), Local1)
                                Store (PHSD (0xD4, 0xB6), Local2)
                            }
                            Else
                            {
                                Store (B1DC, Local0)
                                Store (B1LF, Local1)
                                Store (B1DV, Local2)
                            }

                            Multiply (Local0, 0x0A, Index (BATI, 0x01))
                            Multiply (Local1, 0x0A, Index (BATI, 0x02))
                            Store (Local2, Index (BATI, 0x04))
                            Return (BATI)
                        }

                        Method (_BST, 0, NotSerialized)
                        {
                            If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                            {
                                Store (And (PHSD (0xD4, 0x84), 0xFF, Local0), Index (BATS, 0x00
                                    ))
                                Store (PHSD (0xD4, 0xA6), Local0)
                                Store (PHSD (0xD4, 0xA4), Local1)
                                Store (PHSD (0xD4, 0xA2), Local2)
                            }
                            Else
                            {
                                Store (B1ST, Index (BATS, 0x00))
                                Store (B1VO, Local0)
                                Store (B1AC, Local1)
                                Store (B1AB, Local2)
                            }

                            If (LEqual (Local1, 0xFFFF))
                            {
                                Store (0xFFFFFFFF, Local1)
                            }
                            Else
                            {
                                If (LGreaterEqual (Local1, 0x8000))
                                {
                                    XOr (Local1, 0xFFFF, Local1)
                                    Increment (Local1)
                                }

                                Multiply (Local0, Local1, Local1)
                                Divide (Local1, 0x03E8, , Local1)
                            }

                            Store (Local1, Index (BATS, 0x01))
                            Multiply (Local2, 0x0A, Index (BATS, 0x02))
                            Store (Local0, Index (BATS, 0x03))
                            Return (BATS)
                        }
                    }

                    Scope (\)
                    {
                        Name (PWRS, Ones)
                    }

                    Device (ACAD)
                    {
                        Name (_HID, "ACPI0003")
                        Name (_PCL, Package (0x01)
                        {
                            \_SB
                        })
                        Method (_PSR, 0, NotSerialized)
                        {
                            If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                            {
                                And (PHSD (0xD4, 0x80), 0x0400, Local1)
                            }
                            Else
                            {
                                Store (ACAT, Local1)
                            }

                            Store (Local1, PWRS)
                            If (Local1)
                            {
                                Return (One)
                            }
                            Else
                            {
                                Return (Zero)
                            }
                        }

                        Method (_STA, 0, NotSerialized)
                        {
                            Return (0x0F)
                        }
                    }
                }

                Device (SPIC)
                {
                    Name (_HID, EisaId ("SNY6001"))
                    Name (RSRC, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            _Y17)
                        IRQNoFlags (_Y18)
                            {}
                    })
                    Name (SSRC, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        IRQNoFlags ()
                            {}
                    })
                    Name (SIRT, Package (0x04)
                    {
                        0x06, 
                        0x09, 
                        0x0A, 
                        0x0B
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        CreateByteField (RSRC, \_SB.PCI0.LPCB.SPIC._Y17._MIN, IOM1)
                        CreateByteField (RSRC, 0x03, IOM2)
                        CreateWordField (RSRC, \_SB.PCI0.LPCB.SPIC._Y17._MIN, IO1I)
                        CreateWordField (RSRC, \_SB.PCI0.LPCB.SPIC._Y17._MAX, IO1A)
                        CreateWordField (RSRC, \_SB.PCI0.LPCB.SPIC._Y18._INT, IRQV)
                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            Store (PHSB (0xD4, 0x9C), IOM1)
                            Store (PHSB (0xD4, 0x9D), IOM2)
                        }
                        Else
                        {
                            Store (\_SB.PCI0.LPCB.EC0.SLOB, IOM1)
                            Store (\_SB.PCI0.LPCB.EC0.SHIB, IOM2)
                        }

                        Store (IO1I, IO1A)
                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            ShiftRight (PHSB (0xD4, 0x9B), 0x04, Local0)
                        }
                        Else
                        {
                            ShiftRight (\_SB.PCI0.LPCB.EC0.SIRQ, 0x04, Local0)
                        }

                        FindSetRightBit (Local0, Local1)
                        If (Local1)
                        {
                            Decrement (Local1)
                            Store (DerefOf (Index (SIRT, Local1)), Local0)
                            ShiftLeft (0x01, Local0, IRQV)
                        }

                        Return (RSRC)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x02, IOA1)
                        CreateByteField (Arg0, 0x03, IOA2)
                        CreateWordField (Arg0, 0x02, IOA0)
                        CreateWordField (Arg0, 0x09, IRQV)
                        FindSetRightBit (IRQV, Local0)
                        If (Local0)
                        {
                            Decrement (Local0)
                            Store (Match (SIRT, MEQ, Local0, MTR, 0x00, 0x00), Local1)
                            ShiftLeft (0x10, Local1, Local2)
                        }
                        Else
                        {
                            Store (0x00, Local2)
                        }

                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            PHSW (0xD5, 0x9B, Local2)
                        }
                        Else
                        {
                            Store (Local2, \_SB.PCI0.LPCB.EC0.SIRQ)
                        }

                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            PHSW (0xD5, 0x9D, IOA2)
                            PHSW (0xD5, 0x9C, IOA1)
                        }
                        Else
                        {
                            Store (IOA2, \_SB.PCI0.LPCB.EC0.SHIB)
                            Store (IOA1, \_SB.PCI0.LPCB.EC0.SLOB)
                        }

                        Sleep (0x01)
                        Store (Or (And (IOA0, 0xFFF0), 0x01), \_SB.PCI0.LPCB.GID2)
                        Store (And (\_SB.PCI0.LPCB.MISC, 0xCF), Local0)
                        Store (Or (Local0, 0x10), \_SB.PCI0.LPCB.MISC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x1080,             // Range Minimum
                                0x1080,             // Range Maximum
                                0x01,               // Alignment
                                0x20,               // Length
                                )
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x10A0,             // Range Minimum
                                0x10A0,             // Range Maximum
                                0x01,               // Alignment
                                0x20,               // Length
                                )
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x10C0,             // Range Minimum
                                0x10C0,             // Range Maximum
                                0x01,               // Alignment
                                0x20,               // Length
                                )
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x10E0,             // Range Minimum
                                0x10E0,             // Range Maximum
                                0x01,               // Alignment
                                0x20,               // Length
                                )
                        }
                        EndDependentFn ()
                        IRQNoFlags ()
                            {6,9,10,11}
                    })
                    Method (_DIS, 0, NotSerialized)
                    {
                        Store (_CRS (), SSRC)
                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            PHSW (0xD5, 0x9B, 0x00)
                            PHSW (0xD5, 0x9D, 0x00)
                            PHSW (0xD5, 0x9C, 0x00)
                        }
                        Else
                        {
                            Store (0x00, \_SB.PCI0.LPCB.EC0.SIRQ)
                            Store (0x00, \_SB.PCI0.LPCB.EC0.SHIB)
                            Store (0x00, \_SB.PCI0.LPCB.EC0.SLOB)
                        }

                        Sleep (0x01)
                        Store (0x00, \_SB.PCI0.LPCB.GID2)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            ShiftRight (PHSB (0xD4, 0x9B), 0x04, Local0)
                        }
                        Else
                        {
                            ShiftRight (\_SB.PCI0.LPCB.EC0.SIRQ, 0x04, Local0)
                        }

                        FindSetRightBit (Local0, Local1)
                        If (Local1)
                        {
                            Return (0x0F)
                        }
                        Else
                        {
                            Return (0x0D)
                        }
                    }
                }

                Device (SNC)
                {
                    Name (_HID, EisaId ("SNY5001"))
                    Method (GPID, 0, NotSerialized)
                    {
                        Return (PHSB (0xC0, 0x00))
                    }

                    Method (GBRT, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            Store (PHSD (0xD4, 0x96), Local0)
                        }
                        Else
                        {
                            Store (\_SB.PCI0.LPCB.EC0.BRIT, Local0)
                        }

                        Return (PHSB (0xCF, Local0))
                    }

                    Method (SBRT, 1, NotSerialized)
                    {
                        PHSB (0xC3, Arg0)
                        Return (Zero)
                    }

                    Method (GPBR, 0, NotSerialized)
                    {
                        Return (PHSB (0xC1, 0x00))
                    }

                    Method (SPBR, 1, NotSerialized)
                    {
                        PHSB (0xC2, Arg0)
                        Return (Zero)
                    }

                    Method (GCTR, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            Store (PHSD (0xD4, 0x97), Local0)
                        }
                        Else
                        {
                            Store (\_SB.PCI0.LPCB.EC0.CONT, Local0)
                        }

                        Return (PHSB (0xD0, Local0))
                    }

                    Method (SCTR, 1, NotSerialized)
                    {
                        Store (PHSB (0xCE, Arg0), Local0)
                        If (LEqual (\_SB.PCI0.LPCB.EC0.ECOK, 0x00))
                        {
                            PHSB (0xC6, Local0)
                        }
                        Else
                        {
                            Store (Local0, \_SB.PCI0.LPCB.EC0.CONT)
                        }

                        Return (Zero)
                    }

                    Method (GPCR, 0, NotSerialized)
                    {
                        Return (PHSB (0xC4, 0x00))
                    }

                    Method (SPCR, 1, NotSerialized)
                    {
                        PHSB (0xC5, Arg0)
                        Return (Zero)
                    }

                    Method (PWAK, 0, NotSerialized)
                    {
                        Acquire (PLOK, 0xFFFF)
                        Sleep (0x64)
                        Notify (\_PR.CPU0, 0x80)
                        Sleep (0x64)
                        Release (PLOK)
                        Return (Zero)
                    }

                    Method (PWRN, 0, NotSerialized)
                    {
                        Notify (\_SB.PWRB, 0x80)
                    }

                    Method (CSXB, 1, NotSerialized)
                    {
                        Acquire (MPHS, 0xFFFF)
                        Store (Arg0, SXBF)
                        PHS0 (0xCC)
                        Store (SXBF, Local0)
                        Release (MPHS)
                        Return (Local0)
                    }

                    Method (SODV, 1, NotSerialized)
                    {
                        If (LNotEqual (DSEN, 0x00))
                        {
                            Return (Ones)
                        }

                        Store (Arg0, AODV)
                        If (LNot (And (AODV, CADD)))
                        {
                            Store (0x01, AODV)
                        }

                        If (LNotEqual (CADD, PADD))
                        {
                            Store (CADD, PADD)
                            Notify (\_SB.PCI0, 0x00)
                            Notify (\_SB.PCI0.PEGP, 0x00)
                            Sleep (0x02EE)
                        }

                        Notify (GFX0, 0x80)
                        Notify (\_SB.PCI0.PEGP.NGFX, 0x80)
                        Return (Zero)
                    }

                    Method (GDDI, 0, NotSerialized)
                    {
                        Store (PHS (0xA5), Local0)
                        Store (And (Local0, 0x0F), CADD)
                        Return (Local0)
                    }

                    Method (GWDP, 0, NotSerialized)
                    {
                        Return (And (PHSB (0xD4, 0x74), 0x01))
                    }

                    Mutex (MIDB, 0x00)
                    Method (RBMF, 1, Serialized)
                    {
                        Acquire (MIDB, 0xFFFF)
                        And (Arg0, 0x00010000, Local0)
                        PHSD (0xDC, Local0)
                        Sleep (0x07D0)
                        Store (0x03000000, Local0)
                        Store (PHSD (0xDC, Local0), Local0)
                        Release (MIDB)
                        Return (Local0)
                    }

                    Method (RSBI, 1, Serialized)
                    {
                        Acquire (MIDB, 0xFFFF)
                        Or (And (Arg0, 0x0001FFFF), 0x01000000, Local0)
                        Store (PHSD (0xDC, Local0), Local0)
                        Sleep (0x07D0)
                        Or (And (Arg0, 0x0001FFFF), 0x03000000, Local0)
                        Store (PHSD (0xDC, Local0), Local0)
                        Release (MIDB)
                        Return (Local0)
                    }

                    Method (CBMF, 1, Serialized)
                    {
                        Acquire (MIDB, 0xFFFF)
                        Or (And (Arg0, 0x0001FFFF), 0x02000000, Local0)
                        Store (PHSD (0xDC, Local0), Local0)
                        Release (MIDB)
                        Return (Zero)
                    }

                    Name (BTIM, 0xFFFF)
                    Method (CDPW, 1, Serialized)
                    {
                        If (Arg0)
                        {
                            If (LNot (And (\GL03, 0x08)))
                            {
                                Store (One, \_SB.PCI0.LPCB.EC0.IRST)
                                Or (And (\_SB.PCI0.PATA.ICR4, 0x0C), 0x01, \_SB.PCI0.PATA.ICR4)
                                Sleep (0x0A)
                                Or (\GL03, 0x08, \GL03)
                                Sleep (0x01F4)
                                And (\_SB.PCI0.PATA.ICR4, 0x0C, \_SB.PCI0.PATA.ICR4)
                                Store (Zero, \_SB.PCI0.LPCB.EC0.IRST)
                                Store (BTIM, \_SB.PCI0.PATA.PRIT)
                            }
                        }
                        Else
                        {
                            If (And (\GL03, 0x08))
                            {
                                Store (\_SB.PCI0.PATA.PRIT, BTIM)
                                Store (0x8000, \_SB.PCI0.PATA.PRIT)
                                Store (One, \_SB.PCI0.LPCB.EC0.IRST)
                                Or (And (\_SB.PCI0.PATA.ICR4, 0x0C), 0x01, \_SB.PCI0.PATA.ICR4)
                                Sleep (0x0A)
                                And (\GL03, 0xF7, \GL03)
                                Sleep (0x01F4)
                            }
                        }
                    }

                    Method (GCDP, 0, NotSerialized)
                    {
                        Return (ShiftRight (And (\GL03, 0x08), 0x03))
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
                        IRQ (Edge, ActiveHigh, Exclusive, )
                            {1}
                    })
                }

                Device (PS2M)
                {
                    Name (_HID, EisaId ("SNY9001"))
                    Name (_CID, EisaId ("PNP0F13"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IRQ (Edge, ActiveHigh, Exclusive, )
                            {12}
                    })
                }
            }

            Device (PATA)
            {
                Name (_ADR, 0x001F0001)
                OperationRegion (PACS, PCI_Config, 0x40, 0xC0)
                Field (PACS, DWordAcc, NoLock, Preserve)
                {
                    PRIT,   16, 
                            Offset (0x04), 
                    PSIT,   4, 
                            Offset (0x08), 
                    SYNC,   4, 
                            Offset (0x0A), 
                    SDT0,   2, 
                        ,   2, 
                    SDT1,   2, 
                            Offset (0x14), 
                    ICR0,   4, 
                    ICR1,   4, 
                    ICR2,   4, 
                    ICR3,   4, 
                    ICR4,   4, 
                    ICR5,   4
                }

                Device (PRID)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Name (PBUF, Buffer (0x14)
                        {
                            /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                            /* 0008 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                            /* 0010 */    0x00, 0x00, 0x00, 0x00
                        })
                        CreateDWordField (PBUF, 0x00, PIO0)
                        CreateDWordField (PBUF, 0x04, DMA0)
                        CreateDWordField (PBUF, 0x08, PIO1)
                        CreateDWordField (PBUF, 0x0C, DMA1)
                        CreateDWordField (PBUF, 0x10, FLAG)
                        Store (GETP (PRIT), PIO0)
                        Store (GDMA (And (SYNC, 0x01), And (ICR3, 0x01), 
                            And (ICR0, 0x01), SDT0, And (ICR1, 0x01)), DMA0)
                        If (LEqual (DMA0, 0xFFFFFFFF))
                        {
                            Store (PIO0, DMA0)
                        }

                        If (And (PRIT, 0x4000))
                        {
                            If (LEqual (And (PRIT, 0x90), 0x80))
                            {
                                Store (0x0384, PIO1)
                            }
                            Else
                            {
                                Store (GETT (PSIT), PIO1)
                            }
                        }
                        Else
                        {
                            Store (0xFFFFFFFF, PIO1)
                        }

                        Store (GDMA (And (SYNC, 0x02), And (ICR3, 0x02), 
                            And (ICR0, 0x02), SDT1, And (ICR1, 0x02)), DMA1)
                        If (LEqual (DMA1, 0xFFFFFFFF))
                        {
                            Store (PIO1, DMA1)
                        }

                        Store (GETF (And (SYNC, 0x01), And (SYNC, 0x02), 
                            PRIT), FLAG)
                        If (And (LEqual (PIO0, 0xFFFFFFFF), LEqual (DMA0, 0xFFFFFFFF)))
                        {
                            Store (0x78, PIO0)
                            Store (0x14, DMA0)
                            Store (0x03, FLAG)
                        }

                        Return (PBUF)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        CreateDWordField (Arg0, 0x00, PIO0)
                        CreateDWordField (Arg0, 0x04, DMA0)
                        CreateDWordField (Arg0, 0x08, PIO1)
                        CreateDWordField (Arg0, 0x0C, DMA1)
                        CreateDWordField (Arg0, 0x10, FLAG)
                        If (LEqual (SizeOf (Arg1), 0x0200))
                        {
                            And (PRIT, 0x40F0, PRIT)
                            And (SYNC, 0x02, SYNC)
                            Store (0x00, SDT0)
                            And (ICR0, 0x02, ICR0)
                            And (ICR1, 0x02, ICR1)
                            And (ICR3, 0x02, ICR3)
                            And (ICR5, 0x02, ICR5)
                            CreateWordField (Arg1, 0x62, W490)
                            CreateWordField (Arg1, 0x6A, W530)
                            CreateWordField (Arg1, 0x7E, W630)
                            CreateWordField (Arg1, 0x80, W640)
                            CreateWordField (Arg1, 0xB0, W880)
                            CreateWordField (Arg1, 0xBA, W930)
                            Or (PRIT, 0x8004, PRIT)
                            If (LAnd (And (FLAG, 0x02), And (W490, 0x0800)))
                            {
                                Or (PRIT, 0x02, PRIT)
                            }

                            Or (PRIT, SETP (PIO0, W530, W640), PRIT)
                            If (And (FLAG, 0x01))
                            {
                                Or (SYNC, 0x01, SYNC)
                                Store (SDMA (DMA0), SDT0)
                                If (LLess (DMA0, 0x1E))
                                {
                                    Or (ICR3, 0x01, ICR3)
                                }

                                If (LLess (DMA0, 0x3C))
                                {
                                    Or (ICR0, 0x01, ICR0)
                                }

                                If (And (W930, 0x2000))
                                {
                                    Or (ICR1, 0x01, ICR1)
                                }
                            }
                        }

                        If (LEqual (SizeOf (Arg2), 0x0200))
                        {
                            And (PRIT, 0x3F0F, PRIT)
                            Store (0x00, PSIT)
                            And (SYNC, 0x01, SYNC)
                            Store (0x00, SDT1)
                            And (ICR0, 0x01, ICR0)
                            And (ICR1, 0x01, ICR1)
                            And (ICR3, 0x01, ICR3)
                            And (ICR5, 0x01, ICR5)
                            CreateWordField (Arg2, 0x62, W491)
                            CreateWordField (Arg2, 0x6A, W531)
                            CreateWordField (Arg2, 0x7E, W631)
                            CreateWordField (Arg2, 0x80, W641)
                            CreateWordField (Arg2, 0xB0, W881)
                            CreateWordField (Arg2, 0xBA, W931)
                            Or (PRIT, 0x8040, PRIT)
                            If (LAnd (And (FLAG, 0x08), And (W491, 0x0800)))
                            {
                                Or (PRIT, 0x20, PRIT)
                            }

                            If (And (FLAG, 0x10))
                            {
                                Or (PRIT, 0x4000, PRIT)
                                If (LGreater (PIO1, 0xF0))
                                {
                                    Or (PRIT, 0x80, PRIT)
                                }
                                Else
                                {
                                    Or (PRIT, 0x10, PRIT)
                                    Store (SETT (PIO1, W531, W641), PSIT)
                                }
                            }

                            If (And (FLAG, 0x04))
                            {
                                Or (SYNC, 0x02, SYNC)
                                Store (SDMA (DMA1), SDT1)
                                If (LLess (DMA1, 0x1E))
                                {
                                    Or (ICR3, 0x02, ICR3)
                                }

                                If (LLess (DMA1, 0x3C))
                                {
                                    Or (ICR0, 0x02, ICR0)
                                }

                                If (And (W931, 0x2000))
                                {
                                    Or (ICR1, 0x02, ICR1)
                                }
                            }
                        }
                    }

                    Device (P_D0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Name (PIB0, Buffer (0x0E)
                            {
                                /* 0000 */    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF, 0x03, 
                                /* 0008 */    0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                            })
                            CreateByteField (PIB0, 0x01, PMD0)
                            CreateByteField (PIB0, 0x08, DMD0)
                            If (And (PRIT, 0x02))
                            {
                                If (LEqual (And (PRIT, 0x09), 0x08))
                                {
                                    Store (0x08, PMD0)
                                }
                                Else
                                {
                                    Store (0x0A, PMD0)
                                    ShiftRight (And (PRIT, 0x0300), 0x08, Local0)
                                    ShiftRight (And (PRIT, 0x3000), 0x0C, Local1)
                                    Add (Local0, Local1, Local2)
                                    If (LEqual (0x03, Local2))
                                    {
                                        Store (0x0B, PMD0)
                                    }

                                    If (LEqual (0x05, Local2))
                                    {
                                        Store (0x0C, PMD0)
                                    }
                                }
                            }
                            Else
                            {
                                Store (0x01, PMD0)
                            }

                            If (And (SYNC, 0x01))
                            {
                                Store (Or (SDT0, 0x40), DMD0)
                                If (And (ICR1, 0x01))
                                {
                                    If (And (ICR0, 0x01))
                                    {
                                        Add (DMD0, 0x02, DMD0)
                                    }

                                    If (And (ICR3, 0x01))
                                    {
                                        Store (0x45, DMD0)
                                    }
                                }
                            }
                            Else
                            {
                                Or (Subtract (And (PMD0, 0x07), 0x02), 0x20, DMD0)
                            }

                            Return (PIB0)
                        }
                    }

                    Device (P_D1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Name (PIB1, Buffer (0x0E)
                            {
                                /* 0000 */    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF, 0x03, 
                                /* 0008 */    0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                            })
                            CreateByteField (PIB1, 0x01, PMD1)
                            CreateByteField (PIB1, 0x08, DMD1)
                            If (And (PRIT, 0x20))
                            {
                                If (LEqual (And (PRIT, 0x90), 0x80))
                                {
                                    Store (0x08, PMD1)
                                }
                                Else
                                {
                                    Add (And (PSIT, 0x03), ShiftRight (And (PSIT, 0x0C), 
                                        0x02), Local0)
                                    If (LEqual (0x05, Local0))
                                    {
                                        Store (0x0C, PMD1)
                                    }
                                    Else
                                    {
                                        If (LEqual (0x03, Local0))
                                        {
                                            Store (0x0B, PMD1)
                                        }
                                        Else
                                        {
                                            Store (0x0A, PMD1)
                                        }
                                    }
                                }
                            }
                            Else
                            {
                                Store (0x01, PMD1)
                            }

                            If (And (SYNC, 0x02))
                            {
                                Store (Or (SDT1, 0x40), DMD1)
                                If (And (ICR1, 0x02))
                                {
                                    If (And (ICR0, 0x02))
                                    {
                                        Add (DMD1, 0x02, DMD1)
                                    }

                                    If (And (ICR3, 0x02))
                                    {
                                        Store (0x45, DMD1)
                                    }
                                }
                            }
                            Else
                            {
                                Or (Subtract (And (PMD1, 0x07), 0x02), 0x20, DMD1)
                            }

                            Return (PIB1)
                        }
                    }
                }

                Name (FWSO, "FWSO")
            }

            Device (SATA)
            {
                Name (_ADR, 0x001F0002)
                OperationRegion (SACS, PCI_Config, 0x40, 0xC0)
                Field (SACS, DWordAcc, NoLock, Preserve)
                {
                    PRIT,   16, 
                    SECT,   16, 
                    PSIT,   4, 
                    SSIT,   4, 
                            Offset (0x08), 
                    SYNC,   4, 
                            Offset (0x0A), 
                    SDT0,   2, 
                        ,   2, 
                    SDT1,   2, 
                            Offset (0x0B), 
                    SDT2,   2, 
                        ,   2, 
                    SDT3,   2, 
                            Offset (0x14), 
                    ICR0,   4, 
                    ICR1,   4, 
                    ICR2,   4, 
                    ICR3,   4, 
                    ICR4,   4, 
                    ICR5,   4, 
                            Offset (0x50), 
                    MAPV,   2, 
                            Offset (0x52), 
                    PCSR,   8
                }
            }

            Device (SBUS)
            {
                Name (_ADR, 0x001F0003)
                OperationRegion (SMBP, PCI_Config, 0x40, 0xC0)
                Field (SMBP, DWordAcc, NoLock, Preserve)
                {
                        ,   2, 
                    I2CE,   1
                }

                OperationRegion (SMBI, SystemIO, 0x18E0, 0x10)
                Field (SMBI, ByteAcc, NoLock, Preserve)
                {
                    HSTS,   8, 
                            Offset (0x02), 
                    HCON,   8, 
                    HCOM,   8, 
                    TXSA,   8, 
                    DAT0,   8, 
                    DAT1,   8, 
                    HBDR,   8, 
                    PECR,   8, 
                    RXSA,   8, 
                    SDAT,   16
                }

                Method (SSXB, 2, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SRXB, 1, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0xFFFF)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (0x44, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (DAT0)
                    }

                    Return (0xFFFF)
                }

                Method (SWRB, 3, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (Arg2, DAT0)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SRDB, 2, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0xFFFF)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (Arg1, HCOM)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (DAT0)
                    }

                    Return (0xFFFF)
                }

                Method (SBLW, 4, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (Arg3, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (SizeOf (Arg2), DAT0)
                    Store (0x00, Local1)
                    Store (DerefOf (Index (Arg2, 0x00)), HBDR)
                    Store (0x54, HCON)
                    While (LGreater (SizeOf (Arg2), Local1))
                    {
                        Store (0x0FA0, Local0)
                        While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                        }

                        If (LNot (Local0))
                        {
                            KILL ()
                            Return (0x00)
                        }

                        Store (0x80, HSTS)
                        Increment (Local1)
                        If (LGreater (SizeOf (Arg2), Local1))
                        {
                            Store (DerefOf (Index (Arg2, Local1)), HBDR)
                        }
                    }

                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SBLR, 3, Serialized)
                {
                    Name (TBUF, Buffer (0x0100) {})
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (Arg2, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (Arg1, HCOM)
                    Store (0x54, HCON)
                    Store (0x0FA0, Local0)
                    While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                    {
                        Decrement (Local0)
                        Stall (0x32)
                    }

                    If (LNot (Local0))
                    {
                        KILL ()
                        Return (0x00)
                    }

                    Store (DAT0, Index (TBUF, 0x00))
                    Store (0x80, HSTS)
                    Store (0x01, Local1)
                    While (LLess (Local1, DerefOf (Index (TBUF, 0x00))))
                    {
                        Store (0x0FA0, Local0)
                        While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                        }

                        If (LNot (Local0))
                        {
                            KILL ()
                            Return (0x00)
                        }

                        Store (HBDR, Index (TBUF, Local1))
                        Store (0x80, HSTS)
                        Increment (Local1)
                    }

                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (TBUF)
                    }

                    Return (0x00)
                }

                Method (STRT, 0, Serialized)
                {
                    Store (0xC8, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x40))
                        {
                            Decrement (Local0)
                            Sleep (0x01)
                            If (LEqual (Local0, 0x00))
                            {
                                Return (0x01)
                            }
                        }
                        Else
                        {
                            Store (0x00, Local0)
                        }
                    }

                    Store (0x0FA0, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x01))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                            If (LEqual (Local0, 0x00))
                            {
                                KILL ()
                            }
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }

                    Return (0x01)
                }

                Method (COMP, 0, Serialized)
                {
                    Store (0x0FA0, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x02))
                        {
                            Return (0x01)
                        }
                        Else
                        {
                            Decrement (Local0)
                            Stall (0x32)
                            If (LEqual (Local0, 0x00))
                            {
                                KILL ()
                            }
                        }
                    }

                    Return (0x00)
                }

                Method (KILL, 0, Serialized)
                {
                    Or (HCON, 0x02, HCON)
                    Or (HSTS, 0xFF, HSTS)
                }
            }
        }
    }
}

```Im run-out of ideas... maybe some one now more and can help ?
Thanks 

She system i using is: ubuntu 10.10 i386 on Sony Vaio VGN-S4M/s

[LIST]
[*]Intel Pentium-M Centrino 730 Processor 1.6GHz
[*]2 GB RAM
[*]60GB Hard Drive
[*]NVIDIA GeForce Go 6200 128MB graphics
[/LIST]

---

### Post by majster on 2010-12-05
bump ?

---

### Post by majster on 2010-12-09
any one?

---

### Post by majster on 2010-12-25
?

---

