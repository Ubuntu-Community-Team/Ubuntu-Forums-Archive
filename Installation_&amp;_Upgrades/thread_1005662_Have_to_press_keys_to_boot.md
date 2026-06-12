---
title: "Have to press keys to boot"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by jfbilodeau on 2008-12-08
Good day all,

I had a strange problem when using the 8.10 live CD. To get to the /etc/init.d scripts, I had to continuously press a key on the keyboard. Otherwise, the kernel bootstrap seemed to hang.

Booting without the splash and quiet option removed clearly showed that the kernel would hang after spitting out info on the console, then resume the moment I pressed a key. It didn't seem to matter which key I used.

I was able to succesfully install Ubuntu 8.10, but upon reboot, I had to press keys for the new kernel to boot.

Has anyone else seen this?

lshw:
```

WARNING: you should run this program as super-user.
golbez                    
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1919MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-58
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          size: 1900MHz
          capacity: 1900MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial UNCLAIMED
          description: SMBus
          product: MCP67 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP67 Co-processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
     *-usb:0
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-usb:2
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 4


          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:3
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP67 IDE Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7561A
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: GH09
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 5
             bus info: pci@0000:02:05.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-system:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.1
             bus info: pci@0000:02:05.1
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=sdhci-pci latency=64 module=sdhci_pci
        *-system:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.2
             bus info: pci@0000:02:05.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ricoh-mmc latency=64 module=ricoh_mmc
        *-system:2 UNCLAIMED
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 5.3
             bus info: pci@0000:02:05.3
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=64
        *-generic UNCLAIMED
             product: Illegal Vendor ID
             vendor: Illegal Vendor ID
             physical id: 5.4
             bus info: pci@0000:02:05.4
             version: ff
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master vga_palette cap_list
             configuration: latency=255 maxlatency=255 mingnt=255
     *-ide:1
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1b:24:cf:29:bd
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.173 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
        *-network
             description: Network controller
             product: BCM4311 802.11b/g WLAN
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=b43-pci-bridge latency=0 module=ssb
     *-display UNCLAIMED
          description: VGA compatible controller
          product: GeForce 7150M
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: latency=0
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:c2:bb:f2:6e:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:c4:95:a6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=f6b0d80d-ecd2-43b9-98db-375d71093220 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077f50000 (usable)
[    0.000000]  BIOS-e820: 0000000077f50000 - 0000000077f65000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077f65000 - 0000000077f66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077f66000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x77f50 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 0077e00000 page 2M
[    0.000000]  0077e00000 - 0077f50000 page 4k
[    0.000000] kernel direct mapping tables up to 77f50000 @ 8000-c000
[    0.000000] last_map_addr: 77f50000 end: 77f50000
[    0.000000] RAMDISK: 377b1000 - 37fefaf6
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 77F5C0FB, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 77F649BA, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 77F5C167, 87DF (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 77F65FC0, 0040
[    0.000000] ACPI: TCPA 77F64AAE, 0032 (r1 Phoeni  x        6040000  TL         0)
[    0.000000] ACPI: SRAT 77F64AE0, 00A0 (r1 AMD    HAMMER    6040000 AMD         1)
[    0.000000] ACPI: SSDT 77F64B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 77F64D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 77F64DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 77F64DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 77F64E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 77F64E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-80000000
[    0.000000] NUMA: Allocated memnodemap from a000 - b080
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-0000000077f50000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000c000 -  000000000001afef] pages f
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0077f50000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b1000 - 0037fefaf6]          RAMDISK ==> [00377b1000 - 0037fefaf6]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #6 [000000a000 - 000000b080]       MEMNODEMAP ==> [000000a000 - 000000b080]
[    0.000000] found SMP MP-table at [ffff8800000f8220] 000f8220
[    0.000000]  [ffffe20000000000-ffffe20001dfffff] PMD -> [ffff880001200000-ffff880002ffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x00077f50
[    0.000000] On node 0 totalpages: 491246
[    0.000000]   DMA zone: 2108 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 479634 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 481742
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=f6b0d80d-ecd2-43b9-98db-375d71093220 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1900.127 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ c00000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 1918628k/1965376k available (3112k kernel code, 46356k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3800.25 BogoMIPS (lpj=7600508)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] tseg: 0077f80000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] ACPI: Core revision 20080609
[    0.006661] ACPI: Checking initramfs for custom DSDT
[    0.380615] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.422247] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[    0.422252] Using local APIC timer interrupts.
[    0.424028] APIC timer calibration result 12500871
[    0.424029] Detected 12.500 MHz APIC timer.
[    0.424210] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3800.33 BogoMIPS (lpj=7600663)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.512193] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[    0.512214] Brought up 2 CPUs
[    0.512217] Total of 2 processors activated (7600.58 BogoMIPS).
[    0.512057] System has AMD C1E enabled
[    0.512074] Switch to broadcast mode on CPU1
[    0.512300] CPU0 attaching sched-domain:
[    0.512303]  domain 0: span 0-1 level CPU
[    0.512306]   groups: 0 1
[    0.512310]   domain 1: span 0-1 level NODE
[    0.512312]    groups: 0-1
[    0.512318] CPU1 attaching sched-domain:
[    0.512320]  domain 0: span 0-1 level CPU
[    0.512322]   groups: 1 0
[    0.512326]   domain 1: span 0-1 level NODE
[    0.512328]    groups: 0-1
[    0.512427] Switch to broadcast mode on CPU0
[    0.512427] net_namespace: 1552 bytes
[    0.512427] Booting paravirtualized kernel on bare hardware
[    0.512427] Time: 14:17:11  Date: 12/08/08
[    0.512427] NET: Registered protocol family 16
[    0.512448] node 0 link 0: io port [1000, fffff]
[    0.512448] TOM: 0000000080000000 aka 2048M
[    0.512448] node 0 link 0: mmio [a0000, bffff]
[    0.512448] node 0 link 0: mmio [80000000, dfffffff]
[    0.512448] node 0 link 0: mmio [e0000000, efffffff]
[    0.512448] node 0 link 0: mmio [f0000000, fe0bffff]
[    0.512448] bus: [00,ff] on node 0 link 0
[    0.512448] bus: 00 index 0 io port: [0, ffff]
[    0.512448] bus: 00 index 1 mmio: [a0000, bffff]
[    0.512448] bus: 00 index 2 mmio: [80000000, fcffffffff]
[    0.512448] ACPI: bus type pci registered
[    0.512448] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.512448] PCI: MCFG area at e0000000 reserved in E820
[    0.512448] PCI: Using MMCONFIG at e0000000 - e04fffff
[    0.512448] PCI: Using configuration type 1 for base access
[    0.512788] ACPI: EC: Look up EC in DSDT
[    0.519898] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.520869] ACPI: Interpreter enabled
[    0.520872] ACPI: (supports S0 S3 S4 S5)
[    0.520890] ACPI: Using IOAPIC for interrupt routing
[    0.520965] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.544222] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.544222] ACPI: EC: driver started in interrupt mode
[    0.544222] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.544222] PCI: 0000:00:01.1 reg 10 io port: [3080, 30bf]
[    0.544222] PCI: 0000:00:01.1 reg 20 io port: [3040, 307f]
[    0.544222] PCI: 0000:00:01.1 reg 24 io port: [3000, 303f]
[    0.544233] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.544239] pci 0000:00:01.1: PME# disabled
[    0.544287] PCI: 0000:00:01.3 reg 10 32bit mmio: [f6200000, f627ffff]
[    0.544361] PCI: 0000:00:02.0 reg 10 32bit mmio: [f6486000, f6486fff]
[    0.544382] pci 0000:00:02.0: supports D1
[    0.544384] pci 0000:00:02.0: supports D2
[    0.544386] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544389] pci 0000:00:02.0: PME# disabled
[    0.544409] PCI: 0000:00:02.1 reg 10 32bit mmio: [f6489000, f64890ff]
[    0.544433] pci 0000:00:02.1: supports D1
[    0.544434] pci 0000:00:02.1: supports D2
[    0.544436] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544440] pci 0000:00:02.1: PME# disabled
[    0.544461] PCI: 0000:00:04.0 reg 10 32bit mmio: [f6487000, f6487fff]
[    0.544482] pci 0000:00:04.0: supports D1
[    0.544484] pci 0000:00:04.0: supports D2
[    0.544486] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544489] pci 0000:00:04.0: PME# disabled
[    0.544509] PCI: 0000:00:04.1 reg 10 32bit mmio: [f6489400, f64894ff]
[    0.544533] pci 0000:00:04.1: supports D1
[    0.544535] pci 0000:00:04.1: supports D2
[    0.544537] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544540] pci 0000:00:04.1: PME# disabled
[    0.544574] PCI: 0000:00:06.0 reg 20 io port: [30c0, 30cf]
[    0.544609] PCI: 0000:00:07.0 reg 10 32bit mmio: [f6480000, f6483fff]
[    0.544634] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.544637] pci 0000:00:07.0: PME# disabled
[    0.544690] PCI: 0000:00:09.0 reg 10 io port: [30f0, 30f7]
[    0.544694] PCI: 0000:00:09.0 reg 14 io port: [30e4, 30e7]
[    0.544698] PCI: 0000:00:09.0 reg 18 io port: [30e8, 30ef]
[    0.544701] PCI: 0000:00:09.0 reg 1c io port: [30e0, 30e3]
[    0.544705] PCI: 0000:00:09.0 reg 20 io port: [30d0, 30df]
[    0.544709] PCI: 0000:00:09.0 reg 24 32bit mmio: [f6484000, f6485fff]
[    0.544749] PCI: 0000:00:0a.0 reg 10 32bit mmio: [f6488000, f6488fff]
[    0.544754] PCI: 0000:00:0a.0 reg 14 io port: [30f8, 30ff]
[    0.544758] PCI: 0000:00:0a.0 reg 18 32bit mmio: [f6489c00, f6489cff]
[    0.544762] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [f6489800, f648980f]
[    0.544780] pci 0000:00:0a.0: supports D1
[    0.544781] pci 0000:00:0a.0: supports D2
[    0.544783] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544788] pci 0000:00:0a.0: PME# disabled
[    0.544816] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544819] pci 0000:00:0c.0: PME# disabled
[    0.544846] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544849] pci 0000:00:0d.0: PME# disabled
[    0.544867] PCI: 0000:00:12.0 reg 10 32bit mmio: [f5000000, f5ffffff]
[    0.544871] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.544878] PCI: 0000:00:12.0 reg 1c 64bit mmio: [f4000000, f4ffffff]
[    0.544883] PCI: 0000:00:12.0 reg 30 32bit mmio: [0, 1ffff]
[    0.544915] PCI: 0000:02:05.0 reg 10 32bit mmio: [f6100000, f61007ff]
[    0.544915] pci 0000:02:05.0: supports D1
[    0.544915] pci 0000:02:05.0: supports D2
[    0.544915] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544915] pci 0000:02:05.0: PME# disabled
[    0.544915] PCI: 0000:02:05.1 reg 10 32bit mmio: [f6100800, f61008ff]
[    0.544915] pci 0000:02:05.1: supports D1
[    0.544915] pci 0000:02:05.1: supports D2
[    0.544915] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544915] pci 0000:02:05.1: PME# disabled
[    0.544915] PCI: 0000:02:05.2 reg 10 32bit mmio: [f6100c00, f6100cff]
[    0.544915] pci 0000:02:05.2: supports D1
[    0.544915] pci 0000:02:05.2: supports D2
[    0.544915] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544915] pci 0000:02:05.2: PME# disabled
[    0.544915] PCI: 0000:02:05.3 reg 10 32bit mmio: [f6101000, f61010ff]
[    0.544915] pci 0000:02:05.3: supports D1
[    0.544915] pci 0000:02:05.3: supports D2
[    0.544915] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544915] pci 0000:02:05.3: PME# disabled
[    0.544915] PCI: 0000:02:05.4 reg 10 32bit mmio: [f6101400, f61014ff]
[    0.544915] pci 0000:02:05.4: supports D1
[    0.544915] pci 0000:02:05.4: supports D2
[    0.544915] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544915] pci 0000:02:05.4: PME# disabled
[    0.544915] pci 0000:00:08.0: transparent bridge
[    0.544915] PCI: bridge 0000:00:08.0 32bit mmio: [f6100000, f61fffff]
[    0.544915] PCI: bridge 0000:00:0c.0 io port: [4000, 4fff]
[    0.544915] PCI: bridge 0000:00:0c.0 32bit mmio: [f2000000, f3ffffff]
[    0.544915] PCI: bridge 0000:00:0c.0 64bit mmio pref: [f0000000, f1ffffff]
[    0.544915] PCI: 0000:03:00.0 reg 10 64bit mmio: [f6000000, f6003fff]
[    0.544915] pci 0000:03:00.0: supports D1
[    0.544915] pci 0000:03:00.0: supports D2
[    0.544915] PCI: bridge 0000:00:0d.0 32bit mmio: [f6000000, f60fffff]
[    0.544915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.544915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.544915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.544915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.592332] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.592640] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.592950] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.593252] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.593556] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.593859] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.594145] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.594145] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.594145] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.594145] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.594145] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.594145] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.594145] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.594180] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.594482] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.594785] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.595087] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.595393] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.595699] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.596166] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.600043] pnp: PnP ACPI init
[    0.600052] ACPI: bus type pnp registered
[    0.604430] pnp: PnP ACPI: found 12 devices
[    0.604433] ACPI: ACPI bus type pnp unregistered
[    0.604472] PCI: Using ACPI for IRQ routing
[    0.616042] NET: Registered protocol family 8
[    0.616044] NET: Registered protocol family 20
[    0.620041] NetLabel: Initializing
[    0.620041] NetLabel:  domain hash size = 128
[    0.620041] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.620057] NetLabel:  unlabeled traffic allowed by default
[    0.620151] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.620155] hpet0: 3 32-bit timers, 25000000 Hz
[    0.622781] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.622783]    actual entries 65586
[    0.622927] AppArmor: AppArmor Filesystem Enabled
[    0.622957] ACPI: RTC can wake from S4
[    0.624051] Switched to high resolution mode on CPU 0
[    0.624064] Switched to high resolution mode on CPU 1
[    0.629042] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.629050] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.629053] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.629056] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.629059] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.629062] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.629065] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.629073] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.629076] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.629089] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.629092] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.629095] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.629098] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.629102] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.634508] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.634510] pci 0000:00:08.0:   IO window: disabled
[    0.634515] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.634518] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.634522] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.634525] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.634528] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.634531] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.634535] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.634537] pci 0000:00:0d.0:   IO window: disabled
[    0.634540] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.634543] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.634553] pci 0000:00:08.0: setting latency timer to 64
[    0.634559] pci 0000:00:0c.0: setting latency timer to 64
[    0.634564] pci 0000:00:0d.0: setting latency timer to 64
[    0.634567] bus: 00 index 0 io port: [0, ffff]
[    0.634569] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.634571] bus: 02 index 0 mmio: [0, 0]
[    0.634573] bus: 02 index 1 mmio: [f6100000, f61fffff]
[    0.634575] bus: 02 index 2 mmio: [0, 0]
[    0.634577] bus: 02 index 3 io port: [0, ffff]
[    0.634580] bus: 02 index 4 mmio: [0, ffffffffffffffff]
[    0.634582] bus: 04 index 0 io port: [4000, 4fff]
[    0.634584] bus: 04 index 1 mmio: [f2000000, f3ffffff]
[    0.634586] bus: 04 index 2 mmio: [f0000000, f1ffffff]
[    0.634588] bus: 04 index 3 mmio: [0, 0]
[    0.634590] bus: 03 index 0 mmio: [0, 0]
[    0.634593] bus: 03 index 1 mmio: [f6000000, f60fffff]
[    0.634595] bus: 03 index 2 mmio: [0, 0]
[    0.634597] bus: 03 index 3 mmio: [0, 0]
[    0.634612] NET: Registered protocol family 2
[    0.677144] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.678210] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.680393] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.680953] TCP: Hash tables configured (established 262144 bind 65536)
[    0.680957] TCP reno registered
[    0.689120] NET: Registered protocol family 1
[    0.689257] checking if image is initramfs... it is
[    1.452546] Freeing initrd memory: 8442k freed
[    1.458016] Simple Boot Flag at 0x36 set to 0x1
[    1.459650] audit: initializing netlink socket (disabled)
[    1.459665] type=2000 audit(1228745830.456:1): initialized
[    1.465924] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.469428] VFS: Disk quotas dquot_6.5.1
[    1.469547] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.469677] msgmni has been set to 3763
[    1.469837] io scheduler noop registered
[    1.469840] io scheduler anticipatory registered
[    1.469842] io scheduler deadline registered
[    1.470021] io scheduler cfq registered (default)
[    1.470054] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.470219] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.470235] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.470251] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.470268] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.470283] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.470299] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.470314] pci 0000:00:12.0: Boot video device
[    1.470471] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.470494] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.470516] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.470588] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.470687] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.470709] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.470727] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.470791] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.523876] hpet_resources: 0xfed00000 is busy
[    1.523978] Linux agpgart interface v0.103
[    1.523983] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.527299] brd: module loaded
[    1.527403] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.527562] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.554265] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.554272] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.564216] mice: PS/2 mouse device common for all mice
[    1.564412] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.564449] rtc0: alarms up to one year, y3k, hpet irqs
[    1.564514] cpuidle: using governor ladder
[    1.564516] cpuidle: using governor menu
[    1.564927] TCP cubic registered
[    1.565258] registered taskstats version 1
[    1.565428]   Magic number: 4:840:282
[    1.565459] tty ttyvd: hash matches
[    1.565525] tty tty19: hash matches
[    1.565596] rtc_cmos 00:07: setting system clock to 2008-12-08 14:17:12 UTC (1228745832)
[    1.565599] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.565601] EDD information not available.
[    1.565657] Freeing unused kernel memory: 536k freed
[    1.565959] Write protecting the kernel read-only data: 4348k
[    1.592321] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.714157] fuse init (API version 7.9)
[    1.788214] ACPI: processor limited to max C-state 1
[    1.788395] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.788474] processor ACPI0007:00: registered as cooling_device0
[    1.788479] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.819679] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.819766] processor ACPI0007:01: registered as cooling_device1
[    1.819772] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.822595] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080609]
[    2.268822] usbcore: registered new interface driver usbfs
[    2.268862] usbcore: registered new interface driver hub
[    2.268926] usbcore: registered new device driver usb
[    2.269171] No dock devices found.
[    2.287883] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.288452] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    2.288464] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    2.288479] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.288482] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.288543] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.288570] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    2.288672] SCSI subsystem initialized
[    2.339326] libata version 3.00 loaded.
[    2.347252] usb usb1: configuration #1 chosen from 1 choice
[    2.347294] hub 1-0:1.0: USB hub found
[    2.347310] hub 1-0:1.0: 7 ports detected
[    2.552908] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    2.552916] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    2.552933] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    2.552936] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    2.552970] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    2.552987] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    2.610214] usb usb2: configuration #1 chosen from 1 choice
[    2.610249] hub 2-0:1.0: USB hub found
[    2.610260] hub 2-0:1.0: 2 ports detected
[    2.728067] usb 1-4: new low speed USB device using ohci_hcd and address 2
[    2.817062] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    2.817077] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    2.817093] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.817096] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.817129] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    2.817166] ehci_hcd 0000:00:02.1: debug port 1
[    2.817171] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.817193] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    2.916031] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.916221] usb usb3: configuration #1 chosen from 1 choice
[    2.916252] hub 3-0:1.0: USB hub found
[    2.916262] hub 3-0:1.0: 7 ports detected
[   27.060776] Clocksource tsc unstable (delta = 4398046077023 ns)
[   27.200443] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[   27.200450] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[   27.200466] ehci_hcd 0000:00:04.1: setting latency timer to 64
[   27.200469] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   27.200508] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[   27.200543] ehci_hcd 0000:00:04.1: debug port 1
[   27.200547] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[   27.200556] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[   27.494144] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.494314] usb usb4: configuration #1 chosen from 1 choice
[   27.494347] hub 4-0:1.0: USB hub found
[   27.494355] hub 4-0:1.0: 2 ports detected
[   27.494372] usb 1-4: device not accepting address 2, error -62
[   27.734422] hub 1-0:1.0: unable to enumerate USB device on port 4
[   27.859069] pata_amd 0000:00:06.0: version 0.3.10
[   27.859120] pata_amd 0000:00:06.0: setting latency timer to 64
[   27.859704] scsi0 : pata_amd
[   27.859840] scsi1 : pata_amd
[   27.860374] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   27.860377] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   28.046363] ata1.00: ATAPI: Optiarc DVD RW AD-7561A, GH09, max MWDMA2
[   28.046377] ata1: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[   28.109853] ata1.00: configured for MWDMA2
[   28.109922] ata2: port disabled. ignoring.
[   28.109967] isa bounce pool size: 16 pages
[   28.110919] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561A  GH09 PQ: 0 ANSI: 5
[   28.111203] ahci 0000:00:09.0: version 3.0
[   28.111721] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[   28.111733] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[   28.111828] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   28.111832] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   28.111836] ahci 0000:00:09.0: setting latency timer to 64
[   28.112188] scsi2 : ahci
[   28.112306] scsi3 : ahci
[   28.112393] scsi4 : ahci
[   28.112484] scsi5 : ahci
[   28.112611] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 2301
[   28.112614] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 2301
[   28.112617] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 2301
[   28.112620] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 2301
[   28.202405] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   28.372745] usb 4-2: configuration #1 chosen from 1 choice
[   29.063796] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.064188] ata3.00: ATA-8: WDC WD1200BEVS-60UST0, 01.01A01, max UDMA/100
[   29.064191] ata3.00: 234441648 sectors, multi 16: LBA48 
[   29.064655] ata3.00: configured for UDMA/100
[   29.164360] usb 1-4: new low speed USB device using ohci_hcd and address 4
[   29.609942] usb 1-4: configuration #1 chosen from 1 choice
[   31.002157] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   31.002560] ata4.00: ATA-8: WDC WD1200BEVS-60UST0, 01.01A01, max UDMA/100
[   31.002563] ata4.00: 234441648 sectors, multi 16: LBA48 
[   31.003027] ata4.00: configured for UDMA/100
[   31.489403] ata5: SATA link down (SStatus 0 SControl 300)
[   34.507306] ata6: SATA link down (SStatus 0 SControl 300)
[   34.507440] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
[   34.508257] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
[   34.508373] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   34.508921] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   34.508933] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[   34.508938] forcedeth 0000:00:0a.0: setting latency timer to 64
[   35.177308] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:cf:29:bd
[   35.177312] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   35.179456] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   35.179472] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[   35.231239] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   35.238920] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   35.238934] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   35.238942] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   35.287569] usbcore: registered new interface driver hiddev
[   35.294442] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0/input/input2
[   35.357264] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   35.376300] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   35.376349] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   35.376397] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   35.381237] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-4
[   35.381264] usbcore: registered new interface driver usbhid
[   35.381268] usbhid: v2.6:USB HID core driver
[   35.411815] Driver 'sd' needs updating - please use bus_type methods
[   35.411978] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   35.412026] sd 2:0:0:0: [sda] Write Protect is off
[   35.412029] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.412076] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.412175] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   35.412199] sd 2:0:0:0: [sda] Write Protect is off
[   35.412201] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.412245] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.412251]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   35.420688] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   35.420695] Uniform CD-ROM driver Revision: 3.20
[   35.420942] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   35.698089]  sda1 sda2 sda3
[   35.725825] sd 2:0:0:0: [sda] Attached SCSI disk
[   35.729771] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   35.729798] sd 3:0:0:0: [sdb] Write Protect is off
[   35.729801] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.729843] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.729956] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   35.729977] sd 3:0:0:0: [sdb] Write Protect is off
[   35.729980] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.730020] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.730024]  sdb: sdb1
[   35.996667] sd 3:0:0:0: [sdb] Attached SCSI disk
[   36.378542] PM: Starting manual resume from disk
[   36.378547] PM: Resume from partition 8:2
[   36.378549] PM: Checking hibernation image.
[   36.378751] PM: Resume from disk failed.
[   36.445777] kjournald starting.  Commit interval 5 seconds
[   36.445798] EXT3-fs: mounted filesystem with ordered data mode.
[   36.526661] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00a61f8200]
[   42.565065] udevd version 124 started
[   42.992651] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   43.021059] ACPI: Power Button (FF) [PWRF]
[   43.021210] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   43.037021] ACPI: Sleep Button (CM) [SLPB]
[   43.037142] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   43.037625] ACPI: Lid Switch [LID]
[   43.037747] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   43.069047] ACPI: Power Button (CM) [PWRB]
[   43.069926] ACPI: AC Adapter [ACAD] (on-line)
[   43.381620] ACPI: Battery Slot [BAT0] (battery present)
[   43.381938] ACPI: WMI: Mapper loaded
[   43.902785] acpi device:25: registered as cooling_device2
[   43.903023] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input7
[   43.933034] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   44.089726] ricoh-mmc: Ricoh MMC Controller disabling driver
[   44.089730] ricoh-mmc: Copyright(c) Philip Langdale
[   44.090736] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   44.090754] ricoh-mmc: Controller is now disabled.
[   44.153214] sdhci: Secure Digital Host Controller Interface driver
[   44.153219] sdhci: Copyright(c) Pierre Ossman
[   44.211513] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   44.212113] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   44.212126] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   44.215310] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   44.219910] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.274354] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.357185] Linux video capture interface: v2.00
[   44.468922] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b023)
[   44.471401] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb4/4-2/4-2:1.0/input/input8
[   44.505236] usbcore: registered new interface driver uvcvideo
[   44.505242] USB Video Class driver (v0.1.0)
[   44.515112] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   44.544816] ieee80211_crypt: registered algorithm 'NULL'
[   44.549891] wl: module license 'MIXED/Proprietary' taints kernel.
[   45.203468] b43-phy0: Broadcom 4311 WLAN found
[   45.248205] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   45.248220] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   45.248256] HDA Intel 0000:00:07.0: setting latency timer to 64
[   45.269859] phy0: Selected rate control algorithm 'pid'
[   45.362990] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   45.499562] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   45.578388] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   47.585793] lp: driver loaded but no devices found
[   47.851531] Adding 4096564k swap on /dev/sda2.  Priority:-1 extents:1 across:4096564k
[   48.413648] EXT3 FS on sda3, internal journal
[   49.517246] kjournald starting.  Commit interval 5 seconds
[   49.517550] EXT3 FS on sdb1, internal journal
[   49.517558] EXT3-fs: mounted filesystem with ordered data mode.
[   50.089120] type=1505 audit(1228763880.712:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4496
[   50.269205] type=1505 audit(1228763880.892:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4501
[   50.269454] type=1505 audit(1228763880.892:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4501
[   50.427356] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.437947] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[   51.438031] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x11
[   51.438035] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   51.438038] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[   51.438040] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   52.196672] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   52.453220] ppdev: user-space parallel port driver
[   55.505218] Bluetooth: Core ver 2.13
[   55.505571] NET: Registered protocol family 31
[   55.505578] Bluetooth: HCI device and connection manager initialized
[   55.505590] Bluetooth: HCI socket layer initialized
[   55.537647] Bluetooth: L2CAP ver 2.11
[   55.537673] Bluetooth: L2CAP socket layer initialized
[   55.568037] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   55.568055] Bluetooth: BNEP filters: protocol multicast
[   55.603613] Bridge firewalling registered
[   55.604390] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   55.635599] Bluetooth: RFCOMM socket layer initialized
[   55.635656] Bluetooth: RFCOMM TTY layer initialized
[   55.635660] Bluetooth: RFCOMM ver 1.10
[   55.650026] Bluetooth: SCO (Voice Link) ver 0.6
[   55.650048] Bluetooth: SCO socket layer initialized
[   59.909729] input: b43-phy0 as /devices/virtual/input/input11
[   60.012110] firmware: requesting b43/ucode13.fw
[   60.104591] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
[   60.104613] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   60.223963] input: b43-phy0 as /devices/virtual/input/input12
[   60.317081] firmware: requesting b43/ucode13.fw
[   60.325273] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
[   60.325301] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   60.497706] NET: Registered protocol family 17
[   86.011502] CPU0 attaching NULL sched-domain.
[   86.011542] CPU1 attaching NULL sched-domain.
[   86.041770] CPU0 attaching sched-domain:
[   86.041791]  domain 0: span 0-1 level CPU
[   86.041802]   groups: 0 1
[   86.041813]   domain 1: span 0-1 level NODE
[   86.041819]    groups: 0-1
[   86.041836] CPU1 attaching sched-domain:
[   86.041841]  domain 0: span 0-1 level CPU
[   86.041846]   groups: 1 0
[   86.041855]   domain 1: span 0-1 level NODE
[   86.041863]    groups: 0-1
[  104.068308] NET: Registered protocol family 10
[  104.069406] lo: Disabled Privacy Extensions
[  114.529021] eth0: no IPv6 routers present
[  155.566866] type=1503 audit(1228763986.187:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6122/net/" pid=6122 profile="/usr/sbin/cupsd"
[  156.642521] type=1503 audit(1228763987.263:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6126/net/" pid=6126 profile="/usr/sbin/cupsd"
[  156.647393] type=1503 audit(1228763987.267:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6126 profile="/usr/sbin/cupsd"
[  156.651355] type=1503 audit(1228763987.271:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6126 profile="/usr/sbin/cupsd"
[  156.655518] type=1503 audit(1228763987.275:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6126 profile="/usr/sbin/cupsd"
[  156.659603] type=1503 audit(1228763987.279:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6126 profile="/usr/sbin/cupsd"
[  156.663647] type=1503 audit(1228763987.283:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6126 profile="/usr/sbin/cupsd"
[  156.667850] type=1503 audit(1228763987.287:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6126 profile="/usr/sbin/cupsd"
[  156.671998] type=1503 audit(1228763987.291:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6126 profile="/usr/sbin/cupsd"
[  156.676048] type=1503 audit(1228763987.299:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6126 profile="/usr/sbin/cupsd"
[  201.681616] b43-phy1: Broadcom 4311 WLAN found
[  201.778607] phy1: Selected rate control algorithm 'pid'
[  205.880026] input: b43-phy1 as /devices/virtual/input/input13
[  205.981076] firmware: requesting b43/ucode13.fw
[  205.989164] b43-phy1 ERROR: Firmware file "b43/ucode13.fw" not found
[  205.989193] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  206.086004] input: b43-phy1 as /devices/virtual/input/input14
[  206.180289] firmware: requesting b43/ucode13.fw
[  206.188158] b43-phy1 ERROR: Firmware file "b43/ucode13.fw" not found
[  206.188181] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).

```

---

### Post by jfbilodeau on 2008-12-11
Bump and more details...

I've upgraded to 2.6.27-10, and I still have the same oddity.

When Ubuntu boots, the orange slider starts to move to the right, but stops about a quarter of the way there. Pressing CTRL+ALT+F1 to switch to the 
console shows me the message 'Aperture beyond 4G Ignoring'

That's strange, since I only have 2G of RAM. However, the kernel seems to hang there. But if I press a key, it displays the next boot message, and hangs. Again, pressing a key will allow the kernel to continue booting. Everytime a message is displayed, the kernel seems to wait for a key press. There is no prompts or messages indicating that I should press a key.

This happens until it gets to the /etc/init.d scripts, then the machine boots normally and works normally.

Does anyone have any insights into why that's happening, or how I could go ahead and trouble shoot that?

BTW: I know that this is no longer really an installation issue, but I'm not sure how to move the thread.

Thanks,

J-F

---

### Post by Ayuthia on 2008-12-11
EDIT: Please read post 4.  I forgot about that workaround.

I am curious if the firmware error messages are causing any problems.  Are you using the b43 drivers?  If you have no idea about what I am talking about, it is the driver for your wireless.  Do you know if you are using b43 or Broadcom STA (or not using your wireless)?  I was thinking that you might try blacklisting the b43 driver and see if it makes a difference:

```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
```

If you are currently not using your wireless and have not done it yet, just go into System->Administration->Hardware Drivers.

---

### Post by iponeverything on 2008-12-11
Appears to be a known bug adding:

```
hpet=disable

```
to your boot options is a workaround

see thread:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/272247)

---

### Post by jfbilodeau on 2008-12-11
> **iponeverything said:**
> Appears to be a known bug adding:

```
hpet=disable

```
to your boot options is a workaround

see thread:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/272247)
Thank,

That's exactly my problem. Even my machine make is listed in the bug details. HP Pavilion has got to be the machine that caused me the most grief with Ubuntu :(.

J-F

---

