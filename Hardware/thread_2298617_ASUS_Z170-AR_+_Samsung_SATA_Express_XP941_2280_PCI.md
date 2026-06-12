---
title: "ASUS Z170-AR + Samsung SATA Express XP941 2280 PCIe X4 Gen2 SSD"
date: 2015-10-12
forum: Hardware
---

### Post by Ernie_Ewert on 2015-10-12
[FONT=monospace][COLOR=#000000]I am currently booting with a couple year old Samsung 840 SATA SSD **/dev/sda**. This works great. For testing purposes I have an XP941 installed in the M.2 Socket and SATA Express is enabled. This device is on **/dev/s**[/COLOR]**db**.  

If I boot with the kernel options ```
acpi=off noapic
``` then I get outstanding read/write performance out of the XP941. (It really IS around three times faster than the 840/850 series SATA 3 devices depending on the operation.)  

However, this also disables **Hyper Threading** support. I tried ```
acpi=ht
``` and have the same issue.

[/FONT][FONT=monospace][COLOR=#000000]Ubuntu 15.04
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]3.19.0-30-generic[/COLOR][/FONT]
[FONT=monospace]
This section is filtered on [COLOR=#ff0000]ACPI:[/COLOR]
[/FONT]```
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic.efi.signed acpi=ht root=UUID=7f4115a3-3ef1-4538-aea4-82a28d784cd9 ro quiet splash vt.handoff=7
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000082ea2000-0x0000000082ea2fff] ACPI NVS
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008bc6f000-0x000000008bca7fff] ACPI data
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008bca8000-0x000000008c603fff] ACPI NVS
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] Malformed early option 'acpi'
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] efi:  ESRT=0x8d2ddd98  ACPI=0x8bc7a000  ACPI 2.0=0x8bc7a000  SMBIOS=0xf05e0  SMBIOS 3.0=0x8d2db000  MPS=0xfca20 
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Early table checksum verification disabled
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: RSDP 0x000000008BC7A000 000024 (v02 ALASKA)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: XSDT 0x000000008BC7A098 0000A4 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FACP 0x000000008BC9D388 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: DSDT 0x000000008BC7A1D0 0231B4 (v02 ALASKA A M I    01072009 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FACS 0x000000008C603F80 000040
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: APIC 0x000000008BC9D498 0000BC (v03 ALASKA A M I    01072009 AMI  00010013)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FPDT 0x000000008BC9D558 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FIDT 0x000000008BC9D5A0 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: MCFG 0x000000008BC9D640 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: HPET 0x000000008BC9D680 000038 (v01 ALASKA A M I    01072009 AMI. 0005000B)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9D6B8 00036D (v01 SataRe SataTabl 00001000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LPIT 0x000000008BC9DA28 000094 (v01 INTEL  SKL      00000000 MSFT 0000005F)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9DAC0 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9DD08 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA08B8 000C45 (v02 INTEL  Ther_Rvp 00001000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: DBG2 0x000000008BCA1500 000054 (v00 INTEL           00000000 MSFT 0000005F)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA1558 000704 (v02 INTEL  xh_rvp08 00000000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA1C60 005205 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: UEFI 0x000000008BCA6E68 000042 (v01                 00000000      00000000)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA6EB0 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic.efi.signed acpi=ht root=UUID=7f4115a3-3ef1-4538-aea4-82a28d784cd9 ro quiet splash vt.handoff=7
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.000022] ACPI: Core revision 20141107
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.016703] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20141107/dswload-210)
Oct 12 10:14:47 erniee-kubuntu-dev systemd[1]: Listening on ACPID Listen Socket.
Oct 12 10:14:47 erniee-kubuntu-dev systemd[1]: Starting ACPID Listen Socket.
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.016706] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20141107/psobject-224)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.021920] ACPI: All ACPI Tables successfully acquired
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.207349] PM: Registering ACPI NVS region [mem 0x82ea2000-0x82ea2fff] (4096 bytes)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.207349] PM: Registering ACPI NVS region [mem 0x8bca8000-0x8c603fff] (9814016 bytes)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.212852] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.212853] ACPI: bus type PCI registered
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.212854] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.217030] ACPI: Added _OSI(Module Device)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.217031] ACPI: Added _OSI(Processor Device)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.217032] ACPI: Added _OSI(3.0 _SCP Extensions)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.217032] ACPI: Added _OSI(Processor Aggregator Device)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.221626] ACPI: Executed 21 blocks of module-level executable AML code
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.225125] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.227096] ACPI: Dynamic OEM Table Load:
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.227100] ACPI: SSDT 0xFFFF88084A443000 000768 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.227123] ACPI Error: Unknown opcode 0x19 at table offset 0x04D8, ignoring (20141107/psobject-105)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.228409] ACPI: Dynamic OEM Table Load:
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.228412] ACPI: SSDT 0xFFFF88084A443800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.232071] ACPI: Interpreter enabled
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.232077] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.232082] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.232094] ACPI: (supports S0 S3 S4 S5)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.232095] ACPI: Using IOAPIC for interrupt routing
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.232114] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.233265] ACPI: Power Resource [PG00] (on)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.253056] ACPI: Power Resource [PG01] (on)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.273081] ACPI: Power Resource [PG02] (on)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.294211] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.294417] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.294621] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.294825] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.295027] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.295229] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.295432] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.295642] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.295843] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.296047] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.296255] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.296460] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.296662] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.296865] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.297070] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.297274] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.297476] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.297679] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.297882] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.298084] ACPI: Power Resource [WRST] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.301863] ACPI: Power Resource [FN00] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.301900] ACPI: Power Resource [FN01] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.301938] ACPI: Power Resource [FN02] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.301973] ACPI: Power Resource [FN03] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.302010] ACPI: Power Resource [FN04] (off)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.302691] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.302695] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.302714] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.303461] pci 0000:00:01.0: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.303741] pci 0000:00:14.0: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.304168] pci 0000:00:1b.0: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.304292] pci 0000:00:1c.0: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.304395] pci 0000:00:1c.2: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.304513] pci 0000:00:1d.0: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.304924] pci 0000:00:1f.3: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.305361] pci 0000:00:1f.6: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.305460] acpiphp: Slot [1] registered
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.305680] pci 0000:03:00.0: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.313217] pci 0000:04:00.0: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.321342] pci 0000:06:00.0: System wakeup disabled by ACPI
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330088] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330118] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330148] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 *15)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330178] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330207] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330236] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330265] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330294] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330508] ACPI: Enabled 6 GPEs in block 00 to 7F
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330695] ACPI: bus type USB registered
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.330799] PCI: Using ACPI for IRQ routing
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364041] pnp: PnP ACPI init
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364143] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364381] pnp 00:01: Plug and Play ACPI device, IDs PNP0501 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364475] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364519] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364533] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364551] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364668] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.364693] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.365257] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.365672] pnp: PnP ACPI: found 9 devices
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.647524] ACPI: Sleep Button [SLPB]
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.647542] ACPI: Power Button [PWRB]
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.647559] ACPI: Power Button [PWRF]
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.648173] ACPI: Thermal Zone [TZ00] (28 C)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.648232] ACPI: Thermal Zone [TZ01] (30 C)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.673902] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.673905] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS01._PLD] (Node ffff88084e1132f8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.674278] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.674279] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS02._PLD] (Node ffff88084e113348), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.674650] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.674651] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS03._PLD] (Node ffff88084e113398), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.675020] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.675021] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS04._PLD] (Node ffff88084e1133e8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.675391] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.675393] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS05._PLD] (Node ffff88084e113438), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.675762] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.675763] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS06._PLD] (Node ffff88084e113488), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.676132] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.676133] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS07._PLD] (Node ffff88084e1134d8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.676502] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.676504] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS08._PLD] (Node ffff88084e113528), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.676874] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.676875] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS09._PLD] (Node ffff88084e113578), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.677247] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.677248] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS10._PLD] (Node ffff88084e1135c8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.750498] ACPI PCC probe failed.
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.755906] acpi-fan PNP0C0B:03: hash matches
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    0.755908] acpi PNP0C0B:03: hash matches
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    2.734722] asus_wmi: Disabling ACPI video driver
Oct 12 10:14:47 erniee-kubuntu-dev kernel: [    2.788679] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Oct 12 10:14:47 erniee-kubuntu-dev sensors[766]: acpitz-virtual-0
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: sensor_update: type acpitz
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: sensor_update: type acpitz
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: failed to open /dev/acpi_thermal_rel
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: failed to open /dev/acpi_thermal_rel
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: sensor index:1 acpitz /sys/class/thermal/thermal_zone1/ Async:0
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: zone acpitz bounded
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: message repeated 4 times: [ zone acpitz bounded]
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: /sys/class/hwmon/hwmon0/name->acpitz
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: Zone 0: acpitz, Active:0 Bind:1 Sensor_cnt:1
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: Zone 1: acpitz, Active:0 Bind:0 Sensor_cnt:1
Oct 12 10:14:48 erniee-kubuntu-dev thermald[690]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Oct 12 10:14:48 erniee-kubuntu-dev systemd[1]: Started ACPI event daemon.
Oct 12 10:14:48 erniee-kubuntu-dev systemd[1]: Starting ACPI event daemon...
Oct 12 10:14:48 erniee-kubuntu-dev acpid: starting up with netlink and the input layer
Oct 12 10:14:48 erniee-kubuntu-dev acpid: 9 rules loaded
Oct 12 10:14:48 erniee-kubuntu-dev acpid: waiting for events: event logging is off
Oct 12 10:14:48 erniee-kubuntu-dev acpid: client connected from 844[0:0]
Oct 12 10:14:48 erniee-kubuntu-dev acpid: 1 client rule loaded
Oct 12 10:17:17 erniee-kubuntu-dev kernel: [  152.840623] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:17:42 erniee-kubuntu-dev kernel: [  178.406010] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:17:54 erniee-kubuntu-dev kernel: [  189.947625] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:19:17 erniee-kubuntu-dev kernel: [  273.802328] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:19:19 erniee-kubuntu-dev kernel: [  275.860514] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:19:21 erniee-kubuntu-dev kernel: [  277.565915] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:22:03 erniee-kubuntu-dev kernel: [  440.245976] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:22:56 erniee-kubuntu-dev kernel: [  492.591129] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:25:36 erniee-kubuntu-dev kernel: [  653.211717] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:26:30 erniee-kubuntu-dev kernel: [  707.007076] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:26:30 erniee-kubuntu-dev kernel: [  707.734562] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:26:57 erniee-kubuntu-dev kernel: [  733.910712] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:26:59 erniee-kubuntu-dev kernel: [  735.930772] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:28:36 erniee-kubuntu-dev kernel: [  834.100688] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:28:37 erniee-kubuntu-dev kernel: [  834.297082] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:28:37 erniee-kubuntu-dev kernel: [  834.663817] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:38:38 erniee-kubuntu-dev kernel: [ 1436.925977] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:38:38 erniee-kubuntu-dev kernel: [ 1437.068273] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:49:04 erniee-kubuntu-dev kernel: [ 2063.993639] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 10:50:34 erniee-kubuntu-dev kernel: [ 2153.978739] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:02:08 erniee-kubuntu-dev kernel: [ 2849.669854] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:11:11 erniee-kubuntu-dev kernel: [ 3393.763810] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:11:14 erniee-kubuntu-dev kernel: [ 3397.028340] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:11:14 erniee-kubuntu-dev kernel: [ 3397.200841] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:16:45 erniee-kubuntu-dev kernel: [ 3728.414297] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:22:13 erniee-kubuntu-dev kernel: [ 4057.689019] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:24:02 erniee-kubuntu-dev kernel: [ 4166.768805] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:24:19 erniee-kubuntu-dev kernel: [ 4183.379947] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:24:29 erniee-kubuntu-dev kernel: [ 4193.838838] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:26:08 erniee-kubuntu-dev kernel: [ 4292.868475] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:26:21 erniee-kubuntu-dev kernel: [ 4305.730207] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:26:57 erniee-kubuntu-dev kernel: [ 4341.836236] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:28:24 erniee-kubuntu-dev systemd[1]: Stopping ACPI event daemon...
Oct 12 11:28:24 erniee-kubuntu-dev kernel: [ 4429.256594] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic joydev eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep hid_logitech_hidpp snd_pcm x86_pkg_temp_thermal coretemp kvm_intel snd_seq_midi snd_seq_midi_event kvm i915_bpo snd_rawmidi crct10dif_pclmul snd_seq crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq_device aes_x86_64 snd_timer lrw gf128mul glue_helper ablk_helper snd intel_ips cryptd drm_kms_helper serio_raw drm soundcore shpchp i2c_algo_bit 8250_fintek i2c_hid mac_hid acpi_pad parport_pc ppdev lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic.efi.signed acpi=off noapic root=UUID=7f4115a3-3ef1-4538-aea4-82a28d784cd9 ro quiet splash vt.handoff=7
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000082ea2000-0x0000000082ea2fff] ACPI NVS
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008bc6f000-0x000000008bca7fff] ACPI data
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008bca8000-0x000000008c603fff] ACPI NVS
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.000000] efi:  ESRT=0x8d2ddd98  ACPI=0x8bc7a000  ACPI 2.0=0x8bc7a000  SMBIOS=0xf05e0  SMBIOS 3.0=0x8d2db000  MPS=0xfca20 
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic.efi.signed acpi=off noapic root=UUID=7f4115a3-3ef1-4538-aea4-82a28d784cd9 ro quiet splash vt.handoff=7
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.069633] PM: Registering ACPI NVS region [mem 0x82ea2000-0x82ea2fff] (4096 bytes)
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.069633] PM: Registering ACPI NVS region [mem 0x8bca8000-0x8c603fff] (9814016 bytes)
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.083836] ACPI: Interpreter disabled.
Oct 12 11:28:50 erniee-kubuntu-dev systemd[1]: Listening on ACPID Listen Socket.
Oct 12 11:28:50 erniee-kubuntu-dev systemd[1]: Starting ACPID Listen Socket.
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.114463] pnp: PnP ACPI: disabled
Oct 12 11:28:50 erniee-kubuntu-dev kernel: [    0.409847] ACPI: <n/a>: failed to evaluate _DSM (0x1001)
Oct 12 11:28:50 erniee-kubuntu-dev thermald[651]: failed to open /dev/acpi_thermal_rel
Oct 12 11:28:50 erniee-kubuntu-dev thermald[651]: failed to open /dev/acpi_thermal_rel
Oct 12 11:28:51 erniee-kubuntu-dev systemd[1]: Started ACPI event daemon.
Oct 12 11:28:51 erniee-kubuntu-dev systemd[1]: Starting ACPI event daemon...
Oct 12 11:28:51 erniee-kubuntu-dev acpid: starting up with netlink and the input layer
Oct 12 11:28:51 erniee-kubuntu-dev acpid: 9 rules loaded
Oct 12 11:28:51 erniee-kubuntu-dev acpid: waiting for events: event logging is off
Oct 12 11:28:51 erniee-kubuntu-dev acpid: client connected from 791[0:0]
Oct 12 11:28:51 erniee-kubuntu-dev acpid: 1 client rule loaded
Oct 12 11:29:46 erniee-kubuntu-dev ureadahead[255]: ureadahead:acpi: Ignored relative path
Oct 12 11:29:46 erniee-kubuntu-dev ureadahead[255]: ureadahead:acpi: Ignored relative path
Oct 12 13:16:21 erniee-kubuntu-dev systemd[1]: Stopping ACPI event daemon...
Oct 12 13:16:55 erniee-kubuntu-dev systemd[1]: Listening on ACPID Listen Socket.
Oct 12 13:16:55 erniee-kubuntu-dev systemd[1]: Starting ACPID Listen Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000082ea2000-0x0000000082ea2fff] ACPI NVS
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008bc6f000-0x000000008bca7fff] ACPI data
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008bca8000-0x000000008c603fff] ACPI NVS
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] efi:  ESRT=0x8d2ddd98  ACPI=0x8bc7a000  ACPI 2.0=0x8bc7a000  SMBIOS=0xf05e0  SMBIOS 3.0=0x8d2db000  MPS=0xfca20 
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Early table checksum verification disabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: RSDP 0x000000008BC7A000 000024 (v02 ALASKA)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: XSDT 0x000000008BC7A098 0000A4 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FACP 0x000000008BC9D388 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: DSDT 0x000000008BC7A1D0 0231B4 (v02 ALASKA A M I    01072009 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FACS 0x000000008C603F80 000040
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: APIC 0x000000008BC9D498 0000BC (v03 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FPDT 0x000000008BC9D558 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FIDT 0x000000008BC9D5A0 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: MCFG 0x000000008BC9D640 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: HPET 0x000000008BC9D680 000038 (v01 ALASKA A M I    01072009 AMI. 0005000B)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9D6B8 00036D (v01 SataRe SataTabl 00001000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LPIT 0x000000008BC9DA28 000094 (v01 INTEL  SKL      00000000 MSFT 0000005F)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9DAC0 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9DD08 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA08B8 000C45 (v02 INTEL  Ther_Rvp 00001000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: DBG2 0x000000008BCA1500 000054 (v00 INTEL           00000000 MSFT 0000005F)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA1558 000704 (v02 INTEL  xh_rvp08 00000000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA1C60 005205 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: UEFI 0x000000008BCA6E68 000042 (v01                 00000000      00000000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA6EB0 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000022] ACPI: Core revision 20141107
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.016739] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20141107/dswload-210)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.016742] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20141107/psobject-224)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.021962] ACPI: All ACPI Tables successfully acquired
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206518] PM: Registering ACPI NVS region [mem 0x82ea2000-0x82ea2fff] (4096 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206518] PM: Registering ACPI NVS region [mem 0x8bca8000-0x8c603fff] (9814016 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212025] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212026] ACPI: bus type PCI registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212027] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.216206] ACPI: Added _OSI(Module Device)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.216207] ACPI: Added _OSI(Processor Device)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.216207] ACPI: Added _OSI(3.0 _SCP Extensions)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.216208] ACPI: Added _OSI(Processor Aggregator Device)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.220815] ACPI: Executed 21 blocks of module-level executable AML code
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.224318] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.226312] ACPI: Dynamic OEM Table Load:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.226315] ACPI: SSDT 0xFFFF88084A443000 000768 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.226339] ACPI Error: Unknown opcode 0x19 at table offset 0x04D8, ignoring (20141107/psobject-105)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.227624] ACPI: Dynamic OEM Table Load:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.227627] ACPI: SSDT 0xFFFF88084A443800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231288] ACPI: Interpreter enabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231295] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231300] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231312] ACPI: (supports S0 S3 S4 S5)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231313] ACPI: Using IOAPIC for interrupt routing
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231332] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.232483] ACPI: Power Resource [PG00] (on)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.252232] ACPI: Power Resource [PG01] (on)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.272256] ACPI: Power Resource [PG02] (on)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.293394] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.293600] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.293804] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294006] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294209] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294411] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294612] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294823] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295025] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295229] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295437] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295642] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295844] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296043] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296248] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296453] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296655] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296857] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.297059] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.297262] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301054] ACPI: Power Resource [FN00] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301091] ACPI: Power Resource [FN01] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301128] ACPI: Power Resource [FN02] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301163] ACPI: Power Resource [FN03] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301199] ACPI: Power Resource [FN04] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301880] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301884] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301904] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302650] pci 0000:00:01.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302930] pci 0000:00:14.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303353] pci 0000:00:1b.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303478] pci 0000:00:1c.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303581] pci 0000:00:1c.2: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303699] pci 0000:00:1d.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304114] pci 0000:00:1f.3: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304551] pci 0000:00:1f.6: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304646] acpiphp: Slot [1] registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304866] pci 0000:03:00.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.312394] pci 0000:04:00.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.320517] pci 0000:06:00.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329264] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329295] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329325] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 *15)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329354] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329383] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329412] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329442] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329471] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329685] ACPI: Enabled 6 GPEs in block 00 to 7F
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329935] ACPI: bus type USB registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.330051] PCI: Using ACPI for IRQ routing
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364463] pnp: PnP ACPI init
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364649] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364981] pnp 00:01: Plug and Play ACPI device, IDs PNP0501 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365131] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365292] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365308] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365327] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365466] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365492] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.366180] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.366907] pnp: PnP ACPI: found 9 devices
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651593] ACPI: Sleep Button [SLPB]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651610] ACPI: Power Button [PWRB]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651628] ACPI: Power Button [PWRF]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.652545] ACPI: Thermal Zone [TZ00] (28 C)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.652681] ACPI: Thermal Zone [TZ01] (30 C)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.680746] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.680748] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS01._PLD] (Node ffff88084e1132f8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.681444] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.681445] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS02._PLD] (Node ffff88084e113348), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.682177] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.682178] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS03._PLD] (Node ffff88084e113398), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.682797] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.682798] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS04._PLD] (Node ffff88084e1133e8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.683494] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.683496] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS05._PLD] (Node ffff88084e113438), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.684113] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.684114] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS06._PLD] (Node ffff88084e113488), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.684767] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.684768] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS07._PLD] (Node ffff88084e1134d8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.685424] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.685425] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS08._PLD] (Node ffff88084e113528), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.686220] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.686221] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS09._PLD] (Node ffff88084e113578), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.686872] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.686873] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS10._PLD] (Node ffff88084e1135c8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.768239] ACPI PCC probe failed.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.796620] asus_wmi: Disabling ACPI video driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.821177] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Oct 12 13:16:55 erniee-kubuntu-dev sensors[737]: acpitz-virtual-0
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: sensor_update: type acpitz
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: sensor_update: type acpitz
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: failed to open /dev/acpi_thermal_rel
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: failed to open /dev/acpi_thermal_rel
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: sensor index:1 acpitz /sys/class/thermal/thermal_zone1/ Async:0
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: zone acpitz bounded
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: message repeated 4 times: [ zone acpitz bounded]
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: /sys/class/hwmon/hwmon0/name->acpitz
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: Zone 0: acpitz, Active:0 Bind:1 Sensor_cnt:1
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: Zone 1: acpitz, Active:0 Bind:0 Sensor_cnt:1
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Oct 12 13:16:56 erniee-kubuntu-dev systemd[1]: Started ACPI event daemon.
Oct 12 13:16:56 erniee-kubuntu-dev systemd[1]: Starting ACPI event daemon...
Oct 12 13:16:56 erniee-kubuntu-dev acpid: starting up with netlink and the input layer
Oct 12 13:16:56 erniee-kubuntu-dev acpid: 9 rules loaded
Oct 12 13:16:56 erniee-kubuntu-dev acpid: waiting for events: event logging is off
Oct 12 13:16:56 erniee-kubuntu-dev acpid: client connected from 845[0:0]
Oct 12 13:16:56 erniee-kubuntu-dev acpid: 1 client rule loaded

```[FONT=monospace]

[/FONT]
[FONT=monospace]This is filtered for [COLOR=#ff0000]kernel[/COLOR]. (I am also having issues with avhi-daemon flooding the logs.)
[/FONT]```
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Initializing cgroup subsys cpuacct
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Linux version 3.19.0-30-generic (buildd@lcy01-14) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ) #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 (Ubuntu 3.19.0-30.34-generic 3.19.8-ckt6)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic.efi.signed root=UUID=7f4115a3-3ef1-4538-aea4-82a28d784cd9 ro quiet splash vt.handoff=7
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] KERNEL supported cpus:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   Intel GenuineIntel
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   AMD AuthenticAMD
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   Centaur CentaurHauls
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000082ea1fff] usable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000082ea2000-0x0000000082ea2fff] ACPI NVS
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000082ea3000-0x0000000082eecfff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000082eed000-0x0000000082f2afff] usable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000082f2b000-0x0000000083456fff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000083457000-0x000000008a787fff] usable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008a788000-0x000000008bc6efff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008bc6f000-0x000000008bca7fff] ACPI data
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008bca8000-0x000000008c603fff] ACPI NVS
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008c604000-0x000000008d397fff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008d398000-0x000000008d3fefff] type 20
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x000000008d3ff000-0x000000008d3fffff] usable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000086effffff] usable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] efi: EFI v2.40 by American Megatrends
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] efi:  ESRT=0x8d2ddd98  ACPI=0x8bc7a000  ACPI 2.0=0x8bc7a000  SMBIOS=0xf05e0  SMBIOS 3.0=0x8d2db000  MPS=0xfca20 
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] esrt: Reserving ESRT space from 0x000000008d2ddd98 to 0x000000008d2dddd0.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] SMBIOS 3.0 present.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] AGP: No AGP bridge found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] e820: last_pfn = 0x86f000 max_arch_pfn = 0x400000000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] MTRR default type: write-back
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   00000-9FFFF write-back
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   C0000-FFFFF write-protect
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] MTRR variable ranges enabled:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   0 base 00C0000000 mask 7FC0000000 uncachable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   1 base 00A0000000 mask 7FE0000000 uncachable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   2 base 0090000000 mask 7FF0000000 uncachable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   3 base 008E000000 mask 7FFE000000 uncachable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   4 base 008D800000 mask 7FFF800000 uncachable
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   5 disabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   6 disabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   7 disabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   8 disabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   9 disabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] e820: last_pfn = 0x8d400 max_arch_pfn = 0x400000000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] found SMP MP-table at [mem 0x000fccd0-0x000fccdf] mapped at [ffff8800000fccd0]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Scanning 1 areas for low memory corruption
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Using GB pages for direct mapping
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BRK [0x02fe5000, 0x02fe5fff] PGTABLE
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BRK [0x02fe6000, 0x02fe6fff] PGTABLE
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BRK [0x02fe7000, 0x02fe7fff] PGTABLE
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x86ee00000-0x86effffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x86ee00000-0x86effffff] page 2M
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BRK [0x02fe8000, 0x02fe8fff] PGTABLE
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x860000000-0x86edfffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x860000000-0x86edfffff] page 2M
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x840000000-0x85fffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x840000000-0x85fffffff] page 2M
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x82ea1fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x80000000-0x82dfffff] page 2M
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x82e00000-0x82ea1fff] page 4k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x82eed000-0x82f2afff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x82eed000-0x82f2afff] page 4k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x83457000-0x8a787fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x83457000-0x835fffff] page 4k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x83600000-0x8a5fffff] page 2M
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x8a600000-0x8a787fff] page 4k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BRK [0x02fe9000, 0x02fe9fff] PGTABLE
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] BRK [0x02fea000, 0x02feafff] PGTABLE
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x8d3ff000-0x8d3fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x8d3ff000-0x8d3fffff] page 4k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x83fffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [mem 0x100000000-0x83fffffff] page 1G
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] RAMDISK: [mem 0x345d6000-0x362e2fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Early table checksum verification disabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: RSDP 0x000000008BC7A000 000024 (v02 ALASKA)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: XSDT 0x000000008BC7A098 0000A4 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FACP 0x000000008BC9D388 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: DSDT 0x000000008BC7A1D0 0231B4 (v02 ALASKA A M I    01072009 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FACS 0x000000008C603F80 000040
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: APIC 0x000000008BC9D498 0000BC (v03 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FPDT 0x000000008BC9D558 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: FIDT 0x000000008BC9D5A0 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: MCFG 0x000000008BC9D640 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: HPET 0x000000008BC9D680 000038 (v01 ALASKA A M I    01072009 AMI. 0005000B)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9D6B8 00036D (v01 SataRe SataTabl 00001000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LPIT 0x000000008BC9DA28 000094 (v01 INTEL  SKL      00000000 MSFT 0000005F)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9DAC0 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BC9DD08 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA08B8 000C45 (v02 INTEL  Ther_Rvp 00001000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: DBG2 0x000000008BCA1500 000054 (v00 INTEL           00000000 MSFT 0000005F)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA1558 000704 (v02 INTEL  xh_rvp08 00000000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA1C60 005205 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: UEFI 0x000000008BCA6E68 000042 (v01                 00000000      00000000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: SSDT 0x000000008BCA6EB0 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] No NUMA configuration found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000086effffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x86eff8000-0x86effcfff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]  [ffffea0000000000-ffffea0021bfffff] PMD -> [ffff88084e600000-ffff88086e5fffff] on node 0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Zone ranges:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   Normal   [mem 0x100000000-0x86effffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Movable zone start for each node
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Early memory node ranges
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   node   0: [mem 0x00001000-0x00057fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   node   0: [mem 0x00059000-0x0009efff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   node   0: [mem 0x00100000-0x82ea1fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   node   0: [mem 0x82eed000-0x82f2afff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   node   0: [mem 0x83457000-0x8a787fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   node   0: [mem 0x8d3ff000-0x8d3fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   node   0: [mem 0x100000000-0x86effffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Initmem setup node 0 [mem 0x00001000-0x86effffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] On node 0 totalpages: 8360367
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   DMA zone: 26 pages reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   DMA32 zone: 8777 pages used for memmap
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   DMA32 zone: 561682 pages, LIFO batch:31
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   Normal zone: 121792 pages used for memmap
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]   Normal zone: 7794688 pages, LIFO batch:31
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Reserving Intel graphics stolen memory at 0x8e000000-0x8fffffff
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1808
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x82ea2000-0x82ea2fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x82ea3000-0x82eecfff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x82f2b000-0x83456fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8a788000-0x8bc6efff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8bc6f000-0x8bca7fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8bca8000-0x8c603fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8c604000-0x8d397fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8d398000-0x8d3fefff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8d400000-0x8dffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8e000000-0x8fffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0x90000000-0xdfffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] e820: [mem 0x90000000-0xdfffffff] available for PCI devices
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88086ec00000 s87104 r8192 d31680 u262144
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] pcpu-alloc: s87104 r8192 d31680 u262144 alloc=1*2097152
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 8229708
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Policy zone: Normal
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic.efi.signed root=UUID=7f4115a3-3ef1-4538-aea4-82a28d784cd9 ro quiet splash vt.handoff=7
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] xsave: enabled xstate_bv 0x1f, cntxt size 0x440 using standard form
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] AGP: Checking aperture...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] AGP: No AGP bridge found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Memory: 32661252K/33441468K available (8004K kernel code, 1234K rwdata, 3764K rodata, 1408K init, 1300K bss, 780216K reserved, 0K cma-reserved)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Hierarchical RCU implementation.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] NR_IRQS:16640 nr_irqs:2048 16
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-7.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] vt handoff: transparent VT on vt#7
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] Console: colour dummy device 80x25
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] console [tty0] enabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] hpet clockevent registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] tsc: Fast TSC calibration failed
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] tsc: PIT calibration matches HPET. 1 loops
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000000] tsc: Detected 4006.228 MHz processor
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000018] Calibrating delay loop (skipped), value calculated using timer frequency.. 8012.45 BogoMIPS (lpj=16024912)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000019] pid_max: default: 32768 minimum: 301
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.000022] ACPI: Core revision 20141107
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.016739] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20141107/dswload-210)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.016742] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20141107/psobject-224)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.021962] ACPI: All ACPI Tables successfully acquired
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.023270] Security Framework initialized
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.023279] AppArmor: AppArmor initialized
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.023280] Yama: becoming mindful.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.024358] Dentry cache hash table entries: 4194304 (order: 13, 33554432 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.027872] Inode-cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029347] Mount-cache hash table entries: 65536 (order: 7, 524288 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029365] Mountpoint-cache hash table entries: 65536 (order: 7, 524288 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029538] Initializing cgroup subsys memory
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029541] Initializing cgroup subsys devices
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029542] Initializing cgroup subsys freezer
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029543] Initializing cgroup subsys net_cls
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029544] Initializing cgroup subsys blkio
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029545] Initializing cgroup subsys perf_event
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029546] Initializing cgroup subsys net_prio
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029547] Initializing cgroup subsys hugetlb
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029562] CPU: Physical Processor ID: 0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029563] CPU: Processor Core ID: 0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029565] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.029565] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.030500] mce: CPU supports 10 MCE banks
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.030511] CPU0: Thermal monitoring enabled (TM1)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.030518] process: using mwait in idle threads
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.030520] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.030520] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.030746] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.046986] ftrace: allocating 30120 entries in 118 pages
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.058899] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098645] smpboot: CPU0: Intel(R) Core(TM) i7-6700K CPU @ 4.00GHz (fam: 06, model: 5e, stepping: 03)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098651] TSC deadline timer enabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098668] Performance Events: no PEBS fmt3+, generic architected perfmon, full-width counters, Intel PMU driver.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098671] ... version:                4
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098671] ... bit width:              48
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098671] ... generic registers:      4
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098672] ... value mask:             0000ffffffffffff
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098672] ... max period:             0000ffffffffffff
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098673] ... fixed-purpose events:   3
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.098673] ... event mask:             000000070000000f
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.099154] x86: Booting SMP configuration:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.099154] .... node  #0, CPUs:      #1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.113149] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.113203]  #2 #3 #4 #5 #6 #7
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.198193] x86: Booted up 1 node, 8 CPUs
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.198196] smpboot: Total of 8 processors activated (64099.64 BogoMIPS)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.204134] devtmpfs: initialized
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206488] evm: security.selinux
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206489] evm: security.SMACK64
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206489] evm: security.SMACK64EXEC
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206490] evm: security.SMACK64TRANSMUTE
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206490] evm: security.SMACK64MMAP
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206491] evm: security.ima
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206491] evm: security.capability
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206518] PM: Registering ACPI NVS region [mem 0x82ea2000-0x82ea2fff] (4096 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206518] PM: Registering ACPI NVS region [mem 0x8bca8000-0x8c603fff] (9814016 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206667] pinctrl core: initialized pinctrl subsystem
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206791] RTC time: 20:16:52, date: 10/12/15
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.206855] NET: Registered protocol family 16
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.207989] cpuidle: using governor ladder
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.211995] cpuidle: using governor menu
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212025] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212026] ACPI: bus type PCI registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212027] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212070] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212071] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.212236] PCI: Using configuration type 1 for base access
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.216206] ACPI: Added _OSI(Module Device)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.216207] ACPI: Added _OSI(Processor Device)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.216207] ACPI: Added _OSI(3.0 _SCP Extensions)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.216208] ACPI: Added _OSI(Processor Aggregator Device)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.220815] ACPI: Executed 21 blocks of module-level executable AML code
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.224318] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.226312] ACPI: Dynamic OEM Table Load:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.226315] ACPI: SSDT 0xFFFF88084A443000 000768 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.226339] ACPI Error: Unknown opcode 0x19 at table offset 0x04D8, ignoring (20141107/psobject-105)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.227624] ACPI: Dynamic OEM Table Load:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.227627] ACPI: SSDT 0xFFFF88084A443800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231288] ACPI: Interpreter enabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231295] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231300] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231312] ACPI: (supports S0 S3 S4 S5)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231313] ACPI: Using IOAPIC for interrupt routing
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.231332] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.232483] ACPI: Power Resource [PG00] (on)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.252232] ACPI: Power Resource [PG01] (on)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.272256] ACPI: Power Resource [PG02] (on)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.293394] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.293600] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.293804] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294006] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294209] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294411] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294612] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.294823] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295025] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295229] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295437] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295642] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.295844] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296043] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296248] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296453] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296655] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.296857] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.297059] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.297262] ACPI: Power Resource [WRST] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301054] ACPI: Power Resource [FN00] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301091] ACPI: Power Resource [FN01] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301128] ACPI: Power Resource [FN02] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301163] ACPI: Power Resource [FN03] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301199] ACPI: Power Resource [FN04] (off)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301880] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301884] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301901] \_SB_.PCI0:_OSC invalid UUID
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301902] _OSC request data:1 1f 0 
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.301904] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302411] PCI host bridge to bus 0000:00
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302413] pci_bus 0000:00: root bus resource [bus 00-fe]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302414] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302415] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302416] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302416] pci_bus 0000:00: root bus resource [mem 0x90000000-0xdfffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302417] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302422] pci 0000:00:00.0: [8086:191f] type 00 class 0x060000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302586] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302612] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302650] pci 0000:00:01.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302690] pci 0000:00:02.0: [8086:1912] type 00 class 0x030000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302696] pci 0000:00:02.0: reg 0x10: [mem 0xde000000-0xdeffffff 64bit]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302699] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302702] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302822] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302837] pci 0000:00:14.0: reg 0x10: [mem 0xdf230000-0xdf23ffff 64bit]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302891] pci 0000:00:14.0: PME# supported from D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302930] pci 0000:00:14.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302974] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.302993] pci 0000:00:16.0: reg 0x10: [mem 0xdf24d000-0xdf24dfff 64bit]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303055] pci 0000:00:16.0: PME# supported from D3hot
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303133] pci 0000:00:17.0: [8086:a102] type 00 class 0x010601
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303145] pci 0000:00:17.0: reg 0x10: [mem 0xdf248000-0xdf249fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303151] pci 0000:00:17.0: reg 0x14: [mem 0xdf24c000-0xdf24c0ff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303156] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303162] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303167] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303173] pci 0000:00:17.0: reg 0x24: [mem 0xdf24b000-0xdf24b7ff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303206] pci 0000:00:17.0: PME# supported from D3hot
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303264] pci 0000:00:1b.0: [8086:a167] type 01 class 0x060400
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303316] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303353] pci 0000:00:1b.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303394] pci 0000:00:1c.0: [8086:a110] type 01 class 0x060400
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303441] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303478] pci 0000:00:1c.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303498] pci 0000:00:1c.2: [8086:a112] type 01 class 0x060400
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303544] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303581] pci 0000:00:1c.2: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303614] pci 0000:00:1d.0: [8086:a118] type 01 class 0x060400
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303663] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303699] pci 0000:00:1d.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303743] pci 0000:00:1f.0: [8086:a145] type 00 class 0x060100
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303877] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303886] pci 0000:00:1f.2: reg 0x10: [mem 0xdf244000-0xdf247fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.303980] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304001] pci 0000:00:1f.3: reg 0x10: [mem 0xdf240000-0xdf243fff 64bit]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304028] pci 0000:00:1f.3: reg 0x20: [mem 0xdf220000-0xdf22ffff 64bit]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304071] pci 0000:00:1f.3: PME# supported from D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304114] pci 0000:00:1f.3: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304139] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304186] pci 0000:00:1f.4: reg 0x10: [mem 0xdf24a000-0xdf24a0ff 64bit]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304255] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304383] pci 0000:00:1f.6: [8086:15b8] type 00 class 0x020000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304404] pci 0000:00:1f.6: reg 0x10: [mem 0xdf200000-0xdf21ffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304504] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304551] pci 0000:00:1f.6: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304587] pci 0000:00:01.0: PCI bridge to [bus 01]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304646] acpiphp: Slot [1] registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304649] pci 0000:00:1b.0: PCI bridge to [bus 02]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304718] pci 0000:03:00.0: [1b21:1242] type 00 class 0x0c0330
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304737] pci 0000:03:00.0: reg 0x10: [mem 0xdf100000-0xdf107fff 64bit]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304839] pci 0000:03:00.0: PME# supported from D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.304866] pci 0000:03:00.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.312180] pci 0000:00:1c.0: PCI bridge to [bus 03]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.312183] pci 0000:00:1c.0:   bridge window [mem 0xdf100000-0xdf1fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.312252] pci 0000:04:00.0: [1b21:1080] type 01 class 0x060400
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.312369] pci 0000:04:00.0: supports D1 D2
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.312369] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.312394] pci 0000:04:00.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.320193] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.320308] pci 0000:04:00.0: PCI bridge to [bus 05]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.320389] pci 0000:06:00.0: [144d:a800] type 00 class 0x010601
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.320438] pci 0000:06:00.0: reg 0x24: [mem 0xdf010000-0xdf011fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.320446] pci 0000:06:00.0: reg 0x30: [mem 0xdf000000-0xdf00ffff pref]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.320495] pci 0000:06:00.0: PME# supported from D3hot D3cold
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.320517] pci 0000:06:00.0: System wakeup disabled by ACPI
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.328207] pci 0000:00:1d.0: PCI bridge to [bus 06]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.328210] pci 0000:00:1d.0:   bridge window [mem 0xdf000000-0xdf0fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329264] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329295] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329325] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 *15)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329354] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329383] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329412] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329442] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329471] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329685] ACPI: Enabled 6 GPEs in block 00 to 7F
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329786] vgaarb: setting as boot device: PCI:0000:00:02.0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329787] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329789] vgaarb: loaded
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329789] vgaarb: bridge control possible 0000:00:02.0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329905] SCSI subsystem initialized
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329923] libata version 3.00 loaded.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329935] ACPI: bus type USB registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329943] usbcore: registered new interface driver usbfs
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329947] usbcore: registered new interface driver hub
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.329959] usbcore: registered new device driver usb
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.330051] PCI: Using ACPI for IRQ routing
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.358966] PCI: pci_cache_line_size set to 64 bytes
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359023] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359023] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359024] e820: reserve RAM buffer [mem 0x82ea2000-0x83ffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359025] e820: reserve RAM buffer [mem 0x82f2b000-0x83ffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359025] e820: reserve RAM buffer [mem 0x8a788000-0x8bffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359026] e820: reserve RAM buffer [mem 0x8d400000-0x8fffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359027] e820: reserve RAM buffer [mem 0x86f000000-0x86fffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359082] NetLabel: Initializing
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359083] NetLabel:  domain hash size = 128
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359083] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359089] NetLabel:  unlabeled traffic allowed by default
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359157] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.359160] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.361211] Switched to clocksource hpet
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364437] AppArmor: AppArmor Filesystem Enabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364463] pnp: PnP ACPI init
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364647] system 00:00: [io  0x0290-0x029f] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364649] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364944] pnp 00:01: [dma 0 disabled]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.364981] pnp 00:01: Plug and Play ACPI device, IDs PNP0501 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365126] system 00:02: [io  0x0680-0x069f] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365127] system 00:02: [io  0xffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365128] system 00:02: [io  0xffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365128] system 00:02: [io  0xffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365129] system 00:02: [io  0x1800-0x18fe] could not be reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365130] system 00:02: [io  0x164e-0x164f] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365131] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365291] system 00:03: [io  0x0800-0x087f] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365292] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365308] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365326] system 00:05: [io  0x1854-0x1857] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365327] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365457] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365458] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365459] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365460] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365460] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365461] system 00:06: [mem 0xfed90000-0xfed93fff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365462] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365463] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365464] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365465] system 00:06: [mem 0xdffc0000-0xdffdffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365466] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365485] system 00:07: [mem 0xfd000000-0xfdabffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365486] system 00:07: [mem 0xfdad0000-0xfdadffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365487] system 00:07: [mem 0xfdb00000-0xfdffffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365488] system 00:07: [mem 0xfe000000-0xfe01ffff] could not be reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365489] system 00:07: [mem 0xfe036000-0xfe03bfff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365490] system 00:07: [mem 0xfe03d000-0xfe3fffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365491] system 00:07: [mem 0xfe410000-0xfe7fffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.365492] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.366177] system 00:08: [mem 0xfdaf0000-0xfdafffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.366178] system 00:08: [mem 0xfdae0000-0xfdaeffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.366179] system 00:08: [mem 0xfdac0000-0xfdacffff] has been reserved
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.366180] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.366907] pnp: PnP ACPI: found 9 devices
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375773] pci 0000:00:1b.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375775] pci 0000:00:1b.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375776] pci 0000:00:1b.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375823] pci 0000:00:1b.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375824] pci 0000:00:1b.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375825] pci 0000:00:1b.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375826] pci 0000:00:1b.0: BAR 14: assigned [mem 0x90000000-0x901fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375829] pci 0000:00:1b.0: BAR 15: assigned [mem 0x90200000-0x903fffff 64bit pref]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375830] pci 0000:00:1b.0: BAR 13: assigned [io  0x2000-0x2fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375831] pci 0000:00:01.0: PCI bridge to [bus 01]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375848] pci 0000:00:1b.0: PCI bridge to [bus 02]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375853] pci 0000:00:1b.0:   bridge window [io  0x2000-0x2fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375863] pci 0000:00:1b.0:   bridge window [mem 0x90000000-0x901fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375865] pci 0000:00:1b.0:   bridge window [mem 0x90200000-0x903fffff 64bit pref]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375868] pci 0000:00:1c.0: PCI bridge to [bus 03]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375871] pci 0000:00:1c.0:   bridge window [mem 0xdf100000-0xdf1fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375887] pci 0000:04:00.0: PCI bridge to [bus 05]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375918] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375923] pci 0000:00:1d.0: PCI bridge to [bus 06]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375926] pci 0000:00:1d.0:   bridge window [mem 0xdf000000-0xdf0fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375938] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375939] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375940] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375941] pci_bus 0000:00: resource 7 [mem 0x90000000-0xdfffffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375941] pci_bus 0000:00: resource 8 [mem 0xfd000000-0xfe7fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375942] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375943] pci_bus 0000:02: resource 1 [mem 0x90000000-0x901fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375944] pci_bus 0000:02: resource 2 [mem 0x90200000-0x903fffff 64bit pref]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375944] pci_bus 0000:03: resource 1 [mem 0xdf100000-0xdf1fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375945] pci_bus 0000:06: resource 1 [mem 0xdf000000-0xdf0fffff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.375958] NET: Registered protocol family 2
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.376089] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.376286] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.376364] TCP: Hash tables configured (established 262144 bind 65536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.376372] TCP: reno registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.376388] UDP hash table entries: 16384 (order: 7, 524288 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.376443] UDP-Lite hash table entries: 16384 (order: 7, 524288 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.376504] NET: Registered protocol family 1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.376520] pci 0000:00:02.0: Video device with shadowed ROM
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.377200] PCI: CLS 0 bytes, default 64
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.377222] Trying to unpack rootfs image as initramfs...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.523347] random: nonblocking pool is initialized
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646309] Freeing initrd memory: 29748K (ffff8800345d6000 - ffff8800362e3000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646327] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646328] software IO TLB [mem 0x7d4ce000-0x814ce000] (64MB) mapped at [ffff88007d4ce000-ffff8800814cdfff]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646638] microcode: CPU0 sig=0x506e3, pf=0x2, revision=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646641] microcode: CPU1 sig=0x506e3, pf=0x2, revision=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646648] microcode: CPU2 sig=0x506e3, pf=0x2, revision=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646662] microcode: CPU3 sig=0x506e3, pf=0x2, revision=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646680] microcode: CPU4 sig=0x506e3, pf=0x2, revision=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646689] microcode: CPU5 sig=0x506e3, pf=0x2, revision=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646698] microcode: CPU6 sig=0x506e3, pf=0x2, revision=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646708] microcode: CPU7 sig=0x506e3, pf=0x2, revision=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646793] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.646813] Scanning for low memory corruption every 60 seconds
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.647212] futex hash table entries: 2048 (order: 5, 131072 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.647225] Initialise system trusted keyring
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.647236] audit: initializing netlink subsys (disabled)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.647246] audit: type=2000 audit(1444681012.636:1): initialized
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.647502] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.648182] zpool: loaded
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.648183] zbud: loaded
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.648360] VFS: Disk quotas dquot_6.5.2
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.648376] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.648745] fuse init (API version 7.23)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.648870] Key type big_key registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.650654] Key type asymmetric registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.650656] Asymmetric key parser 'x509' registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.650673] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.650870] io scheduler noop registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.650872] io scheduler deadline registered (default)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.650886] io scheduler cfq registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651396] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651403] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651419] efifb: probing for efifb
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651428] efifb: framebuffer at 0xc0000000, mapped to 0xffffc90013600000, using 3072k, total 3072k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651429] efifb: mode is 1024x768x32, linelength=4096, pages=1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651429] efifb: scrolling: redraw
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651430] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651530] Console: switching to colour frame buffer device 128x48
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651537] fb0: EFI VGA frame buffer device
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651541] intel_idle: does not run on family 6 model 94
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651591] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651593] ACPI: Sleep Button [SLPB]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651610] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651610] ACPI: Power Button [PWRB]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651627] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.651628] ACPI: Power Button [PWRF]
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.652544] thermal LNXTHERM:00: registered as thermal_zone0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.652545] ACPI: Thermal Zone [TZ00] (28 C)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.652680] thermal LNXTHERM:01: registered as thermal_zone1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.652681] ACPI: Thermal Zone [TZ01] (30 C)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.652699] GHES: HEST is not enabled!
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.652802] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.673947] 00:01: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.676752] Linux agpgart interface v0.103
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.678500] brd: module loaded
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679307] loop: module loaded
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679440] libphy: Fixed MDIO Bus: probed
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679441] tun: Universal TUN/TAP device driver, 1.6
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679442] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679517] PPP generic driver version 2.4.2
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679677] xhci_hcd 0000:00:14.0: xHCI Host Controller
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679680] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679841] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679935] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679935] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679936] usb usb1: Product: xHCI Host Controller
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679937] usb usb1: Manufacturer: Linux 3.19.0-30-generic xhci-hcd
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.679938] usb usb1: SerialNumber: 0000:00:14.0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.680045] hub 1-0:1.0: USB hub found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.680080] hub 1-0:1.0: 16 ports detected
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.680746] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.680748] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS01._PLD] (Node ffff88084e1132f8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.681444] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.681445] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS02._PLD] (Node ffff88084e113348), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.682177] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.682178] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS03._PLD] (Node ffff88084e113398), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.682797] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.682798] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS04._PLD] (Node ffff88084e1133e8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.683494] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.683496] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS05._PLD] (Node ffff88084e113438), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.684113] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.684114] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS06._PLD] (Node ffff88084e113488), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.684767] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.684768] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS07._PLD] (Node ffff88084e1134d8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.685424] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.685425] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS08._PLD] (Node ffff88084e113528), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.686220] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.686221] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS09._PLD] (Node ffff88084e113578), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.686872] ACPI Error: No object attached to node [UHSD] ffff88084e1132a8 (20141107/exresnte-128)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.686873] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HS10._PLD] (Node ffff88084e1135c8), AE_AML_NO_OPERAND (20141107/psparse-536)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.690947] xhci_hcd 0000:00:14.0: xHCI Host Controller
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.690948] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.690980] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.690981] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.690981] usb usb2: Product: xHCI Host Controller
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.690982] usb usb2: Manufacturer: Linux 3.19.0-30-generic xhci-hcd
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.690983] usb usb2: SerialNumber: 0000:00:14.0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.691096] hub 2-0:1.0: USB hub found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.691107] hub 2-0:1.0: 10 ports detected
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.698010] xhci_hcd 0000:03:00.0: xHCI Host Controller
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.698013] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757122] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757123] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757123] usb usb3: Product: xHCI Host Controller
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757124] usb usb3: Manufacturer: Linux 3.19.0-30-generic xhci-hcd
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757125] usb usb3: SerialNumber: 0000:03:00.0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757250] hub 3-0:1.0: USB hub found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757254] hub 3-0:1.0: 2 ports detected
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757317] xhci_hcd 0000:03:00.0: xHCI Host Controller
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757318] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 4
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757343] usb usb4: We don't know the algorithms for LPM for this host, disabling LPM.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757351] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757351] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757352] usb usb4: Product: xHCI Host Controller
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757353] usb usb4: Manufacturer: Linux 3.19.0-30-generic xhci-hcd
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757353] usb usb4: SerialNumber: 0000:03:00.0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757454] hub 4-0:1.0: USB hub found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757461] hub 4-0:1.0: 2 ports detected
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757518] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757520] ehci-pci: EHCI PCI platform driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757526] ehci-platform: EHCI generic platform driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757531] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757534] ohci-pci: OHCI PCI platform driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757539] ohci-platform: OHCI generic platform driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757543] uhci_hcd: USB Universal Host Controller Interface driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.757567] i8042: PNP: No PS/2 controller found. Probing ports directly.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.760787] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.760790] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.760951] mousedev: PS/2 mouse device common for all mice
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.761195] rtc_cmos 00:04: RTC can wake from S4
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.761650] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.761775] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.761784] i2c /dev entries driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.761813] device-mapper: uevent: version 1.0.3
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.761887] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.761900] ledtrig-cpu: registered to indicate activity on CPUs
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.761914] EFI Variables Facility v0.08 2004-May-17
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.768238] PCCT header not found.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.768239] ACPI PCC probe failed.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.768286] TCP: cubic registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.768334] NET: Registered protocol family 10
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.768587] NET: Registered protocol family 17
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.768594] Key type dns_resolver registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.768990] Loading compiled-in X.509 certificates
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.769420] Loaded X.509 cert 'Magrathea: Glacier signing key: 08411dd668c266d59a96c625b3012497b2351542'
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.769426] registered taskstats version 1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.771030] Key type trusted registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.774078] Key type encrypted registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.774082] AppArmor: AppArmor sha1 policy hashing enabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.774084] ima: No TPM chip found, activating TPM-bypass!
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.774096] evm: HMAC attrs: 0x1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.775452]   Magic number: 3:767:295
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.775463] tty tty28: hash matches
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.775490] memory memory157: hash matches
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.775783] rtc_cmos 00:04: setting system clock to 2015-10-12 20:16:53 UTC (1444681013)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.777373] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.777373] EDD information not available.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.777412] PM: Hibernation image not present or could not be loaded.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.777816] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.777817] Write protecting the kernel read-only data: 12288k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.778306] Freeing unused kernel memory: 176K (ffff8800027d4000 - ffff880002800000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.778523] Freeing unused kernel memory: 332K (ffff880002bad000 - ffff880002c00000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.797778] wmi: Mapper loaded
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.814015] ahci 0000:00:17.0: version 3.0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.814426] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.814428] ahci 0000:00:17.0: flags: 64bit ncq sntf led clo only pio slum part ems deso sadm sds apst 
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.815192] pps_core: LinuxPPS API ver. 1 registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.815193] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.817086] PTP clock support registered
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.821576] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.821577] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.839051] scsi host0: ahci
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.839482] scsi host1: ahci
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.839956] scsi host2: ahci
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.840316] scsi host3: ahci
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.840353] ata1: SATA max UDMA/133 abar m2048@0xdf24b000 port 0xdf24b100 irq 130
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.840357] ata2: SATA max UDMA/133 abar m2048@0xdf24b000 port 0xdf24b180 irq 130
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.840361] ata3: SATA max UDMA/133 abar m2048@0xdf24b000 port 0xdf24b200 irq 130
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.840366] ata4: SATA max UDMA/133 abar m2048@0xdf24b000 port 0xdf24b280 irq 130
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.840923] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.854342] ahci 0000:06:00.0: AHCI 0001.0300 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.854346] ahci 0000:06:00.0: flags: 64bit ncq led clo only pio ccc 
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.854805] scsi host4: ahci
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    0.854867] ata5: SATA max UDMA/133 abar m8192@0xdf010000 port 0xdf010100 irq 16
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.002562] usb 1-10: new full-speed USB device number 2 using xhci_hcd
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.132958] usb 1-10: New USB device found, idVendor=046d, idProduct=c52b
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.132959] usb 1-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.132960] usb 1-10: Product: USB Receiver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.132961] usb 1-10: Manufacturer: Logitech
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.135439] hidraw: raw HID events driver (C) Jiri Kosina
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.139846] usbcore: registered new interface driver usbhid
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.139847] usbhid: USB HID core driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.141781] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-10/input2
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.158964] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.158997] ata2: SATA link down (SStatus 4 SControl 300)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.159053] ata1: SATA link down (SStatus 4 SControl 300)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.159156] ata4: SATA link down (SStatus 4 SControl 300)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.159683] ata3.00: failed to get NCQ Send/Recv Log Emask 0x1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.159684] ata3.00: ATA-9: Samsung SSD 840 Series, DXT08B0Q, max UDMA/133
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.159685] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.160047] ata3.00: failed to get NCQ Send/Recv Log Emask 0x1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.160124] ata3.00: configured for UDMA/133
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.160247] scsi 2:0:0:0: Direct-Access     ATA      Samsung SSD 840  8B0Q PQ: 0 ANSI: 5
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.160564] ata3.00: Enabling discard_zeroes_data
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.160641] sd 2:0:0:0: Attached scsi generic sg0 type 0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.160652] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.161132] sd 2:0:0:0: [sda] Write Protect is off
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.161133] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.161211] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.161410] ata3.00: Enabling discard_zeroes_data
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.163668]  sda: sda1 sda2 sda3 sda4 sda5
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.164270] ata3.00: Enabling discard_zeroes_data
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.164777] sd 2:0:0:0: [sda] Attached SCSI disk
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.182966] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.183225] ata5.00: ATA-9: SAMSUNG MZHPU512HCGL-00004, UXM6501Q, max UDMA/133
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.183226] ata5.00: 1000215216 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.183513] ata5.00: configured for UDMA/133
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.183629] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG MZHPU512 501Q PQ: 0 ANSI: 5
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.183999] sd 4:0:0:0: Attached scsi generic sg1 type 0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.184033] sd 4:0:0:0: [sdb] 1000215216 512-byte logical blocks: (512 GB/476 GiB)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.184728] sd 4:0:0:0: [sdb] Write Protect is off
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.184729] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.184876] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.186499]  sdb: sdb1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.186723] sd 4:0:0:0: [sdb] Attached SCSI disk
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.187704] e1000e 0000:00:1f.6 eth0: registered PHC clock
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.187706] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 30:5a:3a:54:ce:9d
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.187707] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.187766] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    1.647830] tsc: Refined TSC clocksource calibration: 4007.996 MHz
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.314827] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.455365] systemd[1]: Inserted module 'autofs4'
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.470673] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.470767] systemd[1]: Detected architecture x86-64.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.471199] systemd[1]: Set hostname to <erniee-kubuntu-dev>.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546195] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546200] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546288] systemd[1]: Created slice Root Slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546292] systemd[1]: Starting Root Slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546378] systemd[1]: Listening on Journal Socket (/dev/log).
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546382] systemd[1]: Starting Journal Socket (/dev/log).
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546473] systemd[1]: Listening on Journal Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546479] systemd[1]: Starting Journal Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546563] systemd[1]: Listening on Delayed Shutdown Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546566] systemd[1]: Starting Delayed Shutdown Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546671] systemd[1]: Created slice System Slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.546678] systemd[1]: Starting System Slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.547016] systemd[1]: Starting Setup Virtual Console...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.547340] systemd[1]: Mounting Huge Pages File System...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.547465] systemd[1]: Created slice system-getty.slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.547470] systemd[1]: Starting system-getty.slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.547795] systemd[1]: Starting Increase datagram queue length...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.549108] systemd[1]: Starting Load Kernel Modules...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.549543] systemd[1]: Started Read required files in advance.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.550038] systemd[1]: Starting Read required files in advance...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.550394] systemd[1]: Starting Create list of required static device nodes for the current kernel...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.550550] systemd[1]: Created slice system-systemd\x2dfsck.slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.550554] systemd[1]: Starting system-systemd\x2dfsck.slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.550829] systemd[1]: Mounting Debug File System...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.550955] systemd[1]: Listening on fsck to fsckd communication Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.550961] systemd[1]: Starting fsck to fsckd communication Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.551071] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.551075] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.551263] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.551267] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553036] systemd[1]: Started Set Up Additional Binary Formats.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553177] systemd[1]: Created slice User and Session Slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553183] systemd[1]: Starting User and Session Slice.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553243] systemd[1]: Reached target Slices.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553248] systemd[1]: Starting Slices.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553404] systemd[1]: Listening on Journal Audit Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553408] systemd[1]: Starting Journal Audit Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553719] systemd[1]: Starting Uncomplicated firewall...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553791] systemd[1]: Reached target Remote File Systems (Pre).
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.553796] systemd[1]: Starting Remote File Systems (Pre).
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.554035] systemd[1]: Starting Nameserver information manager...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.554886] systemd[1]: Mounting POSIX Message Queue File System...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.555040] systemd[1]: Listening on udev Kernel Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.555046] systemd[1]: Starting udev Kernel Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.555140] systemd[1]: Reached target Encrypted Volumes.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.555145] systemd[1]: Starting Encrypted Volumes.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.555246] systemd[1]: Listening on udev Control Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.555251] systemd[1]: Starting udev Control Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.555604] systemd[1]: Starting udev Coldplug all Devices...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.556300] systemd[1]: Mounted Huge Pages File System.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.556453] systemd[1]: Mounted Debug File System.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.556882] systemd[1]: Started Setup Virtual Console.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.557364] systemd[1]: Started Increase datagram queue length.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.557885] systemd[1]: Started Create list of required static device nodes for the current kernel.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.558243] systemd[1]: Started Uncomplicated firewall.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.558761] systemd[1]: Mounted POSIX Message Queue File System.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.560784] lp: driver loaded but no devices found
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.561185] systemd[1]: Started Nameserver information manager.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.565042] ppdev: user-space parallel port driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.569597] systemd[1]: Started Load Kernel Modules.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.570615] systemd[1]: Started udev Coldplug all Devices.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.575398] systemd[1]: Starting udev Wait for Complete Device Initialization...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.575754] systemd[1]: Starting Apply Kernel Variables...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.575822] systemd[1]: Mounted Configuration File System.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.576104] systemd[1]: Mounting FUSE Control File System...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.576438] systemd[1]: Starting Create Static Device Nodes in /dev...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.576548] systemd[1]: Listening on Syslog Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.576561] systemd[1]: Starting Syslog Socket.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.576889] systemd[1]: Starting Journal Service...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.577380] systemd[1]: Mounted FUSE Control File System.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.579294] systemd[1]: Started Apply Kernel Variables.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.586941] systemd[1]: Started Create Static Device Nodes in /dev.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.587672] systemd[1]: Starting udev Kernel Device Manager...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.608344] systemd[1]: Started udev Kernel Device Manager.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.609139] systemd[1]: Starting Show Plymouth Boot Screen...
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.640862] systemd[1]: Started Journal Service.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.650204] Switched to clocksource tsc
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.730239] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.733883] [drm] Initialized drm 1.1.0 20060810
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.744373] AVX2 version of gcm_enc/dec engaged.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.744374] AES CTR mode by8 optimization enabled
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.749880] [drm] Memory usable by graphics device = 4096M
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.749883] checking generic (c0000000 300000) vs hw (c0000000 10000000)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.749884] fb: switching to inteldrmfb from EFI VGA
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.749904] Console: switching to colour dummy device 80x25
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.749938] [drm] Replacing VGA console driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.755723] input: Logitech K750 as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.2/0003:046D:C52B.0003/0003:046D:4002.0004/input/input6
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.756322] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.756323] [drm] Driver supports precise vblank timestamp query.
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.756356] logitech-hidpp-device 0003:046D:4002.0004: input,hidraw1: USB HID v1.11 Keyboard [Logitech K750] on usb-0000:00:14.0-10:1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.759635] input: Logitech M705 as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.2/0003:046D:C52B.0003/0003:046D:101B.0005/input/input7
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.759703] logitech-hidpp-device 0003:046D:101B.0005: input,hidraw2: USB HID v1.11 Mouse [Logitech M705] on usb-0000:00:14.0-10:2
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.764166] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.778897] asus_wmi: ASUS WMI generic driver loaded
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.796138] asus_wmi: Initialization: 0x0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.796147] asus_wmi: BIOS WMI version: 0.9
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.796162] asus_wmi: SFUN value: 0x0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.796279] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input8
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.796620] asus_wmi: Disabling ACPI video driver
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.818118] [drm] failed to retrieve link info, disabling eDP
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.821177] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.821224] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.821264] [drm] Initialized i915_bpo 1.6.0 20150522 for 0000:00:02.0 on minor 0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.829929] Adding 15624188k swap on /dev/sda4.  Priority:-1 extents:1 across:15624188k SSFS
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.902677] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.903465] fbcon: inteldrmfb (fb0) is primary device
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.903541] Console: switching to colour frame buffer device 320x100
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.903566] i915_bpo 0000:00:02.0: fb0: inteldrmfb frame buffer device
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.903567] i915_bpo 0000:00:02.0: registered panic notifier
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918603] sound hdaudioC0D0: autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918605] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918607] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918608] sound hdaudioC0D0:    mono: mono_out=0x0
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918609] sound hdaudioC0D0:    dig-out=0x11/0x1e
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918610] sound hdaudioC0D0:    inputs:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918611] sound hdaudioC0D0:      Front Mic=0x19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918612] sound hdaudioC0D0:      Rear Mic=0x18
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.918613] sound hdaudioC0D0:      Line=0x1a
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.931267] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933362] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933392] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933420] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933445] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933471] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933495] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933519] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933543] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933567] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.933590] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.934889] systemd-journald[321]: Received request to flush runtime journal from PID 1
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    2.967509] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.017880] audit: type=1400 audit(1444681015.730:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.017885] audit: type=1400 audit(1444681015.730:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.017888] audit: type=1400 audit(1444681015.730:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.017891] audit: type=1400 audit(1444681015.730:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.018350] audit: type=1400 audit(1444681015.730:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="system_tor" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.019918] audit: type=1400 audit(1444681015.734:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.019921] audit: type=1400 audit(1444681015.734:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.019923] audit: type=1400 audit(1444681015.734:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="pxgsettings" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.019925] audit: type=1400 audit(1444681015.734:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=568 comm="apparmor_parser"
Oct 12 13:16:55 erniee-kubuntu-dev thermald[692]: Running on a vanilla kernel
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.155635] cfg80211: Calling CRDA to update world regulatory domain
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166902] cfg80211: World regulatory domain updated:
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166903] cfg80211:  DFS Master region: unset
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166904] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166905] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166906] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166907] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166909] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166910] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166911] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166912] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Oct 12 13:16:55 erniee-kubuntu-dev kernel: [    3.166913] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Oct 12 13:16:55 erniee-kubuntu-dev NetworkManager[696]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 12 13:16:56 erniee-kubuntu-dev kernel: [    3.828429] [drm] RC6 on
Oct 12 13:16:59 erniee-kubuntu-dev kernel: [    6.331038] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
++SNIP++
++COMMENT++ This is the failure point
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692620] ata5.00: exception Emask 0x52 SAct 0x6000000 SErr 0xffffffff action 0xe frozen
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692623] ata5: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10B8B Dispar BadCRC Handshk LinkSeq TrStaTrns UnrecFIS DevExch }
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692624] ata5.00: failed command: READ FPDMA QUEUED
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692626] ata5.00: cmd 60/08:c8:08:08:40/00:00:00:00:00/40 tag 25 ncq 4096 in
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692626]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x56 (ATA bus error)
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692627] ata5.00: status: { DRDY }
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692628] ata5.00: failed command: WRITE FPDMA QUEUED
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692630] ata5.00: cmd 61/08:d0:00:08:c4/00:00:1d:00:00/40 tag 26 ncq 4096 out
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692630]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x56 (ATA bus error)
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692631] ata5.00: status: { DRDY }
Oct 12 13:29:29 erniee-kubuntu-dev kernel: [  758.692633] ata5: hard resetting link
Oct 12 13:29:31 erniee-kubuntu-dev kernel: [  760.227798] ata5: failed to resume link (SControl FFFFFFFF)
Oct 12 13:29:31 erniee-kubuntu-dev kernel: [  760.227810] ata5: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
Oct 12 13:29:36 erniee-kubuntu-dev kernel: [  765.238203] ata5: hard resetting link
Oct 12 13:29:37 erniee-kubuntu-dev kernel: [  766.773392] ata5: failed to resume link (SControl FFFFFFFF)
Oct 12 13:29:37 erniee-kubuntu-dev kernel: [  766.773404] ata5: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
Oct 12 13:29:37 erniee-kubuntu-dev kernel: [  766.773411] ata5: limiting SATA link speed to <unknown>
Oct 12 13:29:42 erniee-kubuntu-dev kernel: [  771.783822] ata5: hard resetting link
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.319001] ata5: failed to resume link (SControl FFFFFFFF)
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.319013] ata5: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.319019] ata5.00: disabled
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.319023] ata5.00: device reported invalid CHS sector 0
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.319024] ata5.00: device reported invalid CHS sector 0
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824062] sd 4:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824064] sd 4:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824065] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824066] sd 4:0:0:0: [sdb] CDB: 
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824067] Read(10): 28 00 00 40 08 08 00 00 08 00
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824070] blk_update_request: I/O error, dev sdb, sector 4196360
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824075] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 17, block_bitmap = 524289
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824078] sd 4:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824079] sd 4:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824079] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824080] sd 4:0:0:0: [sdb] CDB: 
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824080] Write(10): 2a 00 1d c4 08 00 00 00 08 00
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824083] blk_update_request: I/O error, dev sdb, sector 499386368
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824085] Buffer I/O error on dev sdb1, logical block 62423040, lost sync page write
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824085] sd 4:0:0:0: rejecting I/O to offline device
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824088] ata5: EH complete
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824090] JBD2: Error -5 detected when updating journal superblock for sdb1-8.
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824091] ata5.00: detaching (SCSI 4:0:0:0)
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824092] Aborting journal on device sdb1-8.
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824095] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 18, block_bitmap = 524290
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824096] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824097] JBD2: Error -5 detected when updating journal superblock for sdb1-8.
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824101] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 19, block_bitmap = 524291
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824102] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824105] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 20, block_bitmap = 524292
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824106] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824111] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 21, block_bitmap = 524293
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824112] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824116] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 22, block_bitmap = 524294
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824116] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824120] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 23, block_bitmap = 524295
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824120] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824124] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 24, block_bitmap = 524296
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824124] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824128] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 25, block_bitmap = 524297
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824129] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824132] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:494: comm kworker/u16:0: Cannot read block bitmap - block_group = 26, block_bitmap = 524298
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824133] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.824136] EXT4-fs (sdb1): previous I/O error to superblock detected
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.828206] EXT4-fs error (device sdb1): ext4_journal_check_start:56: Detected aborted journal
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  773.828554] blk_update_request: I/O error, dev sdb, sector 0
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  774.124357] sd 4:0:0:0: [sdb] Synchronizing SCSI cache
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  774.124372] sd 4:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  774.124373] sd 4:0:0:0: [sdb] Stopping disk
Oct 12 13:29:44 erniee-kubuntu-dev kernel: [  774.124375] sd 4:0:0:0: [sdb] Start/Stop Unit failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK

```[FONT=monospace]

[COLOR=#ff0000]This is (what I believe is an unrelated crash as it happens WITHOUT the XF941[/COLOR] (added for info, but I am going to ask what this MIGHT be on another thread):
[/FONT]```
[FONT=monospace][COLOR=#000000]Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311639] ------------[ cut here ]------------[/COLOR]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311668] WARNING: CPU: 6 PID: 845 at /build/linux-qOmAV7/linux-3.19.0/ubuntu/i915/intel_pm.c:3406 skl_update_other_pipe_wm+0x200/0x210 i915_bpo]()
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311670] WARN_ON(!wm_changed)
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311671] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 
snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic eeepc_wmi asus_wmi joydev sparse_keymap snd_hda_i
ntel snd_hda_controller snd_hda_codec snd_hwdep x86_pkg_temp_thermal coretemp snd_pcm kvm_intel snd_seq_midi snd
_seq_midi_event kvm snd_rawmidi snd_seq hid_logitech_hidpp crct10dif_pclmul crc32_pclmul snd_seq_device ghash_cl
mulni_intel snd_timer aesni_intel i915_bpo aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd intel_ips 
serio_raw drm_kms_helper drm soundcore 8250_fintek shpchp i2c_algo_bit i2c_hid acpi_pad mac_hid parport_pc ppdev
 lp parport autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e ptp psmouse pps_core ahci libahci wmi video
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311731] CPU: 6 PID: 845 Comm: Xorg Tainted: G        W      3.
19.0-30-generic #34-Ubuntu
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311733] Hardware name: System manufacturer System Product Name
/Z170-AR, BIOS 0502 07/14/2015
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311735]  ffffffffc0570060 ffff880843cbf568 ffffffff817c4d5f 00
00000000000007
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311738]  ffff880843cbf5b8 ffff880843cbf5a8 ffffffff81076a8a ff
ff880843cbf660
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311741]  ffff880846587000 ffff880843cbf704 ffff880843cbf650 ff
ff880846583000
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311744] Call Trace:
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311753]  [<ffffffff817c4d5f>] dump_stack+0x45/0x57
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311757]  [<ffffffff81076a8a>] warn_slowpath_common+0x8a/0xc0
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311760]  [<ffffffff81076b06>] warn_slowpath_fmt+0x46/0x50
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311774]  [<ffffffffc04ad8c0>] skl_update_other_pipe_wm+0x200/0
x210 [i915_bpo]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311787]  [<ffffffffc04ada9e>] skl_update_wm+0x1ce/0x740 [i915_
bpo]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311809]  [<ffffffffc04f7d9f>] ? gen9_read32+0xff/0x300 [i915_b
po]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311823]  [<ffffffffc04aea6e>] intel_update_watermarks+0x1e/0x3
0 [i915_bpo]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311846]  [<ffffffffc0515fe0>] intel_finish_crtc_commit+0x180/0
x1a0 [i915_bpo]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311856]  [<ffffffffc0415bb1>] drm_atomic_helper_commit_planes_
on_crtc+0x151/0x270 [drm_kms_helper]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311881]  [<ffffffffc052ff80>] intel_atomic_commit+0x70/0x110 [
i915_bpo]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311901]  [<ffffffffc03b5377>] drm_atomic_commit+0x37/0x60 [drm
]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311910]  [<ffffffffc04143e6>] drm_atomic_helper_disable_plane+
0xf6/0x150 [drm_kms_helper]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311914]  [<ffffffff8120a2f0>] ? poll_select_copy_remaining+0x1
30/0x130
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311929]  [<ffffffffc03a4f70>] __setplane_internal+0x1f0/0x2d0 
[drm]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311942]  [<ffffffffc03a516e>] drm_mode_cursor_universal+0x11e/
0x210 [drm]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311948]  [<ffffffff817c9783>] ? __ww_mutex_lock+0x63/0xb0
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311960]  [<ffffffffc03a52de>] drm_mode_cursor_common+0x7e/0x1a
0 [drm]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311964]  [<ffffffff81082b51>] ? __dequeue_signal+0x131/0x210
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311967]  [<ffffffff8120a2f0>] ? poll_select_copy_remaining+0x1
30/0x130
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311982]  [<ffffffffc03a9561>] drm_mode_cursor_ioctl+0x41/0x50 
[drm]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311992]  [<ffffffffc0399a6f>] drm_ioctl+0x1df/0x680 [drm]
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.311997]  [<ffffffff812096a0>] do_vfs_ioctl+0x2e0/0x4e0
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.312000]  [<ffffffff81083792>] ? __set_task_blocked+0x32/0x80
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.312004]  [<ffffffff811f5908>] ? __vfs_read+0x18/0x50
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.312007]  [<ffffffff81086346>] ? __set_current_blocked+0x36/0x9
0
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.312010]  [<ffffffff81209921>] SyS_ioctl+0x81/0xa0
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.312013]  [<ffffffff81086586>] ? SyS_rt_sigprocmask+0x86/0xb0
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.312016]  [<ffffffff817cbe8d>] system_call_fastpath+0x16/0x1b
Oct 12 13:47:01 erniee-kubuntu-dev kernel: [ 1812.312018] ---[ end trace 2a0a725b7d59eb15 ]---
[/FONT]
```

---

### Post by oldfred on 2015-10-12
I have an Asus Z97-AR and have not had any issues other than it needs a lot of settings changed in UEFI to make it boot in UEFI mode. And update to UEFI from Asus reset all those settings back to defaults.

Different brands of Z170 board should not have huge differences.
 Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

 MSI Z170A GAMING PRO motherboard
[http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1)

---

### Post by Ernie_Ewert on 2015-10-12
The change has zero impact on the ISSUE OF THE SSD failing when ACPI is enabled in the kernel.

(As a side note, the change has no impact on the other issue with the Intel Video driver.)

---

### Post by oldfred on 2015-10-12
Every instruction I have seen says you must have AHCI on for SSD to use trim.
Not sure then what conflict you have.

But there have been many issues on ACPI and that varies a lot by kernel & hardware.

---

