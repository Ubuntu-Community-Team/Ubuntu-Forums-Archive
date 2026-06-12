---
title: "Power button and suspend issues on a Dell Latitude 11 tablet 5179"
date: 2018-02-17
forum: Hardware
---

### Post by Mocker on 2018-02-17
Hey folks,

I'm so close in my quest to get a Linux-powered hybrid tablet working. and yet so far.

I just got a refurbished Dell 5179 tablet. It's a Core m5-6Y57, so more standard hardware than the Atom-based tablets. That's specifically why I chose it. I installed Ubuntu 17.10 on it, and and everything works: touchscreen, rotation, wifi, sound... all the stuff I have had trouble with on other tablets I've tried to install Linux on. The only exception is the power button. I cannot get this thing to sleep via the power button, even though I change the Settings > Power > When the Power Button is Pressed option to Suspend.

If I get the unit to sleep (for examople, using systemctrl suspend or setting a timeout for it to suspend and waiting), it seems to suspend, but there's no way to get it to wake up. The power button, keypresses, and mouse don't wake it up. It seems to be hung, as the Caps Lock light doesn't come on when I press it. All I can do is hold down the power button for a while to force it to power off.

I've fully updated Ubuntu. The kernel is at 4.13.0-32-generic. When I do a grep for ACPI messages in dmesg, I get several errors:

```
$ dmesg | grep -i acpi
[    0.000000] BIOS-e820: [mem 0x000000007fba2000-0x000000007fba2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000872a5000-0x00000000872f0fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000872f1000-0x0000000087942fff] ACPI NVS
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000EC480 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 0x00000000872BD0B0 0000DC (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000872E05A0 00010C (v05 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000872BD218 023383 (v02 DELL   CBX3     01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000087940E80 000040
[    0.000000] ACPI: APIC 0x00000000872E06B0 000084 (v03 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000872E0738 000044 (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000872E0780 00003C (v01 DELL   CBX3     01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000872E07C0 000038 (v01 DELL   CBX3     01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x00000000872E07F8 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: WSMT 0x00000000872E0B10 000028 (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: LPIT 0x00000000872E0B38 000094 (v01 INTEL  SKL-ULT  00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x00000000872E0BD0 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000872E0E18 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x00000000872E39C8 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x00000000872E3A00 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x00000000872E3A58 000728 (v02 INTEL  xh_rvp03 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000872E4180 0035AA (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x00000000872E7730 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x00000000872E7778 000E73 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000872E85F0 006ADC (v02 DptfTa DptfTabl 00001000 INTL 20120913)
[    0.000000] ACPI: MSDM 0x00000000872EF0D0 000055 (v03 DELL   CBX3     06222004 AMI  00010013)
[    0.000000] ACPI: SLIC 0x00000000872EF128 000176 (v03 DELL   CBX3     01072009 MSFT 00010013)
[    0.000000] ACPI: DMAR 0x00000000872EF2A0 000114 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: TPM2 0x00000000872EF3B8 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: ASF! 0x00000000872EF3F0 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: WPBT 0x00000000872EF498 000038 (v01 ABT-NT ABT-WPBT 00000001 ABTW 20120402)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.004000] ACPI: Core revision 20170531
[    0.090527] ACPI: 8 ACPI AML tables successfully acquired and loaded
[    0.153811] PM: Registering ACPI NVS region [mem 0x7fba2000-0x7fba2fff] (4096 bytes)
[    0.153811] PM: Registering ACPI NVS region [mem 0x872f1000-0x87942fff] (6627328 bytes)
[    0.156146] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.156148] ACPI: bus type PCI registered
[    0.156151] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.160138] ACPI: Added _OSI(Module Device)
[    0.160140] ACPI: Added _OSI(Processor Device)
[    0.160142] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.160144] ACPI: Added _OSI(Processor Aggregator Device)
[    0.162073] ACPI: Executed 24 blocks of module-level executable AML code
[    0.196105] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.214663] ACPI: Dynamic OEM Table Load:
[    0.214680] ACPI: SSDT 0xFFFF927128038000 000492 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.215469] ACPI: \_PR_.CPU0: _OSC native thermal LVT Acked
[    0.219717] ACPI: Dynamic OEM Table Load:
[    0.219732] ACPI: SSDT 0xFFFF9271280B8400 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.220638] ACPI: Dynamic OEM Table Load:
[    0.220648] ACPI: SSDT 0xFFFF927128054600 00008E (v02 PmRef  Cpu0Hwp  00003000 INTL 20120913)
[    0.221293] ACPI: Dynamic OEM Table Load:
[    0.221303] ACPI: SSDT 0xFFFF9271280E4800 000130 (v02 PmRef  HwpLvt   00003000 INTL 20120913)
[    0.223221] ACPI: Dynamic OEM Table Load:
[    0.223236] ACPI: SSDT 0xFFFF92712803F000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.224805] ACPI: Dynamic OEM Table Load:
[    0.224817] ACPI: SSDT 0xFFFF9271280E5200 000119 (v02 PmRef  ApHwp    00003000 INTL 20120913)
[    0.225719] ACPI: Dynamic OEM Table Load:
[    0.225730] ACPI: SSDT 0xFFFF9271280E5800 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.231730] ACPI: EC: EC started
[    0.231731] ACPI: EC: interrupt blocked
[    0.237879] ACPI: \_SB_.PCI0.LPCB.ECDV: Used as first EC
[    0.237884] ACPI: \_SB_.PCI0.LPCB.ECDV: GPE=0x14, EC_CMD/EC_SC=0x934, EC_DATA=0x930
[    0.237888] ACPI: \_SB_.PCI0.LPCB.ECDV: Used as boot DSDT EC to handle transactions
[    0.237889] ACPI: Interpreter enabled
[    0.237997] ACPI: (supports S0 S3 S4 S5)
[    0.237999] ACPI: Using IOAPIC for interrupt routing
[    0.238099] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.240822] ACPI: Enabled 8 GPEs in block 00 to 7F
[    0.247650] ACPI: Power Resource [PG00] (on)
[    0.248596] ACPI: Power Resource [PG01] (on)
[    0.249492] ACPI: Power Resource [PG02] (on)
[    0.255709] ACPI: Power Resource [WRST] (off)
[    0.256766] ACPI: Power Resource [WRST] (off)
[    0.257673] ACPI: Power Resource [WRST] (off)
[    0.258582] ACPI: Power Resource [WRST] (off)
[    0.259510] ACPI: Power Resource [WRST] (off)
[    0.260450] ACPI: Power Resource [WRST] (off)
[    0.261363] ACPI: Power Resource [WRST] (off)
[    0.262269] ACPI: Power Resource [WRST] (off)
[    0.263171] ACPI: Power Resource [WRST] (off)
[    0.264079] ACPI: Power Resource [WRST] (off)
[    0.264987] ACPI: Power Resource [WRST] (off)
[    0.265893] ACPI: Power Resource [WRST] (off)
[    0.266795] ACPI: Power Resource [WRST] (off)
[    0.267698] ACPI: Power Resource [WRST] (off)
[    0.268607] ACPI: Power Resource [WRST] (off)
[    0.269515] ACPI: Power Resource [WRST] (off)
[    0.270442] ACPI: Power Resource [WRST] (off)
[    0.271359] ACPI: Power Resource [WRST] (off)
[    0.272271] ACPI: Power Resource [WRST] (off)
[    0.273177] ACPI: Power Resource [WRST] (off)
[    0.330374] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.330389] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.334050] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.334053] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.390221] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.390368] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.390510] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.390652] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.390793] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.390934] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.391075] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.391216] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.396337] ACPI: EC: interrupt unblocked
[    0.396358] ACPI: EC: event unblocked
[    0.396397] ACPI: \_SB_.PCI0.LPCB.ECDV: GPE=0x14, EC_CMD/EC_SC=0x934, EC_DATA=0x930
[    0.396401] ACPI: \_SB_.PCI0.LPCB.ECDV: Used as boot DSDT EC to handle transactions and events
[    0.397927] ACPI: bus type USB registered
[    0.402645] PCI: Using ACPI for IRQ routing
[    0.455255] pnp: PnP ACPI init
[    0.455884] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.456175] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.456276] system 00:02: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.456757] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.457353] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.457491] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.458267] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.461274] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.467284] pnp: PnP ACPI: found 8 devices
[    0.478536] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    2.349109] DMAR: ACPI device "device:64" under DMAR at fed91000 as 00:15.0
[    2.349116] DMAR: ACPI device "device:65" under DMAR at fed91000 as 00:15.1
[    2.349122] DMAR: ACPI device "device:66" under DMAR at fed91000 as 00:15.2
[    2.365325] ACPI: AC Adapter [AC] (on-line)
[    2.367647] ACPI: Lid Switch [LID0]
[    2.367818] ACPI: Power Button [PBTN]
[    2.367913] ACPI: Sleep Button [SBTN]
[    2.368285] ACPI: Power Button [PWRF]
[    2.377250] ACPI: Thermal Zone [THM] (-268 C)
[    2.434819] ACPI: Battery Slot [BAT0] (battery present)
[    2.470653] ACPI: Battery Slot [BAT1] (battery present)
[    3.841950] acpi LNXCPU:02: hash matches
[    4.799724] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    6.105323] ACPI Warning: SystemMemory range 0x00000000FE028000-0x00000000FE0281FF conflicts with OpRegion 0x00000000FE028000-0x00000000FE028207 (\_SB.PCI0.GEXP.BAR0) (20170531/utaddress-247)
[    6.105332] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.175901] ACPI Warning: \_SB.IETM._ART: Return Package type mismatch at index 0 - found Integer, expected Reference (20170531/nspredef-297)
[    6.175919] ACPI: Invalid package element [0]: got number, expecting [R]
[    6.176577] ACPI Warning: \_SB.IETM._TRT: Return Package has no elements (empty) (20170531/nsprepkg-130)
[    6.193833] acpi INT33D5:00: intel-hid: created platform device
[    6.960166] ACPI: Invalid package element [0]: got number, expecting [R]
[    6.960192] ACPI: Invalid package element [0]: got number, expecting [R]
```

I have no idea what to do about those issues, or if they are actually problems at all. Googling on them doesn't turn up anything solid.

This issue is not specific to Ubuntu. I've also installed Fedora 27 and it has the same issue (it's also on 4.13 kernel).

I also tried booting Ubuntu 16.04 from USB just to see if this was a regression in a later kernel... but that didn't work either.

Any ideas of what I can do?

---

