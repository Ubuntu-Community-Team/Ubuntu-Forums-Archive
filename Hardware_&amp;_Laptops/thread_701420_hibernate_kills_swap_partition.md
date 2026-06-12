---
title: "hibernate kills swap partition"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by RavanH on 2008-02-19
Hi,

Whenever I try to Hibernate, the system goes into hibernation mode (so it seems, though it takes a very long time) but when starting up, it goes iato normal boot-up process. After login into Gnome (or XFce for that matter) I notice my laptop is no longer using swap. 

When I open the Partition Editor to see what is going on, it reports the partition as 'Unknown'... After reformatting it (and changing the /etc/fstab to reflect the new UUID) and rebooting again, swap is restored to normal. 

Below is what /var/log/messages reports around the time of the last incident... Can anyone shed some light on this?

--Thanks :)

At hibernation:
```
Feb 19 04:34:20 packardbell dhcdbd: Unrequested down ?:3
Feb 19 04:34:22 packardbell kernel: [20307.447020] ohci_hcd 0000:00:1c.1: remove, state 1
Feb 19 04:34:23 packardbell kernel: [20307.447206] usb usb2: USB disconnect, address 1
Feb 19 04:34:23 packardbell kernel: [20307.447280] usb 2-1: USB disconnect, address 2
Feb 19 04:34:23 packardbell kernel: [20307.449163] ohci_hcd 0000:00:1c.1: USB bus 2 deregistered
Feb 19 04:34:23 packardbell kernel: [20307.449463] ACPI: PCI interrupt for device 0000:00:1c.1 disabled
Feb 19 04:34:23 packardbell kernel: [20307.449612] ohci_hcd 0000:00:1c.0: remove, state 1
Feb 19 04:34:23 packardbell kernel: [20307.449692] usb usb1: USB disconnect, address 1
Feb 19 04:34:23 packardbell kernel: [20307.449766] usb 1-1: USB disconnect, address 3
Feb 19 04:34:23 packardbell kernel: [20307.450748] usb 1-2: USB disconnect, address 4
Feb 19 04:34:23 packardbell kernel: [20307.451172] ohci_hcd 0000:00:1c.0: USB bus 1 deregistered
Feb 19 04:34:23 packardbell kernel: [20307.451437] ACPI: PCI interrupt for device 0000:00:1c.0 disabled
Feb 19 04:34:23 packardbell kernel: [20307.573822] ehci_hcd 0000:00:1c.3: remove, state 4
Feb 19 04:34:23 packardbell kernel: [20307.573936] usb usb3: USB disconnect, address 1
Feb 19 04:34:23 packardbell kernel: [20307.591861] ehci_hcd 0000:00:1c.3: USB bus 3 deregistered
Feb 19 04:34:23 packardbell kernel: [20307.592955] ACPI: PCI interrupt for device 0000:00:1c.3 disabled
Feb 19 04:34:23 packardbell kernel: [20307.704405] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Feb 19 04:34:23 packardbell kernel: [20307.776879] ACPI: PCI interrupt for device 0000:00:15.0 disabled
```
And at reboot:
```
Feb 19 16:12:46 packardbell syslogd 1.4.1#21ubuntu3: restart.
Feb 19 16:12:46 packardbell kernel: Inspecting /boot/System.map-2.6.22-14-generic
Feb 19 16:12:46 packardbell kernel: Loaded 26085 symbols from /boot/System.map-2.6.22-14-generic.
Feb 19 16:12:46 packardbell kernel: Symbols match kernel version 2.6.22.
Feb 19 16:12:46 packardbell kernel: No module symbols loaded - kernel modules not enabled. 
Feb 19 16:12:46 packardbell kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Feb 19 16:12:46 packardbell kernel: [    0.000000] Command line: BOOT_IMAGE=(hd0,3)/boot/vmlinuz-2.6.22-14-generic root=/dev/hda3 ro splash vga=789 GRUB_DISTRIBUTOR=Debian
Feb 19 16:12:46 packardbell kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 19 16:12:46 packardbell kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb 19 16:12:46 packardbell kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb 19 16:12:46 packardbell kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Feb 19 16:12:46 packardbell kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000037fef000 (usable)
Feb 19 16:12:46 packardbell kernel: [    0.000000]  BIOS-e820: 0000000037ff0000 - 0000000037ffffc0 (ACPI data)
Feb 19 16:12:46 packardbell kernel: [    0.000000]  BIOS-e820: 0000000037ffffc0 - 0000000038000000 (ACPI NVS)
Feb 19 16:12:46 packardbell kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Feb 19 16:12:46 packardbell kernel: [    0.000000] end_pfn_map = 1048576
Feb 19 16:12:46 packardbell kernel: [    0.000000] DMI 2.3 present.
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000E5010 checksum 0
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: RSDP 000E5010, 0014 (r0 OID_00)
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: RSDT 37FFC310, 002C (r1 INSYDE FACP_000      100 0000    10200)
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: FACP 37FFFB00, 0074 (r1 INSYDE FACP_000      100 0000    10200)
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: DSDT 37FFC350, 37A5 (r1 INSYDE   INT810     1002 INTL 20041105)
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: FACS 37FFFFC0, 0040
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: APIC 37FFFB90, 0068 (r1 INSYDE APIC_000 30303030 0000    10200)
Feb 19 16:12:46 packardbell kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Feb 19 16:12:46 packardbell kernel: [    0.000000] No NUMA configuration found
Feb 19 16:12:46 packardbell kernel: [    0.000000] Faking a node at 0000000000000000-0000000037fef000
Feb 19 16:12:46 packardbell kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000037fef000
Feb 19 16:12:46 packardbell kernel: [    0.000000] No mptable found.
Feb 19 16:12:46 packardbell kernel: [    0.000000] Zone PFN ranges:
Feb 19 16:12:46 packardbell kernel: [    0.000000]   DMA             0 ->     4096
Feb 19 16:12:46 packardbell kernel: [    0.000000]   DMA32        4096 ->  1048576
Feb 19 16:12:46 packardbell kernel: [    0.000000]   Normal    1048576 ->  1048576
Feb 19 16:12:46 packardbell kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb 19 16:12:46 packardbell kernel: [    0.000000]     0:        0 ->      159
Feb 19 16:12:46 packardbell kernel: [    0.000000]     0:      256 ->   229359
Feb 19 16:12:46 packardbell kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 19 16:12:46 packardbell kernel: [    0.000000] Processor #0 (Bootup-CPU)
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 19 16:12:46 packardbell kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 19 16:12:46 packardbell kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb 19 16:12:46 packardbell kernel: [    0.000000] Setting APIC routing to flat
Feb 19 16:12:46 packardbell kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 19 16:12:46 packardbell kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Feb 19 16:12:46 packardbell kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Feb 19 16:12:46 packardbell kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Feb 19 16:12:46 packardbell kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:c7f80000)
Feb 19 16:12:46 packardbell kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Feb 19 16:12:46 packardbell kernel: [    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
Feb 19 16:12:46 packardbell kernel: [    0.000000] Built 1 zonelists.  Total pages: 225003
Feb 19 16:12:46 packardbell kernel: [    0.000000] Kernel command line: BOOT_IMAGE=(hd0,3)/boot/vmlinuz-2.6.22-14-generic root=/dev/hda3 ro splash vga=789 GRUB_DISTRIBUTOR=Debian
Feb 19 16:12:46 packardbell kernel: [    0.000000] Initializing CPU#0
Feb 19 16:12:46 packardbell kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Feb 19 16:12:46 packardbell kernel: [   11.808524] time.c: Detected 1591.858 MHz processor.
Feb 19 16:12:46 packardbell kernel: [   11.808576] Console: colour dummy device 80x25
Feb 19 16:12:46 packardbell kernel: [   11.808648] Checking aperture...
Feb 19 16:12:46 packardbell kernel: [   11.808653] CPU 0: aperture @ 0 size 32 MB
Feb 19 16:12:46 packardbell kernel: [   11.820690] No AGP bridge found
Feb 19 16:12:46 packardbell kernel: [   11.833784] Memory: 892084k/917436k available (2274k kernel code, 24964k reserved, 1185k data, 296k init)
Feb 19 16:12:46 packardbell kernel: [   11.833856] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Feb 19 16:12:46 packardbell kernel: [   11.910488] Calibrating delay using timer specific routine.. 3186.94 BogoMIPS (lpj=6373898)
Feb 19 16:12:46 packardbell kernel: [   11.910536] Security Framework v1.0.0 initialized
Feb 19 16:12:46 packardbell kernel: [   11.910546] SELinux:  Disabled at boot.
Feb 19 16:12:46 packardbell kernel: [   11.910662] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 19 16:12:46 packardbell kernel: [   11.911748] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Feb 19 16:12:46 packardbell kernel: [   11.912274] Mount-cache hash table entries: 256
Feb 19 16:12:46 packardbell kernel: [   11.912458] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb 19 16:12:46 packardbell kernel: [   11.912464] CPU: L2 Cache: 1024K (64 bytes/line)
Feb 19 16:12:46 packardbell kernel: [   11.912469] CPU 0/0 -> Node 0
Feb 19 16:12:46 packardbell kernel: [   11.912493] SMP alternatives: switching to UP code
Feb 19 16:12:46 packardbell kernel: [   11.912873] Early unpacking initramfs... done
Feb 19 16:12:46 packardbell kernel: [   12.302544] ACPI: Core revision 20070126
Feb 19 16:12:46 packardbell kernel: [   12.302604] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Feb 19 16:12:46 packardbell kernel: [   12.346314] Using local APIC timer interrupts.
Feb 19 16:12:46 packardbell kernel: [   12.409114] result 12436389
Feb 19 16:12:46 packardbell kernel: [   12.409117] Detected 12.436 MHz APIC timer.
Feb 19 16:12:46 packardbell kernel: [   12.410340] Brought up 1 CPUs
Feb 19 16:12:46 packardbell kernel: [   12.410667] NET: Registered protocol family 16
Feb 19 16:12:46 packardbell kernel: [   12.410758] ACPI: bus type pci registered
Feb 19 16:12:46 packardbell kernel: [   12.410768] PCI: Using configuration type 1
Feb 19 16:12:46 packardbell kernel: [   12.412069] ACPI: EC: GPE=0x03, ports=0x66, 0x62
Feb 19 16:12:46 packardbell kernel: [   12.413977] ACPI: Interpreter enabled
Feb 19 16:12:46 packardbell kernel: [   12.413982] ACPI: (supports S0 S3 S4 S5)
Feb 19 16:12:46 packardbell kernel: [   12.414000] ACPI: Using IOAPIC for interrupt routing
Feb 19 16:12:46 packardbell kernel: [   12.419439] ACPI: EC: GPE=0x03, ports=0x66, 0x62
Feb 19 16:12:46 packardbell kernel: [   12.419484] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 19 16:12:46 packardbell kernel: [   12.420320] PCI quirk: region 1000-103f claimed by ali7101 ACPI
Feb 19 16:12:46 packardbell kernel: [   12.430514] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 9 10 *11)
Feb 19 16:12:46 packardbell kernel: [   12.430634] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7 9 10 11)
Feb 19 16:12:46 packardbell kernel: [   12.430750] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 9 *10 11)
Feb 19 16:12:46 packardbell kernel: [   12.430863] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
Feb 19 16:12:46 packardbell kernel: [   12.430980] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 *7 9 10 11)
Feb 19 16:12:46 packardbell kernel: [   12.431093] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 7 9 10 11) *0, disabled.
Feb 19 16:12:46 packardbell kernel: [   12.431210] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 7 9 10 *11)
Feb 19 16:12:46 packardbell kernel: [   12.431326] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 7 9 10 *11)
Feb 19 16:12:46 packardbell kernel: [   12.431442] ACPI: PCI Interrupt Link [LNKU] (IRQs 5 *7 9 10 11)
Feb 19 16:12:46 packardbell kernel: [   12.431518] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 19 16:12:46 packardbell kernel: [   12.431532] pnp: PnP ACPI init
Feb 19 16:12:46 packardbell kernel: [   12.431540] ACPI: bus type pnp registered
Feb 19 16:12:46 packardbell kernel: [   12.433830] pnp: PnP ACPI: found 9 devices
Feb 19 16:12:46 packardbell kernel: [   12.433834] ACPI: ACPI bus type pnp unregistered
Feb 19 16:12:46 packardbell kernel: [   12.433887] PCI: Using ACPI for IRQ routing
Feb 19 16:12:46 packardbell kernel: [   12.433891] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Feb 19 16:12:46 packardbell kernel: [   12.433980] NET: Registered protocol family 8
Feb 19 16:12:46 packardbell kernel: [   12.433984] NET: Registered protocol family 20
Feb 19 16:12:46 packardbell kernel: [   12.434096] pnp: 00:05: iomem range 0xe0000-0xfffff could not be reserved
Feb 19 16:12:46 packardbell kernel: [   12.434102] pnp: 00:05: iomem range 0xb0000000-0xbfffffff could not be reserved
Feb 19 16:12:46 packardbell kernel: [   12.434107] pnp: 00:05: iomem range 0xe0000000-0xefffffff has been reserved
Feb 19 16:12:46 packardbell kernel: [   12.434112] pnp: 00:05: iomem range 0xfffc0000-0xffffffff could not be reserved
Feb 19 16:12:46 packardbell kernel: [   12.434122] pnp: 00:07: ioport range 0x330-0x331 has been reserved
Feb 19 16:12:46 packardbell kernel: [   12.434126] pnp: 00:07: ioport range 0x480-0x48f has been reserved
Feb 19 16:12:46 packardbell kernel: [   12.434131] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
Feb 19 16:12:46 packardbell kernel: [   12.434135] pnp: 00:07: ioport range 0x1000-0x107f could not be reserved
Feb 19 16:12:46 packardbell kernel: [   12.434140] pnp: 00:07: ioport range 0x1400-0x140f has been reserved
Feb 19 16:12:46 packardbell kernel: [   12.434285] Time: tsc clocksource has been installed.
Feb 19 16:12:46 packardbell kernel: [   12.434450] PCI: Bridge: 0000:00:01.0
Feb 19 16:12:46 packardbell kernel: [   12.434455]   IO window: c000-dfff
Feb 19 16:12:46 packardbell kernel: [   12.434459]   MEM window: c0000000-cfffffff
Feb 19 16:12:46 packardbell kernel: [   12.434464]   PREFETCH window: 90000000-9fffffff
Feb 19 16:12:46 packardbell kernel: [   12.434468] PCI: Bus 3, cardbus bridge: 0000:00:14.0
Feb 19 16:12:46 packardbell kernel: [   12.434472]   IO window: 00001800-000018ff
Feb 19 16:12:46 packardbell kernel: [   12.434478]   IO window: 00001c00-00001cff
Feb 19 16:12:46 packardbell kernel: [   12.434485]   PREFETCH window: 40000000-43ffffff
Feb 19 16:12:46 packardbell kernel: [   12.434491]   MEM window: 44000000-47ffffff
Feb 19 16:12:46 packardbell kernel: [   12.434498] PCI: Bridge: 0000:00:19.0
Feb 19 16:12:46 packardbell kernel: [   12.434502]   IO window: a000-bfff
Feb 19 16:12:46 packardbell kernel: [   12.434508]   MEM window: b8000000-bfffffff
Feb 19 16:12:46 packardbell kernel: [   12.434514]   PREFETCH window: 88000000-8fffffff
Feb 19 16:12:46 packardbell kernel: [   12.434542] ACPI: PCI Interrupt 0000:00:14.0[A] -> GSI 17 (level, low) -> IRQ 17
Feb 19 16:12:46 packardbell kernel: [   12.434630] NET: Registered protocol family 2
Feb 19 16:12:46 packardbell kernel: [   12.470337] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
Feb 19 16:12:46 packardbell kernel: [   12.470808] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
Feb 19 16:12:46 packardbell kernel: [   12.473632] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 19 16:12:46 packardbell kernel: [   12.474634] TCP: Hash tables configured (established 131072 bind 65536)
Feb 19 16:12:46 packardbell kernel: [   12.474644] TCP reno registered
Feb 19 16:12:46 packardbell kernel: [   12.486431] checking if image is initramfs... it is
Feb 19 16:12:46 packardbell kernel: [   13.242236] Freeing initrd memory: 7746k freed
Feb 19 16:12:46 packardbell kernel: [   13.249823] audit: initializing netlink socket (disabled)
Feb 19 16:12:46 packardbell kernel: [   13.249844] audit(1203437530.384:1): initialized
Feb 19 16:12:46 packardbell kernel: [   13.251893] VFS: Disk quotas dquot_6.5.1
Feb 19 16:12:46 packardbell kernel: [   13.251953] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 19 16:12:46 packardbell kernel: [   13.252048] io scheduler noop registered
Feb 19 16:12:46 packardbell kernel: [   13.252052] io scheduler anticipatory registered
Feb 19 16:12:46 packardbell kernel: [   13.252055] io scheduler deadline registered
Feb 19 16:12:46 packardbell kernel: [   13.252149] io scheduler cfq registered (default)
Feb 19 16:12:46 packardbell kernel: [   13.252157] PCI: MSI quirk detected. MSI deactivated.
Feb 19 16:12:46 packardbell kernel: [   13.360466] Real Time Clock Driver v1.12ac
Feb 19 16:12:46 packardbell kernel: [   13.360565] Linux agpgart interface v0.102 (c) Dave Jones
Feb 19 16:12:46 packardbell kernel: [   13.360570] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Feb 19 16:12:46 packardbell kernel: [   13.361144] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 22
Feb 19 16:12:46 packardbell kernel: [   13.361930] 0000:00:1d.1: ttyS0 at I/O 0xe220 (irq = 22) is a 8250
Feb 19 16:12:46 packardbell kernel: [   13.362139] 0000:00:1d.1: ttyS1 at I/O 0xe228 (irq = 22) is a 8250
Feb 19 16:12:46 packardbell kernel: [   13.362556] 0000:00:1d.1: ttyS2 at I/O 0xe240 (irq = 22) is a 8250
Feb 19 16:12:46 packardbell kernel: [   13.362716] 0000:00:1d.1: ttyS3 at I/O 0xe248 (irq = 22) is a 8250
Feb 19 16:12:46 packardbell kernel: [   13.362796] Couldn't register serial port 0000:00:1d.1: -28
Feb 19 16:12:46 packardbell kernel: [   13.363371] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Feb 19 16:12:46 packardbell kernel: [   13.363610] input: Macintosh mouse button emulation as /class/input/input0
Feb 19 16:12:46 packardbell kernel: [   13.363686] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb 19 16:12:46 packardbell kernel: [   13.370624] i8042.c: Detected active multiplexing controller, rev 1.1.
Feb 19 16:12:46 packardbell kernel: [   13.373875] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 19 16:12:46 packardbell kernel: [   13.373882] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Feb 19 16:12:46 packardbell kernel: [   13.373886] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Feb 19 16:12:46 packardbell kernel: [   13.373890] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Feb 19 16:12:46 packardbell kernel: [   13.373894] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Feb 19 16:12:46 packardbell kernel: [   13.374170] mice: PS/2 mouse device common for all mice
Feb 19 16:12:46 packardbell kernel: [   13.374317] TCP cubic registered
Feb 19 16:12:46 packardbell kernel: [   13.374396] NET: Registered protocol family 1
Feb 19 16:12:46 packardbell kernel: [   13.374616] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Feb 19 16:12:46 packardbell kernel: [   13.374627] Freeing unused kernel memory: 296k freed
Feb 19 16:12:46 packardbell kernel: [   13.405939] input: AT Translated Set 2 keyboard as /class/input/input1
Feb 19 16:12:46 packardbell kernel: [   14.580589] AppArmor: AppArmor initialized<5>audit(1203437531.716:2):  type=1505 info="AppArmor initialized" pid=1218
Feb 19 16:12:46 packardbell kernel: [   14.596463] fuse init (API version 7.8)
Feb 19 16:12:46 packardbell kernel: [   14.601181] Failure registering capabilities with primary security module.
Feb 19 16:12:46 packardbell kernel: [   14.622073] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Feb 19 16:12:46 packardbell kernel: [   14.622081] ACPI: Processor [CPU0] (supports 8 throttling states)
Feb 19 16:12:46 packardbell kernel: [   15.247447] ACPI: PCI Interrupt 0000:00:14.1[B] -> GSI 18 (level, low) -> IRQ 18
Feb 19 16:12:46 packardbell kernel: [   15.297683] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[d0000000-d00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 19 16:12:46 packardbell kernel: [   15.392274] usbcore: registered new interface driver usbfs
Feb 19 16:12:46 packardbell kernel: [   15.392302] usbcore: registered new interface driver hub
Feb 19 16:12:46 packardbell kernel: [   15.392326] usbcore: registered new device driver usb
Feb 19 16:12:46 packardbell kernel: [   15.393096] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
Feb 19 16:12:46 packardbell kernel: [   15.393445] ohci_hcd 0000:00:1c.0: OHCI Host Controller
Feb 19 16:12:46 packardbell kernel: [   15.393610] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 1
Feb 19 16:12:46 packardbell kernel: [   15.393638] ohci_hcd 0000:00:1c.0: irq 17, io mem 0xf8002000
Feb 19 16:12:46 packardbell kernel: [   15.452045] SCSI subsystem initialized
Feb 19 16:12:46 packardbell kernel: [   15.483548] usb usb1: configuration #1 chosen from 1 choice
Feb 19 16:12:46 packardbell kernel: [   15.483580] hub 1-0:1.0: USB hub found
Feb 19 16:12:46 packardbell kernel: [   15.483592] hub 1-0:1.0: 3 ports detected
Feb 19 16:12:46 packardbell kernel: [   15.585276] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 18 (level, low) -> IRQ 18
Feb 19 16:12:46 packardbell kernel: [   15.585547] ohci_hcd 0000:00:1c.1: OHCI Host Controller
Feb 19 16:12:46 packardbell kernel: [   15.585617] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 2
Feb 19 16:12:46 packardbell kernel: [   15.585636] ohci_hcd 0000:00:1c.1: irq 18, io mem 0xf8003000
Feb 19 16:12:46 packardbell kernel: [   15.629084] Marking TSC unstable due to possible TSC halt in C2
Feb 19 16:12:46 packardbell kernel: [   15.629092] Time: acpi_pm clocksource has been installed.
Feb 19 16:12:46 packardbell kernel: [   15.643199] usb usb2: configuration #1 chosen from 1 choice
Feb 19 16:12:46 packardbell kernel: [   15.643230] hub 2-0:1.0: USB hub found
Feb 19 16:12:46 packardbell kernel: [   15.643239] hub 2-0:1.0: 3 ports detected
Feb 19 16:12:46 packardbell kernel: [   15.745557] PCI: Enabling device 0000:00:1c.3 (0000 -> 0002)
Feb 19 16:12:46 packardbell kernel: [   15.745568] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 23
Feb 19 16:12:46 packardbell kernel: [   15.745857] ehci_hcd 0000:00:1c.3: EHCI Host Controller
Feb 19 16:12:46 packardbell kernel: [   15.745931] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 3
Feb 19 16:12:46 packardbell kernel: [   15.745973] ehci_hcd 0000:00:1c.3: debug port 1
Feb 19 16:12:46 packardbell kernel: [   15.769061] ehci_hcd 0000:00:1c.3: irq 23, io mem 0x48001000
Feb 19 16:12:46 packardbell kernel: [   15.889001] usb 1-1: new low speed USB device using ohci_hcd and address 2
Feb 19 16:12:46 packardbell kernel: [   15.889022] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb 19 16:12:46 packardbell kernel: [   15.889132] usb usb3: configuration #1 chosen from 1 choice
Feb 19 16:12:46 packardbell kernel: [   15.889160] hub 3-0:1.0: USB hub found
Feb 19 16:12:46 packardbell kernel: [   15.889167] hub 3-0:1.0: 8 ports detected
Feb 19 16:12:46 packardbell kernel: [   15.998587] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb 19 16:12:46 packardbell kernel: [   15.998595] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb 19 16:12:46 packardbell kernel: [   15.999445] ALI15X3: IDE controller at PCI slot 0000:00:1f.0
Feb 19 16:12:46 packardbell kernel: [   15.999465] ACPI: Unable to derive IRQ for device 0000:00:1f.0
Feb 19 16:12:46 packardbell kernel: [   15.999468] ACPI: PCI Interrupt 0000:00:1f.0[A]: no GSI
Feb 19 16:12:46 packardbell kernel: [   15.999478] ALI15X3: chipset revision 199
Feb 19 16:12:46 packardbell kernel: [   15.999480] ALI15X3: not 100%% native mode: will probe irqs later
Feb 19 16:12:46 packardbell kernel: [   15.999501]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
Feb 19 16:12:46 packardbell kernel: [   15.999519]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
Feb 19 16:12:46 packardbell kernel: [   16.285164] hda: IC25N080ATMR04-0, ATA DISK drive
Feb 19 16:12:46 packardbell kernel: [   16.956860] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb 19 16:12:46 packardbell kernel: [   17.300464] usb 1-1: new low speed USB device using ohci_hcd and address 3
Feb 19 16:12:46 packardbell kernel: [   17.512595] usb 1-1: configuration #1 chosen from 1 choice
Feb 19 16:12:46 packardbell kernel: [   17.712629] hdc: Slimtype DVDRW SOSW-833S, ATAPI CD/DVD-ROM drive
Feb 19 16:12:46 packardbell kernel: [   17.816271] usb 1-2: new full speed USB device using ohci_hcd and address 4
Feb 19 16:12:46 packardbell kernel: [   18.025385] usb 1-2: configuration #1 chosen from 1 choice
Feb 19 16:12:46 packardbell kernel: [   18.332078] usb 2-1: new full speed USB device using ohci_hcd and address 2
Feb 19 16:12:46 packardbell kernel: [   18.384210] ide1 at 0x170-0x177,0x376 on irq 15
Feb 19 16:12:46 packardbell kernel: [   18.392184] hda: max request size: 512KiB
Feb 19 16:12:46 packardbell kernel: [   18.401056] hda: 156301488 sectors (80026 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
Feb 19 16:12:46 packardbell kernel: [   18.401825] hda: cache flushes supported
Feb 19 16:12:46 packardbell kernel: [   18.401869]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 hda8 >
Feb 19 16:12:46 packardbell kernel: [   18.535251] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb 19 16:12:46 packardbell kernel: [   18.535262] Uniform CD-ROM driver Revision: 3.20
Feb 19 16:12:46 packardbell kernel: [   18.535961] usb 2-1: configuration #1 chosen from 1 choice
Feb 19 16:12:46 packardbell kernel: [   18.539087] usbcore: registered new interface driver hiddev
Feb 19 16:12:46 packardbell kernel: [   18.547918] input: HID 0d8c:000c as /class/input/input2
Feb 19 16:12:46 packardbell kernel: [   18.547933] input: USB HID v1.00 Device [HID 0d8c:000c] on usb-0000:00:1c.1-1
Feb 19 16:12:46 packardbell kernel: [   18.547949] usbcore: registered new interface driver usbhid
Feb 19 16:12:46 packardbell kernel: [   18.547953] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Feb 19 16:12:46 packardbell kernel: [   19.305321] EXT3-fs: INFO: recovery required on readonly filesystem.
Feb 19 16:12:46 packardbell kernel: [   19.305327] EXT3-fs: write access will be enabled during recovery.
Feb 19 16:12:46 packardbell kernel: [   23.604960] kjournald starting.  Commit interval 5 seconds
Feb 19 16:12:46 packardbell kernel: [   23.604978] EXT3-fs: recovery complete.
Feb 19 16:12:46 packardbell kernel: [   23.612956] EXT3-fs: mounted filesystem with ordered data mode.
Feb 19 16:12:46 packardbell kernel: [   34.744050] Yenta: CardBus bridge found at 0000:00:14.0 [1631:c00e]
Feb 19 16:12:46 packardbell kernel: [   34.744075] Yenta: Enabling burst memory read transactions
Feb 19 16:12:46 packardbell kernel: [   34.744080] Yenta: Using CSCINT to route CSC interrupts to PCI
Feb 19 16:12:46 packardbell kernel: [   34.744083] Yenta: Routing CardBus interrupts to PCI
Feb 19 16:12:46 packardbell kernel: [   34.744089] Yenta TI: socket 0000:00:14.0, mfunc 0x01001022, devctl 0x66
Feb 19 16:12:46 packardbell kernel: [   34.821497] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 19 16:12:46 packardbell kernel: [   34.974740] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
Feb 19 16:12:46 packardbell kernel: [   34.974747] Socket status: 30000086
Feb 19 16:12:46 packardbell kernel: [   34.975091] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 19 16:12:46 packardbell kernel: [   35.182348] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
Feb 19 16:12:46 packardbell kernel: [   35.184145] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
Feb 19 16:12:46 packardbell kernel: [   35.213698] eth0: ULi M5263 at pci0000:00:1b.0, 00:40:d0:7d:d1:46, irq 20.
Feb 19 16:12:46 packardbell kernel: [   35.509234] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
Feb 19 16:12:46 packardbell kernel: [   35.509241] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
Feb 19 16:12:46 packardbell kernel: [   36.186230] input: PC Speaker as /class/input/input3
Feb 19 16:12:46 packardbell kernel: [   36.313884] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x3aa0b4, caps: 0xa04713/0x200000
Feb 19 16:12:46 packardbell kernel: [   36.318893] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb 19 16:12:46 packardbell kernel: [   36.345528] [fglrx] Maximum main memory to use for locked dma buffers: 799 MBytes.
Feb 19 16:12:46 packardbell kernel: [   36.345566] [fglrx] ASYNCIO init succeed!
Feb 19 16:12:46 packardbell kernel: [   36.346073] [fglrx] PAT is enabled successfully!
Feb 19 16:12:46 packardbell kernel: [   36.346105] [fglrx] module loaded - fglrx 8.45.4 [Jan 16 2008] on minor 0
Feb 19 16:12:46 packardbell kernel: [   36.359730] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Feb 19 16:12:46 packardbell kernel: [   36.542570] ACPI: PCI Interrupt 0000:00:15.0[A] -> GSI 18 (level, low) -> IRQ 18
Feb 19 16:12:46 packardbell kernel: [   36.602780] input: Acecad USB Tablet as /class/input/input5
Feb 19 16:12:46 packardbell kernel: [   36.602857] usbcore: registered new interface driver usb_acecad
Feb 19 16:12:46 packardbell kernel: [   36.602862] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/tablet/acecad.c: v3.2:USB Acecad Flair tablet driver
Feb 19 16:12:46 packardbell kernel: [   36.651077] Linux video capture interface: v2.00
Feb 19 16:12:46 packardbell kernel: [   36.715328] usbcore: registered new interface driver xpad
Feb 19 16:12:46 packardbell kernel: [   36.715336] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
Feb 19 16:12:46 packardbell kernel: [   36.844275] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. SONIX JPEG (sn9c1xx) 
Feb 19 16:12:46 packardbell kernel: [   36.846725] usbcore: registered new interface driver gspca
Feb 19 16:12:46 packardbell kernel: [   36.846732] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
Feb 19 16:12:46 packardbell kernel: [   37.041109] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
Feb 19 16:12:46 packardbell kernel: [   37.041160] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
Feb 19 16:12:46 packardbell kernel: [   37.041214] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
Feb 19 16:12:46 packardbell kernel: [   37.041282] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
Feb 19 16:12:46 packardbell kernel: [   37.220099] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
Feb 19 16:12:46 packardbell kernel: [   37.278341] usbcore: registered new interface driver snd-usb-audio
Feb 19 16:12:46 packardbell kernel: [   37.281126] intel8x0_measure_ac97_clock: measured 53067 usecs
Feb 19 16:12:46 packardbell kernel: [   37.281134] intel8x0: clocking to 48000
Feb 19 16:12:46 packardbell kernel: [   39.067646] EXT3 FS on hda3, internal journal
Feb 19 16:12:46 packardbell kernel: [   43.711765] kjournald starting.  Commit interval 5 seconds
Feb 19 16:12:46 packardbell kernel: [   43.724811] EXT3 FS on hda6, internal journal
Feb 19 16:12:46 packardbell kernel: [   43.724817] EXT3-fs: mounted filesystem with ordered data mode.
Feb 19 16:12:46 packardbell kernel: [   47.293720] ACPI: Battery Slot [BAT0] (battery present)
Feb 19 16:12:46 packardbell kernel: [   47.447988] No dock devices found.
Feb 19 16:12:46 packardbell kernel: [   47.577263] ACPI: AC Adapter [AC] (on-line)
Feb 19 16:12:46 packardbell kernel: [   47.710641] input: Power Button (FF) as /class/input/input6
Feb 19 16:12:46 packardbell kernel: [   47.715220] ACPI: Power Button (FF) [PWRF]
Feb 19 16:12:46 packardbell kernel: [   47.745798] input: Sleep Button (CM) as /class/input/input7
Feb 19 16:12:46 packardbell kernel: [   47.750355] ACPI: Sleep Button (CM) [SBTN]
Feb 19 16:12:46 packardbell kernel: [   47.780995] input: Lid Switch as /class/input/input8
Feb 19 16:12:46 packardbell kernel: [   47.785590] ACPI: Lid Switch [LID]
Feb 19 16:12:46 packardbell kernel: [   47.987244] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-30 processors (version 2.00.00)
Feb 19 16:12:46 packardbell kernel: [   47.987284] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4
Feb 19 16:12:46 packardbell kernel: [   47.987287] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
Feb 19 16:12:47 packardbell kernel: [   49.704912] lp: driver loaded but no devices found
Feb 19 16:12:47 packardbell kernel: [   49.752227] ppdev: user-space parallel port driver
Feb 19 16:12:47 packardbell kernel: [   49.927958] input: Unspecified device as /class/input/input9
Feb 19 16:12:48 packardbell kernel: [   50.340547] audit(1203433968.108:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5061 profile="/usr/sbin/cupsd"
Feb 19 16:12:50 packardbell kernel: [   52.903552] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
Feb 19 16:12:53 packardbell kernel: [   55.811779] NET: Registered protocol family 10
Feb 19 16:12:53 packardbell kernel: [   55.811956] lo: Disabled Privacy Extensions
Feb 19 16:12:53 packardbell kernel: [   55.812178] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 16:12:53 packardbell kernel: [   55.945912] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Feb 19 16:12:53 packardbell kernel: [   56.214044] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Feb 19 16:12:54 packardbell kernel: [   56.230057] NFSD: starting 90-second grace period
Feb 19 16:12:55 packardbell kernel: [   57.289549] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
Feb 19 16:12:56 packardbell kernel: [   58.505798] Failure registering capabilities with primary security module.
Feb 19 16:12:56 packardbell dhcdbd: Started up.
Feb 19 16:12:57 packardbell kernel: [   58.693791] Bluetooth: Core ver 2.11
Feb 19 16:12:57 packardbell kernel: [   58.693894] NET: Registered protocol family 31
Feb 19 16:12:57 packardbell kernel: [   58.693897] Bluetooth: HCI device and connection manager initialized
Feb 19 16:12:57 packardbell kernel: [   58.693901] Bluetooth: HCI socket layer initialized
Feb 19 16:12:57 packardbell kernel: [   58.708313] Bluetooth: L2CAP ver 2.8
Feb 19 16:12:57 packardbell kernel: [   58.708317] Bluetooth: L2CAP socket layer initialized
Feb 19 16:12:57 packardbell kernel: [   58.745596] Bluetooth: RFCOMM socket layer initialized
Feb 19 16:12:57 packardbell kernel: [   58.745681] Bluetooth: RFCOMM TTY layer initialized
Feb 19 16:12:57 packardbell kernel: [   58.745684] Bluetooth: RFCOMM ver 1.8
Feb 19 16:12:59 packardbell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Feb 19 16:12:59 packardbell kernel: [   59.791935] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
Feb 19 16:13:01 packardbell kernel: [   60.830391] NET: Registered protocol family 17
Feb 19 16:13:01 packardbell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Feb 19 16:13:01 packardbell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Feb 19 16:13:01 packardbell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Feb 19 16:13:03 packardbell kernel: [   62.506035] [fglrx] GART Table is not in FRAME_BUFFER range 
Feb 19 16:13:03 packardbell kernel: [   62.506047] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Feb 19 16:13:03 packardbell kernel: [   62.506051] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
Feb 19 16:13:04 packardbell kernel: [   63.312926] [fglrx] interrupt source 20008000 successfully enabled
Feb 19 16:13:04 packardbell kernel: [   63.312933] [fglrx] enable ID = 0x00000004
Feb 19 16:13:04 packardbell kernel: [   63.313079] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
```

System: PackardBell AMD Turion 64bit laptop with Ubuntu Gutsy AMD64, Gnome/XFce, Linux kernel 2.6.22-14 and ATI Radeon Xpress 200M running on  Catalyst 8.01 driver...

---

