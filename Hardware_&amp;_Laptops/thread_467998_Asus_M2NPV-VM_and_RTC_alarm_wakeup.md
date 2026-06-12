---
title: "Asus M2NPV-VM and RTC alarm wakeup"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by Henk Poley on 2007-06-08
I am having troubles setting the wakeup alarm time on the Asus M2NPV-VM motherboard. I'm running the most recent BIOS version and kernel 2.6.20-something from ubuntu. 

Using /proc/acpi/alarm doesn't seem do much. Though when I use the + operator -to setup an offset wakeup time- it seems to reset the system clock to 1 jan 2007 00:00:00. 

And using the program nvram-wakeup needs a reboot on this motherboard. Which isn't that much of a problem, wouldn't the system just hang on reboot-bootup (DVD spins up but that's it, nothing on the screen).

Since both problems seem ACPI related, I've jumped into the DSDT.

For the /sys/acpi/alarm problem the apropriate part of the DSDT reads:
```
                Device (RTC)
                {
                    Name (_HID, EisaId ("PNP0B00"))
                    Name (ATT0, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x00,               // Alignment
                            0x04,               // Length
                            )
                        IRQNoFlags ()
                            {8}
                    })
                    Name (ATT1, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x00,               // Alignment
                            0x04,               // Length
                            )
                    })
                    Method (_CRS, 0, NotSerialized)
                    {
                        If (LEqual (OSFX, 0x03))
                        {
                            If (HPTF)
                            {
                                Return (ATT1)
                            }
                            Else
                            {
                                Return (ATT0)
                            }
                        }
                        Else
                        {
                            Return (ATT0)
                        }
                    }
                }
```

According to the ACPI 3.0 specs the DSDT either needs to define the ACPI methods _STS and _EN for the RTC device, or it just point to the RTC device itself and let the OS figure it out. They seem to have chosen for the latter case on this MB. The Names ATT0 / ATT1 both 'point' to RTC device, or at least RTC_CRS (Current Resource Settings) returns either of them.

How to interpret the ATT0/1 Names?

The reboot problem is still a mystery to me, but it's probably somewhere in there as well.

---

### Post by Henk Poley on 2007-06-09
Still looks like it's RTC related. Kernel 2.6.21 contains quite some fixes for a lot of RTC chips, some of them mention hangs on reboot. When I tried running vanilla 2.6.21.4 (With 'Y' to "PC-Style RTC [..]" in the kernel config) reboots went fine :-)

Current problem: getting the nvidia driver working. Using the ubuntu packages doesn't seem to work (they are built for 2.6.20.x). I'll probably need to build the nividia kernel module myself.

---

### Post by Henk Poley on 2007-06-10
Hmm, building and running the nvidia drivers made the reboot problem come back. Aparently it isn't (entierly) related to the RTC after all.

---

### Post by Henk Poley on 2007-06-10
I have "fixed" this problem by disabling Cool'n'Quiet in the BIOS. Reboots now work. Re-enabled CnQ and reboots still work :-? (with linux-image-2.6.20-16-generic & nvidia-glx-new_1.0.9755+2.6.20.5-16.28_amd64)

Ah well.. at least it's working now :-)

---

