---
title: "Ethernet card not detected!"
date: 2008-07-17
forum: Hardware
---

### Post by Velvet Ghost on 2008-07-17
I've just installed an ethernet card on an old P4 desktop, which did not have one previously. Then, I formatted the hard disk and installed Ubuntu 8.04. However, it seems that the ethernet card was not detected. When I try pppoeconf (I have an ADSL connection), it says eth0 was not found and ifconfig shows only the loopback adapter and no eth0. Same problem with Fedora 9, haven't tried Windows yet. The card is seated perfectly in the PCI slot. I checked that multiple times, and also tried another PCI slot. The DSL modem is working perfectly, since I use the internet with that same modem on my laptop. Any ideas as to what could be wrong? Thanks.

---

### Post by coffeecat on 2008-07-17
> **Velvet Ghost said:**
> When I try pppoeconf (I have an ADSL connection), it says eth0 was not found and ifconfig shows only the loopback adapter and no eth0. 

I guess there could be two explanations. (I'm hypothesising here.) Either there's no kernel module for the particular chipset loaded, or the PCI card is faulty. I really don't know whether there is an ethernet chipset available that wouldn't have a suitable driver in the Ubuntu kernel, but if there is you'd be very unlucky to get hold of one. Do you know what the chipset is?

As far as I know, lspci will list any ethernet pci card it finds, even if no driver is loaded. So try

```
sudo lspci
```in a terminal and see if there is a line with 'ethernet' in it. If there is we'e identified the chipset and that might help to see whether there's a driver problem. If no such line appears, then it would be reasonable to assume the card is faulty.

You say, 'haven't tried Windows yet.' Have you got another (Windows computer) you could try the card in.

---

### Post by Velvet Ghost on 2008-07-21
I ran the command. Here's the output:

atriya@atriya-desktop:~$ sudo lspci
[sudo] password for atriya: 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I also ran the command 'sudo lshw -C network' based on another person's advice. Here's the result:

atriya@atriya-desktop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32

Thanks for offering to help. Looks like I've got a rare and unsupported ethernet card, doesn't it?

---

### Post by stchman on 2008-07-21
> **Velvet Ghost said:**
> I ran the command. Here's the output:

atriya@atriya-desktop:~$ sudo lspci
[sudo] password for atriya: 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I also ran the command 'sudo lshw -C network' based on another person's advice. Here's the result:

atriya@atriya-desktop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32

Thanks for offering to help. Looks like I've got a rare and unsupported ethernet card, doesn't it?
The Realtek 8139 works OOB with Linux.

---

### Post by rogier.de.groot on 2008-07-21
Realtek? Realtek cards always work out of the box. Strange. Maybe the wrong driver / kernel module is being loaded? Check the output of 'dmesg' and 'lsmod' for clues.

---

### Post by Velvet Ghost on 2008-07-21
stchman, I understand that it 'should work' OOB; problem is, it isn't. At least on my machine. rogier.de.groot, I tried your commands, but I can't understand the output and nothing relating to ethernet seems to be present. Any more ideas? Could it be a hardware problem?

---

### Post by rogier.de.groot on 2008-07-22
Please post the output of the 'dmesg' commands so we can inspect them.

---

### Post by Velvet Ghost on 2008-07-22
Here is the output of the dmesg and lsmod commands:

atriya@atriya-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f740000 (usable)
[    0.000000]  BIOS-e820: 000000002f740000 - 000000002f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f750000 - 000000002f800000 (ACPI NVS)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 194368) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194368
[    0.000000]   HighMem    194368 ->   194368
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194368
[    0.000000] On node 0 totalpages: 194368
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1486 pages used for memmap
[    0.000000]   Normal zone: 188786 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7350 checksum 0
[    0.000000] ACPI: RSDP 000F7350, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 2F740000, 0030 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: FACP 2F740200, 0074 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: DSDT 2F740370, 41A8 (r1 INTEL  D845GLAD      10A MSFT  100000D)
[    0.000000] ACPI: FACS 2F750000, 0040
[    0.000000] ACPI: APIC 2F740300, 0068 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: ASF! 2F744520, 0084 (r16 AMIASF I845GASF        1 MSFT  100000D)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:d0800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192850
[    0.000000] Kernel command line: root=UUID=ff875584-923f-43a3-8e76-7183e7c3efd3 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1699.852 MHz processor.
[    9.874864] Console: colour VGA+ 80x25
[    9.874870] console [tty0] enabled
[    9.875610] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.876815] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.906104] Memory: 758148k/777472k available (2177k kernel code, 18724k reserved, 1006k data, 368k init, 0k highmem)
[    9.906119] virtual kernel memory layout:
[    9.906121]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.906122]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.906124]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
[    9.906126]     lowmem  : 0xc0000000 - 0xef740000   ( 759 MB)
[    9.906127]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    9.906129]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[    9.906130]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[    9.906135] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.906193] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    9.986170] Calibrating delay using timer specific routine.. 3403.85 BogoMIPS (lpj=6807718)
[    9.986210] Security Framework initialized
[    9.986219] SELinux:  Disabled at boot.
[    9.986241] AppArmor: AppArmor initialized
[    9.986249] Failure registering capabilities with primary security module.
[    9.986263] Mount-cache hash table entries: 512
[    9.986472] Initializing cgroup subsys ns
[    9.986479] Initializing cgroup subsys cpuacct
[    9.986496] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    9.986518] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    9.986522] CPU: L2 cache: 256K
[    9.986526] CPU: Hyper-Threading is disabled
[    9.986530] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[    9.986551] Compat vDSO mapped to ffffe000.
[    9.986572] Checking 'hlt' instruction... OK.
[   10.002791] SMP alternatives: switching to UP code
[   10.005418] Freeing SMP alternatives: 11k freed
[   10.005638] Early unpacking initramfs... done
[   10.557694] ACPI: Core revision 20070126
[   10.557785] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.561127] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[   10.561193] Total of 1 processors activated (3403.85 BogoMIPS).
[   10.561344] ENABLING IO-APIC IRQs
[   10.561538] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.705801] Brought up 1 CPUs
[   10.705837] CPU0 attaching sched-domain:
[   10.705842]  domain 0: span 01
[   10.705846]   groups: 01
[   10.706187] net_namespace: 64 bytes
[   10.706207] Booting paravirtualized kernel on bare hardware
[   10.707127] Time: 16:53:54  Date: 07/22/08
[   10.707174] NET: Registered protocol family 16
[   10.707576] EISA bus registered
[   10.707616] ACPI: bus type pci registered
[   10.707893] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   10.707897] PCI: Using configuration type 1
[   10.707930] Setting up standard PCI resources
[   10.723091] ACPI: EC: Look up EC in DSDT
[   10.729069] ACPI: Interpreter enabled
[   10.729078] ACPI: (supports S0 S1 S4 S5)
[   10.729102] ACPI: Using IOAPIC for interrupt routing
[   10.739883] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.740499] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   10.740502] * this clock source is slow. If you are sure your timer does not have
[   10.740504] * this bug, please use "acpi_pm_good" to disable the workaround
[   10.740562] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   10.740568] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   10.740896] PCI: Transparent bridge - 0000:00:1e.0
[   10.740930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.741134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   10.743555] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   10.743809] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   10.744050] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   10.744283] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   10.744519] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.744754] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.744989] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.745222] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   10.745504] ACPI: Power Resource [URP1] (off)
[   10.745558] ACPI: Power Resource [URP2] (off)
[   10.745611] ACPI: Power Resource [FDDP] (off)
[   10.745663] ACPI: Power Resource [LPTP] (off)
[   10.745836] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.745904] pnp: PnP ACPI init
[   10.745921] ACPI: bus type pnp registered
[   10.752605] pnp: PnP ACPI: found 15 devices
[   10.752613] ACPI: ACPI bus type pnp unregistered
[   10.752621] PnPBIOS: Disabled by ACPI PNP
[   10.753094] PCI: Using ACPI for IRQ routing
[   10.753101] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.761771] NET: Registered protocol family 8
[   10.761777] NET: Registered protocol family 20
[   10.761932] AppArmor: AppArmor Filesystem Enabled
[   10.765686] Time: tsc clocksource has been installed.
[   10.773788] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   10.773804] system 00:0d: ioport range 0x400-0x47f has been reserved
[   10.773809] system 00:0d: ioport range 0x680-0x6ff has been reserved
[   10.773813] system 00:0d: ioport range 0x480-0x4bf has been reserved
[   10.773820] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   10.773824] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[   10.773837] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   10.773842] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[   10.773846] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   10.773850] system 00:0e: iomem range 0x100000-0x2f7fffff could not be reserved
[   10.773855] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   10.804657] PCI: Bridge: 0000:00:1e.0
[   10.804663]   IO window: d000-dfff
[   10.804672]   MEM window: ff800000-ff8fffff
[   10.804678]   PREFETCH window: cea00000-ceafffff
[   10.804696] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.804718] NET: Registered protocol family 2
[   10.841772] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.842383] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.844068] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.845015] TCP: Hash tables configured (established 131072 bind 65536)
[   10.845022] TCP reno registered
[   10.853927] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   11.365909]  it is
[   11.931341] Freeing initrd memory: 7704k freed
[   11.932359] audit: initializing netlink socket (disabled)
[   11.932383] audit(1216745634.920:1): initialized
[   11.936124] VFS: Disk quotas dquot_6.5.1
[   11.936277] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.936556] io scheduler noop registered
[   11.936561] io scheduler anticipatory registered
[   11.936564] io scheduler deadline registered
[   11.936590] io scheduler cfq registered (default)
[   11.936609] Boot video device is 0000:00:02.0
[   19.926991] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   19.927656] isapnp: Scanning for PnP cards...
[   20.281922] isapnp: No Plug & Play device found
[   20.369990] Real Time Clock Driver v1.12ac
[   20.370162] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.370341] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.370656] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.372226] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.372943] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.374578] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.374743] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.374956] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   20.377943] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.377951] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.382908] mice: PS/2 mouse device common for all mice
[   20.383156] EISA: Probing bus 0 at eisa.0
[   20.383200] EISA: Detected 0 cards.
[   20.383205] cpuidle: using governor ladder
[   20.383208] cpuidle: using governor menu
[   20.383372] NET: Registered protocol family 1
[   20.383429] Using IPI No-Shortcut mode
[   20.383484] registered taskstats version 1
[   20.383615]   Magic number: 0:695:894
[   20.383717]   hash matches device ptyy4
[   20.383803] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.383807] EDD information not available.
[   20.384316] Freeing unused kernel memory: 368k freed
[   20.418710] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.820837] fuse init (API version 7.9)
[   21.862982] ACPI: Processor [CPU1] (supports 8 throttling states)
[   21.863008] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.657143] usbcore: registered new interface driver usbfs
[   22.657184] usbcore: registered new interface driver hub
[   22.675920] usbcore: registered new device driver usb
[   22.701039] USB Universal Host Controller Interface driver v3.0
[   22.701147] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.701166] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.701172] uhci_hcd 0000:00:1d.0: UHCI Host Controlleratriya@atriya-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f740000 (usable)
[    0.000000]  BIOS-e820: 000000002f740000 - 000000002f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f750000 - 000000002f800000 (ACPI NVS)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 194368) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194368
[    0.000000]   HighMem    194368 ->   194368
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194368
[    0.000000] On node 0 totalpages: 194368
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1486 pages used for memmap
[    0.000000]   Normal zone: 188786 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7350 checksum 0
[    0.000000] ACPI: RSDP 000F7350, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 2F740000, 0030 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: FACP 2F740200, 0074 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: DSDT 2F740370, 41A8 (r1 INTEL  D845GLAD      10A MSFT  100000D)
[    0.000000] ACPI: FACS 2F750000, 0040
[    0.000000] ACPI: APIC 2F740300, 0068 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: ASF! 2F744520, 0084 (r16 AMIASF I845GASF        1 MSFT  100000D)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:d0800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192850
[    0.000000] Kernel command line: root=UUID=ff875584-923f-43a3-8e76-7183e7c3efd3 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1699.852 MHz processor.
[    9.874864] Console: colour VGA+ 80x25
[    9.874870] console [tty0] enabled
[    9.875610] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.876815] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.906104] Memory: 758148k/777472k available (2177k kernel code, 18724k reserved, 1006k data, 368k init, 0k highmem)
[    9.906119] virtual kernel memory layout:
[    9.906121]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.906122]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.906124]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
[    9.906126]     lowmem  : 0xc0000000 - 0xef740000   ( 759 MB)
[    9.906127]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    9.906129]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[    9.906130]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[    9.906135] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.906193] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    9.986170] Calibrating delay using timer specific routine.. 3403.85 BogoMIPS (lpj=6807718)
[    9.986210] Security Framework initialized
[    9.986219] SELinux:  Disabled at boot.
[    9.986241] AppArmor: AppArmor initialized
[    9.986249] Failure registering capabilities with primary security module.
[    9.986263] Mount-cache hash table entries: 512
[    9.986472] Initializing cgroup subsys ns
[    9.986479] Initializing cgroup subsys cpuacct
[    9.986496] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    9.986518] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    9.986522] CPU: L2 cache: 256K
[    9.986526] CPU: Hyper-Threading is disabled
[    9.986530] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[    9.986551] Compat vDSO mapped to ffffe000.atriya@atriya-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f740000 (usable)
[    0.000000]  BIOS-e820: 000000002f740000 - 000000002f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f750000 - 000000002f800000 (ACPI NVS)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 194368) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194368
[    0.000000]   HighMem    194368 ->   194368
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194368
[    0.000000] On node 0 totalpages: 194368
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1486 pages used for memmap
[    0.000000]   Normal zone: 188786 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7350 checksum 0
[    0.000000] ACPI: RSDP 000F7350, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 2F740000, 0030 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: FACP 2F740200, 0074 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: DSDT 2F740370, 41A8 (r1 INTEL  D845GLAD      10A MSFT  100000D)
[    0.000000] ACPI: FACS 2F750000, 0040
[    0.000000] ACPI: APIC 2F740300, 0068 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: ASF! 2F744520, 0084 (r16 AMIASF I845GASF        1 MSFT  100000D)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:d0800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192850
[    0.000000] Kernel command line: root=UUID=ff875584-923f-43a3-8e76-7183e7c3efd3 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1699.852 MHz processor.
[    9.874864] Console: colour VGA+ 80x25
[    9.874870] console [tty0] enabled
[    9.875610] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.876815] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.906104] Memory: 758148k/777472k available (2177k kernel code, 18724k reserved, 1006k data, 368k init, 0k highmem)
[    9.906119] virtual kernel memory layout:
[    9.906121]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.906122]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.906124]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
[    9.906126]     lowmem  : 0xc0000000 - 0xef740000   ( 759 MB)
[    9.906127]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    9.906129]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[    9.906130]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[    9.906135] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.906193] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    9.986170] Calibrating delay using timer specific routine.. 3403.85 BogoMIPS (lpj=6807718)
[    9.986210] Security Framework initialized
[    9.986219] SELinux:  Disabled at boot.
[    9.986241] AppArmor: AppArmor initialized
[    9.986249] Failure registering capabilities with primary security module.
[    9.986263] Mount-cache hash table entries: 512
[    9.986472] Initializing cgroup subsys ns
[    9.986479] Initializing cgroup subsys cpuacct
[    9.986496] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[    9.986518] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    9.986522] CPU: L2 cache: 256K
[    9.986526] CPU: Hyper-Threading is disabled
[    9.986530] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
[    9.986551] Compat vDSO mapped to ffffe000.
[    9.986572] Checking 'hlt' instruction... OK.
[   10.002791] SMP alternatives: switching to UP code
[   10.005418] Freeing SMP alternatives: 11k freed
[   10.005638] Early unpacking initramfs... done
[   10.557694] ACPI: Core revision 20070126
[   10.557785] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.561127] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[   10.561193] Total of 1 processors activated (3403.85 BogoMIPS).
[   10.561344] ENABLING IO-APIC IRQs
[   10.561538] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.705801] Brought up 1 CPUs
[   10.705837] CPU0 attaching sched-domain:
[   10.705842]  domain 0: span 01
[   10.705846]   groups: 01
[   10.706187] net_namespace: 64 bytes
[   10.706207] Booting paravirtualized kernel on bare hardware
[   10.707127] Time: 16:53:54  Date: 07/22/08
[   10.707174] NET: Registered protocol family 16
[   10.707576] EISA bus registered
[   10.707616] ACPI: bus type pci registered
[   10.707893] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   10.707897] PCI: Using configuration type 1
[   10.707930] Setting up standard PCI resources
[   10.723091] ACPI: EC: Look up EC in DSDT
[   10.729069] ACPI: Interpreter enabled
[   10.729078] ACPI: (supports S0 S1 S4 S5)
[   10.729102] ACPI: Using IOAPIC for interrupt routing
[   10.739883] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.740499] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   10.740502] * this clock source is slow. If you are sure your timer does not have
[   10.740504] * this bug, please use "acpi_pm_good" to disable the workaround
[   10.740562] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   10.740568] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   10.740896] PCI: Transparent bridge - 0000:00:1e.0
[   10.740930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.741134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   10.743555] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   10.743809] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   10.744050] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   10.744283] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   10.744519] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.744754] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.744989] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.745222] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   10.745504] ACPI: Power Resource [URP1] (off)
[   10.745558] ACPI: Power Resource [URP2] (off)
[   10.745611] ACPI: Power Resource [FDDP] (off)
[   10.745663] ACPI: Power Resource [LPTP] (off)
[   10.745836] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.745904] pnp: PnP ACPI init
[   10.745921] ACPI: bus type pnp registered
[   10.752605] pnp: PnP ACPI: found 15 devices
[   10.752613] ACPI: ACPI bus type pnp unregistered
[   10.752621] PnPBIOS: Disabled by ACPI PNP
[   10.753094] PCI: Using ACPI for IRQ routing
[   10.753101] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.761771] NET: Registered protocol family 8
[   10.761777] NET: Registered protocol family 20
[   10.761932] AppArmor: AppArmor Filesystem Enabled
[   10.765686] Time: tsc clocksource has been installed.
[   10.773788] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   10.773804] system 00:0d: ioport range 0x400-0x47f has been reserved
[   10.773809] system 00:0d: ioport range 0x680-0x6ff has been reserved
[   10.773813] system 00:0d: ioport range 0x480-0x4bf has been reserved
[   10.773820] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   10.773824] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[   10.773837] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   10.773842] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[   10.773846] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   10.773850] system 00:0e: iomem range 0x100000-0x2f7fffff could not be reserved
[   10.773855] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   10.804657] PCI: Bridge: 0000:00:1e.0
[   10.804663]   IO window: d000-dfff
[   10.804672]   MEM window: ff800000-ff8fffff
[   10.804678]   PREFETCH window: cea00000-ceafffff
[   10.804696] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.804718] NET: Registered protocol family 2
[   10.841772] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.842383] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.844068] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.845015] TCP: Hash tables configured (established 131072 bind 65536)
[   10.845022] TCP reno registered
[   10.853927] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   11.365909]  it is
[   11.931341] Freeing initrd memory: 7704k freed
[   11.932359] audit: initializing netlink socket (disabled)
[   11.932383] audit(1216745634.920:1): initialized
[   11.936124] VFS: Disk quotas dquot_6.5.1
[   11.936277] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.936556] io scheduler noop registered
[   11.936561] io scheduler anticipatory registered
[   11.936564] io scheduler deadline registered
[   11.936590] io scheduler cfq registered (default)
[   11.936609] Boot video device is 0000:00:02.0
[   19.926991] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   19.927656] isapnp: Scanning for PnP cards...
[   20.281922] isapnp: No Plug & Play device found
[   20.369990] Real Time Clock Driver v1.12ac
[   20.370162] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.370341] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.370656] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.372226] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.372943] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.374578] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.374743] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.374956] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   20.377943] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.377951] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.382908] mice: PS/2 mouse device common for all mice
[   20.383156] EISA: Probing bus 0 at eisa.0
[   20.383200] EISA: Detected 0 cards.
[   20.383205] cpuidle: using governor ladder
[   20.383208] cpuidle: using governor menu
[   20.383372] NET: Registered protocol family 1
[   20.383429] Using IPI No-Shortcut mode
[   20.383484] registered taskstats version 1
[   20.383615]   Magic number: 0:695:894
[   20.383717]   hash matches device ptyy4
[   20.383803] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.383807] EDD information not available.
[   20.384316] Freeing unused kernel memory: 368k freed
[   20.418710] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.820837] fuse init (API version 7.9)
[   21.862982] ACPI: Processor [CPU1] (supports 8 throttling states)
[   21.863008] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.657143] usbcore: registered new interface driver usbfs
[   22.657184] usbcore: registered new interface driver hub
[   22.675920] usbcore: registered new device driver usb
[   22.701039] USB Universal Host Controller Interface driver v3.0
[   22.701147] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.701166] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.701172] uhci_hcd 0000:00:1d.0: UHCI Host Controlleratriya@atriya-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f740000 (usable)
[    0.000000]  BIOS-e820: 000000002f740000 - 000000002f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f750000 - 000000002f800000 (ACPI NVS)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 194368) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194368
[    0.000000]   HighMem    194368 ->   194368
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194368
[    0.000000] On node 0 totalpages: 194368
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1486 pages used for memmap
[    0.000000]   Normal zone: 188786 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7350 checksum 0
[    0.000000] ACPI: RSDP 000F7350, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 2F740000, 0030 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: FACP 2F740200, 0074 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: DSDT 2F740370, 41A8 (r1 INTEL  D845GLAD      10A MSFT  100000D)
[    0.000000] ACPI: FACS 2F750000, 0040
[    0.000000] ACPI: APIC 2F740300, 0068 (r1 INTEL  D845GLAD 20030627 MSFT       97)
[    0.000000] ACPI: ASF! 2F744520, 0084 (r16 AMIASF I845GASF        1 MSFT  100000D)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:d0800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192850
[    0.000000] Kernel command line: root=UUID=ff875584-923f-43a3-8e76-7183e7c3efd3 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... do
[    9.986572] Checking 'hlt' instruction... OK.
[   10.002791] SMP alternatives: switching to UP code
[   10.005418] Freeing SMP alternatives: 11k freed
[   10.005638] Early unpacking initramfs... done
[   10.557694] ACPI: Core revision 20070126
[   10.557785] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.561127] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[   10.561193] Total of 1 processors activated (3403.85 BogoMIPS).
[   10.561344] ENABLING IO-APIC IRQs
[   10.561538] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.705801] Brought up 1 CPUs
[   10.705837] CPU0 attaching sched-domain:
[   10.705842]  domain 0: span 01
[   10.705846]   groups: 01
[   10.706187] net_namespace: 64 bytes
[   10.706207] Booting paravirtualized kernel on bare hardware
[   10.707127] Time: 16:53:54  Date: 07/22/08
[   10.707174] NET: Registered protocol family 16
[   10.707576] EISA bus registered
[   10.707616] ACPI: bus type pci registered
[   10.707893] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   10.707897] PCI: Using configuration type 1
[   10.707930] Setting up standard PCI resources
[   10.723091] ACPI: EC: Look up EC in DSDT
[   10.729069] ACPI: Interpreter enabled
[   10.729078] ACPI: (supports S0 S1 S4 S5)
[   10.729102] ACPI: Using IOAPIC for interrupt routing
[   10.739883] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.740499] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   10.740502] * this clock source is slow. If you are sure your timer does not have
[   10.740504] * this bug, please use "acpi_pm_good" to disable the workaround
[   10.740562] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   10.740568] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   10.740896] PCI: Transparent bridge - 0000:00:1e.0
[   10.740930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.741134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   10.743555] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   10.743809] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   10.744050] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   10.744283] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   10.744519] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.744754] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.744989] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   10.745222] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   10.745504] ACPI: Power Resource [URP1] (off)
[   10.745558] ACPI: Power Resource [URP2] (off)
[   10.745611] ACPI: Power Resource [FDDP] (off)
[   10.745663] ACPI: Power Resource [LPTP] (off)
[   10.745836] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.745904] pnp: PnP ACPI init
[   10.745921] ACPI: bus type pnp registered
[   10.752605] pnp: PnP ACPI: found 15 devices
[   10.752613] ACPI: ACPI bus type pnp unregistered
[   10.752621] PnPBIOS: Disabled by ACPI PNP
[   10.753094] PCI: Using ACPI for IRQ routing
[   10.753101] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.761771] NET: Registered protocol family 8
[   10.761777] NET: Registered protocol family 20
[   10.761932] AppArmor: AppArmor Filesystem Enabled
[   10.765686] Time: tsc clocksource has been installed.
[   10.773788] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   10.773804] system 00:0d: ioport range 0x400-0x47f has been reserved
[   10.773809] system 00:0d: ioport range 0x680-0x6ff has been reserved
[   10.773813] system 00:0d: ioport range 0x480-0x4bf has been reserved
[   10.773820] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   10.773824] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[   10.773837] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   10.773842] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[   10.773846] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   10.773850] system 00:0e: iomem range 0x100000-0x2f7fffff could not be reserved
[   10.773855] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   10.804657] PCI: Bridge: 0000:00:1e.0
[   10.804663]   IO window: d000-dfff
[   10.804672]   MEM window: ff800000-ff8fffff
[   10.804678]   PREFETCH window: cea00000-ceafffff
[   10.804696] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.804718] NET: Registered protocol family 2
[   10.841772] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.842383] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.844068] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.845015] TCP: Hash tables configured (established 131072 bind 65536)
[   10.845022] TCP reno registered
[   10.853927] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   11.365909]  it is
[   11.931341] Freeing initrd memory: 7704k freed
[   11.932359] audit: initializing netlink socket (disabled)
[   11.932383] audit(1216745634.920:1): initialized
[   11.936124] VFS: Disk quotas dquot_6.5.1
[   11.936277] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.936556] io scheduler noop registered
[   11.936561] io scheduler anticipatory registered
[   11.936564] io scheduler deadline registered
[   11.936590] io scheduler cfq registered (default)
[   11.936609] Boot video device is 0000:00:02.0
[   19.926991] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   19.927656] isapnp: Scanning for PnP cards...
[   20.281922] isapnp: No Plug & Play device found
[   20.369990] Real Time Clock Driver v1.12ac
[   20.370162] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.370341] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.370656] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.372226] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.372943] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.374578] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.374743] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.374956] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   20.377943] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.377951] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.382908] mice: PS/2 mouse device common for all mice
[   20.383156] EISA: Probing bus 0 at eisa.0
[   20.383200] EISA: Detected 0 cards.
[   20.383205] cpuidle: using governor ladder
[   20.383208] cpuidle: using governor menu
[   20.383372] NET: Registered protocol family 1
[   20.383429] Using IPI No-Shortcut mode
[   20.383484] registered taskstats version 1
[   20.383615]   Magic number: 0:695:894
[   20.383717]   hash matches device ptyy4
[   20.383803] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.383807] EDD information not available.
[   20.384316] Freeing unused kernel memory: 368k freed
[   20.418710] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.820837] fuse init (API version 7.9)
[   21.862982] ACPI: Processor [CPU1] (supports 8 throttling states)
[   21.863008] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.657143] usbcore: registered new interface driver usbfs
[   22.657184] usbcore: registered new interface driver hub
[   22.675920] usbcore: registered new device driver usb
[   22.701689] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.701741] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[   22.701988] usb usb1: configuration #1 chosen from 1 choice
[   22.702031] hub 1-0:1.0: USB hub found
[   22.702042] hub 1-0:1.0: 2 ports detected
[   22.805083] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   22.805104] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.805110] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.805159] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.805196] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880
[   22.805389] usb usb2: configuration #1 chosen from 1 choice
[   22.805430] hub 2-0:1.0: USB hub found
[   22.805441] hub 2-0:1.0: 2 ports detected
[   22.909043] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   22.909064] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.909070] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.909110] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.909145] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[   22.909341] usb usb3: configuration #1 chosen from 1 choice
[   22.909385] hub 3-0:1.0: USB hub found
[   22.909400] hub 3-0:1.0: 2 ports detected
[   23.012990] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   23.013014] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.013020] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.013067] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   23.016992] ehci_hcd 0000:00:1d.7: debug port 1
[   23.017002] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   23.017017] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00
[   23.050784] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.050998] usb usb4: configuration #1 chosen from 1 choice
[   23.051042] hub 4-0:1.0: USB hub found
[   23.051053] hub 4-0:1.0: 6 ports detected
[   23.134425] SCSI subsystem initialized
[   23.225645] libata version 3.00 loaded.
[   23.240739] ata_piix 0000:00:1f.1: version 2.12
[   23.240764] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   23.240774] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   23.240850] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.251826] scsi0 : ata_piix
[   23.270017] scsi1 : ata_piix
[   23.272083] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   23.272088] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   23.340672] Floppy drive(s): fd0 is 1.44M
[   23.364254] FDC 0 is a post-1991 82077
[   23.481564] ata1.00: ATA-7: ST380215A, 3.AAC, max UDMA/100
[   23.481571] ata1.00: 156301488 sectors, multi 16: LBA48 
[   23.548072] ata1.00: configured for UDMA/100
[   24.020372] ata2.00: ATAPI: SONY    DVD RW DRU-190A, 1.65, max UDMA/66
[   24.020415] ata2.01: ATAPI: HL-DT-ST GCE-8523B, 1.01, max UDMA/33
[   24.020437] ata2.00: limited to UDMA/33 due to 40-wire cable
[   24.192231] ata2.00: configured for UDMA/33
[   24.356192] ata2.01: configured for UDMA/33
[   24.356397] scsi 0:0:0:0: Direct-Access     ATA      ST380215A        3.AA PQ: 0 ANSI: 5
[   24.358051] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DRU-190A  1.65 PQ: 0 ANSI: 5
[   24.358525] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8523B  1.01 PQ: 0 ANSI: 5
[   24.658660] Driver 'sd' needs updating - please use bus_type methods
[   24.658846] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.658873] sd 0:0:0:0: [sda] Write Protect is off
[   24.658878] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.659256] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.659358] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.659379] sd 0:0:0:0: [sda] Write Protect is off
[   24.659383] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.659416] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.659425]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.676361]  sda1 sda2
[   24.676800] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.686360] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.686396] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   24.686427] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   24.694808] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.694817] Uniform CD-ROM driver Revision: 3.20
[   24.694909] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.699149] sr1: scsi3-mmc drive: 40x/52x writer cd/rw xa/form2 cdda tray
[   24.699250] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   25.270559] Attempting manual resume
[   25.270566] swsusp: Resume From Partition 8:1
[   25.270569] PM: Checking swsusp image.
[   25.270818] PM: Resume from disk failed.
[   25.310414] EXT3-fs: INFO: recovery required on readonly filesystem.
[   25.310422] EXT3-fs: write access will be enabled during recovery.
[   27.753965] kjournald starting.  Commit interval 5 seconds
[   27.753999] EXT3-fs: sda2: orphan cleanup on readonly fs
[   27.754011] ext3_orphan_cleanup: deleting unreferenced inode 817000
[   27.754049] EXT3-fs: sda2: 1 orphan inode deleted
[   27.754052] EXT3-fs: recovery complete.
[   27.779486] EXT3-fs: mounted filesystem with ordered data mode.
[   35.923383] Linux agpgart interface v0.102
[   35.971650] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   36.024345] agpgart: Detected an Intel 830M Chipset.
[   36.024472] agpgart: Detected 8060K stolen memory.
[   36.098275] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.144169] agpgart: AGP aperture is 128M @ 0xf0000000
[   36.148195] iTCO_vendor_support: vendor-support=0
[   36.211162] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   36.219803] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   36.219880] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   36.275293] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.355069] intel_rng: Firmware space is locked read-only. If you can't or
[   36.355074] intel_rng: don't want to disable this in firmware setup, and if
[   36.355076] intel_rng: you are certain that your system has a functional
[   36.355078] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   37.058778] input: Power Button (FF) as /devices/virtual/input/input2
[   37.070503] ACPI: Power Button (FF) [PWRF]
[   37.070727] input: Sleep Button (CM) as /devices/virtual/input/input3
[   37.086708] ACPI: Sleep Button (CM) [SLPB]
[   37.862191] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   39.173026] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   41.100510] parport_pc 00:08: reported by Plug and Play ACPI
[   41.100542] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   41.149332] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   41.149371] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   41.471326] intel8x0_measure_ac97_clock: measured 54780 usecs
[   41.471333] intel8x0: clocking to 48000
[   44.309052] lp0: using parport0 (interrupt-driven).
[   44.404700] Adding 1124508k swap on /dev/sda1.  Priority:-1 extents:1 across:1124508k
[   45.006973] EXT3 FS on sda2, internal journal
[   46.320170] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.891921] No dock devices found.
[   48.501143] apm: BIOS not found.
[   48.648745] ppdev: user-space parallel port driver
[   48.803888] audit(1216745672.649:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4752 profile="/usr/sbin/cupsd" namespace="default"
[   50.035083] Bluetooth: Core ver 2.11
[   50.037338] NET: Registered protocol family 31
[   50.037346] Bluetooth: HCI device and connection manager initialized
[   50.037352] Bluetooth: HCI socket layer initialized
[   50.214111] Bluetooth: L2CAP ver 2.9
[   50.214119] Bluetooth: L2CAP socket layer initialized
[   50.255836] Bluetooth: RFCOMM socket layer initialized
[   50.255865] Bluetooth: RFCOMM TTY layer initialized
[   50.255868] Bluetooth: RFCOMM ver 1.8
[   53.121749] [drm] Initialized drm 1.1.0 20060810
[   53.173163] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   53.173179] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   53.173316] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   67.393544] NET: Registered protocol family 10
[   67.394554] lo: Disabled Privacy Extensions

atriya@atriya-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  267780  8 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
parport_pc             36260  1 
ac97_bus                3072  1 snd_ac97_codec
parport                37832  3 ppdev,lp,parport_pc
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
evdev                  13056  3 
snd_seq_dummy           4868  0 
serio_raw               7940  0 
psmouse                40336  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
pcspkr                  4224  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
i2c_i810                5636  0 
agpgart                34760  3 drm,intel_agp
i2c_algo_bit            7300  1 i2c_i810
i2c_core               24832  2 i2c_i810,i2c_algo_bit
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
floppy                 59588  0 
ata_piix               19588  2 
libata                159344  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

Thanks! I have no idea why those smiling faces appeared in the output as soon as i pasted it.

---

### Post by rogier.de.groot on 2008-07-22
Looks like it isn't even seeing the ethernet card. Maybe it's broken or something. Does it work with another OS (other linux distro, Windows, etc)?

---

### Post by Velvet Ghost on 2008-07-22
What's broken? The Ubuntu install? Well, I have the same problem with Fedora 9. I haven't checked with Windows yet. Is there any way to check if it will work with Windows without actually installing Windows?

---

### Post by ionreflex on 2008-07-22
Paleez guys, keep it up : i have the same problem with a laptop - Compaq Evo N620c, broadcom netextreme gigabit NIC; i tried building and installing the driver from source, but i guess firmware is missing...

I'm gonna check with the command you provide so far and get back to you!

Tanks

---

### Post by rogier.de.groot on 2008-07-23
I meant maybe the *ethernet card* is broken. The kernel isn't even trying to load the driver; maybe the card is broken, maybe there's an IRQ conflict or something (fiddle with the BIOS to solve that) OR maybe the kernel just doesn't have driver.
What kernel are you running anyway (output of 'uname -a' welcome), which module packages are installed? Could you try manually inserting the driver with "sudo modprobe rtl8139" ?
EDIT: After doing the modprobe, please post the last bunch of lines from 'dmesg' again (not the whole thing again, please)

---

### Post by Velvet Ghost on 2008-07-23
I'm running the 64-bit Hardy Heron - just a clean fresh install, everything default; nothing modified. That's kernel 2.6.24-19-generic.

After I run your modprobe command, it says:

FATAL: Module rtl8139 not found.

---

### Post by rogier.de.groot on 2008-07-23
Hmmm... weird; maybe try "sudo modprobe 8139too" instead. And I was wondering, did you try with a 32-bit OS? Did you install the 'restricted' kernel modules & such?

---

