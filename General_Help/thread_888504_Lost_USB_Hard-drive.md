---
title: "Lost USB Hard-drive"
date: 2008-08-13
forum: General Help
---

### Post by DisruptiveTechnology on 2008-08-13
Hi

I am suffering from lost drives. I use typically a lot of external HD's. However I am finding that after I had a couple of systems crashes and a hard reboots, I can no longer find these hard-drives at all on the system. They are plugged in and should be working as far as the hardware is concerned. I cannot even find anything in fstab. I enclose some diagnostics:

mount

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29643   238107366   83  Linux
/dev/sda2           29644       30394     6032407+   5  Extended
/dev/sda5           29644       30394     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System


dmesg

[    0.000000] Linux version 2.6.20-17-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed Jul 9 22:24:42 UTC 2008 (Ubuntu 2.6.20-17.37-generic)
[    0.000000] Command line: root=UUID=bde061d6-398f-4047-82b9-d44097a37e6d ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe8ac00 (usable)
[    0.000000]  BIOS-e820: 000000007fe8ac00 - 000000007fe8cc00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fe8cc00 - 000000007fe8ec00 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe8ec00 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 160) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523914) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x00000000000fec30
[    0.000000] ACPI: RSDT (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x00000000000fcb47
[    0.000000] ACPI: FADT (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x00000000000fcbab
[    0.000000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000fffdbe16
[    0.000000] ACPI: MADT (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x00000000000fcc1f
[    0.000000] ACPI: BOOT (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x00000000000fccc9
[    0.000000] ACPI: ASF! (v016 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x00000000000fccf1
[    0.000000] ACPI: MCFG (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x00000000000fcd58
[    0.000000] ACPI: HPET (v001 DELL    WS 670  0x00000007 ASL  0x00000061) @ 0x00000000000fcd96
[    0.000000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fe8a000
[    0.000000] Entering add_active_range(0, 0, 160) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523914) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fe8a000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      160
[    0.000000]     0:      256 ->   523914
[    0.000000] On node 0 totalpages: 523818
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1087 pages reserved
[    0.000000]   DMA zone: 2857 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7106 pages used for memmap
[    0.000000]   DMA32 zone: 512712 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Intel E7520/7320/7525 detected.<6>ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x06] enabled)
[    0.000000] Processor #6
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] enabled)
[    0.000000] Processor #7
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec80000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, address 0xfec80000, GSI 24-47
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec80800] gsi_base[48])
[    0.000000] IOAPIC[2]: apic_id 10, address 0xfec80800, GSI 48-71
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000f0000
[    0.000000] Nosave address range: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515569
[    0.000000] Kernel command line: root=UUID=bde061d6-398f-4047-82b9-d44097a37e6d ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   14.607751] Console: colour VGA+ 80x25
[   14.608829] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   14.609882] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.610081] Checking aperture...
[   14.610091] Calgary: detecting Calgary via BIOS EBDA area
[   14.610094] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   14.628858] Memory: 2051988k/2095656k available (2218k kernel code, 43284k reserved, 1162k data, 304k init)
[   14.705018] Calibrating delay using timer specific routine.. 5990.70 BogoMIPS (lpj=11981417)
[   14.705082] Security Framework v1.0.0 initialized
[   14.705088] SELinux:  Disabled at boot.
[   14.705119] Mount-cache hash table entries: 256
[   14.705290] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   14.705293] CPU: L2 cache: 2048K
[   14.705296] CPU 0/0 -> Node 0
[   14.705298] using mwait in idle threads.
[   14.705300] CPU: Physical Processor ID: 0
[   14.705302] CPU: Processor Core ID: 0
[   14.705312] CPU0: Thermal monitoring enabled (TM1)
[   14.705325] SMP alternatives: switching to UP code
[   14.705659] Early unpacking initramfs... done
[   15.008531] ACPI: Core revision 20060707
[   15.014035] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   15.084881] Using local APIC timer interrupts.
[   15.118283] result 12469502
[   15.118286] Detected 12.469 MHz APIC timer.
[   15.121079] SMP alternatives: switching to SMP code
[   15.121257] Booting processor 1/4 APIC 0x6
[   15.131857] Initializing CPU#1
[   15.208770] Calibrating delay using timer specific routine.. 5985.63 BogoMIPS (lpj=11971276)
[   15.208781] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.208784] CPU: L2 cache: 2048K
[   15.208786] CPU 1/6 -> Node 0
[   15.208789] CPU: Physical Processor ID: 3
[   15.208790] CPU: Processor Core ID: 0
[   15.208800] CPU1: Thermal monitoring enabled (TM1)
[   15.209185]                   Intel(R) Xeon(TM) CPU 3.00GHz stepping 03
[   15.213006] SMP alternatives: switching to SMP code
[   15.213039] Booting processor 2/4 APIC 0x1
[   15.223683] Initializing CPU#2
[   15.300726] Calibrating delay using timer specific routine.. 5985.63 BogoMIPS (lpj=11971279)
[   15.300740] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.300742] CPU: L2 cache: 2048K
[   15.300746] CPU 2/1 -> Node 0
[   15.300748] CPU: Physical Processor ID: 0
[   15.300750] CPU: Processor Core ID: 0
[   15.300762] CPU2: Thermal monitoring enabled (TM1)
[   15.301166]                   Intel(R) Xeon(TM) CPU 3.00GHz stepping 03
[   15.304986] SMP alternatives: switching to SMP code
[   15.305110] Booting processor 3/4 APIC 0x7
[   15.315693] Initializing CPU#3
[   15.392682] Calibrating delay using timer specific routine.. 5985.65 BogoMIPS (lpj=11971305)
[   15.392693] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.392695] CPU: L2 cache: 2048K
[   15.392698] CPU 3/7 -> Node 0
[   15.392700] CPU: Physical Processor ID: 3
[   15.392701] CPU: Processor Core ID: 0
[   15.392712] CPU3: Thermal monitoring enabled (TM1)
[   15.393098]                   Intel(R) Xeon(TM) CPU 3.00GHz stepping 03
[   15.396697] Brought up 4 CPUs
[   15.396744] time.c: Using 14.318180 MHz WALL HPET GTOD HPET/TSC timer.
[   15.396747] time.c: Detected 2992.694 MHz processor.
[   15.806277] migration_cost=7,1923
[   15.806685] Time: 10:19:52  Date: 07/13/108
[   15.806735] NET: Registered protocol family 16
[   15.806828] ACPI: bus type pci registered
[   15.806837] PCI: Using configuration type 1
[   15.841774] ACPI: Interpreter enabled
[   15.841777] ACPI: Using IOAPIC for interrupt routing
[   15.845096] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.845103] PCI: Probing PCI hardware (bus 00)
[   15.845125] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   15.848762] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   15.848766] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   15.849016] PCI: PXH quirk detected, disabling MSI for SHPC device
[   15.849057] PCI: PXH quirk detected, disabling MSI for SHPC device
[   15.849553] Boot video device is 0000:05:00.0
[   15.849718] PCI: Transparent bridge - 0000:00:1e.0
[   15.849783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.453329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   16.461179] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1.PCI2._PRT]
[   16.468990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1.PCI3._PRT]
[   16.476880] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[   16.482596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[   16.488309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI6._PRT]
[   16.529147] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   16.529906] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   16.530649] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   16.531394] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   16.532159] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   16.532930] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   16.533705] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   16.534455] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   16.534639] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.534650] pnp: PnP ACPI init
[   16.567715] pnp: PnP ACPI: found 10 devices
[   16.567780] PCI: Using ACPI for IRQ routing
[   16.567783] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.567875] NET: Registered protocol family 8
[   16.567878] NET: Registered protocol family 20
[   16.567891] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.567897] hpet0: 3 64-bit timers, 14318180 Hz
[   16.568916] PCI-GART: No AMD northbridge found.
[   16.571399] pnp: 00:01: ioport range 0x800-0x85f could not be reserved
[   16.571404] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[   16.571408] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[   16.571868] PCI: Bridge: 0000:01:00.0
[   16.571870]   IO window: disabled.
[   16.571874]   MEM window: disabled.
[   16.571878]   PREFETCH window: disabled.
[   16.571882] PCI: Bridge: 0000:01:00.2
[   16.571885]   IO window: d000-dfff
[   16.571890]   MEM window: dfe00000-dfefffff
[   16.571893]   PREFETCH window: disabled.
[   16.571897] PCI: Bridge: 0000:00:02.0
[   16.571900]   IO window: d000-dfff
[   16.571905]   MEM window: dfe00000-dfefffff
[   16.571908]   PREFETCH window: disabled.
[   16.571912] PCI: Bridge: 0000:00:03.0
[   16.571914]   IO window: disabled.
[   16.571918]   MEM window: dfd00000-dfdfffff
[   16.571922]   PREFETCH window: disabled.
[   16.571926] PCI: Bridge: 0000:00:04.0
[   16.571927]   IO window: disabled.
[   16.571932]   MEM window: dd000000-dfcfffff
[   16.571936]   PREFETCH window: c0000000-cfffffff
[   16.571941] PCI: Bridge: 0000:00:1e.0
[   16.571942]   IO window: disabled.
[   16.571947]   MEM window: dcf00000-dcffffff
[   16.571951]   PREFETCH window: disabled.
[   16.571968] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.571974] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   16.571990] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   16.572005] PCI: Setting latency timer of device 0000:01:00.2 to 64
[   16.572015] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.572020] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   16.572029] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.572034] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.572042] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.572094] NET: Registered protocol family 2
[   16.617517] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   16.617807] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   16.619932] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.620536] TCP: Hash tables configured (established 262144 bind 65536)
[   16.620539] TCP reno registered
[   16.633670] checking if image is initramfs... it is
[   17.222657] Freeing initrd memory: 6825k freed
[   17.227026] Simple Boot Flag at 0x7a set to 0x80
[   17.227651] audit: initializing netlink socket (disabled)
[   17.227666] audit(1218622793.596:1): initialized
[   17.227947] VFS: Disk quotas dquot_6.5.1
[   17.227971] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   17.228033] io scheduler noop registered
[   17.228036] io scheduler anticipatory registered
[   17.228038] io scheduler deadline registered
[   17.228060] io scheduler cfq registered (default)
[   17.245399] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   17.245430] Allocate Port Service[0000:00:02.0:pcie00]
[   17.245546] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   17.245576] Allocate Port Service[0000:00:03.0:pcie00]
[   17.245692] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.245722] Allocate Port Service[0000:00:04.0:pcie00]
[   17.280089] Real Time Clock Driver v1.12ac
[   17.280158] Linux agpgart interface v0.102 (c) Dave Jones
[   17.280162] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.280289] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.280438] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.281058] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.281269] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.281494] mice: PS/2 mouse device common for all mice
[   17.282352] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.282541] input: Macintosh mouse button emulation as /class/input/input0
[   17.282589] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.282594] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.282923] PNP: No PS/2 controller found. Probing ports directly.
[   17.285390] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.285397] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.285538] TCP cubic registered
[   17.285550] NET: Registered protocol family 1
[   17.285675] ACPI: (supports S0 S1 S3 S4 S5)
[   17.285723]   Magic number: 4:319:325
[   17.285736]   hash matches device ttyye
[   17.285841] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   17.285913] Freeing unused kernel memory: 304k freed
[   18.492626] Capability LSM initialized
[   18.534433] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   18.534443] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   18.534452] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   18.534461] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   19.060892] usbcore: registered new interface driver usbfs
[   19.060931] usbcore: registered new interface driver hub
[   19.060974] usbcore: registered new device driver usb
[   19.062458] USB Universal Host Controller Interface driver v3.0
[   19.062540] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.062558] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.062563] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.062709] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.062739] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   19.062932] usb usb1: configuration #1 chosen from 1 choice
[   19.062989] hub 1-0:1.0: USB hub found
[   19.063001] hub 1-0:1.0: 2 ports detected
[   19.075491] Floppy drive(s): fd0 is 1.44M
[   19.079395] ieee1394: Initialized config rom entry `ip1394'
[   19.082100] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[   19.082113] Copyright (c) 1999-2006 Intel Corporation.
[   19.096188] FDC 0 is a post-1991 82077
[   19.170324] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   19.170341] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.170346] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.170381] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.170411] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[   19.170547] usb usb2: configuration #1 chosen from 1 choice
[   19.170594] hub 2-0:1.0: USB hub found
[   19.170606] hub 2-0:1.0: 2 ports detected
[   19.274234] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.274246] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.274250] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.274280] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.274307] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[   19.274440] usb usb3: configuration #1 chosen from 1 choice
[   19.274481] hub 3-0:1.0: USB hub found
[   19.274493] hub 3-0:1.0: 2 ports detected
[   19.378160] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   19.378172] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   19.378177] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   19.378211] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   19.378235] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[   19.378363] usb usb4: configuration #1 chosen from 1 choice
[   19.378405] hub 4-0:1.0: USB hub found
[   19.378416] hub 4-0:1.0: 2 ports detected
[   19.482283] ACPI: PCI Interrupt 0000:06:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.514015] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   19.532525] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[dcffb800-dcffbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   19.532833] ACPI: PCI Interrupt 0000:00:1d.7[D] -> <6>ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 48 (level, low) -> IRQ 48
[   19.532846] GSI 23 (level, low) -> IRQ 23
[   19.532877] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   19.532883] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   19.532937] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   19.532985] ehci_hcd 0000:00:1d.7: debug port 1
[   19.532993] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   19.533008] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[   19.536903] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.537024] usb usb5: configuration #1 chosen from 1 choice
[   19.537064] hub 5-0:1.0: USB hub found
[   19.537073] hub 5-0:1.0: 8 ports detected
[   19.538230] SCSI subsystem initialized
[   19.544533] libata version 2.20 loaded.
[   19.804291] e1000: 0000:03:0e.0: e1000_probe: (PCI-X:100MHz:64-bit) 00:14:22:35:4f:11
[   19.846883] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   19.846933] ata_piix 0000:00:1f.1: version 2.10ac1
[   19.846964] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   19.847000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   19.847145] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001ffa0 irq 14
[   19.847442] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001ffa8 irq 15
[   19.847467] scsi0 : ata_piix
[   19.847557] ata1: port disabled. ignoring.
[   19.847585] scsi1 : ata_piix
[   20.170106] ata2.00: ATAPI, max UDMA/33
[   20.317748] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   20.338031] ata2.00: configured for UDMA/33
[   20.345111] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GWA4164B D108 PQ: 0 ANSI: 5
[   20.350516] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   20.350536] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   20.350553] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.350604] ata3: SATA max UDMA/133 cmd 0x000000000001fe00 ctl 0x000000000001fe12 bmdma 0x000000000001fea0 irq 18
[   20.350641] ata4: SATA max UDMA/133 cmd 0x000000000001fe20 ctl 0x000000000001fe32 bmdma 0x000000000001fea8 irq 18
[   20.350653] scsi2 : ata_piix
[   20.509684] usb 2-1: configuration #1 chosen from 1 choice
[   20.519024] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
[   20.519033] ata3.00: ATA-7: Maxtor 7L250S0, BACE1G10, max UDMA/133
[   20.519038] ata3.00: 488281250 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   20.531022] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
[   20.531028] ata3.00: configured for UDMA/133
[   20.531044] scsi3 : ata_piix
[   20.698991] ata4.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
[   20.698997] ata4.00: ATA-7: Maxtor 7L250S0, BACE1G10, max UDMA/133
[   20.699001] ata4.00: 488281250 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   20.710961] ata4.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
[   20.710966] ata4.00: configured for UDMA/133
[   20.711090] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 7L250S0   BACE PQ: 0 ANSI: 5
[   20.716575] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 7L250S0   BACE PQ: 0 ANSI: 5
[   20.739844] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   20.739848] Uniform CD-ROM driver Revision: 3.20
[   20.739907] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   20.740031] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[   20.740053] sda: Write Protect is off
[   20.740057] sda: Mode Sense: 00 3a 00 00
[   20.740087] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.740138] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[   20.740157] sda: Write Protect is off
[   20.740159] sda: Mode Sense: 00 3a 00 00
[   20.740200] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.740205]  sda:<5>sr 1:0:0:0: Attached scsi generic sg0 type 5
[   20.743759] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   20.743803] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   20.754027] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   20.772539]  sda1 sda2 <<7>ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[   20.811518]  sda5 >
[   20.811644] sd 2:0:0:0: Attached scsi disk sda
[   20.811717] SCSI device sdb: 488281250 512-byte hdwr sectors (250000 MB)
[   20.811734] sdb: Write Protect is off
[   20.811737] sdb: Mode Sense: 00 3a 00 00
[   20.811761] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.811814] SCSI device sdb: 488281250 512-byte hdwr sectors (250000 MB)
[   20.811836] sdb: Write Protect is off
[   20.811838] sdb: Mode Sense: 00 3a 00 00
[   20.811861] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.811864]  sdb:
[   20.839838] sd 3:0:0:0: Attached scsi disk sdb
[   20.928375] usb 4-2: configuration #1 chosen from 1 choice
[   20.931387] usbcore: registered new interface driver hiddev
[   20.964434] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A as /class/input/input1
[   20.964460] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A] on usb-0000:00:1d.1-1
[   20.979363] input: DELL DELL USB Keyboard as /class/input/input2
[   20.979376] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.3-2
[   20.979393] usbcore: registered new interface driver usbhid
[   20.979397] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   21.075848] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00d04b6c0d086034]
[   21.075954] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[803500144f112200]
[   21.090312] Attempting manual resume
[   21.090316] swsusp: Resume From Partition 8:5
[   21.090318] PM: Checking swsusp image.
[   21.090485] PM: Resume from disk failed.
[   21.094493] scsi4 : SBP-2 IEEE-1394
[   21.120900] kjournald starting.  Commit interval 5 seconds
[   21.120912] EXT3-fs: mounted filesystem with ordered data mode.
[   22.103547] ieee1394: sbp2: Logged into SBP-2 device
[   22.103795] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   22.105857] scsi 4:0:0:0: Direct-Access-RBC ST350083 0A               3.AA PQ: 0 ANSI: 4
[   22.120731] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[   22.121268] sdc: Write Protect is off
[   22.121271] sdc: Mode Sense: 11 00 00 00
[   22.122572] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.123471] SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
[   22.124029] sdc: Write Protect is off
[   22.124032] sdc: Mode Sense: 11 00 00 00
[   22.125332] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.125339]  sdc:<6>e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   30.405812] EDAC MC: Ver: 2.0.1 Jul  9 2008
[   30.413292] EDAC e752x: tolm = 80000, remapbase = ffc000, remaplimit = 0
[   30.413364] EDAC MC0: Giving out device to e752x_edac E7525: DEV 0000:00:00.0
[   30.431864] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.613580] iTCO_vendor_support: vendor-support=0
[   30.620450] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.717604] parport: PnPBIOS parport detected.
[   30.717660] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   30.807017] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   30.807155] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   30.807169] iTCO_wdt: No card detected
[   30.824137] input: PC Speaker as /class/input/input3
[   31.607425] nvidia: module license 'NVIDIA' taints kernel.
[   31.862056] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.862076] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   31.862226] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9639  Mon Apr 16 20:18:26 PDT 2007
[   31.880926] intel_rng: FWH not detected
[   32.198736] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   32.198776] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   32.518827] intel8x0_measure_ac97_clock: measured 58353 usecs
[   32.518830] intel8x0: clocking to 48000
[   52.109352] ieee1394: sbp2: aborting sbp2 command
[   52.109358] sd 4:0:0:0: 
[   52.109360]         command: Read(10): 28 00 00 00 00 00 00 00 08 00
[   53.607106] ieee1394: unsolicited response packet received - no tlabel match
[   53.885511] ieee1394: sbp2: Reconnected to SBP-2 device
[   53.885745] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   53.885759] ieee1394: sbp2: reset requested
[   53.885761] ieee1394: sbp2: generating sbp2 fetch agent reset
[   63.879613] ieee1394: sbp2: aborting sbp2 command
[   63.879617] sd 4:0:0:0: 
[   63.879618]         command: Test Unit Ready: 00 00 00 00 00 00
[   63.879628] ieee1394: sbp2: hpsb_node_write failed.
[   63.879629] 
[   63.879635] sd 4:0:0:0: scsi: Device offlined - not ready after error recovery
[   63.879643] sd 4:0:0:0: SCSI error: return code = 0x00050000
[   63.879646] end_request: I/O error, dev sdc, sector 0
[   63.879650] Buffer I/O error on device sdc, logical block 0
[   63.879685] sd 4:0:0:0: rejecting I/O to offline device
[   63.879689] Buffer I/O error on device sdc, logical block 0
[   63.879705] sd 4:0:0:0: rejecting I/O to offline device
[   63.879708] Buffer I/O error on device sdc, logical block 0
[   63.879723] sd 4:0:0:0: rejecting I/O to offline device
[   63.879726] Buffer I/O error on device sdc, logical block 0
[   63.879736] sd 4:0:0:0: rejecting I/O to offline device
[   63.879739] Buffer I/O error on device sdc, logical block 0
[   63.879743] ldm_validate_partition_table(): Disk read failed.
[   63.879750] sd 4:0:0:0: rejecting I/O to offline device
[   63.879753] Buffer I/O error on device sdc, logical block 0
[   63.879762] sd 4:0:0:0: rejecting I/O to offline device
[   63.879765] Buffer I/O error on device sdc, logical block 0
[   63.879774] sd 4:0:0:0: rejecting I/O to offline device
[   63.879777] Buffer I/O error on device sdc, logical block 0
[   63.879786] sd 4:0:0:0: rejecting I/O to offline device
[   63.879789] Buffer I/O error on device sdc, logical block 0
[   63.879793] Dev sdc: unable to read RDB block 0
[   63.879800] sd 4:0:0:0: rejecting I/O to offline device
[   63.879803] Buffer I/O error on device sdc, logical block 0
[   63.879812] sd 4:0:0:0: rejecting I/O to offline device
[   63.879828] sd 4:0:0:0: rejecting I/O to offline device
[   63.879836] sd 4:0:0:0: rejecting I/O to offline device
[   63.879846] sd 4:0:0:0: rejecting I/O to offline device
[   63.879850]  unknown partition table
[   63.879973] sd 4:0:0:0: Attached scsi disk sdc
[   63.880100] sd 4:0:0:0: Attached scsi generic sg3 type 14
[   64.157598] ieee1394: sbp2: Error reconnecting to SBP-2 device - failed
[   64.158401] ieee1394: sbp2: Logged out of SBP-2 device
[   64.163356] ieee1394: sbp2: Logged into SBP-2 device
[   64.163607] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   64.179196] fuse init (API version 7.8)
[   64.253787] lp0: using parport0 (interrupt-driven).
[   64.337200] Adding 6032368k swap on /dev/disk/by-uuid/57b41765-06a7-4c43-9ee3-f8645870e24b.  Priority:-1 extents:1 across:6032368k
[   64.507547] EXT3 FS on sda1, internal journal
[   66.305465] NET: Registered protocol family 17
[   71.512767] input: Power Button (FF) as /class/input/input4
[   71.512805] ACPI: Power Button (FF) [PWRF]
[   71.512847] input: Power Button (CM) as /class/input/input5
[   71.512873] ACPI: Power Button (CM) [VBTN]
[   71.626201] No dock devices found.
[   71.669296] Using specific hotkey driver
[   71.798911] ibm_acpi: ec object not found
[   71.899004] pcc_acpi: loading...
[   78.188403] ppdev: user-space parallel port driver
[   80.857756] NET: Registered protocol family 10
[   80.857895] lo: Disabled Privacy Extensions
[   81.401996] Bluetooth: Core ver 2.11
[   81.402090] NET: Registered protocol family 31
[   81.402094] Bluetooth: HCI device and connection manager initialized
[   81.402097] Bluetooth: HCI socket layer initialized
[   81.500643] Bluetooth: L2CAP ver 2.8
[   81.500652] Bluetooth: L2CAP socket layer initialized
[   81.530023] Bluetooth: RFCOMM socket layer initialized
[   81.530046] Bluetooth: RFCOMM TTY layer initialized
[   81.530049] Bluetooth: RFCOMM ver 1.8
[   91.801234] eth0: no IPv6 routers present
[  648.113623] EDAC e752x: Non-Fatal Error PCI Express B
[  648.113630] EDAC e752x: Non-Fatal Error PCI Express B
[ 1612.662267] EDAC e752x: Non-Fatal Error PCI Express B
[ 1612.662275] EDAC e752x: Non-Fatal Error PCI Express B
[ 1831.555752] EDAC e752x: Non-Fatal Error PCI Express B
[ 1831.555759] EDAC e752x: Non-Fatal Error PCI Express B

I have tried to fsck the drive as this seems to be throwing back an error, after entering the following command. 

sudo fsck /dev/sda1


fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: clean, 5047573/29769728 files, 56175202/59526841 blocks


more /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bde061d6-398f-4047-82b9-d44097a37e6d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=57b41765-06a7-4c43-9ee3-f8645870e24b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Any ideas?? I have no way of mounting something and I cannot seem to fix the problem illustrated by /dev/sda1 on / type ext3 (rw,errors=remount-ro), which may the cause.

Thanks

---

### Post by mcduck on 2008-08-13
/dev/sda1 is your root partition. Not the external drive. So running fsck won't help you, and you cshouldn't check a mounted partition anyway. (like fsck said to you, "WARNING!!! Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.")

Assuming you only have one internal hard disk, the /dev/sdb show in the fdisk output would be the external drive.. But it seems that fdisk can't find any partitions in that drive, so perhaps your reboots have corrupted it's partition table..

edit: What makes you think there would be any problem with sda1? The "rw,errors=remount-ro" are just configurations how that partition should be mounted (as fstab is a _configuration_ file, teeling what to mount anfd where, not a log file of any sort). "rw" tells to mount the drive as readable & writabe, and "errors=remount-ro" tells that should the drive have any errors it should be remounted as read-only. I see nothing in yor logs that would suggest that there is any errors with that drive. Actually the only errors I see in your log are related to /dev/sdc. even the /dev/sdb that is empty and unpartitioned, based on fdisk output, doesn't seme to produce  nahy error messages.

---

### Post by az on 2008-08-13
To list any drives that HAL detects, run

sudo lshw -C disk -short


To list partitions, run

cat /proc/partitions

---

