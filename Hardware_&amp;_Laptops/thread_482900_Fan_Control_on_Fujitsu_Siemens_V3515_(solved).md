---
title: "Fan Control on Fujitsu Siemens V3515 (solved)"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by santoxyz on 2007-06-24
Hi, I'm new here!



This guide is based on the very good post
"
CPU Fan control - problem solved (amilo pro 2030) 
acojlo
"

-------------

In ubuntu 7.04 (kernel 2.6.20 - already patched for DSDT module in ubuntu) i done this (as root):
- 
cd /etc/mkinitramfs

-
cat /proc/acpi/dsdt > DSDT.dat

- 
iasl -d DSDT.dat

- 
edited DSDT.dsl and replaced Device (FAN) section with the above:

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


-
 iasl -tc DSDT.dsl

(*** I've posted the already patched DSDT on [http://acpi.sourceforge.net/dsdt/](http://acpi.sourceforge.net/dsdt/) ***)

- 
dpkg-reconfigure linux-image-`uname -r` 

- 
reboot

to check that patched DSDT has been loaded you can 

- 
dmesg | grep DSDT

-----

To manually control fan : 

echo 1 > /proc/acpi/fan/FAN/state #slow mode

echo 2 > /proc/acpi/fan/FAN/state #full speed.

echo 3 > /proc/acpi/fan/FAN/state #fan off (if temp<thermal_threshold)

To slow down fan at startup you have to write a simple script to load at boot:

- 
cd /etc/init.d

-
echo "echo 3 > /proc/acpi/fan/FAN/state" > fan_control

- 
update-rc.d fan_control start 51 S

- 
(reboot)

---------


After a little test i saw that fan starts up at slow speed if temperature is >50°C and at full speed >80°C; stops <48°C .


Good Luck!

---

### Post by popeye on 2007-07-02
Hi,

Used your post with succes. But i like to let it start on high speed at a lower temperature, is it possible to lower that value?

Here some additions to the text, otherwise it won´t work.

> In ubuntu 7.04 (kernel 2.6.20 - already patched for DSDT module in ubuntu) i done this (as root):
-
cd /etc/mkinitramfs

should be ```
cd  cd /etc/initramfs-tools
```

mkinitramfs does not exist on my system

> update-rc.d fan_control start 51 S

```
update-rc.d fan_control start 51 S .
```

The dot is to be inserted on the end. Otherwise it complains error expected runlevel.

---

### Post by santoxyz on 2007-07-04
Hi, thanks for your corrections Popeye ..


To change the thermal zones i think you have 2 possibility:

1. patch them in DSDT    (search the google... but it could be dangerous - you have to write them in hex)
     (see here for some suggestion: [http://kjdf.sdf-eu.org/v2035/debian-on-fujitsu-v2035.html](http://kjdf.sdf-eu.org/v2035/debian-on-fujitsu-v2035.html)  )

2. echo something like this (search the google: it's only an example - NOT TESTED!)
echo -n "50:0:0:0:0" > /proc/acpi/thermal_zone/THM/trip_points

the numbers are the thresholds - you have to change them according to your needs (google for more reference)

---

### Post by fifafrazer on 2007-09-14
I'm a newbie on a 3515 laptop, but how do you patch the kernel with dsdt (whatever that is)?

---

### Post by fd1043 on 2007-09-27
Thanks for your post.

On my maschine the fan is now switched off even without the script!

If I apply the script as you advised the fan is switched on again?
Here is what I put in /etc/init.d:
#! /bin/sh

echo 3 > /proc/acpi/fan/FAN/state

exit 0

If I issue the echo command manually, the fan is switched on again at full speed?!
Any ideas?

Thanks Matthias

---

### Post by lizardking on 2008-03-28
Could someone patch my DSDT of Amilo M1425 with that similar line. Because I dont' find the FAN device section.

Here Amilo M1425 DSDT:
```

/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20061109
 *
 * Disassembly of DSDT.dat, Fri Mar 28 17:30:52 2008
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x00003B45 (15173)
 *     Revision         0x01
 *     OEM ID           "UW___"
 *     OEM Table ID     "F08_____"
 *     OEM Revision     0x00000000 (0)
 *     Creator ID       "INTL"
 *     Creator Revision 0x02002026 (33562662)
 */
DefinitionBlock ("DSDT.aml", "DSDT", 1, "UW___", "F08_____", 0x00000000)
{
    Scope (\_PR)
    {
        Processor (CPU1, 0x01, 0x00000410, 0x06)
        {
            OperationRegion (SSDT, SystemMemory, 0x3FFD3F40, 0xFFFF)
            Name (NCPU, 0x01)
            Name (TYPE, 0x80000000)
            Name (HNDL, 0x80000000)
            Method (_PDC, 1, NotSerialized)
            {
                CreateDWordField (Arg0, 0x08, DAT0)
                Store (DAT0, TYPE)
                If (LEqual (NCPU, 0x02))
                {
                    If (LEqual (And (TYPE, 0x0A), 0x0A))
                    {
                        OperationRegion (PMRG, SystemIO, \PMBS, 0x50)
                        Field (PMRG, ByteAcc, NoLock, Preserve)
                        {
                                    Offset (0x41), 
                            DEV4,   1, 
                            DEV5,   1, 
                            DEV6,   1, 
                            DEV7,   1, 
                            STS4,   1, 
                            STS5,   1, 
                            STS6,   1, 
                            STS7,   1
                        }

                        Store (0x01, STS7)
                        Store (0x01, DEV7)
                        Load (SSDT, HNDL)
                    }
                }
            }
        }
    }

    OperationRegion (BIOS, SystemMemory, 0x3FFDF064, 0xFF)
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
        MG2L,   32
    }

    Name (SPIO, 0x2E)
    Name (IO1B, 0x0600)
    Name (IO1L, 0x10)
    Name (IOXB, 0x0640)
    Name (IOXL, 0x10)
    Name (APIC, 0x01)
    Name (PMBS, 0x0400)
    Name (PMLN, 0x80)
    Name (GPBS, 0x0500)
    Name (GPLN, 0x40)
    Name (SMBS, 0x0540)
    Name (SMBL, 0x10)
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
        If (MCTH (\_OS, "Microsoft Windows NT"))
        {
            If (LEqual (OSVR, 0x01))
            {
                If (CondRefOf (_OSI, Local0))
                {
                    If (\_OSI ("Windows 2001"))
                    {
                        Store (0x04, OSVR)
                    }
                }
                Else
                {
                    Store (0x00, OSVR)
                }
            }
        }
        Else
        {
            If (MCTH (\_OS, "Microsoft WindowsME: Millennium Edition"))
            {
                Store (0x02, OSVR)
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
    OperationRegion (DEB0, SystemIO, 0x80, 0x01)
    Field (DEB0, ByteAcc, NoLock, Preserve)
    {
        DBG8,   8
    }

    OperationRegion (DEB1, SystemIO, 0x90, 0x02)
    Field (DEB1, WordAcc, NoLock, Preserve)
    {
        DBG9,   16
    }

    Scope (\_SB)
    {
        Name (PR00, Package (0x08)
        {
            Package (0x04)
            {
                0x001FFFFF, 
                0x01, 
                LNKB, 
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
                0x001DFFFF, 
                0x00, 
                LNKA, 
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
                LNKH, 
                0x00
            }, 

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
        Name (AR00, Package (0x08)
        {
            Package (0x04)
            {
                0x001FFFFF, 
                0x01, 
                0x00, 
                0x11
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
                0x001DFFFF, 
                0x00, 
                0x00, 
                0x10
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
                0x17
            }, 

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
        Name (PR01, Package (0x07)
        {
            Package (0x04)
            {
                0x0009FFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0x000BFFFF, 
                0x00, 
                LNKC, 
                0x00
            }, 

            Package (0x04)
            {
                0x000CFFFF, 
                0x00, 
                LNKB, 
                0x00
            }, 

            Package (0x04)
            {
                0x000BFFFF, 
                0x01, 
                LNKD, 
                0x00
            }, 

            Package (0x04)
            {
                0x000BFFFF, 
                0x02, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0x000DFFFF, 
                0x00, 
                LNKA, 
                0x00
            }, 

            Package (0x04)
            {
                0x000AFFFF, 
                0x00, 
                LNKB, 
                0x00
            }
        })
        Name (AR01, Package (0x05)
        {
            Package (0x04)
            {
                0x0009FFFF, 
                0x00, 
                0x00, 
                0x10
            }, 

            Package (0x04)
            {
                0x000BFFFF, 
                0x00, 
                0x00, 
                0x12
            }, 

            Package (0x04)
            {
                0x000BFFFF, 
                0x01, 
                0x00, 
                0x13
            }, 

            Package (0x04)
            {
                0x000BFFFF, 
                0x02, 
                0x00, 
                0x10
            }, 

            Package (0x04)
            {
                0x000AFFFF, 
                0x00, 
                0x00, 
                0x11
            }
        })
        Name (PRSA, ResourceTemplate ()
        {
            IRQ (Level, ActiveLow, Shared, )
                {6,9,11,12,14,15}
        })
        Alias (PRSA, PRSB)
        Alias (PRSA, PRSC)
        Name (PRSD, ResourceTemplate ()
        {
            IRQ (Level, ActiveLow, Shared, )
                {6,11,12,14,15}
        })
        Name (PRSE, ResourceTemplate ()
        {
            IRQ (Level, ActiveLow, Shared, )
                {3,4,5,6,7,9,11,12,14,15}
        })
        Alias (PRSE, PRSF)
        Alias (PRSE, PRSG)
        Alias (PRSE, PRSH)
        Device (PCI0)
        {
            Name (_HID, EisaId ("PNP0A03"))
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

            Device (P0P1)
            {
                Name (_ADR, 0x001E0000)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x0B, 0x04))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (PICM)
                    {
                        Return (AR01)
                    }

                    Return (PR01)
                }

                Device (CBC0)
                {
                    Name (_ADR, 0x000B0001)
                    Device (\_SB.PCI0.CBC0)
                    {
                        Name (_ADR, 0x000B0000)
                        Name (CPRS, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, )
                                {9,10,11,12}
                        })
                        OperationRegion (CBR0, PCI_Config, 0x00, 0xFF)
                        Field (CBR0, DWordAcc, NoLock, Preserve)
                        {
                                    Offset (0x44), 
                            C044,   32, 
                                    Offset (0xA4), 
                            C0A4,   8, 
                            C0A5,   8, 
                                    Offset (0xE0), 
                            C0E0,   8
                        }

                        Method (_STA, 0, NotSerialized)
                        {
                            Store (0x04, \_SB.PCI0.CBC0.C0E0)
                            Return (0x0F)
                        }

                        Method (_INI, 0, NotSerialized)
                        {
                            Store (0x04, \_SB.PCI0.CBC0.C0E0)
                        }

                        Method (_PRS, 0, NotSerialized)
                        {
                            Return (CPRS)
                        }
                    }
                }

                Device (RTL)
                {
                    Name (_ADR, 0x000A0000)
                    Method (_PRW, 0, NotSerialized)
                    {
                        Return (GPRW (0x0B, 0x04))
                    }
                }
            }

            Device (SMBS)
            {
                Name (_ADR, 0x001F0003)
            }

            Device (MODM)
            {
                Name (_ADR, 0x001F0006)
                Method (_PRW, 0, NotSerialized)
                {
                    Return (GPRW (0x05, 0x03))
                }
            }

            Device (IDE0)
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

                OperationRegion (BAR0, PCI_Config, 0x00, 0x0100)
                Field (BAR0, DWordAcc, NoLock, Preserve)
                {
                            Offset (0x40), 
                    TIMP,   16, 
                    TIMS,   16, 
                    STMP,   4, 
                    STMS,   4, 
                            Offset (0x48), 
                    UDMP,   2, 
                    UDMS,   2, 
                            Offset (0x4A), 
                    UDTP,   6, 
                            Offset (0x4B), 
                    UDTS,   6, 
                            Offset (0x54), 
                    PCB0,   2, 
                    SCB0,   2, 
                    PCA0,   2, 
                    SCA0,   2, 
                        ,   4, 
                    FPB0,   2, 
                    FSB0,   2, 
                    PRSM,   2, 
                    SESM,   2
                }

                Name (TIM0, Package (0x09)
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
                        0x0F
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

                    Package (0x06)
                    {
                        0x00, 
                        0x00, 
                        0x00, 
                        0x00, 
                        0x00, 
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
                Name (GTIM, 0x00)
                Name (GSTM, 0x00)
                Name (GUDM, 0x00)
                Name (GUDT, 0x00)
                Name (GCB0, 0x00)
                Name (GFB0, 0x00)
                Device (CHN0)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Return (GTM (TIMP, STMP, UDMP, UDTP, PCB0, FPB0))
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, Debug)
                        Store (Arg0, TMD0)
                        Store (TIMP, GTIM)
                        Store (UDTP, GUDT)
                        If (STM ())
                        {
                            Store (GTIM, TIMP)
                            Store (GSTM, STMP)
                            Store (GUDM, UDMP)
                            Store (GUDT, UDTP)
                            Store (GCB0, PCB0)
                            Store (GFB0, FPB0)
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
                        Return (GTM (TIMS, STMS, UDMS, UDTS, SCB0, FSB0))
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        Store (Arg0, Debug)
                        Store (Arg0, TMD0)
                        Store (TIMS, GTIM)
                        Store (UDTS, GUDT)
                        If (STM ())
                        {
                            Store (GTIM, TIMS)
                            Store (GSTM, STMS)
                            Store (GUDM, UDMS)
                            Store (GUDT, UDTS)
                            Store (GCB0, SCB0)
                            Store (GFB0, FSB0)
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

                Method (GTM, 6, Serialized)
                {
                    Store (Ones, PIO0)
                    Store (PIO0, PIO1)
                    Store (PIO0, DMA0)
                    Store (PIO0, DMA1)
                    Store (Zero, CHNF)
                    If (REGF) {}
                    Else
                    {
                        Return (TMD0)
                    }

                    If (And (Arg0, 0x02))
                    {
                        Or (CHNF, 0x02, CHNF)
                    }

                    ShiftRight (And (Arg0, 0x3300), 0x08, Local5)
                    Store (Match (DerefOf (Index (TIM0, 0x01)), MLE, Local5, MTR, 
                        0x00, 0x00), Local6)
                    Store (DerefOf (Index (DerefOf (Index (TIM0, 0x00)), Local6)), 
                        Local7)
                    Store (Local7, DMA0)
                    If (And (Arg0, 0x08))
                    {
                        Store (0x0384, PIO0)
                    }
                    Else
                    {
                        Store (Local7, PIO0)
                    }

                    If (And (Arg0, 0x20))
                    {
                        Or (CHNF, 0x08, CHNF)
                    }

                    If (And (Arg0, 0x4000))
                    {
                        Or (CHNF, 0x10, CHNF)
                        Store (Match (DerefOf (Index (TIM0, 0x02)), MLE, Arg1, MTR, 
                            0x00, 0x00), Local5)
                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x00)), Local5)), 
                            Local6)
                        Store (Local6, DMA1)
                        If (And (Arg0, 0x80))
                        {
                            Store (0x0384, PIO1)
                        }
                        Else
                        {
                            Store (Local6, PIO1)
                        }
                    }

                    If (And (Arg2, 0x01))
                    {
                        And (Arg3, 0x03, Local5)
                        If (LAnd (And (Arg5, 0x01), LEqual (Local5, 0x01)))
                        {
                            Add (Local5, 0x04, Local5)
                        }
                        Else
                        {
                            If (And (Arg4, 0x01))
                            {
                                Add (Local5, 0x02, Local5)
                            }
                        }

                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x03)), Local5)), 
                            DMA0)
                        Or (CHNF, 0x01, CHNF)
                    }

                    If (And (Arg2, 0x02))
                    {
                        And (ShiftRight (Arg3, 0x04), 0x03, Local5)
                        If (LAnd (And (Arg5, 0x02), LEqual (Local5, 0x01)))
                        {
                            Add (Local5, 0x04, Local5)
                        }
                        Else
                        {
                            If (And (Arg4, 0x02))
                            {
                                Add (Local5, 0x02, Local5)
                            }
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
                        Return (0x00)
                    }

                    And (GTIM, 0x8044, GTIM)
                    Store (0x00, GSTM)
                    Store (0x00, GUDM)
                    Store (0x00, GCB0)
                    And (GUDT, 0xCC, GUDT)
                    Store (0x00, GFB0)
                    If (And (CHNF, 0x01))
                    {
                        Store (Match (DerefOf (Index (TIM0, 0x03)), MLE, DMA0, MTR, 
                            0x00, 0x00), Local0)
                        If (LGreater (Local0, 0x05))
                        {
                            Store (0x05, Local0)
                        }

                        Or (GUDT, DerefOf (Index (DerefOf (Index (TIM0, 0x04)), Local0
                            )), GUDT)
                        Or (GCB0, DerefOf (Index (DerefOf (Index (TIM0, 0x05)), Local0
                            )), GCB0)
                        Or (GFB0, DerefOf (Index (DerefOf (Index (TIM0, 0x06)), Local0
                            )), GFB0)
                        Or (GUDM, 0x01, GUDM)
                    }
                    Else
                    {
                        If (Or (LEqual (PIO0, Ones), LEqual (PIO0, 0x00)))
                        {
                            If (And (LLess (DMA0, Ones), LGreater (DMA0, 0x00)))
                            {
                                Store (DMA0, PIO0)
                                Or (GTIM, 0x08, GTIM)
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

                        Or (GUDT, ShiftLeft (DerefOf (Index (DerefOf (Index (TIM0, 0x04)), 
                            Local0)), 0x04), GUDT)
                        Or (GCB0, ShiftLeft (DerefOf (Index (DerefOf (Index (TIM0, 0x05)), 
                            Local0)), 0x01), GCB0)
                        Or (GFB0, ShiftLeft (DerefOf (Index (DerefOf (Index (TIM0, 0x06)), 
                            Local0)), 0x01), GFB0)
                        Or (GUDM, 0x02, GUDM)
                    }
                    Else
                    {
                        If (Or (LEqual (PIO1, Ones), LEqual (PIO1, 0x00)))
                        {
                            If (And (LLess (DMA1, Ones), LGreater (DMA1, 0x00)))
                            {
                                Store (DMA1, PIO1)
                                Or (GTIM, 0x80, GTIM)
                            }
                        }
                    }

                    If (And (CHNF, 0x02))
                    {
                        Or (GTIM, 0x03, GTIM)
                    }

                    If (And (CHNF, 0x08))
                    {
                        Or (GTIM, 0x30, GTIM)
                    }

                    And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIO0, MTR, 
                        0x00, 0x00), 0x03, Local0)
                    Store (DerefOf (Index (DerefOf (Index (TIM0, 0x01)), Local0)), 
                        Local1)
                    ShiftLeft (Local1, 0x08, Local2)
                    Or (GTIM, Local2, GTIM)
                    If (And (CHNF, 0x10))
                    {
                        Or (GTIM, 0x4000, GTIM)
                        And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIO1, MTR, 
                            0x00, 0x00), 0x03, Local0)
                        Store (DerefOf (Index (DerefOf (Index (TIM0, 0x02)), Local0)), 
                            GSTM)
                    }

                    Return (0x01)
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
                            Or (0x20, DerefOf (Index (DerefOf (Index (TIM0, 0x08)), Local0
                                )), Local1)
                            GTFB (AT01, Local1, Local7)
                        }
                    }

                    If (IRDY)
                    {
                        And (Match (DerefOf (Index (TIM0, 0x00)), MGE, PIOT, MTR, 
                            0x00, 0x00), 0x03, Local0)
                        Or (0x08, DerefOf (Index (DerefOf (Index (TIM0, 0x07)), Local0
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

            Device (USB1)
            {
                Name (_ADR, 0x001D0000)
                OperationRegion (BAR0, PCI_Config, 0xC0, 0x05)
                Field (BAR0, ByteAcc, NoLock, Preserve)
                {
                    UBL1,   16, 
                            Offset (0x04), 
                    USBW,   8
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

            Device (USB2)
            {
                Name (_ADR, 0x001D0001)
                OperationRegion (BAR0, PCI_Config, 0xC0, 0x05)
                Field (BAR0, ByteAcc, NoLock, Preserve)
                {
                    UBL1,   16, 
                            Offset (0x04), 
                    USBW,   8
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

            Device (USB3)
            {
                Name (_ADR, 0x001D0002)
                OperationRegion (BAR0, PCI_Config, 0xC0, 0x05)
                Field (BAR0, ByteAcc, NoLock, Preserve)
                {
                    UBL1,   16, 
                            Offset (0x04), 
                    USBW,   8
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
                    Return (GPRW (0x0C, 0x03))
                }
            }

            Device (SBRG)
            {
                Name (_ADR, 0x001F0000)
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
                    Name (_HID, EisaId ("SYN0801"))
                    Name (_CID, Package (0x02)
                    {
                        0x00082E4F, 
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

                    Name (CRS1, ResourceTemplate ()
                    {
                        IRQNoFlags ()
                            {12}
                    })
                    Name (CRS2, ResourceTemplate ()
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
                            {12}
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        ShiftLeft (0x01, 0x0A, Local0)
                        If (And (IOST, Local0))
                        {
                            Return (CRS1)
                        }
                        Else
                        {
                            Return (CRS2)
                        }
                    }
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

                Device (UAR1)
                {
                    Name (_UID, 0x01)
                    Name (_HID, EisaId ("PNP0501"))
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (DSTA (0x00))
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        DCNT (0x00, 0x00)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        Return (DCRS (0x00, 0x00))
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        DSRS (Arg0, 0x00)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (CMPR)
                    }

                    Name (CMPR, ResourceTemplate ()
                    {
                        StartDependentFn (0x00, 0x00)
                        {
                            IO (Decode16,
                                0x03F8,             // Range Minimum
                                0x03F8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {4}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03F8,             // Range Minimum
                                0x03F8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x02F8,             // Range Minimum
                                0x02F8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03E8,             // Range Minimum
                                0x03E8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x02E8,             // Range Minimum
                                0x02E8,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        EndDependentFn ()
                    })
                }

                Device (FDC)
                {
                    Name (_HID, EisaId ("PNP0700"))
                    Name (_FDE, Package (0x05)
                    {
                        0x01, 
                        0x00, 
                        0x02, 
                        0x02, 
                        0x02
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (DSTA (0x03))
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        DCNT (0x03, 0x00)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        DCRS (0x03, 0x01)
                        Store (IRQM, IRQE)
                        Store (DMAM, DMAE)
                        Store (IO11, IO21)
                        Store (IO12, IO22)
                        Store (0x06, LEN2)
                        Add (IO21, 0x07, IO31)
                        Store (IO31, IO32)
                        Store (0x01, LEN3)
                        Return (CRS2)
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        DSRS (Arg0, 0x03)
                        CreateWordField (Arg0, 0x11, IRQE)
                        CreateByteField (Arg0, 0x14, DMAE)
                        ENFG (CGLD (0x03))
                        If (IRQE)
                        {
                            FindSetRightBit (IRQE, Local0)
                            Subtract (Local0, 0x01, INTR)
                        }
                        Else
                        {
                            Store (0x00, INTR)
                        }

                        If (DMAE)
                        {
                            FindSetRightBit (DMAE, Local0)
                            Subtract (Local0, 0x01, DMCH)
                        }
                        Else
                        {
                            Store (0x04, DMCH)
                        }

                        EXFG ()
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        StartDependentFn (0x00, 0x00)
                        {
                            IO (Decode16,
                                0x03F0,             // Range Minimum
                                0x03F0,             // Range Maximum
                                0x01,               // Alignment
                                0x06,               // Length
                                )
                            IO (Decode16,
                                0x03F7,             // Range Minimum
                                0x03F7,             // Range Maximum
                                0x01,               // Alignment
                                0x01,               // Length
                                )
                            IRQNoFlags ()
                                {6}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {2}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03F0,             // Range Minimum
                                0x03F0,             // Range Maximum
                                0x01,               // Alignment
                                0x06,               // Length
                                )
                            IO (Decode16,
                                0x03F7,             // Range Minimum
                                0x03F7,             // Range Maximum
                                0x01,               // Alignment
                                0x01,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,2,3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0370,             // Range Minimum
                                0x0370,             // Range Maximum
                                0x01,               // Alignment
                                0x06,               // Length
                                )
                            IO (Decode16,
                                0x0377,             // Range Minimum
                                0x0377,             // Range Maximum
                                0x01,               // Alignment
                                0x01,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,2,3}
                        }
                        EndDependentFn ()
                    })
                }

                Device (LPTE)
                {
                    Method (_HID, 0, NotSerialized)
                    {
                        If (LPTM (0x02))
                        {
                            Return (0x0104D041)
                        }
                        Else
                        {
                            Return (0x0004D041)
                        }
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        Return (DSTA (0x02))
                    }

                    Method (_DIS, 0, NotSerialized)
                    {
                        DCNT (0x02, 0x00)
                    }

                    Method (_CRS, 0, NotSerialized)
                    {
                        DCRS (0x02, 0x01)
                        If (LPTM (0x02))
                        {
                            Store (IRQM, IRQE)
                            Store (DMAM, DMAE)
                            Store (IO11, IO21)
                            Store (IO12, IO22)
                            Store (LEN1, LEN2)
                            Add (IO21, 0x0400, IO31)
                            Store (IO31, IO32)
                            Store (LEN2, LEN3)
                            Return (CRS2)
                        }
                        Else
                        {
                            Return (CRS1)
                        }
                    }

                    Method (_SRS, 1, NotSerialized)
                    {
                        DSRS (Arg0, 0x02)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        If (LPTM (0x02))
                        {
                            Return (EPPR)
                        }
                        Else
                        {
                            Return (LPPR)
                        }
                    }

                    Name (LPPR, ResourceTemplate ()
                    {
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0378,             // Range Minimum
                                0x0378,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0278,             // Range Minimum
                                0x0278,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03BC,             // Range Minimum
                                0x03BC,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0378,             // Range Minimum
                                0x0378,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0278,             // Range Minimum
                                0x0278,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03BC,             // Range Minimum
                                0x03BC,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {}
                        }
                        EndDependentFn ()
                    })
                    Name (EPPR, ResourceTemplate ()
                    {
                        StartDependentFn (0x00, 0x00)
                        {
                            IO (Decode16,
                                0x0378,             // Range Minimum
                                0x0378,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IO (Decode16,
                                0x0778,             // Range Minimum
                                0x0778,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0378,             // Range Minimum
                                0x0378,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IO (Decode16,
                                0x0778,             // Range Minimum
                                0x0778,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,2,3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0278,             // Range Minimum
                                0x0278,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IO (Decode16,
                                0x0678,             // Range Minimum
                                0x0678,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,2,3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03BC,             // Range Minimum
                                0x03BC,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                )
                            IO (Decode16,
                                0x07BC,             // Range Minimum
                                0x07BC,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {3,4,5,6,7,10,11,12}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,2,3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0378,             // Range Minimum
                                0x0378,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IO (Decode16,
                                0x0778,             // Range Minimum
                                0x0778,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,2,3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x0278,             // Range Minimum
                                0x0278,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IO (Decode16,
                                0x0678,             // Range Minimum
                                0x0678,             // Range Maximum
                                0x01,               // Alignment
                                0x08,               // Length
                                )
                            IRQNoFlags ()
                                {}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,2,3}
                        }
                        StartDependentFnNoPri ()
                        {
                            IO (Decode16,
                                0x03BC,             // Range Minimum
                                0x03BC,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                )
                            IO (Decode16,
                                0x07BC,             // Range Minimum
                                0x07BC,             // Range Maximum
                                0x01,               // Alignment
                                0x04,               // Length
                                )
                            IRQNoFlags ()
                                {}
                            DMA (Compatibility, NotBusMaster, Transfer8, )
                                {0,1,2,3}
                        }
                        EndDependentFn ()
                    })
                }

                Device (SIOR)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Method (_UID, 0, NotSerialized)
                    {
                        Return (SPIO)
                    }

                    Name (CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x00,               // Length
                            _Y00)
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x00,               // Length
                            _Y01)
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x00,               // Length
                            _Y02)
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        If (LAnd (LNotEqual (SPIO, 0x03F0), LGreater (SPIO, 0xF0)))
                        {
                            CreateWordField (CRS, \_SB.PCI0.SBRG.SIOR._Y00._MIN, GP10)
                            CreateWordField (CRS, \_SB.PCI0.SBRG.SIOR._Y00._MAX, GP11)
                            CreateByteField (CRS, \_SB.PCI0.SBRG.SIOR._Y00._LEN, GPL1)
                            Store (SPIO, GP10)
                            Store (SPIO, GP11)
                            Store (0x02, GPL1)
                        }

                        If (IO1B)
                        {
                            CreateWordField (CRS, \_SB.PCI0.SBRG.SIOR._Y01._MIN, GP20)
                            CreateWordField (CRS, \_SB.PCI0.SBRG.SIOR._Y01._MAX, GP21)
                            CreateByteField (CRS, \_SB.PCI0.SBRG.SIOR._Y01._LEN, GPL2)
                            Store (IO1B, GP20)
                            Store (IO1B, GP21)
                            Store (IO1L, GPL2)
                        }

                        If (IOXB)
                        {
                            CreateWordField (CRS, \_SB.PCI0.SBRG.SIOR._Y02._MIN, GP30)
                            CreateWordField (CRS, \_SB.PCI0.SBRG.SIOR._Y02._MAX, GP31)
                            CreateByteField (CRS, \_SB.PCI0.SBRG.SIOR._Y02._LEN, GPL3)
                            Store (IOXB, GP30)
                            Store (IOXB, GP31)
                            Store (IOXL, GPL3)
                        }

                        Return (CRS)
                    }
                }

                Name (DCAT, Package (0x15)
                {
                    0x03, 
                    0x02, 
                    0x01, 
                    0x00, 
                    0xFF, 
                    0x0C, 
                    0xFF, 
                    0xFF, 
                    0x0B, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF, 
                    0xFF
                })
                Mutex (MUT0, 0x00)
                Method (ENFG, 1, NotSerialized)
                {
                    Acquire (MUT0, 0x0FFF)
                    Store (Arg0, LDN)
                }

                Method (EXFG, 0, NotSerialized)
                {
                    Release (MUT0)
                }

                Method (LPTM, 1, NotSerialized)
                {
                    ENFG (CGLD (Arg0))
                    And (OPT0, 0x02, Local0)
                    EXFG ()
                    Return (Local0)
                }

                Method (UHID, 1, NotSerialized)
                {
                    If (LEqual (Arg0, 0x01))
                    {
                        ENFG (CGLD (Arg0))
                        And (OPT1, 0x38, Local0)
                        EXFG ()
                        If (Local0)
                        {
                            Return (0x1005D041)
                        }
                    }

                    Return (0x0105D041)
                }

                OperationRegion (IOID, SystemIO, SPIO, 0x02)
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

                Method (CGLD, 1, NotSerialized)
                {
                    Return (DerefOf (Index (DCAT, Arg0)))
                }

                Method (DSTA, 1, NotSerialized)
                {
                    ENFG (CGLD (Arg0))
                    Store (ACTR, Local0)
                    EXFG ()
                    If (LEqual (Local0, 0xFF))
                    {
                        Return (0x00)
                    }

                    And (Local0, 0x01, Local0)
                    Or (IOST, ShiftLeft (Local0, Arg0), IOST)
                    If (Local0)
                    {
                        Return (0x0F)
                    }
                    Else
                    {
                        If (And (ShiftLeft (0x01, Arg0), IOST))
                        {
                            Return (0x0D)
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }
                }

                Method (DCNT, 2, NotSerialized)
                {
                    ENFG (CGLD (Arg0))
                    ShiftLeft (IOAH, 0x08, Local1)
                    Or (IOAL, Local1, Local1)
                    RRIO (Arg0, Arg1, Local1, 0x08)
                    If (LAnd (LLess (DMCH, 0x04), LNotEqual (And (DMCH, 0x03, 
                        Local1), 0x00)))
                    {
                        RDMA (Arg0, Arg1, Increment (Local1))
                    }

                    Store (Arg1, ACTR)
                    EXFG ()
                }

                Name (CRS1, ResourceTemplate ()
                {
                    IO (Decode16,
                        0x0000,             // Range Minimum
                        0x0000,             // Range Maximum
                        0x01,               // Alignment
                        0x00,               // Length
                        _Y05)
                    IRQNoFlags (_Y03)
                        {}
                    DMA (Compatibility, NotBusMaster, Transfer8, _Y04)
                        {}
                })
                CreateWordField (CRS1, \_SB.PCI0.SBRG._Y03._INT, IRQM)
                CreateByteField (CRS1, \_SB.PCI0.SBRG._Y04._DMA, DMAM)
                CreateWordField (CRS1, \_SB.PCI0.SBRG._Y05._MIN, IO11)
                CreateWordField (CRS1, \_SB.PCI0.SBRG._Y05._MAX, IO12)
                CreateByteField (CRS1, \_SB.PCI0.SBRG._Y05._LEN, LEN1)
                Name (CRS2, ResourceTemplate ()
                {
                    IO (Decode16,
                        0x0000,             // Range Minimum
                        0x0000,             // Range Maximum
                        0x01,               // Alignment
                        0x00,               // Length
                        _Y08)
                    IO (Decode16,
                        0x0000,             // Range Minimum
                        0x0000,             // Range Maximum
                        0x01,               // Alignment
                        0x00,               // Length
                        _Y09)
                    IRQNoFlags (_Y06)
                        {6}
                    DMA (Compatibility, NotBusMaster, Transfer8, _Y07)
                        {2}
                })
                CreateWordField (CRS2, \_SB.PCI0.SBRG._Y06._INT, IRQE)
                CreateByteField (CRS2, \_SB.PCI0.SBRG._Y07._DMA, DMAE)
                CreateWordField (CRS2, \_SB.PCI0.SBRG._Y08._MIN, IO21)
                CreateWordField (CRS2, \_SB.PCI0.SBRG._Y08._MAX, IO22)
                CreateByteField (CRS2, \_SB.PCI0.SBRG._Y08._LEN, LEN2)
                CreateWordField (CRS2, \_SB.PCI0.SBRG._Y09._MIN, IO31)
                CreateWordField (CRS2, \_SB.PCI0.SBRG._Y09._MAX, IO32)
                CreateByteField (CRS2, \_SB.PCI0.SBRG._Y09._LEN, LEN3)
                Method (DCRS, 2, NotSerialized)
                {
                    ENFG (CGLD (Arg0))
                    ShiftLeft (IOAH, 0x08, IO11)
                    Or (IOAL, IO11, IO11)
                    Store (IO11, IO12)
                    Subtract (FindSetRightBit (IO11), 0x01, Local0)
                    ShiftLeft (0x01, Local0, LEN1)
                    If (INTR)
                    {
                        ShiftLeft (0x01, INTR, IRQM)
                    }
                    Else
                    {
                        Store (0x00, IRQM)
                    }

                    If (LOr (LGreater (DMCH, 0x03), LEqual (Arg1, 0x00)))
                    {
                        Store (0x00, DMAM)
                    }
                    Else
                    {
                        And (DMCH, 0x03, Local1)
                        ShiftLeft (0x01, Local1, DMAM)
                    }

                    EXFG ()
                    Return (CRS1)
                }

                Method (DSRS, 2, NotSerialized)
                {
                    CreateWordField (Arg0, 0x09, IRQM)
                    CreateByteField (Arg0, 0x0C, DMAM)
                    CreateWordField (Arg0, 0x02, IO11)
                    ENFG (CGLD (Arg1))
                    And (IO11, 0xFF, IOAL)
                    ShiftRight (IO11, 0x08, IOAH)
                    If (IRQM)
                    {
                        FindSetRightBit (IRQM, Local0)
                        Subtract (Local0, 0x01, INTR)
                    }
                    Else
                    {
                        Store (0x00, INTR)
                    }

                    If (DMAM)
                    {
                        FindSetRightBit (DMAM, Local0)
                        Subtract (Local0, 0x01, DMCH)
                    }
                    Else
                    {
                        Store (0x04, DMCH)
                    }

                    EXFG ()
                    DCNT (Arg1, 0x01)
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
                            0x1C,               // Length
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
                            _Y0A)
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x00,               // Length
                            _Y0B)
                        IO (Decode16,
                            0x0860,             // Range Minimum
                            0x0860,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0862,             // Range Minimum
                            0x0862,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0864,             // Range Minimum
                            0x0864,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0866,             // Range Minimum
                            0x0866,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0868,             // Range Minimum
                            0x0868,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x086C,             // Range Minimum
                            0x086C,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        Memory32Fixed (ReadOnly,
                            0xFFF00000,         // Address Base
                            0x00100000,         // Address Length
                            )
                        Memory32Fixed (ReadOnly,
                            0xFFB00000,         // Address Base
                            0x00100000,         // Address Length
                            )
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0A._MIN, GP00)
                        CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0A._MAX, GP01)
                        CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y0A._LEN, GP0L)
                        Store (PMBS, GP00)
                        Store (PMBS, GP01)
                        Store (PMLN, GP0L)
                        If (GPBS)
                        {
                            CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0B._MIN, GP20)
                            CreateWordField (CRS, \_SB.PCI0.SBRG.RMSC._Y0B._MAX, GP21)
                            CreateByteField (CRS, \_SB.PCI0.SBRG.RMSC._Y0B._LEN, GP2L)
                            Store (GPBS, GP20)
                            Store (GPBS, GP21)
                            Store (GPLN, GP2L)
                        }

                        Return (CRS)
                    }
                }

                Device (OMSC)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x00)
                    Name (CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x1100,             // Range Minimum
                            0x1100,             // Range Maximum
                            0x00,               // Alignment
                            0x40,               // Length
                            )
                        IO (Decode16,
                            0x1254,             // Range Minimum
                            0x1254,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x12D4,             // Range Minimum
                            0x12D4,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x1300,             // Range Minimum
                            0x1300,             // Range Maximum
                            0x00,               // Alignment
                            0x76,               // Length
                            )
                        IO (Decode16,
                            0x1377,             // Range Minimum
                            0x1377,             // Range Maximum
                            0x00,               // Alignment
                            0x09,               // Length
                            )
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x00,               // Alignment
                            0x00,               // Length
                            _Y0E)
                        Memory32Fixed (ReadOnly,
                            0x00000000,         // Address Base
                            0x00000000,         // Address Length
                            _Y0C)
                        Memory32Fixed (ReadOnly,
                            0x00000000,         // Address Base
                            0x00000000,         // Address Length
                            _Y0D)
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        If (APIC)
                        {
                            CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y0C._LEN, ML01)
                            CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y0C._BAS, MB01)
                            CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y0D._LEN, ML02)
                            CreateDWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y0D._BAS, MB02)
                            Store (0xFEC00000, MB01)
                            Store (0x1000, ML01)
                            Store (0xFEE00000, MB02)
                            Store (0x1000, ML02)
                        }

                        If (OSFL ()) {}
                        Else
                        {
                            CreateWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y0E._MIN, GP40)
                            CreateWordField (CRS, \_SB.PCI0.SBRG.OMSC._Y0E._MAX, GP41)
                            CreateByteField (CRS, \_SB.PCI0.SBRG.OMSC._Y0E._LEN, GP4L)
                            Store (0x1376, GP40)
                            Store (0x1376, GP41)
                            Store (0x01, GP4L)
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
                            _Y0F)
                        Memory32Fixed (ReadOnly,
                            0x000E0000,         // Address Base
                            0x00020000,         // Address Length
                            _Y10)
                        Memory32Fixed (ReadWrite,
                            0x00100000,         // Address Base
                            0x00000000,         // Address Length
                            _Y11)
                        Memory32Fixed (ReadOnly,
                            0x00000000,         // Address Base
                            0x00000000,         // Address Length
                            _Y12)
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        CreateDWordField (CRS, \_SB.RMEM._Y0F._BAS, BAS1)
                        CreateDWordField (CRS, \_SB.RMEM._Y0F._LEN, LEN1)
                        CreateDWordField (CRS, \_SB.RMEM._Y10._BAS, BAS2)
                        CreateDWordField (CRS, \_SB.RMEM._Y10._LEN, LEN2)
                        CreateDWordField (CRS, \_SB.RMEM._Y11._LEN, LEN3)
                        CreateDWordField (CRS, \_SB.RMEM._Y12._BAS, BAS4)
                        CreateDWordField (CRS, \_SB.RMEM._Y12._LEN, LEN4)
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
                    Name (FGEC, 0x00)
                    Method (_REG, 2, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x03))
                        {
                            Store (Arg1, FGEC)
                        }

                        If (LEqual (OSFL (), 0x01))
                        {
                            Store (0x01, OSEC)
                        }
                        Else
                        {
                            If (LEqual (OSFL (), 0x00))
                            {
                                Store (0x02, OSEC)
                            }
                            Else
                            {
                                If (LEqual (OSFL (), 0x02))
                                {
                                    Store (0x03, OSEC)
                                }
                            }

                            If (LEqual (OSFL (), 0x04))
                            {
                                Store (0x04, OSEC)
                            }
                        }

                        Store (0x98, SSMI)
                    }

                    OperationRegion (ECXP, EmbeddedControl, 0x00, 0x0100)
                    Field (ECXP, ByteAcc, Lock, Preserve)
                    {
                        XIF0,   16, 
                        XIF1,   16, 
                        XIF2,   16, 
                        XIF3,   16, 
                        XIF4,   16, 
                        XIF5,   16, 
                        XIF6,   16, 
                        XIF7,   16, 
                        XIF8,   16, 
                        XIF9,   64, 
                        XIFA,   64, 
                        XIFB,   64, 
                        XIFC,   64, 
                        XST0,   16, 
                        XST1,   16, 
                        XST2,   16, 
                        XST3,   16, 
                        XTP0,   16, 
                        XCIN,   1, 
                            ,   1, 
                        XTIN,   1, 
                                Offset (0x3D), 
                                Offset (0x3E), 
                        XHPP,   7, 
                                Offset (0x3F), 
                                Offset (0x40), 
                        XSEC,   8, 
                        XLPT,   8, 
                                Offset (0xC0), 
                        YIF0,   16, 
                        YIF1,   16, 
                        YIF2,   16, 
                        YIF3,   16, 
                        YIF4,   16, 
                        YIF5,   16, 
                        YIF6,   16, 
                        YIF7,   16, 
                        YIF8,   16, 
                        YIF9,   64, 
                        YIFA,   64, 
                        YIFB,   64, 
                        YIFC,   64, 
                        YST0,   16, 
                        YST1,   16, 
                        YST2,   16, 
                        YST3,   16, 
                        YTP0,   16, 
                        YCIN,   1, 
                            ,   1, 
                        YTIN,   1
                    }

                    Name (_GPE, 0x1C)
                    Name (_PRW, Package (0x02)
                    {
                        0x1C, 
                        0x03
                    })
                    Method (_Q00, 0, NotSerialized)
                    {
                    }

                    Method (_Q18, 0, NotSerialized)
                    {
                        Store ("Trip Point Event", Debug)
                        Notify (\_SB.PCI0.BAT0, 0x80)
                    }

                    Method (_Q06, 0, NotSerialized)
                    {
                        Store (0x06, DBG8)
                        Store ("Battery Change Event", Debug)
                        If (LEqual (OSFL (), 0x01))
                        {
                            If (BTIN)
                            {
                                Notify (\_SB.PCI0.BAT0, 0x01)
                            }
                            Else
                            {
                                Notify (\_SB.PCI0.BAT0, 0x00)
                            }

                            Notify (\_SB.PCI0.BAT0, 0x80)
                            Notify (\_SB.PCI0, 0x00)
                        }

                        If (LEqual (OSFL (), 0x02))
                        {
                            Store (0x01, FAKE)
                            Notify (\_SB.PCI0.AC0, 0x00)
                            Store (0x00, FAKE)
                            Notify (\_SB.PCI0.AC0, 0x00)
                            If (BTIN)
                            {
                                Store (0x22, P378)
                                Notify (\_SB.PCI0.BAT0, 0x00)
                            }
                            Else
                            {
                                Store (0x23, P378)
                                Notify (\_SB.PCI0.BAT0, 0x03)
                            }

                            Notify (\_SB.PCI0.BAT0, 0x81)
                            Notify (\_SB.PCI0.BAT0, 0x80)
                        }

                        If (LOr (LEqual (OSFL (), 0x00), LEqual (OSFL (), 0x04)))
                        {
                            Store (0x22, P378)
                            Sleep (0x01F4)
                            If (BTIN)
                            {
                                Notify (\_SB.PCI0.BAT0, 0x01)
                            }
                            Else
                            {
                                Notify (\_SB.PCI0.BAT0, 0x00)
                            }

                            Notify (\_SB.PCI0.BAT0, 0x80)
                        }
                    }

                    Method (_Q07, 0, NotSerialized)
                    {
                        Store ("AC Change", Debug)
                        Store (0x07, DBG8)
                        If (LEqual (OSFL (), 0x01))
                        {
                            Store (0x00, FAKE)
                            Notify (\_SB.PCI0.AC0, 0x00)
                        }

                        If (LEqual (OSFL (), 0x02))
                        {
                            Store (0x00, FAKE)
                            Notify (\_SB.PCI0.AC0, 0x00)
                        }

                        If (LOr (LEqual (OSFL (), 0x00), LEqual (OSFL (), 0x04)))
                        {
                            Notify (\_SB.PCI0.AC0, 0x80)
                            Notify (\_SB.PCI0.BAT0, 0x80)
                        }
                    }

                    Method (_Q0A, 0, NotSerialized)
                    {
                        Store (0xF1, DBG8)
                        Notify (\_SB.SLPB, 0x80)
                    }

                    Method (_Q0C, 0, NotSerialized)
                    {
                        Store ("FN+F3 Event", Debug)
                        Store (0x82, SSMI)
                    }

                    Method (_Q0D, 0, NotSerialized)
                    {
                        Store ("FN+F4 Event", Debug)
                        If (LEqual (\_SB.PCI0.AGP.VGA.SWIT, 0x00))
                        {
                            If (LEqual (\_SB.PCI0.AGP.VGA.GDFG, 0x01))
                            {
                                Notify (\_SB.PCI0.AGP.VGA, 0x80)
                                Store (0x00, \_SB.PCI0.AGP.VGA.GDFG)
                                Sleep (0x07D0)
                            }

                            If (LEqual (\_SB.PCI0.AGP.VGA.GDTS, 0x00))
                            {
                                If (LEqual (\_SB.PCI0.AGP.VGA.GDGS, 0x01))
                                {
                                    Store (0x00, \_SB.PCI0.AGP.VGA.LCD._DGS)
                                    Store (0x01, \_SB.PCI0.AGP.VGA.CRT._DGS)
                                }

                                If (LEqual (\_SB.PCI0.AGP.VGA.GDGS, 0x02))
                                {
                                    Store (0x01, \_SB.PCI0.AGP.VGA.LCD._DGS)
                                    Store (0x00, \_SB.PCI0.AGP.VGA.CRT._DGS)
                                }

                                If (LEqual (\_SB.PCI0.AGP.VGA.GDGS, 0x03))
                                {
                                    Store (0x01, \_SB.PCI0.AGP.VGA.LCD._DGS)
                                    Store (0x01, \_SB.PCI0.AGP.VGA.CRT._DGS)
                                }

                                Notify (\_SB.PCI0.AGP.VGA, 0x80)
                                If (LEqual (\_SB.PCI0.AGP.VGA.GDGS, 0x03))
                                {
                                    Store (0x01, \_SB.PCI0.AGP.VGA.GDGS)
                                }
                                Else
                                {
                                    Add (0x01, \_SB.PCI0.AGP.VGA.GDGS, \_SB.PCI0.AGP.VGA.GDGS)
                                }
                            }
                        }
                    }

                    Method (_Q10, 0, NotSerialized)
                    {
                        Store ("FN+F7 Event", Debug)
                        Store (0x86, SSMI)
                    }

                    Method (_Q11, 0, NotSerialized)
                    {
                        Store ("FN+F8 Event", Debug)
                        Store (0x87, SSMI)
                    }

                    Method (_Q16, 0, NotSerialized)
                    {
                        Store (0x16, DBG8)
                        Store (0x01, LIDS)
                        Notify (\_SB.PCI0.SBRG.LID, 0x80)
                    }

                    Method (_Q19, 0, NotSerialized)
                    {
                        Store (0x19, DBG8)
                        Store (0x00, LIDS)
                        Notify (\_SB.PCI0.SBRG.LID, 0x80)
                    }

                    Method (_Q1E, 0, NotSerialized)
                    {
                        Store (0x8E, SSMI)
                    }

                    Method (_Q1F, 0, NotSerialized)
                    {
                        Store (0x8F, SSMI)
                    }

                    Method (_Q20, 0, NotSerialized)
                    {
                        Store (0x90, SSMI)
                    }

                    Method (_Q21, 0, NotSerialized)
                    {
                        Store (0x91, SSMI)
                    }

                    Method (_Q22, 0, NotSerialized)
                    {
                        Store (0x92, SSMI)
                    }

                    Method (_Q23, 0, NotSerialized)
                    {
                        Store (0x93, SSMI)
                    }

                    Method (_Q24, 0, NotSerialized)
                    {
                        Store (0x94, SSMI)
                    }

                    Method (_Q25, 0, NotSerialized)
                    {
                        Store (0x95, SSMI)
                    }

                    Method (_Q26, 0, NotSerialized)
                    {
                        Store (0x96, SSMI)
                    }

                    Method (_Q27, 0, NotSerialized)
                    {
                        Store (0x69, THPP)
                        Notify (\_TZ.THRM, 0x80)
                    }

                    Method (_Q2C, 0, NotSerialized)
                    {
                        Store (0x2C, DBG8)
                        If (LEqual (GP41, 0x01))
                        {
                            Store (0x01, \_SB.PCI0.IDE0.SESM)
                            Store (0x01, GP39)
                            Notify (\_SB.PCI0.IDE0.CHN1.DRV0, 0x01)
                        }
                        Else
                        {
                            Store (0x00, \_SB.PCI0.IDE0.SESM)
                            Store (0x00, GP39)
                            Sleep (0x07D0)
                            Notify (\_SB.PCI0.IDE0.CHN1.DRV0, 0x00)
                        }
                    }

                    Method (_Q2D, 0, NotSerialized)
                    {
                        If (LEqual (GP40, 0x01))
                        {
                            Store (0x01, DBG8)
                            Store (0x01, GP42)
                            Store (0x01, GP36)
                            Notify (\_SB.PCI0.SBRG.FDC, 0x01)
                        }
                        Else
                        {
                            Store (0x00, DBG8)
                            Store (0x00, GP36)
                            Store (0x00, GP42)
                            Notify (\_SB.PCI0.SBRG.FDC, 0x00)
                        }
                    }

                    Method (_Q2E, 0, NotSerialized)
                    {
                        Store (0x9B, SSMI)
                        If (LEqual (SMOD, 0x01))
                        {
                            Store (0x00, SMOD)
                        }
                        Else
                        {
                            Store (0x01, SMOD)
                        }

                        Notify (\_PR.CPU1, 0x80)
                    }
                }

                Device (\_SB.PCI0.BAT0)
                {
                    Name (_HID, EisaId ("PNP0C0A"))
                    Name (_UID, 0x00)
                    Name (_PCL, Package (0x01)
                    {
                        \_SB.PCI0.SBRG.EC0
                    })
                    Name (PAK1, Package (0x0D)
                    {
                        0x00, 
                        0x0C56, 
                        0x0C56, 
                        0x00, 
                        0x2A30, 
                        0x013B, 
                        0x9D, 
                        0x10, 
                        0x08, 
                        "259IA", 
                        "001", 
                        "LiON", 
                        "OEM"
                    })
                    Method (_BIF, 0, NotSerialized)
                    {
                        Store ("BIf", Debug)
                        If (LOr (LEqual (OSFL (), 0x00), LEqual (OSFL (), 0x04)))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.XIF0, Index (PAK1, 0x00))
                            Store (\_SB.PCI0.SBRG.EC0.XIF1, Index (PAK1, 0x01))
                            Store (\_SB.PCI0.SBRG.EC0.XIF2, Local0)
                            Store (Local0, Index (PAK1, 0x02))
                            Store (\_SB.PCI0.SBRG.EC0.XIF3, Index (PAK1, 0x03))
                            Store (\_SB.PCI0.SBRG.EC0.XIF4, Index (PAK1, 0x04))
                            Store (Divide (Local0, 0x0A, ), Index (PAK1, 0x05))
                            Store (Divide (Local0, 0x14, ), Index (PAK1, 0x06))
                            Store (\_SB.PCI0.SBRG.EC0.XIF7, Index (PAK1, 0x07))
                        }
                        Else
                        {
                            Store (0x99, SSMI)
                            Store (BIF0, Index (PAK1, 0x00))
                            Store (BIF1, Index (PAK1, 0x01))
                            Store (BIF2, Local0)
                            Store (Local0, Index (PAK1, 0x02))
                            Store (BIF3, Index (PAK1, 0x03))
                            Store (BIF4, Index (PAK1, 0x04))
                            Store (Divide (Local0, 0x0A, ), Index (PAK1, 0x05))
                            Store (Divide (Local0, 0x14, ), Index (PAK1, 0x06))
                            Store (BIF7, Index (PAK1, 0x07))
                        }

                        Return (PAK1)
                    }

                    Name (BFB0, Package (0x04)
                    {
                        0x00, 
                        0xFFFFFFFF, 
                        0x1034, 
                        0x2A30
                    })
                    Method (_BST, 0, NotSerialized)
                    {
                        Store ("BST Start", Debug)
                        If (LOr (LEqual (OSFL (), 0x00), LEqual (OSFL (), 0x04)))
                        {
                            Store (\_SB.PCI0.SBRG.EC0.XST0, Index (BFB0, 0x00))
                            Store (\_SB.PCI0.SBRG.EC0.XST2, Index (BFB0, 0x02))
                            Store (\_SB.PCI0.SBRG.EC0.XST3, Index (BFB0, 0x03))
                        }
                        Else
                        {
                            Store (0x9A, SSMI)
                            Store (BST0, Index (BFB0, 0x00))
                            Store (BST2, Index (BFB0, 0x02))
                            Store (BST3, Index (BFB0, 0x03))
                        }

                        Store ("BST End", Debug)
                        Return (BFB0)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        Store ("BAT_STA Start", Debug)
                        If (LOr (LEqual (OSFL (), 0x00), LEqual (OSFL (), 0x04)))
                        {
                            If (LEqual (\_SB.PCI0.SBRG.EC0.FGEC, 0x00))
                            {
                                Store (0x98, SSMI)
                                Store (BTIN, Local0)
                            }
                            Else
                            {
                                Store (\_SB.PCI0.SBRG.EC0.XTIN, Local0)
                            }

                            If (Local0)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x0F)
                            }
                        }
                        Else
                        {
                            Store (0x98, SSMI)
                            Store (BTIN, Local0)
                            If (Local0)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x0F)
                            }

                            Store ("BAT_STA END", Debug)
                        }
                    }
                }

                Device (\_SB.PCI0.AC0)
                {
                    Name (_HID, "ACPI0003")
                    Name (_PCL, Package (0x01)
                    {
                        \_SB.PCI0.SBRG.EC0
                    })
                    Method (_PSR, 0, NotSerialized)
                    {
                        If (LNotEqual (FAKE, 0x00))
                        {
                            Return (0x00)
                        }
                        Else
                        {
                            If (LOr (LEqual (OSFL (), 0x00), LEqual (OSFL (), 0x04)))
                            {
                                Store (\_SB.PCI0.SBRG.EC0.XCIN, Local0)
                            }
                            Else
                            {
                                Store (ACIN, Local0)
                            }

                            Return (Local0)
                        }
                    }
                }

                Scope (\_TZ)
                {
                    ThermalZone (THRM)
                    {
                        Method (KELV, 1, NotSerialized)
                        {
                            If (LGreater (Arg0, 0x7F))
                            {
                                XOr (Arg0, 0xFF, Local0)
                                Add (Local0, 0x01, Local0)
                                Multiply (Local0, 0x0A, Local0)
                                Subtract (0x0AAC, Local0, Local1)
                            }
                            Else
                            {
                                Multiply (Arg0, 0x0A, Local0)
                                Add (Local0, 0x0AAC, Local1)
                            }

                            Return (Local1)
                        }

                        Method (_TMP, 0, NotSerialized)
                        {
                            Return (KELV (THPP))
                        }

                        Method (_CRT, 0, NotSerialized)
                        {
                            Return (KELV (0x55))
                        }
                    }
                }

                Name (LIDS, 0x01)
                Device (\_SB.PCI0.SBRG.LID)
                {
                    Name (_HID, EisaId ("PNP0C0D"))
                    Name (_PRW, Package (0x02)
                    {
                        0x0B, 
                        0x04
                    })
                    Method (_LID, 0, NotSerialized)
                    {
                        Return (LIDS)
                    }
                }

                Device (\_SB.SLPB)
                {
                    Name (_HID, EisaId ("PNP0C0E"))
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0B)
                    }

                    Method (SBEV, 0, NotSerialized)
                    {
                        If (SLPS)
                        {
                            Store (0x00, SLPS)
                            Notify (SLPB, 0x02)
                        }
                        Else
                        {
                            Store (0x01, SLPS)
                            Notify (SLPB, 0x80)
                        }
                    }

                    Name (_PRW, Package (0x02)
                    {
                        0x0F, 
                        0x04
                    })
                }

                Scope (\)
                {
                    OperationRegion (PMRG, SystemIO, 0x0400, 0x80)
                    Field (PMRG, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x01), 
                        WWAK,   8, 
                                Offset (0x04), 
                        SCIF,   1, 
                                Offset (0x06), 
                        RTCS,   8, 
                                Offset (0x10), 
                        THRT,   8, 
                                Offset (0x30), 
                            ,   3, 
                        LUSB,   1, 
                        SLPE,   1
                    }

                    OperationRegion (OPR3, SystemIO, 0xB2, 0x02)
                    Field (OPR3, ByteAcc, NoLock, Preserve)
                    {
                        SSMI,   8
                    }

                    OperationRegion (OPR2, SystemIO, 0x0378, 0x02)
                    Field (OPR2, ByteAcc, NoLock, Preserve)
                    {
                        P378,   8
                    }

                    OperationRegion (GPBA, SystemIO, GPBS, 0x40)
                    Field (GPBA, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x38), 
                        GP32,   1, 
                        GP33,   1, 
                        GP34,   1, 
                        GP35,   1, 
                        GP36,   1, 
                        GP37,   1, 
                        GP38,   1, 
                        GP39,   1, 
                        GP40,   1, 
                        GP41,   1, 
                        GP42,   1, 
                        GP43,   1
                    }

                    Mutex (ECKP, 0x00)
                    Name (FGEC, 0x00)
                    Name (TEM1, 0x00)
                    Name (THPP, 0x4B)
                    Name (FAKE, 0x00)
                    Name (SLPS, 0x00)
                    Name (SMOD, 0x00)
                    Field (BIOS, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x50), 
                        BIF0,   16, 
                        BIF1,   16, 
                        BIF2,   16, 
                        BIF3,   16, 
                        BIF4,   16, 
                        BIF5,   16, 
                        BIF6,   16, 
                        BIF7,   16, 
                        BIF8,   16, 
                        BIF9,   64, 
                        BIFA,   64, 
                        BIFB,   64, 
                        BIFC,   64, 
                        BST0,   16, 
                        BST1,   16, 
                        BST2,   16, 
                        BST3,   16, 
                        BTP0,   16, 
                        ACIN,   1, 
                            ,   1, 
                        BTIN,   1, 
                                Offset (0x90), 
                        OSEC,   8, 
                        SLPT,   8, 
                        BTNO,   8, 
                        GVCS,   8, 
                                Offset (0xC0), 
                        ZIF0,   16, 
                        ZIF1,   16, 
                        ZIF2,   16, 
                        ZIF3,   16, 
                        ZIF4,   16, 
                        ZIF5,   16, 
                        ZIF6,   16, 
                        ZIF7,   16, 
                        ZIF8,   16, 
                        ZIF9,   64, 
                        ZIFA,   64, 
                        ZIFB,   64, 
                        ZIFC,   64, 
                        ZST0,   16, 
                        ZST1,   16, 
                        ZST2,   16, 
                        ZST3,   16, 
                        ZTP0,   16, 
                        ZCIN,   1, 
                            ,   1, 
                        ZTIN,   1
                    }
                }
            }

            Device (AGP)
            {
                Name (_ADR, 0x00010000)
                Device (VGA)
                {
                    Name (_ADR, 0x00)
                    Method (_DOS, 1, NotSerialized)
                    {
                        Store (Arg0, SWIT)
                    }

                    Name (_DOD, Package (0x02)
                    {
                        0x00010100, 
                        0x00010110
                    })
                    Device (CRT)
                    {
                        Name (_ADR, 0x0100)
                        Name (_DCS, 0x1F)
                        Name (_DGS, 0x01)
                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }

                    Device (LCD)
                    {
                        Name (_ADR, 0x0110)
                        Name (_DCS, 0x1F)
                        Name (_DGS, 0x01)
                        Method (_DSS, 1, NotSerialized)
                        {
                        }

                        Method (_BCM, 1, NotSerialized)
                        {
                        }

                        Name (PBCL, Package (0x07)
                        {
                            0x50, 
                            0x32, 
                            0x14, 
                            0x28, 
                            0x3C, 
                            0x50, 
                            0x64
                        })
                        Method (_BCL, 0, NotSerialized)
                        {
                            Return (PBCL)
                        }
                    }

                    Name (SWIT, 0x00)
                    Name (GDCS, 0x02)
                    Name (GDGS, 0x01)
                    Name (GDTS, 0x00)
                    Name (GDFG, 0x01)
                }
            }
        }

        Scope (\_GPE)
        {
            Method (_L0B, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.P0P1, 0x02)
                Notify (\_SB.PCI0.P0P1.RTL, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }

            Method (_L05, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.MODM, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }

            Method (_L03, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.USB1, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }

            Method (_L04, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.USB2, 0x02)
                Notify (\_SB.PWRB, 0x02)
            }

            Method (_L0C, 0, NotSerialized)
            {
                Notify (\_SB.PCI0.USB3, 0x02)
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

    Scope (\_SB)
    {
        OperationRegion (\_SB.PCI0.SBRG.IROR, PCI_Config, 0x00, 0xFF)
        Field (\_SB.PCI0.SBRG.IROR, ByteAcc, NoLock, Preserve)
        {
                    Offset (0x60), 
            PIRA,   8, 
            PIRB,   8, 
            PIRC,   8, 
            PIRD,   8, 
                    Offset (0x68), 
            PIRE,   8, 
            PIRF,   8, 
            PIRG,   8, 
            PIRH,   8
        }

        Name (BUFA, ResourceTemplate ()
        {
            IRQ (Level, ActiveLow, Shared, _Y13)
                {15}
        })
        CreateWordField (BUFA, \_SB._Y13._INT, ICRS)
        Method (LSTA, 1, NotSerialized)
        {
            And (Arg0, 0x80, Local0)
            If (Local0)
            {
                Return (0x09)
            }
            Else
            {
                Return (0x0B)
            }
        }

        Method (LCRS, 1, NotSerialized)
        {
            And (Arg0, 0x0F, Local0)
            ShiftLeft (0x01, Local0, ICRS)
            Return (BUFA)
        }

        Method (LSRS, 1, NotSerialized)
        {
            CreateWordField (Arg0, 0x01, ISRS)
            FindSetRightBit (ISRS, Local0)
            Return (Decrement (Local0))
        }

        Method (LDIS, 1, NotSerialized)
        {
            Return (Or (Arg0, 0x80))
        }

        Device (LNKA)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x01)
            Method (_STA, 0, NotSerialized)
            {
                Return (LSTA (PIRA))
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSA)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Store (LDIS (PIRA), PIRA)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Return (LCRS (PIRA))
            }

            Method (_SRS, 1, NotSerialized)
            {
                Store (LSRS (Arg0), PIRA)
            }
        }

        Device (LNKB)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x02)
            Method (_STA, 0, NotSerialized)
            {
                Return (LSTA (PIRB))
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSB)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Store (LDIS (PIRB), PIRB)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Return (LCRS (PIRB))
            }

            Method (_SRS, 1, NotSerialized)
            {
                Store (LSRS (Arg0), PIRB)
            }
        }

        Device (LNKC)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x03)
            Method (_STA, 0, NotSerialized)
            {
                Return (LSTA (PIRC))
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSC)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Store (LDIS (PIRC), PIRC)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Return (LCRS (PIRC))
            }

            Method (_SRS, 1, NotSerialized)
            {
                Store (LSRS (Arg0), PIRC)
            }
        }

        Device (LNKD)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x04)
            Method (_STA, 0, NotSerialized)
            {
                Return (LSTA (PIRD))
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSD)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Store (LDIS (PIRD), PIRD)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Return (LCRS (PIRD))
            }

            Method (_SRS, 1, NotSerialized)
            {
                Store (LSRS (Arg0), PIRD)
            }
        }

        Device (LNKE)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x05)
            Method (_STA, 0, NotSerialized)
            {
                Return (LSTA (PIRE))
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSE)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Store (LDIS (PIRE), PIRE)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Return (LCRS (PIRE))
            }

            Method (_SRS, 1, NotSerialized)
            {
                Store (LSRS (Arg0), PIRE)
            }
        }

        Device (LNKF)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x06)
            Method (_STA, 0, NotSerialized)
            {
                Return (LSTA (PIRF))
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSF)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Store (LDIS (PIRF), PIRF)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Return (LCRS (PIRF))
            }

            Method (_SRS, 1, NotSerialized)
            {
                Store (LSRS (Arg0), PIRF)
            }
        }

        Device (LNKG)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x07)
            Method (_STA, 0, NotSerialized)
            {
                Return (LSTA (PIRG))
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSG)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Store (LDIS (PIRG), PIRG)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Return (LCRS (PIRG))
            }

            Method (_SRS, 1, NotSerialized)
            {
                Store (LSRS (Arg0), PIRG)
            }
        }

        Device (LNKH)
        {
            Name (_HID, EisaId ("PNP0C0F"))
            Name (_UID, 0x08)
            Method (_STA, 0, NotSerialized)
            {
                Return (LSTA (PIRH))
            }

            Method (_PRS, 0, NotSerialized)
            {
                Return (PRSH)
            }

            Method (_DIS, 0, NotSerialized)
            {
                Store (LDIS (PIRH), PIRH)
            }

            Method (_CRS, 0, NotSerialized)
            {
                Return (LCRS (PIRH))
            }

            Method (_SRS, 1, NotSerialized)
            {
                Store (LSRS (Arg0), PIRH)
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
                    0x000D0000,         // Range Minimum
                    0x000D3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D4000,         // Range Minimum
                    0x000D6FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D7000,         // Range Minimum
                    0x000D7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000DE000,         // Range Minimum
                    0x000DFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00002000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0x00000000,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, _Y14, AddressRangeMemory, TypeStatic)
            })
            CreateDWordField (CRS, \_SB.PCI0._Y14._MIN, MIN6)
            CreateDWordField (CRS, \_SB.PCI0._Y14._MAX, MAX6)
            CreateDWordField (CRS, \_SB.PCI0._Y14._LEN, LEN6)
            Method (_CRS, 0, NotSerialized)
            {
                Store (MG2B, MIN6)
                Store (MG2L, LEN6)
                Store (MG2L, Local0)
                Add (MIN6, Decrement (Local0), MAX6)
                Return (CRS)
            }
        }
    }

    If (SS1)
    {
        Name (\_SB.PCI0._S1D, 0x02)
        Name (\_SB.PCI0.P0P1._S1D, 0x02)
        Name (\_SB.PCI0.USB1._S1D, 0x02)
        Name (\_SB.PCI0.USB2._S1D, 0x02)
        Name (\_SB.PCI0.USB3._S1D, 0x02)
    }

    If (SS3)
    {
        Name (\_SB.PCI0._S3D, 0x02)
        Name (\_SB.PCI0.P0P1._S3D, 0x02)
        Name (\_SB.PCI0.USB1._S3D, 0x02)
        Name (\_SB.PCI0.USB2._S3D, 0x02)
        Name (\_SB.PCI0.USB3._S3D, 0x02)
    }

    If (SS4)
    {
        Name (\_SB.PCI0._S4D, 0x02)
        Name (\_SB.PCI0.P0P1._S4D, 0x02)
    }

    Method (_PTS, 1, NotSerialized)
    {
        Store (Arg0, DBG8)
        If (LEqual (Arg0, 0x04))
        {
            Store (0x00, SMOD)
            Notify (\_PR.CPU1, 0x80)
            Sleep (0x03E8)
        }

        PTS (Arg0)
        Store (0x00, Index (WAKP, 0x00))
        Store (0x00, Index (WAKP, 0x01))
        If (LEqual (Arg0, 0x05))
        {
            Store (0x01, SLPE)
        }
    }

    Name (SLID, 0x01)
    Method (_WAK, 1, NotSerialized)
    {
        ShiftLeft (Arg0, 0x04, DBG8)
        Store (0x01, SLID)
        WAK (Arg0)
        If (DerefOf (Index (WAKP, 0x00)))
        {
            Store (0x00, Index (WAKP, 0x01))
        }
        Else
        {
            Store (Arg0, Index (WAKP, 0x01))
        }

        If (MCTH (\_OS, "Microsoft Windows"))
        {
            If (LEqual (Arg0, 0x04))
            {
                Notify (\_SB.PWRB, 0x02)
            }
        }

        If (LEqual (Arg0, 0x04))
        {
            Notify (\_SB.PWRB, 0x02)
            If (LEqual (OSFL (), 0x01))
            {
                Store (0x01, OSEC)
            }
            Else
            {
                If (LEqual (OSFL (), 0x00))
                {
                    Store (0x02, OSEC)
                }
                Else
                {
                    If (LEqual (OSFL (), 0x02))
                    {
                        Store (0x03, OSEC)
                    }
                }

                If (LEqual (OSFL (), 0x04))
                {
                    Store (0x04, OSEC)
                }
            }

            Store (0x98, SSMI)
        }

        If (LEqual (Arg0, 0x03)) {}
        Return (WAKP)
    }

    Name (\_S0, Package (0x04)
    {
        0x00, 
        0x00, 
        0x00, 
        0x00
    })
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
            0x07, 
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
        If (Arg0) {}
    }

    Method (WAK, 1, NotSerialized)
    {
    }
}


```

Thanks in advance to help me.

---

