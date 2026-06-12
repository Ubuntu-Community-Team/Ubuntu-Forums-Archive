---
title: "Stopping gnome produces blank screen and system hang on Jaunty 9.04"
date: 2009-05-07
forum: Hardware
---

### Post by Dr. Feelgood on 2009-05-07
I'm almost about fed up with Jaunty and its bugs, but in a last honest effort I'm going to try and get this working 100%.  My laptop (Compaq Presario 700) won't shut down.  All that happens when I use the shutdown option is the computer starts to shut down but then goes to a blank screen, no splash, no cursor, and it freezes.  I have to hard reset manually.  I had read that the wireless card might be the culprit so i tried:
```

sudo ifconfig wlan0 down
sudo ifconfig eth0 down
sudo ifconfig eth1 down

```
... but to no avail.  I also tried vga=791 or apci=off in grub with no results.  Also of note is that removing splash and quiet will show the messages on startup but with no effect on the shutdown.  I've also tried:
```

sudo modprobe -r 8139too
sudo modprobe -r 8139cp
sudo modprobe -r orinoco_cs

```
... also with no results.  Finally I pulled the wireless card out completely... with no results.  Just the same problem over and over again.

I had temporarily given up and started to try and fix another damn Juanty problem, my screen resolution when I noticed that stopping X...
```

sudo /etc/init.d/gdm stop 

```
... reproduced my problemm a blank screen and a frozen system.  What the hell is going on here and how what message logs do I have to look at to see what is happening?

---

### Post by Dr. Feelgood on 2009-05-07
here is the last entry of /var/log/messages:
```

May  7 01:40:03 tashtego syslogd 1.5.0#5ubuntu3: restart.
May  7 01:40:03 tashtego kernel: Inspecting /boot/System.map-2.6.28-11-generic
May  7 01:40:03 tashtego kernel: Cannot find map file.
May  7 01:40:03 tashtego kernel: Loaded 54398 symbols from 56 modules.
May  7 01:40:03 tashtego kernel: [    0.000000] BIOS EBDA/lowmem at: 0009e800/0009e800
May  7 01:40:03 tashtego kernel: [    0.000000] Initializing cgroup subsys cpuset
May  7 01:40:03 tashtego kernel: [    0.000000] Initializing cgroup subsys cpu
May  7 01:40:03 tashtego kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
May  7 01:40:03 tashtego kernel: [    0.000000] KERNEL supported cpus:
May  7 01:40:03 tashtego kernel: [    0.000000]   Intel GenuineIntel
May  7 01:40:03 tashtego kernel: [    0.000000]   AMD AuthenticAMD
May  7 01:40:03 tashtego kernel: [    0.000000]   NSC Geode by NSC
May  7 01:40:03 tashtego kernel: [    0.000000]   Cyrix CyrixInstead
May  7 01:40:03 tashtego kernel: [    0.000000]   Centaur CentaurHauls
May  7 01:40:03 tashtego kernel: [    0.000000]   Transmeta GenuineTMx86
May  7 01:40:03 tashtego kernel: [    0.000000]   Transmeta TransmetaCPU
May  7 01:40:03 tashtego kernel: [    0.000000]   UMC UMC UMC UMC
May  7 01:40:03 tashtego kernel: [    0.000000] BIOS-provided physical RAM map:
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000def0000 (usable)
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 000000000def0000 - 000000000deff000 (ACPI data)
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 000000000deff000 - 000000000df00000 (ACPI NVS)
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 000000000df00000 - 000000000e000000 (usable)
May  7 01:40:03 tashtego kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000] DMI 2.3 present.
May  7 01:40:03 tashtego kernel: [    0.000000] last_pfn = 0xe000 max_arch_pfn = 0x100000
May  7 01:40:03 tashtego kernel: [    0.000000] Scanning 2 areas for low memory corruption
May  7 01:40:03 tashtego kernel: [    0.000000] modified physical RAM map:
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 0000000000010000 - 0000000000091800 (usable)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 00000000000c0000 - 00000000000cc000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 0000000000100000 - 000000000def0000 (usable)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 000000000def0000 - 000000000deff000 (ACPI data)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 000000000deff000 - 000000000df00000 (ACPI NVS)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 000000000df00000 - 000000000e000000 (usable)
May  7 01:40:03 tashtego kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
May  7 01:40:03 tashtego kernel: [    0.000000] RAMDISK: 0d7ae000 - 0dedfd86
May  7 01:40:03 tashtego kernel: [    0.000000] ACPI: RSDP 000F6DC0, 0014 (r0 PTLTD )
May  7 01:40:03 tashtego kernel: [    0.000000] ACPI: RSDT 0DEFB61A, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
May  7 01:40:03 tashtego kernel: [    0.000000] ACPI: FACP 0DEFEE95, 0074 (r1 COMPAQ  EAGLES   6040000 PTL_    F4240)
May  7 01:40:03 tashtego kernel: [    0.000000] ACPI: DSDT 0DEFB646, 384F (r1 COMAPQ   EAGLES  6040000 MSFT  100000D)
May  7 01:40:03 tashtego kernel: [    0.000000] ACPI: FACS 0DEFFFC0, 0040
May  7 01:40:03 tashtego kernel: [    0.000000] ACPI: SSDT 0DEFEF09, 00F7 (r1 PTLTD  POWERNOW  6040000  LTP        1)
May  7 01:40:03 tashtego kernel: [    0.000000] 0MB HIGHMEM available.
May  7 01:40:03 tashtego kernel: [    0.000000] 224MB LOWMEM available.
May  7 01:40:03 tashtego kernel: [    0.000000]   mapped low ram: 0 - 0e000000
May  7 01:40:03 tashtego kernel: [    0.000000]   low ram: 00000000 - 0e000000
May  7 01:40:03 tashtego kernel: [    0.000000]   bootmap 00011000 - 00012c00
May  7 01:40:03 tashtego kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000e000000]
May  7 01:40:03 tashtego kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  7 01:40:03 tashtego kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  7 01:40:03 tashtego kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  7 01:40:03 tashtego kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
May  7 01:40:03 tashtego kernel: [    0.000000]   #4 [000d7ae000 - 000dedfd86]          RAMDISK ==> [000d7ae000 - 000dedfd86]
May  7 01:40:03 tashtego kernel: [    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
May  7 01:40:03 tashtego kernel: [    0.000000]   #6 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
May  7 01:40:03 tashtego kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
May  7 01:40:03 tashtego kernel: [    0.000000]   #8 [0000011000 - 0000013000]          BOOTMAP ==> [0000011000 - 0000013000]
May  7 01:40:03 tashtego kernel: [    0.000000] Zone PFN ranges:
May  7 01:40:03 tashtego kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  7 01:40:03 tashtego kernel: [    0.000000]   Normal   0x00001000 -> 0x0000e000
May  7 01:40:03 tashtego kernel: [    0.000000]   HighMem  0x0000e000 -> 0x0000e000
May  7 01:40:03 tashtego kernel: [    0.000000] Movable zone start PFN for each node
May  7 01:40:03 tashtego kernel: [    0.000000] early_node_map[5] active PFN ranges
May  7 01:40:03 tashtego kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
May  7 01:40:03 tashtego kernel: [    0.000000]     0: 0x00000006 -> 0x00000007
May  7 01:40:03 tashtego kernel: [    0.000000]     0: 0x00000010 -> 0x00000091
May  7 01:40:03 tashtego kernel: [    0.000000]     0: 0x00000100 -> 0x0000def0
May  7 01:40:03 tashtego kernel: [    0.000000]     0: 0x0000df00 -> 0x0000e000
May  7 01:40:03 tashtego kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
May  7 01:40:03 tashtego kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  7 01:40:03 tashtego kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009f000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000c0000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000c0000 - 00000000000cc000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000cc000 - 00000000000dc000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000def0000 - 000000000deff000
May  7 01:40:03 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000deff000 - 000000000df00000
May  7 01:40:03 tashtego kernel: [    0.000000] Allocating PCI resources starting at 10000000 (gap: e000000:f1f80000)
May  7 01:40:03 tashtego kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
May  7 01:40:03 tashtego kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 56756
May  7 01:40:03 tashtego kernel: [    0.000000] Kernel command line: root=UUID=e942c0c6-6128-4828-bbc0-deaf85ed604d ro xforcevesa quiet splash 
May  7 01:40:03 tashtego kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  7 01:40:03 tashtego kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  7 01:40:03 tashtego kernel: [    0.000000] Initializing CPU#0
May  7 01:40:03 tashtego kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
May  7 01:40:03 tashtego kernel: [    0.000000] Fast TSC calibration using PIT
May  7 01:40:03 tashtego kernel: [    0.000000] Detected 1195.862 MHz processor.
May  7 01:40:03 tashtego kernel: [    0.004000] Console: colour VGA+ 80x25
May  7 01:40:03 tashtego kernel: [    0.004000] console [tty0] enabled
May  7 01:40:03 tashtego kernel: [    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
May  7 01:40:03 tashtego kernel: [    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
May  7 01:40:03 tashtego kernel: [    0.004000] allocated 1146880 bytes of page_cgroup
May  7 01:40:03 tashtego kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
May  7 01:40:03 tashtego kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
May  7 01:40:03 tashtego kernel: [    0.004000] Memory: 210280k/229376k available (4126k kernel code, 18256k reserved, 2208k data, 532k init, 0k highmem)
May  7 01:40:03 tashtego kernel: [    0.004000] virtual kernel memory layout:
May  7 01:40:03 tashtego kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
May  7 01:40:03 tashtego kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
May  7 01:40:03 tashtego kernel: [    0.004000]     vmalloc : 0xce800000 - 0xff3fe000   ( 779 MB)
May  7 01:40:03 tashtego kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xce000000   ( 224 MB)
May  7 01:40:03 tashtego kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
May  7 01:40:03 tashtego kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
May  7 01:40:03 tashtego kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
May  7 01:40:03 tashtego kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  7 01:40:03 tashtego kernel: [    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  7 01:40:03 tashtego kernel: [    0.004024] Calibrating delay loop (skipped), value calculated using timer frequency.. 2391.72 BogoMIPS (lpj=4783448)
May  7 01:40:03 tashtego kernel: [    0.004067] Security Framework initialized
May  7 01:40:03 tashtego kernel: [    0.004085] SELinux:  Disabled at boot.
May  7 01:40:03 tashtego kernel: [    0.004146] AppArmor: AppArmor initialized
May  7 01:40:03 tashtego kernel: [    0.004165] Mount-cache hash table entries: 512
May  7 01:40:03 tashtego kernel: [    0.004478] Initializing cgroup subsys ns
May  7 01:40:03 tashtego kernel: [    0.004487] Initializing cgroup subsys cpuacct
May  7 01:40:03 tashtego kernel: [    0.004492] Initializing cgroup subsys memory
May  7 01:40:03 tashtego kernel: [    0.004501] Initializing cgroup subsys freezer
May  7 01:40:03 tashtego kernel: [    0.004528] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  7 01:40:03 tashtego kernel: [    0.004534] CPU: L2 Cache: 256K (64 bytes/line)
May  7 01:40:03 tashtego kernel: [    0.004570] Checking 'hlt' instruction... OK.
May  7 01:40:03 tashtego kernel: [    0.020876] SMP alternatives: switching to UP code
May  7 01:40:03 tashtego kernel: [    0.276863] Freeing SMP alternatives: 18k freed
May  7 01:40:03 tashtego kernel: [    0.276876] ACPI: Core revision 20080926
May  7 01:40:03 tashtego kernel: [    0.280414] ACPI: Checking initramfs for custom DSDT
May  7 01:40:03 tashtego kernel: [    0.770119] ACPI: setting ELCR to 0400 (from 0a30)
May  7 01:40:03 tashtego kernel: [    0.772159] weird, boot CPU (#0) not listedby the BIOS.
May  7 01:40:03 tashtego kernel: [    0.772164] SMP motherboard not detected.
May  7 01:40:03 tashtego kernel: [    0.772170] Local APIC not detected. Using dummy APIC emulation.
May  7 01:40:03 tashtego kernel: [    0.772174] SMP disabled
May  7 01:40:03 tashtego kernel: [    0.772889] Brought up 1 CPUs
May  7 01:40:03 tashtego kernel: [    0.772895] Total of 1 processors activated (2391.72 BogoMIPS).
May  7 01:40:03 tashtego kernel: [    0.776865] net_namespace: 776 bytes
May  7 01:40:03 tashtego kernel: [    0.776891] Booting paravirtualized kernel on bare hardware
May  7 01:40:03 tashtego kernel: [    0.777370] Time:  1:39:40  Date: 05/07/09
May  7 01:40:03 tashtego kernel: [    0.777384] regulator: core version 0.5
May  7 01:40:03 tashtego kernel: [    0.777487] NET: Registered protocol family 16
May  7 01:40:03 tashtego kernel: [    0.777783] EISA bus registered
May  7 01:40:03 tashtego kernel: [    0.777819] ACPI: bus type pci registered
May  7 01:40:03 tashtego kernel: [    0.778249] PCI: PCI BIOS revision 2.10 entry at 0xfd7ae, last bus=1
May  7 01:40:03 tashtego kernel: [    0.778255] PCI: Using configuration type 1 for base access
May  7 01:40:03 tashtego kernel: [    0.785917] ACPI: Interpreter enabled
May  7 01:40:03 tashtego kernel: [    0.785924] ACPI: (supports S0 S3 S4 S5)
May  7 01:40:03 tashtego kernel: [    0.785951] ACPI: Using PIC for interrupt routing
May  7 01:40:03 tashtego kernel: [    0.786594] ACPI: EC: non-query interrupt received, switching to interrupt mode
May  7 01:40:03 tashtego kernel: [    0.792588] ACPI: EC: GPE = 0x6, I/O: command/status = 0x66, data = 0x62
May  7 01:40:03 tashtego kernel: [    0.792593] ACPI: EC: driver started in interrupt mode
May  7 01:40:03 tashtego kernel: [    0.792747] ACPI: No dock devices found.
May  7 01:40:03 tashtego kernel: [    0.792766] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  7 01:40:03 tashtego kernel: [    0.792882] pci 0000:00:00.0: Disabling VIA memory write queue (PCI ID 0305, rev 80): [55] 3c & 1f -> 1c
May  7 01:40:03 tashtego kernel: [    0.793177] pci 0000:00:07.4: quirk: region 8100-810f claimed by vt82c686 SMB
May  7 01:40:03 tashtego kernel: [    0.793325] pci 0000:00:09.0: PME# supported from D3hot
May  7 01:40:03 tashtego kernel: [    0.793331] pci 0000:00:09.0: PME# disabled
May  7 01:40:03 tashtego kernel: [    0.793379] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
May  7 01:40:03 tashtego kernel: [    0.793384] pci 0000:00:0a.0: PME# disabled
May  7 01:40:03 tashtego kernel: [    0.793455] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
May  7 01:40:03 tashtego kernel: [    0.793461] pci 0000:00:0b.0: PME# disabled
May  7 01:40:03 tashtego kernel: [    0.797860] ACPI: PCI Interrupt Link [LNKA] (IRQs *4)
May  7 01:40:03 tashtego kernel: [    0.798108] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
May  7 01:40:03 tashtego kernel: [    0.798346] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
May  7 01:40:03 tashtego kernel: [    0.798597] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
May  7 01:40:03 tashtego kernel: [    0.798817] ACPI: WMI: Mapper loaded
May  7 01:40:03 tashtego kernel: [    0.799358] SCSI subsystem initialized
May  7 01:40:03 tashtego kernel: [    0.799626] usbcore: registered new interface driver usbfs
May  7 01:40:03 tashtego kernel: [    0.799665] usbcore: registered new interface driver hub
May  7 01:40:03 tashtego kernel: [    0.799731] usbcore: registered new device driver usb
May  7 01:40:03 tashtego kernel: [    0.799988] PCI: Using ACPI for IRQ routing
May  7 01:40:03 tashtego kernel: [    0.800177] Bluetooth: Core ver 2.13
May  7 01:40:03 tashtego kernel: [    0.800177] NET: Registered protocol family 31
May  7 01:40:03 tashtego kernel: [    0.800177] Bluetooth: HCI device and connection manager initialized
May  7 01:40:03 tashtego kernel: [    0.800177] Bluetooth: HCI socket layer initialized
May  7 01:40:03 tashtego kernel: [    0.800177] NET: Registered protocol family 8
May  7 01:40:03 tashtego kernel: [    0.800177] NET: Registered protocol family 20
May  7 01:40:03 tashtego kernel: [    0.800180] NetLabel: Initializing
May  7 01:40:03 tashtego kernel: [    0.800184] NetLabel:  domain hash size = 128
May  7 01:40:03 tashtego kernel: [    0.800186] NetLabel:  protocols = UNLABELED CIPSOv4
May  7 01:40:03 tashtego kernel: [    0.800221] NetLabel:  unlabeled traffic allowed by default
May  7 01:40:03 tashtego kernel: [    0.800445] AppArmor: AppArmor Filesystem Enabled
May  7 01:40:03 tashtego kernel: [    0.800463] pnp: PnP ACPI init
May  7 01:40:03 tashtego kernel: [    0.800463] ACPI: bus type pnp registered
May  7 01:40:03 tashtego kernel: [    0.805175] pnp: PnP ACPI: found 11 devices
May  7 01:40:03 tashtego kernel: [    0.805179] ACPI: ACPI bus type pnp unregistered
May  7 01:40:03 tashtego kernel: [    0.805187] PnPBIOS: Disabled by ACPI PNP
May  7 01:40:03 tashtego kernel: [    0.805211] system 00:05: iomem range 0x0-0x9ffff could not be reserved
May  7 01:40:03 tashtego kernel: [    0.805217] system 00:05: iomem range 0xdc000-0xdffff could not be reserved
May  7 01:40:03 tashtego kernel: [    0.805223] system 00:05: iomem range 0x7000000-0x7ffffff could not be reserved
May  7 01:40:03 tashtego kernel: [    0.805233] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
May  7 01:40:03 tashtego kernel: [    0.840109] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
May  7 01:40:03 tashtego kernel: [    0.840114] pci 0000:00:01.0:   IO window: disabled
May  7 01:40:03 tashtego kernel: [    0.840122] pci 0000:00:01.0:   MEM window: 0xe8100000-0xe81fffff
May  7 01:40:03 tashtego kernel: [    0.840128] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
May  7 01:40:03 tashtego kernel: [    0.840136] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
May  7 01:40:03 tashtego kernel: [    0.840141] pci 0000:00:0a.0:   IO window: 0x001c00-0x001cff
May  7 01:40:03 tashtego kernel: [    0.840147] pci 0000:00:0a.0:   IO window: 0x002000-0x0020ff
May  7 01:40:03 tashtego kernel: [    0.840153] pci 0000:00:0a.0:   PREFETCH window: 0x10000000-0x13ffffff
May  7 01:40:03 tashtego kernel: [    0.840159] pci 0000:00:0a.0:   MEM window: 0x14000000-0x17ffffff
May  7 01:40:03 tashtego kernel: [    0.840260] pci 0000:00:0a.0: power state changed by ACPI to D0
May  7 01:40:03 tashtego kernel: [    0.840654] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
May  7 01:40:03 tashtego kernel: [    0.840670] pci 0000:00:0a.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
May  7 01:40:03 tashtego kernel: [    0.840680] bus: 00 index 0 io port: [0x00-0xffff]
May  7 01:40:03 tashtego kernel: [    0.840684] bus: 00 index 1 mmio: [0x000000-0xffffffff]
May  7 01:40:03 tashtego kernel: [    0.840687] bus: 01 index 0 mmio: [0x0-0x0]
May  7 01:40:03 tashtego kernel: [    0.840691] bus: 01 index 1 mmio: [0xe8100000-0xe81fffff]
May  7 01:40:03 tashtego kernel: [    0.840694] bus: 01 index 2 mmio: [0xf0000000-0xf7ffffff]
May  7 01:40:03 tashtego kernel: [    0.840698] bus: 01 index 3 mmio: [0x0-0x0]
May  7 01:40:03 tashtego kernel: [    0.840702] bus: 02 index 0 io port: [0x1c00-0x1cff]
May  7 01:40:03 tashtego kernel: [    0.840705] bus: 02 index 1 io port: [0x2000-0x20ff]
May  7 01:40:03 tashtego kernel: [    0.840709] bus: 02 index 2 mmio: [0x10000000-0x13ffffff]
May  7 01:40:03 tashtego kernel: [    0.840713] bus: 02 index 3 mmio: [0x14000000-0x17ffffff]
May  7 01:40:03 tashtego kernel: [    0.840744] NET: Registered protocol family 2
May  7 01:40:03 tashtego kernel: [    0.840994] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
May  7 01:40:03 tashtego kernel: [    0.841524] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
May  7 01:40:03 tashtego kernel: [    0.841754] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
May  7 01:40:03 tashtego kernel: [    0.841964] TCP: Hash tables configured (established 8192 bind 8192)
May  7 01:40:03 tashtego kernel: [    0.841970] TCP reno registered
May  7 01:40:03 tashtego kernel: [    0.842114] NET: Registered protocol family 1
May  7 01:40:03 tashtego kernel: [    0.842415] checking if image is initramfs... it is
May  7 01:40:03 tashtego kernel: [    1.945672] Freeing initrd memory: 7367k freed
May  7 01:40:03 tashtego kernel: [    1.945949] cpufreq: No nForce2 chipset.
May  7 01:40:03 tashtego kernel: [    1.946272] audit: initializing netlink socket (disabled)
May  7 01:40:03 tashtego kernel: [    1.946330] type=2000 audit(1241660379.944:1): initialized
May  7 01:40:03 tashtego kernel: [    1.959528] HugeTLB registered 4 MB page size, pre-allocated 0 pages
May  7 01:40:03 tashtego kernel: [    1.961959] VFS: Disk quotas dquot_6.5.1
May  7 01:40:03 tashtego kernel: [    1.962069] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  7 01:40:03 tashtego kernel: [    1.963228] fuse init (API version 7.10)
May  7 01:40:03 tashtego kernel: [    1.963398] msgmni has been set to 425
May  7 01:40:03 tashtego kernel: [    1.963844] alg: No test for stdrng (krng)
May  7 01:40:03 tashtego kernel: [    1.963872] io scheduler noop registered
May  7 01:40:03 tashtego kernel: [    1.963876] io scheduler anticipatory registered
May  7 01:40:03 tashtego kernel: [    1.963879] io scheduler deadline registered
May  7 01:40:03 tashtego kernel: [    1.963911] io scheduler cfq registered (default)
May  7 01:40:03 tashtego kernel: [    1.963955] pci 0000:00:00.0: Applying VIA southbridge workaround
May  7 01:40:03 tashtego kernel: [    1.963963] PCI: VIA PCI bridge detected.Disabling DAC.
May  7 01:40:03 tashtego kernel: [    1.963971] pci 0000:00:07.0: Disabling VIA external APIC routing
May  7 01:40:03 tashtego kernel: [    1.969238] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  7 01:40:03 tashtego kernel: [    1.969258] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  7 01:40:03 tashtego kernel: [    1.969977] ACPI: AC Adapter [AC] (on-line)
May  7 01:40:03 tashtego kernel: [    1.982411] ACPI: Battery Slot [BAT0] (battery present)
May  7 01:40:03 tashtego kernel: [    1.982574] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
May  7 01:40:03 tashtego kernel: [    1.982580] ACPI: Power Button (FF) [PWRF]
May  7 01:40:03 tashtego kernel: [    1.982663] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
May  7 01:40:03 tashtego kernel: [    1.982673] ACPI: Sleep Button (CM) [SLPB]
May  7 01:40:03 tashtego kernel: [    1.982750] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
May  7 01:40:03 tashtego kernel: [    1.982757] ACPI: Power Button (CM) [PWRB]
May  7 01:40:03 tashtego kernel: [    1.982847] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
May  7 01:40:03 tashtego kernel: [    1.988833] ACPI: Lid Switch [LID]
May  7 01:40:03 tashtego kernel: [    1.989129] ACPI: CPU0 (power states: C1[C1] C2[C2])
May  7 01:40:03 tashtego kernel: [    1.989179] processor ACPI_CPU:00: registered as cooling_device0
May  7 01:40:03 tashtego kernel: [    1.989186] ACPI: Processor [CPU0] (supports 16 throttling states)
May  7 01:40:03 tashtego kernel: [    1.992061] isapnp: Scanning for PnP cards...
May  7 01:40:03 tashtego kernel: [    2.346324] isapnp: No Plug & Play device found
May  7 01:40:03 tashtego kernel: [    2.348680] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  7 01:40:03 tashtego kernel: [    2.350608] brd: module loaded
May  7 01:40:03 tashtego kernel: [    2.351256] loop: module loaded
May  7 01:40:03 tashtego kernel: [    2.351494] Fixed MDIO Bus: probed
May  7 01:40:03 tashtego kernel: [    2.351508] PPP generic driver version 2.4.2
May  7 01:40:03 tashtego kernel: [    2.351644] input: Macintosh mouse button emulation as /devices/virtual/input/input4
May  7 01:40:03 tashtego kernel: [    2.351715] Driver 'sd' needs updating - please use bus_type methods
May  7 01:40:03 tashtego kernel: [    2.351735] Driver 'sr' needs updating - please use bus_type methods
May  7 01:40:03 tashtego kernel: [    2.353244] scsi0 : pata_via
May  7 01:40:03 tashtego kernel: [    2.353506] scsi1 : pata_via
May  7 01:40:03 tashtego kernel: [    2.354768] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1840 irq 14
May  7 01:40:03 tashtego kernel: [    2.354774] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1848 irq 15
May  7 01:40:03 tashtego kernel: [    2.516543] ata1.00: ATA-5: HITACHI_DK23CA-20, 00H1A0J1, max UDMA/100
May  7 01:40:03 tashtego kernel: [    2.516549] ata1.00: 39070080 sectors, multi 16: LBA 
May  7 01:40:03 tashtego kernel: [    2.532528] ata1.00: configured for UDMA/100
May  7 01:40:03 tashtego kernel: [    2.696435] ata2.00: ATAPI: SD-R2102, 1A15, max MWDMA2
May  7 01:40:03 tashtego kernel: [    2.712455] ata2.00: configured for MWDMA2
May  7 01:40:03 tashtego kernel: [    2.713415] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23CA-2 00H1 PQ: 0 ANSI: 5
May  7 01:40:03 tashtego kernel: [    2.713649] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
May  7 01:40:03 tashtego kernel: [    2.713690] sd 0:0:0:0: [sda] Write Protect is off
May  7 01:40:03 tashtego kernel: [    2.713752] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  7 01:40:03 tashtego kernel: [    2.713932] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
May  7 01:40:03 tashtego kernel: [    2.713963] sd 0:0:0:0: [sda] Write Protect is off
May  7 01:40:03 tashtego kernel: [    2.714020] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  7 01:40:03 tashtego kernel: [    2.714030]  sda: sda1 sda2 < sda5 sda6 >
May  7 01:40:03 tashtego kernel: [    2.742456] sd 0:0:0:0: [sda] Attached SCSI disk
May  7 01:40:03 tashtego kernel: [    2.742583] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  7 01:40:03 tashtego kernel: [    2.745075] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2102 1A15 PQ: 0 ANSI: 5
May  7 01:40:03 tashtego kernel: [    2.751811] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
May  7 01:40:03 tashtego kernel: [    2.751819] Uniform CD-ROM driver Revision: 3.20
May  7 01:40:03 tashtego kernel: [    2.752143] sr 1:0:0:0: Attached scsi generic sg1 type 5
May  7 01:40:03 tashtego kernel: [    2.752466] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  7 01:40:03 tashtego kernel: [    2.752499] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  7 01:40:03 tashtego kernel: [    2.752521] uhci_hcd: USB Universal Host Controller Interface driver
May  7 01:40:03 tashtego kernel: [    2.753135] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
May  7 01:40:03 tashtego kernel: [    2.753153] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
May  7 01:40:03 tashtego kernel: [    2.753173] uhci_hcd 0000:00:07.2: UHCI Host Controller
May  7 01:40:03 tashtego kernel: [    2.753342] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
May  7 01:40:03 tashtego kernel: [    2.753386] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001800
May  7 01:40:03 tashtego kernel: [    2.753603] usb usb1: configuration #1 chosen from 1 choice
May  7 01:40:03 tashtego kernel: [    2.753658] hub 1-0:1.0: USB hub found
May  7 01:40:03 tashtego kernel: [    2.753686] hub 1-0:1.0: 2 ports detected
May  7 01:40:03 tashtego kernel: [    2.753947] usbcore: registered new interface driver libusual
May  7 01:40:03 tashtego kernel: [    2.754017] usbcore: registered new interface driver usbserial
May  7 01:40:03 tashtego kernel: [    2.754038] USB Serial support registered for generic
May  7 01:40:03 tashtego kernel: [    2.754060] usbcore: registered new interface driver usbserial_generic
May  7 01:40:03 tashtego kernel: [    2.754064] usbserial: USB Serial Driver core
May  7 01:40:03 tashtego kernel: [    2.754152] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May  7 01:40:03 tashtego kernel: [    2.756131] serio: i8042 KBD port at 0x60,0x64 irq 1
May  7 01:40:03 tashtego kernel: [    2.756144] serio: i8042 AUX port at 0x60,0x64 irq 12
May  7 01:40:03 tashtego kernel: [    2.756368] mice: PS/2 mouse device common for all mice
May  7 01:40:03 tashtego kernel: [    2.756769] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
May  7 01:40:03 tashtego kernel: [    2.756801] rtc0: alarms up to one year, y3k, 242 bytes nvram
May  7 01:40:03 tashtego kernel: [    2.756953] device-mapper: uevent: version 1.0.3
May  7 01:40:03 tashtego kernel: [    2.757181] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
May  7 01:40:03 tashtego kernel: [    2.757307] device-mapper: multipath: version 1.0.5 loaded
May  7 01:40:03 tashtego kernel: [    2.757313] device-mapper: multipath round-robin: version 1.0.0 loaded
May  7 01:40:03 tashtego kernel: [    2.757480] EISA: Probing bus 0 at eisa.0
May  7 01:40:03 tashtego kernel: [    2.757494] Cannot allocate resource for EISA slot 1
May  7 01:40:03 tashtego kernel: [    2.757499] Cannot allocate resource for EISA slot 2
May  7 01:40:03 tashtego kernel: [    2.757528] Cannot allocate resource for EISA slot 8
May  7 01:40:03 tashtego kernel: [    2.757532] EISA: Detected 0 cards.
May  7 01:40:03 tashtego kernel: [    2.757642] cpuidle: using governor ladder
May  7 01:40:03 tashtego kernel: [    2.757719] cpuidle: using governor menu
May  7 01:40:03 tashtego kernel: [    2.758670] TCP cubic registered
May  7 01:40:03 tashtego kernel: [    2.758846] NET: Registered protocol family 10
May  7 01:40:03 tashtego kernel: [    2.759632] lo: Disabled Privacy Extensions
May  7 01:40:03 tashtego kernel: [    2.760310] NET: Registered protocol family 17
May  7 01:40:03 tashtego kernel: [    2.760353] Bluetooth: L2CAP ver 2.11
May  7 01:40:03 tashtego kernel: [    2.760356] Bluetooth: L2CAP socket layer initialized
May  7 01:40:03 tashtego kernel: [    2.760362] Bluetooth: SCO (Voice Link) ver 0.6
May  7 01:40:03 tashtego kernel: [    2.760366] Bluetooth: SCO socket layer initialized
May  7 01:40:03 tashtego kernel: [    2.760459] Bluetooth: RFCOMM socket layer initialized
May  7 01:40:03 tashtego kernel: [    2.760481] Bluetooth: RFCOMM TTY layer initialized
May  7 01:40:03 tashtego kernel: [    2.760485] Bluetooth: RFCOMM ver 1.10
May  7 01:40:03 tashtego kernel: [    2.760530] powernow-k8: Processor cpuid 662 not supported
May  7 01:40:03 tashtego kernel: [    2.760651] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
May  7 01:40:03 tashtego kernel: [    2.768179] powernow: No PST tables match this cpuid (0x762)
May  7 01:40:03 tashtego kernel: [    2.768183] powernow: This is indicative of a broken BIOS.
May  7 01:40:03 tashtego kernel: [    2.768186] powernow: Trying ACPI perflib
May  7 01:40:03 tashtego kernel: [    2.768226] powernow: Minimum speed 498 MHz. Maximum speed 1195 MHz.
May  7 01:40:03 tashtego kernel: [    2.768495] Using IPI No-Shortcut mode
May  7 01:40:03 tashtego kernel: [    2.768745] registered taskstats version 1
May  7 01:40:03 tashtego kernel: [    2.768931]   Magic number: 9:752:659
May  7 01:40:03 tashtego kernel: [    2.768978] block ram12: hash matches
May  7 01:40:03 tashtego kernel: [    2.769144] rtc_cmos 00:02: setting system clock to 2009-05-07 01:39:42 UTC (1241660382)
May  7 01:40:03 tashtego kernel: [    2.769150] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  7 01:40:03 tashtego kernel: [    2.769154] EDD information not available.
May  7 01:40:03 tashtego kernel: [    2.770854] Freeing unused kernel memory: 532k freed
May  7 01:40:03 tashtego kernel: [    2.771080] Write protecting the kernel text: 4128k
May  7 01:40:03 tashtego kernel: [    2.771150] Write protecting the kernel read-only data: 1532k
May  7 01:40:03 tashtego kernel: [    2.807435] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
May  7 01:40:03 tashtego kernel: [    2.832386] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
May  7 01:40:03 tashtego kernel: [    3.403505] Floppy drive(s): fd0 is 1.44M
May  7 01:40:03 tashtego kernel: [    3.422541] FDC 0 is a post-1991 82077
May  7 01:40:03 tashtego kernel: [    3.635264] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
May  7 01:40:03 tashtego kernel: [    3.635348] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
May  7 01:40:03 tashtego kernel: [    3.643524] 8139too Fast Ethernet driver 0.9.28
May  7 01:40:03 tashtego kernel: [    3.643659] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
May  7 01:40:03 tashtego kernel: [    3.645177] eth0: RealTek RTL8139 at 0x1400, 00:08:02:04:d9:a1, IRQ 11
May  7 01:40:03 tashtego kernel: [    4.339594] Marking TSC unstable due to TSC halts in idle
May  7 01:40:03 tashtego kernel: [    4.413445] PM: Starting manual resume from disk
May  7 01:40:03 tashtego kernel: [    4.419878] EXT3-fs: INFO: recovery required on readonly filesystem.
May  7 01:40:03 tashtego kernel: [    4.419888] EXT3-fs: write access will be enabled during recovery.
May  7 01:40:03 tashtego kernel: [    5.615086] kjournald starting.  Commit interval 5 seconds
May  7 01:40:03 tashtego kernel: [    5.615135] EXT3-fs: recovery complete.
May  7 01:40:03 tashtego kernel: [    5.616424] EXT3-fs: mounted filesystem with ordered data mode.
May  7 01:40:03 tashtego kernel: [   15.514999] udev: starting version 141
May  7 01:40:03 tashtego kernel: [   15.816658] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input6
May  7 01:40:03 tashtego kernel: [   15.852360] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
May  7 01:40:03 tashtego kernel: [   16.063980] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  7 01:40:03 tashtego kernel: [   16.342075] Linux agpgart interface v0.103
May  7 01:40:03 tashtego kernel: [   16.394820] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
May  7 01:40:03 tashtego kernel: [   16.492280] parport_pc: VIA parallel port: io=0x378, irq=7
May  7 01:40:03 tashtego kernel: [   16.638489] input: PC Speaker as /devices/platform/pcspkr/input/input7
May  7 01:40:03 tashtego kernel: [   17.040830] yenta_cardbus 0000:00:0a.0: CardBus bridge found [0e11:b103]
May  7 01:40:03 tashtego kernel: [   17.040860] yenta_cardbus 0000:00:0a.0: Enabling burst memory read transactions
May  7 01:40:03 tashtego kernel: [   17.040868] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
May  7 01:40:03 tashtego kernel: [   17.040872] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
May  7 01:40:03 tashtego kernel: [   17.040879] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01001002, devctl 0x64
May  7 01:40:03 tashtego kernel: [   17.064595] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
May  7 01:40:03 tashtego kernel: [   17.158362] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  7 01:40:03 tashtego kernel: [   17.273126] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0018, PCI irq 11
May  7 01:40:03 tashtego kernel: [   17.273136] yenta_cardbus 0000:00:0a.0: Socket status: 30000010
May  7 01:40:03 tashtego kernel: [   17.279816] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
May  7 01:40:03 tashtego kernel: [   17.287154] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xec000000
May  7 01:40:03 tashtego kernel: [   17.314419] ppdev: user-space parallel port driver
May  7 01:40:03 tashtego kernel: [   17.578353] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
May  7 01:40:03 tashtego kernel: [   17.578374] VIA 82xx Audio 0000:00:07.5: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
May  7 01:40:03 tashtego kernel: [   17.924052] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
May  7 01:40:03 tashtego kernel: [   18.001300] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
May  7 01:40:03 tashtego kernel: [   18.003747] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
May  7 01:40:03 tashtego kernel: [   18.004846] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
May  7 01:40:03 tashtego kernel: [   18.005727] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
May  7 01:40:03 tashtego kernel: [   18.006898] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
May  7 01:40:03 tashtego kernel: [   18.007903] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
May  7 01:40:03 tashtego kernel: [   18.015343] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
May  7 01:40:03 tashtego kernel: [   18.072729] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9d48b1, caps: 0x904713/0x4006
May  7 01:40:03 tashtego kernel: [   18.129739] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
May  7 01:40:03 tashtego kernel: [   19.291316] lp0: using parport0 (interrupt-driven).
May  7 01:40:03 tashtego kernel: [   19.639905] Adding 650592k swap on /dev/sda5.  Priority:-1 extents:1 across:650592k
May  7 01:40:03 tashtego kernel: [   20.367947] EXT3 FS on sda6, internal journal
May  7 01:40:03 tashtego kernel: [   21.886538] type=1505 audit(1241674801.614:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2027
May  7 01:40:03 tashtego kernel: [   22.006475] type=1505 audit(1241674801.734:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2031
May  7 01:40:03 tashtego kernel: [   22.007119] type=1505 audit(1241674801.734:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2031
May  7 01:40:03 tashtego kernel: [   22.007300] type=1505 audit(1241674801.734:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2031
May  7 01:40:03 tashtego kernel: [   22.007448] type=1505 audit(1241674801.734:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2031
May  7 01:40:03 tashtego kernel: [   22.348468] type=1505 audit(1241674802.078:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2036
May  7 01:40:03 tashtego kernel: [   22.349225] type=1505 audit(1241674802.078:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2036
May  7 01:40:03 tashtego kernel: [   22.422861] type=1505 audit(1241674802.150:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2040
May  7 01:40:06 tashtego kernel: [   26.368142] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  7 01:40:06 tashtego kernel: [   26.368150] Bluetooth: BNEP filters: protocol multicast
May  7 01:40:06 tashtego kernel: [   26.405377] Bridge firewalling registered
May  7 01:40:12 tashtego kernel: [   32.270181] eth0: link down
May  7 01:40:12 tashtego kernel: [   32.270318] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  7 01:40:12 tashtego kernel: [   32.316105] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  7 01:40:12 tashtego kernel: [   32.340614] eth1: New link status: Disconnected (0002)
May  7 01:40:13 tashtego kernel: [   33.671591] eth1: New link status: Connected (0001)
May  7 01:40:13 tashtego kernel: [   33.671678] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May  7 01:40:39 tashtego kernel: [   59.953358] eth1: New link status: Disconnected (0002)
May  7 01:40:40 tashtego kernel: [   60.814368] eth1: New link status: Connected (0001)
May  7 13:41:12 tashtego kernel: [   92.340127] Clocksource tsc unstable (delta = -291681368 ns)
ryan@tashtego:~$ 


```

I'm having the same blank screen freeze problem with log off as well.

---

### Post by gorean on 2009-05-07
I have been working on a problem with a USB sound card not having an IRQ.
The only reason that this might be relevant to your situation if I leave it plugged during shutdown sometimes it starts to negotiate with the system for an address and I end up with the system power on with a system halted message on screen.
The operating system has stopped but it did not power down.
I would try:
<shift> F1: to get to regular terminal.
"sudo reboot" or "sudo shutdown -h now" 
then watch the messages as the processes shut down.

syslog may offer some clues "cat /var/syslog" will show results.
dmesg might show some conflict.

Hopefully that gives at least somewhere to look.

---

### Post by Dr. Feelgood on 2009-05-08
Ah but there in lies the rub.  I can't get to terminal outside of X... the instant X stops (or tries to stop) it's blank screen and unresponsive system.  <shift> <F1> actually doesn't do anything for me anyway, neither does <ctl> <alt> <backsp>, but thats besiedes the point.  Any attempt at stopping gnome or the X server produces this problem.

The /var/log/syslog however seems to produce some interesting results
```

May  8 11:57:06 tashtego console-kit-daemon[2388]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 11:57:06 tashtego last message repeated 4 times
May  8 11:57:06 tashtego init: tty4 main process (2176) killed by TERM signal
May  8 11:57:06 tashtego init: tty5 main process (2177) killed by TERM signal
May  8 11:57:06 tashtego init: tty2 main process (2183) killed by TERM signal
May  8 11:57:06 tashtego init: tty3 main process (2186) killed by TERM signal
May  8 11:57:06 tashtego init: tty6 main process (2187) killed by TERM signal
May  8 11:57:06 tashtego init: tty1 main process (2886) killed by TERM signal
May  8 07:58:40 tashtego syslogd 1.5.0#5ubuntu3: restart.
May  8 07:58:40 tashtego kernel: Inspecting /boot/System.map-2.6.28-11-generic
May  8 07:58:40 tashtego kernel: Cannot find map file.
May  8 07:58:40 tashtego kernel: Loaded 54398 symbols from 56 modules.
May  8 07:58:40 tashtego kernel: [    0.000000] BIOS EBDA/lowmem at: 0009e800/0009e800
May  8 07:58:40 tashtego kernel: [    0.000000] Initializing cgroup subsys cpuset
May  8 07:58:40 tashtego kernel: [    0.000000] Initializing cgroup subsys cpu
May  8 07:58:40 tashtego kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
May  8 07:58:40 tashtego kernel: [    0.000000] KERNEL supported cpus:
May  8 07:58:40 tashtego kernel: [    0.000000]   Intel GenuineIntel
May  8 07:58:40 tashtego kernel: [    0.000000]   AMD AuthenticAMD
May  8 07:58:40 tashtego kernel: [    0.000000]   NSC Geode by NSC
May  8 07:58:40 tashtego kernel: [    0.000000]   Cyrix CyrixInstead
May  8 07:58:40 tashtego kernel: [    0.000000]   Centaur CentaurHauls
May  8 07:58:40 tashtego kernel: [    0.000000]   Transmeta GenuineTMx86
May  8 07:58:40 tashtego kernel: [    0.000000]   Transmeta TransmetaCPU
May  8 07:58:40 tashtego kernel: [    0.000000]   UMC UMC UMC UMC
May  8 07:58:40 tashtego kernel: [    0.000000] BIOS-provided physical RAM map:
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000def0000 (usable)
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 000000000def0000 - 000000000deff000 (ACPI data)
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 000000000deff000 - 000000000df00000 (ACPI NVS)
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 000000000df00000 - 000000000e000000 (usable)
May  8 07:58:40 tashtego kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000] DMI 2.3 present.
May  8 07:58:40 tashtego kernel: [    0.000000] last_pfn = 0xe000 max_arch_pfn = 0x100000
May  8 07:58:40 tashtego kernel: [    0.000000] Scanning 2 areas for low memory corruption
May  8 07:58:40 tashtego kernel: [    0.000000] modified physical RAM map:
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 0000000000010000 - 0000000000091800 (usable)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 00000000000c0000 - 00000000000cc000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 0000000000100000 - 000000000def0000 (usable)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 000000000def0000 - 000000000deff000 (ACPI data)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 000000000deff000 - 000000000df00000 (ACPI NVS)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 000000000df00000 - 000000000e000000 (usable)
May  8 07:58:40 tashtego kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
May  8 07:58:40 tashtego kernel: [    0.000000] kernel direct mapping tables up to e000000 @ 10000-15000
May  8 07:58:40 tashtego kernel: [    0.000000] RAMDISK: 0d7ad000 - 0dedfd0f
May  8 07:58:40 tashtego kernel: [    0.000000] ACPI: RSDP 000F6DC0, 0014 (r0 PTLTD )
May  8 07:58:40 tashtego kernel: [    0.000000] ACPI: RSDT 0DEFB61A, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
May  8 07:58:40 tashtego kernel: [    0.000000] ACPI: FACP 0DEFEE95, 0074 (r1 COMPAQ  EAGLES   6040000 PTL_    F4240)
May  8 07:58:40 tashtego kernel: [    0.000000] ACPI: DSDT 0DEFB646, 384F (r1 COMAPQ   EAGLES  6040000 MSFT  100000D)
May  8 07:58:40 tashtego kernel: [    0.000000] ACPI: FACS 0DEFFFC0, 0040
May  8 07:58:40 tashtego kernel: [    0.000000] ACPI: SSDT 0DEFEF09, 00F7 (r1 PTLTD  POWERNOW  6040000  LTP        1)
May  8 07:58:40 tashtego kernel: [    0.000000] 0MB HIGHMEM available.
May  8 07:58:40 tashtego kernel: [    0.000000] 224MB LOWMEM available.
May  8 07:58:40 tashtego kernel: [    0.000000]   mapped low ram: 0 - 0e000000
May  8 07:58:40 tashtego kernel: [    0.000000]   low ram: 00000000 - 0e000000
May  8 07:58:40 tashtego kernel: [    0.000000]   bootmap 00011000 - 00012c00
May  8 07:58:40 tashtego kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000e000000]
May  8 07:58:40 tashtego kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  8 07:58:40 tashtego kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  8 07:58:40 tashtego kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  8 07:58:40 tashtego kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
May  8 07:58:40 tashtego kernel: [    0.000000]   #4 [000d7ad000 - 000dedfd0f]          RAMDISK ==> [000d7ad000 - 000dedfd0f]
May  8 07:58:40 tashtego kernel: [    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
May  8 07:58:40 tashtego kernel: [    0.000000]   #6 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
May  8 07:58:40 tashtego kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
May  8 07:58:40 tashtego kernel: [    0.000000]   #8 [0000011000 - 0000013000]          BOOTMAP ==> [0000011000 - 0000013000]
May  8 07:58:40 tashtego kernel: [    0.000000] Zone PFN ranges:
May  8 07:58:40 tashtego kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  8 07:58:40 tashtego kernel: [    0.000000]   Normal   0x00001000 -> 0x0000e000
May  8 07:58:40 tashtego kernel: [    0.000000]   HighMem  0x0000e000 -> 0x0000e000
May  8 07:58:40 tashtego kernel: [    0.000000] Movable zone start PFN for each node
May  8 07:58:40 tashtego kernel: [    0.000000] early_node_map[5] active PFN ranges
May  8 07:58:40 tashtego kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
May  8 07:58:40 tashtego kernel: [    0.000000]     0: 0x00000006 -> 0x00000007
May  8 07:58:40 tashtego kernel: [    0.000000]     0: 0x00000010 -> 0x00000091
May  8 07:58:40 tashtego kernel: [    0.000000]     0: 0x00000100 -> 0x0000def0
May  8 07:58:40 tashtego kernel: [    0.000000]     0: 0x0000df00 -> 0x0000e000
May  8 07:58:40 tashtego kernel: [    0.000000] On node 0 totalpages: 57204
May  8 07:58:40 tashtego kernel: [    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
May  8 07:58:40 tashtego kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May  8 07:58:40 tashtego kernel: [    0.000000]   DMA zone: 0 pages reserved
May  8 07:58:40 tashtego kernel: [    0.000000]   DMA zone: 3940 pages, LIFO batch:0
May  8 07:58:40 tashtego kernel: [    0.000000]   Normal zone: 416 pages used for memmap
May  8 07:58:40 tashtego kernel: [    0.000000]   Normal zone: 52816 pages, LIFO batch:15
May  8 07:58:40 tashtego kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May  8 07:58:40 tashtego kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May  8 07:58:40 tashtego kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
May  8 07:58:40 tashtego kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  8 07:58:40 tashtego kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009f000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000c0000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000c0000 - 00000000000cc000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000cc000 - 00000000000dc000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000def0000 - 000000000deff000
May  8 07:58:40 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000deff000 - 000000000df00000
May  8 07:58:40 tashtego kernel: [    0.000000] Allocating PCI resources starting at 10000000 (gap: e000000:f1f80000)
May  8 07:58:40 tashtego kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
May  8 07:58:40 tashtego kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
May  8 07:58:40 tashtego kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 56756
May  8 07:58:40 tashtego kernel: [    0.000000] Kernel command line: root=UUID=56b02b03-88d9-4fa8-8657-89aa5bc2bd22 ro xforcevesa quiet splash 
May  8 07:58:40 tashtego kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  8 07:58:40 tashtego kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  8 07:58:40 tashtego kernel: [    0.000000] Initializing CPU#0
May  8 07:58:40 tashtego kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
May  8 07:58:40 tashtego kernel: [    0.000000] Fast TSC calibration using PIT
May  8 07:58:40 tashtego kernel: [    0.000000] Detected 1195.685 MHz processor.
May  8 07:58:40 tashtego kernel: [    0.004000] Console: colour VGA+ 80x25
May  8 07:58:40 tashtego kernel: [    0.004000] console [tty0] enabled
May  8 07:58:40 tashtego kernel: [    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
May  8 07:58:40 tashtego kernel: [    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
May  8 07:58:40 tashtego kernel: [    0.004000] allocated 1146880 bytes of page_cgroup
May  8 07:58:40 tashtego kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
May  8 07:58:40 tashtego kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
May  8 07:58:40 tashtego kernel: [    0.004000] Memory: 210280k/229376k available (4126k kernel code, 18260k reserved, 2208k data, 532k init, 0k highmem)
May  8 07:58:40 tashtego kernel: [    0.004000] virtual kernel memory layout:
May  8 07:58:40 tashtego kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
May  8 07:58:40 tashtego kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
May  8 07:58:40 tashtego kernel: [    0.004000]     vmalloc : 0xce800000 - 0xff3fe000   ( 779 MB)
May  8 07:58:40 tashtego kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xce000000   ( 224 MB)
May  8 07:58:40 tashtego kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
May  8 07:58:40 tashtego kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
May  8 07:58:40 tashtego kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
May  8 07:58:40 tashtego kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  8 07:58:40 tashtego kernel: [    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  8 07:58:40 tashtego kernel: [    0.004025] Calibrating delay loop (skipped), value calculated using timer frequency.. 2391.37 BogoMIPS (lpj=4782740)
May  8 07:58:40 tashtego kernel: [    0.004070] Security Framework initialized
May  8 07:58:40 tashtego kernel: [    0.004089] SELinux:  Disabled at boot.
May  8 07:58:40 tashtego kernel: [    0.004152] AppArmor: AppArmor initialized
May  8 07:58:40 tashtego kernel: [    0.004170] Mount-cache hash table entries: 512
May  8 07:58:40 tashtego kernel: [    0.004482] Initializing cgroup subsys ns
May  8 07:58:40 tashtego kernel: [    0.004491] Initializing cgroup subsys cpuacct
May  8 07:58:40 tashtego kernel: [    0.004495] Initializing cgroup subsys memory
May  8 07:58:40 tashtego kernel: [    0.004506] Initializing cgroup subsys freezer
May  8 07:58:40 tashtego kernel: [    0.004533] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  8 07:58:40 tashtego kernel: [    0.004538] CPU: L2 Cache: 256K (64 bytes/line)
May  8 07:58:40 tashtego kernel: [    0.004574] Checking 'hlt' instruction... OK.
May  8 07:58:40 tashtego kernel: [    0.020873] SMP alternatives: switching to UP code
May  8 07:58:40 tashtego kernel: [    0.277052] Freeing SMP alternatives: 18k freed
May  8 07:58:40 tashtego kernel: [    0.277063] ACPI: Core revision 20080926
May  8 07:58:40 tashtego kernel: [    0.280602] ACPI: Checking initramfs for custom DSDT
May  8 07:58:40 tashtego kernel: [    0.770282] ACPI: setting ELCR to 0400 (from 0a30)
May  8 07:58:40 tashtego kernel: [    0.772158] weird, boot CPU (#0) not listedby the BIOS.
May  8 07:58:40 tashtego kernel: [    0.772163] SMP motherboard not detected.
May  8 07:58:40 tashtego kernel: [    0.772170] Local APIC not detected. Using dummy APIC emulation.
May  8 07:58:40 tashtego kernel: [    0.772174] SMP disabled
May  8 07:58:40 tashtego kernel: [    0.772884] Brought up 1 CPUs
May  8 07:58:40 tashtego kernel: [    0.772890] Total of 1 processors activated (2391.37 BogoMIPS).
May  8 07:58:40 tashtego kernel: [    0.772924] CPU0 attaching NULL sched-domain.
May  8 07:58:40 tashtego kernel: [    0.773793] net_namespace: 776 bytes
May  8 07:58:40 tashtego kernel: [    0.773818] Booting paravirtualized kernel on bare hardware
May  8 07:58:40 tashtego kernel: [    0.774302] Time:  7:58:17  Date: 05/08/09
May  8 07:58:40 tashtego kernel: [    0.774314] regulator: core version 0.5
May  8 07:58:40 tashtego kernel: [    0.774418] NET: Registered protocol family 16
May  8 07:58:40 tashtego kernel: [    0.774721] EISA bus registered
May  8 07:58:40 tashtego kernel: [    0.774757] ACPI: bus type pci registered
May  8 07:58:40 tashtego kernel: [    0.775187] PCI: PCI BIOS revision 2.10 entry at 0xfd7ae, last bus=1
May  8 07:58:40 tashtego kernel: [    0.775192] PCI: Using configuration type 1 for base access
May  8 07:58:40 tashtego kernel: [    0.778188] ACPI: EC: Look up EC in DSDT
May  8 07:58:40 tashtego kernel: [    0.783162] ACPI: Interpreter enabled
May  8 07:58:40 tashtego kernel: [    0.783170] ACPI: (supports S0 S3 S4 S5)
May  8 07:58:40 tashtego kernel: [    0.783197] ACPI: Using PIC for interrupt routing
May  8 07:58:40 tashtego kernel: [    0.783837] ACPI: EC: non-query interrupt received, switching to interrupt mode
May  8 07:58:40 tashtego kernel: [    0.789874] ACPI: EC: GPE = 0x6, I/O: command/status = 0x66, data = 0x62
May  8 07:58:40 tashtego kernel: [    0.789879] ACPI: EC: driver started in interrupt mode
May  8 07:58:40 tashtego kernel: [    0.790033] ACPI: No dock devices found.
May  8 07:58:40 tashtego kernel: [    0.790051] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  8 07:58:40 tashtego kernel: [    0.790138] pci 0000:00:00.0: reg 10 32bit mmio: [0xec000000-0xefffffff]
May  8 07:58:40 tashtego kernel: [    0.790172] pci 0000:00:00.0: Disabling VIA memory write queue (PCI ID 0305, rev 80): [55] 3c & 1f -> 1c
May  8 07:58:40 tashtego kernel: [    0.790218] pci 0000:00:01.0: supports D1
May  8 07:58:40 tashtego kernel: [    0.790325] pci 0000:00:07.1: reg 20 io port: [0x1840-0x184f]
May  8 07:58:40 tashtego kernel: [    0.790386] pci 0000:00:07.2: reg 20 io port: [0x1800-0x181f]
May  8 07:58:40 tashtego kernel: [    0.790466] pci 0000:00:07.4: quirk: region 8100-810f claimed by vt82c686 SMB
May  8 07:58:40 tashtego kernel: [    0.790506] pci 0000:00:07.5: reg 10 io port: [0x1000-0x10ff]
May  8 07:58:40 tashtego kernel: [    0.790515] pci 0000:00:07.5: reg 14 io port: [0x1854-0x1857]
May  8 07:58:40 tashtego kernel: [    0.790523] pci 0000:00:07.5: reg 18 io port: [0x1850-0x1853]
May  8 07:58:40 tashtego kernel: [    0.790580] pci 0000:00:09.0: reg 10 32bit mmio: [0xe8000000-0xe800ffff]
May  8 07:58:40 tashtego kernel: [    0.790588] pci 0000:00:09.0: reg 14 io port: [0x1858-0x185f]
May  8 07:58:40 tashtego kernel: [    0.790616] pci 0000:00:09.0: PME# supported from D3hot
May  8 07:58:40 tashtego kernel: [    0.790622] pci 0000:00:09.0: PME# disabled
May  8 07:58:40 tashtego kernel: [    0.790656] pci 0000:00:0a.0: reg 10 32bit mmio: [0xffbfe000-0xffbfefff]
May  8 07:58:40 tashtego kernel: [    0.790666] pci 0000:00:0a.0: supports D1 D2
May  8 07:58:40 tashtego kernel: [    0.790670] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
May  8 07:58:40 tashtego kernel: [    0.790675] pci 0000:00:0a.0: PME# disabled
May  8 07:58:40 tashtego kernel: [    0.790706] pci 0000:00:0b.0: reg 10 io port: [0x1400-0x14ff]
May  8 07:58:40 tashtego kernel: [    0.790714] pci 0000:00:0b.0: reg 14 32bit mmio: [0xe8010000-0xe80100ff]
May  8 07:58:40 tashtego kernel: [    0.790743] pci 0000:00:0b.0: supports D1 D2
May  8 07:58:40 tashtego kernel: [    0.790747] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
May  8 07:58:40 tashtego kernel: [    0.790752] pci 0000:00:0b.0: PME# disabled
May  8 07:58:40 tashtego kernel: [    0.790815] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8100000-0xe817ffff]
May  8 07:58:40 tashtego kernel: [    0.790823] pci 0000:01:00.0: reg 14 32bit mmio: [0xf0000000-0xf7ffffff]
May  8 07:58:40 tashtego kernel: [    0.790845] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
May  8 07:58:40 tashtego kernel: [    0.790855] pci 0000:01:00.0: supports D1 D2
May  8 07:58:40 tashtego kernel: [    0.790895] pci 0000:00:01.0: bridge 32bit mmio: [0xe8100000-0xe81fffff]
May  8 07:58:40 tashtego kernel: [    0.790901] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf7ffffff]
May  8 07:58:40 tashtego kernel: [    0.790928] bus 00 -> node 0
May  8 07:58:40 tashtego kernel: [    0.790940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  8 07:58:40 tashtego kernel: [    0.795161] ACPI: PCI Interrupt Link [LNKA] (IRQs *4)
May  8 07:58:40 tashtego kernel: [    0.795407] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
May  8 07:58:40 tashtego kernel: [    0.795641] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
May  8 07:58:40 tashtego kernel: [    0.795884] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
May  8 07:58:40 tashtego kernel: [    0.796121] ACPI: WMI: Mapper loaded
May  8 07:58:40 tashtego kernel: [    0.796670] SCSI subsystem initialized
May  8 07:58:40 tashtego kernel: [    0.796788] libata version 3.00 loaded.
May  8 07:58:40 tashtego kernel: [    0.796936] usbcore: registered new interface driver usbfs
May  8 07:58:40 tashtego kernel: [    0.796974] usbcore: registered new interface driver hub
May  8 07:58:40 tashtego kernel: [    0.797040] usbcore: registered new device driver usb
May  8 07:58:40 tashtego kernel: [    0.797287] PCI: Using ACPI for IRQ routing
May  8 07:58:40 tashtego kernel: [    0.797443] Bluetooth: Core ver 2.13
May  8 07:58:40 tashtego kernel: [    0.797443] NET: Registered protocol family 31
May  8 07:58:40 tashtego kernel: [    0.797443] Bluetooth: HCI device and connection manager initialized
May  8 07:58:40 tashtego kernel: [    0.797443] Bluetooth: HCI socket layer initialized
May  8 07:58:40 tashtego kernel: [    0.797443] NET: Registered protocol family 8
May  8 07:58:40 tashtego kernel: [    0.797443] NET: Registered protocol family 20
May  8 07:58:40 tashtego kernel: [    0.797443] NetLabel: Initializing
May  8 07:58:40 tashtego kernel: [    0.797443] NetLabel:  domain hash size = 128
May  8 07:58:40 tashtego kernel: [    0.797443] NetLabel:  protocols = UNLABELED CIPSOv4
May  8 07:58:40 tashtego kernel: [    0.797443] NetLabel:  unlabeled traffic allowed by default
May  8 07:58:40 tashtego kernel: [    0.797443] AppArmor: AppArmor Filesystem Enabled
May  8 07:58:40 tashtego kernel: [    0.797443] pnp: PnP ACPI init
May  8 07:58:40 tashtego kernel: [    0.797443] ACPI: bus type pnp registered
May  8 07:58:40 tashtego kernel: [    0.802373] pnp: PnP ACPI: found 11 devices
May  8 07:58:40 tashtego kernel: [    0.802377] ACPI: ACPI bus type pnp unregistered
May  8 07:58:40 tashtego kernel: [    0.802385] PnPBIOS: Disabled by ACPI PNP
May  8 07:58:40 tashtego kernel: [    0.802409] system 00:05: iomem range 0x0-0x9ffff could not be reserved
May  8 07:58:40 tashtego kernel: [    0.802416] system 00:05: iomem range 0xdc000-0xdffff could not be reserved
May  8 07:58:40 tashtego kernel: [    0.802421] system 00:05: iomem range 0x7000000-0x7ffffff could not be reserved
May  8 07:58:40 tashtego kernel: [    0.802432] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
May  8 07:58:40 tashtego kernel: [    0.837320] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
May  8 07:58:40 tashtego kernel: [    0.837324] pci 0000:00:01.0:   IO window: disabled
May  8 07:58:40 tashtego kernel: [    0.837333] pci 0000:00:01.0:   MEM window: 0xe8100000-0xe81fffff
May  8 07:58:40 tashtego kernel: [    0.837339] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
May  8 07:58:40 tashtego kernel: [    0.837348] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
May  8 07:58:40 tashtego kernel: [    0.837352] pci 0000:00:0a.0:   IO window: 0x001c00-0x001cff
May  8 07:58:40 tashtego kernel: [    0.837358] pci 0000:00:0a.0:   IO window: 0x002000-0x0020ff
May  8 07:58:40 tashtego kernel: [    0.837364] pci 0000:00:0a.0:   PREFETCH window: 0x10000000-0x13ffffff
May  8 07:58:40 tashtego kernel: [    0.837370] pci 0000:00:0a.0:   MEM window: 0x14000000-0x17ffffff
May  8 07:58:40 tashtego kernel: [    0.837393] pci 0000:00:01.0: setting latency timer to 64
May  8 07:58:40 tashtego kernel: [    0.837474] pci 0000:00:0a.0: power state changed by ACPI to D0
May  8 07:58:40 tashtego kernel: [    0.837860] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
May  8 07:58:40 tashtego kernel: [    0.837867] PCI: setting IRQ 11 as level-triggered
May  8 07:58:40 tashtego kernel: [    0.837877] pci 0000:00:0a.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
May  8 07:58:40 tashtego kernel: [    0.837888] bus: 00 index 0 io port: [0x00-0xffff]
May  8 07:58:40 tashtego kernel: [    0.837891] bus: 00 index 1 mmio: [0x000000-0xffffffff]
May  8 07:58:40 tashtego kernel: [    0.837895] bus: 01 index 0 mmio: [0x0-0x0]
May  8 07:58:40 tashtego kernel: [    0.837899] bus: 01 index 1 mmio: [0xe8100000-0xe81fffff]
May  8 07:58:40 tashtego kernel: [    0.837902] bus: 01 index 2 mmio: [0xf0000000-0xf7ffffff]
May  8 07:58:40 tashtego kernel: [    0.837906] bus: 01 index 3 mmio: [0x0-0x0]
May  8 07:58:40 tashtego kernel: [    0.837909] bus: 02 index 0 io port: [0x1c00-0x1cff]
May  8 07:58:40 tashtego kernel: [    0.837913] bus: 02 index 1 io port: [0x2000-0x20ff]
May  8 07:58:40 tashtego kernel: [    0.837917] bus: 02 index 2 mmio: [0x10000000-0x13ffffff]
May  8 07:58:40 tashtego kernel: [    0.837920] bus: 02 index 3 mmio: [0x14000000-0x17ffffff]
May  8 07:58:40 tashtego kernel: [    0.837953] NET: Registered protocol family 2
May  8 07:58:40 tashtego kernel: [    0.838206] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
May  8 07:58:40 tashtego kernel: [    0.838732] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
May  8 07:58:40 tashtego kernel: [    0.838962] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
May  8 07:58:40 tashtego kernel: [    0.839169] TCP: Hash tables configured (established 8192 bind 8192)
May  8 07:58:40 tashtego kernel: [    0.839175] TCP reno registered
May  8 07:58:40 tashtego kernel: [    0.839319] NET: Registered protocol family 1
May  8 07:58:40 tashtego kernel: [    0.839623] checking if image is initramfs... it is
May  8 07:58:40 tashtego kernel: [    1.340154] Switched to high resolution mode on CPU 0
May  8 07:58:40 tashtego kernel: [    1.942790] Freeing initrd memory: 7371k freed
May  8 07:58:40 tashtego kernel: [    1.943067] cpufreq: No nForce2 chipset.
May  8 07:58:40 tashtego kernel: [    1.943388] audit: initializing netlink socket (disabled)
May  8 07:58:40 tashtego kernel: [    1.943446] type=2000 audit(1241769496.940:1): initialized
May  8 07:58:40 tashtego kernel: [    1.956674] HugeTLB registered 4 MB page size, pre-allocated 0 pages
May  8 07:58:40 tashtego kernel: [    1.959066] VFS: Disk quotas dquot_6.5.1
May  8 07:58:40 tashtego kernel: [    1.959177] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  8 07:58:40 tashtego kernel: [    1.960389] fuse init (API version 7.10)
May  8 07:58:40 tashtego kernel: [    1.960559] msgmni has been set to 425
May  8 07:58:40 tashtego kernel: [    1.961010] alg: No test for stdrng (krng)
May  8 07:58:40 tashtego kernel: [    1.961038] io scheduler noop registered
May  8 07:58:40 tashtego kernel: [    1.961042] io scheduler anticipatory registered
May  8 07:58:40 tashtego kernel: [    1.961046] io scheduler deadline registered
May  8 07:58:40 tashtego kernel: [    1.961075] io scheduler cfq registered (default)
May  8 07:58:40 tashtego kernel: [    1.961120] pci 0000:00:00.0: Applying VIA southbridge workaround
May  8 07:58:40 tashtego kernel: [    1.961128] PCI: VIA PCI bridge detected.Disabling DAC.
May  8 07:58:40 tashtego kernel: [    1.961136] pci 0000:00:07.0: Disabling VIA external APIC routing
May  8 07:58:40 tashtego kernel: [    1.961176] pci 0000:01:00.0: Boot video device
May  8 07:58:40 tashtego kernel: [    1.966398] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  8 07:58:40 tashtego kernel: [    1.966416] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  8 07:58:40 tashtego kernel: [    1.967086] ACPI: AC Adapter [AC] (on-line)
May  8 07:58:40 tashtego kernel: [    1.979717] ACPI: Battery Slot [BAT0] (battery present)
May  8 07:58:40 tashtego kernel: [    1.979879] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
May  8 07:58:40 tashtego kernel: [    1.979885] ACPI: Power Button (FF) [PWRF]
May  8 07:58:40 tashtego kernel: [    1.979968] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
May  8 07:58:40 tashtego kernel: [    1.979978] ACPI: Sleep Button (CM) [SLPB]
May  8 07:58:40 tashtego kernel: [    1.980079] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
May  8 07:58:40 tashtego kernel: [    1.980086] ACPI: Power Button (CM) [PWRB]
May  8 07:58:40 tashtego kernel: [    1.980178] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
May  8 07:58:40 tashtego kernel: [    1.986246] ACPI: Lid Switch [LID]
May  8 07:58:40 tashtego kernel: [    1.986544] ACPI: CPU0 (power states: C1[C1] C2[C2])
May  8 07:58:40 tashtego kernel: [    1.986594] processor ACPI_CPU:00: registered as cooling_device0
May  8 07:58:40 tashtego kernel: [    1.986601] ACPI: Processor [CPU0] (supports 16 throttling states)
May  8 07:58:40 tashtego kernel: [    1.989517] isapnp: Scanning for PnP cards...
May  8 07:58:40 tashtego kernel: [    2.343722] isapnp: No Plug & Play device found
May  8 07:58:40 tashtego kernel: [    2.346354] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  8 07:58:40 tashtego kernel: [    2.348333] brd: module loaded
May  8 07:58:40 tashtego kernel: [    2.348973] loop: module loaded
May  8 07:58:40 tashtego kernel: [    2.349194] Fixed MDIO Bus: probed
May  8 07:58:40 tashtego kernel: [    2.349207] PPP generic driver version 2.4.2
May  8 07:58:40 tashtego kernel: [    2.349327] input: Macintosh mouse button emulation as /devices/virtual/input/input4
May  8 07:58:40 tashtego kernel: [    2.349431] Driver 'sd' needs updating - please use bus_type methods
May  8 07:58:40 tashtego kernel: [    2.349450] Driver 'sr' needs updating - please use bus_type methods
May  8 07:58:40 tashtego kernel: [    2.350345] pata_via 0000:00:07.1: version 0.3.3
May  8 07:58:40 tashtego kernel: [    2.350782] scsi0 : pata_via
May  8 07:58:40 tashtego kernel: [    2.351014] scsi1 : pata_via
May  8 07:58:40 tashtego kernel: [    2.352231] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1840 irq 14
May  8 07:58:40 tashtego kernel: [    2.352237] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1848 irq 15
May  8 07:58:40 tashtego kernel: [    2.516519] ata1.00: ATA-5: HITACHI_DK23CA-20, 00H1A0J1, max UDMA/100
May  8 07:58:40 tashtego kernel: [    2.516524] ata1.00: 39070080 sectors, multi 16: LBA 
May  8 07:58:40 tashtego kernel: [    2.532504] ata1.00: configured for UDMA/100
May  8 07:58:40 tashtego kernel: [    2.696434] ata2.00: ATAPI: SD-R2102, 1A15, max MWDMA2
May  8 07:58:40 tashtego kernel: [    2.712455] ata2.00: configured for MWDMA2
May  8 07:58:40 tashtego kernel: [    2.713414] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23CA-2 00H1 PQ: 0 ANSI: 5
May  8 07:58:40 tashtego kernel: [    2.713634] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
May  8 07:58:40 tashtego kernel: [    2.713674] sd 0:0:0:0: [sda] Write Protect is off
May  8 07:58:40 tashtego kernel: [    2.713680] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  8 07:58:40 tashtego kernel: [    2.713735] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 07:58:40 tashtego kernel: [    2.713929] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
May  8 07:58:40 tashtego kernel: [    2.713960] sd 0:0:0:0: [sda] Write Protect is off
May  8 07:58:40 tashtego kernel: [    2.713965] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  8 07:58:40 tashtego kernel: [    2.714017] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 07:58:40 tashtego kernel: [    2.714026]  sda: sda1 sda2 < sda5 sda6 >
May  8 07:58:40 tashtego kernel: [    2.746826] sd 0:0:0:0: [sda] Attached SCSI disk
May  8 07:58:40 tashtego kernel: [    2.746949] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  8 07:58:40 tashtego kernel: [    2.749393] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2102 1A15 PQ: 0 ANSI: 5
May  8 07:58:40 tashtego kernel: [    2.756131] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
May  8 07:58:40 tashtego kernel: [    2.756138] Uniform CD-ROM driver Revision: 3.20
May  8 07:58:40 tashtego kernel: [    2.756341] sr 1:0:0:0: Attached scsi CD-ROM sr0
May  8 07:58:40 tashtego kernel: [    2.756422] sr 1:0:0:0: Attached scsi generic sg1 type 5
May  8 07:58:40 tashtego kernel: [    2.756742] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  8 07:58:40 tashtego kernel: [    2.756776] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  8 07:58:40 tashtego kernel: [    2.756798] uhci_hcd: USB Universal Host Controller Interface driver
May  8 07:58:40 tashtego kernel: [    2.757425] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
May  8 07:58:40 tashtego kernel: [    2.757432] PCI: setting IRQ 9 as level-triggered
May  8 07:58:40 tashtego kernel: [    2.757442] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
May  8 07:58:40 tashtego kernel: [    2.757462] uhci_hcd 0000:00:07.2: UHCI Host Controller
May  8 07:58:40 tashtego kernel: [    2.757629] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
May  8 07:58:40 tashtego kernel: [    2.757672] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001800
May  8 07:58:40 tashtego kernel: [    2.757885] usb usb1: configuration #1 chosen from 1 choice
May  8 07:58:40 tashtego kernel: [    2.757942] hub 1-0:1.0: USB hub found
May  8 07:58:40 tashtego kernel: [    2.757970] hub 1-0:1.0: 2 ports detected
May  8 07:58:40 tashtego kernel: [    2.758224] usbcore: registered new interface driver libusual
May  8 07:58:40 tashtego kernel: [    2.758296] usbcore: registered new interface driver usbserial
May  8 07:58:40 tashtego kernel: [    2.758318] USB Serial support registered for generic
May  8 07:58:40 tashtego kernel: [    2.758340] usbcore: registered new interface driver usbserial_generic
May  8 07:58:40 tashtego kernel: [    2.758347] usbserial: USB Serial Driver core
May  8 07:58:40 tashtego kernel: [    2.758433] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May  8 07:58:40 tashtego kernel: [    2.761603] serio: i8042 KBD port at 0x60,0x64 irq 1
May  8 07:58:40 tashtego kernel: [    2.761615] serio: i8042 AUX port at 0x60,0x64 irq 12
May  8 07:58:40 tashtego kernel: [    2.761870] mice: PS/2 mouse device common for all mice
May  8 07:58:40 tashtego kernel: [    2.762292] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
May  8 07:58:40 tashtego kernel: [    2.762327] rtc0: alarms up to one year, y3k, 242 bytes nvram
May  8 07:58:40 tashtego kernel: [    2.762496] device-mapper: uevent: version 1.0.3
May  8 07:58:40 tashtego kernel: [    2.762749] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
May  8 07:58:40 tashtego kernel: [    2.762890] device-mapper: multipath: version 1.0.5 loaded
May  8 07:58:40 tashtego kernel: [    2.762896] device-mapper: multipath round-robin: version 1.0.0 loaded
May  8 07:58:40 tashtego kernel: [    2.763084] EISA: Probing bus 0 at eisa.0
May  8 07:58:40 tashtego kernel: [    2.763100] Cannot allocate resource for EISA slot 1
May  8 07:58:40 tashtego kernel: [    2.763105] Cannot allocate resource for EISA slot 2
May  8 07:58:40 tashtego kernel: [    2.763133] Cannot allocate resource for EISA slot 8
May  8 07:58:40 tashtego kernel: [    2.763137] EISA: Detected 0 cards.
May  8 07:58:40 tashtego kernel: [    2.763255] cpuidle: using governor ladder
May  8 07:58:40 tashtego kernel: [    2.763336] cpuidle: using governor menu
May  8 07:58:40 tashtego kernel: [    2.764360] TCP cubic registered
May  8 07:58:40 tashtego kernel: [    2.764535] NET: Registered protocol family 10
May  8 07:58:40 tashtego kernel: [    2.765320] lo: Disabled Privacy Extensions
May  8 07:58:40 tashtego kernel: [    2.765936] NET: Registered protocol family 17
May  8 07:58:40 tashtego kernel: [    2.765978] Bluetooth: L2CAP ver 2.11
May  8 07:58:40 tashtego kernel: [    2.765981] Bluetooth: L2CAP socket layer initialized
May  8 07:58:40 tashtego kernel: [    2.765987] Bluetooth: SCO (Voice Link) ver 0.6
May  8 07:58:40 tashtego kernel: [    2.765990] Bluetooth: SCO socket layer initialized
May  8 07:58:40 tashtego kernel: [    2.766082] Bluetooth: RFCOMM socket layer initialized
May  8 07:58:40 tashtego kernel: [    2.766104] Bluetooth: RFCOMM TTY layer initialized
May  8 07:58:40 tashtego kernel: [    2.766108] Bluetooth: RFCOMM ver 1.10
May  8 07:58:40 tashtego kernel: [    2.766152] powernow-k8: Processor cpuid 662 not supported
May  8 07:58:40 tashtego kernel: [    2.766269] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
May  8 07:58:40 tashtego kernel: [    2.773790] powernow: No PST tables match this cpuid (0x762)
May  8 07:58:40 tashtego kernel: [    2.773794] powernow: This is indicative of a broken BIOS.
May  8 07:58:40 tashtego kernel: [    2.773797] powernow: Trying ACPI perflib
May  8 07:58:40 tashtego kernel: [    2.773836] powernow: Minimum speed 498 MHz. Maximum speed 1195 MHz.
May  8 07:58:40 tashtego kernel: [    2.774038] IO APIC resources could be not be allocated.
May  8 07:58:40 tashtego kernel: [    2.774102] Using IPI No-Shortcut mode
May  8 07:58:40 tashtego kernel: [    2.774346] registered taskstats version 1
May  8 07:58:40 tashtego kernel: [    2.774533]   Magic number: 9:775:975
May  8 07:58:40 tashtego kernel: [    2.774677] button PNP0C0E:00: hash matches
May  8 07:58:40 tashtego kernel: [    2.774737] rtc_cmos 00:02: setting system clock to 2009-05-08 07:58:19 UTC (1241769499)
May  8 07:58:40 tashtego kernel: [    2.774744] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  8 07:58:40 tashtego kernel: [    2.774747] EDD information not available.
May  8 07:58:40 tashtego kernel: [    2.776562] Freeing unused kernel memory: 532k freed
May  8 07:58:40 tashtego kernel: [    2.776797] Write protecting the kernel text: 4128k
May  8 07:58:40 tashtego kernel: [    2.776867] Write protecting the kernel read-only data: 1532k
May  8 07:58:40 tashtego kernel: [    2.815467] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
May  8 07:58:40 tashtego kernel: [    2.840386] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
May  8 07:58:40 tashtego kernel: [    3.398231] Floppy drive(s): fd0 is 1.44M
May  8 07:58:40 tashtego kernel: [    3.415958] FDC 0 is a post-1991 82077
May  8 07:58:40 tashtego kernel: [    3.626577] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
May  8 07:58:40 tashtego kernel: [    3.626664] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
May  8 07:58:40 tashtego kernel: [    3.631998] 8139too Fast Ethernet driver 0.9.28
May  8 07:58:40 tashtego kernel: [    3.635864] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
May  8 07:58:40 tashtego kernel: [    3.637321] eth0: RealTek RTL8139 at 0x1400, 00:08:02:04:d9:a1, IRQ 11
May  8 07:58:40 tashtego kernel: [    3.637326] eth0:  Identified 8139 chip type 'RTL-8139C'
May  8 07:58:40 tashtego kernel: [    4.338934] Marking TSC unstable due to TSC halts in idle
May  8 07:58:40 tashtego kernel: [    4.403793] PM: Starting manual resume from disk
May  8 07:58:40 tashtego kernel: [    4.403804] PM: Resume from partition 8:5
May  8 07:58:40 tashtego kernel: [    4.403806] PM: Checking hibernation image.
May  8 07:58:40 tashtego kernel: [    4.404163] PM: Resume from disk failed.
May  8 07:58:40 tashtego kernel: [    4.409723] EXT3-fs: INFO: recovery required on readonly filesystem.
May  8 07:58:40 tashtego kernel: [    4.409733] EXT3-fs: write access will be enabled during recovery.
May  8 07:58:40 tashtego kernel: [    5.967256] kjournald starting.  Commit interval 5 seconds
May  8 07:58:40 tashtego kernel: [    5.967310] EXT3-fs: sda6: orphan cleanup on readonly fs
May  8 07:58:40 tashtego kernel: [    5.967327] ext3_orphan_cleanup: deleting unreferenced inode 106830
May  8 07:58:40 tashtego kernel: [    5.967445] EXT3-fs: sda6: 1 orphan inode deleted
May  8 07:58:40 tashtego kernel: [    5.967449] EXT3-fs: recovery complete.
May  8 07:58:40 tashtego kernel: [    6.040099] EXT3-fs: mounted filesystem with ordered data mode.
May  8 07:58:40 tashtego kernel: [   15.457357] udev: starting version 141
May  8 07:58:40 tashtego kernel: [   15.705425] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input6
May  8 07:58:40 tashtego kernel: [   15.737536] Linux agpgart interface v0.103
May  8 07:58:40 tashtego kernel: [   15.744541] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
May  8 07:58:40 tashtego kernel: [   15.775041] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
May  8 07:58:40 tashtego kernel: [   15.782757] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xec000000
May  8 07:58:40 tashtego kernel: [   15.789615] parport_pc: VIA 686A/8231 detected
May  8 07:58:40 tashtego kernel: [   15.789624] parport_pc: probing current configuration
May  8 07:58:40 tashtego kernel: [   15.789646] parport_pc: Current parallel port base: 0x378
May  8 07:58:40 tashtego kernel: [   15.789730] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
May  8 07:58:40 tashtego kernel: [   15.859950] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  8 07:58:40 tashtego kernel: [   15.884415] parport_pc: VIA parallel port: io=0x378, irq=7
May  8 07:58:40 tashtego kernel: [   16.095078] vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1
May  8 07:58:40 tashtego kernel: [   16.389416] yenta_cardbus 0000:00:0a.0: CardBus bridge found [0e11:b103]
May  8 07:58:40 tashtego kernel: [   16.389445] yenta_cardbus 0000:00:0a.0: Enabling burst memory read transactions
May  8 07:58:40 tashtego kernel: [   16.389452] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
May  8 07:58:40 tashtego kernel: [   16.389457] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
May  8 07:58:40 tashtego kernel: [   16.389464] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01001002, devctl 0x64
May  8 07:58:40 tashtego kernel: [   16.409063] input: PC Speaker as /devices/platform/pcspkr/input/input7
May  8 07:58:40 tashtego kernel: [   16.621133] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0018, PCI irq 11
May  8 07:58:40 tashtego kernel: [   16.621143] yenta_cardbus 0000:00:0a.0: Socket status: 30000010
May  8 07:58:40 tashtego kernel: [   16.989583] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
May  8 07:58:40 tashtego kernel: [   17.096812] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  8 07:58:40 tashtego kernel: [   17.272124] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
May  8 07:58:40 tashtego kernel: [   17.293200] ppdev: user-space parallel port driver
May  8 07:58:40 tashtego kernel: [   17.314550] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
May  8 07:58:40 tashtego kernel: [   17.314560] PCI: setting IRQ 5 as level-triggered
May  8 07:58:40 tashtego kernel: [   17.314570] VIA 82xx Audio 0000:00:07.5: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
May  8 07:58:40 tashtego kernel: [   17.314731] VIA 82xx Audio 0000:00:07.5: setting latency timer to 64
May  8 07:58:40 tashtego kernel: [   17.724896] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
May  8 07:58:40 tashtego kernel: [   17.727320] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
May  8 07:58:40 tashtego kernel: [   17.728405] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
May  8 07:58:40 tashtego kernel: [   17.729274] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
May  8 07:58:40 tashtego kernel: [   17.730429] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
May  8 07:58:40 tashtego kernel: [   17.731422] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
May  8 07:58:40 tashtego kernel: [   17.739027] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
May  8 07:58:40 tashtego kernel: [   17.861932] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
May  8 07:58:40 tashtego kernel: [   17.871059] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
May  8 07:58:40 tashtego kernel: [   18.127325] eth1: Hardware identity 800c:0000:0001:0000
May  8 07:58:40 tashtego kernel: [   18.127453] eth1: Station identity  001f:0009:0001:0004
May  8 07:58:40 tashtego kernel: [   18.127460] eth1: Firmware determined as Intersil 1.4.9
May  8 07:58:40 tashtego kernel: [   18.127465] eth1: Ad-hoc demo mode supported
May  8 07:58:40 tashtego kernel: [   18.127469] eth1: IEEE standard IBSS ad-hoc mode supported
May  8 07:58:40 tashtego kernel: [   18.127472] eth1: WEP supported, 104-bit key
May  8 07:58:40 tashtego kernel: [   18.158573] eth1: MAC address 00:0d:3a:23:1c:41
May  8 07:58:40 tashtego kernel: [   18.158672] eth1: Station name "Prism  I"
May  8 07:58:40 tashtego kernel: [   18.159313] eth1: ready
May  8 07:58:40 tashtego kernel: [   18.161273] eth1: orinoco_cs at 0.0, irq 3, io 0x0100-0x013f
May  8 07:58:40 tashtego kernel: [   18.265350] ieee80211_crypt: registered algorithm 'NULL'
May  8 07:58:40 tashtego kernel: [   18.268120] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9d48b1, caps: 0x904713/0x4006
May  8 07:58:40 tashtego kernel: [   18.349035] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
May  8 07:58:40 tashtego kernel: [   19.017575] lp0: using parport0 (interrupt-driven).
May  8 07:58:40 tashtego kernel: [   19.427565] Adding 650592k swap on /dev/sda5.  Priority:-1 extents:1 across:650592k
May  8 07:58:40 tashtego kernel: [   20.217512] EXT3 FS on sda6, internal journal
May  8 07:58:40 tashtego kernel: [   21.729242] type=1505 audit(1241783918.453:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2028
May  8 07:58:40 tashtego kernel: [   21.849592] type=1505 audit(1241783918.573:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2032
May  8 07:58:40 tashtego kernel: [   21.850216] type=1505 audit(1241783918.573:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2032
May  8 07:58:40 tashtego kernel: [   21.850377] type=1505 audit(1241783918.573:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2032
May  8 07:58:40 tashtego kernel: [   21.850530] type=1505 audit(1241783918.573:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2032
May  8 07:58:40 tashtego kernel: [   22.191635] type=1505 audit(1241783918.913:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2037
May  8 07:58:40 tashtego kernel: [   22.192517] type=1505 audit(1241783918.917:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2037
May  8 07:58:40 tashtego kernel: [   22.266940] type=1505 audit(1241783918.989:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2041
May  8 07:58:42 tashtego acpid: client connected from 2533[111:120] 
May  8 07:58:42 tashtego bluetoothd[2547]: Bluetooth daemon
May  8 07:58:42 tashtego bluetoothd[2547]: Starting SDP server
May  8 07:58:42 tashtego kernel: [   26.145530] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  8 07:58:42 tashtego kernel: [   26.145539] Bluetooth: BNEP filters: protocol multicast
May  8 07:58:42 tashtego bluetoothd[2547]: bridge pan0 created
May  8 07:58:42 tashtego bluetoothd[2547]: Registered interface org.bluez.Service on path /org/bluez/2547/any
May  8 07:58:42 tashtego kernel: [   26.190706] Bridge firewalling registered
May  8 07:58:42 tashtego bluetoothd[2547]: Starting experimental netlink support
May  8 07:58:42 tashtego bluetoothd[2547]: Failed to find Bluetooth netlink family
May  8 07:58:44 tashtego acpid: client connected from 2587[0:0] 
May  8 07:58:44 tashtego NetworkManager: <info>  starting... 
May  8 07:58:44 tashtego NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too') 
May  8 07:58:44 tashtego NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_08_02_04_d9_a1 
May  8 07:58:44 tashtego NetworkManager: <info>  (eth1): driver does not support SSID scans (scan_capa 0x00). 
May  8 07:58:44 tashtego NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'orinoco_cs') 
May  8 07:58:44 tashtego NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_0d_3a_23_1c_41 
May  8 07:58:44 tashtego NetworkManager: <info>  Trying to start the supplicant... 
May  8 07:58:44 tashtego NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 07:58:44 tashtego NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle 
May  8 07:58:44 tashtego avahi-daemon[2635]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
May  8 07:58:44 tashtego avahi-daemon[2635]: Successfully dropped root privileges.
May  8 07:58:44 tashtego avahi-daemon[2635]: avahi-daemon 0.6.23 starting up.
May  8 07:58:44 tashtego avahi-daemon[2635]: Successfully called chroot().
May  8 07:58:44 tashtego avahi-daemon[2635]: Successfully dropped remaining capabilities.
May  8 07:58:44 tashtego nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 07:58:44 tashtego nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 07:58:44 tashtego nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 07:58:44 tashtego nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_08_02_04_d9_a1, iface: eth0): not well known
May  8 07:58:44 tashtego nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_0d_3a_23_1c_41, iface: eth1): not well known
May  8 07:58:44 tashtego nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 07:58:44 tashtego avahi-daemon[2635]: No service file found in /etc/avahi/services.
May  8 07:58:44 tashtego avahi-daemon[2635]: Network interface enumeration completed.
May  8 07:58:44 tashtego avahi-daemon[2635]: Registering HINFO record with values 'I686'/'LINUX'.
May  8 07:58:44 tashtego avahi-daemon[2635]: Server startup complete. Host name is tashtego.local. Local service cookie is 916212141.
May  8 07:58:44 tashtego nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 07:58:44 tashtego nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 07:58:44 tashtego nm-system-settings:    SCPlugin-Ifupdown: (153368376) ... get_connections.
May  8 07:58:44 tashtego nm-system-settings:    SCPlugin-Ifupdown: (153368376) ... get_connections (managed=false): return empty list.
May  8 07:58:44 tashtego nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 07:58:46 tashtego anacron[2746]: Anacron 2.3 started on 2009-05-08
May  8 07:58:46 tashtego anacron[2746]: Normal exit (0 jobs run)
May  8 07:58:46 tashtego /usr/sbin/cron[2789]: (CRON) INFO (pidfile fd = 3)
May  8 07:58:46 tashtego /usr/sbin/cron[2790]: (CRON) STARTUP (fork ok)
May  8 07:58:46 tashtego /usr/sbin/cron[2790]: (CRON) INFO (Running @reboot jobs)
May  8 07:58:48 tashtego NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 07:58:48 tashtego NetworkManager: <info>  (eth0): bringing up device. 
May  8 07:58:48 tashtego NetworkManager: <info>  (eth0): preparing device. 
May  8 07:58:48 tashtego NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 07:58:48 tashtego NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 07:58:48 tashtego NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 07:58:48 tashtego NetworkManager: <info>  (eth1): device state change: 1 -> 2 
May  8 07:58:48 tashtego NetworkManager: <info>  (eth1): bringing up device. 
May  8 07:58:48 tashtego kernel: [   31.276838] eth0: link down
May  8 07:58:48 tashtego kernel: [   31.276957] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  8 07:58:48 tashtego kernel: [   31.319098] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  8 07:58:48 tashtego NetworkManager: <info>  (eth1): preparing device. 
May  8 07:58:48 tashtego NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
May  8 07:58:48 tashtego kernel: [   31.345550] eth1: New link status: Disconnected (0002)
May  8 07:58:48 tashtego NetworkManager: <info>  (eth1): device state change: 2 -> 3 
May  8 07:58:48 tashtego NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready 
May  8 07:58:49 tashtego nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_08_02_04_d9_a1
May  8 07:58:49 tashtego kernel: [   32.917202] eth1: New link status: Connected (0001)
May  8 07:58:49 tashtego kernel: [   32.917289] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May  8 07:58:50 tashtego avahi-daemon[2635]: Registering new address record for fe80::20d:3aff:fe23:1c41 on eth1.*.
May  8 07:58:59 tashtego kernel: [   43.000052] eth1: no IPv6 routers present
May  8 07:59:02 tashtego console-kit-daemon[2391]: WARNING: Couldn't read /proc/2390/environ: Failed to open file '/proc/2390/environ': No such file or directory 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) starting connection 'Auto docjp' 
May  8 07:59:16 tashtego NetworkManager: <info>  (eth1): device state change: 3 -> 4 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
May  8 07:59:16 tashtego NetworkManager: <info>  (eth1): device state change: 4 -> 5 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto docjp' has security, but secrets are required. 
May  8 07:59:16 tashtego NetworkManager: <info>  (eth1): device state change: 5 -> 6 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
May  8 07:59:16 tashtego NetworkManager: <info>  (eth1): device state change: 6 -> 4 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
May  8 07:59:16 tashtego NetworkManager: <info>  (eth1): device state change: 4 -> 5 
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto docjp' has security, and secrets exist.  No new secrets needed. 
May  8 07:59:16 tashtego NetworkManager: <info>  Config: added 'ssid' value 'docjp' 
May  8 07:59:16 tashtego NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
May  8 07:59:16 tashtego NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
May  8 07:59:16 tashtego NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
May  8 07:59:16 tashtego NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
May  8 07:59:16 tashtego NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
May  8 07:59:16 tashtego NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  8 07:59:16 tashtego NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  8 07:59:16 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
May  8 07:59:16 tashtego NetworkManager: <info>  Config: set interface ap_scan to 1 
May  8 07:59:16 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  inactive -> scanning 
May  8 07:59:16 tashtego anacron[3186]: Anacron 2.3 started on 2009-05-08
May  8 07:59:16 tashtego anacron[3186]: Normal exit (0 jobs run)
May  8 07:59:16 tashtego kernel: [   60.171205] eth1: New link status: Disconnected (0002)
May  8 07:59:16 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
May  8 07:59:17 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected 
May  8 07:59:17 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associated 
May  8 07:59:17 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed 
May  8 07:59:17 tashtego NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'docjp'. 
May  8 07:59:17 tashtego NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 07:59:17 tashtego NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
May  8 07:59:17 tashtego NetworkManager: <info>  (eth1): device state change: 5 -> 7 
May  8 07:59:17 tashtego NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
May  8 07:59:17 tashtego kernel: [   61.101578] eth1: New link status: Connected (0001)
May  8 07:59:17 tashtego NetworkManager: <info>  dhclient started with pid 3199 
May  8 07:59:17 tashtego NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
May  8 07:59:18 tashtego dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 07:59:18 tashtego dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 07:59:18 tashtego dhclient: All rights reserved.
May  8 07:59:18 tashtego dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 07:59:18 tashtego dhclient: 
May  8 07:59:18 tashtego NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit 
May  8 07:59:18 tashtego dhclient: Listening on LPF/eth1/00:0d:3a:23:1c:41
May  8 07:59:18 tashtego dhclient: Sending on   LPF/eth1/00:0d:3a:23:1c:41
May  8 07:59:18 tashtego dhclient: Sending on   Socket/fallback
May  8 07:59:22 tashtego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
May  8 07:59:23 tashtego kernel: [   66.816108] ------------[ cut here ]------------
May  8 07:59:23 tashtego kernel: [   66.816119] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x219/0x230()
May  8 07:59:23 tashtego kernel: [   66.816125] NETDEV WATCHDOG: eth1 (orinoco_cs): transmit timed out
May  8 07:59:23 tashtego kernel: [   66.816129] Modules linked in: binfmt_misc bridge stp bnep input_polldev lp hostap_cs joydev hostap ieee80211_crypt orinoco_cs orinoco hermes_dld hermes pcmcia snd_via82xx ppdev gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi psmouse snd_seq_midi_event serio_raw snd_seq snd_timer snd_seq_device snd pcspkr yenta_socket rsrc_nonstatic pcmcia_core soundcore via686a i2c_viapro shpchp parport_pc via_agp parport agpgart video output 8139too 8139cp mii floppy fbcon tileblit font bitblit softcursor
May  8 07:59:23 tashtego kernel: [   66.816208] Pid: 3207, comm: fast-user-switc Not tainted 2.6.28-11-generic #42-Ubuntu
May  8 07:59:23 tashtego kernel: [   66.816213] Call Trace:
May  8 07:59:23 tashtego kernel: [   66.816231]  [<c0139ab0>] warn_slowpath+0x60/0x80
May  8 07:59:23 tashtego kernel: [   66.816248]  [<c0420030>] ? regulator_suspend_standby_mode_show+0x30/0x40
May  8 07:59:23 tashtego kernel: [   66.816261]  [<c049f5a7>] ? unix_stream_recvmsg+0x227/0x490
May  8 07:59:23 tashtego kernel: [   66.816274]  [<c015828d>] ? clocksource_get_next+0x3d/0x50
May  8 07:59:23 tashtego kernel: [   66.816280]  [<c0156eb2>] ? update_wall_time+0x4c2/0x8e0
May  8 07:59:23 tashtego kernel: [   66.816286]  [<c01568f3>] ? getnstimeofday+0x53/0x110
May  8 07:59:23 tashtego kernel: [   66.816295]  [<c02cb03d>] ? strlcpy+0x1d/0x60
May  8 07:59:23 tashtego kernel: [   66.816306]  [<c04312f2>] ? netdev_drivername+0x32/0x40
May  8 07:59:23 tashtego kernel: [   66.816312]  [<c0445e49>] dev_watchdog+0x219/0x230
May  8 07:59:23 tashtego kernel: [   66.816321]  [<c015aee3>] ? tick_dev_program_event+0x33/0xc0
May  8 07:59:23 tashtego kernel: [   66.816332]  [<c0143b00>] run_timer_softirq+0x130/0x200
May  8 07:59:23 tashtego kernel: [   66.816337]  [<c0445c30>] ? dev_watchdog+0x0/0x230
May  8 07:59:23 tashtego kernel: [   66.816343]  [<c0445c30>] ? dev_watchdog+0x0/0x230
May  8 07:59:23 tashtego kernel: [   66.816352]  [<c013f197>] __do_softirq+0x97/0x170
May  8 07:59:23 tashtego kernel: [   66.816358]  [<c013f2cd>] do_softirq+0x5d/0x60
May  8 07:59:23 tashtego kernel: [   66.816364]  [<c013f445>] irq_exit+0x55/0x90
May  8 07:59:23 tashtego kernel: [   66.816374]  [<c0106853>] do_IRQ+0x83/0xa0
May  8 07:59:23 tashtego kernel: [   66.816379]  [<c01051f3>] common_interrupt+0x23/0x30
May  8 07:59:23 tashtego kernel: [   66.816383] ---[ end trace b8da3df604a510ec ]---
May  8 07:59:23 tashtego kernel: [   66.816393] eth1: Tx timeout! ALLOCFID=ffff, TXCOMPLFID=ffff, EVSTAT=8000
May  8 07:59:24 tashtego kernel: [   67.755167] eth1: New link status: Connected (0001)
May  8 07:59:24 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associated 
May  8 07:59:24 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed 
May  8 07:59:29 tashtego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
May  8 07:59:37 tashtego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
May  8 07:59:38 tashtego dhclient: DHCPOFFER of 192.168.1.102 from 192.168.1.1
May  8 07:59:38 tashtego dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
May  8 07:59:38 tashtego dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
May  8 07:59:38 tashtego NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
May  8 07:59:38 tashtego NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 07:59:38 tashtego NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
May  8 07:59:38 tashtego NetworkManager: <info>    address 192.168.1.102 
May  8 07:59:38 tashtego NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 07:59:38 tashtego NetworkManager: <info>    gateway 192.168.1.1 
May  8 07:59:38 tashtego NetworkManager: <info>    hostname 'tashtego' 
May  8 07:59:38 tashtego NetworkManager: <info>    nameserver '72.45.32.34' 
May  8 07:59:38 tashtego NetworkManager: <info>    nameserver '72.45.32.37' 
May  8 07:59:38 tashtego NetworkManager: <info>    domain name 'the-beach.net' 
May  8 07:59:38 tashtego NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 07:59:38 tashtego NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
May  8 07:59:38 tashtego NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
May  8 07:59:38 tashtego avahi-daemon[2635]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
May  8 07:59:38 tashtego avahi-daemon[2635]: New relevant interface eth1.IPv4 for mDNS.
May  8 07:59:38 tashtego avahi-daemon[2635]: Registering new address record for 192.168.1.102 on eth1.IPv4.
May  8 07:59:38 tashtego dhclient: bound to 192.168.1.102 -- renewal in 42536 seconds.
May  8 07:59:39 tashtego NetworkManager: <info>  (eth1): device state change: 7 -> 8 
May  8 07:59:39 tashtego NetworkManager: <info>  Policy set 'Auto docjp' (eth1) as default for routing and DNS. 
May  8 07:59:39 tashtego NetworkManager: <info>  Activation (eth1) successful, device activated. 
May  8 07:59:39 tashtego NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 07:59:48 tashtego kernel: [   91.836067] Clocksource tsc unstable (delta = -291653663 ns)
May  8 11:59:58 tashtego ntpdate[3291]: step time server 91.189.94.4 offset 14400.367497 sec
May  8 12:00:02 tashtego /USR/SBIN/CRON[3336]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
May  8 12:00:02 tashtego /USR/SBIN/CRON[3337]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  8 12:10:01 tashtego /USR/SBIN/CRON[3704]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  8 12:10:07 tashtego console-kit-daemon[2391]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 12:10:07 tashtego last message repeated 4 times
May  8 12:10:08 tashtego init: tty4 main process (2179) killed by TERM signal
May  8 12:10:08 tashtego init: tty5 main process (2180) killed by TERM signal
May  8 12:10:08 tashtego console-kit-daemon[2391]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 12:10:08 tashtego init: tty2 main process (2187) killed by TERM signal
May  8 12:10:08 tashtego init: tty3 main process (2188) killed by TERM signal
May  8 12:10:08 tashtego init: tty6 main process (2189) killed by TERM signal
May  8 12:10:08 tashtego init: tty1 main process (2889) killed by TERM signal
May  8 12:10:08 tashtego console-kit-daemon[2391]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 12:10:08 tashtego last message repeated 5 times
May  8 12:10:09 tashtego NetworkManager: <info>  (eth1): device state change: 8 -> 3 
May  8 12:10:09 tashtego NetworkManager: <info>  (eth1): deactivating device (reason: 38). 
May  8 12:10:09 tashtego NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 3199 
May  8 12:10:10 tashtego kernel: [  712.781667] eth1: New link status: Disconnected (0002)
May  8 12:10:10 tashtego NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
May  8 08:11:05 tashtego syslogd 1.5.0#5ubuntu3: restart.
May  8 08:11:06 tashtego kernel: Inspecting /boot/System.map-2.6.28-11-generic
May  8 08:11:06 tashtego kernel: Cannot find map file.
May  8 08:11:06 tashtego kernel: Loaded 54398 symbols from 56 modules.
May  8 08:11:06 tashtego kernel: [    0.000000] BIOS EBDA/lowmem at: 0009e800/0009e800
May  8 08:11:06 tashtego kernel: [    0.000000] Initializing cgroup subsys cpuset
May  8 08:11:06 tashtego kernel: [    0.000000] Initializing cgroup subsys cpu
May  8 08:11:06 tashtego kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
May  8 08:11:06 tashtego kernel: [    0.000000] KERNEL supported cpus:
May  8 08:11:06 tashtego kernel: [    0.000000]   Intel GenuineIntel
May  8 08:11:06 tashtego kernel: [    0.000000]   AMD AuthenticAMD
May  8 08:11:06 tashtego kernel: [    0.000000]   NSC Geode by NSC
May  8 08:11:06 tashtego kernel: [    0.000000]   Cyrix CyrixInstead
May  8 08:11:06 tashtego kernel: [    0.000000]   Centaur CentaurHauls
May  8 08:11:06 tashtego kernel: [    0.000000]   Transmeta GenuineTMx86
May  8 08:11:06 tashtego kernel: [    0.000000]   Transmeta TransmetaCPU
May  8 08:11:06 tashtego kernel: [    0.000000]   UMC UMC UMC UMC
May  8 08:11:06 tashtego kernel: [    0.000000] BIOS-provided physical RAM map:
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000def0000 (usable)
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 000000000def0000 - 000000000deff000 (ACPI data)
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 000000000deff000 - 000000000df00000 (ACPI NVS)
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 000000000df00000 - 000000000e000000 (usable)
May  8 08:11:06 tashtego kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000] DMI 2.3 present.
May  8 08:11:06 tashtego kernel: [    0.000000] last_pfn = 0xe000 max_arch_pfn = 0x100000
May  8 08:11:06 tashtego kernel: [    0.000000] Scanning 2 areas for low memory corruption
May  8 08:11:06 tashtego kernel: [    0.000000] modified physical RAM map:
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 0000000000010000 - 0000000000091800 (usable)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 00000000000c0000 - 00000000000cc000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 0000000000100000 - 000000000def0000 (usable)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 000000000def0000 - 000000000deff000 (ACPI data)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 000000000deff000 - 000000000df00000 (ACPI NVS)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 000000000df00000 - 000000000e000000 (usable)
May  8 08:11:06 tashtego kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
May  8 08:11:06 tashtego kernel: [    0.000000] kernel direct mapping tables up to e000000 @ 10000-15000
May  8 08:11:06 tashtego kernel: [    0.000000] RAMDISK: 0d7ad000 - 0dedfd0f
May  8 08:11:06 tashtego kernel: [    0.000000] ACPI: RSDP 000F6DC0, 0014 (r0 PTLTD )
May  8 08:11:06 tashtego kernel: [    0.000000] ACPI: RSDT 0DEFB61A, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
May  8 08:11:06 tashtego kernel: [    0.000000] ACPI: FACP 0DEFEE95, 0074 (r1 COMPAQ  EAGLES   6040000 PTL_    F4240)
May  8 08:11:06 tashtego kernel: [    0.000000] ACPI: DSDT 0DEFB646, 384F (r1 COMAPQ   EAGLES  6040000 MSFT  100000D)
May  8 08:11:06 tashtego kernel: [    0.000000] ACPI: FACS 0DEFFFC0, 0040
May  8 08:11:06 tashtego kernel: [    0.000000] ACPI: SSDT 0DEFEF09, 00F7 (r1 PTLTD  POWERNOW  6040000  LTP        1)
May  8 08:11:06 tashtego kernel: [    0.000000] 0MB HIGHMEM available.
May  8 08:11:06 tashtego kernel: [    0.000000] 224MB LOWMEM available.
May  8 08:11:06 tashtego kernel: [    0.000000]   mapped low ram: 0 - 0e000000
May  8 08:11:06 tashtego kernel: [    0.000000]   low ram: 00000000 - 0e000000
May  8 08:11:06 tashtego kernel: [    0.000000]   bootmap 00011000 - 00012c00
May  8 08:11:06 tashtego kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000e000000]
May  8 08:11:06 tashtego kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  8 08:11:06 tashtego kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  8 08:11:06 tashtego kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  8 08:11:06 tashtego kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
May  8 08:11:06 tashtego kernel: [    0.000000]   #4 [000d7ad000 - 000dedfd0f]          RAMDISK ==> [000d7ad000 - 000dedfd0f]
May  8 08:11:06 tashtego kernel: [    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
May  8 08:11:06 tashtego kernel: [    0.000000]   #6 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
May  8 08:11:06 tashtego kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
May  8 08:11:06 tashtego kernel: [    0.000000]   #8 [0000011000 - 0000013000]          BOOTMAP ==> [0000011000 - 0000013000]
May  8 08:11:06 tashtego kernel: [    0.000000] Zone PFN ranges:
May  8 08:11:06 tashtego kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  8 08:11:06 tashtego kernel: [    0.000000]   Normal   0x00001000 -> 0x0000e000
May  8 08:11:06 tashtego kernel: [    0.000000]   HighMem  0x0000e000 -> 0x0000e000
May  8 08:11:06 tashtego kernel: [    0.000000] Movable zone start PFN for each node
May  8 08:11:06 tashtego kernel: [    0.000000] early_node_map[5] active PFN ranges
May  8 08:11:06 tashtego kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
May  8 08:11:06 tashtego kernel: [    0.000000]     0: 0x00000006 -> 0x00000007
May  8 08:11:06 tashtego kernel: [    0.000000]     0: 0x00000010 -> 0x00000091
May  8 08:11:06 tashtego kernel: [    0.000000]     0: 0x00000100 -> 0x0000def0
May  8 08:11:06 tashtego kernel: [    0.000000]     0: 0x0000df00 -> 0x0000e000
May  8 08:11:06 tashtego kernel: [    0.000000] On node 0 totalpages: 57204
May  8 08:11:06 tashtego kernel: [    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
May  8 08:11:06 tashtego kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May  8 08:11:06 tashtego kernel: [    0.000000]   DMA zone: 0 pages reserved
May  8 08:11:06 tashtego kernel: [    0.000000]   DMA zone: 3940 pages, LIFO batch:0
May  8 08:11:06 tashtego kernel: [    0.000000]   Normal zone: 416 pages used for memmap
May  8 08:11:06 tashtego kernel: [    0.000000]   Normal zone: 52816 pages, LIFO batch:15
May  8 08:11:06 tashtego kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
May  8 08:11:06 tashtego kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May  8 08:11:06 tashtego kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
May  8 08:11:06 tashtego kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
May  8 08:11:06 tashtego kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009f000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000c0000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000c0000 - 00000000000cc000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000cc000 - 00000000000dc000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000def0000 - 000000000deff000
May  8 08:11:06 tashtego kernel: [    0.000000] PM: Registered nosave memory: 000000000deff000 - 000000000df00000
May  8 08:11:06 tashtego kernel: [    0.000000] Allocating PCI resources starting at 10000000 (gap: e000000:f1f80000)
May  8 08:11:06 tashtego kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
May  8 08:11:06 tashtego kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
May  8 08:11:06 tashtego kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 56756
May  8 08:11:06 tashtego kernel: [    0.000000] Kernel command line: root=UUID=56b02b03-88d9-4fa8-8657-89aa5bc2bd22 ro xforcevesa quiet splash 
May  8 08:11:06 tashtego kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  8 08:11:06 tashtego kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  8 08:11:06 tashtego kernel: [    0.000000] Initializing CPU#0
May  8 08:11:06 tashtego kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
May  8 08:11:06 tashtego kernel: [    0.000000] Fast TSC calibration using PIT
May  8 08:11:06 tashtego kernel: [    0.000000] Detected 1195.685 MHz processor.
May  8 08:11:06 tashtego kernel: [    0.004000] Console: colour VGA+ 80x25
May  8 08:11:06 tashtego kernel: [    0.004000] console [tty0] enabled
May  8 08:11:06 tashtego kernel: [    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
May  8 08:11:06 tashtego kernel: [    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
May  8 08:11:06 tashtego kernel: [    0.004000] allocated 1146880 bytes of page_cgroup
May  8 08:11:06 tashtego kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
May  8 08:11:06 tashtego kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
May  8 08:11:06 tashtego kernel: [    0.004000] Memory: 210280k/229376k available (4126k kernel code, 18260k reserved, 2208k data, 532k init, 0k highmem)
May  8 08:11:06 tashtego kernel: [    0.004000] virtual kernel memory layout:
May  8 08:11:06 tashtego kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
May  8 08:11:06 tashtego kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
May  8 08:11:06 tashtego kernel: [    0.004000]     vmalloc : 0xce800000 - 0xff3fe000   ( 779 MB)
May  8 08:11:06 tashtego kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xce000000   ( 224 MB)
May  8 08:11:06 tashtego kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
May  8 08:11:06 tashtego kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
May  8 08:11:06 tashtego kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
May  8 08:11:06 tashtego kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  8 08:11:06 tashtego kernel: [    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
May  8 08:11:06 tashtego kernel: [    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 2391.37 BogoMIPS (lpj=4782740)
May  8 08:11:06 tashtego kernel: [    0.004064] Security Framework initialized
May  8 08:11:06 tashtego kernel: [    0.004079] SELinux:  Disabled at boot.
May  8 08:11:06 tashtego kernel: [    0.004133] AppArmor: AppArmor initialized
May  8 08:11:06 tashtego kernel: [    0.004151] Mount-cache hash table entries: 512
May  8 08:11:06 tashtego kernel: [    0.004428] Initializing cgroup subsys ns
May  8 08:11:06 tashtego kernel: [    0.004436] Initializing cgroup subsys cpuacct
May  8 08:11:06 tashtego kernel: [    0.004441] Initializing cgroup subsys memory
May  8 08:11:06 tashtego kernel: [    0.004450] Initializing cgroup subsys freezer
May  8 08:11:06 tashtego kernel: [    0.004474] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  8 08:11:06 tashtego kernel: [    0.004479] CPU: L2 Cache: 256K (64 bytes/line)
May  8 08:11:06 tashtego kernel: [    0.004509] Checking 'hlt' instruction... OK.
May  8 08:11:06 tashtego kernel: [    0.020783] SMP alternatives: switching to UP code
May  8 08:11:06 tashtego kernel: [    0.276829] Freeing SMP alternatives: 18k freed
May  8 08:11:06 tashtego kernel: [    0.276841] ACPI: Core revision 20080926
May  8 08:11:06 tashtego kernel: [    0.280420] ACPI: Checking initramfs for custom DSDT
May  8 08:11:06 tashtego kernel: [    0.770575] ACPI: setting ELCR to 0400 (from 0a30)
May  8 08:11:06 tashtego kernel: [    0.772160] weird, boot CPU (#0) not listedby the BIOS.
May  8 08:11:06 tashtego kernel: [    0.772165] SMP motherboard not detected.
May  8 08:11:06 tashtego kernel: [    0.772170] Local APIC not detected. Using dummy APIC emulation.
May  8 08:11:06 tashtego kernel: [    0.772174] SMP disabled
May  8 08:11:06 tashtego kernel: [    0.772892] Brought up 1 CPUs
May  8 08:11:06 tashtego kernel: [    0.772899] Total of 1 processors activated (2391.37 BogoMIPS).
May  8 08:11:06 tashtego kernel: [    0.772933] CPU0 attaching NULL sched-domain.
May  8 08:11:06 tashtego kernel: [    0.776774] net_namespace: 776 bytes
May  8 08:11:06 tashtego kernel: [    0.776799] Booting paravirtualized kernel on bare hardware
May  8 08:11:06 tashtego kernel: [    0.777280] Time:  8:10:43  Date: 05/08/09
May  8 08:11:06 tashtego kernel: [    0.777293] regulator: core version 0.5
May  8 08:11:06 tashtego kernel: [    0.777396] NET: Registered protocol family 16
May  8 08:11:06 tashtego kernel: [    0.777698] EISA bus registered
May  8 08:11:06 tashtego kernel: [    0.777733] ACPI: bus type pci registered
May  8 08:11:06 tashtego kernel: [    0.778155] PCI: PCI BIOS revision 2.10 entry at 0xfd7ae, last bus=1
May  8 08:11:06 tashtego kernel: [    0.778160] PCI: Using configuration type 1 for base access
May  8 08:11:06 tashtego kernel: [    0.780742] ACPI: EC: Look up EC in DSDT
May  8 08:11:06 tashtego kernel: [    0.785822] ACPI: Interpreter enabled
May  8 08:11:06 tashtego kernel: [    0.785829] ACPI: (supports S0 S3 S4 S5)
May  8 08:11:06 tashtego kernel: [    0.785857] ACPI: Using PIC for interrupt routing
May  8 08:11:06 tashtego kernel: [    0.786499] ACPI: EC: non-query interrupt received, switching to interrupt mode
May  8 08:11:06 tashtego kernel: [    0.792455] ACPI: EC: GPE = 0x6, I/O: command/status = 0x66, data = 0x62
May  8 08:11:06 tashtego kernel: [    0.792460] ACPI: EC: driver started in interrupt mode
May  8 08:11:06 tashtego kernel: [    0.792616] ACPI: No dock devices found.
May  8 08:11:06 tashtego kernel: [    0.792634] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  8 08:11:06 tashtego kernel: [    0.792718] pci 0000:00:00.0: reg 10 32bit mmio: [0xec000000-0xefffffff]
May  8 08:11:06 tashtego kernel: [    0.792751] pci 0000:00:00.0: Disabling VIA memory write queue (PCI ID 0305, rev 80): [55] 3c & 1f -> 1c
May  8 08:11:06 tashtego kernel: [    0.792797] pci 0000:00:01.0: supports D1
May  8 08:11:06 tashtego kernel: [    0.792904] pci 0000:00:07.1: reg 20 io port: [0x1840-0x184f]
May  8 08:11:06 tashtego kernel: [    0.792965] pci 0000:00:07.2: reg 20 io port: [0x1800-0x181f]
May  8 08:11:06 tashtego kernel: [    0.793045] pci 0000:00:07.4: quirk: region 8100-810f claimed by vt82c686 SMB
May  8 08:11:06 tashtego kernel: [    0.793086] pci 0000:00:07.5: reg 10 io port: [0x1000-0x10ff]
May  8 08:11:06 tashtego kernel: [    0.793094] pci 0000:00:07.5: reg 14 io port: [0x1854-0x1857]
May  8 08:11:06 tashtego kernel: [    0.793102] pci 0000:00:07.5: reg 18 io port: [0x1850-0x1853]
May  8 08:11:06 tashtego kernel: [    0.793158] pci 0000:00:09.0: reg 10 32bit mmio: [0xe8000000-0xe800ffff]
May  8 08:11:06 tashtego kernel: [    0.793166] pci 0000:00:09.0: reg 14 io port: [0x1858-0x185f]
May  8 08:11:06 tashtego kernel: [    0.793194] pci 0000:00:09.0: PME# supported from D3hot
May  8 08:11:06 tashtego kernel: [    0.793200] pci 0000:00:09.0: PME# disabled
May  8 08:11:06 tashtego kernel: [    0.793233] pci 0000:00:0a.0: reg 10 32bit mmio: [0xffbfe000-0xffbfefff]
May  8 08:11:06 tashtego kernel: [    0.793244] pci 0000:00:0a.0: supports D1 D2
May  8 08:11:06 tashtego kernel: [    0.793247] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
May  8 08:11:06 tashtego kernel: [    0.793253] pci 0000:00:0a.0: PME# disabled
May  8 08:11:06 tashtego kernel: [    0.793285] pci 0000:00:0b.0: reg 10 io port: [0x1400-0x14ff]
May  8 08:11:06 tashtego kernel: [    0.793294] pci 0000:00:0b.0: reg 14 32bit mmio: [0xe8010000-0xe80100ff]
May  8 08:11:06 tashtego kernel: [    0.793322] pci 0000:00:0b.0: supports D1 D2
May  8 08:11:06 tashtego kernel: [    0.793326] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
May  8 08:11:06 tashtego kernel: [    0.793331] pci 0000:00:0b.0: PME# disabled
May  8 08:11:06 tashtego kernel: [    0.793393] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8100000-0xe817ffff]
May  8 08:11:06 tashtego kernel: [    0.793402] pci 0000:01:00.0: reg 14 32bit mmio: [0xf0000000-0xf7ffffff]
May  8 08:11:06 tashtego kernel: [    0.793424] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
May  8 08:11:06 tashtego kernel: [    0.793434] pci 0000:01:00.0: supports D1 D2
May  8 08:11:06 tashtego kernel: [    0.793474] pci 0000:00:01.0: bridge 32bit mmio: [0xe8100000-0xe81fffff]
May  8 08:11:06 tashtego kernel: [    0.793481] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf7ffffff]
May  8 08:11:06 tashtego kernel: [    0.793509] bus 00 -> node 0
May  8 08:11:06 tashtego kernel: [    0.793519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May  8 08:11:06 tashtego kernel: [    0.797738] ACPI: PCI Interrupt Link [LNKA] (IRQs *4)
May  8 08:11:06 tashtego kernel: [    0.797985] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
May  8 08:11:06 tashtego kernel: [    0.798221] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
May  8 08:11:06 tashtego kernel: [    0.798471] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
May  8 08:11:06 tashtego kernel: [    0.798694] ACPI: WMI: Mapper loaded
May  8 08:11:06 tashtego kernel: [    0.799229] SCSI subsystem initialized
May  8 08:11:06 tashtego kernel: [    0.799341] libata version 3.00 loaded.
May  8 08:11:06 tashtego kernel: [    0.799494] usbcore: registered new interface driver usbfs
May  8 08:11:06 tashtego kernel: [    0.799532] usbcore: registered new interface driver hub
May  8 08:11:06 tashtego kernel: [    0.799598] usbcore: registered new device driver usb
May  8 08:11:06 tashtego kernel: [    0.799855] PCI: Using ACPI for IRQ routing
May  8 08:11:06 tashtego kernel: [    0.800039] Bluetooth: Core ver 2.13
May  8 08:11:06 tashtego kernel: [    0.800139] NET: Registered protocol family 31
May  8 08:11:06 tashtego kernel: [    0.800143] Bluetooth: HCI device and connection manager initialized
May  8 08:11:06 tashtego kernel: [    0.800152] Bluetooth: HCI socket layer initialized
May  8 08:11:06 tashtego kernel: [    0.800157] NET: Registered protocol family 8
May  8 08:11:06 tashtego kernel: [    0.800160] NET: Registered protocol family 20
May  8 08:11:06 tashtego kernel: [    0.800181] NetLabel: Initializing
May  8 08:11:06 tashtego kernel: [    0.800185] NetLabel:  domain hash size = 128
May  8 08:11:06 tashtego kernel: [    0.800187] NetLabel:  protocols = UNLABELED CIPSOv4
May  8 08:11:06 tashtego kernel: [    0.800223] NetLabel:  unlabeled traffic allowed by default
May  8 08:11:06 tashtego kernel: [    0.800448] AppArmor: AppArmor Filesystem Enabled
May  8 08:11:06 tashtego kernel: [    0.800467] pnp: PnP ACPI init
May  8 08:11:06 tashtego kernel: [    0.800467] ACPI: bus type pnp registered
May  8 08:11:06 tashtego kernel: [    0.805048] pnp: PnP ACPI: found 11 devices
May  8 08:11:06 tashtego kernel: [    0.805052] ACPI: ACPI bus type pnp unregistered
May  8 08:11:06 tashtego kernel: [    0.805060] PnPBIOS: Disabled by ACPI PNP
May  8 08:11:06 tashtego kernel: [    0.805083] system 00:05: iomem range 0x0-0x9ffff could not be reserved
May  8 08:11:06 tashtego kernel: [    0.805090] system 00:05: iomem range 0xdc000-0xdffff could not be reserved
May  8 08:11:06 tashtego kernel: [    0.805095] system 00:05: iomem range 0x7000000-0x7ffffff could not be reserved
May  8 08:11:06 tashtego kernel: [    0.805106] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
May  8 08:11:06 tashtego kernel: [    0.839984] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
May  8 08:11:06 tashtego kernel: [    0.839988] pci 0000:00:01.0:   IO window: disabled
May  8 08:11:06 tashtego kernel: [    0.839996] pci 0000:00:01.0:   MEM window: 0xe8100000-0xe81fffff
May  8 08:11:06 tashtego kernel: [    0.840015] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
May  8 08:11:06 tashtego kernel: [    0.840023] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
May  8 08:11:06 tashtego kernel: [    0.840028] pci 0000:00:0a.0:   IO window: 0x001c00-0x001cff
May  8 08:11:06 tashtego kernel: [    0.840034] pci 0000:00:0a.0:   IO window: 0x002000-0x0020ff
May  8 08:11:06 tashtego kernel: [    0.840040] pci 0000:00:0a.0:   PREFETCH window: 0x10000000-0x13ffffff
May  8 08:11:06 tashtego kernel: [    0.840046] pci 0000:00:0a.0:   MEM window: 0x14000000-0x17ffffff
May  8 08:11:06 tashtego kernel: [    0.840065] pci 0000:00:01.0: setting latency timer to 64
May  8 08:11:06 tashtego kernel: [    0.840142] pci 0000:00:0a.0: power state changed by ACPI to D0
May  8 08:11:06 tashtego kernel: [    0.840545] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
May  8 08:11:06 tashtego kernel: [    0.840550] PCI: setting IRQ 11 as level-triggered
May  8 08:11:06 tashtego kernel: [    0.840560] pci 0000:00:0a.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
May  8 08:11:06 tashtego kernel: [    0.840571] bus: 00 index 0 io port: [0x00-0xffff]
May  8 08:11:06 tashtego kernel: [    0.840574] bus: 00 index 1 mmio: [0x000000-0xffffffff]
May  8 08:11:06 tashtego kernel: [    0.840578] bus: 01 index 0 mmio: [0x0-0x0]
May  8 08:11:06 tashtego kernel: [    0.840582] bus: 01 index 1 mmio: [0xe8100000-0xe81fffff]
May  8 08:11:06 tashtego kernel: [    0.840585] bus: 01 index 2 mmio: [0xf0000000-0xf7ffffff]
May  8 08:11:06 tashtego kernel: [    0.840589] bus: 01 index 3 mmio: [0x0-0x0]
May  8 08:11:06 tashtego kernel: [    0.840592] bus: 02 index 0 io port: [0x1c00-0x1cff]
May  8 08:11:06 tashtego kernel: [    0.840596] bus: 02 index 1 io port: [0x2000-0x20ff]
May  8 08:11:06 tashtego kernel: [    0.840600] bus: 02 index 2 mmio: [0x10000000-0x13ffffff]
May  8 08:11:06 tashtego kernel: [    0.840603] bus: 02 index 3 mmio: [0x14000000-0x17ffffff]
May  8 08:11:06 tashtego kernel: [    0.840634] NET: Registered protocol family 2
May  8 08:11:06 tashtego kernel: [    0.840886] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
May  8 08:11:06 tashtego kernel: [    0.841393] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
May  8 08:11:06 tashtego kernel: [    0.841623] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
May  8 08:11:06 tashtego kernel: [    0.841832] TCP: Hash tables configured (established 8192 bind 8192)
May  8 08:11:06 tashtego kernel: [    0.841837] TCP reno registered
May  8 08:11:06 tashtego kernel: [    0.841980] NET: Registered protocol family 1
May  8 08:11:06 tashtego kernel: [    0.842282] checking if image is initramfs... it is
May  8 08:11:06 tashtego kernel: [    1.340149] Switched to high resolution mode on CPU 0
May  8 08:11:06 tashtego kernel: [    1.945135] Freeing initrd memory: 7371k freed
May  8 08:11:06 tashtego kernel: [    1.945406] cpufreq: No nForce2 chipset.
May  8 08:11:06 tashtego kernel: [    1.945723] audit: initializing netlink socket (disabled)
May  8 08:11:06 tashtego kernel: [    1.945783] type=2000 audit(1241770242.944:1): initialized
May  8 08:11:06 tashtego kernel: [    1.958992] HugeTLB registered 4 MB page size, pre-allocated 0 pages
May  8 08:11:06 tashtego kernel: [    1.961441] VFS: Disk quotas dquot_6.5.1
May  8 08:11:06 tashtego kernel: [    1.961550] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  8 08:11:06 tashtego kernel: [    1.962692] fuse init (API version 7.10)
May  8 08:11:06 tashtego kernel: [    1.962859] msgmni has been set to 425
May  8 08:11:06 tashtego kernel: [    1.963305] alg: No test for stdrng (krng)
May  8 08:11:06 tashtego kernel: [    1.963333] io scheduler noop registered
May  8 08:11:06 tashtego kernel: [    1.963337] io scheduler anticipatory registered
May  8 08:11:06 tashtego kernel: [    1.963340] io scheduler deadline registered
May  8 08:11:06 tashtego kernel: [    1.963370] io scheduler cfq registered (default)
May  8 08:11:06 tashtego kernel: [    1.963413] pci 0000:00:00.0: Applying VIA southbridge workaround
May  8 08:11:06 tashtego kernel: [    1.963421] PCI: VIA PCI bridge detected.Disabling DAC.
May  8 08:11:06 tashtego kernel: [    1.963428] pci 0000:00:07.0: Disabling VIA external APIC routing
May  8 08:11:06 tashtego kernel: [    1.963469] pci 0000:01:00.0: Boot video device
May  8 08:11:06 tashtego kernel: [    1.968706] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  8 08:11:06 tashtego kernel: [    1.968725] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  8 08:11:06 tashtego kernel: [    1.969446] ACPI: AC Adapter [AC] (on-line)
May  8 08:11:06 tashtego kernel: [    1.983098] ACPI: Battery Slot [BAT0] (battery present)
May  8 08:11:06 tashtego kernel: [    1.983256] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
May  8 08:11:06 tashtego kernel: [    1.983262] ACPI: Power Button (FF) [PWRF]
May  8 08:11:06 tashtego kernel: [    1.983345] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
May  8 08:11:06 tashtego kernel: [    1.983355] ACPI: Sleep Button (CM) [SLPB]
May  8 08:11:06 tashtego kernel: [    1.983430] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
May  8 08:11:06 tashtego kernel: [    1.983436] ACPI: Power Button (CM) [PWRB]
May  8 08:11:06 tashtego kernel: [    1.983528] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
May  8 08:11:06 tashtego kernel: [    1.988830] ACPI: Lid Switch [LID]
May  8 08:11:06 tashtego kernel: [    1.989127] ACPI: CPU0 (power states: C1[C1] C2[C2])
May  8 08:11:06 tashtego kernel: [    1.989177] processor ACPI_CPU:00: registered as cooling_device0
May  8 08:11:06 tashtego kernel: [    1.989184] ACPI: Processor [CPU0] (supports 16 throttling states)
May  8 08:11:06 tashtego kernel: [    1.992048] isapnp: Scanning for PnP cards...
May  8 08:11:06 tashtego kernel: [    2.346230] isapnp: No Plug & Play device found
May  8 08:11:06 tashtego kernel: [    2.348573] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  8 08:11:06 tashtego kernel: [    2.350463] brd: module loaded
May  8 08:11:06 tashtego kernel: [    2.351101] loop: module loaded
May  8 08:11:06 tashtego kernel: [    2.351341] Fixed MDIO Bus: probed
May  8 08:11:06 tashtego kernel: [    2.351356] PPP generic driver version 2.4.2
May  8 08:11:06 tashtego kernel: [    2.351493] input: Macintosh mouse button emulation as /devices/virtual/input/input4
May  8 08:11:06 tashtego kernel: [    2.351564] Driver 'sd' needs updating - please use bus_type methods
May  8 08:11:06 tashtego kernel: [    2.351584] Driver 'sr' needs updating - please use bus_type methods
May  8 08:11:06 tashtego kernel: [    2.352582] pata_via 0000:00:07.1: version 0.3.3
May  8 08:11:06 tashtego kernel: [    2.353109] scsi0 : pata_via
May  8 08:11:06 tashtego kernel: [    2.353781] scsi1 : pata_via
May  8 08:11:06 tashtego kernel: [    2.354874] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1840 irq 14
May  8 08:11:06 tashtego kernel: [    2.354880] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1848 irq 15
May  8 08:11:06 tashtego kernel: [    2.516515] ata1.00: ATA-5: HITACHI_DK23CA-20, 00H1A0J1, max UDMA/100
May  8 08:11:06 tashtego kernel: [    2.516521] ata1.00: 39070080 sectors, multi 16: LBA 
May  8 08:11:06 tashtego kernel: [    2.532505] ata1.00: configured for UDMA/100
May  8 08:11:06 tashtego kernel: [    2.696437] ata2.00: ATAPI: SD-R2102, 1A15, max MWDMA2
May  8 08:11:06 tashtego kernel: [    2.712455] ata2.00: configured for MWDMA2
May  8 08:11:06 tashtego kernel: [    2.713439] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23CA-2 00H1 PQ: 0 ANSI: 5
May  8 08:11:06 tashtego kernel: [    2.713661] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
May  8 08:11:06 tashtego kernel: [    2.713699] sd 0:0:0:0: [sda] Write Protect is off
May  8 08:11:06 tashtego kernel: [    2.713705] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  8 08:11:06 tashtego kernel: [    2.713759] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 08:11:06 tashtego kernel: [    2.713950] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
May  8 08:11:06 tashtego kernel: [    2.713981] sd 0:0:0:0: [sda] Write Protect is off
May  8 08:11:06 tashtego kernel: [    2.713986] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  8 08:11:06 tashtego kernel: [    2.714038] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 08:11:06 tashtego kernel: [    2.714047]  sda: sda1 sda2 < sda5 sda6 >
May  8 08:11:06 tashtego kernel: [    2.747079] sd 0:0:0:0: [sda] Attached SCSI disk
May  8 08:11:06 tashtego kernel: [    2.747200] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  8 08:11:06 tashtego kernel: [    2.749753] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2102 1A15 PQ: 0 ANSI: 5
May  8 08:11:06 tashtego kernel: [    2.756694] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
May  8 08:11:06 tashtego kernel: [    2.756701] Uniform CD-ROM driver Revision: 3.20
May  8 08:11:06 tashtego kernel: [    2.756896] sr 1:0:0:0: Attached scsi CD-ROM sr0
May  8 08:11:06 tashtego kernel: [    2.756968] sr 1:0:0:0: Attached scsi generic sg1 type 5
May  8 08:11:06 tashtego kernel: [    2.757256] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  8 08:11:06 tashtego kernel: [    2.757287] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  8 08:11:06 tashtego kernel: [    2.757309] uhci_hcd: USB Universal Host Controller Interface driver
May  8 08:11:06 tashtego kernel: [    2.757867] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
May  8 08:11:06 tashtego kernel: [    2.757874] PCI: setting IRQ 9 as level-triggered
May  8 08:11:06 tashtego kernel: [    2.757884] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
May  8 08:11:06 tashtego kernel: [    2.757902] uhci_hcd 0000:00:07.2: UHCI Host Controller
May  8 08:11:06 tashtego kernel: [    2.758053] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
May  8 08:11:06 tashtego kernel: [    2.758093] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001800
May  8 08:11:06 tashtego kernel: [    2.758289] usb usb1: configuration #1 chosen from 1 choice
May  8 08:11:06 tashtego kernel: [    2.758343] hub 1-0:1.0: USB hub found
May  8 08:11:06 tashtego kernel: [    2.758368] hub 1-0:1.0: 2 ports detected
May  8 08:11:06 tashtego kernel: [    2.758606] usbcore: registered new interface driver libusual
May  8 08:11:06 tashtego kernel: [    2.758674] usbcore: registered new interface driver usbserial
May  8 08:11:06 tashtego kernel: [    2.758698] USB Serial support registered for generic
May  8 08:11:06 tashtego kernel: [    2.758722] usbcore: registered new interface driver usbserial_generic
May  8 08:11:06 tashtego kernel: [    2.758727] usbserial: USB Serial Driver core
May  8 08:11:06 tashtego kernel: [    2.758816] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May  8 08:11:06 tashtego kernel: [    2.760766] serio: i8042 KBD port at 0x60,0x64 irq 1
May  8 08:11:06 tashtego kernel: [    2.760781] serio: i8042 AUX port at 0x60,0x64 irq 12
May  8 08:11:06 tashtego kernel: [    2.761034] mice: PS/2 mouse device common for all mice
May  8 08:11:06 tashtego kernel: [    2.761448] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
May  8 08:11:06 tashtego kernel: [    2.761482] rtc0: alarms up to one year, y3k, 242 bytes nvram
May  8 08:11:06 tashtego kernel: [    2.761653] device-mapper: uevent: version 1.0.3
May  8 08:11:06 tashtego kernel: [    2.761906] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
May  8 08:11:06 tashtego kernel: [    2.762047] device-mapper: multipath: version 1.0.5 loaded
May  8 08:11:06 tashtego kernel: [    2.762053] device-mapper: multipath round-robin: version 1.0.0 loaded
May  8 08:11:06 tashtego kernel: [    2.762235] EISA: Probing bus 0 at eisa.0
May  8 08:11:06 tashtego kernel: [    2.762251] Cannot allocate resource for EISA slot 1
May  8 08:11:06 tashtego kernel: [    2.762256] Cannot allocate resource for EISA slot 2
May  8 08:11:06 tashtego kernel: [    2.762285] Cannot allocate resource for EISA slot 8
May  8 08:11:06 tashtego kernel: [    2.762288] EISA: Detected 0 cards.
May  8 08:11:06 tashtego kernel: [    2.762406] cpuidle: using governor ladder
May  8 08:11:06 tashtego kernel: [    2.762483] cpuidle: using governor menu
May  8 08:11:06 tashtego kernel: [    2.763451] TCP cubic registered
May  8 08:11:06 tashtego kernel: [    2.763624] NET: Registered protocol family 10
May  8 08:11:06 tashtego kernel: [    2.764461] lo: Disabled Privacy Extensions
May  8 08:11:06 tashtego kernel: [    2.765050] NET: Registered protocol family 17
May  8 08:11:06 tashtego kernel: [    2.765093] Bluetooth: L2CAP ver 2.11
May  8 08:11:06 tashtego kernel: [    2.765096] Bluetooth: L2CAP socket layer initialized
May  8 08:11:06 tashtego kernel: [    2.765102] Bluetooth: SCO (Voice Link) ver 0.6
May  8 08:11:06 tashtego kernel: [    2.765105] Bluetooth: SCO socket layer initialized
May  8 08:11:06 tashtego kernel: [    2.765193] Bluetooth: RFCOMM socket layer initialized
May  8 08:11:06 tashtego kernel: [    2.765215] Bluetooth: RFCOMM TTY layer initialized
May  8 08:11:06 tashtego kernel: [    2.765219] Bluetooth: RFCOMM ver 1.10
May  8 08:11:06 tashtego kernel: [    2.765263] powernow-k8: Processor cpuid 662 not supported
May  8 08:11:06 tashtego kernel: [    2.765382] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
May  8 08:11:06 tashtego kernel: [    2.772857] powernow: No PST tables match this cpuid (0x762)
May  8 08:11:06 tashtego kernel: [    2.772861] powernow: This is indicative of a broken BIOS.
May  8 08:11:06 tashtego kernel: [    2.772864] powernow: Trying ACPI perflib
May  8 08:11:06 tashtego kernel: [    2.772902] powernow: Minimum speed 498 MHz. Maximum speed 1195 MHz.
May  8 08:11:06 tashtego kernel: [    2.773092] IO APIC resources could be not be allocated.
May  8 08:11:06 tashtego kernel: [    2.773153] Using IPI No-Shortcut mode
May  8 08:11:06 tashtego kernel: [    2.773366] registered taskstats version 1
May  8 08:11:06 tashtego kernel: [    2.773532]   Magic number: 9:57:169
May  8 08:11:06 tashtego kernel: [    2.773709] rtc_cmos 00:02: setting system clock to 2009-05-08 08:10:45 UTC (1241770245)
May  8 08:11:06 tashtego kernel: [    2.773715] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  8 08:11:06 tashtego kernel: [    2.773719] EDD information not available.
May  8 08:11:06 tashtego kernel: [    2.775061] Freeing unused kernel memory: 532k freed
May  8 08:11:06 tashtego kernel: [    2.775287] Write protecting the kernel text: 4128k
May  8 08:11:06 tashtego kernel: [    2.775357] Write protecting the kernel read-only data: 1532k
May  8 08:11:06 tashtego kernel: [    2.811005] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
May  8 08:11:06 tashtego kernel: [    2.840347] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
May  8 08:11:06 tashtego kernel: [    3.402265] Floppy drive(s): fd0 is 1.44M
May  8 08:11:06 tashtego kernel: [    3.419916] FDC 0 is a post-1991 82077
May  8 08:11:06 tashtego kernel: [    3.634646] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
May  8 08:11:06 tashtego kernel: [    3.634725] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
May  8 08:11:06 tashtego kernel: [    3.640121] 8139too Fast Ethernet driver 0.9.28
May  8 08:11:06 tashtego kernel: [    3.640237] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
May  8 08:11:06 tashtego kernel: [    3.641587] eth0: RealTek RTL8139 at 0x1400, 00:08:02:04:d9:a1, IRQ 11
May  8 08:11:06 tashtego kernel: [    3.641592] eth0:  Identified 8139 chip type 'RTL-8139C'
May  8 08:11:06 tashtego kernel: [    4.336744] Marking TSC unstable due to TSC halts in idle
May  8 08:11:06 tashtego kernel: [    4.418477] PM: Starting manual resume from disk
May  8 08:11:06 tashtego kernel: [    4.418488] PM: Resume from partition 8:5
May  8 08:11:06 tashtego kernel: [    4.418491] PM: Checking hibernation image.
May  8 08:11:06 tashtego kernel: [    4.418887] PM: Resume from disk failed.
May  8 08:11:06 tashtego kernel: [    4.424435] EXT3-fs: INFO: recovery required on readonly filesystem.
May  8 08:11:06 tashtego kernel: [    4.424444] EXT3-fs: write access will be enabled during recovery.
May  8 08:11:06 tashtego kernel: [    5.783611] kjournald starting.  Commit interval 5 seconds
May  8 08:11:06 tashtego kernel: [    5.783662] EXT3-fs: recovery complete.
May  8 08:11:06 tashtego kernel: [    5.784923] EXT3-fs: mounted filesystem with ordered data mode.
May  8 08:11:06 tashtego kernel: [   15.157909] udev: starting version 141
May  8 08:11:06 tashtego kernel: [   15.406264] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input6
May  8 08:11:06 tashtego kernel: [   15.437985] Linux agpgart interface v0.103
May  8 08:11:06 tashtego kernel: [   15.444357] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
May  8 08:11:06 tashtego kernel: [   15.468902] parport_pc: VIA 686A/8231 detected
May  8 08:11:06 tashtego kernel: [   15.468911] parport_pc: probing current configuration
May  8 08:11:06 tashtego kernel: [   15.468932] parport_pc: Current parallel port base: 0x378
May  8 08:11:06 tashtego kernel: [   15.469014] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
May  8 08:11:06 tashtego kernel: [   15.489745] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
May  8 08:11:06 tashtego kernel: [   15.497135] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xec000000
May  8 08:11:06 tashtego kernel: [   15.560575] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  8 08:11:06 tashtego kernel: [   15.561738] parport_pc: VIA parallel port: io=0x378, irq=7
May  8 08:11:06 tashtego kernel: [   15.781423] vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1
May  8 08:11:06 tashtego kernel: [   15.967011] input: PC Speaker as /devices/platform/pcspkr/input/input7
May  8 08:11:06 tashtego kernel: [   16.073409] yenta_cardbus 0000:00:0a.0: CardBus bridge found [0e11:b103]
May  8 08:11:06 tashtego kernel: [   16.073438] yenta_cardbus 0000:00:0a.0: Enabling burst memory read transactions
May  8 08:11:06 tashtego kernel: [   16.073445] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
May  8 08:11:06 tashtego kernel: [   16.073450] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
May  8 08:11:06 tashtego kernel: [   16.073457] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01001002, devctl 0x64
May  8 08:11:06 tashtego kernel: [   16.305126] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0018, PCI irq 11
May  8 08:11:06 tashtego kernel: [   16.305137] yenta_cardbus 0000:00:0a.0: Socket status: 30000010
May  8 08:11:06 tashtego kernel: [   16.460097] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
May  8 08:11:06 tashtego kernel: [   16.544252] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  8 08:11:06 tashtego kernel: [   16.957225] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
May  8 08:11:06 tashtego kernel: [   16.958266] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
May  8 08:11:06 tashtego kernel: [   16.958273] PCI: setting IRQ 5 as level-triggered
May  8 08:11:06 tashtego kernel: [   16.958283] VIA 82xx Audio 0000:00:07.5: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
May  8 08:11:06 tashtego kernel: [   16.958437] VIA 82xx Audio 0000:00:07.5: setting latency timer to 64
May  8 08:11:06 tashtego kernel: [   17.007822] ppdev: user-space parallel port driver
May  8 08:11:06 tashtego kernel: [   17.425468] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
May  8 08:11:06 tashtego kernel: [   17.427904] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
May  8 08:11:06 tashtego kernel: [   17.428989] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
May  8 08:11:06 tashtego kernel: [   17.429859] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
May  8 08:11:06 tashtego kernel: [   17.431009] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
May  8 08:11:06 tashtego kernel: [   17.432000] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
May  8 08:11:06 tashtego kernel: [   17.439514] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
May  8 08:11:06 tashtego kernel: [   17.573835] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9d48b1, caps: 0x904713/0x4006
May  8 08:11:06 tashtego kernel: [   17.605253] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
May  8 08:11:06 tashtego kernel: [   17.613216] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
May  8 08:11:06 tashtego kernel: [   17.641136] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
May  8 08:11:06 tashtego kernel: [   17.933759] eth1: Hardware identity 800c:0000:0001:0000
May  8 08:11:06 tashtego kernel: [   17.933889] eth1: Station identity  001f:0009:0001:0004
May  8 08:11:06 tashtego kernel: [   17.933896] eth1: Firmware determined as Intersil 1.4.9
May  8 08:11:06 tashtego kernel: [   17.933901] eth1: Ad-hoc demo mode supported
May  8 08:11:06 tashtego kernel: [   17.933904] eth1: IEEE standard IBSS ad-hoc mode supported
May  8 08:11:06 tashtego kernel: [   17.933907] eth1: WEP supported, 104-bit key
May  8 08:11:06 tashtego kernel: [   18.058729] eth1: MAC address 00:0d:3a:23:1c:41
May  8 08:11:06 tashtego kernel: [   18.058827] eth1: Station name "Prism  I"
May  8 08:11:06 tashtego kernel: [   18.059459] eth1: ready
May  8 08:11:06 tashtego kernel: [   18.061358] eth1: orinoco_cs at 0.0, irq 3, io 0x0100-0x013f
May  8 08:11:06 tashtego kernel: [   18.158429] ieee80211_crypt: registered algorithm 'NULL'
May  8 08:11:06 tashtego kernel: [   18.703889] lp0: using parport0 (interrupt-driven).
May  8 08:11:06 tashtego kernel: [   19.067047] Adding 650592k swap on /dev/sda5.  Priority:-1 extents:1 across:650592k
May  8 08:11:06 tashtego kernel: [   19.798160] EXT3 FS on sda6, internal journal
May  8 08:11:06 tashtego kernel: [   21.300829] type=1505 audit(1241784664.026:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2028
May  8 08:11:06 tashtego kernel: [   21.422203] type=1505 audit(1241784664.146:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2032
May  8 08:11:06 tashtego kernel: [   21.422790] type=1505 audit(1241784664.146:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2032
May  8 08:11:06 tashtego kernel: [   21.422956] type=1505 audit(1241784664.146:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2032
May  8 08:11:06 tashtego kernel: [   21.423106] type=1505 audit(1241784664.146:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2032
May  8 08:11:06 tashtego kernel: [   21.763405] type=1505 audit(1241784664.486:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2037
May  8 08:11:06 tashtego kernel: [   21.764260] type=1505 audit(1241784664.490:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2037
May  8 08:11:06 tashtego kernel: [   21.838674] type=1505 audit(1241784664.562:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2041
May  8 08:11:08 tashtego acpid: client connected from 2533[111:120] 
May  8 08:11:08 tashtego bluetoothd[2547]: Bluetooth daemon
May  8 08:11:08 tashtego bluetoothd[2547]: Starting SDP server
May  8 08:11:08 tashtego kernel: [   25.481813] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  8 08:11:08 tashtego kernel: [   25.481821] Bluetooth: BNEP filters: protocol multicast
May  8 08:11:08 tashtego bluetoothd[2547]: bridge pan0 created
May  8 08:11:08 tashtego bluetoothd[2547]: Registered interface org.bluez.Service on path /org/bluez/2547/any
May  8 08:11:08 tashtego bluetoothd[2547]: Starting experimental netlink support
May  8 08:11:08 tashtego kernel: [   25.518332] Bridge firewalling registered
May  8 08:11:08 tashtego bluetoothd[2547]: Failed to find Bluetooth netlink family
May  8 08:11:09 tashtego acpid: client connected from 2587[0:0] 
May  8 08:11:09 tashtego NetworkManager: <info>  starting... 
May  8 08:11:09 tashtego NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too') 
May  8 08:11:09 tashtego NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_08_02_04_d9_a1 
May  8 08:11:09 tashtego NetworkManager: <info>  (eth1): driver does not support SSID scans (scan_capa 0x00). 
May  8 08:11:09 tashtego NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'orinoco_cs') 
May  8 08:11:09 tashtego NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_0d_3a_23_1c_41 
May  8 08:11:09 tashtego NetworkManager: <info>  Trying to start the supplicant... 
May  8 08:11:09 tashtego NetworkManager: <info>  Trying to start the system settings daemon... 
May  8 08:11:09 tashtego nm-system-settings:    SCPlugin-Ifupdown: init!
May  8 08:11:09 tashtego nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  8 08:11:09 tashtego nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  8 08:11:09 tashtego nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_08_02_04_d9_a1, iface: eth0): not well known
May  8 08:11:09 tashtego nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_0d_3a_23_1c_41, iface: eth1): not well known
May  8 08:11:09 tashtego nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  8 08:11:09 tashtego nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  8 08:11:09 tashtego nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  8 08:11:09 tashtego nm-system-settings:    SCPlugin-Ifupdown: (137844536) ... get_connections.
May  8 08:11:09 tashtego nm-system-settings:    SCPlugin-Ifupdown: (137844536) ... get_connections (managed=false): return empty list.
May  8 08:11:09 tashtego avahi-daemon[2637]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
May  8 08:11:09 tashtego avahi-daemon[2637]: Successfully dropped root privileges.
May  8 08:11:09 tashtego avahi-daemon[2637]: avahi-daemon 0.6.23 starting up.
May  8 08:11:09 tashtego avahi-daemon[2637]: Successfully called chroot().
May  8 08:11:09 tashtego avahi-daemon[2637]: Successfully dropped remaining capabilities.
May  8 08:11:09 tashtego nm-system-settings:    Ifupdown: get unmanaged devices count: 0
May  8 08:11:09 tashtego avahi-daemon[2637]: No service file found in /etc/avahi/services.
May  8 08:11:09 tashtego avahi-daemon[2637]: Network interface enumeration completed.
May  8 08:11:09 tashtego avahi-daemon[2637]: Registering HINFO record with values 'I686'/'LINUX'.
May  8 08:11:09 tashtego avahi-daemon[2637]: Server startup complete. Host name is tashtego.local. Local service cookie is 1312153280.
May  8 08:11:09 tashtego NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle 
May  8 08:11:11 tashtego anacron[2748]: Anacron 2.3 started on 2009-05-08
May  8 08:11:11 tashtego anacron[2748]: Normal exit (0 jobs run)
May  8 08:11:12 tashtego /usr/sbin/cron[2791]: (CRON) INFO (pidfile fd = 3)
May  8 08:11:12 tashtego /usr/sbin/cron[2792]: (CRON) STARTUP (fork ok)
May  8 08:11:12 tashtego /usr/sbin/cron[2792]: (CRON) INFO (Running @reboot jobs)
May  8 08:11:14 tashtego nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_08_02_04_d9_a1
May  8 08:11:14 tashtego NetworkManager: <info>  (eth0): device state change: 1 -> 2 
May  8 08:11:14 tashtego NetworkManager: <info>  (eth0): bringing up device. 
May  8 08:11:14 tashtego NetworkManager: <info>  (eth0): preparing device. 
May  8 08:11:14 tashtego NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
May  8 08:11:14 tashtego NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 08:11:14 tashtego NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
May  8 08:11:14 tashtego NetworkManager: <info>  (eth1): device state change: 1 -> 2 
May  8 08:11:14 tashtego NetworkManager: <info>  (eth1): bringing up device. 
May  8 08:11:14 tashtego kernel: [   31.279370] eth0: link down
May  8 08:11:14 tashtego kernel: [   31.279486] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  8 08:11:14 tashtego kernel: [   31.321288] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  8 08:11:14 tashtego NetworkManager: <info>  (eth1): preparing device. 
May  8 08:11:14 tashtego NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
May  8 08:11:14 tashtego kernel: [   31.344967] eth1: New link status: Disconnected (0002)
May  8 08:11:14 tashtego NetworkManager: <info>  (eth1): device state change: 2 -> 3 
May  8 08:11:14 tashtego NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready 
May  8 08:11:15 tashtego kernel: [   32.682156] eth1: New link status: Connected (0001)
May  8 08:11:15 tashtego kernel: [   32.682233] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May  8 08:11:16 tashtego avahi-daemon[2637]: Registering new address record for fe80::20d:3aff:fe23:1c41 on eth1.*.
May  8 08:11:25 tashtego kernel: [   43.212041] eth1: no IPv6 routers present
May  8 08:11:43 tashtego gdm[2581]: WARNING: Couldn't authenticate user 
May  8 08:11:47 tashtego console-kit-daemon[2391]: WARNING: Couldn't read /proc/2390/environ: Failed to open file '/proc/2390/environ': No such file or directory 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) starting connection 'Auto docjp' 
May  8 08:12:01 tashtego NetworkManager: <info>  (eth1): device state change: 3 -> 4 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
May  8 08:12:01 tashtego NetworkManager: <info>  (eth1): device state change: 4 -> 5 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto docjp' has security, but secrets are required. 
May  8 08:12:01 tashtego NetworkManager: <info>  (eth1): device state change: 5 -> 6 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
May  8 08:12:01 tashtego NetworkManager: <info>  (eth1): device state change: 6 -> 4 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
May  8 08:12:01 tashtego NetworkManager: <info>  (eth1): device state change: 4 -> 5 
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto docjp' has security, and secrets exist.  No new secrets needed. 
May  8 08:12:01 tashtego NetworkManager: <info>  Config: added 'ssid' value 'docjp' 
May  8 08:12:01 tashtego NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
May  8 08:12:01 tashtego NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
May  8 08:12:01 tashtego NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
May  8 08:12:01 tashtego NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
May  8 08:12:01 tashtego NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
May  8 08:12:01 tashtego NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  8 08:12:01 tashtego NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  8 08:12:01 tashtego NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
May  8 08:12:01 tashtego NetworkManager: <info>  Config: set interface ap_scan to 1 
May  8 08:12:01 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  inactive -> scanning 
May  8 08:12:01 tashtego anacron[3190]: Anacron 2.3 started on 2009-05-08
May  8 08:12:01 tashtego anacron[3190]: Normal exit (0 jobs run)
May  8 08:12:01 tashtego kernel: [   79.135625] eth1: New link status: Disconnected (0002)
May  8 08:12:02 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
May  8 08:12:02 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected 
May  8 08:12:02 tashtego kernel: [   80.246445] eth1: New link status: Connected (0001)
May  8 08:12:02 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associated 
May  8 08:12:02 tashtego NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed 
May  8 08:12:02 tashtego NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'docjp'. 
May  8 08:12:02 tashtego NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
May  8 08:12:02 tashtego NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
May  8 08:12:02 tashtego NetworkManager: <info>  (eth1): device state change: 5 -> 7 
May  8 08:12:02 tashtego NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
May  8 08:12:03 tashtego NetworkManager: <info>  dhclient started with pid 3206 
May  8 08:12:03 tashtego NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
May  8 08:12:03 tashtego dhclient: Internet Systems Consortium DHCP Client V3.1.1
May  8 08:12:03 tashtego dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  8 08:12:03 tashtego dhclient: All rights reserved.
May  8 08:12:03 tashtego dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  8 08:12:03 tashtego dhclient: 
May  8 08:12:03 tashtego NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit 
May  8 08:12:03 tashtego dhclient: Listening on LPF/eth1/00:0d:3a:23:1c:41
May  8 08:12:03 tashtego dhclient: Sending on   LPF/eth1/00:0d:3a:23:1c:41
May  8 08:12:03 tashtego dhclient: Sending on   Socket/fallback
May  8 08:12:03 tashtego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
May  8 08:12:11 tashtego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
May  8 08:12:12 tashtego dhclient: DHCPOFFER of 192.168.1.102 from 192.168.1.1
May  8 08:12:12 tashtego dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
May  8 08:12:12 tashtego dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
May  8 08:12:12 tashtego NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
May  8 08:12:12 tashtego NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
May  8 08:12:12 tashtego NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
May  8 08:12:12 tashtego NetworkManager: <info>    address 192.168.1.102 
May  8 08:12:12 tashtego NetworkManager: <info>    prefix 24 (255.255.255.0) 
May  8 08:12:12 tashtego NetworkManager: <info>    gateway 192.168.1.1 
May  8 08:12:12 tashtego NetworkManager: <info>    hostname 'tashtego' 
May  8 08:12:12 tashtego NetworkManager: <info>    nameserver '72.45.32.34' 
May  8 08:12:12 tashtego NetworkManager: <info>    nameserver '72.45.32.37' 
May  8 08:12:12 tashtego NetworkManager: <info>    domain name 'the-beach.net' 
May  8 08:12:12 tashtego NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  8 08:12:12 tashtego NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
May  8 08:12:12 tashtego NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
May  8 08:12:12 tashtego avahi-daemon[2637]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
May  8 08:12:12 tashtego avahi-daemon[2637]: New relevant interface eth1.IPv4 for mDNS.
May  8 08:12:12 tashtego avahi-daemon[2637]: Registering new address record for 192.168.1.102 on eth1.IPv4.
May  8 08:12:12 tashtego dhclient: bound to 192.168.1.102 -- renewal in 40173 seconds.
May  8 08:12:13 tashtego NetworkManager: <info>  (eth1): device state change: 7 -> 8 
May  8 08:12:13 tashtego NetworkManager: <info>  Policy set 'Auto docjp' (eth1) as default for routing and DNS. 
May  8 08:12:13 tashtego NetworkManager: <info>  Activation (eth1) successful, device activated. 
May  8 08:12:13 tashtego NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
May  8 08:12:13 tashtego kernel: [   90.836071] Clocksource tsc unstable (delta = -105105713 ns)
May  8 12:12:16 tashtego ntpdate[3294]: step time server 91.189.94.4 offset 14400.373107 sec
May  8 12:17:02 tashtego /USR/SBIN/CRON[3312]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  8 12:20:02 tashtego /USR/SBIN/CRON[3424]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

```

That was what was given from essentially two reboots.  I think this below is where the computer is trying to shut down but encounters problem (taken from a section above)...

```

May  8 12:00:02 tashtego /USR/SBIN/CRON[3336]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
May  8 12:00:02 tashtego /USR/SBIN/CRON[3337]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  8 12:10:01 tashtego /USR/SBIN/CRON[3704]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  8 12:10:07 tashtego console-kit-daemon[2391]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 12:10:07 tashtego last message repeated 4 times
May  8 12:10:08 tashtego init: tty4 main process (2179) killed by TERM signal
May  8 12:10:08 tashtego init: tty5 main process (2180) killed by TERM signal
May  8 12:10:08 tashtego console-kit-daemon[2391]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 12:10:08 tashtego init: tty2 main process (2187) killed by TERM signal
May  8 12:10:08 tashtego init: tty3 main process (2188) killed by TERM signal
May  8 12:10:08 tashtego init: tty6 main process (2189) killed by TERM signal
May  8 12:10:08 tashtego init: tty1 main process (2889) killed by TERM signal
May  8 12:10:08 tashtego console-kit-daemon[2391]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  8 12:10:08 tashtego last message repeated 5 times
May  8 12:10:09 tashtego NetworkManager: <info>  (eth1): device state change: 8 -> 3 
May  8 12:10:09 tashtego NetworkManager: <info>  (eth1): deactivating device (reason: 38). 
May  8 12:10:09 tashtego NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 3199 
May  8 12:10:10 tashtego kernel: [  712.781667] eth1: New link status: Disconnected (0002)
May  8 12:10:10 tashtego NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
May  8 08:11:05 tashtego syslogd 1.5.0#5ubuntu3: restart.

```

If anyone can understand what's going on here please let me know.

---

### Post by Dr. Feelgood on 2009-05-09
Well I'm giving up folks, I've already ranted a bit in another post for one of my other major 9.04 issues so I'll spare you here but I'm going back to Hardy.  Jaunty just has too many major major bugs for me to deal with that basically make my laptop useless.  I guess I'll just have to wait for the next stable release.  F**k Jaunty.

---

