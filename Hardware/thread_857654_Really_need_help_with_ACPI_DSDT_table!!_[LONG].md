---
title: "Really need help with ACPI DSDT table!! [LONG]"
date: 2008-07-12
forum: Hardware
---

### Post by NightWalker86 on 2008-07-12
Let me start off first by saying that I’m sorry for posting this here, but I really don’t know where else to turn! I’ve tried searching for MONTHS and I’ve done as much as I can by myself, but unfortunately, my very limited knowledge of programming language has stopped me dead in my tracks!

I am trying to rewrite the trips points in my ACPI DSDT table to make the fans idle at about 50% power under Windows Vista. I have extracted my DSDT table and since this is the same file that a lot of you guys need to edit/modify for Linux I was really hoping someone could help me out!

The problem is I can’t figure out where the fans are located in the DSDT table. I was able to locate the thermal zone (Scope (\_TZ) and so far I found what looks to be the critical (TCRT, 0x6E) and passive (TPSV, 0x6E) cooling policy, but I do not see any information relating to active cooling.

Now from what I’ve read so far, and please feel free to correct me if I’m wrong, this means that the active cooling policy/trip points are controlled by the embedded controller. The embedded controller is defined as “PNP0C09” or Device (EC0).

That is about as far as I have gotten. I can’t seem to find the fans (there are four) or even the active cooling policy ANYWHERE! I have read the entire DSDT table numerous times and searched hundreds if not thousands of different web pages for help and can’t seem to find any.

I sort of know what I’m looking for, but I don’t know how to actually identify the trip points or the fans themselves. I’ve probably looked at them a 100 times already without even knowing it because of the way they were named/encoded. 

If anyone can point out where the active cooling policy/trip points are or where the fans are located it would be a HUGE help! I’ve included a copy of my entire DSDT table in this post for anyone willing to give it a look. 

I am new when it comes to programming and different programming languages but I am doing my best to learn everything I can! I have learned a good deal about ACPI in general so I’m not a complete idiot, but the specifics are still over my head.

Also, I apologize again for posting this in a Linux forum, but you guys seem to have a lot more experience with writing/modifying DSDT tables and I could really use a hand! Thanks! 

Here’s my DSDT table….

/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20061109
 *
 * Disassembly of dsdt, Fri Jul 04 05:21:25 2008
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x000073CB (29643)
 *     Revision         0x01
 *     OEM ID           "A0704"
 *     OEM Table ID     "A0704000"
 *     OEM Revision     0x00000000 (0)
 *     Creator ID       "INTL"
 *     Creator Revision 0x20060113 (537264403)
 */
DefinitionBlock ("dsdt.aml", "DSDT", 1, "A0704", "A0704000", 0x00000000)
{
    Scope (\_PR)
    {
        Processor (CPU1, 0x01, 0x00000810, 0x06)
        {
            OperationRegion (STBL, SystemMemory, 0xB7FBE0B0, 0x0229)
            Name (NCPU, 0x02)
            Name (TYPE, 0x80000000)
            Name (HNDL, 0x80000000)
            Name (CFGD, 0xB7FB0509)
            Name (TBLD, 0x80)
            Method (_PDC, 1, NotSerialized)
            {
                CreateDWordField (Arg0, 0x00, REVS)
                CreateDWordField (Arg0, 0x04, SIZE)
                Store (SizeOf (Arg0), Local0)
                Store (Subtract (Local0, 0x08), Local1)
                CreateField (Arg0, 0x40, Multiply (Local1, 0x08), TEMP)
                Name (STS0, Buffer (0x04)
                {
                    0x00, 0x00, 0x00, 0x00
                })
                Concatenate (STS0, TEMP, Local2)
                _OSC (Buffer (0x10)
                    {
                        /* 0000 */    0x16, 0xA6, 0x77, 0x40, 0x0C, 0x29, 0xBE, 0x47, 
                        /* 0008 */    0x9E, 0xBD, 0xD8, 0x70, 0x58, 0x71, 0x39, 0x53
                    }, REVS, SIZE, Local2)
            }

            Method (_OSC, 4, NotSerialized)
            {
                CreateDWordField (Arg3, 0x00, STS0)
                CreateDWordField (Arg3, 0x04, CAP0)
                CreateDWordField (Arg0, 0x00, IID0)
                CreateDWordField (Arg0, 0x04, IID1)
                CreateDWordField (Arg0, 0x08, IID2)
                CreateDWordField (Arg0, 0x0C, IID3)
                Name (UID0, Buffer (0x10)
                {
                    /* 0000 */    0x16, 0xA6, 0x77, 0x40, 0x0C, 0x29, 0xBE, 0x47, 
                    /* 0008 */    0x9E, 0xBD, 0xD8, 0x70, 0x58, 0x71, 0x39, 0x53
                })
                CreateDWordField (UID0, 0x00, EID0)
                CreateDWordField (UID0, 0x04, EID1)
                CreateDWordField (UID0, 0x08, EID2)
                CreateDWordField (UID0, 0x0C, EID3)
                If (LNot (LAnd (LAnd (LEqual (IID0, EID0), LEqual (IID1, EID1)), 
                    LAnd (LEqual (IID2, EID2), LEqual (IID3, EID3)))))
                {
                    Store (0x06, STS0)
                    Return (Arg3)
                }

                If (LNotEqual (Arg1, 0x01))
                {
                    Store (0x0A, STS0)
                    Return (Arg3)
                }

                Or (And (TYPE, 0x7FFFFFFF), CAP0, TYPE)
                If (And (CFGD, 0x01))
                {
                    If (LAnd (LAnd (And (CFGD, 0x01000000), LEqual (And (TYPE, 
                        0x09), 0x09)), LNot (And (TBLD, 0x01))))
                    {
                        Or (TBLD, 0x01, TBLD)
                        Load (STBL, HNDL)
                    }
                }

                If (And (CFGD, 0xF0))
                {
                    If (LAnd (LAnd (And (CFGD, 0x01000000), And (TYPE, 0x18
                        )), LNot (And (TBLD, 0x02))))
                    {
                        Or (TBLD, 0x02, TBLD)
                    }
                }

                Return (Arg3)
            }
        }
    }

    Scope (\_PR)
    {
        Processor (CPU2, 0x02, 0x00000810, 0x06)
        {
            OperationRegion (STBL, SystemMemory, 0xB7FBE2E0, 0x0143)
            Name (NCPU, 0x02)
            Name (TYPE, 0x80000000)
            Name (HNDL, 0x80000000)
            Name (CFGD, 0xB7FB0709)
            Name (TBLD, 0x80)
            Method (_PDC, 1, NotSerialized)
            {
                CreateDWordField (Arg0, 0x00, REVS)
                CreateDWordField (Arg0, 0x04, SIZE)
                Store (SizeOf (Arg0), Local0)
                Store (Subtract (Local0, 0x08), Local1)
                CreateField (Arg0, 0x40, Multiply (Local1, 0x08), TEMP)
                Name (STS1, Buffer (0x04)
                {
                    0x00, 0x00, 0x00, 0x00
                })
                Concatenate (STS1, TEMP, Local2)
                _OSC (Buffer (0x10)
                    {
                        /* 0000 */    0x16, 0xA6, 0x77, 0x40, 0x0C, 0x29, 0xBE, 0x47, 
                        /* 0008 */    0x9E, 0xBD, 0xD8, 0x70, 0x58, 0x71, 0x39, 0x53
                    }, REVS, SIZE, Local2)
            }

            Method (_OSC, 4, NotSerialized)
            {
                CreateDWordField (Arg3, 0x00, STS1)
                CreateDWordField (Arg3, 0x04, CAP1)
                CreateDWordField (Arg0, 0x00, IID0)
                CreateDWordField (Arg0, 0x04, IID1)
                CreateDWordField (Arg0, 0x08, IID2)
                CreateDWordField (Arg0, 0x0C, IID3)
                Name (UID0, Buffer (0x10)
                {
                    /* 0000 */    0x16, 0xA6, 0x77, 0x40, 0x0C, 0x29, 0xBE, 0x47, 
                    /* 0008 */    0x9E, 0xBD, 0xD8, 0x70, 0x58, 0x71, 0x39, 0x53
                })
                CreateDWordField (UID0, 0x00, EID0)
                CreateDWordField (UID0, 0x04, EID1)
                CreateDWordField (UID0, 0x08, EID2)
                CreateDWordField (UID0, 0x0C, EID3)
                If (LNot (LAnd (LAnd (LEqual (IID0, EID0), LEqual (IID1, EID1)), 
                    LAnd (LEqual (IID2, EID2), LEqual (IID3, EID3)))))
                {
                    Store (0x06, STS1)
                    Return (Arg3)
                }

                If (LNotEqual (Arg1, 0x01))
                {
                    Store (0x0A, STS1)
                    Return (Arg3)
                }

                Or (And (TYPE, 0x7FFFFFFF), CAP1, TYPE)
                If (And (CFGD, 0x01))
                {
                    If (LAnd (LAnd (And (CFGD, 0x01000000), LEqual (And (TYPE, 
                        0x09), 0x09)), LNot (And (TBLD, 0x01))))
                    {
                        Or (TBLD, 0x01, TBLD)
                        Load (STBL, HNDL)
                    }
                }

                If (And (CFGD, 0xF0))
                {
                    If (LAnd (LAnd (And (CFGD, 0x01000000), And (TYPE, 0x18
                        )), LNot (And (TBLD, 0x02))))
                    {
                        Or (TBLD, 0x02, TBLD)
                    }
                }

                Return (Arg3)
            }
        }
    }

    Scope (\_PR)
    {
        Processor (CPU3, 0x03, 0x00000810, 0x06)
        {
            OperationRegion (STBL, SystemMemory, 0xFFFF0000, 0xFFFF)
            Name (NCPU, 0x80)
            Name (TYPE, 0x80000000)
            Name (HNDL, 0x80000000)
            Name (CFGD, 0x80000000)
            Name (TBLD, 0x80)
            Method (_PDC, 1, NotSerialized)
            {
                CreateDWordField (Arg0, 0x00, REVS)
                CreateDWordField (Arg0, 0x04, SIZE)
                Store (SizeOf (Arg0), Local0)
                Store (Subtract (Local0, 0x08), Local1)
                CreateField (Arg0, 0x40, Multiply (Local1, 0x08), TEMP)
                Name (STS2, Buffer (0x04)
                {
                    0x00, 0x00, 0x00, 0x00
                })
                Concatenate (STS2, TEMP, Local2)
                _OSC (Buffer (0x10)
                    {
                        /* 0000 */    0x16, 0xA6, 0x77, 0x40, 0x0C, 0x29, 0xBE, 0x47, 
                        /* 0008 */    0x9E, 0xBD, 0xD8, 0x70, 0x58, 0x71, 0x39, 0x53
                    }, REVS, SIZE, Local2)
            }

            Method (_OSC, 4, NotSerialized)
            {
                CreateDWordField (Arg3, 0x00, STS2)
                CreateDWordField (Arg3, 0x04, CAP2)
                CreateDWordField (Arg0, 0x00, IID0)
                CreateDWordField (Arg0, 0x04, IID1)
                CreateDWordField (Arg0, 0x08, IID2)
                CreateDWordField (Arg0, 0x0C, IID3)
                Name (UID0, Buffer (0x10)
                {
                    /* 0000 */    0x16, 0xA6, 0x77, 0x40, 0x0C, 0x29, 0xBE, 0x47, 
                    /* 0008 */    0x9E, 0xBD, 0xD8, 0x70, 0x58, 0x71, 0x39, 0x53
                })
                CreateDWordField (UID0, 0x00, EID0)
                CreateDWordField (UID0, 0x04, EID1)
                CreateDWordField (UID0, 0x08, EID2)
                CreateDWordField (UID0, 0x0C, EID3)
                If (LNot (LAnd (LAnd (LEqual (IID0, EID0), LEqual (IID1, EID1)), 
                    LAnd (LEqual (IID2, EID2), LEqual (IID3, EID3)))))
                {
                    Store (0x06, STS2)
                    Return (Arg3)
                }

                If (LNotEqual (Arg1, 0x01))
                {
                    Store (0x0A, STS2)
                    Return (Arg3)
                }

                Or (And (TYPE, 0x7FFFFFFF), CAP2, TYPE)
                If (And (CFGD, 0x01))
                {
                    If (LAnd (LAnd (And (CFGD, 0x01000000), LEqual (And (TYPE, 
                        0x09), 0x09)), LNot (And (TBLD, 0x01))))
                    {
                        Or (TBLD, 0x01, TBLD)
                        Load (STBL, HNDL)
                    }
                }

                If (And (CFGD, 0xF0))
                {
                    If (LAnd (LAnd (And (CFGD, 0x01000000), And (TYPE, 0x18
                        )), LNot (And (TBLD, 0x02))))
                    {
                        Or (TBLD, 0x02, TBLD)
                    }
                }

                Return (Arg3)
            }
        }
    }

    Scope (\_PR)
    {
        Processor (CPU4, 0x04, 0x00000810, 0x06)
        {
            OperationRegion (STBL, SystemMemory, 0xFFFF0000, 0xFFFF)
            Name (NCPU, 0x80)
            Name (TYPE, 0x80000000)
            Name (HNDL, 0x80000000)
            Name (CFGD, 0x80000000)
            Name (TBLD, 0x80)
            Method (_PDC, 1, NotSerialized)
            {
                CreateDWordField (Arg0, 0x00, REVS)
                CreateDWordField (Arg0, 0x04, SIZE)
                Store (SizeOf (Arg0), Local0)
                Store (Subtract (Local0, 0x08), Local1)
                CreateField (Arg0, 0x40, Multiply (Local1, 0x08), TEMP)
                Name (STS3, Buffer (0x04)
                {
                    0x00, 0x00, 0x00, 0x00
                })
                Concatenate (STS3, TEMP, Local2)
                _OSC (Buffer (0x10)
                    {
                        /* 0000 */    0x16, 0xA6, 0x77, 0x40, 0x0C, 0x29, 0xBE, 0x47, 
                        /* 0008 */    0x9E, 0xBD, 0xD8, 0x70, 0x58, 0x71, 0x39, 0x53
                    }, REVS, SIZE, Local2)
            }

            Method (_OSC, 4, NotSerialized)
            {
                CreateDWordField (Arg3, 0x00, STS3)
                CreateDWordField (Arg3, 0x04, CAP3)
                CreateDWordField (Arg0, 0x00, IID0)
                CreateDWordField (Arg0, 0x04, IID1)
                CreateDWordField (Arg0, 0x08, IID2)
                CreateDWordField (Arg0, 0x0C, IID3)
                Name (UID0, Buffer (0x10)
                {
                    /* 0000 */    0x16, 0xA6, 0x77, 0x40, 0x0C, 0x29, 0xBE, 0x47, 
                    /* 0008 */    0x9E, 0xBD, 0xD8, 0x70, 0x58, 0x71, 0x39, 0x53
                })
                CreateDWordField (UID0, 0x00, EID0)
                CreateDWordField (UID0, 0x04, EID1)
                CreateDWordField (UID0, 0x08, EID2)
                CreateDWordField (UID0, 0x0C, EID3)
                If (LNot (LAnd (LAnd (LEqual (IID0, EID0), LEqual (IID1, EID1)), 
                    LAnd (LEqual (IID2, EID2), LEqual (IID3, EID3)))))
                {
                    Store (0x06, STS3)
                    Return (Arg3)
                }

                If (LNotEqual (Arg1, 0x01))
                {
                    Store (0x0A, STS3)
                    Return (Arg3)
                }

                Or (And (TYPE, 0x7FFFFFFF), CAP3, TYPE)
                If (And (CFGD, 0x01))
                {
                    If (LAnd (LAnd (And (CFGD, 0x01000000), LEqual (And (TYPE, 
                        0x09), 0x09)), LNot (And (TBLD, 0x01))))
                    {
                        Or (TBLD, 0x01, TBLD)
                        Load (STBL, HNDL)
                    }
                }

                If (And (CFGD, 0xF0))
                {
                    If (LAnd (LAnd (And (CFGD, 0x01000000), And (TYPE, 0x18
                        )), LNot (And (TBLD, 0x02))))
                    {
                        Or (TBLD, 0x02, TBLD)
                    }
                }

                Return (Arg3)
            }
        }
    }

    Name (DP80, 0x80)
    Name (DP90, 0x90)
    Name (HPIO, 0x2E)
    Name (PMBS, 0x0800)
    Name (PMLN, 0x80)
    Name (GPBS, 0x0480)
    Name (GPLN, 0x40)
    Name (SMBS, 0x00)
    Name (SMBL, 0x00)
    Name (PM28, 0x0828)
    Name (PM30, 0x0830)
    Name (SUSW, 0xFF)
    Name (HTBA, 0xFED1F404)
    Name (APIC, 0x01)
    Name (PCIB, 0xE0000000)
    Name (PCIL, 0x10000000)
    Name (SMIT, 0xB2)
    Name (CMRQ, 0x80)
    Name (CMER, 0x81)
    Name (CMOR, 0x83)
    OperationRegion (BIOS, SystemMemory, 0xB7FBE064, 0xFF)
    Field (BIOS, ByteAcc, NoLock, Preserve)
    {
        SS1,    1, 
        SS2,    1, 
        SS3,    1, 
        SS4,    1, 
                Offset (0x01), 
        IOST,   16, 
        TOPM,   32, 
        ROMS,   32, 
        MG1B,   32, 
        MG1L,   32, 
        MG2B,   32, 
        MG2L,   32, 
                Offset (0x1C), 
        DMAX,   8, 
        HPTA,   32, 
        CPB0,   32, 
        CPB1,   32, 
        CPB2,   32, 
        CPB3,   32, 
        ASSB,   8, 
        AOTB,   8, 
        AAXB,   32, 
        SMIF,   8, 
        DTSE,   8, 
        DTS1,   8, 
        DTS2,   8, 
        MPEN,   8, 
        TPMF,   8
    }

    Method (RRIO, 4, NotSerialized)
    {
        Store ("RRIO", Debug)
    }

    Method (RDMA, 3, NotSerialized)
    {
        Store ("rDMA", Debug)
    }

    Name (PICM, 0x00)
    Method (_PIC, 1, NotSerialized)
    {
        If (Arg0)
        {
            Store (0xAA, DBG8)
        }
        Else
        {
            Store (0xAC, DBG8)
        }

        Store (Arg0, PICM)
    }

    Name (OSVR, Ones)
    Method (OSFL, 0, NotSerialized)
    {
        If (LNotEqual (OSVR, Ones))
        {
            Return (OSVR)
        }

        If (LEqual (PICM, 0x00))
        {
            Store (0xAC, DBG8)
        }

        Store (0x01, OSVR)
        If (CondRefOf (\_OSI, Local1))
        {
            If (\_OSI ("Windows 2000"))
            {
                Store (0x04, OSVR)
            }

            If (\_OSI ("Windows 2001"))
            {
                Store (0x00, OSVR)
            }

            If (\_OSI ("Windows 2001 SP1"))
            {
                Store (0x00, OSVR)
            }

            If (\_OSI ("Windows 2001 SP2"))
            {
                Store (0x00, OSVR)
            }

            If (\_OSI ("Windows 2001.1"))
            {
                Store (0x00, OSVR)
            }

            If (\_OSI ("Windows 2001.1 SP1"))
            {
                Store (0x00, OSVR)
            }

            If (\_OSI ("Windows 2006"))
            {
                Store (0x00, OSVR)
            }
        }
        Else
        {
            If (MCTH (\_OS, "Microsoft Windows NT"))
            {
                Store (0x04, OSVR)
            }
            Else
            {
                If (MCTH (\_OS, "Microsoft WindowsME: Millennium Edition"))
                {
                    Store (0x02, OSVR)
                }

                If (MCTH (\_OS, "Linux"))
                {
                    Store (0x03, OSVR)
                }
            }
        }

        Return (OSVR)
    }

    Method (MCTH, 2, NotSerialized)
    {
        If (LLess (SizeOf (Arg0), SizeOf (Arg1)))
        {
            Return (Zero)
        }

        Add (SizeOf (Arg0), 0x01, Local0)
        Name (BUF0, Buffer (Local0) {})
        Name (BUF1, Buffer (Local0) {})
        Store (Arg0, BUF0)
        Store (Arg1, BUF1)
        While (Local0)
        {
            Decrement (Local0)
            If (LNotEqual (DerefOf (Index (BUF0, Local0)), DerefOf (Index (
                BUF1, Local0))))
            {
                Return (Zero)
            }
        }

        Return (One)
    }

    Name (PRWP, Package (0x02)
    {
        Zero, 
        Zero
    })
    Method (GPRW, 2, NotSerialized)
    {
        Store (Arg0, Index (PRWP, 0x00))
        Store (ShiftLeft (SS1, 0x01), Local0)
        Or (Local0, ShiftLeft (SS2, 0x02), Local0)
        Or (Local0, ShiftLeft (SS3, 0x03), Local0)
        Or (Local0, ShiftLeft (SS4, 0x04), Local0)
        If (And (ShiftLeft (0x01, Arg1), Local0))
        {
            Store (Arg1, Index (PRWP, 0x01))
        }
        Else
        {
            ShiftRight (Local0, 0x01, Local0)
            If (LOr (LEqual (OSFL (), 0x01), LEqual (OSFL (), 0x02)))
            {
                FindSetLeftBit (Local0, Index (PRWP, 0x01))
            }
            Else
            {
                FindSetRightBit (Local0, Index (PRWP, 0x01))
            }
        }

        Return (PRWP)
    }

    Name (WAKP, Package (0x02)
    {
        Zero, 
        Zero
    })
    OperationRegion (DEB0, SystemIO, DP80, 0x01)
    Field (DEB0, ByteAcc, NoLock, Preserve)
    {
        DBG8,   8
    }

    OperationRegion (DEB1, SystemIO, DP90, 0x02)
    Field (DEB1, WordAcc, NoLock, Preserve)
    {
        DBG9,   16
    }

    Scope (\_SB)
    {
        Name (PR00, Package (0x11)
        {
            Package (0x04)
            {
                0x0001FFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0x0001FFFF, 
                0x01, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0x0001FFFF, 
                0x02, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0x0001FFFF, 
                0x03, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0x001FFFFF, 
                0x00, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0x001FFFFF, 
                0x01, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0x001EFFFF, 
                0x00, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0x001EFFFF, 
                0x01, 
                LNKE, 
                0x00
            }, 

            Package (0x04)
            {
                0x001BFFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0x001CFFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0x001CFFFF, 
                0x01, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0x001CFFFF, 
                0x02, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0x001CFFFF, 
                0x03, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0x001DFFFF, 
                0x00, 
                LNKH, 
                0x00
            }, 

            Package (0x04)
            {
                0x001DFFFF, 
                0x01, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0x001DFFFF, 
                0x02, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0x001DFFFF, 
                0x03, 
                LNKA, 
                0x00
            }
        })
        Name (AR00, Package (0x11)
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
                0x001FFFFF, 
                0x00, 
                0x00, 
                0x12
            }, 

            Package (0x04)
            {
                0x001FFFFF, 
                0x01, 
                0x00, 
                0x13
            }, 

            Package (0x04)
            {
                0x001EFFFF, 
                0x00, 
                0x00, 
                0x11
            }, 

            Package (0x04)
            {
                0x001EFFFF, 
                0x01, 
                0x00, 
                0x14
            }, 

            Package (0x04)
            {
                0x001BFFFF, 
                0x00, 
                0x00, 
                0x10
            }, 

            Package (0x04)
            {
                0x001CFFFF, 
                0x00, 
                0x00, 
                0x10
            }, 

            Package (0x04)
            {
                0x001CFFFF, 
                0x01, 
                0x00, 
                0x11
            }, 

            Package (0x04)
            {
                0x001CFFFF, 
                0x02, 
                0x00, 
                0x12
            }, 

            Package (0x04)
            {
                0x001CFFFF, 
                0x03, 
                0x00, 
                0x13
            }, 

            Package (0x04)
            {
                0x001DFFFF, 
                0x00, 
                0x00, 
                0x17
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
                0x12
            }, 

            Package (0x04)
            {
                0x001DFFFF, 
                0x03, 
                0x00, 
                0x10
            }
        })
        Name (PR01, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                LNKD, 
                0x00
            }
        })
        Name (AR01, Package (0x04)
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
        Name (PR04, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                LNKD, 
                0x00
            }
        })
        Name (AR04, Package (0x04)
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
        Name (PR05, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                LNKA, 
                0x00
            }
        })
        Name (AR05, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                0x00, 
                0x11
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                0x00, 
                0x12
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                0x00, 
                0x13
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                0x00, 
                0x10
            }
        })
        Name (PR06, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                LNKB, 
                0x00
            }
        })
        Name (AR06, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                0x00, 
                0x12
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                0x00, 
                0x13
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                0x00, 
                0x10
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                0x00, 
                0x11
            }
        })
        Name (PR07, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                LNKC, 
                0x00
            }
        })
        Name (AR07, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                0x00, 
                0x13
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                0x00, 
                0x10
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                0x00, 
                0x11
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                0x00, 
                0x12
            }
        })
        Name (PR08, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                LNKD, 
                0x00
            }
        })
        Name (AR08, Package (0x04)
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
        Name (PR09, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                LNKA, 
                0x00
            }
        })
        Name (AR09, Package (0x04)
        {
            Package (0x04)
            {
                0xFFFF, 
                0x00, 
                0x00, 
                0x11
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x01, 
                0x00, 
                0x12
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x02, 
                0x00, 
                0x13
            }, 

            Package (0x04)
            {
                0xFFFF, 
                0x03, 
                0x00, 
                0x10
            }
        })
        Name (PR03, Package (0x02)
        {
            Package (0x04)
            {
                0x0001FFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0x0001FFFF, 
                0x01, 
                LNKB, 
                0x00
            }
        })
        Name (AR03, Package (0x02)
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
            }
        })
        Name (PRSA, ResourceTemplate ()
        {
            IRQ (Level, ActiveLow, Shared, )
                {3,4,5,6,7,10,11,12,14,15}
        })
        Alias (PRSA, PRSB)
        Alias (PRSA, PRSC)
        Alias (PRSA, PRSD)
        Alias (PRSA, PRSE)
        Alias (PRSA, PRSF)
        Alias (PRSA, PRSG)
        Alias (PRSA, PRSH)
        Device (PCI0)
        {
            Name (_HID, EisaId ("PNP0A08"))
            Name (_CID, 0x030AD041)
            Name (_ADR, 0x00)
            Method (^BN00, 0, NotSerialized)
            {
                Return (0x00)
            }

            Method (_BBN, 0, NotSerialized)
            {
                Return (BN00 ())
            }

            Name (_UID, 0x00)
            Method (_PRT, 0, NotSerialized)
            {
                If (PICM)
                {
                    Return (AR00)
                }

                Return (PR00)
            }

            Method (_S3D, 0, NotSerialized)
            {
                If (LOr (LEqual (OSFL (), 0x01), LEqual (OSFL (), 0x02)))
                {
                    Return (0x02)
                }
                Else
                {
                    Return (0x03)
                }
            }

            Device (MCH)
            {
                Name (_HID, EisaId ("PNP0C01"))
                Name (_UID, 0x0A)
                Name (_CRS, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0xFED13000,         // Address Base
                        0x00007000,         // Address Length
                        )
                })
            }

            Method (NPTS, 1, NotSerialized)
            {
            }

            Method (NWAK, 1, NotSerialized)
            {
            }

            Device (P0P1)
            {
                Name (_ADR, 0x00010000)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x09, 0x04))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR01)
                    }

                    Return (PR01)
                }

                Device (VGA)
                {
                    Name (_ADR, 0x00)
                    Name (VGAB, Buffer (0x02) {})
                    CreateWordField (VGAB, 0x00, DISD)
                    CreateByteField (VGAB, 0x00, NXTD)
                    CreateByteField (VGAB, 0x01, AVLD)
                    Name (LCDM, 0x01)
                    Name (CRTM, 0x02)
                    Name (TVOM, 0x04)
                    Name (DONE, 0x00)
                    Name (DOSF, 0x01)
                    Method (_INI, 0, NotSerialized)
                    {
                        Store (GETD (), DISD)
                        Store (One, DONE)
                    }

                    Method (_DOS, 1, NotSerialized)
                    {
                        Store (Arg0, DOSF)
                    }

                    Method (_DOD, 0, NotSerialized)
                    {
                        Return (Package (0x03)
                        {
                            0x00010100, 
                            0x00010110, 
                            0x0200
                        })
                    }

                    Method (CDCS, 1, NotSerialized)
                    {
                        Store (0x0D, Local0)
                        If (And (NXTD, Arg0))
                        {
                            Or (Local0, 0x02, Local0)
                        }

                        If (And (AVLD, Arg0))
                        {
                            Or (Local0, 0x10, Local0)
                        }

                        Return (Local0)
                    }

                    Method (CDGS, 1, NotSerialized)
                    {
                        If (And (NXTD, Arg0))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Device (CRTD)
                    {
                        Name (_ADR, 0x0100)
                        Method (_DCS, 0, NotSerialized)
                        {
                            Return (CDCS (CRTM))
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            Return (CDGS (CRTM))
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                            If (And (Arg0, 0x40000000))
                            {
                                If (And (Arg0, 0x80000000))
                                {
                                    Store (One, DONE)
                                }
                            }
                        }
                    }

                    Device (TVOD)
                    {
                        Name (_ADR, 0x0200)
                        Method (_DCS, 0, NotSerialized)
                        {
                            Return (CDCS (TVOM))
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            Return (CDGS (TVOM))
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                            If (And (Arg0, 0x40000000))
                            {


                                If (And (Arg0, 0x80000000))
                                {
                                    Store (One, DONE)
                                }
                            }
                        }
                    }

                    Device (LCDD)
                    {
                        Name (_ADR, 0x0110)
                        Method (_DCS, 0, NotSerialized)
                        {
                            Return (CDCS (LCDM))
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            Return (CDGS (LCDM))
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                            If (And (Arg0, 0x40000000))
                            {
                                If (And (Arg0, 0x80000000))
                                {
                                    Store (One, DONE)
                                }
                            }
                        }

                        Name (BPKG, Package (0x10)
                        {
                            0x64, 
                            0x5A, 
                            0x50, 
                            0x4B, 
                            0x46, 
                            0x41, 
                            0x3C, 
                            0x37, 
                            0x32, 
                            0x2D, 
                            0x28, 
                            0x23, 
                            0x1E, 
                            0x19, 
                            0x14, 
                            0x0A
                        })
                        Method (_BCL, 0, NotSerialized)
                        {
                            Return (BPKG)
                        }

                        Method (_BCM, 1, NotSerialized)
                        {
                            Store (Match (BPKG, MEQ, Arg0, MTR, 0x00, 0x00), Local0)
                            Subtract (0x0F, Local0, Local0)
                            \_SB.ATKD.SPLV (Local0)
                        }

                        Method (_BQC, 0, NotSerialized)
                        {
                            Store (\_SB.ATKD.GPLV (), Local0)
                            Subtract (0x0F, Local0, Local0)
                            Return (DerefOf (Index (BPKG, Local0)))
                        }
                    }

                    Method (SWHD, 1, Serialized)
                    {
                        If (And (\_SB.PCI0.P0P1.VGA.DOSF, 0x01))
                        {
                            Store (Arg0, PAR1)
                            ISMI (0x73)
                        }
                        Else
                        {
                            Store (Arg0, NXTD)
                            Notify (\_SB.PCI0.P0P1.VGA, 0x80)
                        }

                        Store (One, DONE)
                    }

                    Method (GETD, 0, NotSerialized)
                    {
                        ISMI (0x72)
                        Return (PAR1)
                    }

                    Method (GETM, 0, NotSerialized)
                    {
                        ISMI (0x12)
                        Return (PAR1)
                    }

                    Method (GETN, 0, Serialized)
                    {
                        If (DONE)
                        {
                            Store (GETD (), DISD)
                            Store (GETM (), Local0)
                            If (And (Local0, 0x04))
                            {
                                Return (NXTD)
                            }
                        }

                        Store (0x00, DONE)
                        Store (0x00, Local0)
                        If (\_SB.PCI0.P0P1.VGA.DOSF)
                        {
                            If (LEqual (NXTD, 0x01))
                            {
                                Store (0x02, NXTD)
                            }
                            Else
                            {
                                If (LEqual (NXTD, 0x02))
                                {
                                    Store (0x04, NXTD)
                                }
                                Else
                                {
                                    Store (0x01, NXTD)
                                }
                            }

                            Return (NXTD)
                        }
                        Else
                        {
                            While (LOr (LNotEqual (NXTD, Local0), LEqual (And (NXTD, 0x07
                                ), 0x07)))
                            {
                                Increment (NXTD)
                                If (And (NXTD, 0xF8))
                                {
                                    Store (0x01, NXTD)
                                }

                                And (NXTD, AVLD, Local0)
                            }

                            Return (NXTD)
                        }
                    }

                    OperationRegion (NVID, PCI_Config, 0x00, 0x04)
                    Field (NVID, DWordAcc, NoLock, Preserve)
                    {
                        VGAD,   32
                    }
                }
            }

            Device (P0P3)
            {
                Name (_ADR, 0x001E0000)
                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR03)
                    }

                    Return (PR03)
                }
            }

            Device (SBRG)
            {
                Name (_ADR, 0x001F0000)
                Method (SPTS, 1, NotSerialized)
                {
                    Store (One, PS1S)
                    Store (One, PS1E)
                }

                Method (SWAK, 1, NotSerialized)
                {
                    Store (Zero, PS1E)
                    If (LNot (GNVS (0x12CE)))
                    {
                        Notify (\_SB.PWRB, 0x02)
                    }
                }

                OperationRegion (PMS0, SystemIO, PMBS, PMLN)
                Field (PMS0, ByteAcc, NoLock, Preserve)
                {
                        ,   10, 
                    RTCS,   1, 
                        ,   4, 
                    WAKS,   1, 
                            Offset (0x03), 
                    PWBT,   1, 
                            Offset (0x04)
                }

                OperationRegion (SMIE, SystemIO, PM30, 0x08)
                Field (SMIE, ByteAcc, NoLock, Preserve)
                {
                        ,   4, 
                    PS1E,   1, 
                        ,   31, 
                    PS1S,   1, 
                            Offset (0x08)
                }

                OperationRegion (GPBX, SystemIO, GPBS, GPLN)
                Field (GPBX, ByteAcc, NoLock, Preserve)
                {
                    GPUS,   32, 
                    GPSL,   32, 
                            Offset (0x0C), 
                    GPLV,   32, 
                            Offset (0x18), 
                    GPBL,   32, 
                            Offset (0x2C), 
                    GPIV,   32
                }

                Device (PIC)
                {
                    Name (_HID, EisaId ("PNP0000"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0020,             // Range Minimum
                            0x0020,             // Range Maximum
                            0x00,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A0,             // Range Minimum
                            0x00A0,             // Range Maximum
                            0x00,               // Alignment
                            0x02,               // Length
                            )
                        IRQNoFlags ()
                            {2}
                    })
                }

                Device (DMAD)
                {
                    Name (_HID, EisaId ("PNP0200"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        DMA (Compatibility, BusMaster, Transfer8, )
                            {4}
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x0081,             // Range Minimum
                            0x0081,             // Range Maximum
                            0x00,               // Alignment
                            0x03,               // Length
                            )
                        IO (Decode16,
                            0x0087,             // Range Minimum
                            0x0087,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0089,             // Range Minimum
                            0x0089,             // Range Maximum
                            0x00,               // Alignment
                            0x03,               // Length
                            )
                        IO (Decode16,
                            0x008F,             // Range Minimum
                            0x008F,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x00C0,             // Range Minimum
                            0x00C0,             // Range Maximum
                            0x00,               // Alignment
                            0x20,               // Length
                            )
                    })
                }

                Device (TMR)
                {
                    Name (_HID, EisaId ("PNP0100"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0040,             // Range Minimum
                            0x0040,             // Range Maximum
                            0x00,               // Alignment
                            0x04,               // Length
                            )
                        IRQNoFlags ()
                            {0}
                    })
                }

                Device (RTC0)
                {
                    Name (_HID, EisaId ("PNP0B00"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x00,               // Alignment
                            0x02,               // Length
                            )
                        IRQNoFlags ()
                            {8}
                    })
                }

                Device (PS2K)
                {
                    Name (_HID, EisaId ("PNP0303"))
                    Name (_CID, 0x0B03D041)
                    Method (_STA, 0, NotSerialized)
                    {
                        ShiftLeft (0x01, 0x0A, Local0)
                        If (And (IOST, Local0))
                        {
                            Return (0x0F)
                        }

                        Return (0x00)
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0060,             // Range Minimum
                            0x0060,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0064,             // Range Minimum
                            0x0064,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IRQNoFlags ()
                            {1}
                    })
                }

                Device (PS2M)
                {
                    Name (_HID, EisaId ("SYN0A06"))
                    Name (_CID, Package (0x03)
                    {
                        0x000A2E4F, 
                        0x02002E4F, 
                        0x130FD041
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        ShiftLeft (0x01, 0x0C, Local0)
                        If (And (IOST, Local0))
                        {
                            Return (0x0F)
                        }

                        Return (0x00)
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        IRQNoFlags ()
                            {12}
                    })
                }

                Device (SPKR)
                {
                    Name (_HID, EisaId ("PNP0800"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0061,             // Range Minimum
                            0x0061,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                    })
                }

                Device (COPR)
                {
                    Name (_HID, EisaId ("PNP0C04"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x00F0,             // Range Minimum
                            0x00F0,             // Range Maximum
                            0x00,               // Alignment
                            0x10,               // Length
                            )
                        IRQNoFlags ()
                            {13}
                    })
                }

                Device (EC0)
                {
                    Name (_HID, EisaId ("PNP0C09"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0062,             // Range Minimum
                            0x0062,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0066,             // Range Minimum
                            0x0066,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                    })
                    Name (_GPE, 0x13)
                    Name (REGC, 0x00)
                    Method (_REG, 2, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x03))
                        {
                            Store (Arg1, REGC)
                        }
                    }

                    Method (ECAV, 0, NotSerialized)
                    {
                        If (LEqual (REGC, Ones))
                        {
                            If (LGreaterEqual (_REV, 0x02))
                            {
                                Return (One)
                            }
                            Else
                            {
                                Return (Zero)
                            }
                        }

                        Return (REGC)
                    }

                    OperationRegion (ECOR, EmbeddedControl, 0x00, 0xFF)
                    Field (ECOR, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x04), 
                        CMD1,   8, 
                        CDT1,   8, 
                        CDT2,   8, 
                        CDT3,   8, 
                                Offset (0x80), 
                        EPWS,   8, 
                        EB0S,   8, 
                        EB1S,   8, 
                        EB0R,   8, 
                        EB1R,   8, 
                        EPWF,   8, 
                                Offset (0x87), 
                        EB0T,   8, 
                        EB1T,   8, 
                                Offset (0x93), 
                        TAH0,   16, 
                        TAH1,   16, 
                        TSTP,   8, 
                                Offset (0xA0), 
                        ECPU,   8, 
                        ECRT,   8, 
                        EPSV,   8, 
                        EACT,   8, 
                                Offset (0xB0), 
                        B0PN,   16, 
                        B0VL,   16, 
                        B0RC,   16, 
                        B0FC,   16, 
                        B0MD,   16, 
                        B0ST,   16, 
                        B0CC,   16, 
                        B0TM,   16, 
                        B0C1,   16, 
                        B0C2,   16, 
                        B0C3,   16, 
                        B0C4,   16, 
                                Offset (0xD0), 
                        B1PN,   16, 
                        B1VL,   16, 
                        B1RC,   16, 
                        B1FC,   16, 
                        B1MD,   16, 
                        B1ST,   16, 
                        B1CC,   16, 
                        B1TM,   16, 
                        B1C1,   16, 
                        B1C2,   16, 
                        B1C3,   16, 
                        B1C4,   16, 
                                Offset (0xF0), 
                        B0DC,   16, 
                        B0DV,   16, 
                        B0SN,   16, 
                                Offset (0xF8), 
                        B1DC,   16, 
                        B1DV,   16, 
                        B1SN,   16
                    }

                    OperationRegion (SMBX, EmbeddedControl, 0x18, 0x28)
                    Field (SMBX, ByteAcc, NoLock, Preserve)
                    {
                        PRTC,   8, 
                        SSTS,   5, 
                            ,   1, 
                        ALFG,   1, 
                        CDFG,   1, 
                        ADDR,   8, 
                        CMDB,   8, 
                        BDAT,   256, 
                        BCNT,   8, 
                            ,   1, 
                        ALAD,   7, 
                        ALD0,   8, 
                        ALD1,   8
                    }

                    Field (SMBX, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        DAT0,   8, 
                        DAT1,   8
                    }

                    Field (SMBX, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        DT2B,   16
                    }

                    OperationRegion (NSBS, EmbeddedControl, 0x40, 0x04)
                    Field (NSBS, ByteAcc, NoLock, Preserve)
                    {
                        A2AD,   8, 
                        A2D0,   8, 
                        A2D1,   8, 
                        A3AD,   8
                    }

                    Name (OPST, 0x00)
                    Method (EC0S, 1, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x03)) {}
                        If (Arg0)
                        {
                            If (LLess (Arg0, 0x04))
                            {
                                Store (STC5 (0x12), OPST)
                                SPIN (0x12, 0x00)
                            }
                        }
                    }

                    Method (EC0W, 1, NotSerialized)
                    {
                        If (Arg0)
                        {
                            If (LLess (Arg0, 0x04))
                            {
                                Store (0x33, DBG8)
                                SPIN (0x12, OPST)
                            }
                        }
                    }
                }

                Scope (\_SB.PCI0.SBRG.EC0)
                {
                    Mutex (MUEC, 0x00)
                    Name (WRQK, 0x02)
                    Name (RDQK, 0x03)
                    Name (SDBT, 0x04)
                    Name (RCBT, 0x05)
                    Name (WRBT, 0x06)
                    Name (RDBT, 0x07)
                    Name (WRWD, 0x08)
                    Name (RDWD, 0x09)
                    Name (WRBL, 0x0A)
                    Name (RDBL, 0x0B)
                    Name (PCLL, 0x0C)
                    Name (GOOD, 0x00)
                    Name (UKER, 0x07)
                    Name (DAER, 0x10)
                    Name (CMDN, 0x12)
                    Name (UKE2, 0x13)
                    Name (DADN, 0x17)
                    Name (SBTO, 0x18)
                    Name (USPT, 0x19)
                    Name (SBBY, 0x1A)
                    OperationRegion (DLYP, SystemIO, 0xE1, 0x01)
                    Field (DLYP, ByteAcc, NoLock, Preserve)
                    {
                        DELY,   8
                    }

                    OperationRegion (KBCP, SystemIO, 0x60, 0x07)
                    Field (KBCP, ByteAcc, Lock, Preserve)
                    {
                        KBCD,   8, 
                                Offset (0x02), 
                        EC62,   8, 
                                Offset (0x04), 
                        KBCC,   8, 
                                Offset (0x06), 
                        EC66,   8
                    }

                    Field (KBCP, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x04), 
                        KBOF,   1, 
                        KBIE,   1, 
                                Offset (0x05), 
                                Offset (0x06), 
                        ECOF,   1, 
                        ECIE,   1, 
                                Offset (0x07)
                    }

                    Method (IBFR, 0, Serialized)
                    {
                        Store (0x1000, Local0)
                        While (LAnd (Decrement (Local0), KBIE))
                        {
                            Store (0x00, DELY)
                        }
                    }

                    Method (OBFL, 0, Serialized)
                    {
                        Store (0x1000, Local0)
                        While (LAnd (Decrement (Local0), LNot (KBOF)))
                        {
                            Store (0x00, DELY)
                        }
                    }

                    Method (WKBC, 2, Serialized)
                    {
                        IBFR ()
                        Store (Arg0, KBCC)
                        IBFR ()
                        Store (Arg1, KBCD)
                        IBFR ()
                    }

                    Method (RRAM, 2, Serialized)
                    {
                        If (ECAV ())
                        {
                            If (LNot (Acquire (MUEC, 0xFFFF)))
                            {
                                Store (Arg0, CDT3)
                                Store (Arg1, CDT2)
                                Store (0xBA, CMD1)
                                Store (0x7F, Local0)
                                While (LAnd (Local0, CMD1))
                                {
                                    Sleep (0x01)
                                    Decrement (Local0)
                                }

                                If (LEqual (CMD1, Zero))
                                {
                                    Store (CDT1, Local0)
                                }
                                Else
                                {
                                    Store (Ones, Local0)
                                }

                                Release (MUEC)
                                Return (Local0)
                            }
                        }

                        Return (Ones)
                    }

                    Method (WRAM, 3, Serialized)
                    {
                        If (ECAV ())
                        {
                            If (LNot (Acquire (MUEC, 0xFFFF)))
                            {
                                Store (Arg0, CDT3)
                                Store (Arg1, CDT2)
                                Store (Arg2, CDT1)
                                Store (0xBB, CMD1)
                                Store (0x7F, Local0)
                                While (LAnd (Local0, CMD1))
                                {
                                    Sleep (0x01)
                                    Decrement (Local0)
                                }

                                If (LEqual (CMD1, Zero))
                                {
                                    Store (One, Local0)
                                }
                                Else
                                {
                                    Store (Ones, Local0)
                                }

                                Release (MUEC)
                                Return (Local0)
                            }
                        }

                        Return (Ones)
                    }

                    Method (SADC, 2, Serialized)
                    {
                        If (ECAV ())
                        {
                            If (LNot (Acquire (MUEC, 0xFFFF)))
                            {
                                Store (Arg0, CDT1)
                                Store (Arg1, CDT2)
                                Store (0xC4, CMD1)
                                Store (0x7F, Local0)
                                While (LAnd (Local0, CMD1))
                                {
                                    Sleep (0x01)
                                    Decrement (Local0)
                                }

                                If (LEqual (CMD1, Zero))
                                {
                                    Store (CDT1, Local0)
                                }
                                Else
                                {
                                    Store (Ones, Local0)
                                }

                                Release (MUEC)
                                Return (Local0)
                            }
                        }

                        Return (Ones)
                    }

                    Method (STC5, 1, Serialized)
                    {
                        If (ECAV ())
                        {
                            If (LNot (Acquire (MUEC, 0xFFFF)))
                            {
                                Store (Arg0, CDT1)
                                Store (0xC5, CMD1)
                                Store (0x7F, Local0)
                                While (LAnd (Local0, CMD1))
                                {
                                    Sleep (0x01)
                                    Decrement (Local0)
                                }


                                If (LEqual (CMD1, Zero))
                                {
                                    Store (CDT1, Local0)
                                }
                                Else
                                {
                                    Store (Ones, Local0)
                                }

                                Release (MUEC)
                                Return (Local0)
                            }
                        }

                        Return (Ones)
                    }

                    Method (SPIN, 2, Serialized)
                    {
                        And (Arg0, 0x1F, Local0)
                        If (Arg1)
                        {
                            Or (Local0, 0x20, Local0)
                        }
                        Else
                        {
                            Or (Local0, 0x40, Local0)
                        }

                        STC5 (Local0)
                        Return (Ones)
                    }

                    Method (GPIN, 1, Serialized)
                    {
                        And (Arg0, 0x1F, Local0)
                        Return (STC5 (Local0))
                    }

                    Method (SWTC, 2, Serialized)
                    {
                        Store (0x05, Local2)
                        While (Local2)
                        {
                            Store (Arg1, PRTC)
                            And (Arg0, 0xFFFF, Local1)
                            While (Local1)
                            {
                                If (LEqual (PRTC, 0x00))
                                {
                                    Store (SSTS, Local0)
                                    Store (Zero, Local1)
                                    If (Local0)
                                    {
                                        Decrement (Local2)
                                    }
                                    Else
                                    {
                                        Store (Zero, Local2)
                                    }
                                }
                                Else
                                {
                                    Sleep (0x01)
                                    If (LNotEqual (Local1, 0xFFFF))
                                    {
                                        Decrement (Local1)
                                        If (LEqual (Local1, 0x00))
                                        {
                                            Store (Zero, PRTC)
                                            Store (Zero, Local2)
                                            Store (UKER, Local0)
                                        }
                                    }
                                }
                            }
                        }

                        Return (Local0)
                    }

                    Method (SMBR, 3, Serialized)
                    {
                        Store (Package (0x03)
                            {
                                UKER, 
                                0x00, 
                                0x00
                            }, Local0)
                        If (LNot (ECAV ()))
                        {
                            Return (Local0)
                        }

                        If (LNotEqual (Arg0, RDBL))
                        {
                            If (LNotEqual (Arg0, RDWD))
                            {
                                If (LNotEqual (Arg0, RDBT))
                                {
                                    If (LNotEqual (Arg0, RCBT))
                                    {
                                        If (LNotEqual (Arg0, RDQK))
                                        {
                                            Return (Local0)
                                        }
                                    }
                                }
                            }
                        }

                        If (LNot (Acquire (MUEC, 0xFFFF)))
                        {
                            Store (PRTC, Local1)
                            Store (Zero, Local2)
                            While (LNotEqual (Local1, 0x00))
                            {
                                Stall (0x0A)
                                Increment (Local2)
                                If (LGreater (Local2, 0x03E8))
                                {
                                    Store (SBBY, Index (Local0, 0x00))
                                    Store (Zero, Local1)
                                }
                                Else
                                {
                                    Store (PRTC, Local1)
                                }
                            }

                            If (LLessEqual (Local2, 0x03E8))
                            {
                                ShiftLeft (Arg1, 0x01, Local3)
                                Or (Local3, 0x01, Local3)
                                Store (Local3, ADDR)
                                If (LNotEqual (Arg0, RDQK))
                                {
                                    If (LNotEqual (Arg0, RCBT))
                                    {
                                        Store (Arg2, CMDB)
                                    }
                                }

                                Store (SWTC (0x07D0, Arg0), Index (Local0, 0x00))
                                If (LEqual (DerefOf (Index (Local0, 0x00)), 0x00))
                                {
                                    If (LEqual (Arg0, RDBL))
                                    {
                                        Store (BCNT, Index (Local0, 0x01))
                                        Store (BDAT, Index (Local0, 0x02))
                                    }

                                    If (LEqual (Arg0, RDWD))
                                    {
                                        Store (0x02, Index (Local0, 0x01))
                                        Store (DT2B, Index (Local0, 0x02))
                                    }

                                    If (LEqual (Arg0, RDBT))
                                    {
                                        Store (0x01, Index (Local0, 0x01))
                                        Store (DAT0, Index (Local0, 0x02))
                                    }

                                    If (LEqual (Arg0, RCBT))
                                    {
                                        Store (0x01, Index (Local0, 0x01))
                                        Store (DAT0, Index (Local0, 0x02))
                                    }
                                }
                            }

                            Release (MUEC)
                        }

                        Return (Local0)
                    }

                    Method (SMBW, 5, Serialized)
                    {
                        Store (Package (0x01)
                            {
                                UKER
                            }, Local0)
                        If (LNot (ECAV ()))
                        {
                            Return (Local0)
                        }

                        If (LNotEqual (Arg0, WRBL))
                        {
                            If (LNotEqual (Arg0, WRWD))
                            {
                                If (LNotEqual (Arg0, WRBT))
                                {
                                    If (LNotEqual (Arg0, SDBT))
                                    {
                                        If (LNotEqual (Arg0, WRQK))
                                        {
                                            Return (Local0)
                                        }
                                    }
                                }
                            }
                        }


                        If (LNot (Acquire (MUEC, 0xFFFF)))
                        {
                            Store (PRTC, Local1)
                            Store (Zero, Local2)
                            While (LNotEqual (Local1, 0x00))
                            {
                                Stall (0x0A)
                                Increment (Local2)
                                If (LGreater (Local2, 0x03E8))
                                {
                                    Store (SBBY, Index (Local0, 0x00))
                                    Store (Zero, Local1)
                                }
                                Else
                                {
                                    Store (PRTC, Local1)
                                }
                            }

                            If (LLessEqual (Local2, 0x03E8))
                            {
                                ShiftLeft (Arg1, 0x01, Local3)
                                Store (Local3, ADDR)
                                If (LNotEqual (Arg0, WRQK))
                                {
                                    If (LNotEqual (Arg0, SDBT))
                                    {
                                        Store (Arg2, CMDB)
                                    }
                                }

                                If (LEqual (Arg0, WRBL))
                                {
                                    Store (Arg3, BCNT)
                                    Store (Arg4, BDAT)
                                }

                                If (LEqual (Arg0, WRWD))
                                {
                                    Store (Arg4, DT2B)
                                }

                                If (LEqual (Arg0, WRBT))
                                {
                                    Store (Arg4, DAT0)
                                }

                                If (LEqual (Arg0, SDBT))
                                {
                                    Store (Arg4, DAT0)
                                }

                                Store (SWTC (0x07D0, Arg0), Index (Local0, 0x00))
                            }

                            Release (MUEC)
                        }

                        Return (Local0)
                    }

                    Method (RCTP, 0, Serialized)
                    {
                        If (ECAV ())
                        {
                            Store (ECPU, Local0)
                        }
                        Else
                        {
                            Store (Zero, Local0)
                        }

                        Return (Local0)
                    }

                    Method (TACH, 1, Serialized)
                    {
                        If (LNot (ECAV ()))
                        {
                            Return (Ones)
                        }

                        If (Arg0)
                        {
                            Store (TAH1, Local0)
                        }
                        Else
                        {
                            Store (TAH0, Local0)
                        }

                        And (Local0, 0xFFFF, Local0)
                        If (LNotEqual (Local0, 0x00))
                        {
                            If (LEqual (Local0, 0xFFFF))
                            {
                                Store (Zero, Local0)
                            }
                            Else
                            {
                                Store (0x80, Local1)
                                Store (0x02, Local2)
                                Multiply (Local1, Local2, Local3)
                                Multiply (Local0, Local3, Local4)
                                Divide (0x03938700, Local4, Local5, Local6)
                                Multiply (Local6, 0x0A, Local6)
                                Store (Local6, Local0)
                            }
                        }

                        Return (Local0)
                    }

                    Method (RBAT, 2, Serialized)
                    {
                        If (LNot (ECAV ()))
                        {
                            Return (Ones)
                        }

                        If (LEqual (Acquire (MUEC, 0xFFFF), 0x00))
                        {
                            Store (0x03, Local0)
                            While (Local0)
                            {
                                Store (Arg0, CDT2)
                                Store (Arg1, Local1)
                                ShiftLeft (Local1, 0x01, Local1)
                                Add (Local1, 0xDA, Local1)
                                Store (Local1, CMD1)
                                Store (0x7F, Local1)
                                While (LAnd (CMD1, Local1))
                                {
                                    Decrement (Local1)
                                    Sleep (0x01)
                                }

                                If (LEqual (CMD1, 0x00))
                                {
                                    Store (CDT1, Local1)
                                    Store (Zero, Local0)
                                }
                                Else
                                {
                                    Store (Ones, Local1)
                                    Decrement (Local0)
                                }
                            }

                            Release (MUEC)
                            Return (Local1)
                        }

                        Return (Ones)
                    }

                    Method (WBAT, 3, Serialized)
                    {
                        Or (Arg0, 0x80, Local3)
                        If (LNot (ECAV ()))
                        {
                            Return (Ones)
                        }

                        If (LEqual (Acquire (MUEC, 0xFFFF), 0x00))
                        {
                            Store (0x03, Local0)
                            While (Local0)
                            {
                                Store (Arg2, CDT1)
                                Store (Local3, CDT2)
                                Store (Arg1, Local1)
                                ShiftLeft (Local1, 0x01, Local1)
                                Add (Local1, 0xDA, Local1)
                                Store (Local1, CMD1)
                                Store (0x7F, Local1)
                                While (LAnd (CMD1, Local1))
                                {
                                    Decrement (Local1)
                                    Sleep (0x01)
                                }
                            }

                            Release (MUEC)
                            Return (Local1)
                        }

                        Return (Ones)
                    }
                }

                Scope (\)
                {
                    Method (ECRB, 2, Serialized)
                    {
                        Store (\_SB.PCI0.SBRG.EC0.SMBR (\_SB.PCI0.SBRG.EC0.RDBT, Arg0, Arg1), Local0)
                        If (LEqual (DerefOf (Index (Local0, 0x00)), \_SB.PCI0.SBRG.EC0.GOOD))
                        {
                            Return (DerefOf (Index (Local0, 0x02)))
                        }
                        Else
                        {
                            Return (DerefOf (Index (Local0, 0x00)))
                        }
                    }

                    Method (ECWB, 3, Serialized)
                    {
                        Store (\_SB.PCI0.SBRG.EC0.SMBW (\_SB.PCI0.SBRG.EC0.WRBT, Arg0, Arg1, 0x01, Arg2), Local0)
                        Return (DerefOf (Index (Local0, 0x00)))
                    }

                    OperationRegion (PMBX, SystemIO, 0x0800, 0x40)
                    Field (PMBX, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x28), 
                            ,   19, 
                        KSCS,   1, 
                                Offset (0x2C), 
                            ,   19, 
                        KSCE,   1
                    }
                }

                Method (SEDN, 1, NotSerialized)
                {
                    Store (Arg0, LDN)
                }

                OperationRegion (IOID, SystemIO, HPIO, 0x02)
                Field (IOID, ByteAcc, NoLock, Preserve)
                {
                    INDX,   8, 
                    DATA,   8
                }

                IndexField (INDX, DATA, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x07), 
                    LDN,    8, 
                            Offset (0x30), 
                    ACTR,   8, 
                            Offset (0x60), 
                    IOAH,   8, 
                    IOAL,   8, 
                    IOH2,   8, 
                    IOL2,   8, 
                            Offset (0x70), 
                    INTR,   8, 
                            Offset (0x74), 
                    DMCH,   8, 
                            Offset (0xF0), 
                    OPT0,   8, 
                    OPT1,   8, 
                    OPT2,   8
                }

                Method (DCNT, 2, NotSerialized)
                {
                    SEDN (Arg0)
                    ShiftLeft (IOAH, 0x08, Local1)
                    Or (IOAL, Local1, Local1)
                    If (LAnd (LLess (DMCH, 0x04), LNotEqual (And (DMCH, 0x03, 
                        Local1), 0x00)))
                    {
                        RDMA (Arg0, Arg1, Increment (Local1))
                    }

                    Store (Arg1, ACTR)
                    RRIO (Arg0, Arg1, Local1, 0x08)
                }

                Device (CIR)
                {
                    Name (_HID, EisaId ("ITE8707"))
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (IRST (0x10))
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        DCNT (0x10, 0x00)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Return (IRCR (0x10))
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        IRSR (Arg0, 0x10)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IRPR)
                    }

                    Method (IRST, 1, NotSerialized)
                    {
                        SEDN (Arg0)
                        If (ACTR)
                        {
                            Store (0x0F, Local0)
                        }
                        Else
                        {
                            If (IOAH)
                            {
                                Store (0x0D, Local0)
                            }
                            Else
                            {
                                Store (0x00, Local0)
                            }
                        }

                        Return (Local0)
                    }

                    Name (IRPR, ResourceTemplate ()
                    {
                        StartDependentFn (0x00, 0x00)
                        {
                            IO (Decode16,
                                0x0300,             // Range Minimum
                                0x0300,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {4}
                        }
                        EndDependentFn ()
                    })
                    Name (PBUF, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x08,               // Length
                            _Y00)
                        IRQNoFlags (_Y01)
                            {0}
                    })
                    Method (IRCR, 1, NotSerialized)
                    {
                        CreateByteField (PBUF, \_SB.PCI0.SBRG.CIR._Y00._MIN, IOLO)
                        CreateByteField (PBUF, 0x03, IOHI)
                        CreateWordField (PBUF, \_SB.PCI0.SBRG.CIR._Y00._MIN, IOHL)
                        CreateWordField (PBUF, \_SB.PCI0.SBRG.CIR._Y00._MAX, IORL)
                        CreateByteField (PBUF, \_SB.PCI0.SBRG.CIR._Y00._ALN, ALMN)
                        CreateByteField (PBUF, \_SB.PCI0.SBRG.CIR._Y00._LEN, LENG)
                        CreateWordField (PBUF, \_SB.PCI0.SBRG.CIR._Y01._INT, IRQL)
                        SEDN (Arg0)
                        Store (IOAH, IOHI)
                        Store (IOAL, IOLO)
                        Store (IOHL, IORL)
                        Store (0x01, ALMN)
                        Store (0x04, LENG)
                        Store (One, Local0)
                        ShiftLeft (Local0, INTR, IRQL)
                        Return (PBUF)
                    }

                    Method (IRSR, 2, NotSerialized)
                    {
                        CreateByteField (Arg0, 0x02, POLB)
                        CreateByteField (Arg0, 0x03, POHB)
                        CreateWordField (Arg0, 0x09, PIRQ)
                        SEDN (Arg1)
                        Store (One, ACTR)
                    }
                }

                Device (RMSC)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x10)
                    Name (CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0010,             // Range Minimum
                            0x0010,             // Range Maximum
                            0x00,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x0022,             // Range Minimum
                            0x0022,             // Range Maximum
                            0x00,               // Alignment
                            0x1E,               // Length
                            )
                        IO (Decode16,
                            0x0044,             // Range Minimum
                            0x0044,             // Range Maximum
                            0x00,               // Alignment
                            0x0A,               // Length
                            )
                        IO (Decode16,
                            0x0050,             // Range Minimum
                            0x0050,             // Range Maximum
                            0x00,               // Alignment
                            0x0F,               // Length
                            )
                        IO (Decode16,
                            0x0063,             // Range Minimum
                            0x0063,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0065,             // Range Minimum
                            0x0065,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0067,             // Range Minimum
                            0x0067,             // Range Maximum
                            0x00,               // Alignment
                            0x09,               // Length
                            )
                        IO (Decode16,
                            0x0072,             // Range Minimum
                            0x0072,             // Range Maximum
                            0x00,               // Alignment
                            0x0E,               // Length
                            )
                        IO (Decode16,
                            0x0080,             // Range Minimum
                            0x0080,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0084,             // Range Minimum
                            0x0084,             // Range Maximum
                            0x00,               // Alignment
                            0x03,               // Length
                            )
                        IO (Decode16,
                            0x0088,             // Range Minimum
                            0x0088,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x008C,             // Range Minimum
                            0x008C,             // Range Maximum
                            0x00,               // Alignment
                            0x03,               // Length
                            )
                        IO (Decode16,
                            0x0090,             // Range Minimum
                            0x0090,             // Range Maximum
                            0x00,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x00A2,             // Range Minimum
                            0x00A2,             // Range Maximum
                            0x00,               // Alignment
                            0x1E,               // Length
                            )
                        IO (Decode16,
                            0x00E0,             // Range Minimum
                            0x00E0,             // Range Maximum
                            0x00,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x025C,             // Range Minimum
                            0x025C,             // Range Maximum
                            0x00,               // Alignment
                            0x04,               // Length
                            )
                        IO (Decode16,
                            0x04D0,             // Range Minimum
                            0x04D0,             // Range Maximum
                            0x00,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x00,               // Length
                            _Y02)
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x00,               // Length
                            _Y03)
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x00,               // Length
                            _Y04)
                        Memory32Fixed (ReadWrite,
                            0xFED1C000,         // Address Base
                            0x00004000,         // Address Length
                            )
                        Memory32Fixed (ReadWrite,
                            0xFED20000,         // Address Base
                            0x00020000,         // Address Length
                            )
                        Memory32Fixed (ReadWrite,
                            0xFED50000,         // Address Base
                            0x00040000,         // Address Length
                            )
                        Memory32Fixed (ReadWrite,
                            0xFFB00000,         // Address Base
                            0x00100000,         // Address Length
                            )
                        Memory32Fixed (ReadWrite,
                            0xFFF00000,         // Address Base
                            0x00100000,         // Address Length
                            )
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y02._MIN, GP00)
                        CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y02._MAX, GP01)
                        CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y02._LEN, GP0L)
                        Store (PMBS, GP00)
                        Store (PMBS, GP01)
                        Store (PMLN, GP0L)
                        If (SMBS)
                        {
                            CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y03._MIN, GP10)
                            CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y03._MAX, GP11)
                            CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y03._LEN, GP1L)
                            Store (SMBS, GP10)
                            Store (SMBS, GP11)
                            Store (SMBL, GP1L)
                        }

                        If (GPBS)
                        {
                            CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y04._MIN, GP20)
                            CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y04._MAX, GP21)
                            CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y04._LEN, GP2L)
                            Store (GPBS, GP20)
                            Store (GPBS, GP21)
                            Store (GPLN, GP2L)
                        }

                        Return (CRS)
                    }
                }

                Device (HPET)
                {
                    Name (_HID, EisaId ("PNP0103"))
                    Name (CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0xFED00000,         // Address Base
                            0x00000400,         // Address Length
                            _Y05)
                    })
                    OperationRegion (HPTC, SystemMemory, HTBA, 0x04)
                    Field (HPTC, ByteAcc, NoLock, Preserve)
                    {
                        HPTS,   2, 
                            ,   5, 
                        HPTE,   1, 
                                Offset (0x04)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (LEqual (OSFL (), 0x00))
                        {
                            If (HPTE)
                            {
                                Return (0x0F)
                            }
                        }
                        Else
                        {
                            If (HPTE)
                            {
                                Return (0x0B)
                            }
                        }

                        Return (0x00)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        CreateDWordField (CRS, \_SB.PCI0.SBRG.HPET._Y05._BAS, HPT)
                        Multiply (HPTS, 0x1000, Local0)
                        Add (Local0, 0xFED00000, HPT)
                        Return (CRS)
                    }
                }

                OperationRegion (RX80, PCI_Config, 0x00, 0xFF)
                Field (RX80, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x80), 
                    LPCD,   16, 
                    LPCE,   16
                }

                Name (DBPT, Package (0x04)
                {
                    Package (0x08)
                    {
                        0x03F8, 
                        0x02F8, 
                        0x0220, 
                        0x0228, 
                        0x0238, 
                        0x02E8, 
                        0x0338, 
                        0x03E8
                    }, 

                    Package (0x08)
                    {
                        0x03F8, 
                        0x02F8, 
                        0x0220, 
                        0x0228, 
                        0x0238, 
                        0x02E8, 
                        0x0338, 
                        0x03E8
                    }, 

                    Package (0x03)
                    {
                        0x0378, 
                        0x0278, 
                        0x03BC
                    }, 

                    Package (0x02)
                    {
                        0x03F0, 
                        0x0370
                    }
                })
                Name (DDLT, Package (0x04)
                {
                    Package (0x02)
                    {
                        0x00, 
                        0xFFF8
                    }, 

                    Package (0x02)
                    {
                        0x04, 
                        0xFF8F
                    }, 

                    Package (0x02)
                    {
                        0x08, 
                        0xFCFF
                    }, 

                    Package (0x02)
                    {
                        0x0C, 
                        0xEFFF
                    }
                })
                Method (RRIO, 4, NotSerialized)
                {
                    If (LAnd (LLessEqual (Arg0, 0x03), LGreaterEqual (Arg0, 0x00)))
                    {
                        Store (Match (DerefOf (Index (DBPT, Arg0)), MEQ, Arg2, MTR, 
                            0x00, 0x00), Local0)
                        If (LNotEqual (Local0, Ones))
                        {
                            Store (DerefOf (Index (DerefOf (Index (DDLT, Arg0)), 0x00)), 
                                Local1)
                            Store (DerefOf (Index (DerefOf (Index (DDLT, Arg0)), 0x01)), 
                                Local2)
                            ShiftLeft (Local0, Local1, Local0)
                            And (LPCD, Local2, LPCD)
                            Or (LPCD, Local0, LPCD)
                            WX82 (Arg0, Arg1)
                        }
                    }

                    If (LEqual (Arg0, 0x08))
                    {
                        If (LEqual (Arg2, 0x0200))
                        {
                            WX82 (0x08, Arg0)
                        }
                        Else
                        {
                            If (LEqual (Arg2, 0x0208))
                            {
                                WX82 (0x09, Arg0)
                            }
                        }
                    }

                    If (LAnd (LLessEqual (Arg0, 0x0D), LGreaterEqual (Arg0, 0x0A)))
                    {
                        WX82 (Arg0, Arg1)
                    }
                }

                Method (WX82, 2, NotSerialized)
                {
                    ShiftLeft (0x01, Arg0, Local0)
                    If (Arg1)
                    {
                        Or (LPCE, Local0, LPCE)
                    }
                    Else
                    {
                        Not (Local0, Local0)
                        And (LPCE, Local0, LPCE)
                    }
                }

                Method (RDMA, 3, NotSerialized)
                {
                }

                Scope (\)
                {
                    OperationRegion (\RAMW, SystemMemory, Subtract (TOPM, 0x00010000), 0x00010000)
                    Field (\RAMW, ByteAcc, NoLock, Preserve)
                    {
                        PAR0,   32, 
                        PAR1,   32
                    }

                    OperationRegion (IOB2, SystemIO, 0xB2, 0x02)
                    Field (IOB2, ByteAcc, NoLock, Preserve)
                    {
                        SMIC,   8, 
                        SMIS,   8
                    }

                    Method (ISMI, 1, Serialized)
                    {
                        Store (Arg0, SMIC)
                    }

                    Method (GNVS, 1, Serialized)
                    {
                        Store (Arg0, PAR0)
                        ISMI (0x70)
                        Return (PAR1)
                    }

                    Method (SNVS, 2, Serialized)
                    {
                        Store (Arg0, PAR0)
                        Store (Arg1, PAR1)
                        ISMI (0x71)
                    }
                }

                Device (\_SB.PCI0.PCIE)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x11)
                    Name (CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0xE0000000,         // Address Base
                            0x10000000,         // Address Length
                            _Y06)
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        CreateDWordField (CRS, \_SB.PCI0.PCIE._Y06._BAS, BAS1)
                        CreateDWordField (CRS, \_SB.PCI0.PCIE._Y06._LEN, LEN1)
                        Store (\PCIB, BAS1)
                        Store (\PCIL, LEN1)
                        Return (CRS)
                    }
                }

                Device (OMSC)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x00)
                    Name (CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0x00000000,         // Address Base
                            0x00000000,         // Address Length
                            _Y07)
                        Memory32Fixed (ReadOnly,
                            0x00000000,         // Address Base
                            0x00000000,         // Address Length
                            _Y08)
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        If (APIC)
                        {
                            CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y07._LEN, ML01)
                            CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y07._BAS, MB01)
                            CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y08._LEN, ML02)
                            CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y08._BAS, MB02)
                            Store (0xFEC00000, MB01)
                            Store (0x1000, ML01)
                            Store (0xFEE00000, MB02)
                            Store (0x1000, ML02)
                        }

                        Return (CRS)
                    }
                }

                Device (\_SB.RMEM)
                {
                    Name (_HID, EisaId ("PNP0C01"))
                    Name (_UID, 0x01)
                    Name (CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadWrite,
                            0x00000000,         // Address Base
                            0x000A0000,         // Address Length
                            )
                        Memory32Fixed (ReadOnly,
                            0x00000000,         // Address Base
                            0x00000000,         // Address Length
                            _Y09)
                        Memory32Fixed (ReadOnly,
                            0x000E0000,         // Address Base
                            0x00020000,         // Address Length
                            _Y0A)
                        Memory32Fixed (ReadWrite,
                            0x00100000,         // Address Base
                            0x00000000,         // Address Length
                            _Y0B)
                        Memory32Fixed (ReadOnly,
                            0x00000000,         // Address Base
                            0x00000000,         // Address Length
                            _Y0C)
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        CreateDWordField (CRS, \_SB.RMEM._Y09._BAS, BAS1)
                        CreateDWordField (CRS, \_SB.RMEM._Y09._LEN, LEN1)
                        CreateDWordField (CRS, \_SB.RMEM._Y0A._BAS, BAS2)
                        CreateDWordField (CRS, \_SB.RMEM._Y0A._LEN, LEN2)
                        CreateDWordField (CRS, \_SB.RMEM._Y0B._LEN, LEN3)
                        CreateDWordField (CRS, \_SB.RMEM._Y0C._BAS, BAS4)
                        CreateDWordField (CRS, \_SB.RMEM._Y0C._LEN, LEN4)
                        If (OSFL ()) {}
                        Else
                        {
                            If (MG1B)
                            {
                                If (LGreater (MG1B, 0x000C0000))
                                {
                                    Store (0x000C0000, BAS1)
                                    Subtract (MG1B, BAS1, LEN1)
                                }
                            }
                            Else
                            {
                                Store (0x000C0000, BAS1)
                                Store (0x00020000, LEN1)
                            }

                            If (Add (MG1B, MG1L, Local0))
                            {
                                Store (Local0, BAS2)
                                Subtract (0x00100000, BAS2, LEN2)
                            }
                        }

                        Subtract (MG2B, 0x00100000, LEN3)
                        Add (MG2B, MG2L, BAS4)
                        Subtract (0x00, BAS4, LEN4)
                        Return (CRS)
                    }
                }

                Scope (\)
                {
                    OperationRegion (RCBA, SystemMemory, 0xFED1C000, 0x4000)
                    Field (RCBA, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x3418), 
                        FDRT,   32
                    }

                    Method (ECCA, 0, Serialized)
                    {
                        Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0x80), Local0)
                        If (And (Local0, 0x01))
                        {
                            Return (One)
                        }
                        Else
                        {
                            Return (Zero)
                        }
                    }

                    Method (ECCB, 1, Serialized)
                    {
                        Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0x80), Local0)
                        If (And (Local0, ShiftLeft (0x01, Arg0)))
                        {
                            Return (Zero)
                        }
                        Else
                        {
                            Return (One)
                        }
                    }

                    Method (ECDC, 1, Serialized)
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xF0), Local0)
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xF1), Local1)
                            Return (Or (ShiftLeft (Local1, 0x08), Local0))
                        }
                        Else
                        {
                            Return (Ones)
                        }
                    }

                    Method (ECDV, 1, Serialized)
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xF2), Local0)
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xF3), Local1)
                            Return (Or (ShiftLeft (Local1, 0x08), Local0))
                        }
                        Else
                        {
                            Return (Ones)
                        }
                    }

                    Method (ECPP, 1, Serialized)
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xB0), Local0)
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xB1), Local1)
                            Return (Or (ShiftLeft (Local1, 0x08), Local0))
                        }
                        Else
                        {
                            Return (Ones)
                        }
                    }

                    Method (ECGS, 1, Serialized)
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Return (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0x81))
                        }
                        Else
                        {
                            Return (Ones)
                        }
                    }

                    Method (ECFC, 1, Serialized)
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xB6), Local0)
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xB7), Local1)
                            Return (Or (ShiftLeft (Local1, 0x08), Local0))
                        }
                        Else
                        {
                            Return (Ones)
                        }
                    }

                    Method (ECRC, 1, Serialized)
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xB4), Local0)
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xB5), Local1)
                            Return (Or (ShiftLeft (Local1, 0x08), Local0))
                        }
                        Else
                        {
                            Return (Ones)
                        }
                    }

                    Method (ECPV, 1, Serialized)
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xB2), Local0)
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xB3), Local1)
                            Return (Or (ShiftLeft (Local1, 0x08), Local0))
                        }
                        Else
                        {
                            Return (Ones)
                        }
                    }

                    Method (ECBC, 1, Serialized)
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xBC), Local0)
                            Store (\_SB.PCI0.SBRG.EC0.RRAM (0x08, 0xBD), Local1)
                            Return (Or (ShiftLeft (Local1, 0x08), Local0))
                        }
                        Else
                        {
                            Return (Ones)

                        }
                    }

                    Method (DHLW, 0, NotSerialized)
                    {
                        Store (ECCA (), \ACPS)
                        If (ECCB (0x01))
                        {
                            Store (0x00, \DCPS)
                        }
                        Else
                        {
                            Store (0x01, \DCPS)
                        }

                        \_SB.PCI0.SBRG.EC0.STBR ()
                        Return (One)
                    }
                }

                Scope (\_TZ)
                {
                    Name (TSP, 0x0A)
                    Name (TC1, 0x02)
                    Name (TC2, 0x0A)
                    Name (TCRT, 0x6E)
                    Name (TPSV, 0x6E)
                    Method (KELV, 1, NotSerialized)
                    {
                        And (Arg0, 0xFF, Local0)
                        Multiply (Local0, 0x0A, Local0)
                        Add (Local0, 0x0AAC, Local0)
                        Return (Local0)
                    }

                    Method (CELC, 1, NotSerialized)
                    {
                        Subtract (Arg0, 0x0AAC, Local0)
                        Divide (Local0, 0x0A, Local1, Local0)
                        Return (Local0)
                    }

                    Method (RTMP, 0, Serialized)
                    {
                        Return (\_SB.PCI0.SBRG.EC0.RCTP ())
                    }

                    Method (RSYS, 0, Serialized)
                    {
                        Return (Zero)
                    }

                    ThermalZone (TZ00)
                    {
                        Name (_TZP, 0x012C)
                        Name (_PSL, Package (0x01)
                        {
                            \_PR.CPU1
                        })
                        Method (_CRT, 0, NotSerialized)
                        {
                            Return (KELV (TCRT))
                        }

                        Method (_PSV, 0, NotSerialized)
                        {
                            Return (KELV (TPSV))
                        }

                        Method (_TMP, 0, NotSerialized)
                        {
                            Store (0x05, Local1)
                            While (Local1)
                            {
                                Store (RTMP (), Local0)
                                If (LGreater (Local0, TCRT))
                                {
                                    Decrement (Local1)
                                }
                                Else
                                {
                                    Return (KELV (Local0))
                                }
                            }

                            Return (KELV (Local0))
                        }

                        Method (_TSP, 0, NotSerialized)
                        {
                            Multiply (TSP, 0x01, Local0)
                            Return (Local0)
                        }

                        Method (_TC1, 0, NotSerialized)
                        {
                            Return (TC1)
                        }

                        Method (_TC2, 0, NotSerialized)
                        {
                            Return (TC2)
                        }
                    }
                }

                Scope (\_SB)
                {
                    Device (LID)
                    {
                        Name (LIDS, 0x01)
                        Name (_HID, EisaId ("PNP0C0D"))
                        Method (_LID, 0, NotSerialized)
                        {
                            Return (\_SB.PCI0.SBRG.EC0.GPIN (0x06))
                        }
                    }
                }

                Scope (\_SB.PCI0.SBRG)
                {
                    Field (GPBX, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x0C), 
                            ,   6, 
                        SB06,   1, 
                        SB07,   1, 
                            ,   13, 
                        WLED,   1, 
                                Offset (0x38), 
                            ,   4, 
                        WCTL,   1, 
                        BCTL,   1
                    }
                }

                Scope (\_SB.PCI0.SBRG.EC0)
                {
                    Method (_Q0A, 0, NotSerialized)
                    {
                        Notify (\_SB.SLPB, 0x80)
                    }

                    Method (_Q0B, 0, NotSerialized)
                    {
                        If (LEqual (\WAPF, 0x01))
                        {
                            ATKR (0x5D)
                        }
                        Else
                        {
                            ATKR (0x88)
                        }
                    }

                    Method (_Q0C, 0, NotSerialized)
                    {
                        ATKR (0x50)
                    }

                    Method (_Q0D, 0, NotSerialized)
                    {
                        ATKR (0x51)
                    }

                    Method (_Q0E, 0, NotSerialized)
                    {
                        Store (GNVS (0x44A4), Local0)
                        If (LGreater (Local0, 0x00))
                        {
                            Decrement (Local0)
                        }

                        If (LGreater (Local0, 0x0E))
                        {
                            Store (0x0E, Local0)
                        }

                        SNVS (0x44A4, Local0)
                        STBR ()
                        ATKR (Add (Local0, 0x20))
                    }

                    Method (_Q0F, 0, NotSerialized)
                    {
                        Store (GNVS (0x44A4), Local0)
                        If (LLess (Local0, 0x0F))
                        {
                            Increment (Local0)
                        }
                        Else
                        {
                            Store (0x0F, Local0)
                        }

                        SNVS (0x44A4, Local0)
                        STBR ()
                        ATKR (Add (Local0, 0x10))
                    }

                    Method (_Q10, 0, NotSerialized)
                    {
                        If (ATKN (Add (0x33, \_SB.PCI0.SBRG.EC0.STC5 (0x11))))
                        {
                            \_SB.PCI0.SBRG.EC0.STC5 (0x71)
                        }
                    }

                    Method (_Q11, 0, NotSerialized)
                    {
                        Add (\_SB.PCI0.P0P1.VGA.GETN (), 0x60, Local0)
                        Store (\_SB.PCI0.P0P1.VGA.GETM (), Local1)
                        And (Local1, 0x30, Local2)
                        And (Local1, 0x40, Local3)
                        If (LEqual (Local2, 0x30))
                        {
                            Store (Zero, Local1)
                        }
                        Else
                        {
                            If (LEqual (Local3, 0x40))
                            {
                                Store (Zero, Local1)
                            }
                            Else
                            {
                                Store (One, Local1)
                            }
                        }

                        If (Local1)
                        {
                            ATKR (Local0)
                        }
                    }

                    Method (_Q12, 0, NotSerialized)
                    {
                        ATKR (0x6B)
                    }

                    Method (_Q13, 0, NotSerialized)
                    {
                        ATKR (0x32)
                    }

                    Method (_Q14, 0, NotSerialized)
                    {
                        ATKR (0x31)
                    }

                    Method (_Q15, 0, NotSerialized)
                    {
                        ATKR (0x30)
                    }

                    Method (_Q29, 0, NotSerialized)
                    {
                        ATKN (0x5C)
                    }

                    Method (_QA0, 0, NotSerialized)
                    {
                        Sleep (0x01F4)
                        Store (ECCA (), \ACPS)
                        If (\ACPS)
                        {
                            \_SB.ATKD.SPGS (0x02)
                        }
                        Else
                        {
                            \_SB.ATKD.SPGS (0x03)
                        }

                        Notify (\_SB.PCI0.AC0, 0x80)
                        Notify (\_SB.PCI0.BAT0, 0x80)
                        ATKR (Add (0x57, \ACPS))
                    }

                    Method (_QA1, 0, NotSerialized)
                    {
                        If (ECCB (0x01))
                        {
                            Store (0x00, \DCPS)
                        }
                        Else
                        {
                            Store (0x01, \DCPS)
                        }

                        Notify (\_SB.PCI0.BAT0, 0x01)
                        Notify (\_SB.PCI0.BAT0, 0x81)
                        Notify (\_SB.PCI0.AC0, 0x80)
                    }

                    Method (_QA3, 0, NotSerialized)
                    {
                        Notify (\_SB.PCI0.BAT0, 0x80)
                        Notify (\_SB.PCI0.AC0, 0x80)
                    }

                    Method (_QA4, 0, NotSerialized)
                    {
                        If (LNot (ATKR (0x6E)))
                        {
                            Notify (\_SB.PCI0.BAT0, 0x80)
                        }
                    }

                    Method (_QA6, 0, NotSerialized)
                    {
                        \_SB.ATKD.SPGI (0x03)
                    }

                    Method (_QA7, 0, NotSerialized)
                    {
                        If (LGreater (\GNVS (0x8680), 0x03))
                        {
                            \_SB.ATKD.SPGI (0x02)
                        }
                        Else
                        {
                            \_SB.ATKD.SPGS (\GNVS (0x8680))
                        }
                    }

                    Method (_QB0, 0, NotSerialized)
                    {
                        Notify (\_TZ.TZ00, 0x80)
                    }

                    Method (_QB1, 0, NotSerialized)
                    {
                    }

                    Method (_Q80, 0, NotSerialized)
                    {
                        ATKR (0x50)
                    }

                    Method (_Q81, 0, NotSerialized)
                    {
                        ATKR (0x51)
                    }

                    Method (_Q82, 0, NotSerialized)
                    {
                        ATKN (0x5C)
                    }

                    Method (_Q83, 0, NotSerialized)
                    {
                        ATKR (0x6B)
                    }

                    Method (_Q85, 0, NotSerialized)
                    {
                        Notify (\_SB.LID, 0x80)
                    }

                    Method (_Q86, 0, NotSerialized)
                    {
                        Stall (0x64)
                        Notify (\_SB.PCI0.P0P4, 0x01)
                    }
                }

                Scope (\)
                {
                    Name (MNAM, "C90S")
                    Field (\RAMW, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x10), 
                        ACPS,   1, 
                        DCPS,   1, 
                        LCDC,   1, 
                        CPUC,   1, 
                        PLCK,   1, 
                        FANC,   1, 
                        BLTS,   1, 
                        DC2S,   1, 
                        TPMS,   1, 
                        WAPF,   2, 
                                Offset (0xB0), 
                        TRTY,   8, 
                        FSFN,   8, 
                        FSTA,   16, 
                        FADR,   32, 
                        FSIZ,   16, 
                                Offset (0xC0), 
                        QFNS,   32, 
                        FSBS,   32, 
                        TLVL,   32, 
                        VLVL,   32, 
                        SSTS,   32
                    }

                    OperationRegion (\PMIO, SystemIO, 0x0800, 0x80)
                    Field (\PMIO, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x10), 
                        TDTY,   4, 
                        TENA,   1, 
                        TTDT,   4
                    }

                    Method (ATKN, 1, NotSerialized)
                    {
                        If (\_SB.LID._LID ())
                        {
                            Return (ATKR (Arg0))
                        }

                        Return (0x00)
                    }

                    Method (ATKR, 1, NotSerialized)
                    {
                        If (\_SB.ATKP)
                        {
                            Notify (\_SB.ATKD, Arg0)
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Name (P4PR, 0x00)
                    Method (NBFS, 1, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x05))
                        {
                            SNVS (0x81E8, GNVS (0x8078))
                        }

                        ISMI (0x76)
                        Store (PAR0, P4PR)
                    }

                    Method (NBWK, 1, NotSerialized)
                    {
                        If (LNot (GNVS (0x12CE)))
                        {
                            Notify (\_SB.PWRB, 0x02)
                        }

                        Store (P4PR, PAR0)
                        ISMI (0x77)
                    }
                }

                Scope (\_SB)
                {
                    Name (ATKP, Zero)
                    Device (ATKD)
                    {
                        Name (_HID, "ATK0100")
                        Name (_UID, 0x01010100)
                        Method (INIT, 1, NotSerialized)
                        {
                            Store (One, ATKP)
                            Return (\MNAM)
                        }

                        Method (_INI, 0, NotSerialized)
                        {
                            If (\ACPS)
                            {
                                SPGS (0x02)
                            }
                            Else
                            {
                                SPGS (0x03)
                            }

                            Store (0x00, SSTS)
                        }

                        Method (GPLV, 0, NotSerialized)
                        {
                            Return (GNVS (0x44A4))
                        }

                        Method (SPLV, 1, NotSerialized)
                        {
                            SNVS (0x44A4, Arg0)
                            \_SB.PCI0.SBRG.EC0.STBR ()
                        }

                        Scope (\_SB.PCI0.SBRG.EC0)
                        {
                            Name (PWAC, Buffer (0x10)
                            {
                                /* 0000 */    0x1A, 0x2E, 0x47, 0x63, 0x70, 0x79, 0x87, 0x8F, 
                                /* 0008 */    0x97, 0x9E, 0xA8, 0xB3, 0xBA, 0xCF, 0xD9, 0xFF
                            })
                            Name (PWDC, Buffer (0x10)
                            {
                                /* 0000 */    0x1A, 0x2E, 0x3A, 0x4C, 0x5E, 0x66, 0x6E, 0x72, 
                                /* 0008 */    0x80, 0x87, 0x8F, 0x97, 0x9E, 0xA8, 0xB3, 0xCF
                            })
                            Method (STBR, 0, Serialized)
                            {
                                Store (GNVS (0x44A4), Local0)
                                Store (DerefOf (Index (PWAC, Local0)), Local1)
                                If (\LCDC)
                                {
                                    If (LNot (\ACPS))
                                    {
                                        Store (DerefOf (Index (PWDC, Local0)), Local1)
                                    }
                                }

                                \_SB.PCI0.SBRG.EC0.SADC (Local1, 0x84)
                            }
                        }

                        Scope (\_SB)
                        {
                            Device (SLPB)
                            {
                                Name (_HID, EisaId ("PNP0C0E"))
                                Method (_PRW, 0, NotSerialized)
                                {
                                    Return (Package (0x02)
                                    {
                                        0x0A, 
                                        0x04
                                    })
                                }
                            }
                        }

                        Method (TMPR, 0, NotSerialized)
                        {
                            Store (Multiply (\_SB.PCI0.SBRG.EC0.RCTP (), 0x0A), Local0)
                            Divide (\_SB.PCI0.SBRG.EC0.TACH (0x00), 0x64, Local2)
                            Or (Local0, ShiftLeft (Local2, 0x10), Local0)
                            If (\TENA)
                            {
                                Or (ShiftLeft (\TDTY, 0x18), Local0, Local0)
                            }

                            Return (Local0)
                        }

                        Method (SFUN, 0, NotSerialized)
                        {
                            Return (0x0867)
                        }

                        Name (VGPS, 0x00)
                        Name (THOT, 0x00)
                        Method (UPDS, 0, NotSerialized)
                        {
                            ISMI (0xFA)
                            Notify (\_PR.CPU1, 0x80)
                            Notify (\_PR.CPU1, 0x81)
                        }

                        Method (SPGI, 1, NotSerialized)
                        {
                            Name (_T_0, Zero)
                            Store (Arg0, _T_0)
                            If (LEqual (_T_0, 0x00))
                            {
                                Store (0x04, QFNS)
                                Store (0x013F, FSBS)
                                Store (0x00, SSTS)
                                Store (0x01, VLVL)
                                \_SB.ATKD.SPLV (0x0F)
                            }
                            Else
                            {
                                If (LEqual (_T_0, 0x01))
                                {
                                    Store (0x03, QFNS)
                                    Store (0x0125, FSBS)
                                    Store (0x00, SSTS)
                                    Store (0x02, VLVL)
                                    \_SB.ATKD.SPLV (0x0F)
                                }
                                Else
                                {
                                    If (LEqual (_T_0, 0x02))
                                    {
                                        Store (0x010A, FSBS)
                                        Store (0x03, VLVL)
                                        If (\ACPS)
                                        {
                                            Store (0x02, QFNS)
                                            Store (0x00, SSTS)
                                        }
                                        Else
                                        {
                                            Store (0x01, QFNS)
                                            Store (0x01, SSTS)
                                        }

                                        \_SB.ATKD.SPLV (0x0F)
                                    }
                                    Else
                                    {
                                        If (LEqual (_T_0, 0x03))
                                        {
                                            Store (0x00, QFNS)
                                            Store (0xAF, FSBS)
                                            Store (0x01, SSTS)
                                            Store (0x04, VLVL)
                                            \_SB.ATKD.SPLV (0x05)
                                        }
                                    }
                                }
                            }

                            UPDS ()
                        }

                        Method (SPGS, 1, NotSerialized)
                        {
                            SNVS (0x8680, 0xFF)
                            SPGI (Arg0)
                            Sleep (0x01F4)
                            SNVS (0x8680, Arg0)
                            Return (One)
                        }

                        Method (SFRQ, 1, NotSerialized)
                        {
                            Return (0x00)
                        }

                        Method (GFRQ, 1, NotSerialized)
                        {
                            Return (0x00)
                        }

                        Method (SDSP, 1, NotSerialized)
                        {
                            \_SB.PCI0.P0P1.VGA.SWHD (Arg0)
                        }

                        Name (ECSF, 0x00)
                        Method (ECSR, 1, NotSerialized)
                        {
                            Store (One, ECSF)
                            If (LEqual (Arg0, 0x01))
                            {
                                Store (One, Local0)
                            }
                            Else
                            {
                                If (LEqual (Arg0, 0x02))
                                {
                                    Store (One, Local0)
                                    \SNVS (0x15FD, Local0)
                                }
                                Else
                                {
                                    Store (Zero, Local0)
                                }
                            }

                            Return (Local0)
                        }

                        Method (FSMI, 1, NotSerialized)
                        {
                            Store (Arg0, \FSFN)
                            Or (Arg0, 0xA0, Local0)
                            ISMI (0x90)
                            Return (\FSTA)
                        }

                        Method (FLSH, 1, NotSerialized)
                        {
                            Store (Arg0, \FSTA)
                            FSMI (0x00)
                        }

                        Method (FINI, 1, NotSerialized)
                        {
                            If (ECSF)
                            {
                                Store (Arg0, \FADR)
                                Store (FSMI (0x01), Local0)
                            }
                            Else
                            {
                                Store (Zero, Local0)
                            }

                            Return (Local0)
                        }

                        Method (FERS, 1, NotSerialized)
                        {
                            Store (Arg0, \FSTA)
                            Return (FSMI (0x02))
                        }

                        Method (FWRI, 1, NotSerialized)
                        {
                            Store (Arg0, \FADR)
                            Store (0x1000, \FSIZ)
                            Return (Subtract (0x1000, FSMI (0x03)))
                        }

                        Method (FWRP, 0, NotSerialized)
                        {
                            Store (0x00, \FSIZ)
                            Return (Subtract (0x1000, FSMI (0x03)))
                        }

                        Method (FEBW, 1, NotSerialized)
                        {
                            Store (0x84, DBG8)
                            Store (Arg0, \FADR)
                            Return (FSMI (0x04))
                        }

                        Method (FEBR, 1, NotSerialized)
                        {
                            Store (0x85, DBG8)
                            Store (Arg0, \FADR)
                            Return (FSMI (0x05))
                        }

                        Method (FEDW, 0, NotSerialized)
                        {
                            Store (0x86, DBG8)
                            Return (FSMI (0x06))
                        }

                        Method (WLED, 1, NotSerialized)
                        {
                            Store (\GNVS (0x22C9), Local0)
                            And (Local0, 0x02, Local0)
                            Or (Local0, Arg0, Local0)
                            \SNVS (0x22C9, Local0)
                            If (Arg0)
                            {
                                Or (\_SB.PCI0.SBRG.WLED, 0x01, \_SB.PCI0.SBRG.WLED)
                                Or (\_SB.PCI0.SBRG.WCTL, 0x01, \_SB.PCI0.SBRG.WCTL)
                            }
                            Else
                            {
                                And (\_SB.PCI0.SBRG.WLED, 0x00, \_SB.PCI0.SBRG.WLED)
                                And (\_SB.PCI0.SBRG.WCTL, 0x00, \_SB.PCI0.SBRG.WCTL)
                            }

                            Return (One)
                        }

                        Method (BLED, 1, NotSerialized)
                        {
                            Store (\GNVS (0x22CB), Local0)
                            And (Local0, 0x02, Local0)
                            Or (Local0, Arg0, Local0)
                            \SNVS (0x22CB, Local0)
                            If (Arg0)
                            {
                                Or (\_SB.PCI0.SBRG.BCTL, 0x01, \_SB.PCI0.SBRG.BCTL)
                            }
                            Else
                            {
                                And (\_SB.PCI0.SBRG.BCTL, 0x00, \_SB.PCI0.SBRG.BCTL)
                            }

                            Return (One)
                        }

                        Method (MLED, 1, NotSerialized)
                        {
                            If (Arg0)
                            {
                                \_SB.PCI0.SBRG.EC0.SPIN (0x1A, 0x00)
                            }
                            Else
                            {
                                \_SB.PCI0.SBRG.EC0.SPIN (0x1A, 0x01)
                            }
                        }

                        Method (ANVI, 1, NotSerialized)
                        {
                            Name (_T_0, Zero)
                            Store (Arg0, _T_0)
                            If (LEqual (_T_0, 0x01))
                            {
                                Return (0x01)
                            }
                            Else
                            {
                                If (LEqual (_T_0, 0x02))
                                {
                                    Store (\GNVS (0x0608), Local0)
                                    Return (Local0)
                                }
                                Else
                                {
                                    Return (0x00)
                                }
                            }
                        }

                        Method (RDDT, 0, Serialized)
                        {
                            Store (\_TZ.RSYS (), Local0)
                            And (Local0, 0xFF, Local0)
                            ShiftLeft (Local0, 0x08, Local0)
                            Store (\_TZ.RTMP (), Local1)
                            And (Local1, 0xFF, Local1)
                            Add (Local0, Local1, Local0)
                            ShiftLeft (Local0, 0x10, Local0)
                            Return (Local0)
                        }

                        Method (CWAP, 1, NotSerialized)
                        {
                            Store (\WAPF, Local0)
                            Name (_T_0, Zero)
                            Store (Arg0, _T_0)
                            If (LEqual (_T_0, 0x01))
                            {
                                Or (Local0, 0x01, Local0)
                            }
                            Else
                            {
                                If (LEqual (_T_0, 0x04))
                                {
                                    Or (Local0, 0x02, Local0)
                                }
                                Else
                                {
                                }
                            }

                            Store (Local0, \WAPF)
                            Return (One)
                        }

                        Method (RSTS, 0, NotSerialized)
                        {
                            Store (0x00, Local0)
                            Store (\GNVS (0x22C9), Local1)
                            If (And (Local1, 0x01))
                            {
                                Or (Local0, 0x01, Local0)
                            }

                            Store (\GNVS (0x22CB), Local1)
                            If (And (Local1, 0x01))
                            {
                                Or (Local0, 0x02, Local0)
                            }

                            If (LOr (LEqual (\WAPF, 0x01), LEqual (\WAPF, 0x00)))
                            {
                                Store (0x0300, Local0)
                            }

                            Return (Local0)
                        }

                        Method (HWRS, 0, NotSerialized)
                        {
                            Store (0x00, Local0)
                            Store (\GNVS (0x22C9), Local1)
                            If (And (Local1, 0x02))
                            {
                                Or (Local0, 0x80, Local0)
                            }

                            Store (\GNVS (0x22CB), Local1)
                            If (And (Local1, 0x02))
                            {
                                Or (Local0, 0x0100, Local0)
                            }

                            Return (Local0)
                        }

                        Method (GSTS, 0, NotSerialized)
                        {
                            Return (0x00)
                        }

                        Name (MBIF, Package (0x08)
                        {
                            0x03, 
                            "C90S", 
                            0x00, 
                            0x01000000, 
                            0xE0010001, 
                            0x00, 
                            0x00, 
                            0x00
                        })
                        Name (ASBF, Buffer (0x08)
                        {
                            /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00
                        })
                        CreateDWordField (ASBF, 0x00, ASB0)
                        CreateDWordField (ASBF, 0x04, ASB1)
                        Method (GGRP, 1, Serialized)
                        {
                            Name (_T_0, Zero)
                            Store (Arg0, _T_0)
                            If (LEqual (_T_0, 0x03))
                            {
                                Return (GRP3)
                            }
                            Else
                            {
                                If (LEqual (_T_0, 0x0B))
                                {
                                    Return (GRPB)
                                }
                                Else
                                {
                                    Return (0x00)
                                }
                            }
                        }

                        Method (GITM, 1, Serialized)
                        {
                            CreateDWordField (Arg0, 0x00, PRM0)
                            CreateByteField (Arg0, 0x03, GPID)
                            Store (0x01, ASB0)
                            Name (_T_0, Zero)
                            Store (GPID, _T_0)
                            If (LEqual (_T_0, 0x03))
                            {
                                GIT3 (PRM0)
                            }
                            Else
                            {
                                If (LEqual (_T_0, 0x0B))
                                {
                                    GITB (PRM0)
                                }
                                Else
                                {
                                    Store (0x00, ASB0)
                                }
                            }

                            Return (ASBF)
                        }

                        Method (SITM, 1, Serialized)
                        {
                            CreateDWordField (Arg0, 0x00, PRM0)
                            CreateDWordField (Arg0, 0x04, PRM1)
                            CreateDWordField (Arg0, 0x08, PRM2)
                            CreateByteField (Arg0, 0x03, GPID)
                            Store (0x01, ASB0)
                            Name (_T_0, Zero)
                            Store (GPID, _T_0)
                            If (LEqual (_T_0, 0x03))
                            {
                                SIT3 (PRM0, PRM1, PRM2)
                            }
                            Else
                            {
                                If (LEqual (_T_0, 0x0B))
                                {
                                    SITB (PRM0, PRM1, PRM2)
                                }
                                Else
                                {
                                    Store (0x00, ASB0)
                                }
                            }

                            Return (ASBF)
                        }

                        Name (GBT0, Package (0x07)
                        {
                            0x0B060001, 
                            "System performance", 
                            0x00400000, 
                            0x00, 
                            0x03, 
                            0x01, 
                            0x04
                        })
                        Name (G3T0, Package (0x07)
                        {
                            0x03010011, 
                            "CPU FSB frequency", 
                            0x00, 
                            0x00, 
                            0x4E20, 
                            0x64, 
                            0x92
                        })
                        Name (GRPB, Package (0x01)
                        {
                            GBT0
                        })
                        Name (GRP3, Package (0x01)
                        {
                            G3T0
                        })
                        Method (GIT3, 1, NotSerialized)
                        {
                            Name (_T_0, Zero)
                            Store (And (Arg0, 0xFFFF), _T_0)
                            If (LEqual (_T_0, 0x11))
                            {
                                If (LEqual (\GNVS (0x15E9), 0x01))
                                {
                                    SNVS (0x15E9, 0x00)
                                    Store (\GNVS (0x92C0), Local0)
                                    SNVS (0x15E9, 0x01)
                                }
                                Else
                                {
                                    SNVS (0x15E9, 0x00)
                                    Store (\GNVS (0x92C0), Local0)
                                }

                                If (LGreater (Local0, 0x0159))
                                {
                                    Store (0x010A, Local0)
                                }

                                Subtract (Local0, 0xC8, Local1)
                                Store (Local1, ASB1)
                            }
                            Else
                            {
                                Store (0x00, ASB0)
                            }
                        }

                        Method (SIT3, 3, NotSerialized)
                        {
                            Name (_T_0, Zero)
                            Store (And (Arg0, 0xFFFF), _T_0)
                            If (LEqual (_T_0, 0x11))
                            {
                                If (Arg2)
                                {
                                    Add (Arg1, 0xC8, Local0)
                                    SNVS (0x15E9, 0x00)
                                    SNVS (0x92C0, Local0)
                                }

                                Store (0x03, ASB0)
                            }
                            Else
                            {
                                Store (0x00, ASB0)
                            }
                        }

                        Method (GITB, 1, NotSerialized)
                        {
                            Name (_T_0, Zero)
                            Store (And (Arg0, 0xFFFF), _T_0)
                            If (LEqual (_T_0, 0x01))
                            {
                                If (LGreater (\GNVS (0x8680), 0x03))
                                {
                                    Store (0x02, ASB1)
                                }
                                Else
                                {
                                    Store (\GNVS (0x8680), ASB1)
                                }
                            }
                            Else
                            {
                                Store (0x00, ASB0)
                            }
                        }

                        Method (SITB, 3, NotSerialized)
                        {
                            Name (_T_0, Zero)
                            Store (And (Arg0, 0xFFFF), _T_0)
                            If (LEqual (_T_0, 0x01))
                            {
                                If (Arg2)
                                {
                                    SPGS (Arg1)
                                }

                                If (LEqual (Arg1, 0x00))
                                {
                                    If (\ACPS)
                                    {
                                        Store (\GNVS (0x8678), Local0)
                                        If (LGreater (Local0, 0x01))
                                        {
                                            Store (0x01, ASB0)
                                        }
                                        Else
                                        {
                                            Store (0x05, ASB0)
                                        }
                                    }
                                    Else
                                    {
                                        Store (0x05, ASB0)
                                    }

                                    If (LEqual (\_SB.PCI0.P0P1.VGA.VGAD, 0x039710DE))
                                    {
                                        Store (0x05, ASB0)
                                    }
                                }
                                Else
                                {
                                    If (LEqual (Arg1, 0x01))
                                    {
                                        If (\ACPS)
                                        {
                                            Store (\GNVS (0x8678), Local0)
                                            If (LGreater (Local0, 0x00))
                                            {
                                                Store (0x01, ASB0)
                                            }
                                            Else
                                            {
                                                Store (0x05, ASB0)
                                            }
                                        }
                                        Else
                                        {
                                            Store (0x05, ASB0)
                                        }
                                    }
                                    Else
                                    {
                                        Store (0x01, ASB0)
                                    }
                                }
                            }
                            Else
                            {
                                Store (0x00, ASB0)
                            }
                        }
                    }
                }

                Scope (\_SB.PCI0)
                {
                    Device (BAT0)
                    {
                        Name (_HID, EisaId ("PNP0C0A"))
                        Name (_UID, 0x00)
                        Name (_PCL, Package (0x01)
                        {
                            \_SB.PCI0
                        })
                        Method (_STA, 0, NotSerialized)
                        {
                            If (ECCB (0x01))
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
                            If (And (0x10, _STA ()))
                            {
                                CBIF (0x00)
                            }

                            Return (PBIF)
                        }

                        Method (_BST, 0, NotSerialized)
                        {
                            If (And (0x10, _STA ()))
                            {
                                CBST (0x00)
                            }

                            Return (PBST)
                        }
                    }

                    Name (NBIF, Package (0x0D)
                    {
                        0x01, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0x01, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        " ", 
                        " ", 
                        " ", 
                        " "
                    })
                    Name (PBIF, Package (0x0D)
                    {
                        0x01, 
                        0x10CC, 
                        0x1068, 
                        0x01, 
                        0x36D0, 
                        0x01A4, 
                        0xD2, 
                        0x1C, 
                        0x050A, 
                        "C90S", 
                        " ", 
                        "LION", 
                        "ASUS"
                    })
                    Name (BATF, Buffer (0x02) {})
                    CreateWordField (BATF, 0x00, DATW)
                    Method (CBIF, 1, Serialized)
                    {
                        Store (ECDC (0x01), DATW)
                        If (LNotEqual (DATW, Ones))
                        {
                            Store (DATW, Index (PBIF, 0x01))
                        }

                        Store (Arg0, Index (PBIF, 0x03))
                        Store (ECFC (0x01), DATW)
                        If (LNotEqual (DATW, Ones))
                        {
                            Store (DATW, Index (PBIF, 0x02))
                            Divide (DATW, 0x0A, Local1, Local2)
                            Store (Local2, Index (PBIF, 0x05))
                            Divide (DATW, 0x14, Local1, Local2)
                            Store (Local2, Index (PBIF, 0x06))
                            Divide (Local2, 0x64, Local1, Local2)
                            Store (Local2, Index (PBIF, 0x07))
                            Multiply (Local2, 0x12, Local1)
                            Store (Local1, Index (PBIF, 0x08))
                        }

                        Store (ECDV (0x01), DATW)
                        If (LNotEqual (DATW, Ones))
                        {
                            Store (DATW, Index (PBIF, 0x04))
                        }
                    }

                    Name (PBST, Package (0x04)
                    {
                        0x00, 
                        0x8000, 
                        0x8000, 
                        0x36B0
                    })
                    Method (CBST, 1, Serialized)
                    {
                        Store (ECBC (0x01), DATW)
                        If (LNotEqual (DATW, Ones))
                        {
                            If (And (DATW, 0x8000))
                            {
                                Decrement (DATW)
                                Not (DATW, DATW)
                            }

                            Store (DATW, Index (PBST, 0x01))
                        }

                        Store (0x00, Local0)
                        If (\ACPS)
                        {
                            Store (ECGS (0x01), Local0)
                        }
                        Else
                        {
                            Store (0x01, Local0)
                        }

                        Store (Local0, Index (PBST, 0x00))
                        If (And (ECGS (0x01), 0x10))
                        {
                            Store (ECFC (0x01), DATW)
                        }
                        Else
                        {
                            Store (ECRC (0x01), DATW)
                        }

                        If (LNotEqual (DATW, Ones))
                        {
                            Store (DATW, Index (PBST, 0x02))
                        }

                        Store (ECPV (0x01), DATW)
                        If (LNotEqual (DATW, Ones))
                        {
                            Store (DATW, Index (PBST, 0x03))
                        }
                    }
                }

                Scope (\_SB)
                {
                    Scope (PCI0)
                    {
                        Device (AC0)
                        {
                            Name (_HID, "ACPI0003")
                            Method (_PSR, 0, NotSerialized)
                            {
                                Return (\ACPS)
                            }

                            Name (_PCL, Package (0x01)
                            {
                                \_SB.PCI0
                            })
                        }
                    }
                }
            }

            Device (IDE0)
            {
                Name (_ADR, 0x001F0002)
                Name (\_SB.PCI0.NATA, Package (0x01)
                {
                    0x001F0002
                })
                Name (REGF, 0x01)
                Method (_REG, 2, NotSerialized)
                {
                    If (LEqual (Arg0, 0x02))
                    {
                        Store (Arg1, REGF)
                    }
                }

                Name (TIM0, Package (0x08)
                {
                    Package (0x04)
                    {
                        0x78, 
                        0xB4, 
                        0xF0, 
                        0x0384
                    }, 

                    Package (0x04)
                    {
                        0x23, 
                        0x21, 
                        0x10, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0B, 
                        0x09, 
                        0x04, 
                        0x00
                    }, 

                    Package (0x06)
                    {
                        0x70, 
                        0x49, 
                        0x36, 
                        0x27, 
                        0x19, 
                        0x14
                    }, 

                    Package (0x06)
                    {
                        0x00, 
                        0x01, 
                        0x02, 
                        0x01, 
                        0x02, 
                        0x01
                    }, 

                    Package (0x06)
                    {
                        0x00, 
                        0x00, 
                        0x00, 
                        0x01, 
                        0x01, 
                        0x01
                    }, 

                    Package (0x04)
                    {
                        0x04, 
                        0x03, 
                        0x02, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x02, 
                        0x01, 
                        0x00, 
                        0x00
                    }
                })
                Name (TMD0, Buffer (0x14) {})
                CreateDWordField (TMD0, 0x00, PIO0)
                CreateDWordField (TMD0, 0x04, DMA0)
                CreateDWordField (TMD0, 0x08, PIO1)
                CreateDWordField (TMD0, 0x0C, DMA1)
                CreateDWordField (TMD0, 0x10, CHNF)
                OperationRegion (CFG2, PCI_Config, 0x40, 0x20)
                Field (CFG2, DWordAcc, NoLock, Preserve)
                {
                    PMPT,   4, 
                    PSPT,   4, 
                    PMRI,   6, 
                            Offset (0x02), 
                    SMPT,   4, 
                    SSPT,   4, 
                    SMRI,   6, 
                            Offset (0x04), 
                    PSRI,   4, 
                    SSRI,   4, 
                            Offset (0x08), 
                    PM3E,   1, 
                    PS3E,   1, 
                    SM3E,   1, 
                    SS3E,   1, 
                            Offset (0x0A), 
                    PMUT,   2, 
                        ,   2, 
                    PSUT,   2, 
                            Offset (0x0B), 
                    SMUT,   2, 
                        ,   2, 
                    SSUT,   2, 
                            Offset (0x0C), 
                            Offset (0x14), 
                    PM6E,   1, 
                    PS6E,   1, 
                    SM6E,   1, 
                    SS6E,   1, 
                    PMCR,   1, 
                    PSCR,   1, 
                    SMCR,   1, 
                    SSCR,   1, 
                        ,   4, 
                    PMAE,   1, 
                    PSAE,   1, 
                    SMAE,   1, 
                    SSAE,   1
                }

                Name (GMPT, 0x00)
                Name (GMUE, 0x00)
                Name (GMUT, 0x00)
                Name (GMCR, 0x00)
                Name (GSPT, 0x00)
                Name (GSUE, 0x00)
                Name (GSUT, 0x00)
                Name (GSCR, 0x00)
                Device (CHN0)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        ShiftLeft (PSCR, 0x01, Local1)
                        Or (PMCR, Local1, Local0)
                        ShiftLeft (PMAE, 0x02, Local3)
                        ShiftLeft (PM6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (PM3E, Local3, Local1)
                        ShiftLeft (PMPT, 0x04, Local3)
                        Or (Local1, Local3, Local1)
                        ShiftLeft (PSAE, 0x02, Local3)
                        ShiftLeft (PS6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (PS3E, Local3, Local2)
                        ShiftLeft (PSPT, 0x04, Local3)
                        Or (Local2, Local3, Local2)
                        Return (GTM (PMRI, Local1, PMUT, PSRI, Local2, PSUT, Local0))
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, Debug)
                        Store (Arg0, TMD0)
                        ShiftLeft (PMAE, 0x02, Local3)
                        ShiftLeft (PM6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (PM3E, Local3, Local0)
                        ShiftLeft (PMPT, 0x04, Local3)
                        Or (Local0, Local3, Local0)
                        ShiftLeft (PSAE, 0x02, Local3)
                        ShiftLeft (PS6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (PS3E, Local3, Local1)
                        ShiftLeft (PSPT, 0x04, Local3)
                        Or (Local1, Local3, Local1)
                        Store (PMRI, GMPT)
                        Store (Local0, GMUE)
                        Store (PMUT, GMUT)
                        Store (PMCR, GMCR)
                        Store (PSRI, GSPT)
                        Store (Local1, GSUE)
                        Store (PSUT, GSUT)
                        Store (PSCR, GSCR)
                        STM ()
                        Store (GMPT, PMRI)
                        Store (GMUE, Local0)
                        Store (GMUT, PMUT)
                        Store (GMCR, PMCR)
                        Store (GSUE, Local1)
                        Store (GSUT, PSUT)
                        Store (GSCR, PSCR)
                        If (And (Local0, 0x01))
                        {
                            Store (0x01, PM3E)
                        }
                        Else
                        {
                            Store (0x00, PM3E)
                        }

                        If (And (Local0, 0x02))
                        {
                            Store (0x01, PM6E)
                        }
                        Else
                        {
                            Store (0x00, PM6E)
                        }

                        If (And (Local0, 0x04))
                        {
                            Store (0x01, PMAE)
                        }
                        Else
                        {
                            Store (0x00, PMAE)
                        }

                        If (And (Local1, 0x01))
                        {
                            Store (0x01, PS3E)
                        }
                        Else
                        {
                            Store (0x00, PS3E)
                        }

                        If (And (Local1, 0x02))
                        {
                            Store (0x01, PS6E)
                        }
                        Else
                        {
                            Store (0x00, PS6E)
                        }

                        If (And (Local1, 0x04))
                        {
                            Store (0x01, PSAE)
                        }
                        Else
                        {
                            Store (0x00, PSAE)
                        }

                        Store (GTF (0x00, Arg1), ATA0)
                        Store (GTF (0x01, Arg2), ATA1)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Return (RATA (ATA0))
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Return (RATA (ATA1))
                        }
                    }
                }

                Device (CHN1)
                {
                    Name (_ADR, 0x01)
                    Method (_GTM, 0, NotSerialized)
                    {
                        ShiftLeft (SSCR, 0x01, Local1)
                        Or (SMCR, Local1, Local0)
                        ShiftLeft (SMAE, 0x02, Local3)
                        ShiftLeft (SM6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (SM3E, Local3, Local1)
                        ShiftLeft (SMPT, 0x04, Local3)
                        Or (Local1, Local3, Local1)
                        ShiftLeft (SSAE, 0x02, Local3)
                        ShiftLeft (SS6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (SS3E, Local3, Local2)
                        ShiftLeft (SSPT, 0x04, Local3)
                        Or (Local2, Local3, Local2)
                        Return (GTM (SMRI, Local1, SMUT, SSRI, Local2, SSUT, Local0))
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, Debug)
                        Store (Arg0, TMD0)
                        ShiftLeft (SMAE, 0x02, Local3)
                        ShiftLeft (SM6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (SM3E, Local3, Local0)
                        ShiftLeft (SMPT, 0x04, Local3)
                        Or (Local0, Local3, Local0)
                        ShiftLeft (SSAE, 0x02, Local3)
                        ShiftLeft (SS6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (SS3E, Local3, Local1)
                        ShiftLeft (SSPT, 0x04, Local3)
                        Or (Local1, Local3, Local1)
                        Store (SMRI, GMPT)
                        Store (Local0, GMUE)
                        Store (SMUT, GMUT)
                        Store (SMCR, GMCR)
                        Store (SSRI, GSPT)
                        Store (Local1, GSUE)
                        Store (SSUT, GSUT)
                        Store (SSCR, GSCR)
                        STM ()
                        Store (GMPT, SMRI)
                        Store (GMUE, Local0)
                        Store (GMUT, SMUT)
                        Store (GMCR, SMCR)
                        Store (GSUE, Local1)
                        Store (GSUT, SSUT)
                        Store (GSCR, SSCR)
                        If (And (Local0, 0x01))
                        {
                            Store (0x01, SM3E)
                        }
                        Else
                        {
                            Store (0x00, SM3E)
                        }

                        If (And (Local0, 0x02))
                        {
                            Store (0x01, SM6E)
                        }
                        Else
                        {
                            Store (0x00, SM6E)
                        }

                        If (And (Local0, 0x04))
                        {
                            Store (0x01, SMAE)
                        }
                        Else
                        {
                            Store (0x00, SMAE)
                        }

                        If (And (Local1, 0x01))
                        {
                            Store (0x01, SS3E)
                        }
                        Else
                        {
                            Store (0x00, SS3E)
                        }

                        If (And (Local1, 0x02))
                        {
                            Store (0x01, SS6E)
                        }
                        Else
                        {
                            Store (0x00, SS6E)
                        }

                        If (And (Local1, 0x04))
                        {
                            Store (0x01, SSAE)
                        }
                        Else
                        {
                            Store (0x00, SSAE)
                        }

                        Store (GTF (0x00, Arg1), ATA2)
                        Store (GTF (0x01, Arg2), ATA3)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Return (RATA (ATA2))
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Return (RATA (ATA3))
                        }
                    }
                }

                Method (GTM, 7, Serialized)
                {
                    Store (Ones, PIO0)
                    Store (Ones, PIO1)
                    Store (Ones, DMA0)
                    Store (Ones, DMA1)
                    Store (0x10, CHNF)
                    If (REGF) {}
                    Else
                    {
                        Return (TMD0)
                    }

                    If (And (Arg1, 0x20))
                    {
                        Or (CHNF, 0x02, CHNF)
                    }

                    Store (Match (DerefOf (Index (TIM0, 0x01)), MEQ, Arg0, MTR, 
                        0x00, 0x00), Local6)
                    Store (DerefOf (Index (DerefOf (Index (TIM0, 0x00)), Local6)), 
                        Local7)
                    Store (Local7, DMA0)
                    Store (Local7, PIO0)
                    If (And (Arg4, 0x20))
                    {
                        Or (CHNF, 0x08, CHNF)
                    }

                    Store (Match (DerefOf (Index (TIM0, 0x02)), MEQ, Arg3, MTR, 
                        0x00, 0x00), Local6)
                    Store (DerefOf (Index (DerefOf (Index (TIM0, 0x00)), Local6)), 
                        Local7)
                    Store (Local7, DMA1)
                    Store (Local7, PIO1)
                    If (And (Arg1, 0x07))
                    {
                        Store (Arg2, Local5)
                        If (And (Arg1, 0x02))
                        {
                            Add (Local5, 0x02, Local5)
                        }

                        If (And (Arg1, 0x04))
                        {
                            Add (Local5, 0x04, Local5)
                        }

                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x03)), Local5)), 
                            DMA0)
                        Or (CHNF, 0x01, CHNF)
                    }

                    If (And (Arg4, 0x07))
                    {
                        Store (Arg5, Local5)
                        If (And (Arg4, 0x02))
                        {
                            Add (Local5, 0x02, Local5)
                        }

                        If (And (Arg4, 0x04))
                        {
                            Add (Local5, 0x04, Local5)
                        }

                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x03)), Local5)), 
                            DMA1)
                        Or (CHNF, 0x04, CHNF)
                    }

                    Store (TMD0, Debug)
                    Return (TMD0)
                }

                Method (STM, 0, Serialized)
                {
                    If (REGF) {}
                    Else
                    {
                        Store (0x00, GMUE)
                        Store (0x00, GMUT)
                        Store (0x00, GSUE)
                        Store (0x00, GSUT)
                        If (And (CHNF, 0x01))
                        {
                            Store (Match (DerefOf (Index (TIM0, 0x03)), MLE, DMA0, MTR, 
                                0x00, 0x00), Local0)
                            If (LGreater (Local0, 0x05))
                            {
                                Store (0x05, Local0)
                            }

                            Store (DerefOf (Index (DerefOf (Index (TIM0, 0x04)), Local0)), 
                                GMUT)
                            Or (GMUE, 0x01, GMUE)
                            If (LGreater (Local0, 0x02))
                            {
                                Or (GMUE, 0x02, GMUE)
                            }

                            If (LGreater (Local0, 0x04))
                            {
                                And (GMUE, 0xFD, GMUE)
                                Or (GMUE, 0x04, GMUE)
                            }
                        }
                        Else
                        {
                            If (Or (LEqual (PIO0, Ones), LEqual (PIO0, 0x00)))
                            {
                                If (And (LLess (DMA0, Ones), LGreater (DMA0, 0x00)))
                                {
                                    Store (DMA0, PIO0)
                                    Or (GMUE, 0x80, GMUE)
                                }
                            }
                        }

                        If (And (CHNF, 0x04))
                        {
                            Store (Match (DerefOf (Index (TIM0, 0x03)), MLE, DMA1, MTR, 
                                0x00, 0x00), Local0)
                            If (LGreater (Local0, 0x05))
                            {
                                Store (0x05, Local0)
                            }

                            Store (DerefOf (Index (DerefOf (Index (TIM0, 0x04)), Local0)), 
                                GSUT)
                            Or (GSUE, 0x01, GSUE)
                            If (LGreater (Local0, 0x02))
                            {
                                Or (GSUE, 0x02, GSUE)
                            }

                            If (LGreater (Local0, 0x04))
                            {
                                And (GSUE, 0xFD, GSUE)
                                Or (GSUE, 0x04, GSUE)
                            }
                        }
                        Else
                        {
                            If (Or (LEqual (PIO1, Ones), LEqual (PIO1, 0x00)))
                            {
                                If (And (LLess (DMA1, Ones), LGreater (DMA1, 0x00)))
                                {
                                    Store (DMA1, PIO1)
                                    Or (GSUE, 0x80, GSUE)
                                }
                            }
                        }

                        If (And (CHNF, 0x02))
                        {
                            Or (GMUE, 0x20, GMUE)
                        }

                        If (And (CHNF, 0x08))
                        {
                            Or (GSUE, 0x20, GSUE)
                        }

                        And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIO0, MTR, 
                            0x00, 0x00), 0x07, Local0)
                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x01)), Local0)), 
                            Local1)
                        Store (Local1, GMPT)
                        If (LLess (Local0, 0x03))
                        {
                            Or (GMUE, 0x50, GMUE)
                        }

                        And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIO1, MTR, 
                            0x00, 0x00), 0x07, Local0)
                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x02)), Local0)), 
                            Local1)
                        Store (Local1, GSPT)
                        If (LLess (Local0, 0x03))
                        {
                            Or (GSUE, 0x50, GSUE)
                        }
                    }
                }

                Name (AT01, Buffer (0x07)
                {
                    0x03, 0x00, 0x00, 0x00, 0x00, 0x00, 0xEF
                })
                Name (AT02, Buffer (0x07)
                {
                    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x90
                })
                Name (AT03, Buffer (0x07)
                {
                    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xC6
                })
                Name (AT04, Buffer (0x07)
                {
                    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x91
                })
                Name (ATA0, Buffer (0x1D) {})
                Name (ATA1, Buffer (0x1D) {})
                Name (ATA2, Buffer (0x1D) {})
                Name (ATA3, Buffer (0x1D) {})
                Name (ATAB, Buffer (0x1D) {})
                CreateByteField (ATAB, 0x00, CMDC)
                Method (GTFB, 3, Serialized)
                {
                    Multiply (CMDC, 0x38, Local0)
                    Add (Local0, 0x08, Local1)
                    CreateField (ATAB, Local1, 0x38, CMDX)
                    Multiply (CMDC, 0x07, Local0)
                    CreateByteField (ATAB, Add (Local0, 0x02), A001)
                    CreateByteField (ATAB, Add (Local0, 0x06), A005)
                    Store (Arg0, CMDX)
                    Store (Arg1, A001)
                    Store (Arg2, A005)
                    Increment (CMDC)
                }

                Method (GTF, 2, Serialized)
                {
                    Store (Arg1, Debug)
                    Store (0x00, CMDC)
                    Name (ID49, 0x0C00)
                    Name (ID59, 0x00)
                    Name (ID53, 0x04)
                    Name (ID63, 0x0F00)
                    Name (ID88, 0x0F00)
                    Name (IRDY, 0x01)
                    Name (PIOT, 0x00)
                    Name (DMAT, 0x00)
                    If (LEqual (SizeOf (Arg1), 0x0200))
                    {
                        CreateWordField (Arg1, 0x62, IW49)
                        Store (IW49, ID49)
                        CreateWordField (Arg1, 0x6A, IW53)
                        Store (IW53, ID53)
                        CreateWordField (Arg1, 0x7E, IW63)
                        Store (IW63, ID63)
                        CreateWordField (Arg1, 0x76, IW59)
                        Store (IW59, ID59)
                        CreateWordField (Arg1, 0xB0, IW88)
                        Store (IW88, ID88)
                    }

                    Store (0xA0, Local7)
                    If (Arg0)
                    {
                        Store (0xB0, Local7)
                        And (CHNF, 0x08, IRDY)
                        If (And (CHNF, 0x10))
                        {
                            Store (PIO1, PIOT)
                        }
                        Else
                        {
                            Store (PIO0, PIOT)
                        }

                        If (And (CHNF, 0x04))
                        {
                            If (And (CHNF, 0x10))
                            {
                                Store (DMA1, DMAT)
                            }
                            Else
                            {
                                Store (DMA0, DMAT)
                            }
                        }
                    }
                    Else
                    {
                        And (CHNF, 0x02, IRDY)
                        Store (PIO0, PIOT)
                        If (And (CHNF, 0x01))
                        {
                            Store (DMA0, DMAT)
                        }
                    }

                    If (LAnd (LAnd (And (ID53, 0x04), And (ID88, 0xFF00
                        )), DMAT))
                    {
                        Store (Match (DerefOf (Index (TIM0, 0x03)), MLE, DMAT, MTR, 
                            0x00, 0x00), Local1)
                        If (LGreater (Local1, 0x05))
                        {
                            Store (0x05, Local1)
                        }

                        GTFB (AT01, Or (0x40, Local1), Local7)
                    }
                    Else
                    {
                        If (LAnd (And (ID63, 0xFF00), PIOT))
                        {
                            And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIOT, MTR, 
                                0x00, 0x00), 0x03, Local0)
                            Or (0x20, DerefOf (Index (DerefOf (Index (TIM0, 0x07)), Local0
                                )), Local1)
                            GTFB (AT01, Local1, Local7)
                        }
                    }

                    If (IRDY)
                    {
                        And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIOT, MTR, 
                            0x00, 0x00), 0x07, Local0)
                        Or (0x08, DerefOf (Index (DerefOf (Index (TIM0, 0x06)), Local0
                            )), Local1)
                        GTFB (AT01, Local1, Local7)
                    }
                    Else
                    {
                        If (And (ID49, 0x0400))
                        {
                            GTFB (AT01, 0x01, Local7)
                        }
                    }

                    If (LAnd (And (ID59, 0x0100), And (ID59, 0xFF)))
                    {
                        GTFB (AT03, And (ID59, 0xFF), Local7)
                    }

                    Store (ATAB, Debug)
                    Return (ATAB)
                }

                Method (RATA, 1, NotSerialized)
                {
                    CreateByteField (Arg0, 0x00, CMDN)
                    Multiply (CMDN, 0x38, Local0)
                    CreateField (Arg0, 0x08, Local0, RETB)
                    Store (RETB, Debug)
                    Return (RETB)
                }
            }

            Device (IDE1)
            {
                Name (_ADR, 0x001F0001)
                Name (REGF, 0x01)
                Method (_REG, 2, NotSerialized)
                {
                    If (LEqual (Arg0, 0x02))
                    {
                        Store (Arg1, REGF)
                    }
                }

                Name (TIM0, Package (0x08)
                {
                    Package (0x04)
                    {
                        0x78, 
                        0xB4, 
                        0xF0, 
                        0x0384
                    }, 

                    Package (0x04)
                    {
                        0x23, 
                        0x21, 
                        0x10, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x0B, 
                        0x09, 
                        0x04, 
                        0x00
                    }, 

                    Package (0x06)
                    {
                        0x70, 
                        0x49, 
                        0x36, 
                        0x27, 
                        0x19, 
                        0x14
                    }, 

                    Package (0x06)
                    {
                        0x00, 
                        0x01, 
                        0x02, 
                        0x01, 
                        0x02, 
                        0x01
                    }, 

                    Package (0x06)
                    {
                        0x00, 
                        0x00, 
                        0x00, 
                        0x01, 
                        0x01, 
                        0x01
                    }, 

                    Package (0x04)
                    {
                        0x04, 
                        0x03, 
                        0x02, 
                        0x00
                    }, 

                    Package (0x04)
                    {
                        0x02, 
                        0x01, 
                        0x00, 
                        0x00
                    }
                })
                Name (TMD0, Buffer (0x14) {})
                CreateDWordField (TMD0, 0x00, PIO0)
                CreateDWordField (TMD0, 0x04, DMA0)
                CreateDWordField (TMD0, 0x08, PIO1)
                CreateDWordField (TMD0, 0x0C, DMA1)
                CreateDWordField (TMD0, 0x10, CHNF)
                OperationRegion (CFG2, PCI_Config, 0x40, 0x20)
                Field (CFG2, DWordAcc, NoLock, Preserve)
                {
                    PMPT,   4, 
                    PSPT,   4, 
                    PMRI,   6, 
                            Offset (0x02), 
                    SMPT,   4, 
                    SSPT,   4, 
                    SMRI,   6, 
                            Offset (0x04), 
                    PSRI,   4, 
                    SSRI,   4, 
                            Offset (0x08), 
                    PM3E,   1, 
                    PS3E,   1, 
                    SM3E,   1, 
                    SS3E,   1, 
                            Offset (0x0A), 
                    PMUT,   2, 
                        ,   2, 
                    PSUT,   2, 
                            Offset (0x0B), 
                    SMUT,   2, 
                        ,   2, 
                    SSUT,   2, 
                            Offset (0x0C), 
                            Offset (0x14), 
                    PM6E,   1, 
                    PS6E,   1, 
                    SM6E,   1, 
                    SS6E,   1, 
                    PMCR,   1, 
                    PSCR,   1, 
                    SMCR,   1, 
                    SSCR,   1, 
                        ,   4, 
                    PMAE,   1, 
                    PSAE,   1, 
                    SMAE,   1, 
                    SSAE,   1
                }

                Name (GMPT, 0x00)
                Name (GMUE, 0x00)
                Name (GMUT, 0x00)
                Name (GMCR, 0x00)
                Name (GSPT, 0x00)
                Name (GSUE, 0x00)
                Name (GSUT, 0x00)
                Name (GSCR, 0x00)
                Device (CHN0)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        ShiftLeft (PSCR, 0x01, Local1)
                        Or (PMCR, Local1, Local0)
                        ShiftLeft (PMAE, 0x02, Local3)
                        ShiftLeft (PM6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (PM3E, Local3, Local1)
                        ShiftLeft (PMPT, 0x04, Local3)
                        Or (Local1, Local3, Local1)
                        ShiftLeft (PSAE, 0x02, Local3)
                        ShiftLeft (PS6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (PS3E, Local3, Local2)
                        ShiftLeft (PSPT, 0x04, Local3)
                        Or (Local2, Local3, Local2)
                        Return (GTM (PMRI, Local1, PMUT, PSRI, Local2, PSUT, Local0))
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, Debug)
                        Store (Arg0, TMD0)
                        ShiftLeft (PMAE, 0x02, Local3)
                        ShiftLeft (PM6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (PM3E, Local3, Local0)
                        ShiftLeft (PMPT, 0x04, Local3)
                        Or (Local0, Local3, Local0)
                        ShiftLeft (PSAE, 0x02, Local3)
                        ShiftLeft (PS6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (PS3E, Local3, Local1)
                        ShiftLeft (PSPT, 0x04, Local3)
                        Or (Local1, Local3, Local1)
                        Store (PMRI, GMPT)
                        Store (Local0, GMUE)
                        Store (PMUT, GMUT)
                        Store (PMCR, GMCR)
                        Store (PSRI, GSPT)
                        Store (Local1, GSUE)

                        Store (PSUT, GSUT)
                        Store (PSCR, GSCR)
                        STM ()
                        Store (GMPT, PMRI)
                        Store (GMUE, Local0)
                        Store (GMUT, PMUT)
                        Store (GMCR, PMCR)
                        Store (GSUE, Local1)
                        Store (GSUT, PSUT)
                        Store (GSCR, PSCR)
                        If (And (Local0, 0x01))
                        {
                            Store (0x01, PM3E)
                        }
                        Else
                        {
                            Store (0x00, PM3E)
                        }

                        If (And (Local0, 0x02))
                        {
                            Store (0x01, PM6E)
                        }
                        Else
                        {
                            Store (0x00, PM6E)
                        }

                        If (And (Local0, 0x04))
                        {
                            Store (0x01, PMAE)
                        }
                        Else
                        {
                            Store (0x00, PMAE)
                        }

                        If (And (Local1, 0x01))
                        {
                            Store (0x01, PS3E)
                        }
                        Else
                        {
                            Store (0x00, PS3E)
                        }

                        If (And (Local1, 0x02))
                        {
                            Store (0x01, PS6E)
                        }
                        Else
                        {
                            Store (0x00, PS6E)
                        }

                        If (And (Local1, 0x04))
                        {
                            Store (0x01, PSAE)
                        }
                        Else
                        {
                            Store (0x00, PSAE)
                        }

                        Store (GTF (0x00, Arg1), ATA0)
                        Store (GTF (0x01, Arg2), ATA1)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Return (RATA (ATA0))
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Return (RATA (ATA1))
                        }
                    }
                }

                Device (CHN1)
                {
                    Name (_ADR, 0x01)
                    Method (_GTM, 0, NotSerialized)
                    {
                        ShiftLeft (SSCR, 0x01, Local1)
                        Or (SMCR, Local1, Local0)
                        ShiftLeft (SMAE, 0x02, Local3)
                        ShiftLeft (SM6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (SM3E, Local3, Local1)
                        ShiftLeft (SMPT, 0x04, Local3)
                        Or (Local1, Local3, Local1)
                        ShiftLeft (SSAE, 0x02, Local3)
                        ShiftLeft (SS6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (SS3E, Local3, Local2)
                        ShiftLeft (SSPT, 0x04, Local3)
                        Or (Local2, Local3, Local2)
                        Return (GTM (SMRI, Local1, SMUT, SSRI, Local2, SSUT, Local0))
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, Debug)
                        Store (Arg0, TMD0)
                        ShiftLeft (SMAE, 0x02, Local3)
                        ShiftLeft (SM6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (SM3E, Local3, Local0)
                        ShiftLeft (SMPT, 0x04, Local3)
                        Or (Local0, Local3, Local0)
                        ShiftLeft (SSAE, 0x02, Local3)
                        ShiftLeft (SS6E, 0x01, Local4)
                        Or (Local3, Local4, Local3)
                        Or (SS3E, Local3, Local1)
                        ShiftLeft (SSPT, 0x04, Local3)
                        Or (Local1, Local3, Local1)
                        Store (SMRI, GMPT)
                        Store (Local0, GMUE)
                        Store (SMUT, GMUT)
                        Store (SMCR, GMCR)
                        Store (SSRI, GSPT)
                        Store (Local1, GSUE)
                        Store (SSUT, GSUT)
                        Store (SSCR, GSCR)
                        STM ()
                        Store (GMPT, SMRI)
                        Store (GMUE, Local0)
                        Store (GMUT, SMUT)
                        Store (GMCR, SMCR)
                        Store (GSUE, Local1)
                        Store (GSUT, SSUT)
                        Store (GSCR, SSCR)
                        If (And (Local0, 0x01))
                        {
                            Store (0x01, SM3E)
                        }
                        Else
                        {
                            Store (0x00, SM3E)
                        }

                        If (And (Local0, 0x02))
                        {
                            Store (0x01, SM6E)
                        }
                        Else
                        {
                            Store (0x00, SM6E)
                        }

                        If (And (Local0, 0x04))
                        {
                            Store (0x01, SMAE)
                        }
                        Else
                        {
                            Store (0x00, SMAE)
                        }

                        If (And (Local1, 0x01))
                        {
                            Store (0x01, SS3E)
                        }
                        Else
                        {
                            Store (0x00, SS3E)
                        }

                        If (And (Local1, 0x02))
                        {
                            Store (0x01, SS6E)
                        }
                        Else
                        {
                            Store (0x00, SS6E)
                        }

                        If (And (Local1, 0x04))
                        {
                            Store (0x01, SSAE)
                        }
                        Else
                        {
                            Store (0x00, SSAE)
                        }

                        Store (GTF (0x00, Arg1), ATA2)
                        Store (GTF (0x01, Arg2), ATA3)
                    }

                    Device (DRV0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Return (RATA (ATA2))
                        }
                    }

                    Device (DRV1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Return (RATA (ATA3))
                        }
                    }
                }

                Method (GTM, 7, Serialized)
                {
                    Store (Ones, PIO0)
                    Store (Ones, PIO1)
                    Store (Ones, DMA0)
                    Store (Ones, DMA1)
                    Store (0x10, CHNF)
                    If (REGF) {}
                    Else
                    {
                        Return (TMD0)
                    }

                    If (And (Arg1, 0x20))
                    {
                        Or (CHNF, 0x02, CHNF)
                    }

                    Store (Match (DerefOf (Index (TIM0, 0x01)), MEQ, Arg0, MTR, 
                        0x00, 0x00), Local6)
                    Store (DerefOf (Index (DerefOf (Index (TIM0, 0x00)), Local6)), 
                        Local7)
                    Store (Local7, DMA0)
                    Store (Local7, PIO0)
                    If (And (Arg4, 0x20))
                    {
                        Or (CHNF, 0x08, CHNF)
                    }

                    Store (Match (DerefOf (Index (TIM0, 0x02)), MEQ, Arg3, MTR, 
                        0x00, 0x00), Local6)
                    Store (DerefOf (Index (DerefOf (Index (TIM0, 0x00)), Local6)), 
                        Local7)
                    Store (Local7, DMA1)
                    Store (Local7, PIO1)
                    If (And (Arg1, 0x07))
                    {
                        Store (Arg2, Local5)
                        If (And (Arg1, 0x02))
                        {
                            Add (Local5, 0x02, Local5)
                        }

                        If (And (Arg1, 0x04))
                        {
                            Add (Local5, 0x04, Local5)
                        }

                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x03)), Local5)), 
                            DMA0)
                        Or (CHNF, 0x01, CHNF)
                    }

                    If (And (Arg4, 0x07))
                    {
                        Store (Arg5, Local5)
                        If (And (Arg4, 0x02))
                        {
                            Add (Local5, 0x02, Local5)
                        }

                        If (And (Arg4, 0x04))
                        {
                            Add (Local5, 0x04, Local5)
                        }

                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x03)), Local5)), 
                            DMA1)
                        Or (CHNF, 0x04, CHNF)
                    }

                    Store (TMD0, Debug)
                    Return (TMD0)
                }

                Method (STM, 0, Serialized)
                {
                    If (REGF)
                    {
                        Store (0x00, GMUE)
                        Store (0x00, GMUT)
                        Store (0x00, GSUE)
                        Store (0x00, GSUT)
                        If (And (CHNF, 0x01))
                        {
                            Store (Match (DerefOf (Index (TIM0, 0x03)), MLE, DMA0, MTR, 
                                0x00, 0x00), Local0)
                            If (LGreater (Local0, 0x05))
                            {
                                Store (0x05, Local0)
                            }

                            Store (DerefOf (Index (DerefOf (Index (TIM0, 0x04)), Local0)), 
                                GMUT)
                            Or (GMUE, 0x01, GMUE)
                            If (LGreater (Local0, 0x02))
                            {
                                Or (GMUE, 0x02, GMUE)
                            }

                            If (LGreater (Local0, 0x04))
                            {
                                And (GMUE, 0xFD, GMUE)
                                Or (GMUE, 0x04, GMUE)
                            }
                        }
                        Else
                        {
                            If (Or (LEqual (PIO0, Ones), LEqual (PIO0, 0x00)))
                            {
                                If (And (LLess (DMA0, Ones), LGreater (DMA0, 0x00)))
                                {
                                    Store (DMA0, PIO0)
                                    Or (GMUE, 0x80, GMUE)
                                }
                            }
                        }

                        If (And (CHNF, 0x04))
                        {
                            Store (Match (DerefOf (Index (TIM0, 0x03)), MLE, DMA1, MTR, 
                                0x00, 0x00), Local0)
                            If (LGreater (Local0, 0x05))
                            {
                                Store (0x05, Local0)
                            }

                            Store (DerefOf (Index (DerefOf (Index (TIM0, 0x04)), Local0)), 
                                GSUT)
                            Or (GSUE, 0x01, GSUE)
                            If (LGreater (Local0, 0x02))
                            {
                                Or (GSUE, 0x02, GSUE)
                            }

                            If (LGreater (Local0, 0x04))
                            {
                                And (GSUE, 0xFD, GSUE)
                                Or (GSUE, 0x04, GSUE)
                            }
                        }
                        Else
                        {
                            If (Or (LEqual (PIO1, Ones), LEqual (PIO1, 0x00)))
                            {
                                If (And (LLess (DMA1, Ones), LGreater (DMA1, 0x00)))
                                {
                                    Store (DMA1, PIO1)
                                    Or (GSUE, 0x80, GSUE)
                                }
                            }
                        }

                        If (And (CHNF, 0x02))
                        {
                            Or (GMUE, 0x20, GMUE)
                        }

                        If (And (CHNF, 0x08))
                        {
                            Or (GSUE, 0x20, GSUE)
                        }

                        And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIO0, MTR, 
                            0x00, 0x00), 0x07, Local0)
                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x01)), Local0)), 
                            Local1)
                        Store (Local1, GMPT)
                        If (LLess (Local0, 0x03))
                        {
                            Or (GMUE, 0x50, GMUE)
                        }

                        And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIO1, MTR, 
                            0x00, 0x00), 0x07, Local0)
                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x02)), Local0)), 
                            Local1)
                        Store (Local1, GSPT)
                        If (LLess (Local0, 0x03))
                        {
                            Or (GSUE, 0x50, GSUE)
                        }
                    }
                }

                Name (AT01, Buffer (0x07)
                {
                    0x03, 0x00, 0x00, 0x00, 0x00, 0x00, 0xEF
                })
                Name (AT02, Buffer (0x07)
                {
                    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x90
                })
                Name (AT03, Buffer (0x07)
                {
                    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xC6
                })
                Name (AT04, Buffer (0x07)
                {
                    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x91
                })
                Name (ATA0, Buffer (0x1D) {})
                Name (ATA1, Buffer (0x1D) {})
                Name (ATA2, Buffer (0x1D) {})
                Name (ATA3, Buffer (0x1D) {})
                Name (ATAB, Buffer (0x1D) {})
                CreateByteField (ATAB, 0x00, CMDC)
                Method (GTFB, 3, Serialized)
                {
                    Multiply (CMDC, 0x38, Local0)
                    Add (Local0, 0x08, Local1)
                    CreateField (ATAB, Local1, 0x38, CMDX)
                    Multiply (CMDC, 0x07, Local0)
                    CreateByteField (ATAB, Add (Local0, 0x02), A001)
                    CreateByteField (ATAB, Add (Local0, 0x06), A005)
                    Store (Arg0, CMDX)
                    Store (Arg1, A001)
                    Store (Arg2, A005)
                    Increment (CMDC)
                }

                Method (GTF, 2, Serialized)
                {
                    Store (Arg1, Debug)
                    Store (0x00, CMDC)
                    Name (ID49, 0x0C00)
                    Name (ID59, 0x00)
                    Name (ID53, 0x04)
                    Name (ID63, 0x0F00)
                    Name (ID88, 0x0F00)
                    Name (IRDY, 0x01)
                    Name (PIOT, 0x00)
                    Name (DMAT, 0x00)
                    If (LEqual (SizeOf (Arg1), 0x0200))
                    {
                        CreateWordField (Arg1, 0x62, IW49)
                        Store (IW49, ID49)
                        CreateWordField (Arg1, 0x6A, IW53)
                        Store (IW53, ID53)
                        CreateWordField (Arg1, 0x7E, IW63)
                        Store (IW63, ID63)
                        CreateWordField (Arg1, 0x76, IW59)
                        Store (IW59, ID59)
                        CreateWordField (Arg1, 0xB0, IW88)
                        Store (IW88, ID88)
                    }

                    Store (0xA0, Local7)
                    If (Arg0)
                    {
                        Store (0xB0, Local7)
                        And (CHNF, 0x08, IRDY)
                        If (And (CHNF, 0x10))
                        {
                            Store (PIO1, PIOT)
                        }
                        Else
                        {
                            Store (PIO0, PIOT)
                        }

                        If (And (CHNF, 0x04))
                        {
                            If (And (CHNF, 0x10))
                            {
                                Store (DMA1, DMAT)
                            }
                            Else
                            {
                                Store (DMA0, DMAT)
                            }
                        }
                    }
                    Else
                    {
                        And (CHNF, 0x02, IRDY)
                        Store (PIO0, PIOT)
                        If (And (CHNF, 0x01))
                        {
                            Store (DMA0, DMAT)
                        }
                    }

                    If (LAnd (LAnd (And (ID53, 0x04), And (ID88, 0xFF00
                        )), DMAT))
                    {
                        Store (Match (DerefOf (Index (TIM0, 0x03)), MLE, DMAT, MTR, 
                            0x00, 0x00), Local1)
                        If (LGreater (Local1, 0x05))
                        {
                            Store (0x05, Local1)
                        }

                        GTFB (AT01, Or (0x40, Local1), Local7)
                    }
                    Else
                    {
                        If (LAnd (And (ID63, 0xFF00), PIOT))
                        {
                            And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIOT, MTR, 
                                0x00, 0x00), 0x03, Local0)
                            Or (0x20, DerefOf (Index (DerefOf (Index (TIM0, 0x07)), Local0
                                )), Local1)
                            GTFB (AT01, Local1, Local7)
                        }
                    }

                    If (IRDY)
                    {
                        And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIOT, MTR, 
                            0x00, 0x00), 0x07, Local0)
                        Or (0x08, DerefOf (Index (DerefOf (Index (TIM0, 0x06)), Local0
                            )), Local1)
                        GTFB (AT01, Local1, Local7)
                    }
                    Else
                    {
                        If (And (ID49, 0x0400))
                        {
                            GTFB (AT01, 0x01, Local7)
                        }
                    }

                    If (LAnd (And (ID59, 0x0100), And (ID59, 0xFF)))
                    {
                        GTFB (AT03, And (ID59, 0xFF), Local7)
                    }

                    Store (ATAB, Debug)
                    Return (ATAB)
                }

                Method (RATA, 1, NotSerialized)
                {
                    CreateByteField (Arg0, 0x00, CMDN)
                    Multiply (CMDN, 0x38, Local0)
                    CreateField (Arg0, 0x08, Local0, RETB)
                    Store (RETB, Debug)
                    Return (RETB)
                }
            }

            Device (MC97)
            {
                Name (_ADR, 0x001E0003)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x05, 0x04))
                }
            }

            Device (HDAC)
            {
                Name (_ADR, 0x001B0000)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x05, 0x04))
                }
            }

            Device (P0P5)
            {
                Name (_ADR, 0x001C0001)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x09, 0x04))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR05)
                    }

                    Return (PR05)
                }
            }

            Device (P0P6)
            {
                Name (_ADR, 0x001C0002)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x09, 0x04))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR06)
                    }

                    Return (PR06)
                }
            }

            Device (P0P7)
            {
                Name (_ADR, 0x001C0003)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x09, 0x04))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR07)
                    }

                    Return (PR07)
                }
            }

            Device (P0P8)
            {
                Name (_ADR, 0x001C0004)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x09, 0x04))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR08)
                    }

                    Return (PR08)
                }
            }

            Device (P0P9)
            {
                Name (_ADR, 0x001C0005)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x09, 0x04))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR09)
                    }

                    Return (PR09)
                }
            }

            Device (P0P4)
            {
                Name (_ADR, 0x001C0000)
                Name (_HPP, Package (0x04)
                {
                    0x08, 
                    0x40, 
                    0x01, 
                    0x00
                })
                OperationRegion (SLOT, PCI_Config, 0x54, 0x10)
                Field (SLOT, ByteAcc, NoLock, Preserve)
                {
                    SCAP,   32, 
                    SCTL,   16, 
                    ABP1,   1, 
                    PFD1,   1, 
                    MSC1,   1, 
                    PDC1,   1, 
                    CC10,   1, 
                    MS10,   1, 
                    PDS1,   1, 
                    RSV0,   1, 
                    LASC,   1, 
                    RSV1,   7
                }

                OperationRegion (RHUB, PCI_Config, 0x60, 0x10)
                Field (RHUB, ByteAcc, NoLock, Preserve)
                {
                    PMID,   16, 
                    PMES,   1, 
                    PMEP,   1, 
                    RSV2,   14
                }

                OperationRegion (MISC, PCI_Config, 0xD8, 0x08)
                Field (MISC, ByteAcc, NoLock, Preserve)
                {
                    MPCR,   32, 
                    PMMS,   1, 
                    HPPD,   1, 
                    HPAB,   1, 
                    HPCC,   1, 
                    HPLA,   1, 
                    RSV3,   25, 
                    HPCS,   1, 
                    PMCS,   1
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x09, 0x04))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR04)
                    }

                    Return (PR04)
                }

                Device (XCRD)
                {
                    Name (_ADR, 0x00)
                    Method (_STA, 0, NotSerialized)
                    {
                        If (PDS1)
                        {
                            Return (0x0F)
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }

                    Method (_RMV, 0, NotSerialized)
                    {
                        Return (One)
                    }
                }
            }

            Device (USB0)
            {
                Name (_ADR, 0x001D0000)
                OperationRegion (BAR0, PCI_Config, 0xC4, 0x01)
                Field (BAR0, ByteAcc, NoLock, Preserve)
                {
                    USBW,   2, 
                            Offset (0x01)
                }

                Method (_S3D, 0, NotSerialized)
                {
                    If (LOr (LEqual (OSFL (), 0x01), LEqual (OSFL (), 0x02)))
                    {
                        Return (0x02)
                    }
                    Else
                    {
                        Return (0x03)
                    }
                }

                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, USBW)
                    }
                    Else
                    {
                        Store (0x00, USBW)
                    }
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x03, 0x03))
                }
            }

            Device (USB1)
            {
                Name (_ADR, 0x001D0001)
                OperationRegion (BAR0, PCI_Config, 0xC4, 0x01)
                Field (BAR0, ByteAcc, NoLock, Preserve)
                {
                    USBW,   2, 
                            Offset (0x01)
                }

                Method (_S3D, 0, NotSerialized)
                {
                    If (LOr (LEqual (OSFL (), 0x01), LEqual (OSFL (), 0x02)))
                    {
                        Return (0x02)
                    }
                    Else
                    {
                        Return (0x03)
                    }
                }

                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, USBW)
                    }
                    Else
                    {
                        Store (0x00, USBW)
                    }
                }

                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x04, 0x03))
                }
            }

            Device (USB2)
            {
                Name (_ADR, 0x001D0002)
                OperationRegion (BAR0, PCI_Config, 0xC4, 0x01)
                Field (BAR0, ByteAcc, NoLock, Preserve)
                {
                    USBW,   2, 
                            Offset (0x01)
                }

                Method (_S3D, 0, NotSerialized)
                {
                    If (LOr (LEqual (OSFL (), 0x01), LEqual (OSFL (), 0x02)))
                    {
                        Return (0x02)
                    }
                    Else
                    {
                        Return (0x03)
                    }
                }

                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, USBW)
                    }
                    Else
                    {
                        Store (0x00, USBW)
                    }
                }
            }

            Device (USB3)
            {
                Name (_ADR, 0x001D0003)
                OperationRegion (BAR0, PCI_Config, 0xC4, 0x01)
                Field (BAR0, ByteAcc, NoLock, Preserve)
                {
                    USBW,   2, 
                            Offset (0x01)
                }

                Method (_S3D, 0, NotSerialized)
                {
                    If (LOr (LEqual (OSFL (), 0x01), LEqual (OSFL (), 0x02)))
                    {
                        Return (0x02)
                    }
                    Else
                    {
                        Return (0x03)
                    }
                }

                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, USBW)
                    }
                    Else
                    {
                        Store (0x00, USBW)
                    }
                }
            }

            Device (EUSB)
            {
                Name (_ADR, 0x001D0007)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x0D, 0x03))
                }
            }
        }

        Scope (\_GPE)
        {
            Method (_L09, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.P0P1, 0x02)
                Notify (\_SB.PCI0.P0P5, 0x02)
                Notify (\_SB.PCI0.P0P6, 0x02)
                Notify (\_SB.PCI0.P0P7, 0x02)
                Notify (\_SB.PCI0.P0P8, 0x02)
                Notify (\_SB.PCI0.P0P9, 0x02)
                Notify (\_SB.PCI0.P0P4, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }

            Method (_L05, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.MC97, 0x02)
                Notify (\_SB.PCI0.HDAC, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }

            Method (_L03, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.USB0, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }

            Method (_L04, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.USB1, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }

            Method (_L0D, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.EUSB, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }
        }

        Device (PWRB)
        {
            Name (_HID, EisaId ("PNP0C0C"))
            Name (_UID, 0xAA)
            Name (_STA, 0x0B)
        }
    }

    OperationRegion (\_SB.PCI0.SBRG.PIX0, PCI_Config, 0x60, 0x0C)
    Field (\_SB.PCI0.SBRG.PIX0, ByteAcc, NoLock, Preserve)
    {
        PIRA,   8, 
        PIRB,   8, 
        PIRC,   8, 
        PIRD,   8, 
                Offset (0x08), 
        PIRE,   8, 
        PIRF,   8, 
        PIRG,   8, 
        PIRH,   8
    }

    Scope (\_SB)
    {
        Name (BUFA, ResourceTemplate ()
        {
            IRQ (Level, ActiveLow, Shared, _Y0D)
                {15}
        })
        CreateWordField (BUFA, \_SB._Y0D._INT, IRA0)
        Device (LNKA)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x01)
            Method (_STA, 0, NotSerialized)
            {
                And (PIRA, 0x80, Local0)
                If (Local0)
                {
                    Return (0x09)
                }
                Else
                {
                    Return (0x0B)
                }
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSA)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Or (PIRA, 0x80, PIRA)
            }

            Method (_CRS, 0, NotSerialized)
            {
                And (PIRA, 0x0F, Local0)
                ShiftLeft (0x01, Local0, IRA0)
                Return (BUFA)
            }

            Method (_SRS, 1, NotSerialized)
            {
                CreateWordField (Arg0, 0x01, IRA)
                FindSetRightBit (IRA, Local0)
                Decrement (Local0)
                Store (Local0, PIRA)
            }
        }

        Device (LNKB)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x02)
            Method (_STA, 0, NotSerialized)
            {
                And (PIRB, 0x80, Local0)
                If (Local0)
                {
                    Return (0x09)
                }
                Else
                {
                    Return (0x0B)
                }
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSB)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Or (PIRB, 0x80, PIRB)
            }

            Method (_CRS, 0, NotSerialized)
            {
                And (PIRB, 0x0F, Local0)
                ShiftLeft (0x01, Local0, IRA0)
                Return (BUFA)
            }

            Method (_SRS, 1, NotSerialized)
            {
                CreateWordField (Arg0, 0x01, IRA)
                FindSetRightBit (IRA, Local0)
                Decrement (Local0)
                Store (Local0, PIRB)
            }
        }

        Device (LNKC)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x03)
            Method (_STA, 0, NotSerialized)
            {
                And (PIRC, 0x80, Local0)
                If (Local0)
                {
                    Return (0x09)
                }
                Else
                {
                    Return (0x0B)
                }
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSC)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Or (PIRC, 0x80, PIRC)
            }

            Method (_CRS, 0, NotSerialized)
            {
                And (PIRC, 0x0F, Local0)
                ShiftLeft (0x01, Local0, IRA0)
                Return (BUFA)
            }

            Method (_SRS, 1, NotSerialized)
            {
                CreateWordField (Arg0, 0x01, IRA)
                FindSetRightBit (IRA, Local0)
                Decrement (Local0)
                Store (Local0, PIRC)
            }
        }

        Device (LNKD)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x04)
            Method (_STA, 0, NotSerialized)
            {
                And (PIRD, 0x80, Local0)
                If (Local0)
                {
                    Return (0x09)
                }
                Else
                {
                    Return (0x0B)
                }
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSD)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Or (PIRD, 0x80, PIRD)
            }

            Method (_CRS, 0, NotSerialized)
            {
                And (PIRD, 0x0F, Local0)
                ShiftLeft (0x01, Local0, IRA0)
                Return (BUFA)
            }

            Method (_SRS, 1, NotSerialized)
            {
                CreateWordField (Arg0, 0x01, IRA)
                FindSetRightBit (IRA, Local0)
                Decrement (Local0)
                Store (Local0, PIRD)
            }
        }

        Device (LNKE)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x05)
            Method (_STA, 0, NotSerialized)
            {
                And (PIRE, 0x80, Local0)
                If (Local0)
                {
                    Return (0x09)
                }
                Else
                {
                    Return (0x0B)
                }
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSE)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Or (PIRE, 0x80, PIRE)
            }

            Method (_CRS, 0, NotSerialized)
            {
                And (PIRE, 0x0F, Local0)
                ShiftLeft (0x01, Local0, IRA0)
                Return (BUFA)
            }

            Method (_SRS, 1, NotSerialized)
            {
                CreateWordField (Arg0, 0x01, IRA)
                FindSetRightBit (IRA, Local0)
                Decrement (Local0)
                Store (Local0, PIRE)
            }
        }

        Device (LNKF)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x06)
            Method (_STA, 0, NotSerialized)
            {
                And (PIRF, 0x80, Local0)
                If (Local0)
                {
                    Return (0x09)
                }
                Else
                {
                    Return (0x0B)
                }
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSF)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Or (PIRF, 0x80, PIRF)
            }

            Method (_CRS, 0, NotSerialized)
            {
                And (PIRF, 0x0F, Local0)
                ShiftLeft (0x01, Local0, IRA0)
                Return (BUFA)
            }

            Method (_SRS, 1, NotSerialized)
            {
                CreateWordField (Arg0, 0x01, IRA)
                FindSetRightBit (IRA, Local0)
                Decrement (Local0)
                Store (Local0, PIRF)
            }
        }

        Device (LNKG)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x07)
            Method (_STA, 0, NotSerialized)
            {
                And (PIRG, 0x80, Local0)
                If (Local0)
                {
                    Return (0x09)
                }
                Else
                {
                    Return (0x0B)
                }
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSG)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Or (PIRG, 0x80, PIRG)
            }

            Method (_CRS, 0, NotSerialized)
            {
                And (PIRG, 0x0F, Local0)
                ShiftLeft (0x01, Local0, IRA0)
                Return (BUFA)
            }

            Method (_SRS, 1, NotSerialized)
            {
                CreateWordField (Arg0, 0x01, IRA)
                FindSetRightBit (IRA, Local0)
                Decrement (Local0)
                Store (Local0, PIRG)
            }
        }

        Device (LNKH)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x08)
            Method (_STA, 0, NotSerialized)
            {
                And (PIRH, 0x80, Local0)
                If (Local0)
                {
                    Return (0x09)
                }
                Else
                {
                    Return (0x0B)
                }
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSH)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Or (PIRH, 0x80, PIRH)
            }

            Method (_CRS, 0, NotSerialized)
            {
                And (PIRH, 0x0F, Local0)
                ShiftLeft (0x01, Local0, IRA0)
                Return (BUFA)
            }

            Method (_SRS, 1, NotSerialized)
            {
                CreateWordField (Arg0, 0x01, IRA)
                FindSetRightBit (IRA, Local0)
                Decrement (Local0)
                Store (Local0, PIRH)
            }
        }
    }

    Scope (\_SB)
    {
        Name (XCPD, 0x00)
        Name (XNPT, 0x01)
        Name (XCAP, 0x02)
        Name (XDCP, 0x04)
        Name (XDCT, 0x08)
        Name (XDST, 0x0A)
        Name (XLCP, 0x0C)

        Name (XLCT, 0x10)
        Name (XLST, 0x12)
        Name (XSCP, 0x14)
        Name (XSCT, 0x18)
        Name (XSST, 0x1A)
        Name (XRCT, 0x1C)
        Mutex (MUTE, 0x00)
        Method (RBPE, 1, NotSerialized)
        {
            Acquire (MUTE, 0x03E8)
            Add (Arg0, \PCIB, Local0)
            OperationRegion (PCFG, SystemMemory, Local0, 0x01)
            Field (PCFG, ByteAcc, NoLock, Preserve)
            {
                XCFG,   8
            }

            Release (MUTE)
            Return (XCFG)
        }

        Method (RWPE, 1, NotSerialized)
        {
            Acquire (MUTE, 0x03E8)
            And (Arg0, 0xFFFFFFFE, Arg0)
            Add (Arg0, \PCIB, Local0)
            OperationRegion (PCFG, SystemMemory, Local0, 0x02)
            Field (PCFG, WordAcc, NoLock, Preserve)
            {
                XCFG,   16
            }

            Release (MUTE)
            Return (XCFG)
        }

        Method (RDPE, 1, NotSerialized)
        {
            Acquire (MUTE, 0x03E8)
            And (Arg0, 0xFFFFFFFC, Arg0)
            Add (Arg0, \PCIB, Local0)
            OperationRegion (PCFG, SystemMemory, Local0, 0x04)
            Field (PCFG, DWordAcc, NoLock, Preserve)
            {
                XCFG,   32
            }

            Release (MUTE)
            Return (XCFG)
        }

        Method (WBPE, 2, NotSerialized)
        {
            Acquire (MUTE, 0x0FFF)
            Add (Arg0, \PCIB, Local0)
            OperationRegion (PCFG, SystemMemory, Local0, 0x01)
            Field (PCFG, ByteAcc, NoLock, Preserve)
            {
                XCFG,   8
            }

            Store (Arg1, XCFG)
            Release (MUTE)
        }

        Method (WWPE, 2, NotSerialized)
        {
            Acquire (MUTE, 0x03E8)
            And (Arg0, 0xFFFFFFFE, Arg0)
            Add (Arg0, \PCIB, Local0)
            OperationRegion (PCFG, SystemMemory, Local0, 0x02)
            Field (PCFG, WordAcc, NoLock, Preserve)
            {
                XCFG,   16
            }

            Store (Arg1, XCFG)
            Release (MUTE)
        }

        Method (WDPE, 2, NotSerialized)
        {
            Acquire (MUTE, 0x03E8)
            And (Arg0, 0xFFFFFFFC, Arg0)
            Add (Arg0, \PCIB, Local0)
            OperationRegion (PCFG, SystemMemory, Local0, 0x04)
            Field (PCFG, DWordAcc, NoLock, Preserve)
            {
                XCFG,   32
            }

            Store (Arg1, XCFG)
            Release (MUTE)
        }

        Method (RWDP, 3, NotSerialized)
        {
            Acquire (MUTE, 0x03E8)
            And (Arg0, 0xFFFFFFFC, Arg0)
            Add (Arg0, \PCIB, Local0)
            OperationRegion (PCFG, SystemMemory, Local0, 0x04)
            Field (PCFG, DWordAcc, NoLock, Preserve)
            {
                XCFG,   32
            }

            And (XCFG, Arg2, Local1)
            Or (Local1, Arg1, XCFG)
            Release (MUTE)
        }

        Method (RPME, 1, NotSerialized)
        {
            Add (Arg0, 0x84, Local0)
            Store (\_SB.RDPE (Local0), Local1)
            If (LEqual (Local1, 0xFFFFFFFF))
            {
                Return (0x00)
            }
            Else
            {
                If (LAnd (Local1, 0x00010000))
                {
                    \_SB.WDPE (Local0, And (Local1, 0x00010000))
                    Return (0x01)
                }

                Return (0x00)
            }
        }
    }

    Scope (\_SB)
    {
        Scope (PCI0)
        {
            Name (CRS, ResourceTemplate ()
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
                    0x000A0000,         // Range Minimum
                    0x000BFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00020000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C0000,         // Range Minimum
                    0x000DFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00020000,         // Length
                    ,, _Y0E, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0x00000000,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, _Y0F, AddressRangeMemory, TypeStatic)
            })
            CreateDWordField (CRS, \_SB.PCI0._Y0E._MIN, MIN5)
            CreateDWordField (CRS, \_SB.PCI0._Y0E._MAX, MAX5)
            CreateDWordField (CRS, \_SB.PCI0._Y0E._LEN, LEN5)
            CreateDWordField (CRS, \_SB.PCI0._Y0F._MIN, MIN6)
            CreateDWordField (CRS, \_SB.PCI0._Y0F._MAX, MAX6)
            CreateDWordField (CRS, \_SB.PCI0._Y0F._LEN, LEN6)
            Method (_CRS, 0, NotSerialized)
            {
                Store (MG1L, Local0)
                If (Local0)
                {
                    Store (MG1B, MIN5)
                    Store (MG1L, LEN5)
                    Add (MIN5, Decrement (Local0), MAX5)
                }

                Store (MG2B, MIN6)
                Store (MG2L, LEN6)
                Store (MG2L, Local0)
                Add (MIN6, Decrement (Local0), MAX6)
                Return (CRS)
            }
        }
    }

    Name (WOTB, 0x00)
    Name (WSSB, 0x00)
    Name (WAXB, 0x00)
    Method (_PTS, 1, NotSerialized)
    {
        Store (Arg0, DBG8)
        PTS (Arg0)
        Store (0x00, Index (WAKP, 0x00))
        Store (0x00, Index (WAKP, 0x01))
        If (LAnd (LEqual (Arg0, 0x04), LEqual (OSFL (), 0x02)))
        {
            Sleep (0x0BB8)
        }

        Store (ASSB, WSSB)
        Store (AOTB, WOTB)
        Store (AAXB, WAXB)
        Store (Arg0, ASSB)
        Store (OSFL (), AOTB)
        Store (Zero, AAXB)
        \_SB.ATKD.SPGS (0x02)
    }

    Method (_WAK, 1, NotSerialized)
    {
        ShiftLeft (Arg0, 0x04, DBG8)
        WAK (Arg0)
        If (ASSB)
        {
            Store (WSSB, ASSB)
            Store (WOTB, AOTB)
            Store (WAXB, AAXB)
        }

        If (DerefOf (Index (WAKP, 0x00)))
        {
            Store (0x00, Index (WAKP, 0x01))
        }
        Else
        {
            Store (Arg0, Index (WAKP, 0x01))
        }

        Return (WAKP)
    }

    Device (\_SB.PCI0.SBRG.TPM)
    {
        Name (_HID, EisaId ("IFX0102"))
        Name (_CID, 0x310CD041)
        Name (_UID, 0x01)
        Name (_CRS, ResourceTemplate ()
        {
            IO (Decode16,
                0x004E,             // Range Minimum
                0x004E,             // Range Maximum
                0x01,               // Alignment
                0x02,               // Length
                )
            IO (Decode16,
                0x4700,             // Range Minimum
                0x4700,             // Range Maximum
                0x01,               // Alignment
                0x0C,               // Length
                )
            Memory32Fixed (ReadWrite,
                0xFED40000,         // Address Base
                0x00005000,         // Address Length
                )
        })
        Method (_STA, 0, NotSerialized)
        {
            If (TPMF)
            {
                Return (0x0F)
            }
            Else
            {
                Return (0x00)
            }
        }
    }

    Scope (\_SB.PCI0.SBRG.TPM)
    {
        OperationRegion (CMSR, SystemIO, 0x72, 0x02)
        Field (CMSR, ByteAcc, NoLock, Preserve)
        {
            INQ,    8, 
            DAQ,    8
        }

        IndexField (INQ, DAQ, ByteAcc, NoLock, Preserve)
        {
            RQST,   4, 
            RCNT,   4, 
            ERRS,   16, 
            MOR,    1
        }

        Name (TAAX, 0x00)
        OperationRegion (MIPT, SystemIO, SMIT, 0x01)
        Field (MIPT, ByteAcc, NoLock, Preserve)
        {
            PSMI,   8
        }

        Name (PPI1, Package (0x02)
        {
            0x00, 
            0x00
        })
        Name (PPI2, Package (0x03)
        {
            0x00, 
            0x00, 
            0x00
        })
        Name (MBUF, Buffer (0x04) {})
        CreateByteField (MBUF, 0x00, BUF0)
        CreateByteField (MBUF, 0x01, BUF1)
        CreateByteField (MBUF, 0x02, BUF2)
        CreateByteField (MBUF, 0x03, BUF3)
        Method (_DSM, 4, NotSerialized)
        {
            If (LEqual (Arg0, Buffer (0x10)
                    {
                        /* 0000 */    0xA6, 0xFA, 0xDD, 0x3D, 0x1B, 0x36, 0xB4, 0x4E, 
                        /* 0008 */    0xA4, 0x24, 0x8D, 0x10, 0x08, 0x9D, 0x16, 0x53
                    }))
            {
                Name (_T_0, Zero)
                Store (ToInteger (Arg2), _T_0)
                If (LEqual (_T_0, 0x00))
                {
                    Return (Buffer (0x01)
                    {
                        0x7F
                    })
                }
                Else
                {
                    If (LEqual (_T_0, 0x01))
                    {
                        Return ("1.0")
                    }
                    Else
                    {
                        If (LEqual (_T_0, 0x02))
                        {
                            Store (AAXB, TAAX)
                            Store (CMRQ, BUF0)
                            Store (0xF0, BUF1)
                            Store (ToInteger (DerefOf (Index (Arg3, 0x00))), BUF2)
                            Store (0x01, BUF3)
                            Store (MBUF, AAXB)
                            Store (0xFB, PSMI)
                            Sleep (0x0BB8)
                            Store (TAAX, AAXB)
                            Return (Zero)
                        }
                        Else
                        {
                            If (LEqual (_T_0, 0x03))
                            {
                                Store (AAXB, TAAX)
                                Store (CMRQ, BUF0)
                                Store (0x0F, BUF1)
                                Store (0x00, BUF2)
                                Store (0x00, BUF3)
                                Store (MBUF, AAXB)
                                Store (0xFB, PSMI)
                                Sleep (0x0BB8)
                                Store (AAXB, MBUF)
                                Store (BUF2, Local3)
                                Store (0x00, Index (PPI1, 0x00))
                                Store (Local3, Index (PPI1, 0x01))
                                Store (TAAX, AAXB)
                                Return (PPI1)
                            }
                            Else
                            {
                                If (LEqual (_T_0, 0x04))
                                {
                                    Return (0x02)
                                }
                                Else
                                {
                                    If (LEqual (_T_0, 0x05))
                                    {
                                        Store (AAXB, TAAX)
                                        Store (CMRQ, BUF0)
                                        Store (0xF0, BUF1)
                                        Store (0x00, BUF2)
                                        Store (0x00, BUF3)
                                        Store (MBUF, AAXB)
                                        Store (0xFB, PSMI)
                                        Sleep (0x0BB8)
                                        Store (AAXB, MBUF)
                                        ShiftRight (BUF2, 0x04)
                                        Store (BUF2, Local3)
                                        Store (CMER, BUF0)
                                        Store (0xFF, BUF1)
                                        Store (0x00, BUF2)
                                        Store (0x00, BUF3)
                                        Store (MBUF, AAXB)
                                        Store (0xFB, PSMI)
                                        Sleep (0x0BB8)
                                        Store (AAXB, MBUF)
                                        Store (BUF2, Local6)
                                        Add (CMER, 0x01, Local4)
                                        Store (Local4, BUF0)
                                        Store (0xFF, BUF1)
                                        Store (0x00, BUF2)
                                        Store (0x00, BUF3)
                                        Store (MBUF, AAXB)
                                        Store (0xFB, PSMI)
                                        Sleep (0x0BB8)
                                        Store (AAXB, MBUF)
                                        Store (BUF2, Local7)
                                        Multiply (Local7, 0x0100, Local2)
                                        Add (Local2, Local6, Local2)
                                        Store (0x00, Index (PPI2, 0x00))
                                        Store (Local3, Index (PPI2, 0x01))
                                        If (LEqual (Local2, 0xFFF0))
                                        {
                                            Store (0xFFFFFFF0, Index (PPI2, 0x02))
                                        }
                                        Else
                                        {
                                            If (LEqual (Local2, 0xFFF1))
                                            {
                                                Store (0xFFFFFFF1, Index (PPI2, 0x02))
                                            }
                                            Else
                                            {
                                                Store (Local2, Index (PPI2, 0x02))
                                            }
                                        }

                                        Store (TAAX, AAXB)
                                        Return (PPI2)
                                    }
                                    Else
                                    {
                                        If (LEqual (_T_0, 0x06))
                                        {
                                            Return (Zero)
                                        }
                                        Else
                                        {
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }
            Else
            {
                If (LEqual (Arg0, Buffer (0x10)
                        {
                            /* 0000 */    0xED, 0x54, 0x60, 0x37, 0x13, 0xCC, 0x75, 0x46, 
                            /* 0008 */    0x90, 0x1C, 0x47, 0x56, 0xD7, 0xF2, 0xD4, 0x5D
                        }))
                {
                    Name (_T_1, Zero)
                    Store (ToInteger (Arg2), _T_1)
                    If (LEqual (_T_1, 0x00))
                    {
                        Return (Buffer (0x01)
                        {
                            0x03
                        })
                    }
                    Else
                    {
                        If (LEqual (_T_1, 0x01))
                        {
                            Store (AAXB, TAAX)
                            Store (CMOR, BUF0)
                            Store (0xFE, BUF1)
                            Store (ToInteger (DerefOf (Index (Arg3, 0x00))), BUF2)
                            Store (0x01, BUF3)
                            Store (MBUF, AAXB)
                            Store (0xFB, PSMI)
                            Sleep (0x0BB8)
                            Store (TAAX, AAXB)
                            Return (Zero)
                        }
                        Else
                        {
                        }
                    }
                }
            }

            Return (Buffer (0x01)
            {
                0x00
            })
        }
    }

    Name (\_S0, Package (0x04)
    {
        0x00, 
        0x00, 
        0x00, 
        0x00
    })
    If (SS1)
    {
        Name (\_S1, Package (0x04)
        {
            0x01, 
            0x00, 
            0x00, 
            0x00
        })
    }

    If (SS3)
    {
        Name (\_S3, Package (0x04)
        {
            0x05, 
            0x00, 
            0x00, 
            0x00
        })
    }

    If (SS4)
    {
        Name (\_S4, Package (0x04)
        {
            0x06, 
            0x00, 
            0x00, 
            0x00
        })
    }

    Name (\_S5, Package (0x04)
    {
        0x07, 
        0x00, 
        0x00, 
        0x00
    })
    Method (PTS, 1, NotSerialized)
    {
        If (Arg0)
        {
            \_SB.PCI0.SBRG.EC0.EC0S (Arg0)
            \_SB.PCI0.NPTS (Arg0)
            \_SB.PCI0.SBRG.SPTS (Arg0)
        }
    }

    Scope (\_SB.PCI0)
    {
        Method (_INI, 0, NotSerialized)
        {
        }
    }

    Method (WAK, 1, NotSerialized)
    {
        \_SB.PCI0.SBRG.EC0.EC0W (Arg0)
        \_SB.PCI0.NWAK (Arg0)
        \_SB.PCI0.SBRG.SWAK (Arg0)
        \DHLW ()
    }
}

---

