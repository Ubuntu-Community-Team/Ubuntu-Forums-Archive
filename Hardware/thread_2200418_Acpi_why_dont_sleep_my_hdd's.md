---
title: "Acpi why dont sleep my hdd's"
date: 2014-01-19
forum: Hardware
---

### Post by badmox on 2014-01-19
Hello 

i got in some trouble with acpi and my hdd's, and yes i tried google but there are more the problems out there where acpi is doing more then it should or make it impossible to boot.

In my case it doing not enough. i have a soho Workstation/Server thing for storing and some media serving. (Samba, Rygel ..) and yes it is not a Server by definition no i7 or opteron no raid5 ... (i dont need to serve 50 workstation)

Problem: i cant auto sleep my hdd's (system hdd i dont want to power down / sleep) 

Linux: Xubuntu 13.10 kernel 3.11.10 

Hardware:

MB: Asrock B75 pro3-m 
cpu i3 3220-t
Hdd's : 1 older WD 750gb (system) 1 WD green 2.5tb 2 WD green 3tb 2 WD red 3tb
RAM 16gb adata

hdparm is configured for the hdd's i want to sleep (240 / 20min)

hdparm -I 

```
ATA device, with non-removable media
    Model Number:       WDC WD30EFRX-68AX9N0                    
    Serial Number:      WD-WCC1T1078837
    Firmware Revision:  80.00A80
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Supported: 9 8 7 6 5 
    Likely used: 9
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors: 5860533168
    Logical  Sector size:                   512 bytes
    Physical Sector size:                  4096 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:     2861588 MBytes
    device size with M = 1000*1000:     3000592 MBytes (3000 GB)
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
            Media Card Pass-Through
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    URG for READ_STREAM[_DMA]_EXT
       *    URG for WRITE_STREAM[_DMA]_EXT
       *    IDLE_IMMEDIATE with UNLOAD
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    Idle-Unload when NCQ is active
       *    NCQ priority information
       *    READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Write Same (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[7]
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
            unknown 206[14] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    416min for SECURITY ERASE UNIT. 416min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50014ee208914f28
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 208914f28
Checksum: correct
```
 
hdparm -B

APM_level    = not supported   #why? acpi ?


acpi -a

No support for device type: power_supply  #:confused: normal ? or not google puts only some laptop related things out 


dmesg | grep acpi

```
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.116644] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.155297] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.155553] acpi PNP0A08:00: ACPI _OSC control (0x1c) granted
[    0.174678] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.176068] Found 1 acpi root devices
[    0.188436] Switched to clocksource acpi_pm
[    0.481080] ACPI: Requesting acpi_cpufreq
[   34.956373] acpi device:42: registered as cooling_device4
```

dmesg | grep ACPI

```
[    0.000000] BIOS-e820: [mem 0x00000000ce315000-0x00000000ce594fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ce595000-0x00000000ce599fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ce59a000-0x00000000ce5dcfff] ACPI NVS
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000ce57c078 00074 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000ce5859e0 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000ce57c188 09852 (v02 ALASKA    A M I 00000014 INTL 20051117)
[    0.000000] ACPI: FACS 00000000ce593f80 00040
[    0.000000] ACPI: APIC 00000000ce585ad8 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000ce585b50 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000ce585b90 004A6 (v01 Intel_ AoacTabl 00001000 INTL 20091112)
[    0.000000] ACPI: AAFT 00000000ce586038 000C2 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000ce586100 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000ce586470 008E4 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000ce586d58 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: ASF! 00000000ce5877f0 000A5 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: BGRT 00000000ce587898 0003C (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.007965] ACPI: Core revision 20130517
[    0.014237] ACPI: All ACPI Tables successfully acquired
[    0.115787] PM: Registering ACPI NVS region [mem 0xce315000-0xce594fff] (2621440 bytes)
[    0.115815] PM: Registering ACPI NVS region [mem 0xce59a000-0xce5dcfff] (274432 bytes)
[    0.116641] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.116643] ACPI: bus type PCI registered
[    0.116644] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.123268] ACPI: Added _OSI(Module Device)
[    0.123270] ACPI: Added _OSI(Processor Device)
[    0.123271] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.123272] ACPI: Added _OSI(Processor Aggregator Device)
[    0.124473] ACPI: EC: Look up EC in DSDT
[    0.125890] ACPI: Executed 1 blocks of module-level executable AML code
[    0.132187] ACPI: SSDT 00000000ce2c2018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.132500] ACPI: Dynamic OEM Table Load:
[    0.132502] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.138656] ACPI: SSDT 00000000ce2c3a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.139003] ACPI: Dynamic OEM Table Load:
[    0.139005] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.142476] ACPI: SSDT 00000000ce2c4c18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.142778] ACPI: Dynamic OEM Table Load:
[    0.142780] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.147097] ACPI: Interpreter enabled
[    0.147106] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.147110] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20130517/hwxface-571)
[    0.147118] ACPI: (supports S0 S1 S4 S5)
[    0.147120] ACPI: Using IOAPIC for interrupt routing
[    0.147184] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.147304] ACPI: No dock devices found.
[    0.155029] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.155297] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.155553] acpi PNP0A08:00: ACPI _OSC control (0x1c) granted
[    0.156687] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.157087] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.157314] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.157478] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.157637] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.157846] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.157966] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.175379] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.175443] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.175505] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.175567] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.175628] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.175689] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.175752] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.175816] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.176013] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.176019] ACPI: \_SB_.PCI0: notify handler is installed
[    0.176255] ACPI: bus type ATA registered
[    0.176319] ACPI: bus type USB registered
[    0.176438] PCI: Using ACPI for IRQ routing
[    0.181598] pnp: PnP ACPI init
[    0.181608] ACPI: bus type PNP registered
[    0.181699] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.181725] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.181741] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.181824] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.181847] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.181892] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.181974] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.182284] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.182304] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.182617] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.182798] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.182826] pnp: PnP ACPI: found 11 devices
[    0.182827] ACPI: bus type PNP unregistered
[    0.480967] ACPI: Power Button [PWRB]
[    0.480995] ACPI: Power Button [PWRF]
[    0.481080] ACPI: Requesting acpi_cpufreq
[    0.858458] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.858464] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.858466] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.858611] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.858617] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.858620] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.860037] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.860042] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.860046] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.862868] ata4.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.862873] ata4.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.862876] ata4.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.865396] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.865404] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.865417] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.869150] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.869155] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.869159] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.874760] ata4.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.874763] ata4.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.874764] ata4.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.881507] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.881513] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.881516] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[   34.956667] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   34.957048] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   34.957055] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   34.957060] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPR2 1 (20130517/utaddress-251)
[   34.957064] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[   34.957068] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   34.957070] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPR2 1 (20130517/utaddress-251)
[   34.957073] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[   34.957077] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver


```

google about the warnings:irq conflict "nothing" to worry about (i dont think so but maybe it has nothing to do with the problem )

i hope someone has an idea whats going wrong.

---

