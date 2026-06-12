---
title: "New wifi card won't work."
date: 2010-01-10
forum: Hardware
---

### Post by Marvin666 on 2010-01-10
I recently bough a new card, because my laptop's internal chipset is atheros. It is a liksys wec600n. I have a little wifi detector, and it says my router is broadcasting. The router firm also says it is. The ssid of the network is Local Network, it's on g only mode, and channel 6. I can't get my laptop to reconize the card, or connect.

---

### Post by Marvin666 on 2010-01-10
I tried to install the win xp driver with ndiswrapper, but it didn't work.

---

### Post by Marvin666 on 2010-01-11
*bump*

---

### Post by PRC09 on 2010-01-11
Sorry bad news.....

[http://forums.linksysbycisco.com/linksys/board/message?board.id=Wireless_Adapters&message.id=21483](http://forums.linksysbycisco.com/linksys/board/message?board.id=Wireless_Adapters&message.id=21483)

---

### Post by Marvin666 on 2010-01-11
Do you know of a distro I can get it to work on then? I've heard of people using it with linux before...

---

### Post by gradinaruvasile on 2010-01-11
What version of Ubuntu u have? If 9.04, try upgradung to 9.10, there are more and up to date drivers there.

What does

```
sudo iwlist scan
```

and

```
lspci
```

returns when run in a terminal?

Is the card showing up in network managers list?

And whats wrong with your Atheros wifi? It doesnt work or what?

---

### Post by gradinaruvasile on 2010-01-11
Also, i read that it has broadcom 43xx chipset, at least according to 1 source.
 That has support under Linux. Install the  b43-fwcutter package. See if it works that way.

sudo apt-get install b43-fwcutter

---

### Post by Marvin666 on 2010-01-11
```
marvin@Local-Machine:~$ sudo iwlist scan
[sudo] password for marvin: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

marvin@Local-Machine:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M G (rev b1)
06:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
marvin@Local-Machine:~$ 

```What drivr should I be selecting after I install that? Nothing new came up on my list.
I'll try a dual boot with karmic. Version is on the left and it's on the first machine in my signature.

---

### Post by gradinaruvasile on 2010-01-11
06:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Is the only wireless listed device. Is that your laptop's internal wireless? Is the Linksys inserted?

---

### Post by Marvin666 on 2010-01-11
That's the internal one. I never could get it to work, even with madwifi. I have the card plugged in, both the leds are lit.

---

### Post by gradinaruvasile on 2010-01-11
Open System>Administration>Software Sources and then check off all the boxes. Close and open terminal and type:

sudo apt-get update
sudo apt-get install linux-backports-modules-jaunty

restart. This may activate the internal wireless.

As for the other one... It is not detected at all. You should download a 9.10 live cd and start the computer with that. Maybe it will detect it.

---

### Post by Marvin666 on 2010-01-11
Did that ages ago, and nothing. I have a collection of live cd's, so I'll just pop in xubuntu karmic, and install it on an empty 30gb partition I have. Xubuntu won't mind if /home is before / on the drive, will it?

---

### Post by gradinaruvasile on 2010-01-11
I didnt unrderstand the question. You mean the partitions order? 
You can install on any partition whatever you like. Just make sure that the partition in question is empty.

---

### Post by Marvin666 on 2010-01-11
Ok, karmic is a big no-go.
Shortly after it automatically installed the broadcom restricted drivers, it locked up. This forced me to do a hard shutdown. Karmic appears to be more unstable because this seem to have corrupted it's partition, which causes it to give me a kernel panic (my frist one...) every time I try to start it.

---

### Post by gradinaruvasile on 2010-01-11
Wow... Thats bad. What file system do you have on thet partition? I recommend ext3 instead of the default ext4.

Also, i always try from live cd first. Or, better, live-USB. You can install anything on it as long as you dont reboot it or run out of memory.

---

### Post by Marvin666 on 2010-01-11
I used ext4 for /, and ext3 for /home. Jaunty has had a hard shutdown with the same setup, and never corrupted anything. My bios doesn't support booting from usb. I'll give it another try with ext3 for / tomorrow after school. It's too late to try another install, and I need some sleep.

---

### Post by Marvin666 on 2010-01-11
I can't sleep, so I messed with it more. It turns out karmic crashes every time I try to install version 185 of the restricted nvidia drivers. It crashed the live cd too. From live cd it detects the card as "Broadcom BCM4328 802.11a/b/g/n", but it says wireless networking is disabled, and there's no option to enable it.

---

### Post by gradinaruvasile on 2010-01-11
Ignore the video driver issue. 

what does

dmesg

and

rfkill list

return after booting from the live CD.

---

### Post by Marvin666 on 2010-01-11
I reinstalled karmic on an ext3 partiton this time. I'll try those two when I get home.

---

### Post by gradinaruvasile on 2010-01-11
Try the internal wi-fi without connecting the Linksys.

---

### Post by Marvin666 on 2010-01-11
```


marvin@Local-Machine:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 (Ubuntu 2.6.31-17.54-generic-pae)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  modified: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  modified: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  modified: 00000000cfff0000 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 10000-16000
[    0.000000] RAMDISK: 378a2000 - 37fef0d5
[    0.000000] Allocated new RAMDISK: 008b5000 - 010020d5
[    0.000000] Move RAMDISK from 00000000378a2000 - 0000000037fef0d4 to 008b5000 - 010020d4
[    0.000000] ACPI: RSDP 000f9f00 00014 (v00 MSI_NB)
[    0.000000] ACPI: RSDT cffa0000 0004C (v01 MSI_NB MEGABOOK 20090707 MSFT 00000097)
[    0.000000] ACPI: FACP cffa0200 00084 (v01 MSI_NB MEGABOOK 20090707 MSFT 00000097)
[    0.000000] ACPI: DSDT cffa0680 08A92 (v01 MSI_NB MEGABOOK 00000019 INTL 20051117)
[    0.000000] ACPI: FACS cffae000 00040
[    0.000000] ACPI: APIC cffa0390 00080 (v01 MSI_NB MEGABOOK 20090707 MSFT 00000097)
[    0.000000] ACPI: MCFG cffa0410 0003C (v01 MSI_NB OEMMCFG  20090707 MSFT 00000097)
[    0.000000] ACPI: SLIC cffa0450 00176 (v01 MSI_NB MEGABOOK 20090707 MSFT 00000097)
[    0.000000] ACPI: WDRT cffa05d0 00047 (v01 MSI_NB NV-WDRT  20090707 MSFT 00000097)
[    0.000000] ACPI: ECDT cffa0620 00055 (v01 MSI_NB OEMECDT  20090707 MSFT 00000097)
[    0.000000] ACPI: OEMB cffae040 0007A (v01 MSI_NB OEMB1404 20090707 MSFT 00000097)
[    0.000000] ACPI: HPET cffaa680 00038 (v01 MSI_NB OEMHPET0 20090707 MSFT 00000097)
[    0.000000] ACPI: NVHD cffae0c0 00284 (v01 MSI_NB  NVHDCP  20090707 MSFT 00000097)
[    0.000000] ACPI: SSDT cffaec50 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3718MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00012000 - 00018f40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]
[    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b416f]              BRK ==> [00008ae000 - 00008b416f]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [00008b5000 - 00010020d5]      NEW RAMDISK ==> [00008b5000 - 00010020d5]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cffa0
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 982830
[    0.000000] free_area_init_node: node 0, pgdat c078bd40, node_mem_map c1003200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7437 pages used for memmap
[    0.000000]   HighMem zone: 747669 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c3413000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 973613
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic-pae root=UUID=15dcd509-af17-45dd-87c7-68f3505e96c4 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 23592640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00120000)
[    0.000000] Memory: 3854104k/4718592k available (4590k kernel code, 76384k reserved, 2147k data, 544k init, 3020424k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)
[    0.000000]       .data : 0xc057b894 - 0xc07947e8   (2147 kB)
[    0.000000]       .text : 0xc0100000 - 0xc057b894   (4590 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1999.744 MHz processor.
[    0.000013] spurious 8259A interrupt: IRQ7.
[    0.001894] Console: colour VGA+ 80x25
[    0.001897] console [tty0] enabled
[    0.002066] hpet clockevent registered
[    0.002071] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.002077] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.48 BogoMIPS (lpj=7998976)
[    0.002095] Security Framework initialized
[    0.002113] AppArmor: AppArmor initialized
[    0.002120] Mount-cache hash table entries: 512
[    0.002243] Initializing cgroup subsys ns
[    0.002248] Initializing cgroup subsys cpuacct
[    0.002252] Initializing cgroup subsys memory
[    0.002258] Initializing cgroup subsys freezer
[    0.002261] Initializing cgroup subsys net_cls
[    0.002275] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002277] CPU: L2 cache: 1024K
[    0.002280] CPU: Physical Processor ID: 0
[    0.002282] CPU: Processor Core ID: 0
[    0.002286] mce: CPU supports 6 MCE banks
[    0.002293] CPU0: Thermal monitoring enabled (TM2)
[    0.002297] using mwait in idle threads.
[    0.002303] Performance Counters: Core2 events, Intel PMU driver.
[    0.002309] ... version:                 2
[    0.002310] ... bit width:               40
[    0.002312] ... generic counters:        2
[    0.002314] ... value mask:              000000ffffffffff
[    0.002315] ... max period:              000000007fffffff
[    0.002317] ... fixed-purpose counters:  3
[    0.002319] ... counter mask:            0000000700000003
[    0.002324] Checking 'hlt' instruction... OK.
[    0.018767] ACPI: Core revision 20090521
[    0.035528] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075216] CPU0: Intel Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz stepping 0a
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3999.95 BogoMIPS (lpj=7999915)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.161498] CPU1: Intel Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz stepping 0a
[    0.161515] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164020] Brought up 2 CPUs
[    0.164023] Total of 2 processors activated (7999.44 BogoMIPS).
[    0.164088] CPU0 attaching sched-domain:
[    0.164091]  domain 0: span 0-1 level MC
[    0.164094]   groups: 0 1
[    0.164099] CPU1 attaching sched-domain:
[    0.164101]  domain 0: span 0-1 level MC
[    0.164103]   groups: 1 0
[    0.164178] Booting paravirtualized kernel on bare hardware
[    0.164214] regulator: core version 0.5
[    0.164214] Time: 19:51:50  Date: 01/11/10
[    0.164214] NET: Registered protocol family 16
[    0.164239] EISA bus registered
[    0.164249] ACPI: bus type pci registered
[    0.164323] PCI: MCFG configuration 0: base fc000000 segment 0 buses 0 - 31
[    0.164325] PCI: Not using MMCONFIG.
[    0.164522] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.164524] PCI: Using configuration type 1 for base access
[    0.165550] bio: create slab <bio-0> at 0
[    0.169227] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.169243] ACPI: EC: EC description table is found, configuring boot EC
[    0.169256] ACPI: EC: Look up EC in DSDT
[    0.170107] ACPI: EC: ASUSTek keeps feeding us with broken ECDT tables, which are very hard to workaround. Trying to use DSDT EC info instead. Please send output of acpidump to linux-acpi@vger.kernel.org
[    0.178223] ACPI: Interpreter enabled
[    0.178230] ACPI: (supports S0 S1 S3 S4 S5)
[    0.178253] ACPI: Using IOAPIC for interrupt routing
[    0.178320] PCI: MCFG configuration 0: base fc000000 segment 0 buses 0 - 31
[    0.179328] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.192061] PCI: MCFG area at fc000000 reserved in ACPI motherboard resources
[    0.192064] PCI: Using MMCONFIG for extended config space
[    0.216079] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.216082] ACPI: EC: driver started in interrupt mode
[    0.216543] ACPI: No dock devices found.
[    0.217065] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.217315] pci 0000:00:03.0: reg 10 io port: [0x4f00-0x4fff]
[    0.217428] pci 0000:00:03.2: reg 10 io port: [0x4900-0x493f]
[    0.217444] pci 0000:00:03.2: reg 20 io port: [0x4d00-0x4d3f]
[    0.217450] pci 0000:00:03.2: reg 24 io port: [0x4e00-0x4e3f]
[    0.217476] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.217482] pci 0000:00:03.2: PME# disabled
[    0.217619] pci 0000:00:03.5: reg 10 32bit mmio: [0xfae80000-0xfaefffff]
[    0.217717] pci 0000:00:04.0: reg 10 32bit mmio: [0xfae7f000-0xfae7ffff]
[    0.217752] pci 0000:00:04.0: supports D1 D2
[    0.217755] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.217759] pci 0000:00:04.0: PME# disabled
[    0.217792] pci 0000:00:04.1: reg 10 32bit mmio: [0xfae7ec00-0xfae7ecff]
[    0.217833] pci 0000:00:04.1: supports D1 D2
[    0.217836] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.217840] pci 0000:00:04.1: PME# disabled
[    0.217880] pci 0000:00:08.0: reg 10 32bit mmio: [0xfae78000-0xfae7bfff]
[    0.217915] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.217919] pci 0000:00:08.0: PME# disabled
[    0.217984] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfae7d000-0xfae7dfff]
[    0.217990] pci 0000:00:0a.0: reg 14 io port: [0xc080-0xc087]
[    0.217995] pci 0000:00:0a.0: reg 18 32bit mmio: [0xfae7e800-0xfae7e8ff]
[    0.218001] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xfae7e400-0xfae7e40f]
[    0.218026] pci 0000:00:0a.0: supports D1 D2
[    0.218029] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.218034] pci 0000:00:0a.0: PME# disabled
[    0.218066] pci 0000:00:0b.0: reg 10 io port: [0xc000-0xc007]
[    0.218071] pci 0000:00:0b.0: reg 14 io port: [0xbc00-0xbc03]
[    0.218077] pci 0000:00:0b.0: reg 18 io port: [0xb880-0xb887]
[    0.218082] pci 0000:00:0b.0: reg 1c io port: [0xb800-0xb803]
[    0.218087] pci 0000:00:0b.0: reg 20 io port: [0xb480-0xb48f]
[    0.218093] pci 0000:00:0b.0: reg 24 32bit mmio: [0xfae72000-0xfae73fff]
[    0.218171] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.218175] pci 0000:00:10.0: PME# disabled
[    0.218383] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.218391] pci 0000:00:15.0: PME# disabled
[    0.218624] pci 0000:00:17.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.218632] pci 0000:00:17.0: PME# disabled
[    0.218724] pci 0000:00:09.0: transparent bridge
[    0.218766] pci 0000:02:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.218777] pci 0000:02:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.218787] pci 0000:02:00.0: reg 1c 64bit mmio: [0xf6000000-0xf7ffffff]
[    0.218794] pci 0000:02:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.218801] pci 0000:02:00.0: reg 30 32bit mmio: [0xfafe0000-0xfaffffff]
[    0.218865] pci 0000:00:10.0: bridge io port: [0xd000-0xdfff]
[    0.218868] pci 0000:00:10.0: bridge 32bit mmio: [0xfaf00000-0xfbffffff]
[    0.218874] pci 0000:00:10.0: bridge 64bit mmio pref: [0xe0000000-0xf7ffffff]
[    0.218940] pci 0000:00:15.0: bridge io port: [0xe000-0xefff]
[    0.218949] pci 0000:00:15.0: bridge 32bit mmio: [0xfe000000-0xfeafffff]
[    0.218970] pci 0000:00:15.0: bridge 64bit mmio pref: [0xf8000000-0xf9ffffff]
[    0.219027] pci 0000:06:00.0: reg 10 64bit mmio: [0xfebf0000-0xfebfffff]
[    0.219085] pci 0000:06:00.0: supports D1
[    0.219087] pci 0000:06:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.219092] pci 0000:06:00.0: PME# disabled
[    0.219172] pci 0000:00:17.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.219220] pci_bus 0000:00: on NUMA node 0
[    0.219225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.219418] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]
[    0.219501] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.219594] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.219696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.228880] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.229189] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.229494] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.229800] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.230103] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *0, disabled.
[    0.230405] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.230710] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.231013] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.231318] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.231623] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.231928] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.232238] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.232542] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.232847] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.233153] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.233454] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.233756] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *0, disabled.
[    0.234060] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.234364] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.234669] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.234973] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.235277] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.235582] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.235886] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.236199] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *15
[    0.236503] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.236808] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.237111] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.237415] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.237719] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.238023] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.238327] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.238637] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *7
[    0.238950] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.239259] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *9
[    0.239567] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.239874] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *9
[    0.240185] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *15
[    0.240496] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *14
[    0.240808] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.241164] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.241469] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *0, disabled.
[    0.241771] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *0, disabled.
[    0.242075] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *0, disabled.
[    0.242380] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
[    0.242684] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
[    0.242995] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *10
[    0.243302] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *0, disabled.
[    0.243612] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *11
[    0.243920] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *0, disabled.
[    0.244122] SCSI subsystem initialized
[    0.244153] libata version 3.00 loaded.
[    0.244153] usbcore: registered new interface driver usbfs
[    0.244153] usbcore: registered new interface driver hub
[    0.244153] usbcore: registered new device driver usb
[    0.244153] ACPI: WMI: Mapper loaded
[    0.244153] PCI: Using ACPI for IRQ routing
[    0.256010] Bluetooth: Core ver 2.15
[    0.256025] NET: Registered protocol family 31
[    0.256025] Bluetooth: HCI device and connection manager initialized
[    0.256025] Bluetooth: HCI socket layer initialized
[    0.256025] NetLabel: Initializing
[    0.256025] NetLabel:  domain hash size = 128
[    0.256025] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.256034] NetLabel:  unlabeled traffic allowed by default
[    0.256065] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.256071] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.272012] pnp: PnP ACPI init
[    0.272031] ACPI: bus type pnp registered
[    0.282594] pnp: PnP ACPI: found 12 devices
[    0.282597] ACPI: ACPI bus type pnp unregistered
[    0.282601] PnPBIOS: Disabled by ACPI PNP
[    0.282616] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.282619] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.282622] system 00:04: ioport range 0x4000-0x407f has been reserved
[    0.282624] system 00:04: ioport range 0x4080-0x40ff has been reserved
[    0.282627] system 00:04: ioport range 0x4400-0x447f has been reserved
[    0.282630] system 00:04: ioport range 0x4480-0x44ff has been reserved
[    0.282633] system 00:04: ioport range 0x4800-0x487f has been reserved
[    0.282636] system 00:04: ioport range 0x4880-0x48ff has been reserved
[    0.282640] system 00:04: iomem range 0xfefe2000-0xfefe3fff has been reserved
[    0.282643] system 00:04: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.282646] system 00:04: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.282653] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.282656] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.282662] system 00:0a: iomem range 0xfc000000-0xfdffffff has been reserved
[    0.282668] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.282671] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.282674] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.282677] system 00:0b: iomem range 0x100000-0xdfffffff could not be reserved
[    0.282680] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.317358] AppArmor: AppArmor Filesystem Enabled
[    0.317425] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
[    0.317428] pci 0000:00:09.0:   IO window: disabled
[    0.317433] pci 0000:00:09.0:   MEM window: disabled
[    0.317438] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.317442] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.317446] pci 0000:00:10.0:   IO window: 0xd000-0xdfff
[    0.317451] pci 0000:00:10.0:   MEM window: 0xfaf00000-0xfbffffff
[    0.317456] pci 0000:00:10.0:   PREFETCH window: 0x000000e0000000-0x000000f7ffffff
[    0.317462] pci 0000:00:15.0: PCI bridge, secondary bus 0000:03
[    0.317468] pci 0000:00:15.0:   IO window: 0xe000-0xefff
[    0.317480] pci 0000:00:15.0:   MEM window: 0xfe000000-0xfeafffff
[    0.317489] pci 0000:00:15.0:   PREFETCH window: 0x000000f8000000-0x000000f9ffffff
[    0.317504] pci 0000:00:17.0: PCI bridge, secondary bus 0000:06
[    0.317506] pci 0000:00:17.0:   IO window: disabled
[    0.317518] pci 0000:00:17.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.317527] pci 0000:00:17.0:   PREFETCH window: disabled
[    0.317541] pci 0000:00:09.0: setting latency timer to 64
[    0.317548] pci 0000:00:10.0: setting latency timer to 64
[    0.317985] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 23
[    0.317989]   alloc irq_desc for 23 on node -1
[    0.317991]   alloc kstat_irqs on node -1
[    0.317997] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 23 (level, low) -> IRQ 23
[    0.318006] pci 0000:00:15.0: setting latency timer to 64
[    0.318431] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 22
[    0.318434]   alloc irq_desc for 22 on node -1
[    0.318436]   alloc kstat_irqs on node -1
[    0.318440] pci 0000:00:17.0: PCI INT A -> Link[LRP5] -> GSI 22 (level, low) -> IRQ 22
[    0.318449] pci 0000:00:17.0: setting latency timer to 64
[    0.318456] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.318459] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.318462] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.318464] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.318467] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.318470] pci_bus 0000:02: resource 1 mem: [0xfaf00000-0xfbffffff]
[    0.318473] pci_bus 0000:02: resource 2 pref mem [0xe0000000-0xf7ffffff]
[    0.318475] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.318478] pci_bus 0000:03: resource 1 mem: [0xfe000000-0xfeafffff]
[    0.318481] pci_bus 0000:03: resource 2 pref mem [0xf8000000-0xf9ffffff]
[    0.318483] pci_bus 0000:06: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.318520] NET: Registered protocol family 2
[    0.318621] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.318943] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.319369] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.319644] TCP: Hash tables configured (established 131072 bind 65536)
[    0.319647] TCP reno registered
[    0.319762] NET: Registered protocol family 1
[    0.319830] Trying to unpack rootfs image as initramfs...
[    0.501562] Switched to high resolution mode on CPU 1
[    0.504030] Switched to high resolution mode on CPU 0
[    0.509835] Freeing initrd memory: 7476k freed
[    0.514284] cpufreq-nforce2: No nForce2 chipset.
[    0.514312] Scanning for low memory corruption every 60 seconds
[    0.514417] audit: initializing netlink socket (disabled)
[    0.514433] type=2000 audit(1263239510.512:1): initialized
[    0.523173] highmem bounce pool size: 64 pages
[    0.523178] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.524619] VFS: Disk quotas dquot_6.5.2
[    0.524678] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.525219] fuse init (API version 7.12)
[    0.525302] msgmni has been set to 1644
[    0.525507] alg: No test for stdrng (krng)
[    0.525521] io scheduler noop registered
[    0.525523] io scheduler anticipatory registered
[    0.525525] io scheduler deadline registered
[    0.525568] io scheduler cfq registered (default)
[    0.548099] pci 0000:02:00.0: Boot video device
[    0.548391]   alloc irq_desc for 24 on node -1
[    0.548393]   alloc kstat_irqs on node -1
[    0.548414] pcieport-driver 0000:00:15.0: irq 24 for MSI/MSI-X
[    0.548436] pcieport-driver 0000:00:15.0: setting latency timer to 64
[    0.548805]   alloc irq_desc for 25 on node -1
[    0.548807]   alloc kstat_irqs on node -1
[    0.548825] pcieport-driver 0000:00:17.0: irq 25 for MSI/MSI-X
[    0.548845] pcieport-driver 0000:00:17.0: setting latency timer to 64
[    0.549015] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.549040] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.552762] ACPI: AC Adapter [ADP1] (on-line)
[    0.552842] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.552845] ACPI: Power Button [PWRF]
[    0.552903] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C09:00/PNP0C0D:00/input/input1
[    0.556472] ACPI: Lid Switch [LID0]
[    0.556522] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/PNP0C09:00/PNP0C0E:00/input/input2
[    0.556525] ACPI: Sleep Button [SLPB]
[    0.556573] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    0.556576] ACPI: Power Button [PWRB]
[    0.557312] ACPI: SSDT cffae420 001FA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.557937] ACPI: SSDT cffae6b0 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.558474] Monitor-Mwait will be used to enter C-1 state
[    0.558502] Monitor-Mwait will be used to enter C-2 state
[    0.558524] Monitor-Mwait will be used to enter C-3 state
[    0.558532] Marking TSC unstable due to TSC halts in idle
[    0.558552] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.558578] processor LNXCPU:00: registered as cooling_device0
[    0.558582] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.558930] ACPI: SSDT cffae350 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.559381] ACPI: SSDT cffae620 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.560075] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.560100] processor LNXCPU:01: registered as cooling_device1
[    0.560103] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.578547] thermal LNXTHERM:01: registered as thermal_zone0
[    0.578555] ACPI: Thermal Zone [THRM] (56 C)
[    0.578629] isapnp: Scanning for PnP cards...
[    0.776594] ACPI: Battery Slot [BAT1] (battery present)
[    0.933381] isapnp: No Plug & Play device found
[    0.934594] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.935922] brd: module loaded
[    0.936394] loop: module loaded
[    0.936467] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.936542] ahci 0000:00:0b.0: version 3.0
[    0.936991] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[    0.936996]   alloc irq_desc for 21 on node -1
[    0.936998]   alloc kstat_irqs on node -1
[    0.937005] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 21 (level, low) -> IRQ 21
[    0.937040]   alloc irq_desc for 26 on node -1
[    0.937042]   alloc kstat_irqs on node -1
[    0.937049] ahci 0000:00:0b.0: irq 26 for MSI/MSI-X
[    0.937089] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    0.937092] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pmp pio slum part 
[    0.937097] ahci 0000:00:0b.0: setting latency timer to 64
[    0.937277] scsi0 : ahci
[    0.937378] scsi1 : ahci
[    0.937456] ata1: SATA max UDMA/133 abar m8192@0xfae72000 port 0xfae72100 irq 26
[    0.937459] ata2: SATA max UDMA/133 abar m8192@0xfae72000 port 0xfae72180 irq 26
[    0.938347] Fixed MDIO Bus: probed
[    0.938383] PPP generic driver version 2.4.2
[    0.938480] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.938934] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
[    0.938940]   alloc irq_desc for 20 on node -1
[    0.938942]   alloc kstat_irqs on node -1
[    0.938948] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 20 (level, low) -> IRQ 20
[    0.938962] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.938966] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.939024] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.939051] ehci_hcd 0000:00:04.1: debug port 1
[    0.939056] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    0.939069] ehci_hcd 0000:00:04.1: irq 20, io mem 0xfae7ec00
[    0.948012] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.948082] usb usb1: configuration #1 chosen from 1 choice
[    0.948114] hub 1-0:1.0: USB hub found
[    0.948122] hub 1-0:1.0: 9 ports detected
[    0.948186] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.948633] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    0.948637] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    0.948649] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.948652] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.948686] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    0.948707] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfae7f000
[    1.006064] usb usb2: configuration #1 chosen from 1 choice
[    1.006091] hub 2-0:1.0: USB hub found
[    1.006099] hub 2-0:1.0: 9 ports detected
[    1.006156] uhci_hcd: USB Universal Host Controller Interface driver
[    1.006236] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.033075] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.033081] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.033143] mice: PS/2 mouse device common for all mice
[    1.033279] rtc_cmos 00:06: RTC can wake from S4
[    1.033316] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.033365] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.033462] device-mapper: uevent: version 1.0.3
[    1.033555] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.033615] device-mapper: multipath: version 1.1.0 loaded
[    1.033617] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.033728] EISA: Probing bus 0 at eisa.0
[    1.033743] Cannot allocate resource for EISA slot 4
[    1.033757] EISA: Detected 0 cards.
[    1.033906] cpuidle: using governor ladder
[    1.034067] cpuidle: using governor menu
[    1.034558] TCP cubic registered
[    1.034708] NET: Registered protocol family 10
[    1.035172] lo: Disabled Privacy Extensions
[    1.035509] NET: Registered protocol family 17
[    1.035527] Bluetooth: L2CAP ver 2.13
[    1.035529] Bluetooth: L2CAP socket layer initialized
[    1.035532] Bluetooth: SCO (Voice Link) ver 0.6
[    1.035533] Bluetooth: SCO socket layer initialized
[    1.035573] Bluetooth: RFCOMM TTY layer initialized
[    1.035576] Bluetooth: RFCOMM socket layer initialized
[    1.035578] Bluetooth: RFCOMM ver 1.11
[    1.036025] Using IPI No-Shortcut mode
[    1.036088] PM: Resume from disk failed.
[    1.036101] registered taskstats version 1
[    1.036211]   Magic number: 10:150:900
[    1.036333] rtc_cmos 00:06: setting system clock to 2010-01-11 19:51:51 UTC (1263239511)
[    1.036336] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.036338] EDD information not available.
[    1.053987] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.420071] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.420089] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.435821] ata2.00: ATAPI: HL-DT-STDVDRAM GT10N, 1.01, max UDMA/100
[    1.438847] ata2.00: configured for UDMA/100
[    1.473155] ata1.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133
[    1.473160] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.475699] ata1.00: configured for UDMA/133
[    1.475821] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5
[    1.475937] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.475974] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.476018] sd 0:0:0:0: [sda] Write Protect is off
[    1.476021] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.476046] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.476172]  sda: sda1 sda2 sda3 sda4
[    1.491299] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT10N     1.01 PQ: 0 ANSI: 5
[    1.498952] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.498957] Uniform CD-ROM driver Revision: 3.20
[    1.499084] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.499132] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.516864] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.516895] Freeing unused kernel memory: 544k freed
[    1.517233] Write protecting the kernel text: 4592k
[    1.517334] Write protecting the kernel read-only data: 1836k
[    1.650043] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    1.662456] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.662939] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    1.662945] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.662951] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.685870] acpi device:09: registered as cooling_device2
[    1.687278] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:07/device:08/input/input6
[    1.687317] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    1.725930] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:21:85:e8:69:28
[    1.725935] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    2.000060] Clocksource tsc unstable (delta = -148354978 ns)
[    2.956220] PM: Starting manual resume from disk
[    2.956224] PM: Resume from partition 8:2
[    2.956226] PM: Checking hibernation image.
[    2.956401] PM: Resume from disk failed.
[    2.987247] kjournald starting.  Commit interval 5 seconds
[    2.987262] EXT3-fs: mounted filesystem with writeback data mode.
[    3.795494] type=1505 audit(1263239514.255:2): operation="profile_load" pid=399 name=/sbin/dhclient3
[    3.795549] type=1505 audit(1263239514.255:3): operation="profile_load" pid=399 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.795589] type=1505 audit(1263239514.255:4): operation="profile_load" pid=399 name=/usr/lib/connman/scripts/dhclient-script
[   13.423081] type=1505 audit(1263239523.883:5): operation="profile_load" pid=400 name=/usr/bin/evince
[   13.423657] type=1505 audit(1263239523.883:6): operation="profile_load" pid=400 name=/usr/bin/evince-previewer
[   13.424188] type=1505 audit(1263239523.887:7): operation="profile_load" pid=400 name=/usr/bin/evince-thumbnailer
[   13.692069] type=1505 audit(1263239524.155:8): operation="profile_load" pid=402 name=/usr/lib/cups/backend/cups-pdf
[   13.692197] type=1505 audit(1263239524.155:9): operation="profile_load" pid=402 name=/usr/sbin/cupsd
[   13.769703] type=1505 audit(1263239524.232:10): operation="profile_load" pid=403 name=/usr/sbin/tcpdump
[   14.529692] Adding 10482404k swap on /dev/sda2.  Priority:-1 extents:1 across:10482404k 
[   14.603764] udev: starting version 147
[   15.223229] lp: driver loaded but no devices found
[   15.276118] cfg80211: Calling CRDA to update world regulatory domain
[   15.379252] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.468862] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4d00
[   15.468868] ACPI: I/O resource nForce2_smbus [0x4e00-0x4e3f] conflicts with ACPI region SM00 [0x4e00-0x4e3f]
[   15.468871] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.468873] nForce2_smbus 0000:00:03.2: Error probing SMB2.
[   15.680922] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.839970] psmouse serio1: ID: 10 00 64
[   16.021145] ACPI: PCI Interrupt Link [LN5A] enabled at IRQ 19
[   16.021152]   alloc irq_desc for 19 on node -1
[   16.021154]   alloc kstat_irqs on node -1
[   16.021162] ath9k 0000:06:00.0: PCI INT A -> Link[LN5A] -> GSI 19 (level, low) -> IRQ 19
[   16.021172] ath9k 0000:06:00.0: setting latency timer to 64
[   16.069738] ath: EEPROM regdomain: 0x60
[   16.069741] ath: EEPROM indicates we should expect a direct regpair map
[   16.069744] ath: Country alpha2 being used: 00
[   16.069746] ath: Regpair used: 0x60
[   16.443066] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   16.443521] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   16.443527] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   16.443573] HDA Intel 0000:00:08.0: setting latency timer to 64
[   16.579515] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.580291] Registered led device: ath9k-phy0::radio
[   16.580309] Registered led device: ath9k-phy0::assoc
[   16.580330] Registered led device: ath9k-phy0::tx
[   16.580348] Registered led device: ath9k-phy0::rx
[   16.580369] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8be0000, irq=19
[   16.614880] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input7
[   16.918323] cfg80211: World regulatory domain updated:
[   16.918327]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.918330]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.918345]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.918348]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.918351]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.918353]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.148067] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   17.164126] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input8
[   17.643629] EXT3 FS on sda3, internal journal
[   18.838122] kjournald starting.  Commit interval 5 seconds
[   18.838489] EXT3 FS on sda4, internal journal
[   18.838497] EXT3-fs: mounted filesystem with writeback data mode.
[   20.655525] type=1505 audit(1263239531.116:11): operation="profile_replace" pid=1007 name=/sbin/dhclient3
[   20.655664] type=1505 audit(1263239531.116:12): operation="profile_replace" pid=1007 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   20.655744] type=1505 audit(1263239531.116:13): operation="profile_replace" pid=1007 name=/usr/lib/connman/scripts/dhclient-script
[   30.487692] type=1505 audit(1263239540.947:14): operation="profile_replace" pid=1009 name=/usr/bin/evince
[   30.489277] type=1505 audit(1263239540.951:15): operation="profile_replace" pid=1009 name=/usr/bin/evince-previewer
[   30.490292] type=1505 audit(1263239540.951:16): operation="profile_replace" pid=1009 name=/usr/bin/evince-thumbnailer
[   30.782063] type=1505 audit(1263239541.243:17): operation="profile_replace" pid=1251 name=/usr/lib/cups/backend/cups-pdf
[   30.782288] type=1505 audit(1263239541.243:18): operation="profile_replace" pid=1251 name=/usr/sbin/cupsd
[   30.865405] type=1505 audit(1263239541.327:19): operation="profile_replace" pid=1252 name=/usr/sbin/tcpdump
[   31.552039] eth0: no IPv6 routers present
[   32.915749] ppdev: user-space parallel port driver
marvin@Local-Machine:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
marvin@Local-Machine:~$ 

```Blocked by hardware? I need to try and find a manual for my laptop, it didn't come with an accessible one. I assume it was in pdf format, buried in the windows partition...
EDIT: I found a very well hidden hardware switch, and turned it "on", but it had no effect.

---

### Post by Marvin666 on 2010-01-11
I tried a reboot, and it works now, but there's one catch. I can't get it to use my external wifi card. Is there a way to disable the internal one?
To make troubleshooting easier, I set up the router to only allow wireless connections from the external card.

---

### Post by gradinaruvasile on 2010-01-11
Ok... Well i dont know what BIOS options you have there. It should be obvious, like internal wifi on/off. If there is any. Usually there are. If there is, reboot without the external card and look at the dmesg/rfkill/lspci outputs to confirm that the system cant see it at all.
Also, check the BIOS for options for pci/pcimcia or something like that. lspci did not show your external card so it might be something like a BIOS option to enable/disable the external connectors.

---

### Post by Marvin666 on 2010-01-11
Couldn't find anything in the bios, so I just messed with the drivers, and now I have both cards working. All my connections seem to be independent of each other. How would I make it so I can control the channel and protocol of an adhock I created? Also, is there a way to get this information about a network, before I connect to it? Stupid unstable karmic:
Your system encountered a serious kernel problem. Your system might become unstable now and might need to be restarted.

---

### Post by Marvin666 on 2010-01-11
Figured out selecting a channel, but the program seem to be g only.
Anybody know of a program that lets me make an a, or n ad-hock, and choose the channel on it?

---

### Post by gradinaruvasile on 2010-01-12
Well ican't help you with that. Never used this kind of stuff on Ubuntu. We did try the ad-hoc thing on Windows but was utterly unreliable.

But im glad that you got the cards working.

---

