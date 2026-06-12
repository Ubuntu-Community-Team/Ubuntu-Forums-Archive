---
title: "SD Card Reader and Bluetooth chip problems on Aspire One 756"
date: 2015-08-19
forum: Hardware
---

### Post by thatmayh3mguy on 2015-08-19
I have this little netbook that I have been slowly upgrading and I've ran into two very annoying problems.

First problem is my SD card reader. the laptop is an Aspire one AO756-2623. When I originally bought it, it was running Windows 7 Starter. I have since replaced it with Ubuntu 14.04. ever since the OS change my SD card reader has stopped working entirely. I can't seem to find a solution for it

Second problem. I recently replaced my Wi-Fi chip with this one:
[http://www.amazon.com/gp/product/B00JY6X9HM?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s00](http://www.amazon.com/gp/product/B00JY6X9HM?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s00)
It was a pain to get it to work and even now the the Bluetooth options show there are no adapters. I've looked in additional drivers but it says its using an alternate driver. 

I'm not new to Linux but I'm nowhere near a pro or even a good novice. I'm learning everyday and I need help with this one guys 

here are the results of lsusb:

[code]
Bus 002 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b336 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[code]

here are the results of lspci:

[code]
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
04:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10)
[code]

---

### Post by weatherman2 on 2015-08-19
I've been running Ubuntu 12.04 on my AO756 for a few years.  I have upgraded the RAM to 16GB and the SSD to a 500GB SSD.  I upgraded wireless card to an Intel 6235 dual band + Bluetooth card; I have an Intel 7260 AC card ready to replace that one when I get around to it.  I've had great luck with Intel wireless cards in Ubuntu, so I stick with them.  The 6235 has worked great for two years, including bluetooth.

Obviously I can't help you with the with your wireless card as I have a different one in a different version of Ubuntu. One note: on my Acer, I can toggle wireless modes using the Fn + F3 key.  Each toggle sets a different combination of WiFi + bluetooth enabled; I can hit it once then both are disabled; hit it again and WiFi is enabled but Bluetooth still disabled; hit it again to enable both.  (Or something like that.)  Anyway, try hitting Fn + F3 a few times and see if anything changes with bluetooth for you.

My AO756 came with Windows 8.  In Windows 8 (still dual boot), I can any SDXC card, whether it was FAT32 (old style) or exFat.  In Ubuntu, to get my card reader to work at all, I had to add this to my /etc/rc.local file:

```

setpci -s 00:1c.2 0x50.B=0x40

```

I don't know if that will work for you with Ubuntu 14.04 but its worth a shot - just type it at the command line:

```

sudo setpci -s 00:1c.2 0x50.B=0x40
```

After that, I was able to read FAT32 cards but not exFat, the newer format used for SDXC cards and/or newer cameras.  (I think Windows has a soft limit on FAT32 partition size of 32GB, though you can make them larger than that; still, for larger cards like a 64GB SDXC card I have, the newer exFat format is used for larger partitions, I guess.)  exFat wasn't supported at all in Ubuntu 12.04 until I added support for it.  Once I did that, I could read my 64GB SDXC card with a USB card reader but still not the internal card reader - it still reads only FAT32 cards.  I never got around to making that work - had hoped it would work someday when I get around to upgrading to 14.04.  So, let me know if the setpci thing works for and what format card(s) you are able to read with it!

---

### Post by thatmayh3mguy on 2015-08-19
```

sudo setpci -s 00:1c.2 0x50.B=0x40
```

Did not work. :/

---

### Post by weatherman2 on 2015-08-19
What kind of card did you plug in afterward - exFat or FAT32?  (or something else?)

---

### Post by thatmayh3mguy on 2015-08-19
FAT32 32Gb 
[http://www.staples.com/Sandisk-Ultra-PLUS-SDSDQUT032GA46-microSDHC-32GB-Tablet-Flash-Memory-Card/product_1694937?cid=PS:GooglePLAs:1694937&ci_src=17588969&ci_sku=1694937&KPID=1694937&gclid=Cj0KEQjw0tCuBRDIjJ_Mlb6zzpQBEiQAyjCoBqj25GDb124mbANo6iQu-kCfPmUrZE_RYeOAW5hzdcgaAot98P8HAQ&kpid=1694937](http://www.staples.com/Sandisk-Ultra-PLUS-SDSDQUT032GA46-microSDHC-32GB-Tablet-Flash-Memory-Card/product_1694937?cid=PS:GooglePLAs:1694937&ci_src=17588969&ci_sku=1694937&KPID=1694937&gclid=Cj0KEQjw0tCuBRDIjJ_Mlb6zzpQBEiQAyjCoBqj25GDb124mbANo6iQu-kCfPmUrZE_RYeOAW5hzdcgaAot98P8HAQ&kpid=1694937)
this guy here

---

### Post by weatherman2 on 2015-08-19
Plug the card in again, then type:

```
dmesg
```

I don't remember needing to deal with tg3, but you might play with it as suggested in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178131)

There's another setpci suggestion there as well:

```
[COLOR=#333333][FONT=monospace]setpci -s 00:1c.2 0x50.B=0x41
```
[/FONT][/COLOR]
Your AO756 may not be identical to mine.

---

### Post by thatmayh3mguy on 2015-08-19
dmesg gets me this

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-25-generic (buildd@lgw01-20) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 (Ubuntu 3.19.0-25.26~14.04.1-generic 3.19.8-ckt2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-25-generic root=UUID=ae9723a8-4047-44ba-a588-03b467b25b87 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040200000-0x00000000a6abefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000a6abf000-0x00000000a6ebefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000a6ebf000-0x00000000a6fbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000a6fbf000-0x00000000a6ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000a6fff000-0x00000000a6ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000a7000000-0x00000000af9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Acer AO756/Mimic             , BIOS V1.02 04/26/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x24f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0A7000000 mask FFF000000 uncachable
[    0.000000]   3 base 0A8000000 mask FF8000000 uncachable
[    0.000000]   4 base 0B0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   6 base 100000000 mask F00000000 write-back
[    0.000000]   7 base 200000000 mask FC0000000 write-back
[    0.000000]   8 base 240000000 mask FF0000000 write-back
[    0.000000]   9 base 24F600000 mask FFFE00000 uncachable
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] e820: last_pfn = 0xa7000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x24f400000-0x24f5fffff]
[    0.000000]  [mem 0x24f400000-0x24f5fffff] page 2M
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x240000000-0x24f3fffff]
[    0.000000]  [mem 0x240000000-0x24f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x220000000-0x23fffffff]
[    0.000000]  [mem 0x220000000-0x23fffffff] page 2M
[    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x3fffffff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x40200000-0xa6abefff]
[    0.000000]  [mem 0x40200000-0xa69fffff] page 2M
[    0.000000]  [mem 0xa6a00000-0xa6abefff] page 4k
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xa6fff000-0xa6ffffff]
[    0.000000]  [mem 0xa6fff000-0xa6ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21fffffff]
[    0.000000]  [mem 0x100000000-0x21fffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35a30000-0x36d0ffff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FE020 000024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 0x00000000A6FFE210 00008C (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 0x00000000A6FFB000 0000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: DSDT 0x00000000A6FEC000 00B57F (v01 ACRSYS ACRPRDCT 00000000 1025 00040000)
[    0.000000] ACPI: FACS 0x00000000A6FBB000 000040
[    0.000000] ACPI: UEFI 0x00000000A6FFD000 000236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASF! 0x00000000A6FFC000 0000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: HPET 0x00000000A6FFA000 000038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: APIC 0x00000000A6FF9000 00008C (v02 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MCFG 0x00000000A6FF8000 00003C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SLIC 0x00000000A6FEB000 000176 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 0x00000000A6FEA000 0006FE (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
[    0.000000] ACPI: BOOT 0x00000000A6FE8000 000028 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASPT 0x00000000A6FE3000 000034 (v07 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: FPDT 0x00000000A6FE1000 000044 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 0x00000000A6FE0000 000758 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 0x00000000A6FDF000 000A92 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024f5fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x24f5f4000-0x24f5f8fff]
[    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246e00000-ffff88024ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x24f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x3fffffff]
[    0.000000]   node   0: [mem 0x40200000-0xa6abefff]
[    0.000000]   node   0: [mem 0xa6fff000-0xa6ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x24f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x24f5fffff]
[    0.000000] On node 0 totalpages: 2055260
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 156 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10587 pages used for memmap
[    0.000000]   DMA32 zone: 677568 pages, LIFO batch:31
[    0.000000]   Normal zone: 21464 pages used for memmap
[    0.000000]   Normal zone: 1373696 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xa7a00000-0xaf9fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40000000-0x401fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xa6abf000-0xa6ebefff]
[    0.000000] PM: Registered nosave memory: [mem 0xa6ebf000-0xa6fbefff]
[    0.000000] PM: Registered nosave memory: [mem 0xa6fbf000-0xa6ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xa7000000-0xaf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafa00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffc7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc80000-0xffffffff]
[    0.000000] e820: [mem 0xafa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88024f200000 s86144 r8192 d32640 u262144
[    0.000000] pcpu-alloc: s86144 r8192 d32640 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2022989
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-25-generic root=UUID=ae9723a8-4047-44ba-a588-03b467b25b87 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7988488K/8221040K available (7918K kernel code, 1172K rwdata, 3752K rodata, 1408K init, 1292K bss, 232552K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1396.811 MHz processor
[    0.000057] Calibrating delay loop (skipped), value calculated using timer frequency.. 2793.62 BogoMIPS (lpj=5587244)
[    0.000061] pid_max: default: 32768 minimum: 301
[    0.000069] ACPI: Core revision 20141107
[    0.012161] ACPI: All ACPI Tables successfully acquired
[    0.031546] Security Framework initialized
[    0.031571] AppArmor: AppArmor initialized
[    0.031573] Yama: becoming mindful.
[    0.032503] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.035291] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.036529] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.036546] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.036867] Initializing cgroup subsys memory
[    0.036875] Initializing cgroup subsys devices
[    0.036879] Initializing cgroup subsys freezer
[    0.036882] Initializing cgroup subsys net_cls
[    0.036885] Initializing cgroup subsys blkio
[    0.036888] Initializing cgroup subsys perf_event
[    0.036891] Initializing cgroup subsys net_prio
[    0.036894] Initializing cgroup subsys hugetlb
[    0.036932] CPU: Physical Processor ID: 0
[    0.036934] CPU: Processor Core ID: 0
[    0.036941] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.036941] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.036945] mce: CPU supports 7 MCE banks
[    0.036962] CPU0: Thermal monitoring enabled (TM1)
[    0.036970] process: using mwait in idle threads
[    0.036976] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.036976] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.037165] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
[    0.040003] ftrace: allocating 29988 entries in 118 pages
[    0.065676] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.105359] smpboot: CPU0: Intel(R) Celeron(R) CPU 877 @ 1.40GHz (fam: 06, model: 2a, stepping: 07)
[    0.105371] TSC deadline timer enabled
[    0.105410] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.105442] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.105446] ... version:                3
[    0.105448] ... bit width:              48
[    0.105449] ... generic registers:      8
[    0.105451] ... value mask:             0000ffffffffffff
[    0.105453] ... max period:             0000ffffffffffff
[    0.105454] ... fixed-purpose events:   3
[    0.105456] ... event mask:             00000007000000ff
[    0.106889] x86: Booting SMP configuration:
[    0.106892] .... node  #0, CPUs:      #1
[    0.119960] x86: Booted up 1 node, 2 CPUs
[    0.119965] smpboot: Total of 2 processors activated (5587.24 BogoMIPS)
[    0.120066] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.121992] devtmpfs: initialized
[    0.128814] evm: security.selinux
[    0.128817] evm: security.SMACK64
[    0.128819] evm: security.SMACK64EXEC
[    0.128820] evm: security.SMACK64TRANSMUTE
[    0.128822] evm: security.SMACK64MMAP
[    0.128823] evm: security.ima
[    0.128825] evm: security.capability
[    0.128922] PM: Registering ACPI NVS region [mem 0xa6ebf000-0xa6fbefff] (1048576 bytes)
[    0.129180] pinctrl core: initialized pinctrl subsystem
[    0.129355] RTC time:  0:32:08, date: 08/20/15
[    0.129526] NET: Registered protocol family 16
[    0.135988] cpuidle: using governor ladder
[    0.137756] cpuidle: using governor menu
[    0.137880] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.137883] ACPI: bus type PCI registered
[    0.137886] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.138022] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.138026] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.138553] PCI: Using configuration type 1 for base access
[    0.142431] ACPI: Added _OSI(Module Device)
[    0.142435] ACPI: Added _OSI(Processor Device)
[    0.142437] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.142439] ACPI: Added _OSI(Processor Aggregator Device)
[    0.147007] ACPI: Executed 1 blocks of module-level executable AML code
[    0.151058] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.151576] ACPI: Dynamic OEM Table Load:
[    0.151591] ACPI: SSDT 0xFFFF88024551A000 00083B (v01 PmRef  Cpu0Cst  00003001 INTL 20100121)
[    0.152524] ACPI: Dynamic OEM Table Load:
[    0.152535] ACPI: SSDT 0xFFFF880246896400 000303 (v01 PmRef  ApIst    00003000 INTL 20100121)
[    0.153339] ACPI: Dynamic OEM Table Load:
[    0.153347] ACPI: SSDT 0xFFFF8802454C1800 000119 (v01 PmRef  ApCst    00003000 INTL 20100121)
[    0.154420] ACPI: Interpreter enabled
[    0.154430] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.154438] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.154460] ACPI: (supports S0 S3 S4 S5)
[    0.154462] ACPI: Using IOAPIC for interrupt routing
[    0.154503] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.303977] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.303987] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.304096] \_SB_.PCI0:_OSC invalid UUID
[    0.304098] _OSC request data:1 1f 0 
[    0.304104] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.305157] PCI host bridge to bus 0000:00
[    0.305162] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.305165] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.305168] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.305172] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.305175] pci_bus 0000:00: root bus resource [mem 0xafa00000-0xfeafffff]
[    0.305187] pci 0000:00:00.0: [8086:0104] type 00 class 0x060000
[    0.305329] pci 0000:00:02.0: [8086:0106] type 00 class 0x030000
[    0.305347] pci 0000:00:02.0: reg 0x10: [mem 0xc0000000-0xc03fffff 64bit]
[    0.305356] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.305364] pci 0000:00:02.0: reg 0x20: [io  0x2000-0x203f]
[    0.305544] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.305585] pci 0000:00:16.0: reg 0x10: [mem 0xc0804000-0xc080400f 64bit]
[    0.305718] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.305869] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.306172] pci 0000:00:1a.0: reg 0x10: [mem 0xc0809000-0xc08093ff]
[    0.307884] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.307975] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.308054] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.308087] pci 0000:00:1b.0: reg 0x10: [mem 0xc0800000-0xc0803fff 64bit]
[    0.308235] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.308302] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.308369] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.308530] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.308604] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.308669] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.308828] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.308900] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.308966] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    0.309127] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.309197] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.309278] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.309577] pci 0000:00:1d.0: reg 0x10: [mem 0xc0808000-0xc08083ff]
[    0.311298] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.311387] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.311456] pci 0000:00:1f.0: [8086:1e5e] type 00 class 0x060100
[    0.311741] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.311780] pci 0000:00:1f.2: reg 0x10: [io  0x2088-0x208f]
[    0.311796] pci 0000:00:1f.2: reg 0x14: [io  0x2094-0x2097]
[    0.311812] pci 0000:00:1f.2: reg 0x18: [io  0x2080-0x2087]
[    0.311829] pci 0000:00:1f.2: reg 0x1c: [io  0x2090-0x2093]
[    0.311845] pci 0000:00:1f.2: reg 0x20: [io  0x2060-0x207f]
[    0.311861] pci 0000:00:1f.2: reg 0x24: [mem 0xc0807000-0xc08077ff]
[    0.311961] pci 0000:00:1f.2: PME# supported from D3hot
[    0.312084] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.312114] pci 0000:00:1f.3: reg 0x10: [mem 0xc0805000-0xc08050ff 64bit]
[    0.312155] pci 0000:00:1f.3: reg 0x20: [io  0x2040-0x205f]
[    0.312404] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.312601] pci 0000:03:00.0: [14e4:43b1] type 00 class 0x028000
[    0.312642] pci 0000:03:00.0: reg 0x10: [mem 0xc0600000-0xc0607fff 64bit]
[    0.312671] pci 0000:03:00.0: reg 0x18: [mem 0xc0400000-0xc05fffff 64bit]
[    0.312864] pci 0000:03:00.0: supports D1 D2
[    0.312867] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312920] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.313036] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.313048] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc06fffff]
[    0.313244] pci 0000:04:00.0: [14e4:16b5] type 00 class 0x020000
[    0.313291] pci 0000:04:00.0: reg 0x10: [mem 0xc0710000-0xc071ffff 64bit pref]
[    0.313323] pci 0000:04:00.0: reg 0x18: [mem 0xc0720000-0xc072ffff 64bit pref]
[    0.313381] pci 0000:04:00.0: reg 0x30: [mem 0xfffff800-0xffffffff pref]
[    0.313539] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.313597] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.313709] pci 0000:04:00.1: [14e4:16bc] type 00 class 0x080501
[    0.313753] pci 0000:04:00.1: reg 0x10: [mem 0xc0700000-0xc070ffff 64bit pref]
[    0.313984] pci 0000:04:00.1: PME# supported from D0 D3hot D3cold
[    0.322081] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.322113] pci 0000:00:1c.2:   bridge window [mem 0xc0700000-0xc07fffff 64bit pref]
[    0.394522] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.394602] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.394678] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.394756] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.394830] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.394908] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.394984] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.395064] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.395183] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.395238] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.395402] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.395406] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.395410] vgaarb: loaded
[    0.395412] vgaarb: bridge control possible 0000:00:02.0
[    0.395794] SCSI subsystem initialized
[    0.395867] libata version 3.00 loaded.
[    0.395909] ACPI: bus type USB registered
[    0.395943] usbcore: registered new interface driver usbfs
[    0.395957] usbcore: registered new interface driver hub
[    0.395979] usbcore: registered new device driver usb
[    0.396185] PCI: Using ACPI for IRQ routing
[    0.405082] PCI: pci_cache_line_size set to 64 bytes
[    0.405276] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.405279] e820: reserve RAM buffer [mem 0xa6abf000-0xa7ffffff]
[    0.405281] e820: reserve RAM buffer [mem 0xa7000000-0xa7ffffff]
[    0.405284] e820: reserve RAM buffer [mem 0x24f600000-0x24fffffff]
[    0.405472] NetLabel: Initializing
[    0.405475] NetLabel:  domain hash size = 128
[    0.405476] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.405496] NetLabel:  unlabeled traffic allowed by default
[    0.405598] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.405607] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.407659] Switched to clocksource hpet
[    0.416595] AppArmor: AppArmor Filesystem Enabled
[    0.416699] pnp: PnP ACPI init
[    0.416817] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.416921] pnp 00:01: Plug and Play ACPI device, IDs SYN1b61 SYN1b00 SYN0002 PNP0f13 (active)
[    0.417109] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.417114] system 00:02: [io  0xfd60-0xfd63] has been reserved
[    0.417117] system 00:02: [io  0x1000-0x100f] has been reserved
[    0.417120] system 00:02: [io  0xffff] has been reserved
[    0.417123] system 00:02: [io  0xffff] has been reserved
[    0.417127] system 00:02: [io  0x0400-0x0453] could not be reserved
[    0.417131] system 00:02: [io  0x0458-0x047f] has been reserved
[    0.417134] system 00:02: [io  0x0500-0x057f] has been reserved
[    0.417137] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.417142] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.417183] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.417259] system 00:04: [io  0x0454-0x0457] has been reserved
[    0.417263] system 00:04: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.487912] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.487917] system 00:05: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.487920] system 00:05: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.487923] system 00:05: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.487927] system 00:05: [mem 0xe0000000-0xefffffff] has been reserved
[    0.487930] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.487933] system 00:05: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.487937] system 00:05: [mem 0xff000000-0xff000fff] has been reserved
[    0.487941] system 00:05: [mem 0xff010000-0xffffffff] could not be reserved
[    0.487944] system 00:05: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.487948] system 00:05: [mem 0xafa00000-0xafa00fff] has been reserved
[    0.487952] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.488299] system 00:06: [mem 0x20000000-0x201fffff] has been reserved
[    0.488303] system 00:06: [mem 0x40000000-0x401fffff] has been reserved
[    0.488307] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.488333] pnp: PnP ACPI: found 7 devices
[    0.495663] pci 0000:04:00.0: can't claim BAR 6 [mem 0xfffff800-0xffffffff pref]: no compatible bridge window
[    0.495686] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.495691] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.495694] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.495728] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.495731] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.495734] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.495742] pci 0000:00:1c.0: BAR 14: assigned [mem 0xafb00000-0xafcfffff]
[    0.495749] pci 0000:00:1c.0: BAR 15: assigned [mem 0xafd00000-0xafefffff 64bit pref]
[    0.495753] pci 0000:00:1c.2: BAR 14: assigned [mem 0xaff00000-0xafffffff]
[    0.495758] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.495762] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.495767] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.495776] pci 0000:00:1c.0:   bridge window [mem 0xafb00000-0xafcfffff]
[    0.495783] pci 0000:00:1c.0:   bridge window [mem 0xafd00000-0xafefffff 64bit pref]
[    0.495794] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.495803] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc06fffff]
[    0.495819] pci 0000:04:00.0: BAR 6: assigned [mem 0xaff00000-0xaff007ff pref]
[    0.495822] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.495831] pci 0000:00:1c.2:   bridge window [mem 0xaff00000-0xafffffff]
[    0.495838] pci 0000:00:1c.2:   bridge window [mem 0xc0700000-0xc07fffff 64bit pref]
[    0.495850] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.495853] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.495856] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.495858] pci_bus 0000:00: resource 7 [mem 0xafa00000-0xfeafffff]
[    0.495862] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.495864] pci_bus 0000:02: resource 1 [mem 0xafb00000-0xafcfffff]
[    0.495867] pci_bus 0000:02: resource 2 [mem 0xafd00000-0xafefffff 64bit pref]
[    0.495871] pci_bus 0000:03: resource 1 [mem 0xc0400000-0xc06fffff]
[    0.495874] pci_bus 0000:04: resource 1 [mem 0xaff00000-0xafffffff]
[    0.495877] pci_bus 0000:04: resource 2 [mem 0xc0700000-0xc07fffff 64bit pref]
[    0.495920] NET: Registered protocol family 2
[    0.496198] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.496465] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.496680] TCP: Hash tables configured (established 65536 bind 65536)
[    0.496719] TCP: reno registered
[    0.496739] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.496791] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.496904] NET: Registered protocol family 1
[    0.496927] pci 0000:00:02.0: Video device with shadowed ROM
[    0.527903] PCI: CLS 64 bytes, default 64
[    0.527986] Trying to unpack rootfs image as initramfs...
[    1.047727] Freeing initrd memory: 19328K (ffff880035a30000 - ffff880036d10000)
[    1.047739] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.047743] software IO TLB [mem 0xa2abf000-0xa6abf000] (64MB) mapped at [ffff8800a2abf000-ffff8800a6abefff]
[    1.047803] Simple Boot Flag at 0x44 set to 0x1
[    1.047960] RAPL PMU detected, hw unit 2^-16 Joules, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    1.048036] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x26
[    1.048045] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x26
[    1.048118] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.048157] Scanning for low memory corruption every 60 seconds
[    1.048728] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.048760] Initialise system trusted keyring
[    1.048794] audit: initializing netlink subsys (disabled)
[    1.048816] audit: type=2000 audit(1440030729.024:1): initialized
[    1.049322] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.051762] zpool: loaded
[    1.051767] zbud: loaded
[    1.052044] VFS: Disk quotas dquot_6.5.2
[    1.052110] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.052854] fuse init (API version 7.23)
[    1.053080] Key type big_key registered
[    1.053591] Key type asymmetric registered
[    1.053597] Asymmetric key parser 'x509' registered
[    1.053659] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.053710] io scheduler noop registered
[    1.053717] io scheduler deadline registered (default)
[    1.053771] io scheduler cfq registered
[    1.054515] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.054543] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.054591] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    1.054593] vesafb: scrolling: redraw
[    1.054596] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.054604] mtrr: type mismatch for b0000000,800000 old: write-back new: write-combining
[    1.054607] mtrr: type mismatch for b0000000,400000 old: write-back new: write-combining
[    1.054610] mtrr: type mismatch for b0000000,200000 old: write-back new: write-combining
[    1.054612] mtrr: type mismatch for b0000000,100000 old: write-back new: write-combining
[    1.054615] mtrr: type mismatch for b0000000,80000 old: write-back new: write-combining
[    1.054618] mtrr: type mismatch for b0000000,40000 old: write-back new: write-combining
[    1.054621] mtrr: type mismatch for b0000000,20000 old: write-back new: write-combining
[    1.054623] mtrr: type mismatch for b0000000,10000 old: write-back new: write-combining
[    1.054626] mtrr: type mismatch for b0000000,8000 old: write-back new: write-combining
[    1.054629] mtrr: type mismatch for b0000000,4000 old: write-back new: write-combining
[    1.054632] mtrr: type mismatch for b0000000,2000 old: write-back new: write-combining
[    1.054634] mtrr: type mismatch for b0000000,1000 old: write-back new: write-combining
[    1.054659] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90010e80000, using 4160k, total 4160k
[    1.054792] Console: switching to colour frame buffer device 170x48
[    1.054819] fb0: VESA VGA frame buffer device
[    1.054845] intel_idle: MWAIT substates: 0x21120
[    1.054847] intel_idle: v0.4 model 0x2A
[    1.054849] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.055099] ACPI: AC Adapter [ACAD] (off-line)
[    1.055254] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[    1.055261] ACPI: Power Button [PWRB]
[    1.055327] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0D:00/input/input1
[    1.055353] ACPI: Lid Switch [LID0]
[    1.055412] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input2
[    1.055416] ACPI: Sleep Button [SLPB]
[    1.055481] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.055485] ACPI: Power Button [PWRF]
[    1.055777] GHES: HEST is not enabled!
[    1.055947] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.407761] ACPI: Battery Slot [BAT1] (battery present)
[    1.408001] Linux agpgart interface v0.103
[    1.411150] brd: module loaded
[    1.412203] loop: module loaded
[    1.412542] libphy: Fixed MDIO Bus: probed
[    1.412549] tun: Universal TUN/TAP device driver, 1.6
[    1.412551] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.412622] PPP generic driver version 2.4.2
[    1.412744] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.412753] ehci-pci: EHCI PCI platform driver
[    1.412937] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.412946] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.412967] ehci-pci 0000:00:1a.0: debug port 2
[    1.416889] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.416913] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc0809000
[    1.427554] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.427626] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.427629] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.427632] usb usb1: Product: EHCI Host Controller
[    1.427634] usb usb1: Manufacturer: Linux 3.19.0-25-generic ehci_hcd
[    1.427637] usb usb1: SerialNumber: 0000:00:1a.0
[    1.427860] hub 1-0:1.0: USB hub found
[    1.427870] hub 1-0:1.0: 2 ports detected
[    1.428171] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.428179] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.428197] ehci-pci 0000:00:1d.0: debug port 2
[    1.432115] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.432133] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc0808000
[    1.443659] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.443761] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.443765] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.443768] usb usb2: Product: EHCI Host Controller
[    1.443771] usb usb2: Manufacturer: Linux 3.19.0-25-generic ehci_hcd
[    1.443774] usb usb2: SerialNumber: 0000:00:1d.0
[    1.444086] hub 2-0:1.0: USB hub found
[    1.444099] hub 2-0:1.0: 2 ports detected
[    1.444284] ehci-platform: EHCI generic platform driver
[    1.444306] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.444317] ohci-pci: OHCI PCI platform driver
[    1.444337] ohci-platform: OHCI generic platform driver
[    1.444351] uhci_hcd: USB Universal Host Controller Interface driver
[    1.444447] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS1] at 0x60,0x64 irq 1,12
[    1.457833] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.457840] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.458262] mousedev: PS/2 mouse device common for all mice
[    1.459098] rtc_cmos 00:03: RTC can wake from S4
[    1.459313] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.459350] rtc_cmos 00:03: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.459379] i2c /dev entries driver
[    1.459486] device-mapper: uevent: version 1.0.3
[    1.459617] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    1.459638] Intel P-state driver initializing.
[    1.459857] Consider also installing thermald for improved thermal control.
[    1.459876] ledtrig-cpu: registered to indicate activity on CPUs
[    1.460597] PCCT header not found.
[    1.460601] ACPI PCC probe failed.
[    1.460885] TCP: cubic registered
[    1.461188] NET: Registered protocol family 10
[    1.461734] NET: Registered protocol family 17
[    1.461751] Key type dns_resolver registered
[    1.462252] Loading compiled-in X.509 certificates
[    1.465034] Loaded X.509 cert 'Magrathea: Glacier signing key: 6aaa11d18c2d3a40b1b4dbe5bf8ad656ddf51838'
[    1.465076] registered taskstats version 1
[    1.469478] Key type trusted registered
[    1.474323] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.476224] Key type encrypted registered
[    1.476238] AppArmor: AppArmor sha1 policy hashing enabled
[    1.476245] ima: No TPM chip found, activating TPM-bypass!
[    1.476277] evm: HMAC attrs: 0x1
[    1.476876]   Magic number: 11:987:506
[    1.476993] rtc_cmos 00:03: setting system clock to 2015-08-20 00:32:09 UTC (1440030729)
[    1.477070] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.477072] EDD information not available.
[    1.477209] PM: Hibernation image not present or could not be loaded.
[    1.477689] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    1.477692] Write protecting the kernel read-only data: 12288k
[    1.478004] Freeing unused kernel memory: 260K (ffff8800017bf000 - ffff880001800000)
[    1.478150] Freeing unused kernel memory: 344K (ffff880001baa000 - ffff880001c00000)
[    1.498099] systemd-udevd[103]: starting version 204
[    1.543411] pps_core: LinuxPPS API ver. 1 registered
[    1.543416] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.543823] sdhci: Secure Digital Host Controller Interface driver
[    1.543827] sdhci: Copyright(c) Pierre Ossman
[    1.545689] PTP clock support registered
[    1.546184] sdhci-pci 0000:04:00.1: SDHCI controller found [14e4:16bc] (rev 10)
[    1.546420] sdhci-pci 0000:04:00.1: No vmmc regulator found
[    1.546423] sdhci-pci 0000:04:00.1: No vqmmc regulator found
[    1.552683] ahci 0000:00:1f.2: version 3.0
[    1.552916] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.552942] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x1 impl SATA mode
[    1.552947] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[    1.554660] mmc0: SDHCI controller on PCI [0000:04:00.1] using ADMA 64-bit
[    1.556413] tg3.c:v3.137 (May 11, 2014)
[    1.558160] scsi host0: ahci
[    1.565139] scsi host1: ahci
[    1.565405] scsi host2: ahci
[    1.565533] scsi host3: ahci
[    1.565614] ata1: SATA max UDMA/133 abar m2048@0xc0807000 port 0xc0807100 irq 24
[    1.565617] ata2: DUMMY
[    1.565619] ata3: DUMMY
[    1.565621] ata4: DUMMY
[    1.611804] tg3 0000:04:00.0 eth0: Tigon3 [partno(BCM57785) rev 57785100] (PCI Express) MAC address dc:0e:a1:b7:86:5d
[    1.611811] tg3 0000:04:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    1.611815] tg3 0000:04:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.611818] tg3 0000:04:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    1.739650] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.755647] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.873327] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.873334] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.873765] hub 1-1:1.0: USB hub found
[    1.873907] hub 1-1:1.0: 4 ports detected
[    1.883600] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.884035] ata1.00: supports DRM functions and may not be fully accessible
[    1.887000] ata1.00: disabling queued TRIM support
[    1.887010] ata1.00: ATA-9: Crucial_CT240M500SSD1, MU03, max UDMA/133
[    1.887015] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.887936] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.887943] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.888328] hub 2-1:1.0: USB hub found
[    1.888397] hub 2-1:1.0: 4 ports detected
[    1.890669] ata1.00: supports DRM functions and may not be fully accessible
[    1.893623] ata1.00: disabling queued TRIM support
[    1.897008] ata1.00: configured for UDMA/133
[    1.897321] scsi 0:0:0:0: Direct-Access     ATA      Crucial_CT240M50 MU03 PQ: 0 ANSI: 5
[    1.897803] ata1.00: Enabling discard_zeroes_data
[    1.897826] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
[    1.897830] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.897857] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.897980] sd 0:0:0:0: [sda] Write Protect is off
[    1.897984] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.898036] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.898164] ata1.00: Enabling discard_zeroes_data
[    1.898668]  sda: sda1 sda2 < sda5 >
[    1.899098] ata1.00: Enabling discard_zeroes_data
[    1.899281] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.948324] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.047497] tsc: Refined TSC clocksource calibration: 1396.826 MHz
[    2.066566] random: init urandom read with 15 bits of entropy available
[    2.099528] init: plymouth-upstart-bridge main process (170) terminated with status 1
[    2.099548] init: plymouth-upstart-bridge main process ended, respawning
[    2.112584] init: plymouth-upstart-bridge main process (180) terminated with status 1
[    2.112612] init: plymouth-upstart-bridge main process ended, respawning
[    2.127695] init: plymouth-upstart-bridge main process (190) terminated with status 1
[    2.127773] init: plymouth-upstart-bridge main process ended, respawning
[    2.143624] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    2.231724] psmouse serio1: synaptics: queried max coordinates: x [..5702], y [..4806]
[    2.282110] usb 1-1.3: New USB device found, idVendor=04f2, idProduct=b336
[    2.282116] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.282119] usb 1-1.3: Product: HD WebCam
[    2.282122] usb 1-1.3: Manufacturer: HD WebCam
[    2.286393] psmouse serio1: synaptics: queried min coordinates: x [1240..], y [1048..]
[    2.335866] Adding 8219644k swap on /dev/sda5.  Priority:-1 extents:1 across:8219644k SSFS
[    2.390895] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x126c00, board id: 2292, fw id: 1146734
[    2.456844] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    2.464681] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    2.831434] systemd-udevd[372]: starting version 204
[    2.910222] lp: driver loaded but no devices found
[    2.927675] ppdev: user-space parallel port driver
[    3.019563] wmi: Mapper loaded
[    3.057823] Switched to clocksource tsc
[    3.067270] Bluetooth: Core ver 2.20
[    3.067722] NET: Registered protocol family 31
[    3.067726] Bluetooth: HCI device and connection manager initialized
[    3.067733] Bluetooth: HCI socket layer initialized
[    3.067737] Bluetooth: L2CAP socket layer initialized
[    3.067748] Bluetooth: SCO socket layer initialized
[    3.091686] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.091691] Bluetooth: BNEP filters: protocol multicast
[    3.091698] Bluetooth: BNEP socket layer initialized
[    3.101509] Bluetooth: RFCOMM TTY layer initialized
[    3.101522] Bluetooth: RFCOMM socket layer initialized
[    3.101532] Bluetooth: RFCOMM ver 1.11
[    3.177156] audit: type=1400 audit(1440030731.197:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=479 comm="apparmor_parser"
[    3.177168] audit: type=1400 audit(1440030731.197:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=479 comm="apparmor_parser"
[    3.177877] audit: type=1400 audit(1440030731.197:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=479 comm="apparmor_parser"
[    3.199219] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.283371] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20141107/utaddress-258)
[    3.283383] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.283388] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[    3.283393] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.283395] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[    3.283400] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.283402] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[    3.283407] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.283408] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.292903] cfg80211: Calling CRDA to update world regulatory domain
[    3.335928] audit: type=1400 audit(1440030731.357:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=504 comm="apparmor_parser"
[    3.377365] media: Linux media interface: v0.10
[    3.392220] audit: type=1400 audit(1440030731.413:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=513 comm="apparmor_parser"
[    3.392233] audit: type=1400 audit(1440030731.413:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=513 comm="apparmor_parser"
[    3.392240] audit: type=1400 audit(1440030731.413:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=513 comm="apparmor_parser"
[    3.392955] audit: type=1400 audit(1440030731.413:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=513 comm="apparmor_parser"
[    3.392964] audit: type=1400 audit(1440030731.413:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=513 comm="apparmor_parser"
[    3.433316] [drm] Initialized drm 1.1.0 20060810
[    3.437637] Linux video capture interface: v2.00
[    3.518122] wl: module license 'MIXED/Proprietary' taints kernel.
[    3.518128] Disabling lock debugging due to kernel taint
[    3.529656] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    3.616676] uvcvideo: Found UVC 1.00 device HD WebCam (04f2:b336)
[    3.631497] input: HD WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input7
[    3.631713] usbcore: registered new interface driver uvcvideo
[    3.631716] USB Video Class driver (1.1.1)
[    3.646244] [drm] Memory usable by graphics device = 2048M
[    3.646251] checking generic (b0000000 410000) vs hw (b0000000 10000000)
[    3.646254] fb: switching to inteldrmfb from VESA VGA
[    3.646299] Console: switching to colour dummy device 80x25
[    3.646424] [drm] Replacing VGA console driver
[    3.660702] intel_rapl: Found RAPL domain package
[    3.660708] intel_rapl: Found RAPL domain core
[    3.660710] intel_rapl: Found RAPL domain uncore
[    3.675430] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.675435] [drm] Driver supports precise vblank timestamp query.
[    3.675617] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.737008] fbcon: inteldrmfb (fb0) is primary device
[    3.737086] Console: switching to colour frame buffer device 170x48
[    3.737119] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.737122] i915 0000:00:02.0: registered panic notifier
[    3.799339] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[    3.800797] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.802007] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    3.802181] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[    3.865014] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.865021] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.865025] sound hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.865027] sound hdaudioC0D0:    mono: mono_out=0x0
[    3.865029] sound hdaudioC0D0:    inputs:
[    3.865033] sound hdaudioC0D0:      Internal Mic=0x1b
[    3.865036] sound hdaudioC0D0:      Mic=0x19
[    3.903141] acer_wmi: Acer Laptop ACPI-WMI Extras
[    3.903159] acer_wmi: Function bitmap for Communication Button: 0x1
[    3.916552] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    3.916716] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    3.916875] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    3.954400] acer_wmi: Brightness must be controlled by acpi video driver
[    3.994121] input: Acer WMI hotkeys as /devices/virtual/input/input12
[    3.995138] input: Acer BMA150 accelerometer as /devices/virtual/input/input13
[    4.002784] random: nonblocking pool is initialized
[    4.007693] cfg80211: World regulatory domain updated:
[    4.007699] cfg80211:  DFS Master region: unset
[    4.007701] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    4.007705] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    4.007709] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    4.007712] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    4.007714] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    4.007717] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    4.081995] init: failsafe main process (600) killed by TERM signal
[    4.951157] mmc0: new ultra high speed DDR50 SDHC card at address aaaa
[    4.957033] Driver 'mmcblk' needs updating - please use bus_type methods
[    4.957195] mmcblk0: mmc0:aaaa SL32G 29.7 GiB 
[    4.970847] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.970853] mmcblk0: retrying using single block read
[    4.971372] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.971377] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.973312] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.973721] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.973724] mmcblk0: retrying using single block read
[    4.974069] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.974072] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.976032] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.976472] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.976474] mmcblk0: retrying using single block read
[    4.976816] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.976819] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.978685] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.979223] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.979226] mmcblk0: retrying using single block read
[    4.979563] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.979566] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.981445] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.981855] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.981857] mmcblk0: retrying using single block read
[    4.982206] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.982209] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.984126] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.984497] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.984499] mmcblk0: retrying using single block read
[    4.984846] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.984849] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.986727] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.987274] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.987277] mmcblk0: retrying using single block read
[    4.987625] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.987627] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.989515] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.989919] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.989922] mmcblk0: retrying using single block read
[    4.990268] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.990271] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.992365] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.992375] ldm_validate_partition_table(): Disk read failed.
[    4.992767] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.992769] mmcblk0: retrying using single block read
[    4.993117] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.993120] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.995007] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.995445] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.995448] mmcblk0: retrying using single block read
[    4.995833] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    4.995836] blk_update_request: I/O error, dev mmcblk0, sector 0
[    4.997764] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[    4.998140] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    4.998142] mmcblk0: retrying using single block read
[    4.998488] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.000826] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.000830] mmcblk0: retrying using single block read
[    5.001174] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.003036] Dev mmcblk0: unable to read RDB block 0
[    5.003467] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.003470] mmcblk0: retrying using single block read
[    5.003812] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.006132] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.006135] mmcblk0: retrying using single block read
[    5.006480] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.009472] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.009475] mmcblk0: retrying using single block read
[    5.009820] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.012168] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.012170] mmcblk0: retrying using single block read
[    5.012516] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.014393]  mmcblk0: unable to read partition table
[    5.026533] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.026539] mmcblk0: retrying using single block read
[    5.026875] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.029327] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.029330] mmcblk0: retrying using single block read
[    5.029674] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.039186] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.039189] mmcblk0: retrying using single block read
[    5.039528] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.041851] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.041854] mmcblk0: retrying using single block read
[    5.042200] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.044499] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.044503] mmcblk0: retrying using single block read
[    5.044848] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.047274] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.047278] mmcblk0: retrying using single block read
[    5.047621] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.049917] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.049920] mmcblk0: retrying using single block read
[    5.050265] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.052678] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.052681] mmcblk0: retrying using single block read
[    5.052993] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.055279] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.055282] mmcblk0: retrying using single block read
[    5.055626] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.058410] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.058413] mmcblk0: retrying using single block read
[    5.058760] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.061048] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.061051] mmcblk0: retrying using single block read
[    5.061398] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.063765] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.063768] mmcblk0: retrying using single block read
[    5.064111] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.066400] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.066402] mmcblk0: retrying using single block read
[    5.066747] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.069124] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.069127] mmcblk0: retrying using single block read
[    5.069470] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.071876] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.071879] mmcblk0: retrying using single block read
[    5.072257] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.074571] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.074573] mmcblk0: retrying using single block read
[    5.074922] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.077589] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.077593] mmcblk0: retrying using single block read
[    5.077905] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.080183] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.080186] mmcblk0: retrying using single block read
[    5.080500] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.082774] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.082777] mmcblk0: retrying using single block read
[    5.087884] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.091976] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.091980] mmcblk0: retrying using single block read
[    5.095244] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.097545] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.097548] mmcblk0: retrying using single block read
[    5.097855] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.100108] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.100111] mmcblk0: retrying using single block read
[    5.100418] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.102627] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.102630] mmcblk0: retrying using single block read
[    5.102944] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.106022] mmcblk0: error -84 transferring data, sector 120, nr 8, cmd response 0x900, card status 0xb00
[    5.106025] mmcblk0: retrying using single block read
[    5.108493] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.108496] mmcblk0: retrying using single block read
[    5.108805] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.111160] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.111163] mmcblk0: retrying using single block read
[    5.111489] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.113752] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.113755] mmcblk0: retrying using single block read
[    5.114071] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.116339] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.116343] mmcblk0: retrying using single block read
[    5.116637] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.118899] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.118902] mmcblk0: retrying using single block read
[    5.119270] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.121280] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.122717] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.122724] mmcblk0: retrying using single block read
[    5.123037] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.134178] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.134185] mmcblk0: retrying using single block read
[    5.134563] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.135976] mmcblk0: error -84 transferring data, sector 4, nr 4, cmd response 0x900, card status 0x0
[    5.138058] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.138064] mmcblk0: retrying using single block read
[    5.138382] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.141279] mmcblk0: error -84 transferring data, sector 128, nr 8, cmd response 0x900, card status 0xb00
[    5.141284] mmcblk0: retrying using single block read
[    5.141597] mmcblk0: error -84 transferring data, sector 128, nr 8, cmd response 0x900, card status 0x0
[    5.145673] mmcblk0: error -84 transferring data, sector 264, nr 8, cmd response 0x900, card status 0xb00
[    5.145679] mmcblk0: retrying using single block read
[    5.146696] mmcblk0: error -84 transferring data, sector 266, nr 6, cmd response 0x900, card status 0x0
[    5.148573] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.148578] mmcblk0: retrying using single block read
[    5.148979] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.151606] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.151611] mmcblk0: retrying using single block read
[    5.151948] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.154301] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.154304] mmcblk0: retrying using single block read
[    5.154604] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.157485] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.157491] mmcblk0: retrying using single block read
[    5.157796] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.163163] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.163168] mmcblk0: retrying using single block read
[    5.163527] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.165786] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.165789] mmcblk0: retrying using single block read
[    5.166096] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.168452] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.168456] mmcblk0: retrying using single block read
[    5.168764] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.169563] mmcblk0: error -84 transferring data, sector 3, nr 5, cmd response 0x900, card status 0x0
[    5.170983] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.170986] mmcblk0: retrying using single block read
[    5.171296] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.173578] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.173581] mmcblk0: retrying using single block read
[    5.173894] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.177283] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.177288] mmcblk0: retrying using single block read
[    5.177595] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.183027] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.183030] mmcblk0: retrying using single block read
[    5.183428] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.185864] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.185867] mmcblk0: retrying using single block read
[    5.186173] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.188449] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.188452] mmcblk0: retrying using single block read
[    5.188760] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.190980] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.190982] mmcblk0: retrying using single block read
[    5.193466] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.195908] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.195913] mmcblk0: retrying using single block read
[    5.196224] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.197109] mmcblk0: error -84 transferring data, sector 3, nr 5, cmd response 0x900, card status 0x0
[    5.198656] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.198662] mmcblk0: retrying using single block read
[    5.198977] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.202586] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.202592] mmcblk0: retrying using single block read
[    5.202900] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.205652] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.205655] mmcblk0: retrying using single block read
[    5.205972] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.207061] mmcblk0: error -84 transferring data, sector 4, nr 4, cmd response 0x900, card status 0x0
[    5.208738] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.208741] mmcblk0: retrying using single block read
[    5.209059] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.211320] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.211323] mmcblk0: retrying using single block read
[    5.211632] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.214098] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.214100] mmcblk0: retrying using single block read
[    5.214418] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.216983] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.216986] mmcblk0: retrying using single block read
[    5.217302] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.222478] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.222485] mmcblk0: retrying using single block read
[    5.222797] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.225414] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.225419] mmcblk0: retrying using single block read
[    5.225897] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.234105] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.234113] mmcblk0: retrying using single block read
[    5.234487] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.237208] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.237214] mmcblk0: retrying using single block read
[    5.237524] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.239988] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.239994] mmcblk0: retrying using single block read
[    5.240319] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.242988] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.242992] mmcblk0: retrying using single block read
[    5.243349] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.246327] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.246333] mmcblk0: retrying using single block read
[    5.246643] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.248952] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.248958] mmcblk0: retrying using single block read
[    5.249266] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.251644] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.251648] mmcblk0: retrying using single block read
[    5.251967] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.254312] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.254317] mmcblk0: retrying using single block read
[    5.254626] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.256963] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.256968] mmcblk0: retrying using single block read
[    5.257398] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.262993] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.262999] mmcblk0: retrying using single block read
[    5.263318] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.266224] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.266228] mmcblk0: retrying using single block read
[    5.266641] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.268546] mmcblk0: error -84 transferring data, sector 7, nr 1, cmd response 0x900, card status 0x0
[    5.268938] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.268941] mmcblk0: retrying using single block read
[    5.269222] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.271598] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.271603] mmcblk0: retrying using single block read
[    5.271955] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.274232] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.274238] mmcblk0: retrying using single block read
[    5.274602] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.275730] mmcblk0: error -84 transferring data, sector 4, nr 4, cmd response 0x900, card status 0x0
[    5.276963] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.276968] mmcblk0: retrying using single block read
[    5.277279] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.279730] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.279736] mmcblk0: retrying using single block read
[    5.280104] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.282493] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.282498] mmcblk0: retrying using single block read
[    5.282809] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.285749] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.285754] mmcblk0: retrying using single block read
[    5.286066] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.300093] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.300100] mmcblk0: retrying using single block read
[    5.300926] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.307849] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[    5.307856] mmcblk0: retrying using single block read
[    5.308374] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[    5.327443] init: Failed to spawn thermald main process: unable to execute: No such file or directory
[    6.088210] init: plymouth-upstart-bridge main process ended, respawning
[    6.102227] init: plymouth-upstart-bridge main process ended, respawning
[   44.190618] systemd-hostnamed[1979]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1052.525924] mmc0: card aaaa removed
[ 2108.757306] mmc0: new ultra high speed DDR50 SDHC card at address aaaa
[ 2108.759257] mmcblk0: mmc0:aaaa SL32G 29.7 GiB 
[ 2108.771742] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.771755] mmcblk0: retrying using single block read
[ 2108.772145] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.772156] blk_update_request: 89 callbacks suppressed
[ 2108.772161] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.774022] buffer_io_error: 82 callbacks suppressed
[ 2108.774028] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.774551] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.774560] mmcblk0: retrying using single block read
[ 2108.774859] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.774866] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.775921] mmcblk0: error -84 transferring data, sector 3, nr 5, cmd response 0x900, card status 0x0
[ 2108.775930] blk_update_request: I/O error, dev mmcblk0, sector 3
[ 2108.777268] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.777707] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.777711] mmcblk0: retrying using single block read
[ 2108.778011] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.778016] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.779861] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.780332] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.780335] mmcblk0: retrying using single block read
[ 2108.780615] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.780619] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.782467] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.782966] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.782974] mmcblk0: retrying using single block read
[ 2108.783523] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.783532] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.785752] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.786293] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.786301] mmcblk0: retrying using single block read
[ 2108.786708] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.786732] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.788921] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.789388] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.789392] mmcblk0: retrying using single block read
[ 2108.789751] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.789756] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.791704] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.792088] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.792092] mmcblk0: retrying using single block read
[ 2108.792388] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.792392] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.794206] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.794268] ldm_validate_partition_table(): Disk read failed.
[ 2108.794622] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.794625] mmcblk0: retrying using single block read
[ 2108.795072] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.795078] blk_update_request: I/O error, dev mmcblk0, sector 0
[ 2108.796893] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.797282] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.797286] mmcblk0: retrying using single block read
[ 2108.797581] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.799649] Buffer I/O error on dev mmcblk0, logical block 0, async page read
[ 2108.800093] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.800101] mmcblk0: retrying using single block read
[ 2108.800447] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.802747] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.802752] mmcblk0: retrying using single block read
[ 2108.803046] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.804941] Dev mmcblk0: unable to read RDB block 0
[ 2108.805299] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.805304] mmcblk0: retrying using single block read
[ 2108.805589] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.808010] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.808015] mmcblk0: retrying using single block read
[ 2108.808310] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.811018] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.811022] mmcblk0: retrying using single block read
[ 2108.811311] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.813596] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.813600] mmcblk0: retrying using single block read
[ 2108.813894] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.815898]  mmcblk0: unable to read partition table
[ 2108.826483] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.826494] mmcblk0: retrying using single block read
[ 2108.826827] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.829397] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.829405] mmcblk0: retrying using single block read
[ 2108.829726] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.833575] mmcblk0: error -84 transferring data, sector 62333688, nr 8, cmd response 0x900, card status 0xb00
[ 2108.833583] mmcblk0: retrying using single block read
[ 2108.835104] mmcblk0: error -84 transferring data, sector 62333691, nr 5, cmd response 0x900, card status 0x0
[ 2108.835855] mmcblk0: error -84 transferring data, sector 62333693, nr 3, cmd response 0x900, card status 0x0
[ 2108.841769] mmcblk0: error -84 transferring data, sector 62332960, nr 8, cmd response 0x900, card status 0xb00
[ 2108.841774] mmcblk0: retrying using single block read
[ 2108.842137] mmcblk0: error -84 transferring data, sector 62332960, nr 8, cmd response 0x900, card status 0x0
[ 2108.846488] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.846492] mmcblk0: retrying using single block read
[ 2108.846777] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.849072] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.849081] mmcblk0: retrying using single block read
[ 2108.849374] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.851779] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.851787] mmcblk0: retrying using single block read
[ 2108.852091] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.854329] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.854333] mmcblk0: retrying using single block read
[ 2108.854626] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.857086] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.857094] mmcblk0: retrying using single block read
[ 2108.857388] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.859701] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.859705] mmcblk0: retrying using single block read
[ 2108.859998] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.861645] mmcblk0: error -84 transferring data, sector 6, nr 2, cmd response 0x900, card status 0x0
[ 2108.862309] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.862314] mmcblk0: retrying using single block read
[ 2108.862606] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.865331] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.865336] mmcblk0: retrying using single block read
[ 2108.865629] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.867913] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.867918] mmcblk0: retrying using single block read
[ 2108.868237] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.870494] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.870499] mmcblk0: retrying using single block read
[ 2108.870808] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.873072] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.873076] mmcblk0: retrying using single block read
[ 2108.873382] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.875801] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.875806] mmcblk0: retrying using single block read
[ 2108.876123] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.878423] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.878427] mmcblk0: retrying using single block read
[ 2108.878735] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.881009] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.881013] mmcblk0: retrying using single block read
[ 2108.881317] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.883645] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.883650] mmcblk0: retrying using single block read
[ 2108.883942] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.884493] mmcblk0: error -84 transferring data, sector 2, nr 6, cmd response 0x900, card status 0x0
[ 2108.886219] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.886223] mmcblk0: retrying using single block read
[ 2108.886514] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.888794] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.888798] mmcblk0: retrying using single block read
[ 2108.889090] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.891444] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.891449] mmcblk0: retrying using single block read
[ 2108.891770] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.894014] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.894019] mmcblk0: retrying using single block read
[ 2108.894323] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.896628] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.896632] mmcblk0: retrying using single block read
[ 2108.896937] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.899207] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.899212] mmcblk0: retrying using single block read
[ 2108.899536] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.902219] mmcblk0: error -84 transferring data, sector 56, nr 8, cmd response 0x900, card status 0xb00
[ 2108.902223] mmcblk0: retrying using single block read
[ 2108.905307] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.905312] mmcblk0: retrying using single block read
[ 2108.905631] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.907960] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.907965] mmcblk0: retrying using single block read
[ 2108.908283] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.910558] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.910563] mmcblk0: retrying using single block read
[ 2108.910878] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.913147] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.913152] mmcblk0: retrying using single block read
[ 2108.913448] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.915741] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.915746] mmcblk0: retrying using single block read
[ 2108.916036] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.918289] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.918294] mmcblk0: retrying using single block read
[ 2108.918582] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.920992] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.921001] mmcblk0: retrying using single block read
[ 2108.921290] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.923550] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.923555] mmcblk0: retrying using single block read
[ 2108.923842] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.926120] mmcblk0: error -84 transferring data, sector 16, nr 8, cmd response 0x900, card status 0xb00
[ 2108.926124] mmcblk0: retrying using single block read
[ 2108.931983] mmcblk0: error -84 transferring data, sector 288, nr 8, cmd response 0x900, card status 0xb00
[ 2108.931992] mmcblk0: retrying using single block read
[ 2108.939636] mmcblk0: error -84 transferring data, sector 400, nr 8, cmd response 0x900, card status 0xb00
[ 2108.939640] mmcblk0: retrying using single block read
[ 2108.944128] mmcblk0: error -84 transferring data, sector 448, nr 8, cmd response 0x900, card status 0xb00
[ 2108.944131] mmcblk0: retrying using single block read
[ 2108.948753] mmcblk0: error -84 transferring data, sector 496, nr 8, cmd response 0x900, card status 0xb00
[ 2108.948756] mmcblk0: retrying using single block read
[ 2108.960038] mmcblk0: error -84 transferring data, sector 928, nr 8, cmd response 0x900, card status 0xb00
[ 2108.960042] mmcblk0: retrying using single block read
[ 2108.963371] mmcblk0: error -84 transferring data, sector 952, nr 8, cmd response 0x900, card status 0xb00
[ 2108.963376] mmcblk0: retrying using single block read
[ 2108.966731] mmcblk0: error -84 transferring data, sector 976, nr 8, cmd response 0x900, card status 0xb00
[ 2108.966734] mmcblk0: retrying using single block read
[ 2108.971499] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.971503] mmcblk0: retrying using single block read
[ 2108.971790] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.973988] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.973993] mmcblk0: retrying using single block read
[ 2108.974296] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.976617] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.976622] mmcblk0: retrying using single block read
[ 2108.976912] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.979178] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.979183] mmcblk0: retrying using single block read
[ 2108.979503] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.981706] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.981710] mmcblk0: retrying using single block read
[ 2108.981999] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.984251] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.984255] mmcblk0: retrying using single block read
[ 2108.984542] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.986733] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.986737] mmcblk0: retrying using single block read
[ 2108.987081] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.989318] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.989322] mmcblk0: retrying using single block read
[ 2108.989634] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.991927] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.991931] mmcblk0: retrying using single block read
[ 2108.992245] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.994471] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.994475] mmcblk0: retrying using single block read
[ 2108.994788] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.997024] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.997028] mmcblk0: retrying using single block read
[ 2108.997337] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2108.999711] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2108.999718] mmcblk0: retrying using single block read
[ 2109.000062] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.002356] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.002360] mmcblk0: retrying using single block read
[ 2109.002719] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.004990] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.004995] mmcblk0: retrying using single block read
[ 2109.005284] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.007557] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.007563] mmcblk0: retrying using single block read
[ 2109.007890] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.010143] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.010148] mmcblk0: retrying using single block read
[ 2109.010457] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.012821] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.012827] mmcblk0: retrying using single block read
[ 2109.013123] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.015421] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.015426] mmcblk0: retrying using single block read
[ 2109.015722] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.017944] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.017950] mmcblk0: retrying using single block read
[ 2109.018274] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.020541] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.020546] mmcblk0: retrying using single block read
[ 2109.020841] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.023090] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.023095] mmcblk0: retrying using single block read
[ 2109.023409] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.024789] mmcblk0: error -84 transferring data, sector 5, nr 3, cmd response 0x900, card status 0x0
[ 2109.025752] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.025757] mmcblk0: retrying using single block read
[ 2109.026110] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.028524] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.028531] mmcblk0: retrying using single block read
[ 2109.028821] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.031049] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.031054] mmcblk0: retrying using single block read
[ 2109.031457] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.033762] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.033766] mmcblk0: retrying using single block read
[ 2109.034063] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.036264] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.036269] mmcblk0: retrying using single block read
[ 2109.036589] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.038877] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.038889] mmcblk0: retrying using single block read
[ 2109.039185] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.041833] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.041840] mmcblk0: retrying using single block read
[ 2109.042123] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.043753] mmcblk0: error -84 transferring data, sector 6, nr 2, cmd response 0x900, card status 0x0
[ 2109.044405] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.044409] mmcblk0: retrying using single block read
[ 2109.044694] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.047036] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.047041] mmcblk0: retrying using single block read
[ 2109.047342] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.049617] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.049623] mmcblk0: retrying using single block read
[ 2109.049934] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.052291] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.052296] mmcblk0: retrying using single block read
[ 2109.052606] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.054879] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.054888] mmcblk0: retrying using single block read
[ 2109.055240] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.057557] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.057561] mmcblk0: retrying using single block read
[ 2109.057876] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.060210] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.060215] mmcblk0: retrying using single block read
[ 2109.060548] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.062812] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.062816] mmcblk0: retrying using single block read
[ 2109.063145] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.065434] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.065438] mmcblk0: retrying using single block read
[ 2109.065727] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.067963] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.067967] mmcblk0: retrying using single block read
[ 2109.068287] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.070569] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.070573] mmcblk0: retrying using single block read
[ 2109.070868] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.073094] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.073098] mmcblk0: retrying using single block read
[ 2109.073390] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.075638] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.075642] mmcblk0: retrying using single block read
[ 2109.075964] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.078202] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.078206] mmcblk0: retrying using single block read
[ 2109.078498] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.080775] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.080779] mmcblk0: retrying using single block read
[ 2109.081067] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0
[ 2109.083357] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 2109.083361] mmcblk0: retrying using single block read
[ 2109.083681] mmcblk0: error -84 transferring data, sector 0, nr 8, cmd response 0x900, card status 0x0



```


also that other setpci didnt seem to do anything. but to verify I just have to type 
```

sudo [COLOR=#333333][FONT=monospace]setpci -s 00:1c.2 0x50.B=0x41
[/FONT][/COLOR]
```

Correct?

---

### Post by weatherman2 on 2015-08-19
Yes, that would be correct.

---

### Post by thatmayh3mguy on 2015-08-20
yea I did that and nothing happened

---

### Post by weatherman2 on 2015-08-20
I'm not sure how much more help I can offer because I'm using a different version of Ubuntu.  Did you read that bug report over pretty carefully?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178131)

Also, have you tried any other smaller SD cards?  I note now that I have assumed my 64GB SDXC card can't be read because it is exFat but perhaps it is the size that's the real problem.  The FAT32 card I have that works fine is only 8GB.

---

### Post by thatmayh3mguy on 2015-08-20
yea I tried all of the work arounds and nothing seems to work. 
i just tried it with a 4gb card fat32 sd card and got nothing

---

