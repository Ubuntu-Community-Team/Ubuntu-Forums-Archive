---
title: "my laptop shuts down"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by malcolmx82 on 2008-01-10
hi
this is my fist post here...my name is Marco and i'm Italian so i apologize for my bad english...
i have ubuntu 7.10 installed on my laptop and i've got a strange problem..
a few days ago i was playing neverput and after i think 15 minutes mi laptop shut down...

now what i see is that even everytime i watch youtube videos for more than 10 minutes or play frozenbubble for 20 minutes and all things like that my laptop overheats (i think so because of the noise my fan does and it shuts down...

the strange thing is that when i do all this things under Windows nothing strange happens...

what can i do?

thanks a lot

PS: i have an hp pavillion and an ati mobility radeon x700 video card....i have installed its driver via restricted driver manager

---

### Post by malcolmx82 on 2008-01-12
up

---

### Post by amo-ej1 on 2008-01-12
are you working on battery ? or on power ?

---

### Post by malcolmx82 on 2008-01-12
no i always work on power...

ot/nice avatar/ot

---

### Post by cubeist on 2008-01-12
Next time it happens, note the time, reboot and open System>Admin>System Log and then view and post any error messages you get from that time.  At least this will give us a place to start from.

---

### Post by malcolmx82 on 2008-01-12
here it is...i was playing briquolo...just to test it...and at 1.35 it shuts down....

```
Jan 13 01:22:17 marco-laptop syslogd 1.4.1#21ubuntu3: restart.
Jan 13 01:22:17 marco-laptop anacron[5859]: Job `cron.daily' terminated
Jan 13 01:22:17 marco-laptop anacron[5859]: Normal exit (1 job run)
Jan 13 01:34:27 marco-laptop -- MARK --
Jan 13 01:35:34 marco-laptop kernel: [ 1298.804000] ACPI: Critical trip point
Jan 13 01:35:34 marco-laptop kernel: [ 1298.804000] Critical temperature reached (102 C), shutting down.
Jan 13 01:35:34 marco-laptop kernel: [ 1299.044000] ACPI: Invalid passive threshold
Jan 13 01:35:34 marco-laptop kernel: [ 1299.044000] ACPI: Critical trip point
Jan 13 01:35:34 marco-laptop kernel: [ 1299.044000] Critical temperature reached (84 C), shutting down.
Jan 13 01:35:34 marco-laptop kernel: [ 1299.048000] ACPI: Critical trip point
Jan 13 01:35:34 marco-laptop kernel: [ 1299.048000] Critical temperature reached (102 C), shutting down.
Jan 13 01:35:34 marco-laptop kernel: [ 1299.052000] ACPI: Critical trip point
Jan 13 01:35:34 marco-laptop kernel: [ 1299.052000] Critical temperature reached (84 C), shutting down.
Jan 13 01:35:34 marco-laptop init: tty4 main process (4356) killed by TERM signal
Jan 13 01:35:34 marco-laptop init: tty5 main process (4357) killed by TERM signal
Jan 13 01:35:34 marco-laptop init: tty2 main process (4361) killed by TERM signal
Jan 13 01:35:34 marco-laptop init: tty3 main process (4362) killed by TERM signal
Jan 13 01:35:34 marco-laptop init: tty1 main process (4363) killed by TERM signal
Jan 13 01:35:34 marco-laptop init: tty6 main process (4364) killed by TERM signal
Jan 13 01:35:38 marco-laptop avahi-daemon[5176]: Got SIGTERM, quitting.
Jan 13 01:35:38 marco-laptop avahi-daemon[5176]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Jan 13 01:35:38 marco-laptop atieventsd[4940]: Closing acpid connection 
Jan 13 01:35:38 marco-laptop atieventsd[4940]: Closing control socket 
Jan 13 01:35:38 marco-laptop atieventsd[4940]: ATI External Events Daemon shutting down 
Jan 13 01:35:42 marco-laptop exiting on signal 15
Jan 13 01:36:41 marco-laptop syslogd 1.4.1#21ubuntu3: restart.
Jan 13 01:36:41 marco-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Jan 13 01:36:41 marco-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Jan 13 01:36:41 marco-laptop kernel: Symbols match kernel version 2.6.22.
Jan 13 01:36:41 marco-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fee0000 (usable)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 000000001fee0000 - 000000001feeb000 (ACPI data)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 000000001feeb000 - 000000001ff00000 (ACPI NVS)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] 510MB LOWMEM available.
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 130784) 0 entries of 256 used
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Zone PFN ranges:
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   DMA             0 ->     4096
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   Normal       4096 ->   130784
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   HighMem    130784 ->   130784
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]     0:        0 ->   130784
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] On node 0 totalpages: 130784
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   Normal zone: 989 pages used for memmap
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   Normal zone: 125699 pages, LIFO batch:31
Jan 13 01:36:41 marco-laptop kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] DMI present.
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F76A0 checksum 0
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: RSDP 000F76A0, 0014 (r0 HP    )
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: RSDT 1FEE5277, 0044 (r1 HP     309E      6040000  LTP        0)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: FACP 1FEEAE88, 0074 (r1 HP     309E      6040000 LOHR       5F)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: DSDT 1FEE5B1C, 536C (r1 HP     309E      6040000 MSFT  100000E)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: FACS 1FEFBFC0, 0040
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: APIC 1FEEAEFC, 0068 (r1 HP     309E      6040000 LOHR       5F)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: BOOT 1FEEAFD8, 0028 (r1 HP     309E      6040000  LTP        1)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: MCFG 1FEEAF9C, 003C (r1 HP     309E      6040000 LOHR       5F)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: SSDT 1FEE56D3, 0235 (r1 HP     309E         3000 INTL 20030224)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: SSDT 1FEE54FB, 01D8 (r1 HP     309E         3001 INTL 20030224)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: SSDT 1FEE53E7, 0114 (r1 HP     309E         3000 INTL 20030224)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: SSDT 1FEE52BB, 012C (r1 HP     309E            1 INTL 20030224)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Processor #0 6:13 APIC version 20
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 129763
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Kernel command line: root=UUID=a381afcf-601e-4f57-9834-074a518e4eaf ro quiet splash locale=it_IT
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Initializing CPU#0
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jan 13 01:36:41 marco-laptop kernel: [    0.000000] Detected 1729.619 MHz processor.
Jan 13 01:36:41 marco-laptop kernel: [    7.797678] Console: colour VGA+ 80x25
Jan 13 01:36:41 marco-laptop kernel: [    7.797834] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 13 01:36:41 marco-laptop kernel: [    7.798031] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 13 01:36:41 marco-laptop kernel: [    7.810821] Memory: 506892k/523136k available (2015k kernel code, 15716k reserved, 916k data, 364k init, 0k highmem)
Jan 13 01:36:41 marco-laptop kernel: [    7.810831] virtual kernel memory layout:
Jan 13 01:36:41 marco-laptop kernel: [    7.810832]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Jan 13 01:36:41 marco-laptop kernel: [    7.810833]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jan 13 01:36:41 marco-laptop kernel: [    7.810834]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Jan 13 01:36:41 marco-laptop kernel: [    7.810836]     lowmem  : 0xc0000000 - 0xdfee0000   ( 510 MB)
Jan 13 01:36:41 marco-laptop kernel: [    7.810837]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Jan 13 01:36:41 marco-laptop kernel: [    7.810838]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Jan 13 01:36:41 marco-laptop kernel: [    7.810839]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Jan 13 01:36:41 marco-laptop kernel: [    7.810843] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jan 13 01:36:41 marco-laptop kernel: [    7.810879] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Jan 13 01:36:41 marco-laptop kernel: [    7.890898] Calibrating delay using timer specific routine.. 3462.72 BogoMIPS (lpj=6925444)
Jan 13 01:36:41 marco-laptop kernel: [    7.890923] Security Framework v1.0.0 initialized
Jan 13 01:36:41 marco-laptop kernel: [    7.890930] SELinux:  Disabled at boot.
Jan 13 01:36:41 marco-laptop kernel: [    7.890944] Mount-cache hash table entries: 512
Jan 13 01:36:41 marco-laptop kernel: [    7.891061] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
Jan 13 01:36:41 marco-laptop kernel: [    7.891073] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 13 01:36:41 marco-laptop kernel: [    7.891076] CPU: L2 cache: 2048K
Jan 13 01:36:41 marco-laptop kernel: [    7.891078] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
Jan 13 01:36:41 marco-laptop kernel: [    7.891087] Compat vDSO mapped to ffffe000.
Jan 13 01:36:41 marco-laptop kernel: [    7.891098] Checking 'hlt' instruction... OK.
Jan 13 01:36:41 marco-laptop kernel: [    7.906989] SMP alternatives: switching to UP code
Jan 13 01:36:41 marco-laptop kernel: [    7.907152] Freeing SMP alternatives: 11k freed
Jan 13 01:36:41 marco-laptop kernel: [    7.907395] Early unpacking initramfs... done
Jan 13 01:36:41 marco-laptop kernel: [    8.254737] ACPI: Core revision 20070126
Jan 13 01:36:41 marco-laptop kernel: [    8.254804] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jan 13 01:36:41 marco-laptop kernel: [    8.267022] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
Jan 13 01:36:41 marco-laptop kernel: [    8.267047] Total of 1 processors activated (3462.72 BogoMIPS).
Jan 13 01:36:41 marco-laptop kernel: [    8.267236] ENABLING IO-APIC IRQs
Jan 13 01:36:41 marco-laptop kernel: [    8.267431] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 13 01:36:41 marco-laptop kernel: [    8.414913] Brought up 1 CPUs
Jan 13 01:36:41 marco-laptop kernel: [    8.415016] Booting paravirtualized kernel on bare hardware
Jan 13 01:36:41 marco-laptop kernel: [    8.415086] Time:  1:36:13  Date: 00/13/108
Jan 13 01:36:41 marco-laptop kernel: [    8.415106] NET: Registered protocol family 16
Jan 13 01:36:41 marco-laptop kernel: [    8.415177] EISA bus registered
Jan 13 01:36:41 marco-laptop kernel: [    8.415192] ACPI: bus type pci registered
Jan 13 01:36:41 marco-laptop kernel: [    8.415595] PCI: PCI BIOS revision 2.10 entry at 0xfd860, last bus=7
Jan 13 01:36:41 marco-laptop kernel: [    8.415598] PCI: Using configuration type 1
Jan 13 01:36:41 marco-laptop kernel: [    8.415600] Setting up standard PCI resources
Jan 13 01:36:41 marco-laptop kernel: [    8.424021] ACPI: EC: Look up EC in DSDT
Jan 13 01:36:41 marco-laptop kernel: [    8.424433] ACPI: EC: GPE=0x1b, ports=0x66, 0x62
Jan 13 01:36:41 marco-laptop kernel: [    8.425337] ACPI: Interpreter enabled
Jan 13 01:36:41 marco-laptop kernel: [    8.425340] ACPI: (supports S0 S3 S4 S5)
Jan 13 01:36:41 marco-laptop kernel: [    8.425355] ACPI: Using IOAPIC for interrupt routing
Jan 13 01:36:41 marco-laptop kernel: [    8.429988] ACPI: EC: GPE=0x1b, ports=0x66, 0x62
Jan 13 01:36:41 marco-laptop kernel: [    8.430032] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 13 01:36:41 marco-laptop kernel: [    8.430044] PCI: Probing PCI hardware (bus 00)
Jan 13 01:36:41 marco-laptop kernel: [    8.430672] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jan 13 01:36:41 marco-laptop kernel: [    8.430676] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Jan 13 01:36:41 marco-laptop kernel: [    8.431539] PCI: Transparent bridge - 0000:00:1e.0
Jan 13 01:36:41 marco-laptop kernel: [    8.431647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 13 01:36:41 marco-laptop kernel: [    8.431861] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
Jan 13 01:36:41 marco-laptop kernel: [    8.431979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jan 13 01:36:41 marco-laptop kernel: [    8.432103] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Jan 13 01:36:41 marco-laptop kernel: [    8.433976] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jan 13 01:36:41 marco-laptop kernel: [    8.434060] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jan 13 01:36:41 marco-laptop kernel: [    8.434141] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jan 13 01:36:41 marco-laptop kernel: [    8.434221] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jan 13 01:36:41 marco-laptop kernel: [    8.434301] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jan 13 01:36:41 marco-laptop kernel: [    8.434381] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jan 13 01:36:41 marco-laptop kernel: [    8.434461] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jan 13 01:36:41 marco-laptop kernel: [    8.434541] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jan 13 01:36:41 marco-laptop kernel: [    8.434624] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 13 01:36:41 marco-laptop kernel: [    8.434632] pnp: PnP ACPI init
Jan 13 01:36:41 marco-laptop kernel: [    8.434638] ACPI: bus type pnp registered
Jan 13 01:36:41 marco-laptop kernel: [    8.436532] pnp: PnP ACPI: found 8 devices
Jan 13 01:36:41 marco-laptop kernel: [    8.436535] ACPI: ACPI bus type pnp unregistered
Jan 13 01:36:41 marco-laptop kernel: [    8.436539] PnPBIOS: Disabled by ACPI PNP
Jan 13 01:36:41 marco-laptop kernel: [    8.436577] PCI: Using ACPI for IRQ routing
Jan 13 01:36:41 marco-laptop kernel: [    8.436580] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jan 13 01:36:41 marco-laptop kernel: [    8.436584] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
Jan 13 01:36:41 marco-laptop kernel: [    8.436634] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
Jan 13 01:36:41 marco-laptop kernel: [    8.436679] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
Jan 13 01:36:41 marco-laptop kernel: [    8.457699] NET: Registered protocol family 8
Jan 13 01:36:41 marco-laptop kernel: [    8.457701] NET: Registered protocol family 20
Jan 13 01:36:41 marco-laptop kernel: [    8.457750] pnp: 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
Jan 13 01:36:41 marco-laptop kernel: [    8.457753] pnp: 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
Jan 13 01:36:41 marco-laptop kernel: [    8.457756] pnp: 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
Jan 13 01:36:41 marco-laptop kernel: [    8.457760] pnp: 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
Jan 13 01:36:41 marco-laptop kernel: [    8.458880] Time: tsc clocksource has been installed.
Jan 13 01:36:41 marco-laptop kernel: [    8.488022] PCI: Bridge: 0000:00:01.0
Jan 13 01:36:41 marco-laptop kernel: [    8.488025]   IO window: 3000-3fff
Jan 13 01:36:41 marco-laptop kernel: [    8.488029]   MEM window: c8100000-c81fffff
Jan 13 01:36:41 marco-laptop kernel: [    8.488032]   PREFETCH window: d0000000-d7ffffff
Jan 13 01:36:41 marco-laptop kernel: [    8.488035] PCI: Bridge: 0000:00:1c.0
Jan 13 01:36:41 marco-laptop kernel: [    8.488037]   IO window: disabled.
Jan 13 01:36:41 marco-laptop kernel: [    8.488042]   MEM window: disabled.
Jan 13 01:36:41 marco-laptop kernel: [    8.488046]   PREFETCH window: disabled.
Jan 13 01:36:41 marco-laptop kernel: [    8.488054] PCI: Bus 7, cardbus bridge: 0000:06:06.0
Jan 13 01:36:41 marco-laptop kernel: [    8.488056]   IO window: 00004400-000044ff
Jan 13 01:36:41 marco-laptop kernel: [    8.488062]   IO window: 00004800-000048ff
Jan 13 01:36:41 marco-laptop kernel: [    8.488068]   PREFETCH window: 30000000-33ffffff
Jan 13 01:36:41 marco-laptop kernel: [    8.488074]   MEM window: 34000000-37ffffff
Jan 13 01:36:41 marco-laptop kernel: [    8.488079] PCI: Bridge: 0000:00:1e.0
Jan 13 01:36:41 marco-laptop kernel: [    8.488082]   IO window: 4000-4fff
Jan 13 01:36:41 marco-laptop kernel: [    8.488088]   MEM window: c8200000-c82fffff
Jan 13 01:36:41 marco-laptop kernel: [    8.488092]   PREFETCH window: 30000000-33ffffff
Jan 13 01:36:41 marco-laptop kernel: [    8.488107] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jan 13 01:36:41 marco-laptop kernel: [    8.488113] PCI: Setting latency timer of device 0000:00:01.0 to 64
Jan 13 01:36:41 marco-laptop kernel: [    8.488133] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
Jan 13 01:36:41 marco-laptop kernel: [    8.488140] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Jan 13 01:36:41 marco-laptop kernel: [    8.488153] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jan 13 01:36:41 marco-laptop kernel: [    8.488171] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 18
Jan 13 01:36:41 marco-laptop kernel: [    8.488178] PCI: Setting latency timer of device 0000:06:06.0 to 64
Jan 13 01:36:41 marco-laptop kernel: [    8.488191] NET: Registered protocol family 2
Jan 13 01:36:41 marco-laptop kernel: [    8.526901] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jan 13 01:36:41 marco-laptop kernel: [    8.526934] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
Jan 13 01:36:41 marco-laptop kernel: [    8.527070] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Jan 13 01:36:41 marco-laptop kernel: [    8.527166] TCP: Hash tables configured (established 16384 bind 16384)
Jan 13 01:36:41 marco-laptop kernel: [    8.527169] TCP reno registered
Jan 13 01:36:41 marco-laptop kernel: [    8.538979] checking if image is initramfs... it is
Jan 13 01:36:41 marco-laptop kernel: [    8.990853] Switched to high resolution mode on CPU 0
Jan 13 01:36:41 marco-laptop kernel: [    9.217304] Freeing initrd memory: 7344k freed
Jan 13 01:36:41 marco-laptop kernel: [    9.217457] Simple Boot Flag at 0x36 set to 0x1
Jan 13 01:36:41 marco-laptop kernel: [    9.217699] audit: initializing netlink socket (disabled)
Jan 13 01:36:41 marco-laptop kernel: [    9.217714] audit(1200188173.036:1): initialized
Jan 13 01:36:41 marco-laptop kernel: [    9.219526] VFS: Disk quotas dquot_6.5.1
Jan 13 01:36:41 marco-laptop kernel: [    9.219572] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 13 01:36:41 marco-laptop kernel: [    9.219661] io scheduler noop registered
Jan 13 01:36:41 marco-laptop kernel: [    9.219664] io scheduler anticipatory registered
Jan 13 01:36:41 marco-laptop kernel: [    9.219666] io scheduler deadline registered
Jan 13 01:36:41 marco-laptop kernel: [    9.219681] io scheduler cfq registered (default)
Jan 13 01:36:41 marco-laptop kernel: [    9.219774] Boot video device is 0000:01:00.0
Jan 13 01:36:41 marco-laptop kernel: [    9.219853] PCI: Setting latency timer of device 0000:00:01.0 to 64
Jan 13 01:36:41 marco-laptop kernel: [    9.219881] assign_interrupt_mode Found MSI capability
Jan 13 01:36:41 marco-laptop kernel: [    9.219884] Allocate Port Service[0000:00:01.0:pcie00]
Jan 13 01:36:41 marco-laptop kernel: [    9.219951] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Jan 13 01:36:41 marco-laptop kernel: [    9.220002] assign_interrupt_mode Found MSI capability
Jan 13 01:36:41 marco-laptop kernel: [    9.220005] Allocate Port Service[0000:00:1c.0:pcie00]
Jan 13 01:36:41 marco-laptop kernel: [    9.220036] Allocate Port Service[0000:00:1c.0:pcie02]
Jan 13 01:36:41 marco-laptop kernel: [    9.220176] isapnp: Scanning for PnP cards...
Jan 13 01:36:41 marco-laptop kernel: [    9.574825] isapnp: No Plug & Play device found
Jan 13 01:36:41 marco-laptop kernel: [    9.597601] Real Time Clock Driver v1.12ac
Jan 13 01:36:41 marco-laptop kernel: [    9.597702] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jan 13 01:36:41 marco-laptop kernel: [    9.598322] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 19
Jan 13 01:36:41 marco-laptop kernel: [    9.598331] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
Jan 13 01:36:41 marco-laptop kernel: [    9.598856] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan 13 01:36:41 marco-laptop kernel: [    9.599032] input: Macintosh mouse button emulation as /class/input/input0
Jan 13 01:36:41 marco-laptop kernel: [    9.599102] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 13 01:36:41 marco-laptop kernel: [    9.605346] i8042.c: Detected active multiplexing controller, rev 1.1.
Jan 13 01:36:41 marco-laptop kernel: [    9.608460] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 13 01:36:41 marco-laptop kernel: [    9.608465] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 13 01:36:41 marco-laptop kernel: [    9.608468] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 13 01:36:41 marco-laptop kernel: [    9.608470] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 13 01:36:41 marco-laptop kernel: [    9.608473] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 13 01:36:41 marco-laptop kernel: [    9.608637] mice: PS/2 mouse device common for all mice
Jan 13 01:36:41 marco-laptop kernel: [    9.608918] EISA: Probing bus 0 at eisa.0
Jan 13 01:36:41 marco-laptop kernel: [    9.608925] Cannot allocate resource for EISA slot 1
Jan 13 01:36:41 marco-laptop kernel: [    9.608928] Cannot allocate resource for EISA slot 2
Jan 13 01:36:41 marco-laptop kernel: [    9.608930] Cannot allocate resource for EISA slot 3
Jan 13 01:36:41 marco-laptop kernel: [    9.608933] Cannot allocate resource for EISA slot 4
Jan 13 01:36:41 marco-laptop kernel: [    9.608951] EISA: Detected 0 cards.
Jan 13 01:36:41 marco-laptop kernel: [    9.609045] TCP cubic registered
Jan 13 01:36:41 marco-laptop kernel: [    9.609059] NET: Registered protocol family 1
Jan 13 01:36:41 marco-laptop kernel: [    9.609082] Using IPI No-Shortcut mode
Jan 13 01:36:41 marco-laptop kernel: [    9.609259]   Magic number: 8:627:609
Jan 13 01:36:41 marco-laptop kernel: [    9.609369]   hash matches device 0000:00:01.0:pcie00
Jan 13 01:36:41 marco-laptop kernel: [    9.609566] Freeing unused kernel memory: 364k freed
Jan 13 01:36:41 marco-laptop kernel: [   10.090688] input: AT Translated Set 2 keyboard as /class/input/input1
Jan 13 01:36:41 marco-laptop kernel: [   10.491103] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jan 13 01:36:41 marco-laptop kernel: [   10.691107] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jan 13 01:36:41 marco-laptop kernel: [   10.795536] AppArmor: AppArmor initialized<5>audit(1200188174.536:2):  type=1505 info="AppArmor initialized" pid=1193
Jan 13 01:36:41 marco-laptop kernel: [   10.891059] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jan 13 01:36:41 marco-laptop kernel: [   11.002280] fuse init (API version 7.8)
Jan 13 01:36:41 marco-laptop kernel: [   11.005695] Failure registering capabilities with primary security module.
Jan 13 01:36:41 marco-laptop kernel: [   11.091348] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jan 13 01:36:41 marco-laptop kernel: [   11.208822] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Jan 13 01:36:41 marco-laptop kernel: [   13.006409] ACPI: Thermal Zone [THR0] (90 C)
Jan 13 01:36:41 marco-laptop kernel: [    5.152000] Marking TSC unstable due to: possible TSC halt in C2.
Jan 13 01:36:41 marco-laptop kernel: [    5.152000] ACPI: Invalid passive threshold
Jan 13 01:36:41 marco-laptop kernel: [    5.152000] ACPI: Thermal Zone [THR1] (71 C)
Jan 13 01:36:41 marco-laptop kernel: [    5.156000] Time: acpi_pm clocksource has been installed.
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] usbcore: registered new interface driver usbfs
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] usbcore: registered new interface driver hub
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] usbcore: registered new device driver usb
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] USB Universal Host Controller Interface driver v3.0
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] usb usb1: configuration #1 chosen from 1 choice
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] hub 1-0:1.0: USB hub found
Jan 13 01:36:41 marco-laptop kernel: [    5.492000] hub 1-0:1.0: 2 ports detected
Jan 13 01:36:41 marco-laptop kernel: [    5.596000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
Jan 13 01:36:41 marco-laptop kernel: [    5.596000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Jan 13 01:36:41 marco-laptop kernel: [    5.596000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 13 01:36:41 marco-laptop kernel: [    5.596000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jan 13 01:36:41 marco-laptop kernel: [    5.596000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
Jan 13 01:36:41 marco-laptop kernel: [    5.596000] usb usb2: configuration #1 chosen from 1 choice
Jan 13 01:36:41 marco-laptop kernel: [    5.596000] hub 2-0:1.0: USB hub found
Jan 13 01:36:41 marco-laptop kernel: [    5.596000] hub 2-0:1.0: 2 ports detected
Jan 13 01:36:41 marco-laptop kernel: [    5.620000] 8139too Fast Ethernet driver 0.9.28
Jan 13 01:36:41 marco-laptop kernel: [    5.644000] SCSI subsystem initialized
Jan 13 01:36:41 marco-laptop kernel: [    5.648000] libata version 2.21 loaded.
Jan 13 01:36:41 marco-laptop kernel: [    5.700000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
Jan 13 01:36:41 marco-laptop kernel: [    5.700000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Jan 13 01:36:41 marco-laptop kernel: [    5.700000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 13 01:36:41 marco-laptop kernel: [    5.700000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jan 13 01:36:41 marco-laptop kernel: [    5.700000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001840
Jan 13 01:36:41 marco-laptop kernel: [    5.700000] usb usb3: configuration #1 chosen from 1 choice
Jan 13 01:36:41 marco-laptop kernel: [    5.700000] hub 3-0:1.0: USB hub found
Jan 13 01:36:41 marco-laptop kernel: [    5.700000] hub 3-0:1.0: 2 ports detected
Jan 13 01:36:41 marco-laptop kernel: [    5.804000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
Jan 13 01:36:41 marco-laptop kernel: [    5.804000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Jan 13 01:36:41 marco-laptop kernel: [    5.804000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan 13 01:36:41 marco-laptop kernel: [    5.804000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Jan 13 01:36:41 marco-laptop kernel: [    5.804000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
Jan 13 01:36:41 marco-laptop kernel: [    5.804000] usb usb4: configuration #1 chosen from 1 choice
Jan 13 01:36:41 marco-laptop kernel: [    5.804000] hub 4-0:1.0: USB hub found
Jan 13 01:36:41 marco-laptop kernel: [    5.804000] hub 4-0:1.0: 2 ports detected
Jan 13 01:36:41 marco-laptop kernel: [    5.836000] usb 1-2: new low speed USB device using uhci_hcd and address 2
Jan 13 01:36:41 marco-laptop kernel: [    5.908000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Jan 13 01:36:41 marco-laptop kernel: [    5.908000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Jan 13 01:36:41 marco-laptop kernel: [    5.908000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 13 01:36:41 marco-laptop kernel: [    5.908000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jan 13 01:36:41 marco-laptop kernel: [    5.908000] ehci_hcd 0000:00:1d.7: debug port 1
Jan 13 01:36:41 marco-laptop kernel: [    5.908000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Jan 13 01:36:41 marco-laptop kernel: [    5.908000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xc8000000
Jan 13 01:36:41 marco-laptop kernel: [    5.952000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 13 01:36:41 marco-laptop kernel: [    5.952000] usb usb5: configuration #1 chosen from 1 choice
Jan 13 01:36:41 marco-laptop kernel: [    5.952000] hub 5-0:1.0: USB hub found
Jan 13 01:36:41 marco-laptop kernel: [    5.952000] hub 5-0:1.0: 8 ports detected
Jan 13 01:36:41 marco-laptop kernel: [    6.056000] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 21 (level, low) -> IRQ 23
Jan 13 01:36:41 marco-laptop kernel: [    6.064000] Clocksource tsc unstable (delta = -208467403 ns)
Jan 13 01:36:41 marco-laptop kernel: [    6.104000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[c8208000-c82087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jan 13 01:36:41 marco-laptop kernel: [    6.104000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 19
Jan 13 01:36:41 marco-laptop kernel: [    6.104000] eth0: RealTek RTL8139 at 0xe0848400, 00:0a:e4:d7:33:54, IRQ 19
Jan 13 01:36:41 marco-laptop kernel: [    6.104000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Jan 13 01:36:41 marco-laptop kernel: [    6.108000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jan 13 01:36:41 marco-laptop kernel: [    6.108000] ata_piix 0000:00:1f.1: version 2.11
Jan 13 01:36:41 marco-laptop kernel: [    6.108000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 22
Jan 13 01:36:41 marco-laptop kernel: [    6.108000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Jan 13 01:36:41 marco-laptop kernel: [    6.108000] scsi0 : ata_piix
Jan 13 01:36:41 marco-laptop kernel: [    6.108000] scsi1 : ata_piix
Jan 13 01:36:41 marco-laptop kernel: [    6.108000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118c0 irq 14
Jan 13 01:36:41 marco-laptop kernel: [    6.108000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118c8 irq 15
Jan 13 01:36:41 marco-laptop kernel: [    6.360000] usb 1-2: device not accepting address 2, error -71
Jan 13 01:36:41 marco-laptop kernel: [    6.492000] ata1.00: ATA-6: ST9808210A, 3.02, max UDMA/100
Jan 13 01:36:41 marco-laptop kernel: [    6.492000] ata1.00: 156301488 sectors, multi 16: LBA48 
Jan 13 01:36:41 marco-laptop kernel: [    6.492000] ata1.01: ATAPI: MATSHITAUJ-840D, 1.02, max MWDMA2
Jan 13 01:36:41 marco-laptop kernel: [    6.508000] ata1.00: configured for UDMA/100
Jan 13 01:36:41 marco-laptop kernel: [    6.680000] ata1.01: configured for MWDMA2
Jan 13 01:36:41 marco-laptop kernel: [    6.680000] ata2: port disabled. ignoring.
Jan 13 01:36:41 marco-laptop kernel: [    6.680000] scsi 0:0:0:0: Direct-Access     ATA      ST9808210A       3.02 PQ: 0 ANSI: 5
Jan 13 01:36:41 marco-laptop kernel: [    6.680000] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.02 PQ: 0 ANSI: 5
Jan 13 01:36:41 marco-laptop kernel: [    6.696000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jan 13 01:36:41 marco-laptop kernel: [    6.696000] sd 0:0:0:0: [sda] Write Protect is off
Jan 13 01:36:41 marco-laptop kernel: [    6.696000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 13 01:36:41 marco-laptop kernel: [    6.696000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 13 01:36:41 marco-laptop kernel: [    6.696000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jan 13 01:36:41 marco-laptop kernel: [    6.696000] sd 0:0:0:0: [sda] Write Protect is off
Jan 13 01:36:41 marco-laptop kernel: [    6.696000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 13 01:36:41 marco-laptop kernel: [    6.696000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 13 01:36:41 marco-laptop kernel: [    6.696000]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3
Jan 13 01:36:41 marco-laptop kernel: [    6.776000] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 13 01:36:41 marco-laptop kernel: [    6.780000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 13 01:36:41 marco-laptop kernel: [    6.780000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
Jan 13 01:36:41 marco-laptop kernel: [    6.796000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jan 13 01:36:41 marco-laptop kernel: [    6.796000] Uniform CD-ROM driver Revision: 3.20
Jan 13 01:36:41 marco-laptop kernel: [    6.796000] sr 0:0:1:0: Attached scsi CD-ROM sr0
Jan 13 01:36:41 marco-laptop kernel: [    7.208000] usb 1-2: new low speed USB device using uhci_hcd and address 4
Jan 13 01:36:41 marco-laptop kernel: [    7.336000] Attempting manual resume
Jan 13 01:36:41 marco-laptop kernel: [    7.336000] swsusp: Resume From Partition 8:5
Jan 13 01:36:41 marco-laptop kernel: [    7.336000] PM: Checking swsusp image.
Jan 13 01:36:41 marco-laptop kernel: [    7.336000] PM: Resume from disk failed.
Jan 13 01:36:41 marco-laptop kernel: [    7.368000] kjournald starting.  Commit interval 5 seconds
Jan 13 01:36:41 marco-laptop kernel: [    7.368000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 13 01:36:41 marco-laptop kernel: [    7.376000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[05e40a00682b5035]
Jan 13 01:36:41 marco-laptop kernel: [    7.388000] usb 1-2: configuration #1 chosen from 1 choice
Jan 13 01:36:41 marco-laptop kernel: [    7.632000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jan 13 01:36:41 marco-laptop kernel: [    7.804000] usb 2-1: configuration #1 chosen from 1 choice
Jan 13 01:36:41 marco-laptop kernel: [   16.192000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 13 01:36:41 marco-laptop kernel: [   16.196000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 13 01:36:41 marco-laptop kernel: [   16.284000] Linux agpgart interface v0.102 (c) Dave Jones
Jan 13 01:36:41 marco-laptop kernel: [   17.436000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jan 13 01:36:41 marco-laptop kernel: [   17.640000] [fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
Jan 13 01:36:41 marco-laptop kernel: [   17.640000] [fglrx] ASYNCIO init succeed!
Jan 13 01:36:41 marco-laptop kernel: [   17.640000] [fglrx] PAT is enabled successfully!
Jan 13 01:36:41 marco-laptop kernel: [   17.640000] [fglrx] module loaded - fglrx 8.44.3 [Dec 19 2007] on minor 0
Jan 13 01:36:41 marco-laptop kernel: [   17.664000] iTCO_vendor_support: vendor-support=0
Jan 13 01:36:41 marco-laptop kernel: [   17.668000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Jan 13 01:36:41 marco-laptop kernel: [   17.668000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
Jan 13 01:36:41 marco-laptop kernel: [   17.668000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jan 13 01:36:41 marco-laptop kernel: [   17.724000] usbcore: registered new interface driver hiddev
Jan 13 01:36:41 marco-laptop kernel: [   17.740000] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /class/input/input2
Jan 13 01:36:41 marco-laptop kernel: [   17.740000] input: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:1d.0-2
Jan 13 01:36:41 marco-laptop kernel: [   17.740000] usbcore: registered new interface driver usbhid
Jan 13 01:36:41 marco-laptop kernel: [   17.740000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jan 13 01:36:41 marco-laptop kernel: [   17.748000] Bluetooth: Core ver 2.11
Jan 13 01:36:41 marco-laptop kernel: [   17.748000] NET: Registered protocol family 31
Jan 13 01:36:41 marco-laptop kernel: [   17.748000] Bluetooth: HCI device and connection manager initialized
Jan 13 01:36:41 marco-laptop kernel: [   17.748000] Bluetooth: HCI socket layer initialized
Jan 13 01:36:41 marco-laptop kernel: [   17.768000] ieee80211_crypt: registered algorithm 'NULL'
Jan 13 01:36:41 marco-laptop kernel: [   17.768000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Jan 13 01:36:41 marco-laptop kernel: [   17.768000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan 13 01:36:41 marco-laptop kernel: [   17.800000] Yenta: CardBus bridge found at 0000:06:06.0 [103c:309d]
Jan 13 01:36:41 marco-laptop kernel: [   17.800000] Yenta: Enabling burst memory read transactions
Jan 13 01:36:41 marco-laptop kernel: [   17.800000] Yenta: Using CSCINT to route CSC interrupts to PCI
Jan 13 01:36:41 marco-laptop kernel: [   17.800000] Yenta: Routing CardBus interrupts to PCI
Jan 13 01:36:41 marco-laptop kernel: [   17.800000] Yenta TI: socket 0000:06:06.0, mfunc 0x01aa1b02, devctl 0x64
Jan 13 01:36:41 marco-laptop kernel: [   17.860000] intel_rng: FWH not detected
Jan 13 01:36:41 marco-laptop kernel: [   17.868000] Bluetooth: HCI USB driver ver 2.9
Jan 13 01:36:41 marco-laptop kernel: [   17.868000] usbcore: registered new interface driver hci_usb
Jan 13 01:36:41 marco-laptop kernel: [   17.928000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
Jan 13 01:36:41 marco-laptop kernel: [   17.928000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jan 13 01:36:41 marco-laptop kernel: [   17.944000] sdhci: Secure Digital Host Controller Interface driver
Jan 13 01:36:41 marco-laptop kernel: [   17.944000] sdhci: Copyright(c) Pierre Ossman
Jan 13 01:36:41 marco-laptop kernel: [   18.032000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
Jan 13 01:36:41 marco-laptop kernel: [   18.032000] Socket status: 30000006
Jan 13 01:36:41 marco-laptop kernel: [   18.032000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
Jan 13 01:36:41 marco-laptop kernel: [   18.032000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
Jan 13 01:36:41 marco-laptop kernel: [   18.032000] cs: IO port probe 0x4000-0x4fff: clean.
Jan 13 01:36:41 marco-laptop kernel: [   18.032000] pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
Jan 13 01:36:41 marco-laptop kernel: [   18.032000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
Jan 13 01:36:41 marco-laptop kernel: [   18.040000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 20 (level, low) -> IRQ 19
Jan 13 01:36:41 marco-laptop kernel: [   18.040000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jan 13 01:36:41 marco-laptop kernel: [   18.092000] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jan 13 01:36:41 marco-laptop kernel: [   18.292000] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
Jan 13 01:36:41 marco-laptop kernel: [   18.504000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Jan 13 01:36:41 marco-laptop kernel: [   18.504000] sdhci: SDHCI controller found at 0000:06:06.4 [104c:8034] (rev 0)
Jan 13 01:36:41 marco-laptop kernel: [   18.504000] ACPI: PCI Interrupt 0000:06:06.4[A] -> GSI 22 (level, low) -> IRQ 18
Jan 13 01:36:41 marco-laptop kernel: [   18.504000] mmc0: SDHCI at 0xc8209000 irq 18 DMA
Jan 13 01:36:41 marco-laptop kernel: [   18.508000] mmc1: SDHCI at 0xc8208c00 irq 18 DMA
Jan 13 01:36:41 marco-laptop kernel: [   18.508000] mmc2: SDHCI at 0xc8208800 irq 18 DMA
Jan 13 01:36:41 marco-laptop kernel: [   18.512000] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 22 (level, low) -> IRQ 18
Jan 13 01:36:41 marco-laptop kernel: [   18.568000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
Jan 13 01:36:41 marco-laptop kernel: [   18.568000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
Jan 13 01:36:41 marco-laptop kernel: [   18.600000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
Jan 13 01:36:41 marco-laptop kernel: [   18.604000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jan 13 01:36:41 marco-laptop kernel: [   18.604000] cs: IO port probe 0x820-0x8ff: clean.
Jan 13 01:36:41 marco-laptop kernel: [   18.604000] cs: IO port probe 0xc00-0xcf7: clean.
Jan 13 01:36:41 marco-laptop kernel: [   18.604000] cs: IO port probe 0xa00-0xaff: clean.
Jan 13 01:36:41 marco-laptop kernel: [   18.784000] input: PS/2 Mouse as /class/input/input3
Jan 13 01:36:41 marco-laptop kernel: [   18.800000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
Jan 13 01:36:41 marco-laptop kernel: [   19.492000] intel8x0_measure_ac97_clock: measured 55510 usecs
Jan 13 01:36:41 marco-laptop kernel: [   19.492000] intel8x0: clocking to 48000
Jan 13 01:36:41 marco-laptop kernel: [   20.156000] lp: driver loaded but no devices found
Jan 13 01:36:41 marco-laptop kernel: [   20.208000] Adding 779112k swap on /dev/sda5.  Priority:-1 extents:1 across:779112k
Jan 13 01:36:41 marco-laptop kernel: [   21.032000] EXT3 FS on sda6, internal journal
Jan 13 01:36:41 marco-laptop kernel: [   26.256000] kjournald starting.  Commit interval 5 seconds
Jan 13 01:36:41 marco-laptop kernel: [   26.256000] EXT3 FS on sda7, internal journal
Jan 13 01:36:41 marco-laptop kernel: [   26.256000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 13 01:36:41 marco-laptop kernel: [   28.004000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jan 13 01:36:41 marco-laptop kernel: [   28.044000] ACPI: AC Adapter [AC] (on-line)
Jan 13 01:36:41 marco-laptop kernel: [   28.056000] No dock devices found.
Jan 13 01:36:41 marco-laptop kernel: [   28.096000] ACPI: Battery Slot [BAT0] (battery present)
Jan 13 01:36:41 marco-laptop kernel: [   28.164000] input: Power Button (FF) as /class/input/input5
Jan 13 01:36:41 marco-laptop kernel: [   28.168000] ACPI: Power Button (FF) [PWRF]
Jan 13 01:36:41 marco-laptop kernel: [   28.208000] input: Lid Switch as /class/input/input6
Jan 13 01:36:41 marco-laptop kernel: [   28.212000] ACPI: Lid Switch [LID0]
Jan 13 01:36:41 marco-laptop kernel: [   28.256000] input: Sleep Button (CM) as /class/input/input7
Jan 13 01:36:41 marco-laptop kernel: [   28.260000] ACPI: Sleep Button (CM) [SLPB]
Jan 13 01:36:41 marco-laptop kernel: [   28.300000] input: Power Button (CM) as /class/input/input8
Jan 13 01:36:41 marco-laptop kernel: [   28.304000] ACPI: Power Button (CM) [PWB]
Jan 13 01:36:41 marco-laptop NetworkManager: <info>  starting... 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.199916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2590'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.415066] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2591'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.415820] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_5653'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.416421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2660'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.416912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2658'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.417302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.417691] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.418079] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_7d_noserial'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.418466] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_7d_noserial_if0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.418947] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2659'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.419333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.419719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.420104] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.420490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.420876] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if0_bluetooth_hci'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.421262] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if1'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.421664] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if2'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.422052] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_if3'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.422438] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_265a'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.422849] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.423235] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.423619] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_265b'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.424004] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.424387] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.424783] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_265c'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.425166] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.425549] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.425940] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.426323] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_4220'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.426722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8031'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.427105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8032'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.427488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8033'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.427871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8034'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.428255] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_10ec_8139'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.428638] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.429020] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266d'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.429425] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2641'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.429807] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266f'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.430189] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.430581] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0'). 
Jan 13 01:36:42 marco-laptop kernel: [   29.484000] ppdev: user-space parallel port driver
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.517771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.518445] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266a'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.518972] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.519362] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.519748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.520134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.520522] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.520921] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.521308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.521695] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.522080] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.522465] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.522860] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.523244] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a08'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.523629] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.524013] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_INT0800'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.524396] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.524779] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.525162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.525545] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.525928] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_AUI1500'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.526310] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.526717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_7d_noserial_if0_logicaldev_input'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.527102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.527495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.527878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.528261] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.528643] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.529036] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8034_mmc_host'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.529428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8034_mmc_host_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.529811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8034_mmc_host_1'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.530193] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0a_e4_d7_33_54'). 
Jan 13 01:36:42 marco-laptop kernel: [   29.576000] eth0: link down
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  Deactivating device eth0. 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.595548] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_00_17_b7_55'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2200'. 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Jan 13 01:36:42 marco-laptop NetworkManager: <info>  Deactivating device eth1. 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.658290] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.658762] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266f_scsi_host_scsi_device_lun0_0_scsi_generic'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.659153] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_1'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.659539] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.659944] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_control__1'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.660330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_oss_pcm_0_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.660726] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_oss_mixer__1'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.661110] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.661494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.661878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_1'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.662261] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_2'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.662644] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_capture_3'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.663040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_266e_alsa_playback_4'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.663422] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.663803] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.664184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.664592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.665018] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.665417] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.665801] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.666183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.666564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_7d_noserial_usbraw'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.667032] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.667412] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_171d_noserial_usbraw'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.667792] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.668196] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.668586] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.668967] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST9808210A_3LF2A04V'). 
Jan 13 01:36:42 marco-laptop kernel: [   29.804000] audit(1200184602.612:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4849 profile="/usr/sbin/cupsd"
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.854637] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_FC18E94718E9018E'). 
Jan 13 01:36:42 marco-laptop NetworkManager: <debug> [1200184602.900566] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Jan 13 01:36:42 marco-laptop kernel: [   29.956000] apm: BIOS not found.
Jan 13 01:36:43 marco-laptop NetworkManager: <debug> [1200184603.129608] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_457C_286B'). 
Jan 13 01:36:43 marco-laptop NetworkManager: <debug> [1200184603.134107] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3d1e7d34_6d22_46c3_a072_05477feb983b'). 
Jan 13 01:36:43 marco-laptop NetworkManager: <debug> [1200184603.138735] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a381afcf_601e_4f57_9834_074a518e4eaf'). 
Jan 13 01:36:43 marco-laptop atieventsd[4908]: ATI External Events Daemon started... 
Jan 13 01:36:43 marco-laptop atieventsd[4908]: Event daemon control socket created 
Jan 13 01:36:43 marco-laptop atieventsd[4908]: acpid connection established 
Jan 13 01:36:43 marco-laptop NetworkManager: <debug> [1200184603.220691] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_d81adb45_ec70_4445_a227_ccbcb0a96363'). 
Jan 13 01:36:43 marco-laptop NetworkManager: <debug> [1200184603.437789] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Jan 13 01:36:43 marco-laptop NetworkManager: <debug> [1200184603.466827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Jan 13 01:36:43 marco-laptop NetworkManager: <debug> [1200184603.467283] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Jan 13 01:36:43 marco-laptop NetworkManager: <debug> [1200184603.467918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_UJ_840D'). 
Jan 13 01:36:43 marco-laptop kernel: [   30.804000] Failure registering capabilities with primary security module.
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: Successfully dropped root privileges.
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: avahi-daemon 0.6.20 starting up.
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: Successfully called chroot().
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: Successfully dropped remaining capabilities.
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: No service file found in /etc/avahi/services.
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: Network interface enumeration completed.
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 13 01:36:43 marco-laptop avahi-daemon[5145]: Server startup complete. Host name is marco-laptop.local. Local service cookie is 3855664496.
Jan 13 01:36:43 marco-laptop dhcdbd: Started up.
Jan 13 01:36:43 marco-laptop hcid[5180]: Bluetooth HCI daemon
Jan 13 01:36:43 marco-laptop hcid[5180]: HCI dev 0 registered
Jan 13 01:36:43 marco-laptop hcid[5180]: Starting SDP server
Jan 13 01:36:43 marco-laptop kernel: [   30.976000] Bluetooth: L2CAP ver 2.8
Jan 13 01:36:43 marco-laptop kernel: [   30.976000] Bluetooth: L2CAP socket layer initialized
Jan 13 01:36:43 marco-laptop hcid[5180]: Created local server at unix:abstract=/var/run/dbus-WaYvGduR9T,guid=0d599449c06ee4590792940047895d1b
Jan 13 01:36:43 marco-laptop hcid[5180]: HCI dev 0 up
Jan 13 01:36:43 marco-laptop hcid[5180]: Device hci0 has been added
Jan 13 01:36:44 marco-laptop audio[5187]: Bluetooth Audio daemon
Jan 13 01:36:44 marco-laptop audio[5187]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Jan 13 01:36:44 marco-laptop input[5188]: Bluetooth Input daemon
Jan 13 01:36:44 marco-laptop input[5188]: Registered input manager path:/org/bluez/input
Jan 13 01:36:44 marco-laptop audio[5187]: Unix socket created: 5
Jan 13 01:36:44 marco-laptop kernel: [   31.084000] Bluetooth: RFCOMM socket layer initialized
Jan 13 01:36:44 marco-laptop kernel: [   31.084000] Bluetooth: RFCOMM TTY layer initialized
Jan 13 01:36:44 marco-laptop kernel: [   31.084000] Bluetooth: RFCOMM ver 1.8
Jan 13 01:36:44 marco-laptop hcid[5180]: Starting security manager 0
Jan 13 01:36:44 marco-laptop hcid[5180]: Device hci0 has been activated
Jan 13 01:36:44 marco-laptop audio[5187]: add_service_record: got record id 0x10000
Jan 13 01:36:44 marco-laptop audio[5187]: add_service_record: got record id 0x10001
Jan 13 01:36:44 marco-laptop audio[5187]: Registered manager path:/org/bluez/audio
Jan 13 01:36:44 marco-laptop anacron[5242]: Anacron 2.3 started on 2008-01-13
Jan 13 01:36:45 marco-laptop anacron[5242]: Normal exit (0 jobs run)
Jan 13 01:36:45 marco-laptop /usr/sbin/cron[5269]: (CRON) INFO (pidfile fd = 3)
Jan 13 01:36:45 marco-laptop /usr/sbin/cron[5272]: (CRON) STARTUP (fork ok)
Jan 13 01:36:45 marco-laptop /usr/sbin/cron[5272]: (CRON) INFO (Running @reboot jobs)
Jan 13 01:36:46 marco-laptop kernel: [   33.504000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jan 13 01:36:48 marco-laptop kernel: [   35.704000] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
Jan 13 01:36:48 marco-laptop kernel: [   35.704000] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X40000
Jan 13 01:36:48 marco-laptop kernel: [   35.704000] [fglrx] Reserve Block - 2 offset =  0X7fbb000 length = 0X40000
Jan 13 01:37:04 marco-laptop kernel: [   51.788000] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000003 not found in mutex list
Jan 13 01:37:04 marco-laptop kernel: [   51.844000] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
Jan 13 01:37:04 marco-laptop kernel: [   51.868000] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
Jan 13 01:37:04 marco-laptop kernel: [   51.924000] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
Jan 13 01:37:04 marco-laptop kernel: [   51.948000] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
Jan 13 01:37:07 marco-laptop hcid[5180]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Jan 13 01:37:07 marco-laptop hcid[5180]: Default authorization agent (:1.19, /org/bluez/auth) registered
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Jan 13 01:37:14 marco-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Will activate connection 'eth1/A02-RA141-W54'. 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Activation (eth1) started... 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan 13 01:37:14 marco-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'A02-RA141-W54' is unencrypted, no key needed. 
Jan 13 01:37:16 marco-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 13 01:37:16 marco-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan 13 01:37:16 marco-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Jan 13 01:37:16 marco-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Jan 13 01:37:16 marco-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Jan 13 01:37:17 marco-laptop kernel: [   65.028000] NET: Registered protocol family 17
Jan 13 01:37:17 marco-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 13 01:37:17 marco-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: response was '0' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4130322d52413134312d573534' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'A02-RA141-W54'. 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 13 01:37:18 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan 13 01:37:19 marco-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan 13 01:37:19 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan 13 01:37:19 marco-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jan 13 01:37:19 marco-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jan 13 01:37:21 marco-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Jan 13 01:37:24 marco-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 13 01:37:24 marco-laptop dhclient: DHCPACK from 192.168.1.254
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: New relevant interface eth1.IPv4 for mDNS.
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Jan 13 01:37:24 marco-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jan 13 01:37:24 marco-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Jan 13 01:37:24 marco-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jan 13 01:37:24 marco-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Jan 13 01:37:24 marco-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>    address 192.168.1.100 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>    netmask 255.255.255.0 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>    broadcast 192.168.1.255 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>    gateway 192.168.1.254 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>    nameserver 192.168.1.254 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>    hostname 'dhcppc0' 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jan 13 01:37:24 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: Withdrawing address record for 192.168.1.100 on eth1.
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: New relevant interface eth1.IPv4 for mDNS.
Jan 13 01:37:24 marco-laptop avahi-daemon[5145]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Jan 13 01:37:24 marco-laptop dhclient: bound to 192.168.1.100 -- renewal in 39557 seconds.
Jan 13 01:37:25 marco-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Jan 13 01:37:25 marco-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan 13 01:37:25 marco-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jan 13 01:37:25 marco-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Jan 13 01:37:25 marco-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jan 13 01:37:26 marco-laptop kernel: [   73.092000] NET: Registered protocol family 10
Jan 13 01:37:26 marco-laptop kernel: [   73.092000] lo: Disabled Privacy Extensions
Jan 13 01:37:26 marco-laptop kernel: [   73.092000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 13 01:37:26 marco-laptop ntpdate[5710]: adjust time server 91.189.94.4 offset -0.076638 sec
Jan 13 01:37:27 marco-laptop avahi-daemon[5145]: Registering new address record for fe80::215:ff:fe17:b755 on eth1.*.
Jan 13 01:37:36 marco-laptop kernel: [   83.400000] eth1: no IPv6 routers present
```


i think something critical is already in the first lines where it talks about temperatures reached  :(

---

### Post by cubeist on 2008-01-14
Yes, your laptop is overheating, or at least the software thinks it is overheating (it probably is, although those temperatures are so high I am sure you would notice... 102 would be burning your legs).

I am not sure the exact fix for your problem.  You could try making a new post in these forums with a more specific title.

Sorry, I can't offer better advice...

---

### Post by pieisgood4589 on 2008-01-14
Let's try this-

How old is the laptop? How much RAM? How much video RAM? How much harddrive space? 

Once I get this info, I can try to help some more.

PS-
You might want to get a better cooling fan. :)
As for the issue of not shutting down in Windows, Windows XP is in fact less RAM intensive than Ubuntu at the moment, and Windows doesn't have a built-in software for telling the temperature of your system.

---

### Post by moeFinley on 2008-01-14
I have the same issue.  I can see that my machine runs at about 55 C and the fan won't kick in until it's higher than that.  As soon as the fan does kick in the temperature shoots down to about 50 C.  In my opinion it should keep going but doesn't resulting it being to easy for it to overheat.

---

### Post by cubeist on 2008-01-14
Two things crossed my mind.  FIrst, is your fan working? Mine comes on around 60 and keeps things between 50 and 60, which I believe is about normal for most laptops.

Second, I wonder if APM would do a better job regulating the fan than ACPI?  Because right now it sounds like either your fan is broken or the software controlling the fan is not working.

---

### Post by malcolmx82 on 2008-01-15
> **pieisgood4589 said:**
> Let's try this-

How old is the laptop? How much RAM? How much video RAM? How much harddrive space? 

Once I get this info, I can try to help some more.

PS-
You might want to get a better cooling fan. :)
As for the issue of not shutting down in Windows, Windows XP is in fact less RAM intensive than Ubuntu at the moment, and Windows doesn't have a built-in software for telling the temperature of your system.

first of all i'd like to say that i'm a little bit noob so if there is any command to give to have all these informations..well..it would be good :)

anyway...
i have an hp pavillion dv4000 (i guess dv4266EA but i'm not 100% sure about that)
512 MB of ram
ATI mobility radeon x700 (256 MB of ram i guess)

disk space 

```
File system         blocchi di   1K   Usati Disponib. Uso% Montato su
/dev/sda6              8649544   3157516   5052652  39% /
varrun                  257376        88    257288   1% /var/run
varlock                 257376         0    257376   0% /var/lock
udev                    257376        88    257288   1% /dev
devshm                  257376         0    257376   0% /dev/shm
lrm                     257376     33652    223724  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda7             12160072   1080292  10462084  10% /home
/dev/sda1             31745624  27751428   3994196  88% /media/sda1

```

---

### Post by malcolmx82 on 2008-01-16
no desktop effects at all...
i think the fan is working properly because in windows it never makes the noise it does when i use ubuntu...

so i guess it's not a problem of the fan not working well..anyway...i'm not an expert about this :)

---

### Post by warrior24 on 2008-01-16
Have you tried using compressed air to clean the laptop fan area?

---

### Post by rje_nc on 2008-01-16
I support laptop and desktop systems at a local university, and I have seen this problem many times on different brands of laptops.

In my experience, most laptop overheating issues are due to the cooling fans ingesting dust from the workspace into the fan and across the radiator that is ofen present to transfer the heat from the CPU, graphics card, and other internal components.  If your laptop draws air in from the bottom and exhausts out the side of the system, this can easily cause the airflow to be restricted over time.

I have seen many laptops (many Dell laptops have this problem), where the radiator fins get clogged up much like a clothes dryer filter screen collects lint from your clothes.  Over time, the fins get so clogged they will not pass nearly enough air to provide proper cooling.  I have also seen laptop fans with big hair and/or dust balls in the fan blade assembly, causing similar cooling problems and often leading to fan failure.

You might be able to blow out the fan channel and the cooling fins by blowing "canned air" backwards through the system to dislodge the dust.  The problem is often the dust gets lodged in other areas of your laptop that way.  The best way is to remove your keyboard and top bezels to get access to the fan and carefully clean out - blow out the assembly and make sure the airflow path is clear.

My daughter had an old Toshiba Satellite 1805 running Linux (Slackware I think) at college that would fail when she tried to play a DVD movie or DIVX file. after about 10 minutes.  It ran better under Windows but it was noticeably warm.  Once I cleaned out the cooling channels she did not have any further problems with the laptop.

I honestly think this problem kills more laptop systems that otherwise would run fine than most people realize. 

Hope this helps...

Bob

---

### Post by warrior24 on 2008-01-17
epically when you use it on a bed which covers the air holes with the blanket.

---

### Post by malcolmx82 on 2008-01-17
> My daughter had an old Toshiba Satellite 1805 running Linux (Slackware I think) at college that would fail when she tried to play a DVD movie or DIVX file. after about 10 minutes. It ran better under Windows but it was noticeably warm. Once I cleaned out the cooling channels she did not have any further problems with the laptop.

i think this could be my problem because what i notice is that windows never shuts down but it is really hot..
on the other side there is ubuntu shutting down...
now what i have to learn is how to clean the fan and everything else...
'cause i don't think it will be so easy :neutral:

---

### Post by rje_nc on 2008-01-17
> **malcolmx82 said:**
> i think this could be my problem because what i notice is that windows never shuts down but it is really hot..
on the other side there is ubuntu shutting down...
now what i have to learn is how to clean the fan and everything else...
'cause i don't think it will be so easy :neutral:

On most laptops, removing the keyboard will give decent access to most of the internal components.  Some keyboards can be removed by removing screws underneath the system, they are often marked with a keyboard symbol molded into the back cover next to each screw.  On other systems (many Dell's are like this), you first pry off the plastic bezel above the keyboard to gain access to the keyboard mount screws.

See if you can find some service info on the web.  Lenovo/IBM has excellent hardware maintenance manuals available for almost all their laptops.  I was able to find a hardware manual for my old Compaq Presario 2145 on the HP website.  Otherwise, post the details of your laptop and maybe someone can tell what needs to be removed first for your system.  It isn't too hard if you take your time and be gentle with it!

Bob

---

### Post by moeFinley on 2008-01-20
It seems my laptop (Advent 8212) has a hardware issue that causes unexpected shutdowns.

[http://www.cheaplaptops.org.uk/advent-8112-laptop-with-15ghz-intel-core-2-duo-processor-only-44999/](http://www.cheaplaptops.org.uk/advent-8112-laptop-with-15ghz-intel-core-2-duo-processor-only-44999/)
[http://www.w00tw00t.co.uk/support/viewtopic.php?t=3209&postdays=0&postorder=asc&start=15](http://www.w00tw00t.co.uk/support/viewtopic.php?t=3209&postdays=0&postorder=asc&start=15)
[http://www.w00tw00t.co.uk/support/viewtopic.php?p=6317#6317](http://www.w00tw00t.co.uk/support/viewtopic.php?p=6317#6317)
[http://www.w00tw00t.co.uk/support/viewtopic.php?p=7553](http://www.w00tw00t.co.uk/support/viewtopic.php?p=7553)

Lots of people are blaming the motherboard which is a quite common Intel chipset (GM965 Crestline 	82965GM (GMCH) 	ICH8-M 	May 2007 Core 2 Duo, Celeron M).

---

### Post by malcolmx82 on 2008-01-30
well..
i've made something with a friend of mine and now we know that under windows everything is ok because temperature is always between 50 and 60..
but when i use ubuntu something changes...

could it be due to ati driver?
i've installed the latest ones (i think so) using envy..

and what about apm?i don't know what it is....

---

### Post by malcolmx82 on 2008-01-30
if it can be useful this is the output of the command top when i play neverput

```
top - 23:35:06 up 4 min,  2 users,  load average: 0.48, 0.79, 0.41
Tasks: 112 total,   3 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s): 73.3%us,  1.7%sy,  0.0%ni, 24.7%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    514756k total,   493712k used,    21044k free,    14320k buffers
Swap:   779112k total,        0k used,   779112k free,   231484k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5794 marco     16   0  194m  39m  14m R 74.5  7.8   0:27.54 neverputt                                                                                       
 5315 root      15   0  197m  41m  14m S  0.3  8.3   0:06.83 Xorg                                                                                            
 5676 marco     16   0 28032  12m 8880 S  0.3  2.5   0:00.38 sensors-applet                                                                                  
    1 root      22   0  2948 1856  532 S  0.0  0.4   0:01.20 init                                                                                            
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                                                        
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                         
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                       
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
  121 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod                                                                                         
  140 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  141 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  142 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                         
  193 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1996 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1997 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 2086 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                        
 2096 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 ata/0                                                                                           
 2097 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
 2197 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                     
 2199 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_0                                                                                       
 2200 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                       
 2431 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kjournald                                                                                       
 2657 root      15  -4  3024 1380  408 S  0.0  0.3   0:00.20 udevd                                                                                           
 3592 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 tifm                                                                                            
 3630 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                       
 3636 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kmmcd                                                                                           
 3640 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                                                                                         
 3641 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ipw2200/0                                                                                       
 4010 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald       
```

---

