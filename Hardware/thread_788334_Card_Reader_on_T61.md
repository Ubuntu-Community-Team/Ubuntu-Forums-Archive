---
title: "Card Reader on T61"
date: 2008-05-09
forum: Hardware
---

### Post by Reactor5 on 2008-05-09
The card reader on my Lenovo/IBM T61 laptop is either not being recognized or I don't know where to find it.  Anyone have common solutions?

---

### Post by teaker1s on 2008-05-09
```
lspci 
```
```
lsusb
```
post output and lets see what the vendor and product id is

---

### Post by Reactor5 on 2008-05-10
Here's the whole output of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```

I think the last 6 lines are the ones we're looking for (15:00.0-15:00.5)  I don't know what to do with this information though.  LSUSB is as follows:

```
Bus 007 Device 008: ID 17ef:1004 ChipsBnk 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
```

I looked around for ricoh and there wasn't anything really helpful.

---

### Post by teaker1s on 2008-05-14
Only thing that may or not be of any interest
[http://lkml.org/lkml/2007/10/1/375]("http://lkml.org/lkml/2007/10/1/375")

---

### Post by Reactor5 on 2008-07-02
For readers reading this and wondering whether I ever got it working: I was using a faulty card.  It worked with others.

---

### Post by DCAM77 on 2009-03-18
I am in the same situation as Reactor5 except I'm pretty sure that my memory stick is functional (works when I boot into vista on the same computer).

I see the advice from Teaker1s but I am new to Linux and am worried about trying this.

Running Ubunto 8.10 installed by wubi on Lenovo T61 - embarrassed to say I'm not certain whether it's 32- or 64-bit

Would be grateful for any help anyone can provide.

lspci gives:

doug@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

---

### Post by Admiral Nesquick on 2009-03-18
Could you post the output of **dmesg** ? The Ricoh card reader maybe integrated in your motherboard. And then lspci and lsusb won't cut the deal.

I see a Ricoh somewhere in the lspci output though, but i'm not sure if that is a card reader.

---

### Post by DCAM77 on 2009-03-18
Thanks for the response Admiral Nesquick.

First half of output:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] Command line: root=UUID=18DE6439DE6410F4 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfecc000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x13c000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xbfeb0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfeb0000 page 4k
[    0.000000] kernel direct mapping tables up to bfeb0000 @ 8000-d000
[    0.000000] last_map_addr: bfeb0000 end: bfeb0000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 013c000000 page 2M
[    0.000000] kernel direct mapping tables up to 13c000000 @ b000-11000
[    0.000000] last_map_addr: 13c000000 end: 13c000000
[    0.000000] RAMDISK: 7f76d000 - 7ffef171
[    0.000000] ACPI: RSDP 000F68D0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT BFEBB77F, 0094 (r1 LENOVO TP-7L        2210  LTP        0)
[    0.000000] ACPI: FACP BFEBB900, 00F4 (r3 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080609]
[    0.000000] ACPI: DSDT BFEBBD1D, FED1 (r1 LENOVO TP-7L        2210 MSFT  3000000)
[    0.000000] ACPI: FACS BFEE4000, 0040
[    0.000000] ACPI: SSDT BFEBBAB4, 0269 (r1 LENOVO TP-7L        2210 MSFT  3000000)
[    0.000000] ACPI: ECDT BFECBBEE, 0052 (r1 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: TCPA BFECBC40, 0032 (r2 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: APIC BFECBC72, 0068 (r1 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: MCFG BFECBCDA, 003C (r1 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: HPET BFECBD16, 0038 (r1 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: SLIC BFECBDF0, 0176 (r1 LENOVO TP-7L        2210  LTP        0)
[    0.000000] ACPI: BOOT BFECBF66, 0028 (r1 LENOVO TP-7L        2210  LTP        1)
[    0.000000] ACPI: ASF! BFECBF8E, 0072 (r16 LENOVO TP-7L        2210 PTL         1)
[    0.000000] ACPI: SSDT BFEE271B, 025F (r1 LENOVO TP-7L        2210 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE297A, 00A6 (r1 LENOVO TP-7L        2210 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE2A20, 04F7 (r1 LENOVO TP-7L        2210 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE2F17, 01D8 (r1 LENOVO TP-7L        2210 INTL 20050513)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad T61
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000013c000000
[    0.000000] Bootmem setup node 0 0000000000000000-000000013c000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000c000 -  00000000000337ff] pages 28
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 013c000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b9f5c]    TEXT DATA BSS ==> [0000200000 - 00008b9f5c]
[    0.000000]   #3 [007f76d000 - 007ffef171]          RAMDISK ==> [007f76d000 - 007ffef171]
[    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000]   #6 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
[    0.000000] found SMP MP-table at [ffff8800000f6900] 000f6900
[    0.000000]  [ffffe20000000000-ffffe20004ffffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0013c000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bfeb0
[    0.000000]     0: 0x00100000 -> 0x0013c000
[    0.000000] On node 0 totalpages: 1031757
[    0.000000]   DMA zone: 2105 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 765680 pages, LIFO batch:31
[    0.000000]   Normal zone: 241920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfeb0000 - 00000000bfecc000
[    0.000000] PM: Registered nosave memory: 00000000bfecc000 - 00000000bff00000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:30000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1009705
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=18DE6439DE6410F4 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2493.721 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3979556k/5177344k available (3116k kernel code, 147472k reserved, 1575k data, 540k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4987.44 BogoMIPS (lpj=9974884)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] CPU0: Thermal monitoring enabled (TM2)
[    0.004000] using mwait in idle threads.
[    0.004014] ACPI: Core revision 20080609
[    0.011054] ACPI: Checking initramfs for custom DSDT
[    0.316494] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.358101] CPU0: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz stepping 06
[    0.358104] Using local APIC timer interrupts.
[    0.360023] APIC timer calibration result 12468628
[    0.360024] Detected 12.468 MHz APIC timer.
[    0.360134] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4987.45 BogoMIPS (lpj=9974911)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.448885] CPU1: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz stepping 06
[    0.448906] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.452028] Measured 457175 cycles TSC warp between CPUs, turning off TSC clock.
[    0.452028] Marking TSC unstable due to check_tsc_sync_source failed
[    0.452061] Brought up 2 CPUs
[    0.452063] Total of 2 processors activated (9974.89 BogoMIPS).
[    0.452112] CPU0 attaching sched-domain:
[    0.452114]  domain 0: span 0-1 level MC
[    0.452116]   groups: 0 1
[    0.452119]   domain 1: span 0-1 level NODE
[    0.452121]    groups: 0-1
[    0.452124] CPU1 attaching sched-domain:
[    0.452125]  domain 0: span 0-1 level MC
[    0.452127]   groups: 1 0
[    0.452129]   domain 1: span 0-1 level NODE
[    0.452131]    groups: 0-1
[    0.452206] net_namespace: 1552 bytes
[    0.452206] Booting paravirtualized kernel on bare hardware
[    0.452256] Time: 10:03:55  Date: 03/18/09
[    0.452281] NET: Registered protocol family 16
[    0.452296] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.452296] ACPI: bus type pci registered
[    0.452296] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.452296] PCI: MCFG area at f0000000 reserved in E820
[    0.454011] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.454013] PCI: Using configuration type 1 for base access
[    0.457233] ACPI: EC: EC description table is found, configuring boot EC
[    0.464558] ACPI: BIOS _OSI(Linux) query honored via DMI
[    0.464051] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.476029] ACPI: Interpreter enabled
[    0.476029] ACPI: (supports S0 S3 S4 S5)
[    0.476104] ACPI: Using IOAPIC for interrupt routing
[    0.489080] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[    0.489080] ACPI: EC: driver started in interrupt mode
[    0.492045] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.492097] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.492099] pci 0000:00:01.0: PME# disabled
[    0.492181] PCI: 0000:00:19.0 reg 10 32bit mmio: [fe200000, fe21ffff]
[    0.492197] PCI: 0000:00:19.0 reg 14 32bit mmio: [fe225000, fe225fff]
[    0.492213] PCI: 0000:00:19.0 reg 18 io port: [1840, 185f]
[    0.492297] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.492305] pci 0000:00:19.0: PME# disabled
[    0.492404] PCI: 0000:00:1a.0 reg 20 io port: [1860, 187f]
[    0.492539] PCI: 0000:00:1a.1 reg 20 io port: [1880, 189f]
[    0.492663] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fe226c00, fe226fff]
[    0.492774] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.492780] pci 0000:00:1a.7: PME# disabled
[    0.492805] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fe220000, fe223fff]
[    0.492805] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.492805] pci 0000:00:1b.0: PME# disabled
[    0.492805] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.492805] pci 0000:00:1c.0: PME# disabled
[    0.492805] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.492805] pci 0000:00:1c.1: PME# disabled
[    0.492805] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.492805] pci 0000:00:1c.2: PME# disabled
[    0.492805] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.492805] pci 0000:00:1c.3: PME# disabled
[    0.492805] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.492805] pci 0000:00:1c.4: PME# disabled
[    0.492805] PCI: 0000:00:1d.0 reg 20 io port: [18a0, 18bf]
[    0.492805] PCI: 0000:00:1d.1 reg 20 io port: [18c0, 18df]
[    0.492929] PCI: 0000:00:1d.2 reg 20 io port: [18e0, 18ff]
[    0.493067] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fe227000, fe2273ff]
[    0.493189] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.493196] pci 0000:00:1d.7: PME# disabled
[    0.493442] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.493447] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.493500] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.493515] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.493529] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.493542] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.493556] PCI: 0000:00:1f.1 reg 20 io port: [1830, 183f]
[    0.493651] PCI: 0000:00:1f.2 reg 10 io port: [1c48, 1c4f]
[    0.493659] PCI: 0000:00:1f.2 reg 14 io port: [1c1c, 1c1f]
[    0.493668] PCI: 0000:00:1f.2 reg 18 io port: [1c40, 1c47]
[    0.493676] PCI: 0000:00:1f.2 reg 1c io port: [1c18, 1c1b]
[    0.493685] PCI: 0000:00:1f.2 reg 20 io port: [1c20, 1c3f]
[    0.493693] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fe226000, fe2267ff]
[    0.493725] pci 0000:00:1f.2: PME# supported from D3hot
[    0.493731] pci 0000:00:1f.2: PME# disabled
[    0.493763] PCI: 0000:00:1f.3 reg 10 32bit mmio: [fe227400, fe2274ff]
[    0.493787] PCI: 0000:00:1f.3 reg 20 io port: [1c60, 1c7f]
[    0.493872] PCI: 0000:01:00.0 reg 10 32bit mmio: [d6000000, d6ffffff]
[    0.493883] PCI: 0000:01:00.0 reg 14 64bit mmio: [e0000000, efffffff]
[    0.493894] PCI: 0000:01:00.0 reg 1c 64bit mmio: [d4000000, d5ffffff]
[    0.493900] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    0.493906] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.493969] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.493971] PCI: bridge 0000:00:01.0 32bit mmio: [d4000000, d6ffffff]
[    0.493975] PCI: bridge 0000:00:01.0 64bit mmio pref: [e0000000, efffffff]
[    0.494032] PCI: bridge 0000:00:1c.0 io port: [3000, 3fff]
[    0.494038] PCI: bridge 0000:00:1c.0 32bit mmio: [fc000000, fdffffff]
[    0.494051] PCI: bridge 0000:00:1c.0 64bit mmio pref: [f8000000, f80fffff]
[    0.494178] PCI: 0000:03:00.0 reg 10 64bit mmio: [df2fe000, df2fffff]
[    0.494294] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.494307] pci 0000:03:00.0: PME# disabled
[    0.494355] PCI: bridge 0000:00:1c.1 io port: [4000, 4fff]
[    0.494364] PCI: bridge 0000:00:1c.1 32bit mmio: [dc100000, df2fffff]
[    0.494377] PCI: bridge 0000:00:1c.1 64bit mmio pref: [dfd00000, dfdfffff]
[    0.494445] PCI: bridge 0000:00:1c.2 io port: [5000, 5fff]
[    0.494451] PCI: bridge 0000:00:1c.2 32bit mmio: [d8000000, d9ffffff]
[    0.494464] PCI: bridge 0000:00:1c.2 64bit mmio pref: [dfa00000, dfafffff]
[    0.494531] PCI: bridge 0000:00:1c.3 io port: [6000, 6fff]
[    0.494538] PCI: bridge 0000:00:1c.3 32bit mmio: [d0000000, d1ffffff]
[    0.494546] PCI: bridge 0000:00:1c.3 64bit mmio pref: [df700000, df7fffff]
[    0.494614] PCI: bridge 0000:00:1c.4 io port: [7000, 7fff]
[    0.494620] PCI: bridge 0000:00:1c.4 32bit mmio: [cc000000, cdffffff]
[    0.494629] PCI: bridge 0000:00:1c.4 64bit mmio pref: [df400000, df4fffff]
[    0.494697] PCI: 0000:15:00.0 reg 10 32bit mmio: [f8100000, f8100fff]
[    0.494727] pci 0000:15:00.0: supports D1
[    0.494728] pci 0000:15:00.0: supports D2
[    0.494730] pci 0000:15:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.494738] pci 0000:15:00.0: PME# disabled
[    0.494799] PCI: 0000:15:00.1 reg 10 32bit mmio: [f8101000, f81017ff]
[    0.494894] pci 0000:15:00.1: supports D1
[    0.494895] pci 0000:15:00.1: supports D2
[    0.494896] pci 0000:15:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.494903] pci 0000:15:00.1: PME# disabled
[    0.494960] PCI: 0000:15:00.2 reg 10 32bit mmio: [f8101800, f81018ff]
[    0.495045] pci 0000:15:00.2: supports D1
[    0.495046] pci 0000:15:00.2: supports D2
[    0.495047] pci 0000:15:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.495055] pci 0000:15:00.2: PME# disabled
[    0.495119] PCI: 0000:15:00.3 reg 10 32bit mmio: [f8101c00, f8101cff]
[    0.495212] pci 0000:15:00.3: supports D1
[    0.495213] pci 0000:15:00.3: supports D2
[    0.495214] pci 0000:15:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.495221] pci 0000:15:00.3: PME# disabled
[    0.495284] PCI: 0000:15:00.4 reg 10 32bit mmio: [f8102000, f81020ff]
[    0.495371] pci 0000:15:00.4: supports D1
[    0.495372] pci 0000:15:00.4: supports D2
[    0.495373] pci 0000:15:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.495380] pci 0000:15:00.4: PME# disabled
[    0.495438] PCI: 0000:15:00.5 reg 10 32bit mmio: [f8102400, f81024ff]
[    0.495529] pci 0000:15:00.5: supports D1
[    0.495530] pci 0000:15:00.5: supports D2
[    0.495531] pci 0000:15:00.5: PME# supported from D0 D1 D2 D3hot D3cold
[    0.495538] pci 0000:15:00.5: PME# disabled
[    0.495635] pci 0000:00:1e.0: transparent bridge
[    0.495641] PCI: bridge 0000:00:1e.0 io port: [8000, bfff]
[    0.495649] PCI: bridge 0000:00:1e.0 32bit mmio: [f8100000, fbffffff]
[    0.495663] PCI: bridge 0000:00:1e.0 64bit mmio pref: [f4000000, f7ffffff]
[    0.495745] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.495997] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.496142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.496283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.496422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.496562] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.496704] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.496852] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.500197] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[    0.500428] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.500658] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.500887] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.501116] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.501345] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.501574] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.501807] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.504093] ACPI: Power Resource [PUBS] (on)
[    0.504208] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.504216] pnp: PnP ACPI init
[    0.504216] ACPI: bus type pnp registered
[    0.508941] pnp: PnP ACPI: found 11 devices
[    0.508942] ACPI: ACPI bus type pnp unregistered
[    0.509213] PCI: Using ACPI for IRQ routing
[    0.536045] NET: Registered protocol family 8
[    0.536047] NET: Registered protocol family 20
[    0.536065] NetLabel: Initializing
[    0.536065] NetLabel:  domain hash size = 128
[    0.536065] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.536065] NetLabel:  unlabeled traffic allowed by default
[    0.536065] PCI-GART: No AMD northbridge found.
[    0.536072] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.536075] hpet0: 3 64-bit timers, 14318180 Hz
[    0.538041] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.538043]    actual entries 65586
[    0.538109] AppArmor: AppArmor Filesystem Enabled
[    0.538136] ACPI: RTC can wake from S4
[    0.540047] Switched to high resolution mode on CPU 0
[    0.540947] Switched to high resolution mode on CPU 1
[    0.553020] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.553022] system 00:00: iomem range 0xc0000-0xc3fff has been reserved
[    0.553024] system 00:00: iomem range 0xc4000-0xc7fff has been reserved
[    0.553028] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    0.553030] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[    0.553032] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.553034] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.553036] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.553037] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.553039] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.553041] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.553043] system 00:00: iomem range 0x100000-0xbfffffff could not be reserved
[    0.553045] system 00:00: iomem range 0xfec00000-0xfed3ffff could not be reserved
[    0.553047] system 00:00: iomem range 0xfed4c000-0xffffffff could not be reserved
[    0.553052] system 00:02: ioport range 0x164e-0x164f has been reserved
[    0.553054] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.553056] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.553058] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.553060] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.553062] system 00:02: ioport range 0x1600-0x165f could not be reserved
[    0.553064] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.553066] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.553068] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.553070] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.553072] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.553074] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[    0.558189] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf0000000-0xefffffff]
[    0.558191] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.558194] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.558197] pci 0000:00:01.0:   MEM window: 0xd4000000-0xd6ffffff
[    0.558199] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.558203] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.558208] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.558218] pci 0000:00:1c.0:   MEM window: 0xfc000000-0xfdffffff
[    0.558224] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8000000-0x000000f80fffff
[    0.558232] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.558237] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.558247] pci 0000:00:1c.1:   MEM window: 0xdc100000-0xdf2fffff
[    0.558253] pci 0000:00:1c.1:   PREFETCH window: 0x000000dfd00000-0x000000dfdfffff
[    0.558262] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.558267] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.558274] pci 0000:00:1c.2:   MEM window: 0xd8000000-0xd9ffffff
[    0.558280] pci 0000:00:1c.2:   PREFETCH window: 0x000000dfa00000-0x000000dfafffff
[    0.558289] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.558294] pci 0000:00:1c.3:   IO window: 0x6000-0x6fff
[    0.558304] pci 0000:00:1c.3:   MEM window: 0xd0000000-0xd1ffffff
[    0.558310] pci 0000:00:1c.3:   PREFETCH window: 0x000000df700000-0x000000df7fffff
[    0.558318] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.558323] pci 0000:00:1c.4:   IO window: 0x7000-0x7fff
[    0.558330] pci 0000:00:1c.4:   MEM window: 0xcc000000-0xcdffffff
[    0.558336] pci 0000:00:1c.4:   PREFETCH window: 0x000000df400000-0x000000df4fffff
[    0.558347] pci 0000:15:00.0: CardBus bridge, secondary bus 0000:16
[    0.558349] pci 0000:15:00.0:   IO window: 0x008000-0x0080ff
[    0.558356] pci 0000:15:00.0:   IO window: 0x008400-0x0084ff
[    0.558363] pci 0000:15:00.0:   PREFETCH window: 0xf4000000-0xf7ffffff
[    0.558370] pci 0000:15:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.558377] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:15
[    0.558382] pci 0000:00:1e.0:   IO window: 0x8000-0xbfff
[    0.558389] pci 0000:00:1e.0:   MEM window: 0xf8100000-0xfbffffff
[    0.558395] pci 0000:00:1e.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    0.558410] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.558413] pci 0000:00:01.0: setting latency timer to 64
[    0.558427] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.558432] pci 0000:00:1c.0: setting latency timer to 64
[    0.558449] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.558454] pci 0000:00:1c.1: setting latency timer to 64
[    0.558470] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.558475] pci 0000:00:1c.2: setting latency timer to 64
[    0.558487] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.558492] pci 0000:00:1c.3: setting latency timer to 64
[    0.558508] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.558515] pci 0000:00:1c.4: setting latency timer to 64
[    0.558523] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    0.558535] pci 0000:00:1e.0: setting latency timer to 64
[    0.558549] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

---

### Post by DCAM77 on 2009-03-18
Extract of second half containing the only mention of "Ricoh" (the forum won't let me post the whole thing - gives an error saying I've include 21 images when my limit is 8 per message???):

[   11.919590] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/device:07/input/input7
[   11.937026] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   12.414872] nvidia: module license 'NVIDIA' taints kernel.
[   12.668728] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   12.668743] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.668752] nvidia 0000:01:00.0: setting latency timer to 64
[   12.670243] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.82  Tue Nov  4 16:50:05 PST 2008
[   12.753928] iTCO_vendor_support: vendor-support=0
[   12.768482] Bluetooth: Core ver 2.13
[   12.768904] NET: Registered protocol family 31
[   12.768906] Bluetooth: HCI device and connection manager initialized
[   12.768908] Bluetooth: HCI socket layer initialized
[   12.781282] Non-volatile memory driver v1.2
[   12.781398] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.781400] ricoh-mmc: Copyright(c) Philip Langdale
[   12.781823] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   12.781852] ricoh-mmc: Controller is now disabled.
[   12.797678] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   12.829581] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   12.882852] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   12.884479] usbcore: registered new interface driver btusb
[   12.891464] sdhci: Secure Digital Host Controller Interface driver
[   12.891466] sdhci: Copyright(c) Pierre Ossman
[   12.915902] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.958028] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   12.958034] Socket status: 30000006
[   12.958036] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   12.958039] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   12.958040] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   12.958261] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[   12.958285] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   12.959300] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   12.959311] sdhci-pci 0000:15:00.2: setting latency timer to 64

---

### Post by Admiral Nesquick on 2009-03-18
> [ 12.781398] ricoh-mmc: Ricoh MMC Controller disabling driver
[ 12.781400] ricoh-mmc: Copyright(c) Philip Langdale
[ 12.781823] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[ 12.781852] ricoh-mmc: Controller is now disabled.

The card reader is detected but is disabled. 

Type this :

> /sbin/setpci -s ‘03:01.0&#8242; 0xCA=0×57
/sbin/setpci -s ‘03:01.0&#8242; 0xCB=0×02
/sbin/setpci -s ‘03:01.0&#8242; 0xCA=0×00

You might want to put that in a start up script for now if it works.

---

### Post by DCAM77 on 2009-03-18
Thanks for the reply.  I tried this (making the following changes: used sudo, used /usr/bin/setpci instead of /sbin/setpci and used '15:00.3' instead of '03:01.0').

Unfortunately I'm still not able to mount a memory stick and dmesg output is unchanged.  I've tried rebooting but to no avail - Haven't trying to put the commands in the start up script (I'll have to figre out how to do that).

Thanks for the help Admiral Nesquick - let me know if you have any other ideas...

---

### Post by DCAM77 on 2009-03-20
Further info for anyone interested:

Ricoh reader works perfectly with SD card but not at all with a memory stick.

If I can fix this then I'll have no further need for Vista!

---

### Post by weissed on 2009-12-20
Hi!

Did you manage to make it work with Memory stick cards?

Thanks

---

