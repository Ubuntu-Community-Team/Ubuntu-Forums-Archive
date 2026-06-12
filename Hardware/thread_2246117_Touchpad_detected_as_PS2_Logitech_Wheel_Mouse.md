---
title: "Touchpad detected as PS/2 Logitech Wheel Mouse"
date: 2014-09-28
forum: Hardware
---

### Post by andreas27 on 2014-09-28
Hey Everybody!

I bought this Asus N550JK about 4 weeks ago and everything was working (almost) perfectly fine (Right click didn't work flawlessly due to a hardware defekt).
After another defect (Some defective pixels) i thought this is enough and sent it in for repair.
So i got the Notebook back today and they replaced the Touchpad...
Now the Touchpad is detected as "PS/2 Logitech Wheel Mouse" as it can be seen here:
```

andreas@andreas-N550JK:~$ xinput 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

``` 
Now i can move the pointer around and also tapping is working but i can't use Multigesture which is pretty annoying since i can't scroll anymore... The touchpad specific options in mouse settings are also missing!
Here is what dmesg says:
```

[    0.000000] ACPI: _OSI method disabled
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7829128K/8268864K available (7373K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1440K bss, 439736K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] tsc: Detected 2394.550 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.10 BogoMIPS (lpj=9578200)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000746] Security Framework initialized
[    0.000760] AppArmor: AppArmor initialized
[    0.000760] Yama: becoming mindful.
[    0.001140] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002790] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003528] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003534] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003705] Initializing cgroup subsys memory
[    0.003709] Initializing cgroup subsys devices
[    0.003710] Initializing cgroup subsys freezer
[    0.003711] Initializing cgroup subsys blkio
[    0.003712] Initializing cgroup subsys perf_event
[    0.003713] Initializing cgroup subsys hugetlb
[    0.003729] CPU: Physical Processor ID: 0
[    0.003730] CPU: Processor Core ID: 0
[    0.003733] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003733] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.004498] mce: CPU supports 9 MCE banks
[    0.004509] CPU0: Thermal monitoring enabled (TM1)
[    0.004518] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.004518] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.004518] tlb_flushall_shift: 6
[    0.004599] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
[    0.005317] ACPI: Core revision 20131115
[    0.014672] ACPI: All ACPI Tables successfully acquired
[    0.019567] ftrace: allocating 28537 entries in 112 pages
[    0.028376] dmar: Host address width 39
[    0.028377] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.028383] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.028384] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.028387] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008020660462 ecap f010da
[    0.028388] dmar: RMRR base: 0x000000c9a7d000 end: 0x000000c9a89fff
[    0.028389] dmar: RMRR base: 0x000000cbc00000 end: 0x000000cfdfffff
[    0.028454] IOAPIC id 8 under DRHD base  0xfed91000 IOMMU 1
[    0.028455] HPET id 0 under DRHD base 0xfed91000
[    0.028586] Enabled IRQ remapping in x2apic mode
[    0.028587] Enabling x2apic
[    0.028587] Enabled x2apic
[    0.028592] Switched APIC routing to cluster x2apic.
[    0.029008] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068725] smpboot: CPU0: Intel(R) Core(TM) i7-4700HQ CPU @ 2.40GHz (fam: 06, model: 3c, stepping: 03)
[    0.068731] TSC deadline timer enabled
[    0.068739] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.068743] ... version:                3
[    0.068744] ... bit width:              48
[    0.068745] ... generic registers:      4
[    0.068745] ... value mask:             0000ffffffffffff
[    0.068746] ... max period:             0000ffffffffffff
[    0.068746] ... fixed-purpose events:   3
[    0.068747] ... event mask:             000000070000000f
[    0.069860] x86: Booting SMP configuration:
[    0.083754] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.069861] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.167145] x86: Booted up 1 node, 8 CPUs
[    0.167148] smpboot: Total of 8 processors activated (38312.80 BogoMIPS)
[    0.172932] devtmpfs: initialized
[    0.174465] EVM: security.selinux
[    0.174465] EVM: security.SMACK64
[    0.174466] EVM: security.ima
[    0.174467] EVM: security.capability
[    0.174496] PM: Registering ACPI NVS region [mem 0xb97fd000-0xb9803fff] (28672 bytes)
[    0.174497] PM: Registering ACPI NVS region [mem 0xc9e1c000-0xcab1efff] (13643776 bytes)
[    0.175101] pinctrl core: initialized pinctrl subsystem
[    0.175139] regulator-dummy: no parameters
[    0.175164] RTC time: 17:14:08, date: 09/28/14
[    0.175185] NET: Registered protocol family 16
[    0.175250] cpuidle: using governor ladder
[    0.175251] cpuidle: using governor menu
[    0.175277] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.175278] ACPI: bus type PCI registered
[    0.175279] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.175313] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.175314] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.180473] PCI: Using configuration type 1 for base access
[    0.181079] bio: create slab <bio-0> at 0
[    0.181183] ACPI: Added _OSI(Module Device)
[    0.181184] ACPI: Added _OSI(Processor Device)
[    0.181185] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.181186] ACPI: Added _OSI(Processor Aggregator Device)
[    0.182867] ACPI : EC: EC description table is found, configuring boot EC
[    0.184655] ACPI: Executed 2 blocks of module-level executable AML code
[    0.208919] ACPI: SSDT 00000000c9aebc18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
[    0.209479] ACPI: Dynamic OEM Table Load:
[    0.209481] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
[    0.213036] ACPI: SSDT 00000000c9aeb618 0005AA (v01  PmRef    ApIst 00003000 INTL 20120711)
[    0.213654] ACPI: Dynamic OEM Table Load:
[    0.213655] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20120711)
[    0.216916] ACPI: SSDT 00000000c9aead98 000119 (v01  PmRef    ApCst 00003000 INTL 20120711)
[    0.217474] ACPI: Dynamic OEM Table Load:
[    0.217475] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20120711)
[    0.221980] ACPI: Interpreter enabled
[    0.221987] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.221993] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.222008] ACPI: (supports S0 S3 S4 S5)
[    0.222010] ACPI: Using IOAPIC for interrupt routing
[    0.222034] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.222236] ACPI: No dock devices found.
[    0.228994] ACPI: Power Resource [PG00] (on)
[    0.232550] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    0.232553] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff8802234f4708), AE_NOT_FOUND (20131115/psparse-536)
[    0.232562] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    0.232564] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff8802234f4708), AE_NOT_FOUND (20131115/psparse-536)
[    0.232576] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    0.232578] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff8802234f4708), AE_NOT_FOUND (20131115/psparse-536)
[    0.233410] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.233413] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.233750] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.234137] PCI host bridge to bus 0000:00
[    0.234139] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.234140] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.234141] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.234142] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.234143] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.234144] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.234145] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.234146] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.234147] pci_bus 0000:00: root bus resource [mem 0xcfe00000-0xfeafffff]
[    0.234153] pci 0000:00:00.0: [8086:0c04] type 00 class 0x060000
[    0.234210] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.234234] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.234268] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.234290] pci 0000:00:02.0: [8086:0416] type 00 class 0x030000
[    0.234297] pci 0000:00:02.0: reg 0x10: [mem 0xf7400000-0xf77fffff 64bit]
[    0.234302] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.234305] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.234356] pci 0000:00:03.0: [8086:0c0c] type 00 class 0x040300
[    0.234362] pci 0000:00:03.0: reg 0x10: [mem 0xf7a14000-0xf7a17fff 64bit]
[    0.234438] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.234454] pci 0000:00:14.0: reg 0x10: [mem 0xf7a00000-0xf7a0ffff 64bit]
[    0.234506] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.234533] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.234554] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.234571] pci 0000:00:16.0: reg 0x10: [mem 0xf7a1e000-0xf7a1e00f 64bit]
[    0.234627] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.234683] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    0.234701] pci 0000:00:1a.0: reg 0x10: [mem 0xf7a1c000-0xf7a1c3ff]
[    0.234780] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.234818] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.234842] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    0.234854] pci 0000:00:1b.0: reg 0x10: [mem 0xf7a10000-0xf7a13fff 64bit]
[    0.234910] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.234940] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.234959] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    0.235014] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.235045] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.235065] pci 0000:00:1c.1: [8086:8c12] type 01 class 0x060400
[    0.235121] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.235169] pci 0000:00:1c.2: [8086:8c14] type 01 class 0x060400
[    0.235225] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.235256] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.235274] pci 0000:00:1c.3: [8086:8c16] type 01 class 0x060400
[    0.235330] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.235361] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.235387] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    0.235405] pci 0000:00:1d.0: reg 0x10: [mem 0xf7a1b000-0xf7a1b3ff]
[    0.235485] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.235523] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.235544] pci 0000:00:1f.0: [8086:8c49] type 00 class 0x060100
[    0.235678] pci 0000:00:1f.2: [8086:8c03] type 00 class 0x010601
[    0.235692] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.235698] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.235705] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.235711] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.235718] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.235724] pci 0000:00:1f.2: reg 0x24: [mem 0xf7a1a000-0xf7a1a7ff]
[    0.235757] pci 0000:00:1f.2: PME# supported from D3hot
[    0.235798] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.235811] pci 0000:00:1f.3: reg 0x10: [mem 0xf7a19000-0xf7a190ff 64bit]
[    0.235829] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.235914] pci 0000:01:00.0: [10de:1391] type 00 class 0x030200
[    0.235920] pci 0000:01:00.0: reg 0x10: [mem 0xf6000000-0xf6ffffff]
[    0.235927] pci 0000:01:00.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.235933] pci 0000:01:00.0: reg 0x1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.235938] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.235943] pci 0000:01:00.0: reg 0x30: [mem 0xf7000000-0xf707ffff pref]
[    0.235972] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.241816] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.241818] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.241821] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.241824] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.241884] acpiphp: Slot [1] registered
[    0.241890] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.241949] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.242085] pci 0000:04:00.0: [8086:08b1] type 00 class 0x028000
[    0.242135] pci 0000:04:00.0: reg 0x10: [mem 0xf7900000-0xf7901fff 64bit]
[    0.242346] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.249845] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.249851] pci 0000:00:1c.2:   bridge window [mem 0xf7900000-0xf79fffff]
[    0.249937] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
[    0.249955] pci 0000:05:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.249983] pci 0000:05:00.0: reg 0x18: [mem 0xf7800000-0xf7800fff 64bit]
[    0.250001] pci 0000:05:00.0: reg 0x20: [mem 0xf2100000-0xf2103fff 64bit pref]
[    0.250077] pci 0000:05:00.0: supports D1 D2
[    0.250078] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.257839] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.257843] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.257846] pci 0000:00:1c.3:   bridge window [mem 0xf7800000-0xf78fffff]
[    0.257851] pci 0000:00:1c.3:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.257887] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.258707] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    0.258747] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 12)
[    0.258785] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 10 12)
[    0.258832] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
[    0.258865] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.258897] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.258929] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
[    0.258960] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    0.258986] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    0.258988] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff8802234f4708), AE_NOT_FOUND (20131115/psparse-536)
[    0.259354] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.259359] ACPI: \_SB_.PCI0: notify handler is installed
[    0.259421] Found 1 acpi root devices
[    0.259472] ACPI : EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.259535] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.259537] vgaarb: loaded
[    0.259538] vgaarb: bridge control possible 0000:00:02.0
[    0.259637] SCSI subsystem initialized
[    0.259668] libata version 3.00 loaded.
[    0.259679] ACPI: bus type USB registered
[    0.259690] usbcore: registered new interface driver usbfs
[    0.259694] usbcore: registered new interface driver hub
[    0.259718] usbcore: registered new device driver usb
[    0.259790] PCI: Using ACPI for IRQ routing
[    0.260997] PCI: pci_cache_line_size set to 64 bytes
[    0.261044] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.261045] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.261046] e820: reserve RAM buffer [mem 0xb97fd000-0xbbffffff]
[    0.261046] e820: reserve RAM buffer [mem 0xba06f000-0xbbffffff]
[    0.261047] e820: reserve RAM buffer [mem 0xc98e0000-0xcbffffff]
[    0.261048] e820: reserve RAM buffer [mem 0xc9e1c000-0xcbffffff]
[    0.261049] e820: reserve RAM buffer [mem 0xcb000000-0xcbffffff]
[    0.261050] e820: reserve RAM buffer [mem 0x22f200000-0x22fffffff]
[    0.261095] NetLabel: Initializing
[    0.261096] NetLabel:  domain hash size = 128
[    0.261097] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.261104] NetLabel:  unlabeled traffic allowed by default
[    0.261138] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.261141] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.263168] Switched to clocksource hpet
[    0.266008] AppArmor: AppArmor Filesystem Enabled
[    0.266020] pnp: PnP ACPI init
[    0.266028] ACPI: bus type PNP registered
[    0.266083] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.266086] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.266135] pnp 00:01: [dma 4]
[    0.266144] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.266162] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.266224] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.266252] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.266327] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.266329] system 00:05: [io  0xffff] has been reserved
[    0.266330] system 00:05: [io  0xffff] has been reserved
[    0.266331] system 00:05: [io  0xffff] has been reserved
[    0.266332] system 00:05: [io  0x1c00-0x1cfe] has been reserved
[    0.266333] system 00:05: [io  0x1d00-0x1dfe] has been reserved
[    0.266334] system 00:05: [io  0x1e00-0x1efe] has been reserved
[    0.266335] system 00:05: [io  0x1f00-0x1ffe] has been reserved
[    0.266336] system 00:05: [io  0x1800-0x18fe] could not be reserved
[    0.266337] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.266339] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266353] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.266379] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.266380] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.266408] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.266409] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266426] system 00:09: [io  0x0240-0x0259] has been reserved
[    0.266427] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266461] pnp 00:0a: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.266482] pnp 00:0b: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.266728] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.266730] system 00:0c: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.266731] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.266732] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.266733] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.266734] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.266736] system 00:0c: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.266737] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.266738] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.266739] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.266740] system 00:0c: [mem 0xf7fdf000-0xf7fdffff] has been reserved
[    0.266741] system 00:0c: [mem 0xf7fe0000-0xf7feffff] has been reserved
[    0.266743] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266787] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266890] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    0.266893] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff8802234f4708), AE_NOT_FOUND (20131115/psparse-536)
[    0.266972] pnp: PnP ACPI: found 14 devices
[    0.266973] ACPI: bus type PNP unregistered
[    0.272658] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.272660] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.272662] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000
[    0.272676] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.272677] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.272678] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.272680] pci 0000:00:1c.1: BAR 14: assigned [mem 0xcfe00000-0xcfffffff]
[    0.272682] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf2200000-0xf23fffff 64bit pref]
[    0.272684] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    0.272685] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.272687] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.272689] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.272691] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.272693] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.272702] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.272704] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.272708] pci 0000:00:1c.1:   bridge window [mem 0xcfe00000-0xcfffffff]
[    0.272712] pci 0000:00:1c.1:   bridge window [mem 0xf2200000-0xf23fffff 64bit pref]
[    0.272716] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.272720] pci 0000:00:1c.2:   bridge window [mem 0xf7900000-0xf79fffff]
[    0.272727] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.272729] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.272733] pci 0000:00:1c.3:   bridge window [mem 0xf7800000-0xf78fffff]
[    0.272737] pci 0000:00:1c.3:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.272742] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.272743] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.272744] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.272745] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.272746] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.272747] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.272748] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.272749] pci_bus 0000:00: resource 11 [mem 0xcfe00000-0xfeafffff]
[    0.272750] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.272751] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    0.272752] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.272753] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.272754] pci_bus 0000:03: resource 1 [mem 0xcfe00000-0xcfffffff]
[    0.272755] pci_bus 0000:03: resource 2 [mem 0xf2200000-0xf23fffff 64bit pref]
[    0.272756] pci_bus 0000:04: resource 1 [mem 0xf7900000-0xf79fffff]
[    0.272757] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    0.272758] pci_bus 0000:05: resource 1 [mem 0xf7800000-0xf78fffff]
[    0.272759] pci_bus 0000:05: resource 2 [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.272780] NET: Registered protocol family 2
[    0.272883] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.273006] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.273169] TCP: Hash tables configured (established 65536 bind 65536)
[    0.273183] TCP: reno registered
[    0.273190] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.273218] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.273270] NET: Registered protocol family 1
[    0.273277] pci 0000:00:02.0: Boot video device
[    0.273597] PCI: CLS 64 bytes, default 64
[    0.273631] Trying to unpack rootfs image as initramfs...
[    0.569307] Freeing initrd memory: 27804K (ffff8800349a2000 - ffff8800364c9000)
[    0.569337] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.569339] software IO TLB [mem 0xb57fd000-0xb97fd000] (64MB) mapped at [ffff8800b57fd000-ffff8800b97fcfff]
[    0.569532] microcode: CPU0 sig=0x306c3, pf=0x20, revision=0x17
[    0.569538] microcode: CPU1 sig=0x306c3, pf=0x20, revision=0x17
[    0.569541] microcode: CPU2 sig=0x306c3, pf=0x20, revision=0x17
[    0.569546] microcode: CPU3 sig=0x306c3, pf=0x20, revision=0x17
[    0.569550] microcode: CPU4 sig=0x306c3, pf=0x20, revision=0x17
[    0.569554] microcode: CPU5 sig=0x306c3, pf=0x20, revision=0x17
[    0.569560] microcode: CPU6 sig=0x306c3, pf=0x20, revision=0x17
[    0.569565] microcode: CPU7 sig=0x306c3, pf=0x20, revision=0x17
[    0.569596] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.569597] Scanning for low memory corruption every 60 seconds
[    0.569772] Initialise system trusted keyring
[    0.569798] audit: initializing netlink socket (disabled)
[    0.569805] type=2000 audit(1411924448.556:1): initialized
[    0.588196] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.588842] zbud: loaded
[    0.588936] VFS: Disk quotas dquot_6.5.2
[    0.588960] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.589193] fuse init (API version 7.22)
[    0.589234] msgmni has been set to 15730
[    0.589265] Key type big_key registered
[    0.589604] Key type asymmetric registered
[    0.589605] Asymmetric key parser 'x509' registered
[    0.589620] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.589656] io scheduler noop registered
[    0.589657] io scheduler deadline registered (default)
[    0.589669] io scheduler cfq registered
[    0.589790] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    0.589873] pcieport 0000:00:1c.0: irq 43 for MSI/MSI-X
[    0.589965] pcieport 0000:00:1c.1: irq 44 for MSI/MSI-X
[    0.590059] pcieport 0000:00:1c.2: irq 45 for MSI/MSI-X
[    0.590147] pcieport 0000:00:1c.3: irq 46 for MSI/MSI-X
[    0.590198] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.590200] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.590202] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.590212] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.590215] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.590224] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.590228] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.590237] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.590238] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.590241] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.590252] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.590253] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    0.590256] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.590263] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.590290] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 8c12 ss_vid 1043 ss_did 11cd
[    0.590316] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
[    0.590319] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.590342] efifb: probing for efifb
[    0.590614] efifb: framebuffer at 0xd0000000, mapped to 0xffffc90004e80000, using 3072k, total 3072k
[    0.590615] efifb: mode is 1024x768x32, linelength=4096, pages=1
[    0.590615] efifb: scrolling: redraw
[    0.590616] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.591880] Console: switching to colour frame buffer device 128x48
[    0.593083] fb0: EFI VGA frame buffer device
[    0.593090] intel_idle: MWAIT substates: 0x42120
[    0.593090] intel_idle: v0.4 model 0x3C
[    0.593091] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.593201] ipmi message handler version 39.2
[    0.599468] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.599508] ACPI: AC Adapter [AC0] (on-line)
[    0.599594] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.600302] ACPI: Lid Switch [LID]
[    0.600327] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.600330] ACPI: Sleep Button [SLPB]
[    0.600351] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.600353] ACPI: Power Button [PWRF]
[    0.600907] thermal LNXTHERM:00: registered as thermal_zone0
[    0.600909] ACPI: Thermal Zone [THRM] (46 C)
[    0.600927] GHES: HEST is not enabled!
[    0.600983] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.601925] Linux agpgart interface v0.103
[    0.602725] brd: module loaded
[    0.603136] loop: module loaded
[    0.603339] libphy: Fixed MDIO Bus: probed
[    0.603382] tun: Universal TUN/TAP device driver, 1.6
[    0.603382] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.603409] PPP generic driver version 2.4.2
[    0.603435] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.603437] ehci-pci: EHCI PCI platform driver
[    0.603512] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.603515] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.603527] ehci-pci 0000:00:1a.0: debug port 2
[    0.607454] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.607469] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7a1c000
[    0.619489] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.619520] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.619522] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.619523] usb usb1: Product: EHCI Host Controller
[    0.619524] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    0.619525] usb usb1: SerialNumber: 0000:00:1a.0
[    0.619732] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.619746] ACPI: Battery Slot [BAT0] (battery present)
[    0.619852] hub 1-0:1.0: USB hub found
[    0.619857] hub 1-0:1.0: 2 ports detected
[    0.619981] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.619984] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.619994] ehci-pci 0000:00:1d.0: debug port 2
[    0.623877] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.623890] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7a1b000
[    0.635496] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.635524] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.635526] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.635528] usb usb2: Product: EHCI Host Controller
[    0.635529] usb usb2: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    0.635530] usb usb2: SerialNumber: 0000:00:1d.0
[    0.635652] hub 2-0:1.0: USB hub found
[    0.635657] hub 2-0:1.0: 2 ports detected
[    0.635740] ehci-platform: EHCI generic platform driver
[    0.635746] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.635747] ohci-pci: OHCI PCI platform driver
[    0.635753] ohci-platform: OHCI generic platform driver
[    0.635760] uhci_hcd: USB Universal Host Controller Interface driver
[    0.635856] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.635859] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.635948] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.635970] xhci_hcd 0000:00:14.0: irq 47 for MSI/MSI-X
[    0.636023] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.636025] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.636026] usb usb3: Product: xHCI Host Controller
[    0.636027] usb usb3: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    0.636028] usb usb3: SerialNumber: 0000:00:14.0
[    0.636137] hub 3-0:1.0: USB hub found
[    0.636155] hub 3-0:1.0: 14 ports detected
[    0.639118] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.639121] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.639148] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.639149] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.639150] usb usb4: Product: xHCI Host Controller
[    0.639151] usb usb4: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    0.639152] usb usb4: SerialNumber: 0000:00:14.0
[    0.639259] hub 4-0:1.0: USB hub found
[    0.639268] hub 4-0:1.0: 4 ports detected
[    0.647592] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.649989] i8042: Detected active multiplexing controller, rev 1.1
[    0.651386] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.651389] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.651401] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.651411] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.651418] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.651554] mousedev: PS/2 mouse device common for all mice
[    0.651696] rtc_cmos 00:06: RTC can wake from S4
[    0.651808] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.651833] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.651868] device-mapper: uevent: version 1.0.3
[    0.651925] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.651929] ledtrig-cpu: registered to indicate activity on CPUs
[    0.651930] EFI Variables Facility v0.08 2004-May-17
[    0.654039] TCP: cubic registered
[    0.654091] NET: Registered protocol family 10
[    0.654197] NET: Registered protocol family 17
[    0.654202] Key type dns_resolver registered
[    0.654464] Loading compiled-in X.509 certificates
[    0.655019] Loaded X.509 cert 'Magrathea: Glacier signing key: 38f3b6c63a85affdfbbe0e53339df8e0c6b6c9d5'
[    0.655034] registered taskstats version 1
[    0.656979] Key type trusted registered
[    0.658819] Key type encrypted registered
[    0.660571] AppArmor: AppArmor sha1 policy hashing enabled
[    0.660573] IMA: No TPM chip found, activating TPM-bypass!
[    0.660952] regulator-dummy: disabling
[    0.661116]   Magic number: 14:95:240
[    0.661238] rtc_cmos 00:06: setting system clock to 2014-09-28 17:14:09 UTC (1411924449)
[    0.662397] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.662399] EDD information not available.
[    0.662426] PM: Hibernation image not present or could not be loaded.
[    0.663042] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    0.663043] Write protecting the kernel read-only data: 12288k
[    0.664495] Freeing unused kernel memory: 808K (ffff880002736000 - ffff880002800000)
[    0.665559] Freeing unused kernel memory: 692K (ffff880002b53000 - ffff880002c00000)
[    0.676462] systemd-udevd[146]: starting version 204
[    0.692821] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.693921] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.693928] r8169 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.693934] ahci 0000:00:1f.2: version 3.0
[    0.694293] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    0.694346] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x14 impl SATA mode
[    0.694349] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio ems apst 
[    0.694999] [drm] Initialized drm 1.1.0 20060810
[    0.699990] r8169 0000:05:00.0: irq 49 for MSI/MSI-X
[    0.700038] scsi0 : ahci
[    0.700125] scsi1 : ahci
[    0.700168] r8169 0000:05:00.0 eth0: RTL8168g/8111g at 0xffffc90004c84000, 10:c3:7b:1d:f3:7e, XID 0c000800 IRQ 49
[    0.700171] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.700191] scsi2 : ahci
[    0.700349] scsi3 : ahci
[    0.700411] scsi4 : ahci
[    0.700444] ata1: DUMMY
[    0.700446] ata2: DUMMY
[    0.700449] ata3: SATA max UDMA/133 abar m2048@0xf7a1a000 port 0xf7a1a200 irq 48
[    0.700450] ata4: DUMMY
[    0.700452] ata5: SATA max UDMA/133 abar m2048@0xf7a1a000 port 0xf7a1a300 irq 48
[    0.705797] [drm] Memory usable by graphics device = 2048M
[    0.705799] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[    0.705800] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[    0.705809] Console: switching to colour dummy device 80x25
[    0.751681] i915 0000:00:02.0: irq 50 for MSI/MSI-X
[    0.751696] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.751697] [drm] Driver supports precise vblank timestamp query.
[    0.751764] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.931772] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.019804] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.019822] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.020399] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.020403] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.020405] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.021246] ata5.00: ATA-8: SanDisk SD6SB1M256G1002, X231600, max UDMA/133
[    1.021248] ata5.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.021415] ata3.00: ATAPI: MATSHITABD-CMB UJ172 S, 1.00, max UDMA/133
[    1.021816] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.021818] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.021820] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.022511] ata3.00: configured for UDMA/133
[    1.022658] ata5.00: configured for UDMA/133
[    1.025632] scsi 2:0:0:0: CD-ROM            MATSHITA BD-CMB UJ172 S   1.00 PQ: 0 ANSI: 5
[    1.027855] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.027857] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.027947] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.028001] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.028149] scsi 4:0:0:0: Direct-Access     ATA      SanDisk SD6SB1M2 X231 PQ: 0 ANSI: 5
[    1.028264] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.028315] sd 4:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    1.028660] sd 4:0:0:0: [sda] Write Protect is off
[    1.028662] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.028793] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.030594]  sda: sda1 sda2 sda3
[    1.031379] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.046703] random: lvm urandom read with 34 bits of entropy available
[    1.061079] bio: create slab <bio-1> at 1
[    1.068146] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    1.068149] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.068425] hub 1-1:1.0: USB hub found
[    1.068517] hub 1-1:1.0: 6 ports detected
[    1.087879] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    1.105848] fbcon: inteldrmfb (fb0) is primary device
[    1.179967] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.312502] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    1.312503] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.312749] hub 2-1:1.0: USB hub found
[    1.312836] hub 2-1:1.0: 8 ports detected
[    1.480183] usb 3-5: new full-speed USB device number 2 using xhci_hcd
[    1.497186] usb 3-5: New USB device found, idVendor=8087, idProduct=07dc
[    1.497188] usb 3-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.568254] tsc: Refined TSC clocksource calibration: 2394.455 MHz
[    1.664338] usb 3-7: new high-speed USB device number 3 using xhci_hcd
[    1.781614] usb 3-7: New USB device found, idVendor=13d3, idProduct=5188
[    1.781615] usb 3-7: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.781616] usb 3-7: Product: USB2.0 UVC HD Webcam
[    1.781617] usb 3-7: Manufacturer: Azurewave
[    1.781618] usb 3-7: SerialNumber: NULL
[    1.952649] usb 3-8: new high-speed USB device number 4 using xhci_hcd
[    1.969057] usb 3-8: New USB device found, idVendor=0bda, idProduct=0139
[    1.969058] usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.969059] usb 3-8: Product: USB2.0-CRW
[    1.969060] usb 3-8: Manufacturer: Generic
[    1.969061] usb 3-8: SerialNumber: 20100201396000000
[    2.569213] Switched to clocksource tsc
[    2.781239] Console: switching to colour frame buffer device 240x67
[    2.784566] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.784567] i915 0000:00:02.0: registered panic notifier
[    2.785025] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    2.786504] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    2.787519] acpi device:6a: registered as cooling_device8
[    2.787546] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:5a/LNXVIDEO:00/input/input12
[    2.788563] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.789483] acpi device:7e: registered as cooling_device9
[    2.797315] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input13
[    2.797407] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.829335] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    3.346037] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    3.674123] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.714482] systemd-udevd[423]: starting version 204
[    3.819686] lp: driver loaded but no devices found
[    3.830804] ppdev: user-space parallel port driver
[    3.846880] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[    3.855898] wmi: Mapper loaded
[    3.879249] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \GPIS 1 (20131115/utaddress-251)
[    3.879255] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 2 (20131115/utaddress-251)
[    3.879259] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.879263] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    3.879266] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GP01 2 (20131115/utaddress-251)
[    3.879269] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 3 (20131115/utaddress-251)
[    3.879272] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPR_ 4 (20131115/utaddress-251)
[    3.879274] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.879276] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    3.879278] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GP01 2 (20131115/utaddress-251)
[    3.879281] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 3 (20131115/utaddress-251)
[    3.879284] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPR_ 4 (20131115/utaddress-251)
[    3.879286] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.879288] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.883078] mei_me 0000:00:16.0: irq 51 for MSI/MSI-X
[    3.896605] random: nonblocking pool is initialized
[    3.899354] nvidia: module license 'NVIDIA' taints kernel.
[    3.899358] Disabling lock debugging due to kernel taint
[    3.903614] cfg80211: Calling CRDA to update world regulatory domain
[    3.903890] Bluetooth: Core ver 2.17
[    3.903903] NET: Registered protocol family 31
[    3.903904] Bluetooth: HCI device and connection manager initialized
[    3.903911] Bluetooth: HCI socket layer initialized
[    3.903914] Bluetooth: L2CAP socket layer initialized
[    3.903917] Bluetooth: SCO socket layer initialized
[    3.909908] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    3.909910] Copyright(c) 2003-2013 Intel Corporation
[    3.910079] iwlwifi 0000:04:00.0: irq 52 for MSI/MSI-X
[    3.911047] usbcore: registered new interface driver btusb
[    3.913886] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    3.915563] input: PS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input11
[    3.918794] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
[    3.918800] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.32  Tue Aug  5 20:58:26 PDT 2014
[    3.923740] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.926464] Bluetooth: hci0: read Intel version: 370710018002030d00
[    3.927958] iwlwifi 0000:04:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    3.928113] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    3.931789] type=1400 audit(1411924452.765:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=563 comm="apparmor_parser"
[    3.931795] type=1400 audit(1411924452.765:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=563 comm="apparmor_parser"
[    3.931799] type=1400 audit(1411924452.765:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=563 comm="apparmor_parser"
[    3.932189] type=1400 audit(1411924452.765:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=563 comm="apparmor_parser"
[    3.932193] type=1400 audit(1411924452.765:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=563 comm="apparmor_parser"
[    3.932393] type=1400 audit(1411924452.765:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=563 comm="apparmor_parser"
[    3.947977] EXT4-fs (dm-2): mounted filesystem with ordered data mode. Opts: (null)
[    3.949293] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[    3.949825] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[    3.949877] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[    3.950103] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[    3.952021] Linux video capture interface: v2.00
[    3.952388] scsi5 : SCSI emulation for RTS5139 USB card reader
[    3.952568] scsi 5:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    3.952572] usbcore: registered new interface driver rts5139
[    3.958460] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    3.965226] asus_wmi: ASUS WMI generic driver loaded
[    3.971770] HDA driver get symbol successfully from i915 module
[    3.973018] asus_wmi: Initialization: 0x1
[    3.973048] asus_wmi: BIOS WMI version: 7.9
[    3.973085] asus_wmi: SFUN value: 0x6a0877
[    3.973966] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input14
[    3.974053] uvcvideo: Found UVC 1.00 device USB2.0 UVC HD Webcam (13d3:5188)
[    3.974207] snd_hda_intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[    3.978593] snd_hda_intel 0000:00:03.0: irq 54 for MSI/MSI-X
[    3.981685] cfg80211: World regulatory domain updated:
[    3.981688] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.981690] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.981691] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.981693] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.981694] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.981695] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.983260] asus_wmi: Backlight controlled by ACPI video driver
[    3.983704] input: USB2.0 UVC HD Webcam as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/input/input15
[    3.983792] usbcore: registered new interface driver uvcvideo
[    3.983794] USB Video Class driver (1.1.1)
[    3.988257] SKU: Nid=0x1d sku_cfg=0x40c00001
[    3.988259] SKU: port_connectivity=0x1
[    3.988259] SKU: enable_pcbeep=0x0
[    3.988260] SKU: check_sum=0x00000000
[    3.988261] SKU: customization=0x00000000
[    3.988261] SKU: external_amp=0x0
[    3.988262] SKU: platform_type=0x0
[    3.988262] SKU: swap=0x0
[    3.988263] SKU: override=0x1
[    3.988483] autoconfig: line_outs=2 (0x14/0x1a/0x0/0x0/0x0) type:speaker
[    3.988484]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.988485]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[    3.988486]    mono: mono_out=0x0
[    3.988486]    inputs:
[    3.988487]      Mic=0x1b
[    3.988488]      Internal Mic=0x12
[    3.988489] realtek: No valid SSID, checking pincfg 0x40c00001 for NID 0x1d
[    3.988490] realtek: Enabling init ASM_ID=0x0001 CODEC_ID=10ec0668
[    3.993269] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input18
[    3.993336] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input17
[    3.993407] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input16
[    3.993804] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input20
[    3.993856] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input19
[    4.047551] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    4.100016] init: failsafe main process (787) killed by TERM signal
[    4.115709] type=1400 audit(1411924452.949:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=896 comm="apparmor_parser"
[    4.115714] type=1400 audit(1411924452.949:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=896 comm="apparmor_parser"
[    4.115951] type=1400 audit(1411924452.949:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=896 comm="apparmor_parser"
[    4.132656] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    4.150056] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.238562] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.238564] Bluetooth: BNEP filters: protocol multicast
[    4.238573] Bluetooth: BNEP socket layer initialized
[    4.240922] Bluetooth: RFCOMM TTY layer initialized
[    4.240932] Bluetooth: RFCOMM socket layer initialized
[    4.240936] Bluetooth: RFCOMM ver 1.11
[    4.253804] init: cups main process (899) killed by HUP signal
[    4.253810] init: cups main process ended, respawning
[    4.401662] init: samba-ad-dc main process (1036) terminated with status 1
[    4.411150] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[    4.411424] iwlwifi 0000:04:00.0: L1 Disabled; Enabling L0S
[    4.423492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.423752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.468666] r8169 0000:05:00.0 eth0: link down
[    4.468713] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.468968] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.311962] Adding 4194300k swap on /dev/mapper/cryptswap.  Priority:-1 extents:1 across:4194300k SSFS
[    5.670995] bbswitch: version 0.8
[    5.671001] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    5.671005] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    5.671014] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[    5.671082] bbswitch: detected an Optimus _DSM function
[    5.671089] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    5.675524] [drm] Module unloaded
[    5.676529] bbswitch: disabling discrete graphics
[    5.676541] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[    5.691621] pci_raw_set_power_state: 108 callbacks suppressed
[    5.691626] pci 0000:01:00.0: Refused to change power state, currently in D0
[    5.863359] init: plymouth-upstart-bridge main process ended, respawning
[    5.866778] init: plymouth-upstart-bridge main process (1513) terminated with status 1
[    5.866785] init: plymouth-upstart-bridge main process ended, respawning
[    8.075749] wlan0: authenticate with 00:00:00:00:00:00
[    8.077787] wlan0: send auth to 00:00:00:00:00:00 (try 1/3)
[    8.182294] wlan0: send auth to 00:00:00:00:00:00 (try 2/3)
[    8.286372] wlan0: send auth to 00:00:00:00:00:00 (try 3/3)
[    8.393751] wlan0: authentication with 00:00:00:00:00:00 timed out
[    8.548147] wlan0: authenticate with 08:96:d7:e9:26:50
[    8.549696] wlan0: direct probe to 08:96:d7:e9:26:50 (try 1/3)
[    8.750751] wlan0: direct probe to 08:96:d7:e9:26:50 (try 2/3)
[    8.954912] wlan0: direct probe to 08:96:d7:e9:26:50 (try 3/3)
[    9.158416] wlan0: authentication with 08:96:d7:e9:26:50 timed out
[   12.846802] wlan0: authenticate with 08:96:d7:e9:26:50
[   12.848490] wlan0: direct probe to 08:96:d7:e9:26:50 (try 1/3)
[   13.050219] wlan0: direct probe to 08:96:d7:e9:26:50 (try 2/3)
[   13.255115] wlan0: direct probe to 08:96:d7:e9:26:50 (try 3/3)
[   13.457890] wlan0: authentication with 08:96:d7:e9:26:50 timed out
[   23.427392] wlan0: authenticate with 08:96:d7:e9:26:52
[   23.429187] wlan0: send auth to 08:96:d7:e9:26:52 (try 1/3)
[   23.430789] wlan0: authenticated
[   23.433888] wlan0: associate with 08:96:d7:e9:26:52 (try 1/3)
[   23.443857] wlan0: RX AssocResp from 08:96:d7:e9:26:52 (capab=0x411 status=0 aid=1)
[   23.444807] wlan0: associated
[   23.444834] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.444871] cfg80211: Calling CRDA for country: DE
[   23.446700] cfg80211: Regulatory domain changed to country: DE
[   23.446702] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.446704] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   23.446704] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   23.446705] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   23.446706] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   23.446707] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   23.508217] wlan0: Limiting TX power to 23 (23 - 0) dBm as advertised by 08:96:d7:e9:26:52
[   34.193781] type=1400 audit(1411924483.002:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2603 comm="apparmor_parser"
[   34.193786] type=1400 audit(1411924483.002:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2603 comm="apparmor_parser"
[   34.194018] type=1400 audit(1411924483.002:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2603 comm="apparmor_parser"

```
I am using Xubuntu 14.04 with the Kernel 3.13.0-36-generic.
What is wrong with that Touchpad? Any Help would be appreciated!

Cheers

---

### Post by andreas27 on 2014-09-28
Okay, little update:

i tried it with a Fedora-Livestick: Same Problem
Latest Ubuntu upstream kernel (3.17-rc6-utopic): Same Problem

Help!!! :)

Cheers

P.S.: I've seen that there are several threads around with almost the same problem an it seems to be kernel related (However, i'm no specialist :D). Moreover it seems like this problem occurs over and over again with different kernels...

---

### Post by G.Baskerville on 2014-12-09
did you solve the problem? i have a new asus a555ld with the same behaviour with xubuntu 14.04.
```
xinput:
&#9121; Virtual core pointer                       id=2   [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                 id=4   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                  id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                      id=3   [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                id=5   [slave  keyboard (3)]
    &#8627; Power Button                               id=6   [slave  keyboard (3)]
    &#8627; Video Bus                                  id=7   [slave  keyboard (3)]
    &#8627; Video Bus                                  id=8   [slave  keyboard (3)]
    &#8627; Sleep Button                               id=9   [slave  keyboard (3)]
    &#8627; USB Camera                                 id=10   [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                           id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard 

```

did you try this solution [http://ubuntuforums.org/showthread.php?t=2253069](http://ubuntuforums.org/showthread.php?t=2253069) ?
it doesn't work for me, but maybe it can help you.

p.s.
I found also this: [http://askubuntu.com/questions/470388/how-do-i-get-the-touchpad-working-on-an-asus-x450l](http://askubuntu.com/questions/470388/how-do-i-get-the-touchpad-working-on-an-asus-x450l)

---

### Post by Pilot6 on 2014-12-09
Please give output of

dmesg | grep pnp

If you have a Focaltech touchpad, the only option is to install a custom kernel with a driver. Until the driver is merged into mainline.

---

### Post by G.Baskerville on 2014-12-09
this is the output you asked me
```
dmesg | grep pnp
[    0.255177] pnp: PnP ACPI init
[    0.255366] pnp 00:01: [dma 4]
[    0.255383] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.255401] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.255505] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.255695] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.255874] pnp 00:09: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.255909] pnp 00:0a: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.256773] pnp: PnP ACPI: found 13 devices
```

---

### Post by Pilot6 on 2014-12-09
You have a Focaltech touchpad. You can try my kernel image.
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

Copy files to your home directory and run

sudo dpkg -i linux*.deb

---

### Post by G.Baskerville on 2014-12-09
it doesn't work...:(
the touchpad is still detected as a logitech ps/2 mouse:
```
xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB Camera                                  id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]


```

---

### Post by Pilot6 on 2014-12-09
That can't be. Did you reboot after installing?

---

### Post by G.Baskerville on 2014-12-09
yes I did. I checked also the expanded grub menù in order to load the correct kernel.

---

### Post by Pilot6 on 2014-12-09
You have FLT101 device. It must be detected. It may not work in some cases, but should be detected either way.
Give output

uname -a

---

### Post by Pilot6 on 2014-12-09
If you have 3.16.0-26... kernel and it still does not work, then there is another unknown problem with some models.

Try to add i8042.noloop=1 to /etc/default/grub in the line like this

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1"

and run

sudo update-grub

---

### Post by G.Baskerville on 2014-12-10
yeah! problem solved!

```
xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; GiGa HiD                                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; FocalTechPS/2 FocalTech FocalTech Touchpad    id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB Camera                                  id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]

```

your kernel wasn't working because of my fault. I previously installed wrong drivers for elantech touchpads and after removing them the focaltech touchpad began to work correctly. thank you!
you said that probably focaltech drivers have still to be merged into the kernel mainline and I found many similar problems on the net. do you know something about the kernel version that will include those drivers?

---

### Post by Pilot6 on 2014-12-10
That sounds good, that the driver works OK. Regarding the official commit.
Noone knows when it is applied. Probably in 3.19.

Anyway I will keep my build updated, and you can download debs from the same place.
Here is the source link.

[https://github.com/hanipouspilot/ubuntu-fixes/tree/pilot6](https://github.com/hanipouspilot/ubuntu-fixes/tree/pilot6)

---

### Post by G.Baskerville on 2014-12-10
thank you again!

---

### Post by ale14 on 2014-12-12
Hi, I have an Asus A555LD with the same touchpad FLT101:

```
dmesg | grep pnp
[    0.251878] pnp: PnP ACPI init
[    0.252291] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.252501] pnp 00:06: Plug and Play ACPI device, IDs FLT0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.252540] pnp 00:07: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.253509] pnp: PnP ACPI: found 11 devices

```

I followed your instructions and installed your custom kernel.
Rebooted:
```
uname -a
Linux zap 3.16.0-28-generic #37 SMP Thu Dec 11 13:43:10 MSK 2014 x86_64 x86_64 x86_64 GNU/Linux

```

but still no success:

```
xinput 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB Camera                                  id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```

I even tried to append "i8042.noloop=1" to grub while rebooting, but nothing changed.
What am I doing wrong?

---

### Post by Pilot6 on 2014-12-12
Did you install any elantech drivers or anything like that? The detect code is very simple and should always work.
You may try also to add "i8042.nomux=1 i8042.noloop=1" parameter.

---

### Post by ale14 on 2014-12-12
Yes you're right, and I'm an idiot!

Actually I tried to install elantech driver before, but I was sure to have them uninstalled when I found they didn't work. 
I was wrong: they were still there!
As soon as I finally removed them and rebooted (no extra parameter needed in grub) it worked perfectly!

Here are the steps I had to follow to completely remove elantech drivers, in case someone need them:

```
sudo dkms status

psmouse, elantech-x551c, 3.16.0-25-generic, x86_64: built
psmouse, elantech-x551c, 3.16.0-28-generic, x86_64: installed
```

I tried to unistall:

```
sudo dkms uninstall -m psmouse -v elantech-x551c

    [...]
    DKMS: uninstall completed.

```

but that wan't enough:

```
sudo dkms status

psmouse, elantech-x551c, 3.16.0-25-generic, x86_64: built
psmouse, elantech-x551c, 3.16.0-28-generic, x86_64: built
```

they must be [B]removed:

[/B]```
sudo dkms remove psmouse/elantech-x551c  --all

    [...]
    ------------------------------
    Deleting module version: elantech-x551c
    completely from the DKMS tree.
    ------------------------------
    Done.

```

After that I reinstalled your custom kernel:

```
sudo dpkg -i linux*.deb
```

and rebooted.

Problem solved.
Thank you!

---

### Post by Pilot6 on 2014-12-12
BTW, There are both Elantech and Focaltech drivers in my build.

---

### Post by Matias_Coca on 2015-02-27
Thanks Pilot6, works for me on asus x450L!

---

### Post by vbessa on 2015-04-07
Also worked for me (notebook Asus X450LD - Ubuntu 14.04). However, the system complained about some unmet dependencies, which was solved by running Package Manager (filter: broken). In addition, my keyboard stopped working properly, meaning no accent (also easy to correct: just add set proper keyboard language). Also, the 'right-click' now is a 'two-finger-click'; any area of the mouse pad is a 'left-click'.

Thanks a lot!

---

### Post by Skarv on 2015-05-06
Hello.
Got a "newer" Asus model here.
X200MA, more of a (modern) netbook.

Did try the stuff here, as I searched google. Added i8042.noloop=1 grub, installed the custom kernel by pilot6.
All good. This was with the stock harddrive, a slow 5400rpm.
I changed the harddrive, to a Intel 320 120GB. All good, installed xubuntu.

And now, this dosn't work. The same system, only the harddrive is "new". Kind of frustrating....

---

### Post by Pilot6 on 2015-05-06
Skarv,

You do not need [COLOR=#000000] i8042.noloop=1 for this model. I have exactly same netbook.
I think the problem is that you installed xubuntu with another kernel.
Give output of

uname -a
xinput
dmesg | grep pnp[/COLOR]

---

### Post by Skarv on 2015-05-06
Linux korpen 3.16.0-37-generic #49-Ubuntu SMP Wed Apr 29 20:38:03 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

> | Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 VGA UVC WebCam                       id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

> 
[    0.265683] pnp: PnP ACPI init
[    0.265800] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.266333] pnp 00:03: Plug and Play ACPI device, IDs FLT0102 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.266425] pnp 00:04: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.268369] pnp: PnP ACPI: found 6 devices

---

### Post by Pilot6 on 2015-05-06
OK. It is vanilla Ubuntu 3.16 kernel. The touchpad should not work with multitouch.
You have two options.
1. Install 3.19 kernel and download my dkms driver.
2. Install my kernel build.

The thing is that you updated your kernel, but my build was older. Systems boots always with latest kernel.
I plan to stop building images, because I made a dkms driver for kernel 3.19.
But the problem is that 3.19 kernel for Ubuntu 14.04 is not in official repositories. That's why it is not quite simple to install it from ppa.
Now I built the latest image. I hope it will be last, then you will be able to upgrade to 3.19 and install just the driver.

---

### Post by Skarv on 2015-05-06
So I did.

Before I threw out the stock harddrive.

I did,
i8042.noloop=1
dpkg -i yourkernel

And it worked. I installed my xubuntu from the same flashdrive. I did the same now... but yourkernel dosnt seem to installed then... hmm

Cursor is way to itchy now.

edit:

Okey, I'll try later tonight. Home with sick kid, and all the fun that brings :).

Thanks.

---

### Post by Pilot6 on 2015-05-06
So, remove i8042.noloop=1.
Then download my new images and install them.
Or just boot with my old image using grub menu.

My image is installed, but after you updated your system, it boots with a newer kernel. Is this clear now?
That is why I made that dkms driver. Using it you will not nead to reinstall kernels after each kernel update.

And your hard drive has nothing to do with it at all.

---

### Post by Joshmccullough on 2015-07-17
> **Pilot6 said:**
> You have a Focaltech touchpad. You can try my kernel image.
[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

Copy files to your home directory and run

sudo dpkg -i linux*.deb

I've got an ASUS X750JA laptop, same issue: touchpad only allows for the most basic of functions.  I'm running Linux Mint 17.1 - KDE, is there any reason this fix wouldn't work on my system?  I'd love to have full touchpad functionality, especially the ability to turn it off so my cat doesn't keep moving it when I'm working :)

---

### Post by Pilot6 on 2015-07-17
This a very old solution. I suggest removing that kernel.
And give output of

xinput
dmesg | grep pnp
uname -a
dkms status

Mint and DE is not related at all.

---

### Post by Joshmccullough on 2015-07-17
I'll do that when I get a moment, thanks for the assist/quick reply!

---

### Post by Joshmccullough on 2015-07-17
> **Pilot6 said:**
> This a very old solution. I suggest removing that kernel.
And give output of

xinput
dmesg | grep pnp
uname -a
dkms status

Mint and DE is not related at all.

**Xinput** results:

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                 id=13   [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Wireless Mouse          id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                      id=10   [slave  keyboard (3)]


**dmesg | grep pnp**

[    0.270998] pnp: PnP ACPI init
[    0.271020] pnp 00:00: [dma 4]
[    0.271030] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.271040] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.271107] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.271135] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.271235] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.271404] pnp 00:0a: Plug and Play ACPI device, IDs FLT0101 PNP0f13 (active)
[    0.271427] pnp 00:0b: Plug and Play ACPI device, IDs ATK3001 PNPc030 PNP0303 (active)
[    0.276564] pnp: PnP ACPI: found 15 devices


**uname -a**

Linux joshandkaren-X750JA 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


**dkms status**

vboxhost, 5.0.0, 3.13.0-37-generic, x86_64: installed
virtualbox-guest, 4.3.18, 3.13.0-37-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)

Hope any/all of this information is useful, thank you for any input and assistance!

---

### Post by Pilot6 on 2015-07-18
You have a Focaltech touchpad. If your distro is based on Ubuntu 14.04, then you can run

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install linux-generic-lts-vivid focaltech-dkms

then reboot.

Or manually install kernel 3.19 and focaltech-dkms package from that repository.

---

### Post by Joshmccullough on 2015-07-23
> **Pilot6 said:**
> You have a Focaltech touchpad. If your distro is based on Ubuntu 14.04, then you can run

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install linux-generic-lts-vivid focaltech-dkms

then reboot.

Or manually install kernel 3.19 and focaltech-dkms package from that repository.

You're a genius!!!!!!  It worked like a charm, now I've got a functional trackpad!!!!!!  Thank you so much for your help; I've been scouring the interwebz for a solution for so long, and now it just works!!!!!  :p

EDIT: For those who follow these instructions, you'll find the program 'Pointing devices' listed under Settings, this will allow you to adjust settings for the trackpad.  At least, this is where it showed up for me using Linux Mint 17.1 KDE.

---

### Post by Matias_Coca on 2015-08-19
Hello, thanks in advance.
I update to the kernel and stop working.

mati@inti:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech  USB WheelMouse                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 FocalTech FocalTech Touchpad in mouse emulation mode    id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627;             Logitech              Logitech Z205      id=11    [slave  keyboard (3)]
    &#8627; USB Camera                                  id=12    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

mati@inti:~$  dmesg | grep pnp
[    0.229696] pnp: PnP ACPI init
[    0.230113] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.230315] pnp 00:06: Plug and Play ACPI device, IDs FLT0102 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.230355] pnp 00:07: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.231237] pnp: PnP ACPI: found 10 devices
mati@inti:~$  uname -a
Linux inti 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:32 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
mati@inti:~$ dkms status
mati@inti:~$ 
Any idea?

---

### Post by Pilot6 on 2015-08-19
How did you install the driver? Something is wrong with your dkms.
I just upgraded to the same kernel and it built OK.
Re-install the driver from ppa.

---

### Post by Matias_Coca on 2015-08-19
I remove and install again from ppa the drivers and now
mati@inti:~$ dkms status
focaltech, 1.5: added
I reboot the system but still not working, any idea?

---

### Post by Pilot6 on 2015-08-20
How did you install from ppa? Which commands did you use?
It should not be "added" it should be "installed".

And give output of

ls /var/lib/dkms

---

### Post by Matias_Coca on 2015-08-20
> **Pilot6 said:**
> How did you install from ppa? Which commands did you use?
It should not be "added" it should be "installed".

And give output of

ls /var/lib/dkms
I install like this

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install focaltech-dkms

I re do all the step, and now works, I don't know why.
mati@inti:~$  ls /var/lib/dkms 
dkms_dbversion  focaltech  nvidia-355
mati@inti:~$  dkms status
focaltech, 1.5, 3.19.0-26-generic, x86_64: installed

Thanks!!!

---

### Post by mickmau5 on 2015-09-15
> **Pilot6 said:**
> You have a Focaltech touchpad. If your distro is based on Ubuntu 14.04, then you can run

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install linux-generic-lts-vivid focaltech-dkms

then reboot.

Or manually install kernel 3.19 and focaltech-dkms package from that repository.

Hello. 
Wow Pilot6 great help so far here.
I've also been having touchpad issues: double-finger scroll doesn't work and I am having an awful time trying to disable tap-to-click.
The regular System Settings GUI doesn't seem to effect my touchpad, and the "GPointing Device Settings" doesn't see it.
Anyways, I think this should help BUT I'm just hesitant to proceed with this suggestion because my kernel is different.
I'm running Mint 17.1 Cinnamon, v2.4.8, Kernel 3.13.0-37-generic.
Is this a safe installation?

---

### Post by Skarv on 2015-09-20
Great news, but, files can't not be found.

W: [http://ppa.launchpad.net/hanipouspilot/focaltech-dkms/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/hanipouspilot/focaltech-dkms/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found


W: [http://ppa.launchpad.net/hanipouspilot/focaltech-dkms/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/hanipouspilot/focaltech-dkms/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

edit:
Just realize I'm on 14.10, duh. This was for 14.04, right...

---

