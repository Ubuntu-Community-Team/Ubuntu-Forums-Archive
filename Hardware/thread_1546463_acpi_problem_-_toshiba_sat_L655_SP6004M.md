---
title: "acpi problem - toshiba sat L655 SP6004M"
date: 2010-08-05
forum: Hardware
---

### Post by sigfrido on 2010-08-05
Hello all. I just bought a Toshiba Satellite Laptop L655 SP6004M (i3-core, 3G RAM) and I'm having a hard time trying to get complete acpi support on Lucid.

The thing is battery appears as not present and therefore any battery applets will never work, not showing how much power is left -let alone getting full acpi support when unplugging the AC cable, such as adjusting screen brightness, hard drive energy saving policies, etc.

So far I have tried three strategies posted on this forum related to similar toshiba series (A505 S6005, Pro L650, etc):

[LIST=1]
[*]Patching and recompiling the kernel, and setting acpi=copy_dsts on grub.cfg
[*]Installing a super-recent kernel version (v2.6.35-rc1)
[*]Updating the BIOS
[/LIST]

... none of these have worked.

Any thoughts on this? Is there a log for the acpi errors/events? Where can I find it?

---

### Post by lidex on 2010-08-07
> **sigfrido said:**
> Hello all. I just bought a Toshiba Satellite Laptop L655 SP6004M (i3-core, 3G RAM) and I'm having a hard time trying to get complete acpi support on Lucid.

The thing is battery appears as not present and therefore any battery applets will never work, not showing how much power is left -let alone getting full acpi support when unplugging the AC cable, such as adjusting screen brightness, hard drive energy saving policies, etc.

So far I have tried three strategies posted on this forum related to similar toshiba series (A505 S6005, Pro L650, etc):

[LIST=1]
[*]Patching and recompiling the kernel, and setting acpi=copy_dsts on grub.cfg
[*]Installing a super-recent kernel version (v2.6.35-rc1)
[*]Updating the BIOS
[/LIST]

... none of these have worked.

Any thoughts on this? Is there a log for the acpi errors/events? Where can I find it?

Try dmesg:
```
dmesg | less
```
Or syslog:
```
cat /var/log/syslog
```

---

### Post by dino99 on 2010-08-07
search "tosh" into synaptic and install the specific packages

---

### Post by sigfrido on 2010-08-27
Hello all, still around with the same problem (see below). I tried the suggestions you guys gave to me, but I can't figure out what's going on.

Also, ubuntu released a patched kernel just recently. I upgraded, but still have no recognizable battery.

Could any one point out what kernel/system info I need to display to target the problem? Or maybe suggesting a particular kernel patch? 

This is what i get (i have the battery plugged in):

```

ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000

[    0.541106] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.541108] ACPI: bus type pci registered
[    0.541167] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.541170] PCI: MCFG area at e0000000 reserved in E820
[    0.541171] PCI: Using MMCONFIG for extended config space
[    0.541173] PCI: Using configuration type 1 for base access
[    0.541896] bio: create slab <bio-0> at 0
[    0.543406] ACPI: EC: Look up EC in DSDT
[    0.545132] ACPI: Executed 1 blocks of module-level executable AML code
[    0.549538] ACPI: BIOS _OSI(Linux) query ignored
[    0.551274] ACPI: Interpreter enabled
[    0.551282] ACPI: (supports S0 S3 S4 S5)
[    0.551315] ACPI: Using IOAPIC for interrupt routing
[    0.561032] ACPI: EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.561787] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.562738] _OSC invalid UUID
[    0.562741] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.562816] pci 0000:00:02.0: reg 10 64bit mmio: [0xd0000000-0xd03fffff]
[    0.562822] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.562826] pci 0000:00:02.0: reg 20 io port: [0x5050-0x5057]
[    0.562919] pci 0000:00:16.0: reg 10 64bit mmio: [0xd6406100-0xd640610f]
[    0.562976] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.562981] pci 0000:00:16.0: PME# disabled
[    0.563053] pci 0000:00:1a.0: reg 10 32bit mmio: [0xd6405c00-0xd6405fff]
[    0.563120] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.563125] pci 0000:00:1a.0: PME# disabled
[    0.563179] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd6400000-0xd6403fff]
[    0.563238] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.563243] pci 0000:00:1b.0: PME# disabled
[    0.563332] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.563337] pci 0000:00:1c.0: PME# disabled
[    0.563431] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.563436] pci 0000:00:1c.4: PME# disabled
[    0.563527] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.563531] pci 0000:00:1c.5: PME# disabled
[    0.563598] pci 0000:00:1d.0: reg 10 32bit mmio: [0xd6405800-0xd6405bff]
[    0.563664] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.563669] pci 0000:00:1d.0: PME# disabled
[    0.563894] pci 0000:00:1f.2: reg 10 io port: [0x5048-0x504f]
[    0.563902] pci 0000:00:1f.2: reg 14 io port: [0x505c-0x505f]
[    0.563910] pci 0000:00:1f.2: reg 18 io port: [0x5040-0x5047]
[    0.563917] pci 0000:00:1f.2: reg 1c io port: [0x5058-0x505b]
[    0.563924] pci 0000:00:1f.2: reg 20 io port: [0x5020-0x503f]
[    0.563932] pci 0000:00:1f.2: reg 24 32bit mmio: [0xd6405000-0xd64057ff]
[    0.563978] pci 0000:00:1f.2: PME# supported from D3hot
[    0.563982] pci 0000:00:1f.2: PME# disabled
[    0.564024] pci 0000:00:1f.3: reg 10 64bit mmio: [0xd6406000-0xd64060ff]
[    0.564042] pci 0000:00:1f.3: reg 20 io port: [0x5000-0x501f]
[    0.564113] pci 0000:00:1f.6: reg 10 64bit mmio: [0xd6404000-0xd6404fff]
[    0.564231] pci 0000:00:1c.0: bridge io port: [0x4000-0x4fff]
[    0.564236] pci 0000:00:1c.0: bridge 32bit mmio: [0xd5400000-0xd63fffff]
[    0.564245] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0400000-0xd13fffff]
[    0.565604] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.565670] pci 0000:02:00.0: reg 14 32bit mmio: [0xd4400000-0xd4403fff]
[    0.568441] pci 0000:02:00.0: supports D1 D2
[    0.568444] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.568565] pci 0000:02:00.0: PME# disabled
[    0.569447] pci 0000:00:1c.4: bridge io port: [0x3000-0x3fff]
[    0.569452] pci 0000:00:1c.4: bridge 32bit mmio: [0xd4400000-0xd53fffff]
[    0.569460] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xd1400000-0xd23fffff]
[    0.569527] pci 0000:03:00.0: reg 10 64bit mmio: [0xd3400000-0xd343ffff]
[    0.569537] pci 0000:03:00.0: reg 18 io port: [0x2000-0x207f]
[    0.569612] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.569618] pci 0000:03:00.0: PME# disabled
[    0.569689] pci 0000:00:1c.5: bridge io port: [0x2000-0x2fff]
[    0.569693] pci 0000:00:1c.5: bridge 32bit mmio: [0xd3400000-0xd43fffff]
[    0.569702] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xd2400000-0xd33fffff]
[    0.569756] pci 0000:00:1e.0: transparent bridge
[    0.569792] pci_bus 0000:00: on NUMA node 0
[    0.569802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.570032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.570226] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.570349] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.570640] _OSC invalid UUID
[    0.588383] ACPI: PCI Root Bridge [CPBG] (0000:ff)
[    0.588523] pci_bus 0000:ff: on NUMA node 0
[    0.588821] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.588968] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.589113] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.589258] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.589402] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.589547] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.589691] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.589836] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.600909] pnp: PnP ACPI init
[    0.600925] ACPI: bus type pnp registered
[    0.604000] pnp: PnP ACPI: found 11 devices
[    0.604002] ACPI: ACPI bus type pnp unregistered
[    0.604005] PnPBIOS: Disabled by ACPI PNP
[    0.683423] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.683555] ACPI: AC Adapter [ACAD] (on-line)
[    0.683613] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.683616] ACPI: Power Button [PWRB]
[    0.683650] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.683739] ACPI: Lid Switch [LID]
[    0.683772] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.683774] ACPI: Power Button [PWRF]
[    0.685198] ACPI: SSDT b7691918 00402 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.685978] ACPI: SSDT b768f018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.686617] Monitor-Mwait will be used to enter C-1 state
[    0.686642] Monitor-Mwait will be used to enter C-3 state
[    0.686679] processor LNXCPU:00: registered as cooling_device0
[    0.687261] ACPI: SSDT b7690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.687855] ACPI: SSDT b768ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.688590] processor LNXCPU:01: registered as cooling_device1
[    0.689560] processor LNXCPU:02: registered as cooling_device2
[    0.694491] processor LNXCPU:03: registered as cooling_device3
[    0.698367] ACPI: Battery Slot [BAT1] (battery absent)

```

Cheers!

---

### Post by RafaelBarreto on 2010-08-31
Same problem here, but in a L655-S5065.
I installed all toshiba related packs, and upgraded the bios and the kernel.

**ACPI: Battery Slot [BAT1] (battery absent)**

Does anyone have a tip?

```

$ uname -a
Linux zennla 2.6.35-020635-generic #020635 SMP Mon Aug 2 09:08:21 UTC 2010 x86_64 GNU/Linux

``````
$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

``````

$ dmesg | grep -i acpi
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-020635-generic root=UUID=b42e460d-eb6c-46bc-b8f3-efe8f4aaff18 ro acpi=copy_dsdt crashkernel=384M-2G:64M,2G-:128M quiet splash
[    0.000000]  BIOS-e820: 00000000bb6bf000 - 00000000bb7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb7bf000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  modified: 00000000bb6bf000 - 00000000bb7bf000 (ACPI NVS)
[    0.000000]  modified: 00000000bb7bf000 - 00000000bb7ff000 (ACPI data)
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT 00000000bb7fe120 00074 (v01 TOSQCI TOSQCI00 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bb7fc000 000F4 (v04 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bb7ed000 0BFF8 (v02 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bb76e000 00040
[    0.000000] ACPI: ASF! 00000000bb7fd000 000A5 (v32 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 00000000bb7fb000 00038 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bb7fa000 0008C (v02 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bb7f9000 0003C (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bb7ec000 00176 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 00000000bb7e8000 00028 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 00000000bb7e5000 00034 (v04 INTEL  Calpella 00000001 MSFT 01000013)
[    0.000000] ACPI: WDAT 00000000bb7e4000 00224 (v01 INTEL  Calpella 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bb7e3000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-020635-generic root=UUID=b42e460d-eb6c-46bc-b8f3-efe8f4aaff18 ro acpi=copy_dsdt crashkernel=384M-2G:64M,2G-:128M quiet splash
[    0.000000]   #6 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.004482] ACPI: Core revision 20100428
[    0.015203] ACPI: Forced DSDT copy: length 0x0BFF8 copied locally, original unmapped
[    0.815234] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.815236] ACPI: bus type pci registered
[    0.841576] ACPI: EC: Look up EC in DSDT
[    0.844235] ACPI: Executed 1 blocks of module-level executable AML code
[    0.848320] ACPI: BIOS _OSI(Linux) query ignored
[    0.850838] ACPI: SSDT 00000000bb691918 00402 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.851531] ACPI: Dynamic OEM Table Load:
[    0.851534] ACPI: SSDT (null) 00402 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.852016] ACPI: SSDT 00000000bb68f018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.852643] ACPI: Dynamic OEM Table Load:
[    0.852645] ACPI: SSDT (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.853351] ACPI: SSDT 00000000bb690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.854047] ACPI: Dynamic OEM Table Load:
[    0.854050] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.854310] ACPI: SSDT 00000000bb68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.855013] ACPI: Dynamic OEM Table Load:
[    0.855015] ACPI: SSDT (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.856579] ACPI: Interpreter enabled
[    0.856582] ACPI: (supports S0 S3 S4 S5)
[    0.856619] ACPI: Using IOAPIC for interrupt routing
[    0.867759] ACPI: EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.868447] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.868451] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.869127] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.875908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.876148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.876359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.876493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.896429] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.896954] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.897096] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.897234] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.897373] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.897512] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.897654] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.897793] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.897932] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.898563] ACPI: WMI: Mapper loaded
[    0.898565] PCI: Using ACPI for IRQ routing
[    0.908332] pnp: PnP ACPI init
[    0.908353] ACPI: bus type pnp registered
[    0.911216] pnp: PnP ACPI: found 11 devices
[    0.911218] ACPI: ACPI bus type pnp unregistered
[    1.169758] ACPI: AC Adapter [ACAD] (off-line)
[    1.169823] ACPI: Power Button [PWRB]
[    1.169951] ACPI: Lid Switch [LID]
[    1.169986] ACPI: Power Button [PWRF]
[    1.170905] ACPI: acpi_idle registered with cpuidle
[    1.176747] ACPI: Battery Slot [BAT1] (battery absent)
[    7.864557] acpi device:01: registered as cooling_device4
[    7.865460] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

``````

$ aptitude search tosh
p   libqyotoshared1                                                             - shared library for Qt 4 CLI bindings                                                  
v   toshiba-fan                                                                 -                                                                                       
v   toshiba-hotkey                                                              -                                                                                       
i   toshset                                                                     - Access much of the Toshiba laptop hardware interface                                  
i   toshutils                                                                   - Toshiba laptop utilities                               

```

---

### Post by ktemkin on 2010-08-31
The following steps should solve your problem (if my gut feeling is right), which is with boot-time DSDT corruption.

1) [Install the Maverick-to-lucid kernel backport.]("http://www.ubuntuupdates.org/packages/show/203545")
2) Add the following kernel flag to your GRUB configuration:

```
acpi=copy-dsdt
```

Sorry for the lack of detail- I'm at work and thus don't have access to linux configuration files.

---

### Post by RafaelBarreto on 2010-08-31
ktemkin, thank you in advance for replying to this issue.

I followed these steps:
1) First I installed the kernel-ppa ([http://www.ubuntuupdates.org/ppa/kernel-ppa?dist=lucid](http://www.ubuntuupdates.org/ppa/kernel-ppa?dist=lucid))
```
sudo add-apt-repository ppa:kernel-ppa/ppa 
sudo aptitude update
```2)Then installed the package: linux-image-generic-lts-backport-maverick
```
sudo aptitude install linux-image-generic-lts-backport-maverick
```I checked /boot/grub/grub.cfg, and found that acpi=copy_dsdt was already there:
```
$ grep acpi /boot/grub/grub.cfg
        linux   /boot/vmlinuz-2.6.35-020635-generic root=UUID=b42e460d-eb6c-46bc-b8f3-efe8f4aaff18 ro acpi=copy_dsdt  crashkernel=384M-2G:64M,2G-:128M quiet splash
        linux   /boot/vmlinuz-2.6.35-020635-generic root=UUID=b42e460d-eb6c-46bc-b8f3-efe8f4aaff18 ro single acpi=copy_dsdt
        linux   /boot/vmlinuz-2.6.35-19-generic root=UUID=b42e460d-eb6c-46bc-b8f3-efe8f4aaff18 ro acpi=copy_dsdt  crashkernel=384M-2G:64M,2G-:128M quiet splash
        linux   /boot/vmlinuz-2.6.35-19-generic root=UUID=b42e460d-eb6c-46bc-b8f3-efe8f4aaff18 ro single acpi=copy_dsdt
```Then I rebooted my laptop with the new kernel:

```
$ uname -a
Linux zennla 2.6.35-19-generic #25~lucid1-Ubuntu SMP Wed Aug 25 03:50:05 UTC 2010 x86_64 GNU/Linux
```And the battery continues to be "absent".

```
$ dmesg | grep battery
[    0.997196] ACPI: Battery Slot [BAT1] (battery absent)
```If you have any other idea, I will highly appreciate.
This my "first second" of dmesg:
```

$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-19-generic (buildd@berkelium) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #25~lucid1-Ubuntu SMP Wed Aug 25 03:50:05 UTC 2010 (Ubuntu 2.6.35-19.25~lucid1-generic 2.6.35.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-19-generic root=UUID=b42e460d-eb6c-46bc-b8f3-efe8f4aaff18 ro acpi=copy_dsdt crashkernel=384M-2G:64M,2G-:128M quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bb63f000 (usable)
[    0.000000]  BIOS-e820: 00000000bb63f000 - 00000000bb6bf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb6bf000 - 00000000bb7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb7bf000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bb7ff000 - 00000000bb800000 (usable)
[    0.000000]  BIOS-e820: 00000000bb800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
[    0.000000] DMI 2.6 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE80000 mask FFFF80000 write-protect
[    0.000000]   2 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   3 base 080000000 mask FC0000000 write-back
[    0.000000]   4 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   5 base 0BB800000 mask FFF800000 uncachable
[    0.000000]   6 base 100000000 mask FC0000000 write-back
[    0.000000]   7 base 138000000 mask FF8000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbb800 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d000 (usable)
[    0.000000]  modified: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bb63f000 (usable)
[    0.000000]  modified: 00000000bb63f000 - 00000000bb6bf000 (reserved)
[    0.000000]  modified: 00000000bb6bf000 - 00000000bb7bf000 (ACPI NVS)
[    0.000000]  modified: 00000000bb7bf000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  modified: 00000000bb7ff000 - 00000000bb800000 (usable)
[    0.000000]  modified: 00000000bb800000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe80000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bb800000
[    0.000000]  0000000000 - 00bb800000 page 2M
[    0.000000] kernel direct mapping tables up to bb800000 @ 16000-1a000
[    0.000000] init_memory_mapping: 0000000100000000-0000000138000000
[    0.000000]  0100000000 - 0138000000 page 2M
[    0.000000] kernel direct mapping tables up to 138000000 @ 18000-1e000
[    0.000000] RAMDISK: 37713000 - 37ff0000
[    0.000000] Reserving 128MB of memory at 32MB for crashkernel (System RAM: 4992MB)
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT 00000000bb7fe120 00074 (v01 TOSQCI TOSQCI00 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bb7fc000 000F4 (v04 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bb7ed000 0BFF8 (v02 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bb76e000 00040
[    0.000000] ACPI: ASF! 00000000bb7fd000 000A5 (v32 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 00000000bb7fb000 00038 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bb7fa000 0008C (v02 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bb7f9000 0003C (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bb7ec000 00176 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 00000000bb7e8000 00028 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 00000000bb7e5000 00034 (v04 INTEL  Calpella 00000001 MSFT 01000013)
[    0.000000] ACPI: WDAT 00000000bb7e4000 00224 (v01 INTEL  Calpella 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bb7e3000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000138000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000138000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880100200000-ffff8801039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bb63f
[    0.000000]     0: 0x000bb7ff -> 0x000bb800
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 996813
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3925 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 749176 pages, LIFO batch:31
[    0.000000]   Normal zone: 3136 pages used for memmap
[    0.000000]   Normal zone: 226240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [19000 - 197ff]
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bb63f000 - 00000000bb6bf000
[    0.000000] PM: Registered nosave memory: 00000000bb6bf000 - 00000000bb7bf000
[    0.000000] PM: Registered nosave memory: 00000000bb7bf000 - 00000000bb7ff000
[    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1b000
[    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe80000
[    0.000000] PM: Registered nosave memory: 00000000ffe80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91456 r8192 d23232 u262144
[    0.000000] early_res array is doubled to 128 at [19800 - 1a7ff]
[    0.000000] pcpu-alloc: s91456 r8192 d23232 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 979341
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-19-generic root=UUID=b42e460d-eb6c-46bc-b8f3-efe8f4aaff18 ro acpi=copy_dsdt crashkernel=384M-2G:64M,2G-:128M quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (66 early reservations)
[    0.000000]   #1 [0001000000 - 0001d16e94]   TEXT DATA BSS
[    0.000000]   #2 [0037713000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [000009d000 - 0000100000]   BIOS reserved
[    0.000000]   #4 [0001d17000 - 0001d1727a]             BRK
[    0.000000]   #5 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #6 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #7 [0000016000 - 0000018000]         PGTABLE
[    0.000000]   #8 [0000018000 - 0000019000]         PGTABLE
[    0.000000]   #9 [0002000000 - 000a000000]    CRASH KERNEL
[    0.000000]   #10 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #11 [0001d17280 - 0001d18280]         BOOTMEM
[    0.000000]   #12 [0001d18280 - 0001d18568]         BOOTMEM
[    0.000000]   #13 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #14 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #15 [0100200000 - 0103a00000]        MEMMAP 0
[    0.000000]   #16 [0001d18580 - 0001d18700]         BOOTMEM
[    0.000000]   #17 [0001d18700 - 0001d30700]         BOOTMEM
[    0.000000]   #18 [0001d30700 - 0001d36700]         BOOTMEM
[    0.000000]   #19 [0001d37000 - 0001d38000]         BOOTMEM
[    0.000000]   #20 [0001d16ec0 - 0001d16f01]         BOOTMEM
[    0.000000]   #21 [0001d16f40 - 0001d16f83]         BOOTMEM
[    0.000000]   #22 [0001d36700 - 0001d36b28]         BOOTMEM
[    0.000000]   #23 [0001d36b40 - 0001d36ba8]         BOOTMEM
[    0.000000]   #24 [0001d36bc0 - 0001d36c28]         BOOTMEM
[    0.000000]   #25 [0001d36c40 - 0001d36ca8]         BOOTMEM
[    0.000000]   #26 [0001d36cc0 - 0001d36d28]         BOOTMEM
[    0.000000]   #27 [0001d36d40 - 0001d36da8]         BOOTMEM
[    0.000000]   #28 [0001d36dc0 - 0001d36e28]         BOOTMEM
[    0.000000]   #29 [0001d36e40 - 0001d36ea8]         BOOTMEM
[    0.000000]   #30 [0001d36ec0 - 0001d36f28]         BOOTMEM
[    0.000000]   #31 [0001d36f40 - 0001d36fa8]         BOOTMEM
[    0.000000]   #32 [0001d38000 - 0001d38068]         BOOTMEM
[    0.000000]   #33 [0001d38080 - 0001d380e8]         BOOTMEM
[    0.000000]   #34 [0001d38100 - 0001d38168]         BOOTMEM
[    0.000000]   #35 [0001d38180 - 0001d381e8]         BOOTMEM
[    0.000000]   #36 [0001d38200 - 0001d38268]         BOOTMEM
[    0.000000]   #37 [0001d38280 - 0001d382e8]         BOOTMEM
[    0.000000]   #38 [0001d38300 - 0001d38368]         BOOTMEM
[    0.000000]   #39 [0001d38380 - 0001d383e8]         BOOTMEM
[    0.000000]   #40 [0001d38400 - 0001d38468]         BOOTMEM
[    0.000000]   #41 [0001d16fc0 - 0001d16fe0]         BOOTMEM
[    0.000000]   #42 [0001d36fc0 - 0001d36fe0]         BOOTMEM
[    0.000000]   #43 [0001d38480 - 0001d384a0]         BOOTMEM
[    0.000000]   #44 [0001d384c0 - 0001d3855a]         BOOTMEM
[    0.000000]   #45 [0001d38580 - 0001d3861a]         BOOTMEM
[    0.000000]   #46 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #47 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #48 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #49 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #50 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #51 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #52 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #53 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #54 [0001d3a640 - 0001d3a648]         BOOTMEM
[    0.000000]   #55 [0001d3a680 - 0001d3a688]         BOOTMEM
[    0.000000]   #56 [0001d3a6c0 - 0001d3a6e0]         BOOTMEM
[    0.000000]   #57 [0001d3a700 - 0001d3a740]         BOOTMEM
[    0.000000]   #58 [0001d3a740 - 0001d3a860]         BOOTMEM
[    0.000000]   #59 [0001d3a880 - 0001d3a8c8]         BOOTMEM
[    0.000000]   #60 [0001d3a900 - 0001d3a948]         BOOTMEM
[    0.000000]   #61 [0001d3a980 - 0001d42980]         BOOTMEM
[    0.000000]   #62 [000a000000 - 000e000000]         BOOTMEM
[    0.000000]   #63 [0001d42980 - 0001d62980]         BOOTMEM
[    0.000000]   #64 [0001d62980 - 0001da2980]         BOOTMEM
[    0.000000]   #65 [000001a800 - 0000022800]         BOOTMEM
[    0.000000] Memory: 3709204k/5111808k available (5702k kernel code, 1124556k absent, 278048k reserved, 5387k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:744
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 40632320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2261.448 MHz processor.
[    0.000009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4522.89 BogoMIPS (lpj=22614480)
[    0.000013] pid_max: default: 32768 minimum: 301
[    0.000034] Security Framework initialized
[    0.000051] AppArmor: AppArmor initialized
[    0.000052] Yama: becoming mindful.
[    0.000469] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001518] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001920] Mount-cache hash table entries: 256
[    0.002033] Initializing cgroup subsys ns
[    0.002037] Initializing cgroup subsys cpuacct
[    0.002041] Initializing cgroup subsys memory
[    0.002048] Initializing cgroup subsys devices
[    0.002050] Initializing cgroup subsys freezer
[    0.002053] Initializing cgroup subsys net_cls
[    0.002074] CPU: Physical Processor ID: 0
[    0.002076] CPU: Processor Core ID: 0
[    0.002082] mce: CPU supports 9 MCE banks
[    0.002091] CPU0: Thermal monitoring handled by SMI
[    0.002099] using mwait in idle threads.
[    0.002101] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.002108] ... version:                3
[    0.002109] ... bit width:              48
[    0.002110] ... generic registers:      4
[    0.002111] ... value mask:             0000ffffffffffff
[    0.002113] ... max period:             000000007fffffff
[    0.002114] ... fixed-purpose events:   3
[    0.002116] ... event mask:             000000070000000f
[    0.004324] ACPI: Core revision 20100428
[    0.015042] ACPI: Forced DSDT copy: length 0x0BFF8 copied locally, original unmapped
[    0.047056] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.047061] ftrace: allocating 22654 entries in 89 pages
[    0.054858] Setting APIC routing to flat
[    0.055269] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.155099] CPU0: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz stepping 02
[    0.273017] Booting Node   0, Processors  #1
[    0.432602] CPU1: Thermal monitoring handled by SMI
[    0.452757]  #2
[    0.612242] CPU2: Thermal monitoring handled by SMI
[    0.632334]  #3
[    0.791883] CPU3: Thermal monitoring handled by SMI
[    0.811930] Brought up 4 CPUs
[    0.811933] Total of 4 processors activated (18088.84 BogoMIPS).
[    0.813690] devtmpfs: initialized
[    0.814665] regulator: core version 0.5
[    0.814693] Time: 20:32:34  Date: 08/30/10
[    0.814725] NET: Registered protocol family 16
[    0.814819] Trying to unpack rootfs image as initramfs...
[    0.814827] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.814830] ACPI: bus type pci registered
[    0.814906] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.814909] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.851655] PCI: Using configuration type 1 for base access
[    0.852406] bio: create slab <bio-0> at 0
[    0.854863] ACPI: EC: Look up EC in DSDT
[    0.857361] ACPI: Executed 1 blocks of module-level executable AML code
[    0.861241] ACPI: BIOS _OSI(Linux) query ignored
[    0.863743] ACPI: SSDT 00000000bb691918 00402 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.864365] ACPI: Dynamic OEM Table Load:
[    0.864368] ACPI: SSDT (null) 00402 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.864848] ACPI: SSDT 00000000bb68f018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.865447] ACPI: Dynamic OEM Table Load:
[    0.865450] ACPI: SSDT (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.866148] ACPI: SSDT 00000000bb690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.866820] ACPI: Dynamic OEM Table Load:
[    0.866823] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.867081] ACPI: SSDT 00000000bb68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.867711] ACPI: Dynamic OEM Table Load:
[    0.867714] ACPI: SSDT (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.869242] ACPI: Interpreter enabled
[    0.869245] ACPI: (supports S0 S3 S4 S5)
[    0.869282] ACPI: Using IOAPIC for interrupt routing
[    0.880058] ACPI: EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.880734] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.880738] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.881389] \_SB_.PCI0:_OSC invalid UUID
[    0.881391] _OSC request data:1 8 1f
[    0.881395] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.882238] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.882240] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.882243] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.882246] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfeafffff]
[    0.882302] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
[    0.882307] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.882311] pci 0000:00:02.0: reg 20: [io  0x5050-0x5057]
[    0.882394] pci 0000:00:16.0: reg 10: [mem 0xd6406100-0xd640610f 64bit]
[    0.882451] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.882457] pci 0000:00:16.0: PME# disabled
[    0.882517] pci 0000:00:1a.0: reg 10: [mem 0xd6405c00-0xd6405fff]
[    0.882583] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.882588] pci 0000:00:1a.0: PME# disabled
[    0.882634] pci 0000:00:1b.0: reg 10: [mem 0xd6400000-0xd6403fff 64bit]
[    0.882692] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.882697] pci 0000:00:1b.0: PME# disabled
[    0.882790] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.882795] pci 0000:00:1c.0: PME# disabled
[    0.882893] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.882898] pci 0000:00:1c.4: PME# disabled
[    0.882990] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.882995] pci 0000:00:1c.5: PME# disabled
[    0.883050] pci 0000:00:1d.0: reg 10: [mem 0xd6405800-0xd6405bff]
[    0.883115] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.883120] pci 0000:00:1d.0: PME# disabled
[    0.883321] pci 0000:00:1f.2: reg 10: [io  0x5048-0x504f]
[    0.883329] pci 0000:00:1f.2: reg 14: [io  0x505c-0x505f]
[    0.883337] pci 0000:00:1f.2: reg 18: [io  0x5040-0x5047]
[    0.883344] pci 0000:00:1f.2: reg 1c: [io  0x5058-0x505b]
[    0.883352] pci 0000:00:1f.2: reg 20: [io  0x5020-0x503f]
[    0.883359] pci 0000:00:1f.2: reg 24: [mem 0xd6405000-0xd64057ff]
[    0.883404] pci 0000:00:1f.2: PME# supported from D3hot
[    0.883409] pci 0000:00:1f.2: PME# disabled
[    0.883446] pci 0000:00:1f.3: reg 10: [mem 0xd6406000-0xd64060ff 64bit]
[    0.883465] pci 0000:00:1f.3: reg 20: [io  0x5000-0x501f]
[    0.883527] pci 0000:00:1f.6: reg 10: [mem 0xd6404000-0xd6404fff 64bit]
[    0.883648] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.883653] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.883658] pci 0000:00:1c.0:   bridge window [mem 0xd5400000-0xd63fffff]
[    0.883666] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.884794] pci 0000:02:00.0: reg 10: [io  0x3000-0x30ff]
[    0.885109] pci 0000:02:00.0: reg 14: [mem 0xd4400000-0xd4403fff]
[    0.886331] pci 0000:02:00.0: supports D1 D2
[    0.886333] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.886538] pci 0000:02:00.0: PME# disabled
[    0.887029] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
[    0.887033] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.887038] pci 0000:00:1c.4:   bridge window [mem 0xd4400000-0xd53fffff]
[    0.887046] pci 0000:00:1c.4:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.887143] pci 0000:03:00.0: reg 10: [mem 0xd3400000-0xd343ffff 64bit]
[    0.887152] pci 0000:03:00.0: reg 18: [io  0x2000-0x207f]
[    0.887230] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.887236] pci 0000:03:00.0: PME# disabled
[    0.887263] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.887266] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
[    0.887271] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.887276] pci 0000:00:1c.5:   bridge window [mem 0xd3400000-0xd43fffff]
[    0.887283] pci 0000:00:1c.5:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.887358] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.887364] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.887369] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.887376] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.887379] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.887381] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.887383] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.887385] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    0.887421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.887671] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.887884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.888018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.888317] \_SB_.PCI0:_OSC invalid UUID
[    0.888318] _OSC request data:1 19 1f
[    0.907548] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.908090] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.908229] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.908368] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.908505] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.908642] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.908779] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.908915] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.909051] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.909119] HEST: Table is not found!
[    0.909180] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.909190] vgaarb: loaded
[    0.909309] SCSI subsystem initialized
[    0.909430] libata version 3.00 loaded.
[    0.909478] usbcore: registered new interface driver usbfs
[    0.909487] usbcore: registered new interface driver hub
[    0.909513] usbcore: registered new device driver usb
[    0.909717] ACPI: WMI: Mapper loaded
[    0.909719] PCI: Using ACPI for IRQ routing
[    0.909722] PCI: pci_cache_line_size set to 64 bytes
[    0.909976] reserve RAM buffer: 000000000009d000 - 000000000009ffff
[    0.909978] reserve RAM buffer: 00000000bb63f000 - 00000000bbffffff
[    0.909981] reserve RAM buffer: 00000000bb800000 - 00000000bbffffff
[    0.910063] NetLabel: Initializing
[    0.910064] NetLabel:  domain hash size = 128
[    0.910066] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.910080] NetLabel:  unlabeled traffic allowed by default
[    0.910116] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.910121] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.912144] Switching to clocksource tsc
[    0.919868] AppArmor: AppArmor Filesystem Enabled
[    0.919887] pnp: PnP ACPI init
[    0.919905] ACPI: bus type pnp registered
[    0.922709] pnp: PnP ACPI: found 11 devices
[    0.922711] ACPI: ACPI bus type pnp unregistered
[    0.922724] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.922727] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.922729] system 00:05: [io  0x0810-0x0813] has been reserved
[    0.922731] system 00:05: [io  0xffff] has been reserved
[    0.922733] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.922735] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.922738] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.922743] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.922745] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.922747] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.922750] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.922752] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.922755] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.922757] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.922759] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.922762] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.922764] system 00:09: [mem 0xd6500000-0xd6500fff] has been reserved
[    0.922766] system 00:09: [mem 0xff808000-0xff8080ff] has been reserved
[    0.927472] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.927478] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.927484] pci 0000:00:1c.0:   bridge window [mem 0xd5400000-0xd63fffff]
[    0.927489] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.927497] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
[    0.927500] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.927506] pci 0000:00:1c.4:   bridge window [mem 0xd4400000-0xd53fffff]
[    0.927511] pci 0000:00:1c.4:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.927519] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
[    0.927523] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    0.927529] pci 0000:00:1c.5:   bridge window [mem 0xd3400000-0xd43fffff]
[    0.927534] pci 0000:00:1c.5:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.927542] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.927543] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.927549] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.927554] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.927575]   alloc irq_desc for 17 on node -1
[    0.927576]   alloc kstat_irqs on node -1
[    0.927582] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.927588] pci 0000:00:1c.0: setting latency timer to 64
[    0.927599] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.927603] pci 0000:00:1c.4: setting latency timer to 64
[    0.927612]   alloc irq_desc for 16 on node -1
[    0.927613]   alloc kstat_irqs on node -1
[    0.927617] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.927622] pci 0000:00:1c.5: setting latency timer to 64
[    0.927630] pci 0000:00:1e.0: setting latency timer to 64
[    0.927635] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.927636] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.927638] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.927640] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfeafffff]
[    0.927642] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.927644] pci_bus 0000:01: resource 1 [mem 0xd5400000-0xd63fffff]
[    0.927646] pci_bus 0000:01: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.927648] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.927650] pci_bus 0000:02: resource 1 [mem 0xd4400000-0xd53fffff]
[    0.927652] pci_bus 0000:02: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.927654] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.927656] pci_bus 0000:03: resource 1 [mem 0xd3400000-0xd43fffff]
[    0.927658] pci_bus 0000:03: resource 2 [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.927660] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.927662] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.927663] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.927665] pci_bus 0000:04: resource 7 [mem 0xc0000000-0xfeafffff]
[    0.927697] NET: Registered protocol family 2
[    0.927842] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.928834] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.931608] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.931943] TCP: Hash tables configured (established 524288 bind 65536)
[    0.931945] TCP reno registered
[    0.931957] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.931994] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.932119] NET: Registered protocol family 1
[    0.932135] pci 0000:00:02.0: Boot video device
[    0.971624] PCI: CLS 64 bytes, default 64
[    0.971628] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.971631] Placing 64MB software IO TLB between ffff88000a000000 - ffff88000e000000
[    0.971634] software IO TLB at phys 0xa000000 - 0xe000000
[    0.971676] Simple Boot Flag at 0x44 set to 0x1
[    0.971925] Scanning for low memory corruption every 60 seconds
[    0.972057] audit: initializing netlink socket (disabled)
[    0.972069] type=2000 audit(1283200354.820:1): initialized
[    0.986062] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.987315] VFS: Disk quotas dquot_6.5.2
[    0.987367] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.987873] fuse init (API version 7.14)
[    0.987943] msgmni has been set to 7244
[    0.988324] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.988327] io scheduler noop registered
[    0.988329] io scheduler deadline registered
[    0.988361] io scheduler cfq registered (default)
[    0.988460] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.988508]   alloc irq_desc for 40 on node -1
[    0.988510]   alloc kstat_irqs on node -1
[    0.988523] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.988608] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.988652]   alloc irq_desc for 41 on node -1
[    0.988653]   alloc kstat_irqs on node -1
[    0.988661] pcieport 0000:00:1c.4: irq 41 for MSI/MSI-X
[    0.988741] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.988783]   alloc irq_desc for 42 on node -1
[    0.988784]   alloc kstat_irqs on node -1
[    0.988792] pcieport 0000:00:1c.5: irq 42 for MSI/MSI-X
[    0.988878] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.989046] \_SB_.PCI0:_OSC invalid UUID
[    0.989048] _OSC request data:1 0 1f
[    0.989179] \_SB_.PCI0:_OSC invalid UUID
[    0.989181] _OSC request data:1 0 1f
[    0.989308] \_SB_.PCI0:_OSC invalid UUID
[    0.989310] _OSC request data:1 0 1f
[    0.989449] \_SB_.PCI0:_OSC invalid UUID
[    0.989451] _OSC request data:1 0 1f
[    0.989577] \_SB_.PCI0:_OSC invalid UUID
[    0.989579] _OSC request data:1 0 1f
[    0.989704] \_SB_.PCI0:_OSC invalid UUID
[    0.989705] _OSC request data:1 0 1f
[    0.989739] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.989798] intel_idle: MWAIT substates: 0x1120
[    0.989800] intel_idle: v0.4 model 0x25
[    0.989802] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.989968] ACPI: AC Adapter [ACAD] (on-line)
[    0.990029] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.990032] ACPI: Power Button [PWRB]
[    0.990063] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.990169] ACPI: Lid Switch [LID]
[    0.990204] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.990206] ACPI: Power Button [PWRF]
[    0.991104] ACPI: acpi_idle yielding to intel_idle
[    0.996909] ERST: Table is not found!
[    0.997196] ACPI: Battery Slot [BAT1] (battery absent)
[    0.998550] Linux agpgart interface v0.103
[    0.998578] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.000107] brd: module loaded
[    1.000685] loop: module loaded
[    1.001228] Fixed MDIO Bus: probed

```

---

### Post by ktemkin on 2010-09-01
Sorry, was kind of in a rush to get that last reply out, as I had to head home. 

Here is the only mention of battery in my dmesg logs, though my battery works fine.

```

[    0.343664] ACPI: Battery Slot [BAT1] (battery absent)

```

Can you post the output of the acpi command? You'll probably need to sudo apt-get install it.

If you don't get any output, try running it as root.

---

### Post by sigfrido on 2010-09-01
Shouldn't it be

```
acpi=copy_dsdt
```

?

---

### Post by sigfrido on 2010-09-01
That was my guess, installing a new kernel won't do the job. I've tried several kernels and patches, compiling them in my computer and still i don't get it to work. Maybe one should post it as a kernel bug.

---

### Post by RafaelBarreto on 2010-09-01
Thank you again for your attention, ktemkin.

acpi has no output, even as root.
I tried with the option -V (--everything):

```
$ sudo acpi -V
Adapter 0: on-line
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
```There was no need to install it.
Also, looking to the processes, I have:

```
$ ps aux | grep acpi
root        35  0.0  0.0      0     0 ?        S    16:39   0:00 [kacpid]
root        36  0.0  0.0      0     0 ?        S    16:39   0:00 [kacpi_notify]
root        37  0.0  0.0      0     0 ?        S    16:39   0:00 [kacpi_hotplug]
root      1057  0.0  0.0   4476  1124 ?        Ss   16:39   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
```@ sigfrido
Yes... it is "acpi=copy_dsdt", but it was included automatically in the grub.cfg by the kernels >= 2.6.35.


EDIT
The command "acpi -V" returns to me " Adapter 0: on-line" when I start the laptop with the AC plugged, and " Adapter 0: off-line" when I start it with the AC unplugged. And it does not change if I plug or unplug the AC after it starts.

dmesg diff (relevant part)
```

< [    0.990433] ACPI: AC Adapter [ACAD] (on-line)
> [    0.990434] ACPI: AC Adapter [ACAD] (off-line)

```

---

### Post by sigfrido on 2010-09-02
I get the same as rafaelbarreto. Even acpi gives me the same info posted by rafael. I wish someone could point the problem out of all that information?? I'm up to try a new kernel patch, but don't know what to look for...

Thanks.

---

### Post by RafaelBarreto on 2010-09-02
I sent a report to the Toshiba Linux Mailing List:
[http://linux.toshiba-dme.co.jp/pipermail/tlinux-users/2010-September/000516.html](http://linux.toshiba-dme.co.jp/pipermail/tlinux-users/2010-September/000516.html)

And maybe our issue has some relation to this previous issue:
[http://ubuntuforums.org/showthread.php?t=1470732](http://ubuntuforums.org/showthread.php?t=1470732)
(But I see this previous issue was fixed after "acpi=copy_dsdt")

---

### Post by sigfrido on 2010-09-03
@rafael that's cool. I think toshiba laptops are highly unsupported. I also didn't have wireless and ethernet. Acpi is the only noticeable trouble I can't fix. I do think is related to a kernel patch. In posts where they fix the same prob, they do it by patching the kernel. We need another patch, but hey, I'm no kernel expert, so I find it difficult to point out the problem. Hopefully someone would look at this post and point it out.

---

### Post by RafaelBarreto on 2010-09-06
Well... I agree that the toshiba laptops are highly unsupported when the OS is linux.
About 2 years ago I bought another toshiba satellite (A500), and I had the same trouble (that time using ubuntu 8.04). It is very frustrating to enter the official toshiba support homepage ([http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp)) and find the only OS there is windows. This makes me think I did a mistake.

I am not a kernel expert too, so I have no chance to fix this by myself. 

Looking to the output of "acpi -V" and checking it presents "Adapter 0: on-line" when the laptop starts with the cable connected, and "Adapter 0: off-line" when it starts with the cable disconnected, makes me think in some moment the acpid is getting the right stats (maybe related to the "copy_dsdt" fix)...

But as far the power management icon never appears and the "acpi -V" output does not change _after_ the system is on (no matter if I plug or unplug the cable), makes me think this issue is a bit more complex (hald is not running in my system, for example, and in some pages of the internet I read hald is part of the battery stats collecting work). Anyway, I tried to run hald by myself, and nothing changed.

I will keep waiting.

---

### Post by sigfrido on 2010-09-06
Well, patching a kernel is not that complicated as it might seem. In these posts they provide pretty good directions to do it. Now, I find it interesting what you comment on hald, because all these patches are about acpi, and I've tried several. It might be both... I'll keep diggin on.

---

### Post by sigfrido on 2010-09-21
I downloaded the beta version of ubuntu 10.10 and the battery is still shown as not present...

---

### Post by RafaelBarreto on 2010-09-28
Thank you for the info... you saved me from re-installing the OS.
Btw, I had no reply/feedback (linux toshiba, acpi, nor ubuntu devs).

Also, nothing changed here.
I am using the kernel 2.6.35-22, and the battery is still not present, and the cable information does not update/change after the OS is initialized.

---

### Post by RafaelBarreto on 2010-09-28
Ok... digging the gentoo forum, I found an old "how to fix acpi problems"
[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)
and I checked the DSDT:

```

$ sudo cat /proc/acpi/dsdt > dsdt.dat
$ iasl -d dsdt.dat
....
$ iasl -tc dsdt.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2918:             Method (CBRL, 0, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (CBRL)

dsdt.dsl  2980:                 Name (_T_0, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_0)

dsdt.dsl  3360:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  4759:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  5009:                         Name (_T_0, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_0)

dsdt.dsl 10098:             Method (EVNT, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (EVNT)

dsdt.dsl 10650:                 Name (_T_0, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_0)

dsdt.dsl 10698:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl 10766:                         Name (_T_2, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_2)

dsdt.dsl 10803:                                 Name (_T_3, Zero)
Remark   5110 -            Use of compiler reserved name ^  (_T_3)

dsdt.dsl 10836:                                 Name (_T_4, Zero)
Remark   5110 -            Use of compiler reserved name ^  (_T_4)

dsdt.dsl 10896:                                             Name (_T_5, Zero)
Remark   5110 -                        Use of compiler reserved name ^  (_T_5)

dsdt.dsl 10900:                                                 Name (_T_6, Zero)
Remark   5110 -                            Use of compiler reserved name ^  (_T_6)

dsdt.dsl 10953:                                                 Name (_T_7, Zero)
Remark   5110 -                            Use of compiler reserved name ^  (_T_7)

dsdt.dsl 10982:                                                         Name (_T_8, Zero)
Remark   5110 -                                    Use of compiler reserved name ^  (_T_8)

dsdt.dsl 11039:                                                             Name (_T_9, Zero)
Remark   5110 -                                        Use of compiler reserved name ^  (_T_9)

dsdt.dsl 11097:                                                             Name (_T_A, Zero)
Remark   5110 -                                        Use of compiler reserved name ^  (_T_A)

dsdt.dsl 11160:                                                             Name (_T_B, Zero)
Remark   5110 -                                        Use of compiler reserved name ^  (_T_B)

dsdt.dsl 11186:                                                                     Name (_T_C, Zero)
Remark   5110 -                                                Use of compiler reserved name ^  (_T_C)

dsdt.dsl 11213:                                                                         Name (_T_D, Zero)
Remark   5110 -                                                    Use of compiler reserved name ^  (_T_D)

dsdt.dsl 11233:                                                                     Name (_T_E, Zero)
Remark   5110 -                                                Use of compiler reserved name ^  (_T_E)

dsdt.dsl 11280:                                                                         Name (_T_F, Zero)
Remark   5110 -                                                    Use of compiler reserved name ^  (_T_F)

dsdt.dsl 11353:                                                                                 Name (_T_G, Zero)
Remark   5110 -                                                            Use of compiler reserved name ^  (_T_G)

dsdt.dsl 11410:                                                                                     Name (_T_H, Zero)
Remark   5110 -                                                                Use of compiler reserved name ^  (_T_H)

dsdt.dsl 11414:                                                                                         Name (_T_I, Zero)
Remark   5110 -                                                                    Use of compiler reserved name ^  (_T_I)

dsdt.dsl 11476:                                                                                             Name (_T_J, Zero)
Remark   5110 -                                                                        Use of compiler reserved name ^  (_T_J)

dsdt.dsl 11519:                                                                                                 Name (_T_K, Zero)
Remark   5110 -                                                                            Use of compiler reserved name ^  (_T_K)

dsdt.dsl 11614:                                                                                                         Name (_T_L, Zero)
Remark   5110 -                                                                                    Use of compiler reserved name ^  (_T_L)

dsdt.dsl 11655:                                                                                                         Name (_T_M, Zero)
Remark   5110 -                                                                                    Use of compiler reserved name ^  (_T_M)

dsdt.dsl 11669:                                                                                                                     Name (_T_N, Zero)
Remark   5110 -                                                                                                Use of compiler reserved name ^  (_T_N)

dsdt.dsl 11741:                                                                                                             Name (_T_O, Zero)
Remark   5110 -                                                                                        Use of compiler reserved name ^  (_T_O)

dsdt.dsl 11772:                                                                                             Name (_T_P, Zero)
Remark   5110 -                                                                        Use of compiler reserved name ^  (_T_P)

dsdt.dsl 11776:                                                                                                 Name (_T_Q, Zero)
Remark   5110 -                                                                            Use of compiler reserved name ^  (_T_Q)

dsdt.dsl 11857:                                                                                                             Name (_T_R, Zero)
Remark   5110 -                                                                                        Use of compiler reserved name ^  (_T_R)

dsdt.dsl 12876:             Method (BTST, 0, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (BTST)

ASL Input:  dsdt.dsl - 12979 lines, 475657 bytes, 5441 keywords
AML Output: dsdt.aml - 49138 bytes, 1128 named objects, 4313 executable opcodes

Compilation complete. 0 Errors, 3 Warnings, 32 Remarks, 6 Optimizations

```
I got no errors, but I am unable to check if the warnings are related to our ACDC/BATTERY issue.
Please, if there is some ACPI expert around here, check these files and tell us if there is any chance to change the .dsl and fix this issue.


Thanks in advance!

---

### Post by volcom7205 on 2010-10-16
I have an l655-s5072 and im having the same problem. tried the release of 10.10 and still no battery recognized. anyone having any luck?

---

### Post by sigfrido on 2010-10-17
There... 
I tried to make sense of what rafael posted, but I'm not able. It's so good that volcom told us about his experience with ubuntu 10.10. I wasn't sure if I should upgrade or not, though it's more probable they will patch newer versions of the kernel, I think.
I think we should file a bug or something at the ubuntu kernel developers page. This is not going to go away just by doing a minor adjustment here or there.
Cheers.

---

### Post by RafaelBarreto on 2010-10-19
As far as I could understand, this is an acpi issue that could be fixed changing the dsdt (my previous post).

So, we need to get help from some real acpi expert (not exactly distro related).

---

### Post by sigfrido on 2010-10-21
@rafael acpi is a kernel feature. acpi support is included in the kernel, and fixes should be made in the kernel. Distros make several patches in their kernel releases. We need a kernel expert. I'm surprised this post is not receiving more attention.

---

### Post by gmoutso on 2010-10-22
Hi. I have a toshiba L600 from china. Since it is not sold in the west, I will keep a close eye on this thread if you guys find a solution. The problems I have are the same.
Let me know if I could help.
Cheers

---

### Post by RafaelBarreto on 2010-10-26
Well... this means I really do not understand about kernel nor acpi stuff :P.

Anyway, I found a useful tip:

Even without any battery information in my system, sometimes I use my laptop without the AC power. I do it because I believe the battery life will decrease a lot if I never use it. So, recently I realized that my laptop starts to blink one of the front side leds (third one in my case) when the battery is about 10 minutes to end.
I expect this tip to be useful to you (as it is to me).

Anyway, are you sure there is nothing I can do in the dsdt to retrieve the bat info?
Maybe people are not replying to this thread because it is a very specific issue (the title does not help much...)

Well..... we have no other choice except wait some good (kernel expert) soul to help us. :P

---

### Post by vdubhack on 2010-10-29
I am using a qosmio x505-886 and did not realize until I bought it how troublesome Toshibas are with Linux :( 

I am running 10.10 64bit 
Linux 2.6.35-23-generic #36-Ubuntu SMP Tue Oct 26 17:13:06 UTC 2010 x86_64 GNU/Linux


I have a similar issue as you guys my battery shows as not there, but seems to operate fine for me when on AC power or not. I have not seen it as an issue other than it does not see it. 
```

dmesg | grep battery
[    1.976337] ACPI: Battery Slot [BAT1] (battery absent)

```

```

 sudo acpi -V
Battery 0: Full, 100%
Battery 0: design capacity 8000 mAh, last full capacity 7965 mAh = 99%
Adapter 0: on-line
Thermal 0: ok, 82.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 104.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 99.0 degrees C
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: Processor 0 of 10
Cooling 7: Processor 0 of 10
Cooling 8: Processor 0 of 10

```

I just started this bug in case any of you other Toshiba owners are experiencing the same as me, its PCI ACPI related.
[https://bugs.launchpad.net/ubuntu/+bug/668148](https://bugs.launchpad.net/ubuntu/+bug/668148)

---

### Post by RafaelBarreto on 2010-11-28
@ vdubhack

If acpi is returning to you the charge of the battery, then you do not have the same issue as us. TBH, I think you have no issue at all.

Anyway, I do not have this issue anymore too... my laptop was stole inside my office in the middle of the night (3 weeks ago). And now I bought a Dell (which presents no issues with acpi). BTW, do not buy the track service against stealing (lojack something)... it is ********, and I am really pissed with Dell. It is just a windows software that work only when your laptop is connected to the internet (and obviously running windows!).

---

### Post by brent.yerkish on 2010-12-09
Thought I'd jump on the pile.  My battery claims to be absent as well.  Glad to know I'm not the only one, though.  

The tip about the light was useful.  Thanks!

---

### Post by canucked on 2010-12-09
I configured a Toshiba Satellite L655-S5115 for a friend and also could not get the battery to be recognized in Ubuntu.  Just adding to the aforementioned pile.

(And sorry to hear about the stolen laptop, RafaelBarreto)

---

### Post by sigfrido on 2010-12-11
@rafael, so sad to hear that. Now you won't have the fun and joy of fixing acpi :P

If anyone might want to try, ubuntu 11.04 - alpha is out there. Maybe the kernel would have this acpi bug fixed already.

Cheers!

---

### Post by canucked on 2010-12-11
I tried the Ubuntu 11.04 Natty alpha1 64-bit live-USB with a Toshiba L655 but the battery still wasn't recognized.  (The built-in mic, microphone jack, and headphone jack didn't work with Natty, nor did wireless.)

I summarized my Toshiba L655 hardware issues in this thread:
[http://ubuntuforums.org/showthread.php?t=1641931]("http://ubuntuforums.org/showthread.php?t=1641931")

---

### Post by denied on 2010-12-30
Yeah this is a great problem. I just bought the C660-D1 for my mom and its all gone haywire! I can install ubuntu 10.04 x64 and it works. But as soon as i try to update it to 10.10 everything fails. I've tried so many distros now im almost out of dvds =) The fail is in the new kernel of 10.10 something seems to have changed drastically.

Though im sitting with a fresh copy of OpenSuse and when you load the cd you have the option to turn of acpi during boot. And amazingly it got me to the installation screen! (had to reboot to see if that was the option that made it go that far =)

Now the weirdest part is this, when i try to add to the command line in ubuntu 10.10 boot, acpi=off my screen starts to flicker. This is without pressing enter, it actually happens when i write acpi=o then the screen goes all wild and insane. Im so close to make a youtube video out of it because this issue is like a seeing a ghost. I've never in my life experienced anything like this. It resembles the mad screen u got back in the days when u did a wrong x config =)

I must say im amazed about this issue, i'll try to install OpenSuse now and see how far i can get. After all i could upgrade to 10.10 ubuntu but then i couldnt boot it. If u ask me this is a heavy duty issue for the kernel devs.


EDiT:

Well OpenSuse 11.3 is definitely working! As far as i can see from the first look, the network driver is working 100% and compiz is working with the 3d cube (from default), screen resolution is as it should be, sound driver is working out of the box, my god. I must say im SERIOUSLY impressed with OpenSuse right now. Its been for ever since i tested that dist but wow!

I would suggest you do the same, press F5 when u boot the cd to change the kernel options and pick no ACPI option there. Let us know how it goes, in that case if you also can make something successful then there is some serious issues to the ubuntu kernel when it comes to Toshiba laptops.

---

### Post by techinterplay on 2011-01-12
> **canucked said:**
> I tried the Ubuntu 11.04 Natty alpha1 64-bit live-USB with a Toshiba L655 but the battery still wasn't recognized.  (The built-in mic, microphone jack, and headphone jack didn't work with Natty, nor did wireless.)

I summarized my Toshiba L655 hardware issues in this thread:
[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Guys, I do have the same issue. I am with Toshiba Satellite L650 X5310. Here is my dmesg 

*[    0.973991] ACPI: Battery Slot [BAT1] (battery absent)*

[I]sudo acpi -V
[sudo] password for me: 
Adapter 0: on-line
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10[/I]

The in-built mic too is not recognised, oh I am lucky in the case of speakers ,webcam, wireless and external mic jack ;). There is a flickering while loading the login page and it goes after I login.

I have updated the BIOS and kernel  to the latest one. I have Centos and BackTrack Linux installed on the same laptop and all posses the same issue. So its a typical Kernel related issue as you guys concluded and need a fix/patch. I am not sure how long we have to wait for this to be done by someone how are good with Kernels :( *sighs*

---

### Post by Bucky Ball on 2011-01-13
Hey, denied. I am just about to install OpenSuse 11.3. I have downloaded  the Gnome version just to try off the disk and I like the look of it so  have also downloaded the full DVD install. Which one did you go for? If  I install the Gnome minimal version, can I then just download whatever  packages I want and bloat out to the full DVD install anyhow???

Tnx in advance. ;)

ps: I know this is a bit off topic and should possibly be in the OpenSUSE forum so apologies, but ... I am using a Toshiba Satellite Pro L510 and the wireless in Ubuntu 10.10 is rubbish. Randomly fluctuating signal strength and extremely slow. I have tried everything but no joy (including every Ubuntu kernel from Lucid's 2.6.32 to Natty's 2.6.37 2.6.35-24 is the only one I have been able to get running. That is why I am going to try OpenSUSE. See if that makes any diff re my wireless issue. ;)

---

### Post by techinterplay on 2011-01-14
@Bucky, FYI wireless runs just fine for me on Ubuntu 10.10. I just installed the Broadcom driver from  System--> Administration --> Additional Drivers. It automatically pulled-up the Broadcom STA wireless driver upon a search :-) I got webcam and mic too working just fine but Battery issue still remains :( I am going to try Debain Squeeze by tomorrow and will let you know the results. Below is my wireless device 

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

---

### Post by techinterplay on 2011-01-14
@Bucky, FYI wireless runs just fine for me on Ubuntu 10.10. I just installed the Broadcom driver from  System--> Administration --> Additional Drivers. It automatically pulled-up the Broadcom STA wireless driver upon a search :-) I got webcam and mic too working just fine but Battery issue still remains :( I am going to try Debain Squeeze by tomorrow and will let you know the results. Below is my wireless device 

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

---

### Post by techinterplay on 2011-01-14
@Bucky, FYI wireless runs just fine for me on Ubuntu 10.10. I just  installed the Broadcom driver from  System--> Administration -->  Additional Drivers. It automatically pulled-up the Broadcom STA wireless  driver upon a search :smile: I got webcam and mic too working just fine but Battery issue still remains :sad: I am going to try Debain Squeeze by tomorrow and will let you know the results. Below is my wireless device 

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

---

### Post by sigfrido on 2011-01-14
Hello all. I have been trying new kernel versions and even an opensuse live cd (just to check whether some other kernels have a fix for the acpi problem, not that I want to switch to other disto). I haven been lucky.

However I noticed an interesting fact. I usually set Advanced Power Management level for the hard drive at 254 (automatically, when booting). When I boot my laptop using the battery only, the APM level is set to 128 (a super saving energy level, but also a hard drive killer). This is interesting, because it means to me that at some level the system is detecting that the energy supply is battery only, i.e., it knows the battery is present or not. The weird thing is that somehow statistics about it are missing... I even have cpu scaling support.

Hope this piece of information can help someone (including me).


Cheers!

---

### Post by sigfrido on 2011-01-14
Hello all. I have been trying new kernel versions and even an opensuse live cd (just to check whether some other kernels have a fix for the acpi problem, not that I want to switch to other disto). I haven been lucky.

However I noticed an interesting fact. I usually set Advanced Power Management level for the hard drive at 254 (automatically, when booting). When I boot my laptop using the battery only, the APM level is set to 128 (a super saving energy level, but also a hard drive killer). This is interesting, because it means to me that at some level the system is detecting that the energy supply is battery only, i.e., it knows the battery is present or not. The weird thing is that somehow statistics about it are missing... I even have cpu scaling support.

Hope this piece of information can help someone (including me).


Cheers!

---

### Post by sigfrido on 2011-01-14
Hello all. I have been trying new kernel versions and even an opensuse live cd (just to check whether some other kernels have a fix for the acpi problem, not that I want to switch to other disto). I haven't been lucky.

However I noticed an interesting fact. I usually set Advanced Power Management level for the hard drive at 254 (automatically, when booting). When I boot my laptop using the battery only, the APM level is set to 128 (a super saving energy level, but also a hard drive killer). This is interesting, because it means to me that at some level the system is detecting that the energy supply is battery only, i.e., it knows the battery is present or not. The weird thing is that somehow statistics about it are missing... I even have cpu scaling support.

Hope this piece of information can help someone (including me).


Cheers!

---

### Post by techinterplay on 2011-06-03
Hello Everyone,

Good News :-) battery issue has been resolved [http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html)
Hope this helps!

---

### Post by sigfrido on 2011-07-03
Hello. Thank you techinterplay for the link. I followed directions, but I'm still struggling with the kernel compilation. It simply doesn't compile. I'm getting my hands dirty on this this Sunday and I'll post the result once I'm able to compile the kernel correctly.
Cheers.

---

### Post by sigfrido on 2012-02-11
Hello all. I tried the solution posted here by techinterplay

[http://techinterplay.com/fix-toshiba-battery-issue-linux.html]("http://techinterplay.com/fix-toshiba-battery-issue-linux.html")

and it works! I had some troubles compiling the kernel before, but I decided to try a few days ago with the 3.0.0-xx kernel series (I'm now on Ubuntu 11.10). Be careful with directions posted in that link, because there is a typo:

The next to the last line of code you need to run should be

update-initramfs -c -k 2.6.38-tuxsage

(- instead of a +),

if you are repeating directions verbatim. Of course the kernel version you download should replace the version number used there. Don't forget to use sudo.

When you compile the kernel a lot of files are created in your partition under the folder containing the source code of the kernel. Be sure you have enough space on your partition; the compilation I ran took up to 7 Gib + of disk space. You might also want to delete the files after the compilation.

I have nothing to say about the method there proposed regarding kernel compilation, but there's another way, the "git method", that ensures you will have the latest kernel version supported by Ubuntu. The method techinterplay suggests, the "source archive method", works pretty fine, but you might get an outdated kernel version. You can read about this here

[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

I tried the git method myself and got positive results, but it represents a bit more laborious way to do things. I will post later my solution on another thread.

---

