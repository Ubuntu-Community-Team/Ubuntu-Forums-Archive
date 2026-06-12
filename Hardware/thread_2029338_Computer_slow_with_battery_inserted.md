---
title: "Computer slow with battery inserted"
date: 2012-07-19
forum: Hardware
---

### Post by neclepsio on 2012-07-19
Hi everyone.

After a lot of troubleshooting, I found out what slows down my HP laptop.

When the battery is inserted and not fully charged, the computer slowly slows down when turned on, so that it's completely unusable after 5 minutes. 
If rebooted, the same happens, until the battery is fully charged.
If I check the CPU usage, it's almost all to the foreground process, no matter what it is.

The battery itself is damaged, according to a POST message at each boot; it lasts about half an hour with a full charge and I don't want to buy a new one - I'd rather change the notebook. The BIOS is updated.

Without battery, there is no slowdown.

When booting from a live USB (which previously worked well), I have the same problem.

It looks to me like some kind of "charging" message queue keeps growing...

Can anybody please help me?



Thank you,
Ignazio

---

### Post by matt_symes on 2012-07-19
Hi

Try booting with the kernel flag

```
acpi=off
```That will have other side effects but may highlight acpi battery readings as the problem or not.

Do you still have the same problem when using that flag ?

Kind regards

---

### Post by neclepsio on 2012-07-22
Thank you Matt.

It seems there are no problems using acpi=off.
The battery seems always fully charged. When disconnected from AC, the battery is reported as "not present".

Thank you.

---

### Post by neclepsio on 2012-07-23
What now? How can I debug the problem?

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) does not seem too helpful for my case.

Which flag could I try?


Thank you,
Ignazio

---

### Post by matt_symes on 2012-07-24
Hi

> It seems there are no problems using acpi=off.Just to confirm, you are not seeing the battery problems when you disable acpi using the kernel command line options ?

If so it sounds like there is a problem with ACPI and your battery. Maybe suprious interrupts are being generated. Let's take a look at the logs.

Remove the ACPI option from the grub command line and boot the computer as you used to.

Please post the output of 

```
grep ACPI /var/log/syslog
```Case in important in the above command, as in all command from the terminal, so ACPI does need to be in uppercase.

Please post the output back between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```Kind regards

---

### Post by neclepsio on 2012-07-24
Thank you.

This is the log. The computer is charged and full speed; I'm running on battery to reproduce the problem soon.
Anyway, I remember examining dmesg while the computer was slow, but found no relevant message.
In the meanwhile, there is something interesting?
Moreover, acpi=ht seems to work fine.

Thank you,
Ignazio

```

Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000]  BIOS-e820: 0000000077970000 - 0000000077980000 (ACPI NVS)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000]  BIOS-e820: 000000007a0f4000 - 000000007a2f4000 (ACPI NVS)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000]  BIOS-e820: 000000007bacf000 - 000000007bbcf000 (ACPI NVS)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000]  BIOS-e820: 000000007bbcf000 - 000000007bbff000 (ACPI data)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: RSDP 00000000000f6970 00024 (v02 HPQOEM)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: XSDT 000000007bbfe120 0006C (v01 HPQOEM SLIC-MPC 0000000F      01000013)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: FACP 000000007bbfc000 000F4 (v03 HPQOEM 1526     0000000F HP   00000001)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: DSDT 000000007bbdb000 1B628 (v01 HPQOEM 1526     00000001 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: FACS 000000007bbad000 00040
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: HPET 000000007bbfb000 00038 (v01 HPQOEM 1526     00000001 HP   00000001)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: APIC 000000007bbfa000 00084 (v01 HPQOEM 1526     00000001 HP   00000001)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: MCFG 000000007bbf9000 0003C (v01 HPQOEM 1526     00000001 HP   00000001)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: ASF! 000000007bbf8000 000A0 (v32 HPQOEM 1526     00000001 HP   00000001)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: SSDT 000000007bbd8000 002DD (v01 HPQOEM SataAhci 00001000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: SSDT 000000007bbd6000 0066C (v01  PmRef    CpuPm 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: SSDT 000000007bbd5000 00288 (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: SSDT 000000007bbd4000 00225 (v01  PmRef    ApTst 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.010729] ACPI: Core revision 20110623
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.153080] PM: Registering ACPI NVS region at 77970000 (65536 bytes)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.153080] PM: Registering ACPI NVS region at 7a0f4000 (2097152 bytes)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.153080] PM: Registering ACPI NVS region at 7bacf000 (1048576 bytes)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.153115] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.153118] ACPI: bus type pci registered
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.220281] ACPI: Added _OSI(Module Device)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.220284] ACPI: Added _OSI(Processor Device)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.220286] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.220288] ACPI: Added _OSI(Processor Aggregator Device)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.222497] ACPI: EC: Look up EC in DSDT
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.240136] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.513791] ACPI: SSDT 000000007bac6c98 00233 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.514314] ACPI: Dynamic OEM Table Load:
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.514317] ACPI: SSDT           (null) 00233 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.514434] ACPI: SSDT 000000007bac4618 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.514937] ACPI: Dynamic OEM Table Load:
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.514940] ACPI: SSDT           (null) 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.536256] ACPI: SSDT 000000007bac5e18 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.536788] ACPI: Dynamic OEM Table Load:
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.536791] ACPI: SSDT           (null) 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.548123] ACPI: SSDT 000000007bac6f18 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.548640] ACPI: Dynamic OEM Table Load:
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.548643] ACPI: SSDT           (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.804122] ACPI: Interpreter enabled
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.804127] ACPI: (supports S0 S3 S4 S5)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.804148] ACPI: Using IOAPIC for interrupt routing
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.805315] ACPI: Power Resource [APPR] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.833294] ACPI: Power Resource [PFN6] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.833351] ACPI: Power Resource [PFN7] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.833407] ACPI: Power Resource [PFN8] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.833459] ACPI: Power Resource [PFN9] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.833515] ACPI: Power Resource [PFNA] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.833570] ACPI: Power Resource [PFNB] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.833609] ACPI: Power Resource [PGF0] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.834164] ACPI: Power Resource [PFN0] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.834223] ACPI: Power Resource [PFN1] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.834276] ACPI: Power Resource [PFN2] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.834332] ACPI: Power Resource [PFN3] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.834387] ACPI: Power Resource [PFN4] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.834440] ACPI: Power Resource [PFN5] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.835214] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.835463] ACPI: No dock devices found.
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.835469] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.836187] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.852252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.852384] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.852420] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.852460] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.852519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.852551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.852616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.853067]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.854184]  pci0000:00: ACPI _OSC control (0x1d) granted
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861504] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861553] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861598] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861646] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861691] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861736] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861781] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861826] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.861949] PCI: Using ACPI for IRQ routing
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.883659] pnp: PnP ACPI init
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.883678] ACPI: bus type pnp registered
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.884209] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.884385] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.884784] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.884843] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.884961] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.885131] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.885215] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.885358] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.885432] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.885622] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.885691] pnp 00:0a: Plug and Play ACPI device, IDs SYN0176 SYN0100 SYN0002 PNP0f13 (active)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.885817] pnp: PnP ACPI: found 11 devices
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.885819] ACPI: ACPI bus type pnp unregistered
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.942755] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.942856] ACPI: AC Adapter [AC] (on-line)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.942955] ACPI: Sleep Button [SLPB]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943044] ACPI: Lid Switch [LID]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943102] ACPI: Power Button [PWRF]
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943201] ACPI: Fan [FAN6] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943251] ACPI: Fan [FAN7] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943304] ACPI: Fan [FAN8] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943355] ACPI: Fan [FAN9] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943407] ACPI: Fan [FANA] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943455] ACPI: Fan [FANB] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943490] ACPI: Fan [FANG] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943542] ACPI: Fan [FAN0] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943593] ACPI: Fan [FAN1] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943642] ACPI: Fan [FAN2] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943694] ACPI: Fan [FAN3] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943748] ACPI: Fan [FAN4] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.943799] ACPI: Fan [FAN5] (off)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    0.945528] ACPI: acpi_idle registered with cpuidle
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.438016] ACPI: Thermal Zone [GFXZ] (16 C)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.446360] ACPI: Thermal Zone [DTSZ] (50 C)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.458715] ACPI: Thermal Zone [CPUZ] (52 C)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.461403] ACPI: Thermal Zone [SKNZ] (46 C)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.469828] ACPI: Thermal Zone [BATZ] (30 C)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.473518] ACPI: Thermal Zone [FDTZ] (34 C)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.473561] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.473571] ACPI: Battery Slot [BAT0] (battery present)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.518127] ACPI: Battery Slot [BAT0] (battery present)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.913426] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    1.915412] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    2.254165] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 24 18:20:33 neclepsio-HP-620 kernel: [    2.273811] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 24 18:20:33 neclepsio-HP-620 kernel: [   15.899243] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jul 24 18:20:33 neclepsio-HP-620 kernel: [   16.048683] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jul 24 18:20:33 neclepsio-HP-620 kernel: [   16.048694] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0

```

---

### Post by neclepsio on 2012-07-24
I couldn't reproduce today. Can it be that the slowdown happens when the computer is cold, and everything is ok when it's hot?

---

### Post by neclepsio on 2012-07-25
This is the full log while unusably slow:

```

Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000]  BIOS-e820: 0000000077970000 - 0000000077980000 (ACPI NVS)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000]  BIOS-e820: 000000007a0f4000 - 000000007a2f4000 (ACPI NVS)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000]  BIOS-e820: 000000007bacf000 - 000000007bbcf000 (ACPI NVS)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000]  BIOS-e820: 000000007bbcf000 - 000000007bbff000 (ACPI data)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: RSDP 00000000000f6970 00024 (v02 HPQOEM)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: XSDT 000000007bbfe120 0006C (v01 HPQOEM SLIC-MPC 0000000F      01000013)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: FACP 000000007bbfc000 000F4 (v03 HPQOEM 1526     0000000F HP   00000001)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: DSDT 000000007bbdb000 1B628 (v01 HPQOEM 1526     00000001 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: FACS 000000007bbad000 00040
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: HPET 000000007bbfb000 00038 (v01 HPQOEM 1526     00000001 HP   00000001)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: APIC 000000007bbfa000 00084 (v01 HPQOEM 1526     00000001 HP   00000001)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: MCFG 000000007bbf9000 0003C (v01 HPQOEM 1526     00000001 HP   00000001)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: ASF! 000000007bbf8000 000A0 (v32 HPQOEM 1526     00000001 HP   00000001)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: SSDT 000000007bbd8000 002DD (v01 HPQOEM SataAhci 00001000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: SSDT 000000007bbd6000 0066C (v01  PmRef    CpuPm 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: SSDT 000000007bbd5000 00288 (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: SSDT 000000007bbd4000 00225 (v01  PmRef    ApTst 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.010306] ACPI: Core revision 20110623
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.153082] PM: Registering ACPI NVS region at 77970000 (65536 bytes)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.153082] PM: Registering ACPI NVS region at 7a0f4000 (2097152 bytes)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.153082] PM: Registering ACPI NVS region at 7bacf000 (1048576 bytes)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.153116] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.153119] ACPI: bus type pci registered
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.220284] ACPI: Added _OSI(Module Device)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.220286] ACPI: Added _OSI(Processor Device)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.220288] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.220290] ACPI: Added _OSI(Processor Aggregator Device)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.222505] ACPI: EC: Look up EC in DSDT
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.240134] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.513772] ACPI: SSDT 000000007bac6c98 00233 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.514296] ACPI: Dynamic OEM Table Load:
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.514299] ACPI: SSDT           (null) 00233 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.514416] ACPI: SSDT 000000007bac4618 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.514919] ACPI: Dynamic OEM Table Load:
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.514922] ACPI: SSDT           (null) 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.536255] ACPI: SSDT 000000007bac5e18 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.536787] ACPI: Dynamic OEM Table Load:
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.536790] ACPI: SSDT           (null) 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.548123] ACPI: SSDT 000000007bac6f18 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.548641] ACPI: Dynamic OEM Table Load:
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.548644] ACPI: SSDT           (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.800122] ACPI: Interpreter enabled
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.800127] ACPI: (supports S0 S3 S4 S5)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.800148] ACPI: Using IOAPIC for interrupt routing
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.801314] ACPI: Power Resource [APPR] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.829296] ACPI: Power Resource [PFN6] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.829354] ACPI: Power Resource [PFN7] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.829410] ACPI: Power Resource [PFN8] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.829462] ACPI: Power Resource [PFN9] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.829518] ACPI: Power Resource [PFNA] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.829573] ACPI: Power Resource [PFNB] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.829613] ACPI: Power Resource [PGF0] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.830169] ACPI: Power Resource [PFN0] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.830228] ACPI: Power Resource [PFN1] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.830280] ACPI: Power Resource [PFN2] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.830336] ACPI: Power Resource [PFN3] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.830391] ACPI: Power Resource [PFN4] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.830445] ACPI: Power Resource [PFN5] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.831219] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.831466] ACPI: No dock devices found.
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.831472] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.832187] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.848254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.848386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.848421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.848460] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.848519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.848552] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.848616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.849070]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.850186]  pci0000:00: ACPI _OSC control (0x1d) granted
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857466] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857514] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857560] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857607] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857652] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857699] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857744] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857788] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.857910] PCI: Using ACPI for IRQ routing
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.879653] pnp: PnP ACPI init
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.879673] ACPI: bus type pnp registered
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.880202] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.880379] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.880777] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.880836] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.880953] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.881123] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.881206] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.881349] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.881424] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.881615] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.881684] pnp 00:0a: Plug and Play ACPI device, IDs SYN0176 SYN0100 SYN0002 PNP0f13 (active)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.881809] pnp: PnP ACPI: found 11 devices
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.881811] ACPI: ACPI bus type pnp unregistered
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.938782] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.938886] ACPI: AC Adapter [AC] (on-line)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.938978] ACPI: Sleep Button [SLPB]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939068] ACPI: Lid Switch [LID]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939121] ACPI: Power Button [PWRF]
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939217] ACPI: Fan [FAN6] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939268] ACPI: Fan [FAN7] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939320] ACPI: Fan [FAN8] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939373] ACPI: Fan [FAN9] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939424] ACPI: Fan [FANA] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939474] ACPI: Fan [FANB] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939504] ACPI: Fan [FANG] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939559] ACPI: Fan [FAN0] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939610] ACPI: Fan [FAN1] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939661] ACPI: Fan [FAN2] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939710] ACPI: Fan [FAN3] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939762] ACPI: Fan [FAN4] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.939814] ACPI: Fan [FAN5] (off)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    0.941511] ACPI: acpi_idle registered with cpuidle
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.433874] ACPI: Thermal Zone [GFXZ] (16 C)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.442489] ACPI: Thermal Zone [DTSZ] (34 C)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.446021] ACPI: Thermal Zone [CPUZ] (35 C)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.448694] ACPI: Thermal Zone [SKNZ] (28 C)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.456333] ACPI: Thermal Zone [BATZ] (55 C)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.460080] ACPI: Thermal Zone [FDTZ] (34 C)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.460129] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.460143] ACPI: Battery Slot [BAT0] (battery present)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.513377] ACPI: Battery Slot [BAT0] (battery present)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.880964] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    1.882082] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    2.219801] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 25 17:53:14 neclepsio-HP-620 kernel: [    2.238748] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 25 17:53:14 neclepsio-HP-620 kernel: [   16.581173] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jul 25 17:53:14 neclepsio-HP-620 kernel: [   16.635276] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jul 25 17:53:14 neclepsio-HP-620 kernel: [   16.635287] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0

```

---

### Post by matt_symes on 2012-07-27
Hi

I cannot really see much wrong with the logs.

Maybe the best idea (apart from getting a new battery) is to continue using one of the acpi kernel boot flags.

Kind regards

---

### Post by neclepsio on 2012-07-28
Thank you.

I'm not sure the new battery would solve. The issue is not related to the presence of the battery (as I previously though, but maybe to the temperature: the computer seems to work well only when hot(!).
acpi=off seems to solve, I'm not sure about acpi=ht. Having just one/two shots per day testing is difficult.
Anyway, with acpi=off I have some problems that maybe you can help me fix:
- multimedia keys do not work;
- the fan is always on.

Thank you very much for your help.

---

### Post by matt_symes on 2012-07-29
Hi

> Anyway, with acpi=off I have some problems that maybe you can help me fix:
- multimedia keys do not work;
- the fan is always on.The problem does look to be an ACPI issue. 

The effects you have noted above are one of the side effects of turning off ACPI.

You want to use the minimum impact ACPI flags that will ensure your system still works while fixing the battery issue. acpi=off is very high impact.

There is something else we can check for though (assuming, still, that it is the battery causing the problem).

Let's unbind the acpi battery module and see if you still get the slowdowns.

The first thing you will need to do is locate the module and device.

Open a terminal and type

```
ls /sys/bus/acpi/drivers/battery
```This will show the pnp device name. Here's mine.

```
matthew-Aspire-7540% ls /sys/bus/acpi/drivers/battery                                  
bind  **PNP0C0A:00**  uevent  unbind
matthew-Aspire-7540%
```The device name is highlighted in bold. You then need to unbind the driver from the device.

On my machine i need to type this.
```

matthew-Aspire-7540% echo -n "**PNP0C0A:00**" | sudo tee /sys/bus/acpi/drivers/battery/unbind
matthew-Aspire-7540% 
```Basically what i am doing to echoing the name of the device into the unbind file.

You will need to do the same but replace the name of the device with whatever your is called (discovered from the first ls command).

Do this as soon as you turn the computer on and can get to a terminal.

This will not persist after reboots so, if it works, we will need to create a script for you.

Post back on efficacy.

EDIT: I find it hard to see how being cold could make the laptop slow down, however.....

If it is due to the laptop temperatures then we could also unbind the thermal drivers as see if that helps.

They are be unbound from

```
/sys/bus/acpi/drivers/thermal
```

You will want to unbind all of them as you may have more than one thermal zone. Make sure the laptop does not over heat though.

Kind regards

---

### Post by neclepsio on 2012-07-30
Thank you.

I added
```
echo -n "PNP0C0A:00" | tee /sys/bus/acpi/drivers/battery/unbind
```
(I have the same device name) to /etc/rc.local and I will see what it happens in the next few days.

If the problem continues, I will try with thermal devices.


Thank you.
Ignazio

---

### Post by neclepsio on 2012-07-31
Unbinding battery driver does not help.
I'm trying thermal zone now , but I'm a little bit scared.
Is there any other driver I should try? Maybe AC?

Am I safe, since this is the output of sensors?

```

neclepsio@neclepsio-HP-620:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +42.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +43.0°C  (high = +105.0°C, crit = +105.0°C)

```

---

### Post by matt_symes on 2012-08-01
Hi

> Am I safe, since this is the output of sensors? 

Those temps are fine.

Remember, this is a test only. While the test is being performed you need to ensure the laptop stays cool.

You can run a fan by the laptop to help ensure good air flow and keep it in a cool room.

Kind regards

---

### Post by neclepsio on 2012-08-01
It's difficult to have a cool room in southern Italy in August! :)

With thermal devices unbound (and battery bound) I have no problem so far, but I need a couple days of testing before being sure. I cannot figure out an explanation. 

Anyway, the CPU is running now at 55 °C (should be fine until 70 °C, right?) - and the fan is at full speed.
At lower temperatures, the fan slows down. This means I lose no major functionality? Or maybe some part of the computer other than the processor could be damaged?

Thank you.

---

### Post by matt_symes on 2012-08-01
Hi

> **neclepsio said:**
> It's difficult to have a cool room in southern Italy in August! :)

With thermal devices unbound (and battery bound) I have no problem so far, but I need a couple days of testing before being sure. I cannot figure out an explanation. 

Anyway, the CPU is running now at 55 °C (should be fine until 70 °C, right?) - and the fan is at full speed.
At lower temperatures, the fan slows down. This means I lose no major functionality? Or maybe some part of the computer other than the processor could be damaged?

Thank you.

I just wanted to check. You are running the computer WITHOUT the acpi=off switch ? These tests need to be run without them :)

55 °C is fine. Even 70 °C is workable but don't let it get too much hotter than that. Most laptops will shutdown from the BIOS when a certain critical temperature is reached regardless of whether the OS temperature modules are loaded or not.

There will be no major loss of functionality if the temperature sensors modules are causing the problem.

More testing is required first, though, so please post back in a couple of days.

Kind regards

---

### Post by neclepsio on 2012-08-02
I checked:

```

neclepsio@neclepsio-HP-620:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=68854e53-eecd-4fcf-b3c1-720cfc4411e8 ro quiet splash vt.handoff=7

```

Moreover, the /sys/bus/acpi structure is present.

It seems strange to me too. Do you have a possible explanation?
I still had no slowdown since unbinding thermal devices, I will post again in a couple of days.

Thank you very much for your help.
Ignazio

---

### Post by matt_symes on 2012-08-02
Hi

> Moreover, the /sys/bus/acpi structure is present.

That is good. It means ACPI is running and  you are not using the ACPI=off boot option.

Post back on how the laptop is behaving in a while. 

If it is the thermal drivers that are causing the problem,  we can start thinking about a solution or do some more digging to try to find out why the thermal drivers are misbehaving.

Kind regards

---

### Post by neclepsio on 2012-08-03
Hi.

With thermal drivers unbound, even today everything is fine.
I tried to rebind them after 30 minutes. The readings are:

```

root@neclepsio-HP-620:/etc# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +16.0°C  (crit = +108.0°C)
temp2:        +35.0°C  (crit = +105.0°C)
temp3:        +49.0°C  (crit = +108.0°C)
temp4:        +49.0°C  (crit = +105.0°C)
temp5:        +32.2°C  (crit = +108.0°C)
temp6:        +45.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +45.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +47.0°C  (high = +105.0°C, crit = +105.0°C)

```

The computer shows no slowdown after 30 minutes from rebinding.

So, I wrote two scripts to bind and unbind thermal drivers, and added to rc.local:
```

/etc/unbindthermal 
at -f /etc/bindthermal  now + 30 minute

```

So, about:
> 
If it is the thermal drivers that are causing the problem, we can start thinking about a solution or do some more digging to try to find out why the thermal drivers are misbehaving.


Do you think this is a kind of solution? I think I'm fine with that, and I thank you so much for your help so far.
If you are willing to, I would be even more happy to do some digging, and find out what drove me crazy for so much time, and maybe a real fix.


Thank you,
Ignazio

---

### Post by neclepsio on 2012-08-05
> 
temp1:        +16.0°C  (crit = +108.0°C)


Just an information: room temperature is 27-33 °C (with air conditioner on).
Moreover, temp1 seems to always be 16 °C.
This is a very unlikely reading.

EDIT: just unbinding this thermal device, the computer seems to work. May it be a hardware failure?

Ignazio

---

### Post by neclepsio on 2012-08-12
> **neclepsio said:**
> just unbinding this thermal device, the computer seems to work.
Ignazio

UPDATE: this is not true, today I went back to unbinding all thermal devices for the first 30 minutes.

---

### Post by neclepsio on 2012-11-06
Ubuntu 12.10 solves the problem.

---

