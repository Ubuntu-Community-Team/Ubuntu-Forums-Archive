---
title: "No USB Device support"
date: 2010-08-11
forum: Hardware
---

### Post by exsoar on 2010-08-11
I am definitely not a Linux expert but I have a laptop that needs to have Ubuntu installed.  I have a problem I've been dodging for a couple of weeks with usb devices not being recognized by Ubuntu. As far as I can tell Ubuntu sees the USB controller, bus and hubs but doesn't do anything with the devices plugged into them. I have devices and wireless mouse with a USB dongle and a flash drive that are needed and I can't get either to show up. The only I can test them is by trying them on a Windows box and they work fine. Any ideas would be greatly appreciated.


```
# dmidecode 2.9
SMBIOS 2.4 present.
19 structures occupying 688 bytes.
Table at 0x000F0210.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Acer
    Version: V2.00
    Release Date: 08/03/2006
    Address: 0xE4860
    Runtime Size: 112544 bytes
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        Smart battery is supported
        BIOS boot specification is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Acer            
    Product Name: Aspire 5100     
    Version: V2.00
    Serial Number: LXABH0J0066430EB041601
    UUID: 36323361-3934-3831-6237-0016D45642DB
    Wake-up Type: Power Switch
    SKU Number: Not Specified
    Family: Not Specified

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Acer
    Product Name: Navarro
    Version: N/A
    Serial Number: LXABH0J0066430EB041601

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: Acer
    Type: Notebook
    Lock: Not Present
    Version: N/A
    Serial Number: LXABH0J0066430EB041601          
    Asset Tag: ................................
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: Socket M2/S1G1
    Type: Central Processor
    Family: Opteron
    Manufacturer: AMD
    ID: 82 0F 04 00 FF FB 8B 17
    Signature: Family 15, Model 72, Stepping 2
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        HTT (Hyper-threading technology)
    Version: Engineering Sample
    Voltage: 1.4 V
    External Clock: 200 MHz
    Max Speed: 1600 MHz
    Current Speed: 1600 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: Not Provided
    L2 Cache Handle: 0x0005
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 512 KB
    Maximum Size: 1024 KB
    Supported SRAM Types:
        Burst
        Pipeline Burst
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0006, DMI type 9, 13 bytes
System Slot Information
    Designation: PCMCIA Slot0
    Type: 32-bit PC Card (PCMCIA)
    Current Usage: Unknown
    Length: Long
    ID: Adapter 0, Socket 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PC Card-16 is supported
        Cardbus is supported
        Hot-plug devices are supported

Handle 0x0007, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Disabled
    Description: ATI RS485M

Handle 0x0008, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Disabled
    Description: HD-Audio

Handle 0x0009, DMI type 15, 29 bytes
System Event Log
    Area Length: 16 bytes
    Header Start Offset: 0x0000
    Header Length: 16 bytes
    Data Start Offset: 0x0010
    Access Method: General-purpose non-volatile data functions
    Access Address: 0x0000
    Status: Valid, Not Full
    Change Token: 0x00000000
    Header Format: Type 1
    Supported Log Type Descriptors: 3
    Descriptor 1: POST error
    Data Format 1: POST results bitmap
    Descriptor 2: Single-bit ECC memory error
    Data Format 2: Multiple-event
    Descriptor 3: Multi-bit ECC memory error
    Data Format 3: Multiple-event

Handle 0x000A, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x000B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: No Error
    Total Width: 128 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 1
    Locator: S1
    Bank Locator: Bank 0
    Type: DDR2
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x000C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: No Error
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: 2
    Locator: S2
    Bank Locator: Bank 1
    Type: DDR2
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x000D, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x000E, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Array Handle: 0x000A
    Partition Width: 0

Handle 0x000F, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x000B
    Memory Array Mapped Address Handle: 0x000E
    Partition Row Position: 2
    Interleave Position: 1
    Interleaved Data Depth: 6

Handle 0x0010, DMI type 22, 26 bytes
Portable Battery
    Location: Left Front
    Manufacturer: Not Specified
    Name: <BAD INDEX>
    Design Capacity: Unknown
    Design Voltage: Unknown
    SBDS Version: Not Specified
    Maximum Error: Unknown
    SBDS Serial Number: 0000
    SBDS Manufacture Date: 1980-00-00
    SBDS Chemistry: Not Specified
    OEM-specific Information: 0x00000000

Handle 0x0011, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0x0012, DMI type 127, 4 bytes
End Of Table
``````
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``` ```
 *-core
       description: Motherboard
       product: Navarro
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXABH0J0066430EB041601
  *-usb:0
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13
       bus info: pci@0000:00:13.0
       version: 80
       width: 32 bits
       clock: 66MHz
       capabilities: msi bus_master cap_list
       configuration: driver=ohci_hcd latency=64
       resources: irq:19 memory:c0004000-c0004fff
  *-usb:1
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.1
       bus info: pci@0000:00:13.1
       version: 80
       width: 32 bits
       clock: 66MHz
       capabilities: msi bus_master cap_list
       configuration: driver=ohci_hcd latency=64
       resources: irq:19 memory:c0005000-c0005fff
  *-usb:2
       description: USB Controller
       product: IXP SB400 USB2 Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.2
       bus info: pci@0000:00:13.2
       version: 80
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=ehci_hcd latency=64
       resources: irq:19 memory:c0006000-c0006fff
  *-serial
       description: SMBus
       product: IXP SB400 SMBus Controller
       vendor: ATI Technologies Inc
       physical id: 14
       bus info: pci@0000:00:14.0
       version: 83
       width: 32 bits
       clock: 66MHz
       capabilities: ht cap_list
       configuration: driver=piix4_smbus latency=0
       resources: irq:0 ioport:8400(size=16) memory:fed00000-fed003ff
``````
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
```


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e90000 (usable)
[    0.000000]  BIOS-e820: 0000000037e90000 - 0000000037e9a000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e9a000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x37e90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 0038000000 mask FFF8000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000037e90000 (usable)
[    0.000000]  modified: 0000000037e90000 - 0000000037e9a000 (ACPI data)
[    0.000000]  modified: 0000000037e9a000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  modified: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 29792000 - 29f2bd0f
[    0.000000] ACPI: RSDP 000f80e0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 37e91f82 00034 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 37e99d7a 00074 (v01 ATI    Bowfin   06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 37e91fb6 07DC4 (v01   Acer  Navarro 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 37e9afc0 00040
[    0.000000] ACPI: SSDT 37e99dee 00182 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 37e99f70 00054 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 37e99fc4 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [0029792000 - 0029f2bd0f]          RAMDISK ==> [0029792000 - 0029f2bd0f]
[    0.000000]   #5 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #6 [00008dc000 - 00008df111]              BRK ==> [00008dc000 - 00008df111]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f8110] f8110
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00037e90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00037e90
[    0.000000] On node 0 totalpages: 228905
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 14 pages used for memmap
[    0.000000]   HighMem zone: 1668 pages, LIFO batch:0
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x83
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227115
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=09654cdd-2660-4ae3-9b2f-7b38ced86b0b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4580160 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00037e90)
[    0.000000] Memory: 886668k/916032k available (4679k kernel code, 28448k reserved, 2116k data, 660k init, 6728k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.819 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.63 BogoMIPS (lpj=6383276)
[    0.008027] Security Framework initialized
[    0.008049] AppArmor: AppArmor initialized
[    0.008058] Mount-cache hash table entries: 512
[    0.008202] Initializing cgroup subsys ns
[    0.008208] Initializing cgroup subsys cpuacct
[    0.008213] Initializing cgroup subsys memory
[    0.008221] Initializing cgroup subsys devices
[    0.008224] Initializing cgroup subsys freezer
[    0.008228] Initializing cgroup subsys net_cls
[    0.008249] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008253] CPU: L2 Cache: 256K (64 bytes/line)
[    0.008256] CPU: Physical Processor ID: 0
[    0.008259] CPU: Processor Core ID: 0
[    0.008263] mce: CPU supports 5 MCE banks
[    0.008276] using C1E aware idle routine
[    0.008284] Performance Events: AMD PMU driver.
[    0.008293] ... version:                0
[    0.008295] ... bit width:              48
[    0.008298] ... generic registers:      4
[    0.008300] ... value mask:             0000ffffffffffff
[    0.008303] ... max period:             00007fffffffffff
[    0.008306] ... fixed-purpose events:   0
[    0.008308] ... event mask:             000000000000000f
[    0.008313] Checking 'hlt' instruction... OK.
[    0.026925] ACPI: Core revision 20090903
[    0.040012] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040019] ftrace: allocating 21780 entries in 43 pages
[    0.048073] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048429] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.088116] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.092001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.012000] Initializing CPU#1
[    0.012000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.012000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.012000] CPU: Physical Processor ID: 0
[    0.012000] CPU: Processor Core ID: 1
[    0.176128] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.176163] Brought up 2 CPUs
[    0.176167] Total of 2 processors activated (6383.83 BogoMIPS).
[    0.176161] System has AMD C1E enabled
[    0.176161] Switch to broadcast mode on CPU1
[    0.176342] CPU0 attaching sched-domain:
[    0.176346]  domain 0: span 0-1 level MC
[    0.176350]   groups: 0 1
[    0.176357] CPU1 attaching sched-domain:
[    0.176360]  domain 0: span 0-1 level MC
[    0.176363]   groups: 1 0
[    0.176467] Switch to broadcast mode on CPU0
[    0.176467] devtmpfs: initialized
[    0.176467] regulator: core version 0.5
[    0.176467] Time: 13:26:25  Date: 08/12/10
[    0.176467] NET: Registered protocol family 16
[    0.176467] Trying to unpack rootfs image as initramfs...
[    0.176467] EISA bus registered
[    0.176467] ACPI: bus type pci registered
[    0.176467] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 7
[    0.176467] PCI: MCFG area at e0000000 reserved in E820
[    0.176467] PCI: Using MMCONFIG for extended config space
[    0.176467] PCI: Using configuration type 1 for base access
[    0.180153] bio: create slab <bio-0> at 0
[    0.181238] ACPI: EC: Look up EC in DSDT
[    0.183944] ACPI Warning: Package List length (0x1) larger than NumElements count (0x0), truncated
[    0.183952]  (20090903/dsobject-515)
[    0.184048] ACPI Warning: Package List length (0x1) larger than NumElements count (0x0), truncated
[    0.184055]  (20090903/dsobject-515)
[    0.204665] ACPI: Interpreter enabled
[    0.204676] ACPI: (supports S0 S3 S4 S5)
[    0.204700] ACPI: Using IOAPIC for interrupt routing
[    0.257506] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.257756] ACPI: No dock devices found.
[    0.258886] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.259023] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.259028] pci 0000:00:04.0: PME# disabled
[    0.259071] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.259075] pci 0000:00:05.0: PME# disabled
[    0.259147] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0004000-0xc0004fff]
[    0.259260] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0005000-0xc0005fff]
[    0.259383] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0006000-0xc0006fff]
[    0.259457] pci 0000:00:13.2: supports D1 D2
[    0.259460] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.259467] pci 0000:00:13.2: PME# disabled
[    0.259525] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
[    0.259536] pci 0000:00:14.0: reg 14 32bit mmio: [0xfed00000-0xfed003ff]
[    0.259576] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.259644] pci 0000:00:14.1: reg 10 io port: [0x8430-0x8437]
[    0.259655] pci 0000:00:14.1: reg 14 io port: [0x8424-0x8427]
[    0.259665] pci 0000:00:14.1: reg 18 io port: [0x8428-0x842f]
[    0.259676] pci 0000:00:14.1: reg 1c io port: [0x8420-0x8423]
[    0.259686] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
[    0.259792] pci 0000:00:14.2: reg 10 64bit mmio: [0xc0000000-0xc0003fff]
[    0.259860] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.259866] pci 0000:00:14.2: PME# disabled
[    0.260138] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc8000000-0xcfffffff]
[    0.260144] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.260150] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.260163] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.260175] pci 0000:01:05.0: supports D1 D2
[    0.260196] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.260201] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.260207] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xcfffffff]
[    0.260270] pci 0000:00:04.0: bridge io port: [0x00-0xfff]
[    0.260275] pci 0000:00:04.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.260281] pci 0000:00:04.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.260343] pci 0000:00:05.0: bridge io port: [0x00-0xfff]
[    0.260348] pci 0000:00:05.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.260409] pci 0000:06:01.0: reg 10 io port: [0xa000-0xa0ff]
[    0.260422] pci 0000:06:01.0: reg 14 32bit mmio: [0xc0210000-0xc02100ff]
[    0.260496] pci 0000:06:01.0: supports D1 D2
[    0.260499] pci 0000:06:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.260507] pci 0000:06:01.0: PME# disabled
[    0.260566] pci 0000:06:02.0: reg 10 32bit mmio: [0xc0200000-0xc020ffff]
[    0.260707] pci 0000:06:04.0: reg 10 32bit mmio: [0xc0211000-0xc0211fff]
[    0.260741] pci 0000:06:04.0: supports D1 D2
[    0.260745] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.260753] pci 0000:06:04.0: PME# disabled
[    0.260813] pci 0000:06:04.1: reg 10 32bit mmio: [0xc0210400-0xc021047f]
[    0.260897] pci 0000:06:04.1: supports D1 D2
[    0.260901] pci 0000:06:04.1: PME# supported from D0 D1 D2 D3hot
[    0.260908] pci 0000:06:04.1: PME# disabled
[    0.260968] pci 0000:06:04.2: reg 10 32bit mmio: [0xc0210800-0xc02108ff]
[    0.261052] pci 0000:06:04.2: supports D1 D2
[    0.261055] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
[    0.261063] pci 0000:06:04.2: PME# disabled
[    0.261124] pci 0000:06:04.3: reg 10 32bit mmio: [0xc0210c00-0xc0210c7f]
[    0.261208] pci 0000:06:04.3: supports D1 D2
[    0.261211] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
[    0.261218] pci 0000:06:04.3: PME# disabled
[    0.261279] pci 0000:06:04.4: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.261363] pci 0000:06:04.4: supports D1 D2
[    0.261367] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
[    0.261374] pci 0000:06:04.4: PME# disabled
[    0.261448] pci 0000:00:14.4: transparent bridge
[    0.261458] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.261465] pci 0000:00:14.4: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.261513] pci_bus 0000:00: on NUMA node 0
[    0.261519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.261645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.261725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.261809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB4_._PRT]
[    0.261886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB5_._PRT]
[    0.261997] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.262115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.268229] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.268374] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.268505] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.268634] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.268763] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.268897] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.269027] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.269156] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.269285] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.269436] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.269445] vgaarb: loaded
[    0.269590] SCSI subsystem initialized
[    0.269727] libata version 3.00 loaded.
[    0.269818] usbcore: registered new interface driver usbfs
[    0.269835] usbcore: registered new interface driver hub
[    0.269874] usbcore: registered new device driver usb
[    0.270129] ACPI: WMI: Mapper loaded
[    0.270132] PCI: Using ACPI for IRQ routing
[    0.270141] pci 0000:00:04.0: BAR 13: can't allocate resource
[    0.270145] pci 0000:00:04.0: BAR 14: can't allocate resource
[    0.270148] pci 0000:00:04.0: BAR 15: can't allocate resource
[    0.270152] pci 0000:00:05.0: BAR 13: can't allocate resource
[    0.270155] pci 0000:00:05.0: BAR 14: can't allocate resource
[    0.270398] NetLabel: Initializing
[    0.270401] NetLabel:  domain hash size = 128
[    0.270403] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.270421] NetLabel:  unlabeled traffic allowed by default
[    0.272778] AppArmor: AppArmor Filesystem Enabled
[    0.272807] pnp: PnP ACPI init
[    0.272834] ACPI: bus type pnp registered
[    0.275964] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.296214] pnp: PnP ACPI: found 10 devices
[    0.296217] ACPI: ACPI bus type pnp unregistered
[    0.296222] PnPBIOS: Disabled by ACPI PNP
[    0.296239] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.296244] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.296249] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.296261] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.296266] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.296271] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.296276] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.296280] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.296285] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.296289] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.296294] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.296299] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.296303] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.296308] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.296313] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.296317] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.296322] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.296327] system 00:08: ioport range 0x280-0x293 has been reserved
[    0.296332] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.296340] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.296345] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.331071] Switching to clocksource acpi_pm
[    0.331468] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.331468] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.331468] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.331468] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff
[    0.331468] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.331468] pci 0000:00:04.0:   IO window: disabled
[    0.331468] pci 0000:00:04.0:   MEM window: disabled
[    0.331468] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.331468] pci 0000:00:05.0: PCI bridge, secondary bus 0000:04
[    0.331468] pci 0000:00:05.0:   IO window: disabled
[    0.331468] pci 0000:00:05.0:   MEM window: disabled
[    0.331468] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.331468] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
[    0.331468] pci 0000:06:04.0:   IO window: 0x00a400-0x00a4ff
[    0.331468] pci 0000:06:04.0:   IO window: 0x00a800-0x00a8ff
[    0.331468] pci 0000:06:04.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.331468] pci 0000:06:04.0:   MEM window: 0x44000000-0x47ffffff
[    0.331468] pci 0000:00:14.4: PCI bridge, secondary bus 0000:06
[    0.331468] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.331468] pci 0000:00:14.4:   MEM window: 0xc0200000-0xc02fffff
[    0.331468] pci 0000:00:14.4:   PREFETCH window: 0x40000000-0x43ffffff
[    0.331468] pci 0000:00:04.0: setting latency timer to 64
[    0.331468] pci 0000:00:05.0: setting latency timer to 64
[    0.331468]   alloc irq_desc for 20 on node -1
[    0.331468]   alloc kstat_irqs on node -1
[    0.331468] pci 0000:06:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.331468] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.331468] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.331468] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.331468] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.331468] pci_bus 0000:01: resource 2 pref mem [0xc8000000-0xcfffffff]
[    0.331468] pci_bus 0000:02: resource 0 mem: [0x0-0xfff]
[    0.331468] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]
[    0.331468] pci_bus 0000:02: resource 2 mem: [0x0-0xfffff]
[    0.331468] pci_bus 0000:04: resource 0 mem: [0x0-0xfff]
[    0.331468] pci_bus 0000:04: resource 1 mem: [0x0-0xfffff]
[    0.331468] pci_bus 0000:06: resource 0 io:  [0xa000-0xafff]
[    0.331468] pci_bus 0000:06: resource 1 mem: [0xc0200000-0xc02fffff]
[    0.331468] pci_bus 0000:06: resource 2 pref mem [0x40000000-0x43ffffff]
[    0.331468] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.331468] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.331468] pci_bus 0000:07: resource 0 io:  [0xa400-0xa4ff]
[    0.331468] pci_bus 0000:07: resource 1 io:  [0xa800-0xa8ff]
[    0.331468] pci_bus 0000:07: resource 2 pref mem [0x40000000-0x43ffffff]
[    0.331468] pci_bus 0000:07: resource 3 mem: [0x44000000-0x47ffffff]
[    0.331468] NET: Registered protocol family 2
[    0.331468] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.331468] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.331468] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.331468] TCP: Hash tables configured (established 131072 bind 65536)
[    0.331468] TCP reno registered
[    0.331468] NET: Registered protocol family 1
[    0.331468] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.331468] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.331468] pci 0000:01:05.0: Boot video device
[    0.331468] cpufreq-nforce2: No nForce2 chipset.
[    0.331468] Scanning for low memory corruption every 60 seconds
[    0.331468] audit: initializing netlink socket (disabled)
[    0.331468] type=2000 audit(1281619584.328:1): initialized
[    0.344200] highmem bounce pool size: 64 pages
[    0.344207] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.346173] VFS: Disk quotas dquot_6.5.2
[    0.346252] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.347025] fuse init (API version 7.13)
[    0.347134] msgmni has been set to 1719
[    0.347455] alg: No test for stdrng (krng)
[    0.347532] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.347536] io scheduler noop registered
[    0.347539] io scheduler anticipatory registered
[    0.347541] io scheduler deadline registered
[    0.347592] io scheduler cfq registered (default)
[    0.347779] pcieport 0000:00:04.0: setting latency timer to 64
[    0.347850] pcieport 0000:00:05.0: setting latency timer to 64
[    0.347902] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.347932] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.350112] ACPI: AC Adapter [ACAD] (on-line)
[    0.350201] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.350268] ACPI: Lid Switch [LID]
[    0.350324] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.350329] ACPI: Power Button [PWRB]
[    0.350385] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.350389] ACPI: Sleep Button [SLPB]
[    0.350465] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.350469] ACPI: Power Button [PWRF]
[    0.350792] ACPI: processor limited to max C-state 1
[    0.350827] processor LNXCPU:00: registered as cooling_device0
[    0.350871] processor LNXCPU:01: registered as cooling_device1
[    0.390502] ACPI: Invalid active0 threshold
[    0.396857] thermal LNXTHERM:01: registered as thermal_zone0
[    0.396868] ACPI: Thermal Zone [THRM] (54 C)
[    0.398901] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.400693] brd: module loaded
[    0.401337] loop: module loaded
[    0.401480] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.401702]   alloc irq_desc for 16 on node -1
[    0.401706]   alloc kstat_irqs on node -1
[    0.401716] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.401775] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.402194] Fixed MDIO Bus: probed
[    0.402240] PPP generic driver version 2.4.2
[    0.402300] tun: Universal TUN/TAP device driver, 1.6
[    0.402304] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.402416] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.402441]   alloc irq_desc for 19 on node -1
[    0.402444]   alloc kstat_irqs on node -1
[    0.402451] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.402474] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.402518] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.402613] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000
[    0.402908] isapnp: Scanning for PnP cards...
[    0.445940] Freeing initrd memory: 7783k freed
[    0.452265] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.452439] usb usb1: configuration #1 chosen from 1 choice
[    0.452486] hub 1-0:1.0: USB hub found
[    0.452503] hub 1-0:1.0: 8 ports detected
[    0.452647] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.452678] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.452709] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.452762] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.452789] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000
[    0.509252] usb usb2: configuration #1 chosen from 1 choice
[    0.509295] hub 2-0:1.0: USB hub found
[    0.509313] hub 2-0:1.0: 4 ports detected
[    0.509395] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.509420] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.509472] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.509499] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000
[    0.565148] usb usb3: configuration #1 chosen from 1 choice
[    0.565182] hub 3-0:1.0: USB hub found
[    0.565196] hub 3-0:1.0: 4 ports detected
[    0.565276] uhci_hcd: USB Universal Host Controller Interface driver
[    0.565381] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    0.565729] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.565822] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.565836] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.565841] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.565846] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.565850] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.565951] mice: PS/2 mouse device common for all mice
[    0.566123] rtc_cmos 00:04: RTC can wake from S4
[    0.566171] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.566203] rtc0: alarms up to one month, 114 bytes nvram
[    0.566334] device-mapper: uevent: version 1.0.3
[    0.566543] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.566632] device-mapper: multipath: version 1.1.0 loaded
[    0.566636] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.566814] EISA: Probing bus 0 at eisa.0
[    0.566824] Cannot allocate resource for EISA slot 1
[    0.566856] Cannot allocate resource for EISA slot 8
[    0.566859] EISA: Detected 0 cards.
[    0.566973] cpuidle: using governor ladder
[    0.566976] cpuidle: using governor menu
[    0.567560] TCP cubic registered
[    0.567752] NET: Registered protocol family 10
[    0.568331] lo: Disabled Privacy Extensions
[    0.568749] NET: Registered protocol family 17
[    0.568796] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[    0.568843] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[    0.568846] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    0.570850] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.583928] Using IPI No-Shortcut mode
[    0.584053] PM: Resume from disk failed.
[    0.584069] registered taskstats version 1
[    0.584525]   Magic number: 6:665:432
[    0.584635] rtc_cmos 00:04: setting system clock to 2010-08-12 13:26:26 UTC (1281619586)
[    0.584640] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.584643] EDD information not available.
[    0.688192] ACPI: Battery Slot [BAT1] (battery present)
[    0.758087] isapnp: No Plug & Play device found
[    0.758104] Freeing unused kernel memory: 660k freed
[    0.758769] Write protecting the kernel text: 4680k
[    0.758819] Write protecting the kernel read-only data: 1840k
[    0.784584] udev: starting version 151
[    0.878127] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    0.878136] hub 1-0:1.0: hub_port_status failed (err = -32)
[    0.943675] scsi0 : pata_atiixp
[    0.943863] scsi1 : pata_atiixp
[    0.944730] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    0.944735] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    0.950265] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.950296] 8139cp 0000:06:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.082135] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    1.082144] hub 1-0:1.0: hub_port_status failed (err = -32)
[    1.116931] ata1.00: ATA-7: HTS421212H9AT00, HA4OA70S, max UDMA/100
[    1.116936] ata1.00: 234441648 sectors, multi 16: LBA48 
[    1.116976] ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PP02, max UDMA/33
[    1.132871] ata1.00: configured for UDMA/100
[    1.148583] ata1.01: configured for UDMA/33
[    1.151093] scsi 0:0:0:0: Direct-Access     ATA      HTS421212H9AT00  HA4O PQ: 0 ANSI: 5
[    1.151323] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.151379] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.154786] sd 0:0:0:0: [sda] Write Protect is off
[    1.154792] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.154798] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PP02 PQ: 0 ANSI: 5
[    1.154837] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.166630] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.166635] Uniform CD-ROM driver Revision: 3.20
[    1.166665]  sda:
[    1.166801] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.166884] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.183978]  sda1 sda2 < sda5 >
[    1.199489] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.286135] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    1.286141] hub 1-0:1.0: hub_port_status failed (err = -32)
[    1.324112] 8139too Fast Ethernet driver 0.9.28
[    1.324178]   alloc irq_desc for 21 on node -1
[    1.324181]   alloc kstat_irqs on node -1
[    1.324191] 8139too 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.326101] eth0: RealTek RTL8139 at 0xa000, 00:16:d4:56:42:db, IRQ 21
[    1.490142] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    1.490151] hub 1-0:1.0: hub_port_status failed (err = -32)
[    1.652623] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.652630] EXT4-fs (sda1): write access will be enabled during recovery
[    1.694124] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    1.694132] hub 1-0:1.0: hub_port_status failed (err = -32)
[    1.694137] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[    1.750234] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    1.750240] hub 1-0:1.0: hub_port_status failed (err = -32)
[    1.954223] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    1.954229] hub 1-0:1.0: hub_port_status failed (err = -32)
[    2.158209] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    2.158216] hub 1-0:1.0: hub_port_status failed (err = -32)
[    2.362211] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    2.362218] hub 1-0:1.0: hub_port_status failed (err = -32)
[    2.620063] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    4.910180] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    4.910189] hub 1-0:1.0: hub_port_status failed (err = -32)
[    5.114164] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    5.114173] hub 1-0:1.0: hub_port_status failed (err = -32)
[    5.318128] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    5.318137] hub 1-0:1.0: hub_port_status failed (err = -32)
[    5.522187] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    5.522195] hub 1-0:1.0: hub_port_status failed (err = -32)
[    5.726171] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    5.726179] hub 1-0:1.0: hub_port_status failed (err = -32)
[    5.726183] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[    5.782141] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    5.782149] hub 1-0:1.0: hub_port_status failed (err = -32)
[    5.986157] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    5.986166] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.190136] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    6.190144] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.394188] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    6.394195] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.598136] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    6.598144] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.598147] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[    6.654132] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    6.654140] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.858129] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    6.858137] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.062113] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    7.062118] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.266117] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    7.266122] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.458853] EXT4-fs (sda1): orphan cleanup on readonly fs
[    7.458865] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2108027
[    7.458973] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1835850
[    7.459052] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1836819
[    7.459077] EXT4-fs (sda1): 3 orphan inodes deleted
[    7.459081] EXT4-fs (sda1): recovery complete
[    7.470127] ehci_hcd 0000:00:13.2: port 4 reset error -110
[    7.470134] hub 1-0:1.0: hub_port_status failed (err = -32)
[    7.470138] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[    7.470157] hub 1-0:1.0: unable to enumerate USB device on port 4
[    7.714163] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    7.908066] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    8.088061] usb 2-3: device descriptor read/64, error -62
[    8.372065] usb 2-3: device descriptor read/64, error -62
[    8.652058] usb 2-3: new full speed USB device using ohci_hcd and address 3
[    8.820082] usb 2-3: device descriptor read/64, error -62
[    9.104082] usb 2-3: device descriptor read/64, error -62
[    9.384069] usb 2-3: new full speed USB device using ohci_hcd and address 4
[    9.792044] usb 2-3: device not accepting address 4, error -62
[    9.968067] usb 2-3: new full speed USB device using ohci_hcd and address 5
[   10.376056] usb 2-3: device not accepting address 5, error -62
[   10.376077] hub 2-0:1.0: unable to enumerate USB device on port 3
[   10.552066] usb 2-4: new low speed USB device using ohci_hcd and address 6
[   10.732076] usb 2-4: device descriptor read/64, error -62
[   11.016076] usb 2-4: device descriptor read/64, error -62
[   11.296081] usb 2-4: new low speed USB device using ohci_hcd and address 7
[   11.476064] usb 2-4: device descriptor read/64, error -62
[   11.760064] usb 2-4: device descriptor read/64, error -62
[   12.040062] usb 2-4: new low speed USB device using ohci_hcd and address 8
[   12.448058] usb 2-4: device not accepting address 8, error -62
[   12.624056] usb 2-4: new low speed USB device using ohci_hcd and address 9
[   13.032060] usb 2-4: device not accepting address 9, error -62
[   13.032077] hub 2-0:1.0: unable to enumerate USB device on port 4
[   24.837915] Adding 10233364k swap on /dev/sda5.  Priority:-1 extents:1 across:10233364k 
[   25.047367] udev: starting version 151
[   25.134153] lp: driver loaded but no devices found
[   25.194847] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.219832] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   25.335610] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1f/LNXVIDEO:00/input/input6
[   25.335685] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.336097] Linux agpgart interface v0.103
[   25.479356] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   25.488483] sdhci: Secure Digital Host Controller Interface driver
[   25.488488] sdhci: Copyright(c) Pierre Ossman
[   25.490259] [drm] Initialized drm 1.1.0 20060810
[   25.490530] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[   25.490560]   alloc irq_desc for 23 on node -1
[   25.490563]   alloc kstat_irqs on node -1
[   25.490572] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   25.490680] Registered led device: mmc0::
[   25.490749] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
[   25.490770] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[   25.490790] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[   25.490800] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   25.490860] Registered led device: mmc1::
[   25.490896] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[   25.497968] acer-wmi: Acer Laptop ACPI-WMI Extras
[   25.504238] yenta_cardbus 0000:06:04.0: CardBus bridge found [1025:009f]
[   25.504291] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
[   25.504294] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
[   25.504303] yenta_cardbus 0000:06:04.0: TI: mfunc 0x90501212, devctl 0x44
[   25.504912] Registered led device: acer-wmi::mail
[   25.534671] type=1505 audit(1281619611.447:2):  operation="profile_load" pid=625 name="/sbin/dhclient3"
[   25.535030] type=1505 audit(1281619611.447:3):  operation="profile_load" pid=625 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.535231] type=1505 audit(1281619611.447:4):  operation="profile_load" pid=625 name="/usr/lib/connman/scripts/dhclient-script"
[   25.559363] cfg80211: Calling CRDA to update world regulatory domain
[   25.588806] cfg80211: World regulatory domain updated:
[   25.588813]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.588817]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.588821]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.588825]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.588829]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.588832]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.646708] [drm] radeon defaulting to kernel modesetting.
[   25.646715] [drm] radeon kernel modesetting enabled.
[   25.646798] radeon 0000:01:05.0: power state changed by ACPI to D0
[   25.646809] radeon 0000:01:05.0: power state changed by ACPI to D0
[   25.646821]   alloc irq_desc for 17 on node -1
[   25.646823]   alloc kstat_irqs on node -1
[   25.646833] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.651093] [drm] radeon: Initializing kernel modesetting.
[   25.657429] [drm] register mmio base: 0xC0100000
[   25.657433] [drm] register mmio size: 65536
[   25.657814] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   25.657838] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   25.657885] [drm] Generation 2 PCI interface, using max accessible memory
[   25.657889] [drm] radeon: VRAM 128M
[   25.657892] [drm] radeon: VRAM from 0x38000000 to 0x3FFFFFFF
[   25.657894] [drm] radeon: GTT 32M
[   25.657897] [drm] radeon: GTT from 0x40000000 to 0x41FFFFFF
[   25.657943] [drm] radeon: irq initialized.
[   25.658100] [drm] Detected VRAM RAM=128M, BAR=128M
[   25.658107] [drm] RAM width 128bits DDR
[   25.659051] [TTM] Zone  kernel: Available graphics memory: 444442 kiB.
[   25.659057] [TTM] Zone highmem: Available graphics memory: 447806 kiB.
[   25.659082] [drm] radeon: 128M of VRAM memory ready
[   25.659085] [drm] radeon: 32M of GTT memory ready.
[   25.659110] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   25.659699] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[   25.659716] [drm] radeon: cp idle (0x10000C03)
[   25.659780] [drm] Loading R300 Microcode
[   25.659788] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   25.675475] eth0: link down
[   25.675965] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.701632] [drm] radeon: ring at 0x0000000040000000
[   25.701654] [drm] ring test succeeded in 1 usecs
[   25.701863] [drm] radeon: ib pool ready.
[   25.701952] [drm] ib test succeeded in 0 usecs
[   25.701993] [drm] Default TV standard: NTSC
[   25.701996] [drm] 14.318180000 MHz TV ref clk
[   25.702097] [drm] Panel ID String: AUO                     
[   25.702101] [drm] Panel Size 1280x800
[   25.702165] [drm] Radeon Display Connectors
[   25.702168] [drm] Connector 0:
[   25.702170] [drm]   VGA
[   25.702174] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   25.702177] [drm]   Encoders:
[   25.702180] [drm]     CRT1: INTERNAL_DAC2
[   25.702182] [drm] Connector 1:
[   25.702184] [drm]   LVDS
[   25.702188] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   25.702191] [drm]   Encoders:
[   25.702193] [drm]     LCD1: INTERNAL_LVDS
[   25.737830] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   25.737837] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[   25.737849] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   25.737854] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[   25.738196] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   25.738201] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   25.744634]   alloc irq_desc for 22 on node -1
[   25.744639]   alloc kstat_irqs on node -1
[   25.744651] ath5k 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.744719] ath5k 0000:06:02.0: registered as 'phy0'
[   25.920017] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.005477] type=1505 audit(1281619611.919:5):  operation="profile_load" pid=746 name="/usr/share/gdm/guest-session/Xsession"
[   26.013040] type=1505 audit(1281619611.927:6):  operation="profile_replace" pid=747 name="/sbin/dhclient3"
[   26.013414] type=1505 audit(1281619611.927:7):  operation="profile_replace" pid=747 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.017382] type=1505 audit(1281619611.931:8):  operation="profile_replace" pid=747 name="/usr/lib/connman/scripts/dhclient-script"
[   26.031267] [drm] fb mappable at 0xC8040000
[   26.031270] [drm] vram apper at 0xC8000000
[   26.031273] [drm] size 4096000
[   26.031275] [drm] fb depth is 24
[   26.031277] [drm]    pitch is 5120
[   26.036062] type=1505 audit(1281619611.951:9):  operation="profile_load" pid=748 name="/usr/bin/evince"
[   26.041714] fb0: radeondrmfb frame buffer device
[   26.041719] registered panic notifier
[   26.041726] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   26.049421] vga16fb: initializing
[   26.049430] vga16fb: mapped to 0xc00a0000
[   26.049436] vga16fb: not registering due to another framebuffer present
[   26.050433] type=1505 audit(1281619611.963:10):  operation="profile_load" pid=748 name="/usr/bin/evince-previewer"
[   26.059373] type=1505 audit(1281619611.971:11):  operation="profile_load" pid=748 name="/usr/bin/evince-thumbnailer"
[   26.072970] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   26.079348] hda_codec: ALC883: BIOS auto-probing.
[   26.080737] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   26.110431] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   26.212726] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   26.215452] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   26.216591] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   26.217539] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   26.218549] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   26.232492] Console: switching to colour frame buffer device 160x50
[   26.474210] ath: EEPROM regdomain: 0x63
[   26.474215] ath: EEPROM indicates we should expect a direct regpair map
[   26.474221] ath: Country alpha2 being used: 00
[   26.474224] ath: Regpair used: 0x63
[   26.486890] phy0: Selected rate control algorithm 'minstrel'
[   26.487901] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   26.573658] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.799167] ppdev: user-space parallel port driver
[   29.616073] usb 2-3: new full speed USB device using ohci_hcd and address 10
[   29.784071] usb 2-3: device descriptor read/64, error -62
[   30.056071] usb 2-3: device descriptor read/64, error -62
[   30.336061] usb 2-3: new full speed USB device using ohci_hcd and address 11
[   30.517072] usb 2-3: device descriptor read/64, error -62
[   30.801088] usb 2-3: device descriptor read/64, error -62
[   31.069070] usb 2-3: new full speed USB device using ohci_hcd and address 12
[   31.477048] usb 2-3: device not accepting address 12, error -62
[   31.653068] usb 2-3: new full speed USB device using ohci_hcd and address 13
[   32.061038] usb 2-3: device not accepting address 13, error -62
[   32.061095] hub 2-0:1.0: unable to enumerate USB device on port 3
[   32.236229] usb 2-4: new low speed USB device using ohci_hcd and address 14
[   32.416080] usb 2-4: device descriptor read/64, error -62
[   32.700079] usb 2-4: device descriptor read/64, error -62
[   32.980082] usb 2-4: new low speed USB device using ohci_hcd and address 15
[   33.160080] usb 2-4: device descriptor read/64, error -62
[   33.444104] usb 2-4: device descriptor read/64, error -62
[   33.724059] usb 2-4: new low speed USB device using ohci_hcd and address 16
[   34.132060] usb 2-4: device not accepting address 16, error -62
[   34.308077] usb 2-4: new low speed USB device using ohci_hcd and address 17
[   34.716062] usb 2-4: device not accepting address 17, error -62
[   34.716085] hub 2-0:1.0: unable to enumerate USB device on port 4
[   37.684065] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   40.652069] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   43.620061] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   46.588067] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   46.936055] usb 2-3: new full speed USB device using ohci_hcd and address 18
[   47.104077] usb 2-3: device descriptor read/64, error -62
[   47.388062] usb 2-3: device descriptor read/64, error -62
[   47.668075] usb 2-3: new full speed USB device using ohci_hcd and address 19
[   47.848055] usb 2-3: device descriptor read/64, error -62
[   48.132066] usb 2-3: device descriptor read/64, error -62
[   48.412056] usb 2-3: new full speed USB device using ohci_hcd and address 20
[   48.820737] usb 2-3: device not accepting address 20, error -62
[   48.996072] usb 2-3: new full speed USB device using ohci_hcd and address 21
[   49.404055] usb 2-3: device not accepting address 21, error -62
[   49.404075] hub 2-0:1.0: unable to enumerate USB device on port 3
[   49.580070] usb 2-4: new low speed USB device using ohci_hcd and address 22
[   49.760058] usb 2-4: device descriptor read/64, error -62
[   50.028060] usb 2-4: device descriptor read/64, error -62
[   50.308084] usb 2-4: new low speed USB device using ohci_hcd and address 23
[   50.488057] usb 2-4: device descriptor read/64, error -62
[   50.772063] usb 2-4: device descriptor read/64, error -62
[   51.052062] usb 2-4: new low speed USB device using ohci_hcd and address 24
[   51.460058] usb 2-4: device not accepting address 24, error -62
[   51.636062] usb 2-4: new low speed USB device using ohci_hcd and address 25
[   52.044063] usb 2-4: device not accepting address 25, error -62
[   52.044082] hub 2-0:1.0: unable to enumerate USB device on port 4
[   87.676063] Clocksource tsc unstable (delta = -100324272 ns)
[  131.890678] wlan0: direct probe to AP 90:27:e4:5c:23:61 (try 1)
[  131.890735] wlan0: deauthenticating from 90:27:e4:5c:23:61 by local choice (reason=3)
[  131.890845] wlan0: direct probe to AP 90:27:e4:5c:23:61 (try 1)
[  131.894941] wlan0: direct probe responded
[  131.894956] wlan0: authenticate with AP 90:27:e4:5c:23:61 (try 1)
[  131.904411] wlan0: authenticated
[  131.904476] wlan0: associate with AP 90:27:e4:5c:23:61 (try 1)
[  131.912302] wlan0: RX AssocResp from 90:27:e4:5c:23:61 (capab=0x431 status=0 aid=1)
[  131.912313] wlan0: associated
[  131.914523] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  131.914701] cfg80211: Calling CRDA for country: US
[  131.924664] cfg80211: Received country IE:
[  131.924675] cfg80211: Regulatory domain: US
[  131.924681]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  131.924689]     (2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[  131.924695] cfg80211: CRDA thinks this should applied:
[  131.924700] cfg80211: Regulatory domain: US
[  131.924704]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  131.924711]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  131.924719]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  131.924726]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  131.924733]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  131.924740]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  131.924747]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  131.924753] cfg80211: We intersect both of these and get:
[  131.924757] cfg80211: Regulatory domain: 98
[  131.924762]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  131.924769]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  131.924782] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[  131.924788] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[  131.924794] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[  131.924808] cfg80211: Current regulatory domain updated by AP to: US
[  131.924813]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  131.924821]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  132.018332] padlock: VIA PadLock not detected.
[  141.980054] wlan0: no IPv6 routers present
```Thanks

---

### Post by exsoar on 2010-08-12
I have tried updating but still nothing. This seems to be pretty common with Ubuntu and Acer laptops.

---

