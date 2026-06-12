---
title: "CPU Frequency scalining not working"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by thwint on 2007-11-27
Hi all,
Like so many other people around I have a problem with frequency scaling.

Reading many different posts, bug reports, howtos ... I was not able to solve the problem.

I'm running Hardy on a Fujitsu-Siemens Lifebook E8400.

According to cpufreq-info my CPU is recognized correctly it tells me that the frequency should be within 800 MHz and 800 MHz. 
It is possible to change the governor, but the speed is not changeable.
```

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.80 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, powersave, ondemand, userspace, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.80 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, powersave, ondemand, userspace, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).

```

Also the /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq have the same value.

Grep for ACPI in dmesg has the following result:
```
[    0.000000]  BIOS-e820: 000000009f6d0000 - 000000009f6df000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009f6df000 - 000000009f6e3000 (ACPI NVS)
[    0.000000] ACPI: RSDP signature @ 0xC00F6360 checksum 0
[    0.000000] ACPI: RSDP 000F6360, 0024 (r2 FUJ   )
[    0.000000] ACPI: XSDT 9F6D4E62, 007C (r1 FSC    PC        1080000 FUJ       100)
[    0.000000] ACPI: SSDT 9F6DCD6B, 02D1 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: FACP 9F6DD03C, 00F4 (r3 FSC    PC        1080000 FUJ       100)
[    0.000000] ACPI: DSDT 9F6D4EDE, 7E8D (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: FACS 9F6E2FC0, 0040
[    0.000000] ACPI: HPET 9F6DD130, 0038 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: MCFG 9F6DD168, 003C (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: SSDT 9F6DD1A4, 04EF (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: SSDT 9F6DD693, 01CA (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: SSDT 9F6DD85D, 10E2 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: SSDT 9F6DE93F, 0447 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: APIC 9F6DED86, 0068 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: BOOT 9F6DEDEE, 0028 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[    0.000000] ACPI: SLIC 9F6DEE16, 0176 (r1 FSC    PC        1080000 FUJ       100)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[   27.856978] ACPI: Core revision 20070126
[   27.857023] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.169292] ACPI: bus type pci registered
[   28.171331] ACPI: EC: Look up EC in DSDT
[   28.172195] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   28.173714] ACPI Error (tbinstal-0134): Table has invalid signature [    ], must be SSDT, PSDT or OEMx [20070126]
[   28.173723] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_._INI] (Node df839cf0), AE_BAD_SIGNATURE
[   28.177270] ACPI: Interpreter enabled
[   28.177272] ACPI: (supports S0 S3 S4 S5)
[   28.177291] ACPI: Using IOAPIC for interrupt routing
[   28.186796] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   28.186846] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.189012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.189329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   28.189469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   28.189608] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   28.189770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   28.193277] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   28.193397] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   28.193513] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   28.193630] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   28.193746] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   28.193861] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   28.193976] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   28.194122] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   28.194266] pnp: PnP ACPI init
[   28.194273] ACPI: bus type pnp registered
[   28.199165] pnp: PnP ACPI: found 12 devices
[   28.199168] ACPI: ACPI bus type pnp unregistered
[   28.199172] PnPBIOS: Disabled by ACPI PNP
[   28.199218] PCI: Using ACPI for IRQ routing
[   28.419709] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.419743] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   28.419776] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   28.419810] ACPI: PCI Interrupt 0000:1c:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.419833] ACPI: PCI Interrupt 0000:1c:03.1[A] -> GSI 16 (level, low) -> IRQ 16
[   30.693756] ACPI: SSDT 9F6DFDD2, 0238 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[   30.694003] ACPI: SSDT 9F6E02D2, 046E (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[   30.694369] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   30.694588] ACPI: SSDT 9F6E021A, 00B8 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[   30.694818] ACPI: SSDT 9F6E0740, 0047 (r1 FUJ    FJNB1CF   1080000 FUJ       100)
[   30.695193] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   30.696241] ACPI: Thermal Zone [TZ00] (27 C)
[   30.696636] ACPI: Thermal Zone [TZ01] (27 C)
[    3.312000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 22 (level, low) -> IRQ 19
[    3.416000] ACPI: PCI Interrupt 0000:00:1a.1[A] -> GSI 22 (level, low) -> IRQ 19
[    3.520000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 22 (level, low) -> IRQ 19
[    3.628000] ACPI: PCI Interrupt 0000:00:1d.1[A] -> GSI 22 (level, low) -> IRQ 19
[    3.732000] ACPI: PCI Interrupt 0000:00:1a.7[B] -> GSI 23 (level, low) -> IRQ 20
[    3.840000] ACPI: PCI Interrupt 0000:00:1d.7[B] -> GSI 23 (level, low) -> IRQ 20
[    3.948000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 20 (level, low) -> IRQ 21
[    4.616000] ACPI: PCI Interrupt 0000:1c:03.4[A] -> GSI 16 (level, low) -> IRQ 16
[    4.616000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 20 (level, low) -> IRQ 21
[    6.788000] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 16 (level, low) -> IRQ 16
[    6.912000] ACPI: PCI Interrupt 0000:00:1d.2[A] -> GSI 22 (level, low) -> IRQ 19
[   15.688000] ACPI: PCI Interrupt 0000:1c:03.2[A] -> GSI 16 (level, low) -> IRQ 16
[   15.748000] ACPI: PCI Interrupt 0000:14:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[   15.816000] parport_pc 00:0b: reported by Plug and Play ACPI
[   15.992000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 22
[   17.196000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 21 (level, low) -> IRQ 22
[   22.044000] ACPI: Power Button (FF) [PWRF]
[   22.084000] ACPI: Lid Switch [LID]
[   22.084000] ACPI: Power Button (CM) [PWRB]
[   22.096000] ACPI: Sleep Button (CM) [SLPB]
[   22.148000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.176000] ACPI: Battery Slot [CMB1] (battery present)
[   22.176000] ACPI: Battery Slot [CMB2] (battery absent)
[   22.196000] ACPI: ACPI Dock Station Driver 
[   22.204000] ACPI: \_SB_.PCI0.PATA.PRIM.MAST: found ejectable bay
[   22.204000] ACPI: \_SB_.PCI0.PATA.PRIM.MAST: Adding notify handler
[   22.204000] ACPI: Error installing bay notify handler
[   22.204000] ACPI: Bay [\_SB_.PCI0.PATA.PRIM.MAST] Added
[   22.324000] ACPI: AC Adapter [AC] (on-line)
[   32.388000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16

```

The lines containing errors let me suspect a faulty BIOS
```

[   28.173714] ACPI Error (tbinstal-0134): Table has invalid signature [    ], must be SSDT, PSDT or OEMx [20070126]
[   28.173723] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_._INI] (Node df839cf0), AE_BAD_SIGNATURE
```

I'm already running the latest BIOS, so there is nothing I can do about it.

Is there a way to get frequency scaling working? The current workarounds (disable frequency scaling or running on 800 MHz) are not practicable.

Any help would be appreciated.

---

### Post by rcampbell on 2007-11-30
Hi, I don't have any solutions, but I though I would say that on my Fujitsu T4220 tablet, I also get those exact ACPI errors on my dmesg output, and my CPU is also stuck at 800MHz, regardless of the load.
I'm leaning towards a BIOS/ACPI issue as well.

---

### Post by ranpha on 2007-12-26
I heard a lot of story that it's a BIOS error yes. Not only on fujitsu t4220 but on other centrino laptops also

However if have some cpu_scaling working. On battery it's 800mhz but on a connected power supply it jumps to 2ghz.

I just install cpufrequtils and cpufreqd

see my wiki entry
[https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)

---

### Post by Tommaso on 2008-03-04
Hi,
I'm having exactly the same issues on Acer Travelmate 4000 with a Centrino CPU using Ubuntu Hardy...All work well since I was using Faisty and Gutsy release, so I think is a a bug of hardy....I hope they will fix it!!
Bye...

---

