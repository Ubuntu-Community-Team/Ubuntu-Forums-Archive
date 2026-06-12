---
title: "Ubuntu Processor Power State Management"
date: 2012-08-22
forum: Hardware
---

### Post by AoFhEkOl on 2012-08-22
Hello,

I have a problem with Ubuntu.  About 10 maybe 30 mins into using ubuntu it black screens and restarts.  This seems to be a bios bug (as i have been told by wildman), and this happened on windows too.  

```
tim@tim-desktop:~$ dmesg | grep -i acpi
[    0.000000]  BIOS-e820: 00000000bdf55000 - 00000000bdf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bdfe4000 - 00000000bdffd000 (ACPI data)
[    0.000000] ACPI: RSDP 000f6ad0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bdff70ab 0007C (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP bdfe8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bdfe9000 05A6F (v02 Intel  CANTIGA  06040000 INTL 20060608)
[    0.000000] ACPI: FACS bdf8efc0 00040
[    0.000000] ACPI: APIC bdffcd1e 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET bdffcd86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bdffcdbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: SLIX bdffcdfa 00176 (v01 Compal JHL00_90 06040000 TBD  00000001)
[    0.000000] ACPI: APIC bdffcf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bdffcfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: TCPA bdfef000 00032 (v00                 00000000      00000000)
[    0.000000] ACPI: SSDT bdfe7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bdfe6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bdfe5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.008786] ACPI: Core revision 20110623
[    0.153835] PM: Registering ACPI NVS region at bdf55000 (303104 bytes)
[    0.153835] ACPI: bus type pci registered
[    0.156992] ACPI: Added _OSI(Module Device)
[    0.156994] ACPI: Added _OSI(Processor Device)
[    0.156996] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.156998] ACPI: Added _OSI(Processor Aggregator Device)
[    0.158382] ACPI: EC: Look up EC in DSDT
[    0.161847] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.162198] ACPI: SSDT bdf1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.162532] ACPI: Dynamic OEM Table Load:
[    0.162535] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.162656] ACPI: SSDT bdf18620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.162973] ACPI: Dynamic OEM Table Load:
[    0.162976] ACPI: SSDT   (null) 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.224302] ACPI: SSDT bdf19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.224659] ACPI: Dynamic OEM Table Load:
[    0.224662] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.256143] ACPI: SSDT bdf19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.256479] ACPI: Dynamic OEM Table Load:
[    0.256482] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.280768] ACPI: Interpreter enabled
[    0.280768] ACPI: (supports S0 S3 S4 S5)
[    0.280768] ACPI: Using IOAPIC for interrupt routing
[    0.280859] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.322476] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.322623] ACPI: No dock devices found.
[    0.322630] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.322884] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.340262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.340415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.340460] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.340597] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.340652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.340685] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.340722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.340766]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.340769]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.340771] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.346395] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.346444] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.346491] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.346539] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.346588] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.346633] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.346678] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.346722] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.347258] PCI: Using ACPI for IRQ routing
[    0.360072] pnp: PnP ACPI init
[    0.360089] ACPI: bus type pnp registered
[    0.360493] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.360601] pnp 00:01: Plug and Play ACPI device, IDs ENE0100 (active)
[    0.360651] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.360782] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.360826] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.360950] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.360993] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.380123] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.380169] pnp 00:08: Plug and Play ACPI device, IDs SYN070b SYN0700 SYN0002 PNP0f13 (active)
[    0.380409] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.380492] pnp 00:0a: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    0.380605] pnp: PnP ACPI: found 11 devices
[    0.380606] ACPI: ACPI bus type pnp unregistered
[    0.380610] PnPBIOS: Disabled by ACPI PNP
[    0.459882] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.460081] ACPI: AC Adapter [ACAD] (on-line)
[    0.460213] ACPI: Lid Switch [LID0]
[    0.460256] ACPI: Power Button [PWRB]
[    0.460299] ACPI: Power Button [PWRF]
[    0.462290] ACPI: acpi_idle registered with cpuidle
[    0.480577] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.480585] ACPI: Battery Slot [BAT1] (battery present)
[    0.500299] ACPI: Battery Slot [BAT1] (battery present)
[   13.774610] acpi device:02: registered as cooling_device2
[   13.774736] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)

tim@tim-desktop:~$ dmesg | grep -i error
[   14.142360] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

tim@tim-desktop:~$ dmesg | grep -i warn
nothing
```


My solution on windows was to change the processor driver from the intel one to a processor driver that was in device manager. The difference between the two is this.

[COLOR="Blue"]"Processor" has no sleep states or power management, the "Intel Processor" uses the intelppm driver and allows full power state management. If switching to a processor driver that doesn't allow sleep states "fixes" things, it's likely there's a hardware issue in one (or more) of the CPU cores or L1 caches at that point.
[/COLOR]

In windows after this change the computer was fine, no problems putting it to sleep or hibernating it.

So, how can i do this on ubuntu?

---

### Post by AoFhEkOl on 2012-08-22
Bump

---

### Post by AoFhEkOl on 2012-08-30
No one?

---

### Post by ahallubuntu on 2012-08-30
More details are needed.  What kind of computer?  (Make/model?)  What's the exact CPU?  What version of Ubuntu?

---

### Post by AoFhEkOl on 2012-08-30
Specs 
Laptop - pcspecalist - enigma - compal
Intel processor dual core 2.53ghz p8700
ATI mobility radeon 512mb 4650
4.0gb ram
Khlb2 motherboard - compal
 
Ubuntu 12.04

---

### Post by Toz on 2012-08-30
> [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]

Out of curiosity, have you tried the "acpi_apic_instance=2" kernel parameter and did it make a difference?

---

### Post by AoFhEkOl on 2012-08-30
> **Toz said:**
> Out of curiosity, have you tried the "acpi_apic_instance=2" kernel parameter and did it make a difference?
 
Yeah I did, with no change

---

### Post by AoFhEkOl on 2012-08-30
Are there any other kernel boot commands I don't know about? What does acpi_apic_instance=2 do? Can I change it to =1?

---

### Post by Toz on 2012-08-30
As far as I know, some bioses provide multiple APIC/MADT tables (which it shouldn't really do). That kernel parameter instructs the system to use the other tables. The default is 0 which actually runs acpi_apic_instance=1, so there are no other options here.

Can you post back the contents of /var/log/dmesg after you boot with acpi_apic_instance=2, to see what the differences are?

Have you checked to see if there is a bios update available for your system?

---

### Post by AoFhEkOl on 2012-08-31
This is the dmesg file
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-10-generic (buildd@akateko) (gcc version 4.7.1 (Ubuntu/Linaro 4.7.1-6ubuntu1) ) #10-Ubuntu SMP Mon Aug 13 15:25:53 UTC 2012 (Ubuntu 3.5.0-10.10-generic 3.5.1)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d2000-0x00000000000d3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bdab0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bdab1000-0x00000000bdab6fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bdab7000-0x00000000bdbb4fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bdbb5000-0x00000000bdc0efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bdc0f000-0x00000000bdd07fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bdd08000-0x00000000bdf0efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bdf0f000-0x00000000bdf17fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bdf18000-0x00000000bdf1efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bdf1f000-0x00000000bdf54fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bdf55000-0x00000000bdf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bdf9f000-0x00000000bdfe3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bdfe4000-0x00000000bdffcfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bdffd000-0x00000000bdffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] ACPI: Shall use APIC/MADT table 2
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI:                  /KHLB2, BIOS 1.05 09/16/2009
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 4GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] total RAM covered: 4096M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64K 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.000000] found SMP MP-table at [mem 0x000f6b80-0x000f6b8f] mapped at [c00f6b80]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x7f02e000-0x7fffefff]
[    0.000000] Allocated new RAMDISK: [mem 0x36c2d000-0x37bfd91b]
[    0.000000] Move RAMDISK from [mem 0x7f02e000-0x7fffe91b] to [mem 0x36c2d000-0x37bfd91b]
[    0.000000] ACPI: RSDP 000f6ad0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bdff70b9 0007C (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP bdfe8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bdfe9000 05A61 (v02 Intel  CANTIGA  06040000 INTL 20060608)
[    0.000000] ACPI: FACS bdf8efc0 00040
[    0.000000] ACPI: APIC bdffcd1e 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET bdffcd86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bdffcdbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: SLIX bdffcdfa 00176 (v01 Compal JHL00_90 06040000 TBD  00000001)
[    0.000000] ACPI: APIC bdffcf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bdffcfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: TCPA bdfef000 00032 (v00                 00000000      00000000)
[    0.000000] ACPI: SSDT bdfe7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bdfe6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bdfe5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 2
[    0.000000] ACPI: If "acpi_apic_instance=0" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4228MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xbdab0fff]
[    0.000000]   node   0: [mem 0xbdab7000-0xbdbb4fff]
[    0.000000]   node   0: [mem 0xbdc0f000-0xbdd07fff]
[    0.000000]   node   0: [mem 0xbdf0f000-0xbdf17fff]
[    0.000000]   node   0: [mem 0xbdf1f000-0xbdf54fff]
[    0.000000]   node   0: [mem 0xbdf9f000-0xbdfe3fff]
[    0.000000]   node   0: [mem 0xbdffd000-0xbdffffff]
[    0.000000]   node   0: [mem 0x00000000-0x3fffffff]
[    0.000000] On node 0 totalpages: 1039548
[    0.000000] free_area_init_node: node 0, pgdat c18a0540, node_mem_map f442c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8457 pages used for memmap
[    0.000000]   HighMem zone: 802856 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0xbe000000-0xffffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f43fe000 s34112 r0 d23232 u57344
[    0.000000] pcpu-alloc: s34112 r0 d23232 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1029307
[    0.000000] Kernel command line: initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash acpi_apic_instance=2 BOOT_IMAGE=/casper/vmlinuz 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled
 xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 10485632 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00140000)
[    0.000000] Memory: 4079200k/5242880k available (5951k kernel code, 78992k reserved, 2932k data, 752k init, 3245252k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc18ae000 - 0xc196a000   ( 752 kB)
[    0.000000]       .data : 0xc15cffd8 - 0xc18ad2c0   (2932 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15cffd8   (5951 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3408000 soft=f340a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2526.774 MHz processor.
[    0.004001] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.54 BogoMIPS (lpj=10107096)
[    0.004004] pid_max: default: 32768 minimum: 301
[    0.004024] Security Framework initialized
[    0.004036] AppArmor: AppArmor initialized
[    0.004037] Yama: becoming mindful.
[    0.004078] Mount-cache hash table entries: 512
[    0.004263] Initializing cgroup subsys cpuacct
[    0.004265] Initializing cgroup subsys memory
[    0.004271] Initializing cgroup subsys devices
[    0.004273] Initializing cgroup subsys freezer
[    0.004274] Initializing cgroup subsys blkio
[    0.004276] Initializing cgroup subsys perf_event
[    0.004301] CPU: Physical Processor ID: 0
[    0.004302] CPU: Processor Core ID: 0
[    0.004305] mce: CPU supports 6 MCE banks
[    0.004311] CPU0: Thermal monitoring enabled (TM2)
[    0.004313] using mwait in idle threads.
[    0.006269] ACPI: Core revision 20120320
[    0.012010] ftrace: allocating 24565 entries in 48 pages
[    0.024050] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024423] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067229] CPU0: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.068003] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.068003] CPU 1 irqstacks, hard=f34e2000 soft=f34e4000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.076061] Brought up 2 CPUs
[    0.076065] Total of 2 processors activated (10107.09 BogoMIPS).
[    0.077821] devtmpfs: initialized
[    0.077821] EVM: security.selinux
[    0.077821] EVM: security.SMACK64
[    0.077821] EVM: security.capability
[    0.077821] PM: Registering ACPI NVS region [mem 0xbdf55000-0xbdf9efff] (303104 bytes)
[    0.080429] dummy: 
[    0.080458] RTC time:  7:39:23, date: 08/31/12
[    0.080495] NET: Registered protocol family 16
[    0.080505] Trying to unpack rootfs image as initramfs...
[    0.080657] EISA bus registered
[    0.080755] ACPI: bus type pci registered
[    0.080814] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.080816] PCI: not using MMCONFIG
[    0.080970] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
[    0.081183] PCI: PCI BIOS revision 3.00 entry at 0xfde01, last bus=38
[    0.081184] PCI: Using configuration type 1 for base access
[    0.276112] bio: create slab <bio-0> at 0
[    0.276213] ACPI: Added _OSI(Module Device)
[    0.276215] ACPI: Added _OSI(Processor Device)
[    0.276217] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.276219] ACPI: Added _OSI(Processor Aggregator Device)
[    0.277616] ACPI: EC: Look up EC in DSDT
[    0.281070] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.281409] ACPI: SSDT bdf1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.281755] ACPI: Dynamic OEM Table Load:
[    0.281757] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.281876] ACPI: SSDT bdf18620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.282206] ACPI: Dynamic OEM Table Load:
[    0.282209] ACPI: SSDT   (null) 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    3.120507] ACPI: SSDT bdf19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    3.120883] ACPI: Dynamic OEM Table Load:
[    3.120886] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    3.137063] Freeing initrd memory: 16196k freed
[    3.148331] ACPI: SSDT bdf19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    3.148680] ACPI: Dynamic OEM Table Load:
[    3.148683] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    3.148702] ACPI: Interpreter enabled
[    3.148702] ACPI: (supports S0 S3 S4 S5)
[    3.148702] ACPI: Using IOAPIC for interrupt routing
[    3.148702] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    3.149050] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    3.149052] PCI: Using MMCONFIG for extended config space
[    3.194422] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    3.194570] ACPI: No dock devices found.
[    3.194575] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    3.194831] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    3.195295] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    3.195297] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    3.195300] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    3.195302] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    3.195304] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    3.195307] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    3.195309] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    3.195340] PCI host bridge to bus 0000:00
[    3.195343] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    3.195345] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    3.195347] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    3.195349] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    3.195351] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    3.195353] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    3.195355] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff]
[    3.195368] pci 0000:00:00.0: [8086:2a40] type 00 class 0x060000
[    3.195390] DMAR: Forcing write-buffer flush capability
[    3.195391] DMAR: Disabling IOMMU for graphics on this chipset
[    3.195417] pci 0000:00:01.0: [8086:2a41] type 01 class 0x060400
[    3.195459] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    3.195509] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    3.195565] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    3.195633] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    3.195688] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    3.195752] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
[    3.195806] pci 0000:00:1a.2: reg 20: [io  0x1840-0x185f]
[    3.195882] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    3.195908] pci 0000:00:1a.7: reg 10: [mem 0xf2504800-0xf2504bff]
[    3.196019] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    3.196051] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    3.196070] pci 0000:00:1b.0: reg 10: [mem 0xf2500000-0xf2503fff 64bit]
[    3.196160] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    3.196187] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    3.196283] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    3.196314] pci 0000:00:1c.2: [8086:2944] type 01 class 0x060400
[    3.196405] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    3.196434] pci 0000:00:1c.3: [8086:2946] type 01 class 0x060400
[    3.196527] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    3.196555] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
[    3.196647] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    3.196680] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    3.196734] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    3.196798] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    3.196853] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    3.196918] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    3.196972] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    3.197048] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    3.197073] pci 0000:00:1d.7: reg 10: [mem 0xf2504c00-0xf2504fff]
[    3.197185] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    3.197211] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    3.197291] pci 0000:00:1f.0: [8086:2919]
 type 00 class 0x060100
[    3.197421] pci 0000:00:1f.2: [8086:2929] type 00 class 0x010601
[    3.197445] pci 0000:00:1f.2: reg 10: [io  0x18f0-0x18f7]
[    3.197455] pci 0000:00:1f.2: reg 14: [io  0x18e4-0x18e7]
[    3.197465] pci 0000:00:1f.2: reg 18: [io  0x18e8-0x18ef]
[    3.197474] pci 0000:00:1f.2: reg 1c: [io  0x18e0-0x18e3]
[    3.197484] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18df]
[    3.197494] pci 0000:00:1f.2: reg 24: [mem 0xf2504000-0xf25047ff]
[    3.197555] pci 0000:00:1f.2: PME# supported from D3hot
[    3.197578] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    3.197597] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff 64bit]
[    3.197623] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    3.197697] pci 0000:01:00.0: [1002:9480] type 00 class 0x030000
[    3.197713] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    3.197724] pci 0000:01:00.0: reg 14: [io  0x2000-0x20ff]
[    3.197735] pci 0000:01:00.0: reg 18: [mem 0xcfef0000-0xcfefffff]
[    3.197773] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    3.197824] pci 0000:01:00.0: supports D1 D2
[    3.197853] pci 0000:01:00.1: [1002:aa38] type 00 class 0x040300
[    3.197869] pci 0000:01:00.1: reg 10: [mem 0xcfeec000-0xcfeeffff]
[    3.197974] pci 0000:01:00.1: supports D1 D2
[    3.198018] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    3.198021] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    3.198025] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    3.198029] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.198099] pci 0000:02:00.0: [197b:2382] type 00 class 0x088000
[    3.198121] pci 0000:02:00.0: reg 10: [mem 0xf2100000-0xf21000ff]
[    3.198204] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    3.198320] pci 0000:02:00.2: [197b:2381] type 00 class 0x080501
[    3.198342] pci 0000:02:00.2: reg 10: [mem 0xf2100400-0xf21004ff]
[    3.198535] pci 0000:02:00.3: [197b:2383] type 00 class 0x088000
[    3.198556] pci 0000:02:00.3: reg 10: [mem 0xf2100800-0xf21008ff]
[    3.204218] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    3.204226] pci 0000:00:1c.0:   bridge window [mem 0xf2100000-0xf21fffff]
[    3.204308] pci 0000:0e:00.0: [168c:001c] type 00 class 0x020000
[    3.204337] pci 0000:0e:00.0: reg 10: [mem 0xf2200000-0xf220ffff 64bit]
[    3.204477] pci 0000:0e:00.0: PME# supported from D3hot
[    3.204510] pci 0000:0e:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    3.204521] pci 0000:00:1c.2: PCI bridge to [bus 0e-0e]
[    3.204528] pci 0000:00:1c.2:   bridge window [mem 0xf2200000-0xf22fffff]
[    3.204605] pci 0000:14:00.0: [10ec:8168] type 00 class 0x020000
[    3.204625] pci 0000:14:00.0: reg 10: [io  0x3000-0x30ff]
[    3.204659] pci 0000:14:00.0: reg 18: [mem 0xf2010000-0xf2010fff 64bit pref]
[    3.204680] pci 0000:14:00.0: reg 20: [mem 0xf2000000-0xf200ffff 64bit pref]
[    3.204695] pci 0000:14:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    3.204771] pci 0000:14:00.0: supports D1 D2
[    3.204773] pci 0000:14:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    3.212216] pci 0000:00:1c.3: PCI bridge to [bus 14-14]
[    3.212221] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    3.212229] pci 0000:00:1c.3:   bridge window [mem 0xf2000000-0xf20fffff 64bit pref]
[    3.212281] pci 0000:00:1c.4: PCI bridge to [bus 1a-1b]
[    3.212285] pci 0000:00:1c.4:   bridge window [io  0x4000-0x4fff]
[    3.212289] pci 0000:00:1c.4:   bridge window [mem 0xf4000000-0xf5ffffff]
[    3.212296] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    3.212366] pci 0000:00:1e.0: PCI bridge to [bus 26-26] (subtractive decode)
[    3.212378] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    3.212380] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    3.212383] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    3.212385] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    3.212387] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    3.212389] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    3.212391] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    3.212420] pci_bus 0000:00: on NUMA node 0
[    3.212423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    3.212550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    3.212589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    3.212717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    3.212769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    3.212800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    3.212836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    3.212878]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    3.212881]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    3.212882] ACPI _OSC control for PCIe not granted, disabling ASPM
[    3.218106] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    3.218154] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    3.218200] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    3.218244] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    3.218291] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    3.218338] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    3.218382] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    3.218428] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    3.218497] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    3.218497] vgaarb: loaded
[    3.218497] vgaarb: bridge control possible 0000:01:00.0
[    3.218497] SCSI subsystem initialized
[    3.218497] libata version 3.00 loaded.
[    3.218497] ACPI: bus type usb registered
[    3.218497] usbcore: registered new interface driver usbfs
[    3.218497] usbcore: registered new interface driver hub
[    3.218497] usbcore: registered new device driver usb
[    3.218497] PCI: Using ACPI for IRQ routing
[    3.218497] PCI: pci_cache_line_size set to 64 bytes
[    3.218497] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
[    3.218497] e820: reserve RAM buffer [mem 0xbdab1000-0xbfffffff]
[    3.218497] e820: reserve RAM buffer [mem 0xbdbb5000-0xbfffffff]
[    3.218497] e820: reserve RAM buffer [mem 0xbdd08000-0xbfffffff]
[    3.218497] e820: reserve RAM buffer [mem 0xbdf18000-0xbfffffff]
[    3.218497] e820: reserve RAM buffer [mem 0xbdf55000-0xbfffffff]
[    3.218497] e820: reserve RAM buffer [mem 0xbdfe4000-0xbfffffff]
[    3.218497] e820: reserve RAM buffer [mem 0xbe000000-0xbfffffff]
[    3.218497] NetLabel: Initializing
[    3.218497] NetLabel:  domain hash size = 128
[    3.218497] NetLabel:  protocols = UNLABELED CIPSOv4
[    3.218497] NetLabel:  unlabeled traffic allowed by default
[    3.218497] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    3.218497] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    3.218497] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    3.224217] Switching to clocksource hpet
[    3.231669] AppArmor: AppArmor Filesystem Enabled
[    3.231693] pnp: PnP ACPI init
[    3.231709] ACPI: bus type pnp registered
[    3.231995] pnp 00:00: [bus 00-ff]
[    3.232011] pnp 00:00: [io  0x0000-0x0cf7 window]
[    3.232013] pnp 00:00: [io  0x0cf8-0x0cff]
[    3.232015] pnp 00:00: [io  0x0d00-0xffff window]
[    3.232017] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    3.232019] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    3.232021] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    3.232023] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    3.232025] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    3.232027] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    3.232029] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    3.232031] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    3.232033] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    3.232035] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    3.232038] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    3.232040] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    3.232042] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    3.232044] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    3.232046] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    3.232048] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    3.232104] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    3.232163] pnp 00:01: [io  0x0000-0x001f]
[    3.232165] pnp 00:01: [io  0x0081-0x0091]
[    3.232167] pnp 00:01: [io  0x0093-0x009f]
[    3.232169] pnp 00:01: [io  0x00c0-0x00df]
[    3.232171] pnp 00:01: [dma 4]
[    3.232197] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    3.232261] pnp 00:02: [mem 0xfed00000-0xfed003ff]
[    3.232317] system 00:02: [mem 0xfed00000-0xfed003ff] has been reserved
[    3.232321] system 00:02: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    3.232331] pnp 00:03: [io  0x00f0]
[    3.232342] pnp 00:03: [irq 13]
[    3.232368] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    3.232379] pnp 00:04: [io  0x002e-0x002f]
[    3.232382] pnp 00:04: [io  0x004e-0x004f]
[    3.232383] pnp 00:04: [io  0x0061]
[    3.232385] pnp 00:04: [io  0x0063]
[    3.232387] pnp 00:04: [io  0x0065]
[    3.232389] pnp 00:04: [io  0x0067]
[    3.232390] pnp 00:04: [io  0x0068]
[    3.232392] pnp 00:04: [io  0x006c]
[    3.232394] pnp 00:04: [io  0x0070]
[    3.232396] pnp 00:04: [io  0x0080]
[    3.232398] pnp 00:04:
 [io  0x0092]
[    3.232399] pnp 00:04: [io  0x00b2-0x00b3]
[    3.232402] pnp 00:04: [io  0x0400-0x047f]
[    3.232403] pnp 00:04: [io  0x0480-0x048f]
[    3.232405] pnp 00:04: [io  0xffff]
[    3.232407] pnp 00:04: [io  0xffff]
[    3.232409] pnp 00:04: [io  0x1000-0x107f]
[    3.232411] pnp 00:04: [io  0x1180-0x11ff]
[    3.232413] pnp 00:04: [io  0xfe00]
[    3.232470] system 00:04: [io  0x0400-0x047f] has been reserved
[    3.232473] system 00:04: [io  0x0480-0x048f] has been reserved
[    3.232475] system 00:04: [io  0xffff] has been reserved
[    3.232478] system 00:04: [io  0xffff] has been reserved
[    3.232480] system 00:04: [io  0x1000-0x107f] has been reserved
[    3.232482] system 00:04: [io  0x1180-0x11ff] has been reserved
[    3.232485] system 00:04: [io  0xfe00] has been reserved
[    3.232488] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.232496] pnp 00:05: [io  0x0070-0x0077]
[    3.232501] pnp 00:05: [irq 8]
[    3.232527] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    3.252029] pnp 00:06: [io  0x0060]
[    3.252032] pnp 00:06: [io  0x0064]
[    3.252037] pnp 00:06: [irq 1]
[    3.252069] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    3.252080] pnp 00:07: [irq 12]
[    3.252109] pnp 00:07: Plug and Play ACPI device, IDs SYN070b SYN0700 SYN0002 PNP0f13 (active)
[    3.252220] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    3.252223] pnp 00:08: [mem 0xfed10000-0xfed13fff]
[    3.252225] pnp 00:08: [mem 0xfed18000-0xfed18fff]
[    3.252227] pnp 00:08: [mem 0xfed19000-0xfed19fff]
[    3.252229] pnp 00:08: [mem 0xe0000000-0xefffffff]
[    3.252230] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    3.252232] pnp 00:08: [mem 0xfed40000-0xfed44fff]
[    3.252234] pnp 00:08: [mem 0xfed45000-0xfed8ffff]
[    3.252293] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    3.252296] system 00:08: [mem 0xfed10000-0xfed13fff] has been reserved
[    3.252298] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    3.252301] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    3.252303] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    3.252306] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    3.252308] system 00:08: [mem 0xfed40000-0xfed44fff] has been reserved
[    3.252311] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    3.252314] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.252349] pnp 00:09: [mem 0xfed40000-0xfed44fff]
[    3.252390] pnp 00:09: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    3.252501] pnp: PnP ACPI: found 10 devices
[    3.252502] ACPI: ACPI bus type pnp unregistered
[    3.252505] PnPBIOS: Disabled by ACPI PNP
[    3.289003] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02-02] add_size 1000
[    3.289007] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x001fffff pref] to [bus 02-02] add_size 200000
[    3.289017] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 0e-0e] add_size 1000
[    3.289020] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0e-0e] add_size 200000
[    3.289030] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x001fffff] to [bus 14-14] add_size 400000
[    3.289051] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x001fffff pref] get_res_add_size add_size 200000
[    3.289054] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    3.289056] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x001fffff] get_res_add_size add_size 400000
[    3.289058] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    3.289060] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    3.289066] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc02fffff pref]
[    3.289070] pci 0000:00:1c.2: BAR 15: assigned [mem 0xc0300000-0xc04fffff 64bit pref]
[    3.289073] pci 0000:00:1c.3: BAR 14: assigned [mem 0xc0500000-0xc09fffff]
[    3.289077] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    3.289080] pci 0000:00:1c.2: BAR 13: assigned [io  0x6000-0x6fff]
[    3.289083] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0a00000-0xc0a000ff 64bit]
[    3.289092] pci 0000:01:00.0: BAR 6: assigned [mem 0xcfe00000-0xcfe1ffff pref]
[    3.289094] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    3.289097] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    3.289101] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    3.289104] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.289109] pci 0000:02:00.0: BAR 6: assigned [mem 0xc0000000-0xc000ffff pref]
[    3.289111] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    3.289114] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    3.289119] pci 0000:00:1c.0:   bridge window [mem 0xf2100000-0xf21fffff]
[    3.289124] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc02fffff pref]
[    3.289130] pci 0000:00:1c.2: PCI bridge to [bus 0e-0e]
[    3.289133] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    3.289138] pci 0000:00:1c.2:   bridge window [mem 0xf2200000-0xf22fffff]
[    3.289143] pci 0000:00:1c.2:   bridge window [mem 0xc0300000-0xc04fffff 64bit pref]
[    3.289150] pci 0000:14:00.0: BAR 6: assigned [mem 0xf2020000-0xf202ffff pref]
[    3.289152] pci 0000:00:1c.3: PCI bridge to [bus 14-14]
[    3.289155] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    3.289160] pci 0000:00:1c.3:   bridge window [mem 0xc0500000-0xc09fffff]
[    3.289164] pci 0000:00:1c.3:   bridge window [mem 0xf2000000-0xf20fffff 64bit pref]
[    3.289171] pci 0000:00:1c.4: PCI bridge to [bus 1a-1b]
[    3.289174] pci 0000:00:1c.4:   bridge window [io  0x4000-0x4fff]
[    3.289179] pci 0000:00:1c.4:   bridge window [mem 0xf4000000-0xf5ffffff]
[    3.289183] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    3.289190] pci 0000:00:1e.0: PCI bridge to [bus 26-26]
[    3.289240] pci 0000:00:1e.0: setting latency timer to 64
[    3.289244] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    3.289246] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    3.289248] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    3.289250] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    3.289252] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    3.289254] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    3.289256] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xfebfffff]
[    3.289258] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    3.289260] pci_bus 0000:01: resource 1 [mem 0xcfe00000-0xcfefffff]
[    3.289262] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.289265] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    3.289267] pci_bus 0000:02: resource 1 [mem 0xf2100000-0xf21fffff]
[    3.289269] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc02fffff pref]
[    3.289271] pci_bus 0000:0e: resource 0 [io  0x6000-0x6fff]
[    3.289273] pci_bus 0000:0e: resource 1 [mem 0xf2200000-0xf22fffff]
[    3.289275] pci_bus 0000:0e: resource 2 [mem 0xc0300000-0xc04fffff 64bit pref]
[    3.289277] pci_bus 0000:14: resource 0 [io  0x3000-0x3fff]
[    3.289279] pci_bus 0000:14: resource 1 [mem 0xc0500000-0xc09fffff]
[    3.289281] pci_bus 0000:14: resource 2 [mem 0xf2000000-0xf20fffff 64bit pref]
[    3.289283] pci_bus 0000:1a: resource 0 [io  0x4000-0x4fff]
[    3.289285] pci_bus 0000:1a: resource 1 [mem 0xf4000000-0xf5ffffff]
[    3.289287] pci_bus 0000:1a: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    3.289289] pci_bus 0000:26: resource 4 [io  0x0000-0x0cf7]
[    3.289291] pci_bus 0000:26: resource 5 [io  0x0d00-0xffff]
[    3.289293] pci_bus 0000:26: resource 6 [mem 0x000a0000-0x000bffff]
[    3.289295] pci_bus 0000:26: resource 7 [mem 0x000d4000-0x000d7fff]
[    3.289297] pci_bus 0000:26: resource 8 [mem 0x000d8000-0x000dbfff]
[    3.289299] pci_bus 0000:26: resource 9 [mem 0x000dc000-0x000dffff]
[    3.289301] pci_bus 0000:26: resource 10 [mem 0xc0000000-0xfebfffff]
[    3.289328] NET: Registered protocol family 2
[    3.289379] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    3.289509] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    3.289896] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    3.290076] TCP: Hash tables configured (established 131072 bind 65536)
[    3.290078] TCP: reno registered
[    3.290080] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    3.290088] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    3.290136] NET: Registered protocol family 1
[    3.290351] pci 0000:01:00.0: Boot video device
[    3.290372] PCI: CLS 64 bytes, default 64
[    3.290455] Simple Boot Flag at 0x36 set to 0x1
[    3.290752] audit: initializing netlink socket (disabled)
[    3.290759] type=2000 audit(1346398765.284:1): initialized
[    3.310153] highmem bounce pool size: 64 pages
[    3.310165] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.312087] VFS: Disk quotas dquot_6.5.2
[    3.312131] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.312625] fuse init (API version 7.19)
[    3.312705] msgmni has been set to 1660
[    3.313049] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    3.313072] io scheduler noop registered
[    3.313074] io scheduler deadline registered (default)
[    3.313081] io scheduler cfq registered
[    3.313209] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    3.313298] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    3.313402] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    3.313508] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    3.313612] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    3.313693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.313713]
 pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.313768] intel_idle: does not run on family 6 model 23
[    3.314167] ACPI: AC Adapter [ACAD] (on-line)
[    3.314255] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    3.314272] ACPI: Lid Switch [LID0]
[    3.314308] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    3.314311] ACPI: Power Button [PWRB]
[    3.314346] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    3.314349] ACPI: Power Button [PWRF]
[    3.314416] ACPI: Requesting acpi_cpufreq
[    3.317363] Monitor-Mwait will be used to enter C-1 state
[    3.317399] Monitor-Mwait will be used to enter C-2 state
[    3.317426] Monitor-Mwait will be used to enter C-3 state
[    3.317432] Marking TSC unstable due to TSC halts in idle
[    3.317444] ACPI: acpi_idle registered with cpuidle
[    3.356579] ACPI: Battery Slot [BAT1] (battery present)
[    3.356605] GHES: HEST is not enabled!
[    3.356645] isapnp: Scanning for PnP cards...
[    3.356681] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.357744] Linux agpgart interface v0.103
[    3.359124] brd: module loaded
[    3.359741] loop: module loaded
[    3.359836] ahci 0000:00:1f.2: version 3.0
[    3.359883] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    3.359925] ahci: SSS flag set, parallel bus scan disabled
[    3.359954] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    3.359957] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems 
[    3.359961] ahci 0000:00:1f.2: setting latency timer to 64
[    3.376293] ACPI: Battery Slot [BAT1] (battery present)
[    3.384460] scsi0 : ahci
[    3.384520] scsi1 : ahci
[    3.384575] scsi2 : ahci
[    3.384629] scsi3 : ahci
[    3.384681] scsi4 : ahci
[    3.384732] scsi5 : ahci
[    3.384777] ata1: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504100 irq 45
[    3.384779] ata2: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504180 irq 45
[    3.384781] ata3: DUMMY
[    3.384782] ata4: DUMMY
[    3.384784] ata5: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504300 irq 45
[    3.384786] ata6: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504380 irq 45
[    3.385083] Fixed MDIO Bus: probed
[    3.385125] tun: Universal TUN/TAP device driver, 1.6
[    3.385127] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.385185] PPP generic driver version 2.4.2
[    3.385223] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.385252] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.385255] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.385261] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.385286] ehci_hcd 0000:00:1a.7: debug port 1
[    3.389174] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    3.389188] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf2504800
[    3.400013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.400032] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.400034] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.400036] usb usb1: Product: EHCI Host Controller
[    3.400038] usb usb1: Manufacturer: Linux 3.5.0-10-generic ehci_hcd
[    3.400040] usb usb1: SerialNumber: 0000:00:1a.7
[    3.400131] hub 1-0:1.0: USB hub found
[    3.400135] hub 1-0:1.0: 6 ports detected
[    3.400215] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.400219] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.400223] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.400245] ehci_hcd 0000:00:1d.7: debug port 1
[    3.404128] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    3.404144] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf2504c00
[    3.416014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.416040] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    3.416042] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.416044] usb usb2: Product: EHCI Host Controller
[    3.416046] usb usb2: Manufacturer: Linux 3.5.0-10-generic ehci_hcd
[    3.416048] usb usb2: SerialNumber: 0000:00:1d.7
[    3.416136] hub 2-0:1.0: USB hub found
[    3.416139] hub 2-0:1.0: 6 ports detected
[    3.416206] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.416222] uhci_hcd: USB Universal Host Controller Interface driver
[    3.416240] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.416243] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.416247] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.416278] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    3.416307] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    3.416310] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.416312] usb usb3: Product: UHCI Host Controller
[    3.416314] usb usb3: Manufacturer: Linux 3.5.0-10-generic uhci_hcd
[    3.416315] usb usb3: SerialNumber: 0000:00:1a.0
[    3.416403] hub 3-0:1.0: USB hub found
[    3.416407] hub 3-0:1.0: 2 ports detected
[    3.416469] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.416473] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.416477] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.416507] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    3.416535] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    3.416537] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.416539] usb usb4: Product: UHCI Host Controller
[    3.416541] usb usb4: Manufacturer: Linux 3.5.0-10-generic uhci_hcd
[    3.416543] usb usb4: SerialNumber: 0000:00:1a.1
[    3.416614] hub 4-0:1.0: USB hub found
[    3.416617] hub 4-0:1.0: 2 ports detected
[    3.416678] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.416681] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.416685] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.416707] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    3.416733] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    3.416735] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.416737] usb usb5: Product: UHCI Host Controller
[    3.416739] usb usb5: Manufacturer: Linux 3.5.0-10-generic uhci_hcd
[    3.416741] usb usb5: SerialNumber: 0000:00:1a.2
[    3.416811] hub 5-0:1.0: USB hub found
[    3.416814] hub 5-0:1.0: 2 ports detected
[    3.416877] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.416880] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.416884] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.416905] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    3.416931] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    3.416933] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.416935] usb usb6: Product: UHCI Host Controller
[    3.416937] usb usb6: Manufacturer: Linux 3.5.0-10-generic uhci_hcd
[    3.416939] usb usb6: SerialNumber: 0000:00:1d.0
[    3.417023] hub 6-0:1.0: USB hub found
[    3.417026] hub 6-0:1.0: 2 ports detected
[    3.417090] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.417093] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.417097] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.417119] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    3.417145] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    3.417147] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.417149] usb usb7: Product: UHCI Host Controller
[    3.417151] usb usb7: Manufacturer: Linux 3.5.0-10-generic uhci_hcd
[    3.417153] usb usb7: SerialNumber: 0000:00:1d.1
[    3.417224] hub 7-0:1.0: USB hub found
[    3.417227] hub 7-0:1.0: 2 ports detected
[    3.417288] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.417291] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.417295] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.417325] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    3.417353] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    3.417355] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.417357] usb usb8: Product: UHCI Host Controller
[    3.417359] usb usb8: Manufacturer: Linux 3.5.0-10-generic uhci_hcd
[    3.417361] usb usb8: SerialNumber: 0000:00:1d.2
[    3.417432] hub 8-0:1.0: USB hub found
[    3.417435] hub 8-0:1.0: 2 ports detected
[    3.417545] usbcore: registered new interface driver libusual
[    3.417587] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.447331] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.447335] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.447421] mousedev: PS/2 mouse device common for all mice
[    3.449467] rtc_cmos 00:05: RTC can wake from S4
[    3.449569] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.449593] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.449637] device-mapper: uevent: version 1.0.3
[    3.449687] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    3.449714] EISA: Probing bus 0 at eisa.0
[    3.449716] EISA: Cannot allocate resource for mainboard
[    3.449717] Cannot allocate resource for EISA slot 1
[    3.449719] Cannot allocate resource for EISA slot 2
[    3.449720] Cannot allocate resource for EISA slot 3
[    3.449721] Cannot allocate resource for EISA slot 4
[    3.449723] Cannot allocate resource for EISA slot 5
[    3.449724] Cannot allocate resource for EISA slot 6
[    3.449725] Cannot allocate resource for EISA slot 7
[    3.449727] Cannot allocate resource for EISA slot 8
[
    3.449728] EISA: Detected 0 cards.
[    3.449769] cpuidle: using governor ladder
[    3.449818] cpuidle: using governor menu
[    3.449820] EFI Variables Facility v0.08 2004-May-17
[    3.449954] ashmem: initialized
[    3.450067] TCP: cubic registered
[    3.450160] NET: Registered protocol family 10
[    3.450327] NET: Registered protocol family 17
[    3.450335] Key type dns_resolver registered
[    3.450420] Using IPI No-Shortcut mode
[    3.450487] PM: Hibernation image not present or could not be loaded.
[    3.450498] registered taskstats version 1
[    3.452673] Key type trusted registered
[    3.454345] Key type encrypted registered
[    3.456511]   Magic number: 8:216:674
[    3.456588] rtc_cmos 00:05: setting system clock to 2012-08-31 07:39:26 UTC (1346398766)
[    3.457018] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.457019] EDD information not available.
[    3.472821] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.704042] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.710028] isapnp: No Plug & Play device found
[    3.715740] ata1.00: ATA-8: Corsair Force 3 SSD, 1.3.3, max UDMA/133
[    3.715744] ata1.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.725741] ata1.00: configured for UDMA/133
[    3.725931] scsi 0:0:0:0: Direct-Access     ATA      Corsair Force 3  1.3. PQ: 0 ANSI: 5
[    3.726045] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    3.726057] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.726092] sd 0:0:0:0: [sda] Write Protect is off
[    3.726094] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.726125] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.726519]  sda: sda1 sda2
[    3.726824] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.824106] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    3.956970] usb 2-1: New USB device found, idVendor=0781, idProduct=5567
[    3.956974] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.956978] usb 2-1: Product: Cruzer Blade
[    3.956980] usb 2-1: Manufacturer: SanDisk
[    3.956983] usb 2-1: SerialNumber: 20043109610A0FA1C15B
[    3.958658] Initializing USB Mass Storage driver...
[    3.958741] scsi6 : usb-storage 2-1:1.0
[    3.958792] usbcore: registered new interface driver usb-storage
[    3.958794] USB Mass Storage support registered.
[    4.044122] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.063993] ata2.00: ATAPI: TSSTcorp CDDVDW SN-S083C, SB00, max UDMA/100
[    4.063997] ata2.00: applying bridge limits
[    4.068039] usb 2-2: new high-speed USB device number 3 using ehci_hcd
[    4.083059] ata2.00: configured for UDMA/100
[    4.085453] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-S083C  SB00 PQ: 0 ANSI: 5
[    4.089669] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.089673] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.089826] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.089922] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.200855] usb 2-2: New USB device found, idVendor=1c7a, idProduct=0801
[    4.200859] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.200862] usb 2-2: Product: FingerPrinter Reader
[    4.200865] usb 2-2: Manufacturer: Generic
[    4.200868] usb 2-2: SerialNumber: 00000000000006
[    4.312097] usb 2-3: new high-speed USB device number 4 using ehci_hcd
[    4.408062] ata5: SATA link down (SStatus 0 SControl 300)
[    4.469488] usb 2-3: New USB device found, idVendor=04f2, idProduct=b109
[    4.469492] usb 2-3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    4.469495] usb 2-3: Product: USB 2.0 Camera
[    4.469498] usb 2-3: Manufacturer: Sonix Technology Co., Ltd.
[    4.469501] usb 2-3: SerialNumber: SN0001
[    4.708057] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    4.728060] ata6: SATA link down (SStatus 0 SControl 300)
[    4.728173] Freeing unused kernel memory: 752k freed
[    4.728476] Write protecting the kernel text: 5952k
[    4.728499] Write protecting the kernel read-only data: 2432k
[    4.728500] NX-protecting the kernel data: 4288k
[    4.744050] udevd[116]: starting version 175
[    4.802716] [drm] Initialized drm 1.1.0 20060810
[    4.806998] sdhci: Secure Digital Host Controller Interface driver
[    4.807001] sdhci: Copyright(c) Pierre Ossman
[    4.807241] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2382] (rev 0)
[    4.807307] mmc0: no vmmc regulator found
[    4.807337] Registered led device: mmc0::
[    4.821091] acpi device:02: registered as cooling_device2
[    4.821132] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[    4.821175] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[    4.831545] [drm] radeon defaulting to kernel modesetting.
[    4.831548] [drm] radeon kernel modesetting enabled.
[    4.832477] [drm] initializing kernel modesetting (RV730 0x1002:0x9480 0x14C0:0x003E).
[    4.832501] [drm] register mmio base: 0xCFEF0000
[    4.832502] [drm] register mmio size: 65536
[    4.832608] ATOM BIOS: Compal_KHLBX_M96M_gDDR3
[    4.832631] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    4.832633] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[    4.834728] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.834833] r8169 0000:14:00.0: irq 46 for MSI/MSI-X
[    4.834990] r8169 0000:14:00.0: eth0: RTL8168c/8111c at 0xf844c000, 00:26:22:1d:5a:7f, XID 1c4000c0 IRQ 46
[    4.834993] r8169 0000:14:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    4.835550] [drm] Detected VRAM RAM=512M, BAR=256M
[    4.835552] [drm] RAM width 128bits DDR
[    4.836076] mmc0: SDHCI controller on PCI [0000:02:00.0] using ADMA
[    4.836092] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2381] (rev 0)
[    4.836110] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
[    4.837646] [TTM] Zone  kernel: Available graphics memory: 425448 kiB
[    4.837648] [TTM] Zone highmem: Available graphics memory: 2048074 kiB
[    4.837650] [TTM] Initializing pool allocator
[    4.837654] [TTM] Initializing DMA pool allocator
[    4.837673] [drm] radeon: 512M of VRAM memory ready
[    4.837675] [drm] radeon: 512M of GTT memory ready.
[    4.837688] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.837690] [drm] Driver supports precise vblank timestamp query.
[    4.837747] radeon 0000:01:00.0: irq 47 for MSI/MSI-X
[    4.837758] radeon 0000:01:00.0: radeon: using MSI.
[    4.837793] [drm] radeon: irq initialized.
[    4.837796] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    4.838420] [drm] Loading RV730 Microcode
[    4.878281] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[    4.878334] radeon 0000:01:00.0: WB enabled
[    4.878337] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffc90c00
[    4.883378] usb 3-1: New USB device found, idVendor=0a5c, idProduct=2151
[    4.883381] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.883384] usb 3-1: Product: BCM2046 Bluetooth Device
[    4.883386] usb 3-1: Manufacturer: Broadcom Corp
[    4.883388] usb 3-1: SerialNumber: 002269EA5F5A
[    4.924348] [drm] ring test on 0 succeeded in 0 usecs
[    4.924489] [drm] ib test on ring 0 succeeded in 0 usecs
[    4.924773] [drm] Radeon Display Connectors
[    4.924775] [drm] Connector 0:
[    4.924776] [drm]   VGA-1
[    4.924778] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    4.924780] [drm]   Encoders:
[    4.924781] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    4.924782] [drm] Connector 1:
[    4.924784] [drm]   LVDS-1
[    4.924791] [drm]   DDC: 0x7f68 0x7f68 0x7f6c 0x7f6c 0x7f70 0x7f70 0x7f74 0x7f74
[    4.924792] [drm]   Encoders:
[    4.924793] [drm]     LCD1: INTERNAL_UNIPHY2
[    4.924794] [drm] Connector 2:
[    4.924801] [drm]   HDMI-A-1
[    4.924802] [drm]   HPD1
[    4.924804] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    4.924805] [drm]   Encoders:
[    4.924806] [drm]     DFP1: INTERNAL_UNIPHY
[    4.924834] [drm] radeon: power management initialized
[    4.956813] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.00 PQ: 0 ANSI: 2
[    4.957535] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.958260] sd 6:0:0:0: [sdb] 31250432 512-byte logical blocks: (16.0 GB/14.9 GiB)
[    4.959755] sd 6:0:0:0: [sdb] Write Protect is off
[    4.959760] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    4.960518] sd 6:0:0:0: [sdb] No Caching mode page present
[    4.960522] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.963626] sd 6:0:0:0: [sdb] No Caching mode page present
[    4.963630] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.964467]  sdb: sdb1
[    4.967264] sd 6:0:0:0: [sdb] No Caching mode page present
[    4.967268] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.967271] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    4.969550] mmc0: new SDHC card at address e624
[    4.971341] mmcblk0: mmc0:e624 SU16G 14.8 GiB 
[    4.981413]  mmcblk0: p1
[    5.928620] [drm] fb mappable at 0xD0142000
[    5.928623] [drm] vram apper at 0xD0000000
[    5.928624] [drm] size 4325376
[    5.928625] [drm] fb depth is 24
[    5.928626] [drm]    pitch is 5632
[    5.928706] fbcon: radeondrmfb (fb0) is primary device
[    6.795879] Console: switching to colour frame buffer device 170x48
[    6.799396] fb0: radeondrmfb frame buffer device
[    6.799397] drm: registered panic notifier
[    6.799401] [drm] Initialized radeon 2.17.0 20080528 for 0000:01:00.0 on minor 0
[    6.943564] xor: automatically using best checksumming function:
[  
  6.980008]    pIII_sse  : 10121.000 MB/sec
[    6.980568] device-mapper: dm-raid45: initialized v0.2594b
[    7.893994] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   16.036561] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.109067] udevd[1215]: starting version 175
[   16.705219] microcode: CPU0 sig=0x1067a, pf=0x80, revision=0xa07
[   16.724791] Bluetooth: Core ver 2.16
[   16.724806] NET: Registered protocol family 31
[   16.724808] Bluetooth: HCI device and connection manager initialized
[   16.724809] Bluetooth: HCI socket layer initialized
[   16.724811] Bluetooth: L2CAP socket layer initialized
[   16.724814] Bluetooth: SCO socket layer initialized
[   16.767558] compal_laptop: Identified laptop model 'KHLB2', enabling extra features
[   16.770367] microcode: CPU1 sig=0x1067a, pf=0x80, revision=0xa07
[   16.777816] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   16.789036] compal_laptop: Driver 0.2.7 successfully loaded
[   16.792822] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   16.792828] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.792830] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   16.792833] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   16.792837] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.792840] ACPI Warning: 0x00001180-0x000011bf SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   16.792843] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.792844] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   16.822147] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.822150] Bluetooth: BNEP filters: protocol multicast
[   16.829024] Bluetooth: RFCOMM TTY layer initialized
[   16.829055] Bluetooth: RFCOMM socket layer initialized
[   16.829057] Bluetooth: RFCOMM ver 1.11
[   16.856529] lp: driver loaded but no devices found
[   16.876055] init: failsafe main process (1431) killed by TERM signal
[   16.907523] cfg80211: Calling CRDA to update world regulatory domain
[   16.948427] ppdev: user-space parallel port driver
[   16.955360] device-mapper: multipath: version 1.4.0 loaded
[   16.955914] usbcore: registered new interface driver btusb
[   17.002152] tpm_tis 00:09: 1.2 TPM (device-id 0xB, rev-id 16)
[   17.070434] Linux video capture interface: v2.00
[   17.120633] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b109)
[   17.132087] tpm_tis 00:09: Adjusting TPM timeout parameters.
[   17.133444] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input5
[   17.133620] usbcore: registered new interface driver uvcvideo
[   17.133622] USB Video Class driver (1.1.1)
[   17.153732] cfg80211: World regulatory domain updated:
[   17.153736] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.153738] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.153740] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.153742] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.153744] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.153745] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.461183] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   17.578485] ath5k 0000:0e:00.0: registered as 'phy0'
[   17.598274] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   17.598466] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   17.598973] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   17.599053] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   17.643929] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   17.879080] r8169 0000:14:00.0: eth0: link down
[   17.879350] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.879668] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

```
This is from the terminal
```
ubuntu@ubuntu:~$ dmesg | grep -i acpi 
[    0.000000] BIOS-e820: [mem 0x00000000bdf55000-0x00000000bdf9efff] ACPI NVS 
[    0.000000] BIOS-e820: [mem 0x00000000bdfe4000-0x00000000bdffcfff] ACPI data 
[    0.000000] ACPI: Shall use APIC/MADT table 2 
[    0.000000] ACPI: RSDP 000f6ad0 00024 (v02 PTLTD ) 
[    0.000000] ACPI: XSDT bdff70b9 0007C (v01 PTLTD  ? XSDT   06040000  LTP 00000000) 
[    0.000000] ACPI: FACP bdfe8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001) 
[    0.000000] ACPI: DSDT bdfe9000 05A61 (v02 Intel  CANTIGA  06040000 INTL 20060608) 
[    0.000000] ACPI: FACS bdf8efc0 00040 
[    0.000000] ACPI: APIC bdffcd1e 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A) 
[    0.000000] ACPI: HPET bdffcd86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A) 
[    0.000000] ACPI: MCFG bdffcdbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A) 
[    0.000000] ACPI: SLIX bdffcdfa 00176 (v01 Compal JHL00_90 06040000 TBD  00000001) 
[    0.000000] ACPI: APIC bdffcf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000) 
[    0.000000] ACPI: BOOT bdffcfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001) 
[    0.000000] ACPI: TCPA bdfef000 00032 (v00                 00000000      00000000) 
[    0.000000] ACPI: SSDT bdfe7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624) 
[    0.000000] ACPI: SSDT bdfe6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624) 
[    0.000000] ACPI: SSDT bdfe5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624) 
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 2 
[    0.000000] ACPI: If "acpi_apic_instance=0" works better, notify linux-acpi@vger.kernel.org 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: PM-Timer IO Port: 0x408 
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
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000 
[    0.000000] Kernel command line: initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash acpi_apic_instance=2 BOOT_IMAGE=/casper/vmlinuz 
[    0.006269] ACPI: Core revision 20120320 
[    0.077821] PM: Registering ACPI NVS region [mem 0xbdf55000-0xbdf9efff] (303104 bytes) 
[    0.080755] ACPI: bus type pci registered 
[    0.276213] ACPI: Added _OSI(Module Device) 
[    0.276215] ACPI: Added _OSI(Processor Device) 
[    0.276217] ACPI: Added _OSI(3.0 _SCP Extensions) 
[    0.276219] ACPI: Added _OSI(Processor Aggregator Device) 
[    0.277616] ACPI: EC: Look up EC in DSDT 
[    0.281070] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored 
[    0.281409] ACPI: SSDT bdf1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624) 
[    0.281755] ACPI: Dynamic OEM Table Load: 
[    0.281757] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624) 
[    0.281876] ACPI: SSDT bdf18620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624) 
[    0.282206] ACPI: Dynamic OEM Table Load: 
[    0.282209] ACPI: SSDT   (null) 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624) 
[    3.120507] ACPI: SSDT bdf19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624) 
[    3.120883] ACPI: Dynamic OEM Table Load: 
[    3.120886] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624) 
[    3.148331] ACPI: SSDT bdf19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624) 
[    3.148680] ACPI: Dynamic OEM Table Load: 
[    3.148683] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624) 
[    3.148702] ACPI: Interpreter enabled 
[    3.148702] ACPI: (supports S0 S3 S4 S5) 
[    3.148702] ACPI: Using IOAPIC for interrupt routing 
[    3.149050] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources 
[    3.194422] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62 
[    3.194570] ACPI: No dock devices found. 
[    3.194575] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug 
[    3.194831] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff]) 
[    3.212423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    3.212550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT] 
[    3.212589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT] 
[    3.212717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT] 
[    3.212769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT] 
[    3.212800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT] 
[    3.212836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT] 
[    3.212878]  pci0000:00: Requesting ACPI _OSC control (0x1d) 
[    3.212881]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d 
[    3.212882] ACPI _OSC control for PCIe not granted, disabling ASPM 
[    3.218106] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15) 
[    3.218154] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[    3.218200] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15) 
[    3.218244] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10 
[    3.218291] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled. 
[    3.218338] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[    3.218382] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15) 
[    3.218428] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15) 
[    3.218497] ACPI: bus type usb registered 
[    3.218497] PCI: Using ACPI for IRQ routing 
[    3.231693] pnp: PnP ACPI init 
[    3.231709] ACPI: bus type pnp registered 
[    3.232104] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active) 
[    3.232197] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active) 
[    3.232321] system 00:02: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active) 
[    3.232368] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active) 
[    3.232488] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    3.232527] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active) 
[    3.252069] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active) 
[    3.252109] pnp 00:07: Plug and Play ACPI device, IDs SYN070b SYN0700 SYN0002 PNP0f13 (active) 
[    3.252314] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    3.252390] pnp 00:09: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active) 
[    3.252501] pnp: PnP ACPI: found 10 devices 
[    3.252502] ACPI: ACPI bus type pnp unregistered 
[    3.252505] PnPBIOS: Disabled by ACPI PNP 
[    3.314167] ACPI: AC Adapter [ACAD] (on-line) 
[    3.314272] ACPI: Lid Switch [LID0] 
[    3.314311] ACPI: Power Button [PWRB] 
[    3.314349] ACPI: Power Button [PWRF] 
[    3.314416] ACPI: Requesting acpi_cpufreq 
[    3.317444] ACPI: acpi_idle registered with cpuidle 
[    3.356579] ACPI: Battery Slot [BAT1] (battery present) 
[    3.376293] ACPI: Battery Slot [BAT1] (battery present) 
[    4.821091] acpi device:02: registered as cooling_device2 
[    4.821132] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no) 
[   16.792822] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251) 
[   16.792828] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver 
[   16.792833] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251) 
[   16.792837] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver 
[   16.792840] ACPI Warning: 0x00001180-0x000011bf SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251) 
[   16.792843] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver 
```

Nothing for dmesg grep -i error

```
ubuntu@ubuntu:~$ dmesg | grep -i warn 
[   16.792822] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251) 
[   16.792833] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251) 
[   16.792840] ACPI Warning: 0x00001180-0x000011bf SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251) 
```

I have updated the bios lots of times, to the latest.

---

### Post by Toz on 2012-08-31
> **Bowater said:**
> 
```
Linux version 3.5.0-10-generic (buildd@akateko)
```

```
ubuntu@ubuntu:~$ dmesg | grep -i warn 
[   16.792822] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251) 
[   16.792833] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251) 
[   16.792840] ACPI Warning: 0x00001180-0x000011bf SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251) 
```

Again out of curiosity mostly, can you try "acpi_apic_instance=2" with a 3.2x kernel? See:
- [https://bugzilla.kernel.org/show_bug.cgi?id=45851]("https://bugzilla.kernel.org/show_bug.cgi?id=45851")
- [https://bugzilla.kernel.org/show_bug.cgi?id=44991]("https://bugzilla.kernel.org/show_bug.cgi?id=44991")
- [https://lkml.org/lkml/2012/8/14/309]("https://lkml.org/lkml/2012/8/14/309")

Also, what does:
```
cat /proc/cpuinfo | grep 'cpu cores'
```
...report with and without that kernel parameter?

---

### Post by AoFhEkOl on 2012-08-31
With Kernel parameter
tim@tim-desktop:~$ cat /proc/cpuinfo | grep 'cpu cores' 
cpu cores	: 2 
cpu cores	: 2 
tim@tim-desktop:~$ 

without kernel parameter
tim@tim-desktop:~$ cat /proc/cpuinfo | grep 'cpu cores' 
cpu cores	: 2 
cpu cores	: 2 

Kernel 3.2

dmesg | grep -i warn : Nothing



```
tim@tim-desktop:~$  dmesg | grep -i acpi 
[    0.000000]  BIOS-e820: 00000000bdf55000 - 00000000bdf9f000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 00000000bdfe4000 - 00000000bdffd000 (ACPI data) 
[    0.000000] ACPI: Shall use APIC/MADT table 2 
[    0.000000] ACPI: RSDP 000f6ad0 00024 (v02 PTLTD ) 
[    0.000000] ACPI: XSDT bdff70b9 0007C (v01 PTLTD  ? XSDT   06040000  LTP 00000000) 
[    0.000000] ACPI: FACP bdfe8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001) 
[    0.000000] ACPI: DSDT bdfe9000 05A61 (v02 Intel  CANTIGA  06040000 INTL 20060608) 
[    0.000000] ACPI: FACS bdf8efc0 00040 
[    0.000000] ACPI: APIC bdffcd1e 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A) 
[    0.000000] ACPI: HPET bdffcd86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A) 
[    0.000000] ACPI: MCFG bdffcdbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A) 
[    0.000000] ACPI: SLIX bdffcdfa 00176 (v01 Compal JHL00_90 06040000 TBD  00000001) 
[    0.000000] ACPI: APIC bdffcf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000) 
[    0.000000] ACPI: BOOT bdffcfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001) 
[    0.000000] ACPI: TCPA bdfef000 00032 (v00                 00000000      00000000) 
[    0.000000] ACPI: SSDT bdfe7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624) 
[    0.000000] ACPI: SSDT bdfe6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624) 
[    0.000000] ACPI: SSDT bdfe5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624) 
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 2 
[    0.000000] ACPI: If "acpi_apic_instance=0" works better, notify linux-acpi@vger.kernel.org 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: PM-Timer IO Port: 0x408 
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
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000 
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=fa16961b-8316-4938-a1b7-f17f0fb506b7 ro quiet splash acpi_apic_instance=2 
[    0.006217] ACPI: Core revision 20110623 
[    0.149836] PM: Registering ACPI NVS region at bdf55000 (303104 bytes) 
[    0.149836] ACPI: bus type pci registered 
[    0.152862] ACPI: Added _OSI(Module Device) 
[    0.152864] ACPI: Added _OSI(Processor Device) 
[    0.152866] ACPI: Added _OSI(3.0 _SCP Extensions) 
[    0.152868] ACPI: Added _OSI(Processor Aggregator Device) 
[    0.154254] ACPI: EC: Look up EC in DSDT 
[    0.157726] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored 
[    0.158081] ACPI: SSDT bdf1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624) 
[    0.158414] ACPI: Dynamic OEM Table Load: 
[    0.158418] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624) 
[    0.158540] ACPI: SSDT bdf18620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624) 
[    0.158857] ACPI: Dynamic OEM Table Load: 
[    0.158860] ACPI: SSDT   (null) 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624) 
[    0.216298] ACPI: SSDT bdf19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624) 
[    0.216653] ACPI: Dynamic OEM Table Load: 
[    0.216656] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624) 
[    0.248145] ACPI: SSDT bdf19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624) 
[    0.248481] ACPI: Dynamic OEM Table Load: 
[    0.248484] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624) 
[    0.269319] ACPI: Interpreter enabled 
[    0.269319] ACPI: (supports S0 S3 S4 S5) 
[    0.269319] ACPI: Using IOAPIC for interrupt routing 
[    0.269319] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources 
[    0.310497] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62 
[    0.310590] ACPI: No dock devices found. 
[    0.310590] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug 
[    0.310590] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff]) 
[    0.328256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.328410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT] 
[    0.328456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT] 
[    0.328591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT] 
[    0.328646] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT] 
[    0.328678] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT] 
[    0.328715] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT] 
[    0.328761]  pci0000:00: Requesting ACPI _OSC control (0x1d) 
[    0.328764]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d 
[    0.328766] ACPI _OSC control for PCIe not granted, disabling ASPM 
[    0.334224] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15) 
[    0.334273] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[    0.334320] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15) 
[    0.334367] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10 
[    0.334414] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled. 
[    0.334463] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[    0.334510] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15) 
[    0.334557] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15) 
[    0.335100] PCI: Using ACPI for IRQ routing 
[    0.352101] pnp: PnP ACPI init 
[    0.352122] ACPI: bus type pnp registered 
[    0.352518] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active) 
[    0.352614] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active) 
[    0.352750] system 00:02: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active) 
[    0.352799] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active) 
[    0.352923] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    0.352967] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active) 
[    0.372118] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active) 
[    0.372163] pnp 00:07: Plug and Play ACPI device, IDs SYN070b SYN0700 SYN0002 PNP0f13 (active) 
[    0.372402] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    0.372484] pnp 00:09: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active) 
[    0.372596] pnp: PnP ACPI: found 10 devices 
[    0.372598] ACPI: ACPI bus type pnp unregistered 
[    0.372602] PnPBIOS: Disabled by ACPI PNP 
[    0.451147] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared 
[    0.451395] ACPI: AC Adapter [ACAD] (on-line) 
[    0.451504] ACPI: Lid Switch [LID0] 
[    0.451547] ACPI: Power Button [PWRB] 
[    0.451592] ACPI: Power Button [PWRF] 
[    0.453662] ACPI: acpi_idle registered with cpuidle 
[    0.472578] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared 
[    0.472587] ACPI: Battery Slot [BAT1] (battery present) 
[    0.492299] ACPI: Battery Slot [BAT1] (battery present) 
[    0.992210] acpi device:1f: hash matches 
[    7.815713] acpi device:02: registered as cooling_device2 
[    7.815861] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no) 
```

---

### Post by Toz on 2012-08-31
From your original post:
> My solution on windows was to change the processor driver from the intel one to a processor driver that was in device manager. The difference between the two is this.

"Processor" has no sleep states or power management, the "Intel Processor" uses the intelppm driver and allows full power state management. If switching to a processor driver that doesn't allow sleep states "fixes" things, it's likely there's a hardware issue in one (or more) of the CPU cores or L1 caches at that point.

It sounds like "processor" in windows is just an acpi-disabled state of the regular intel processor driver (I could be wrong). You could try booting with "acpi=off" for a test, though I wouldn't recommend running it that way too long. Since it seems to work in Windows though, it might be worth a try?

---

### Post by AoFhEkOl on 2012-09-01
That would make sense, acpi=off boots but i have no wifi.  Thats the main problem...

---

### Post by AoFhEkOl on 2012-09-02
So what now? ;)

---

### Post by Toz on 2012-09-02
It may be a bit of a stretch, but can you give the following kernel parameters a try:
- acpi=strict
- noapic

---

### Post by AoFhEkOl on 2012-09-02
I tried them and no luck.. Are there any other kernel commands?

---

### Post by Toz on 2012-09-02
The whole listing can be found here: [http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt"). 

Perhaps you should create a launchpad bug report and try to get one of the kernel devs to have a look at it.

---

### Post by AoFhEkOl on 2012-09-03
processor.nocst=1  what does this do exactly? Because it works, do you want me to do other tests so we can help others? or just mark as solved?

---

### Post by Toz on 2012-09-03
By all means mark it solved if the issue is solved. As for the parameter, I have never come up against it before. However, looking at post #16 of this link: [https://bugzilla.redhat.com/show_bug.cgi?id=727865]("https://bugzilla.redhat.com/show_bug.cgi?id=727865") gives some explanation as to what might be happening.

---

### Post by AoFhEkOl on 2012-09-04
Thanks for your help Toz ):P

---

