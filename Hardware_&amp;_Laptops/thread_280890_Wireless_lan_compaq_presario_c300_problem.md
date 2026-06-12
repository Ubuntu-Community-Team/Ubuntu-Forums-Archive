---
title: "Wireless lan compaq presario c300 problem"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by Dennisb1 on 2006-10-20
Hello,

I have a compaq presario c300 laptop with Broadcom 802.11bg wlan pci card but when im trying in ubuntu dapper drake to use it it is not possible
When im looking in device manager i see a unknown hardware and i have a screenshot here:
[[img=http://img216.imageshack.us/img216/2286/schermafdruk1rx5.th.png]](http://img216.imageshack.us/my.php?image=schermafdruk1rx5.png)
Can someone help me?
I have a internet connection on it because im now wired... :mad: 

Thank you,
Dennis


UPDATE: i just installed nsisomething like that :P with the gui wireless network drivers where you can use windows drivers.
When im choosing my drivers it saying hardware present: YES
So its detecting it but im not getting any wireless connection in the network settings only a dial up connection and a lan connection :(

I just plugged in my old usb wireless adapter and use the same wireless network drivers for windows and that one works but can only be use on wep networks and i have a wkip secure router :( but i want my pci card in my laptop working
When ubuntu starts im getting PCI:Cannot allocate ... something like that and im sure that my wlan card is in that list

---

### Post by kazetsukai on 2006-10-22
I've bought the same laptop with the same "unknown" broadcom WiFi adapter.

I've gone the ndiswrapper route, and have gotten this far:

-NDIS reports driver,hardware present
-Dmesg shows ndiswrapper return with complaints about the code being 64 bit and not 32 bit. 

Apparently, where you sand I are getting the driver from, (HP?) NDIS is assuming to use the 64 bit version of the driver even though we're running 32 Bit OSes and then hitting an error when loading the kernel module.

So far, I've been unable to modify the driver inf file to get the 32 bit driver loaded, as I don't use Windows and haven't had much experience with it.

That being said, I haven't given up yet, and if I get it working, I'll update and post the necessary files here.

Please post the results of the "dmesg" command here.

---

### Post by paulbakker on 2006-10-27
I bought this laptop yesterday and I have the same problems, so I am very interested in what you guys find out.

I'll attach the output of dmesg.

---

### Post by paulbakker on 2006-10-27
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003f680000 (usable)
[17179569.184000]  BIOS-e820: 000000003f680000 - 000000003f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 118MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f65c0
[17179569.184000] On node 0 totalpages: 259712
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 30336 pages, LIFO batch:7
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6590
[17179569.184000] ACPI: RSDT (v001 PTLTD  Capell00 0x06040000  LTP 0x00000000) @ 0x3f68d0f6
[17179569.184000] ACPI: FADT (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x3f693dfc
[17179569.184000] ACPI: MADT (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x3f693e70
[17179569.184000] ACPI: HPET (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x3f693ed8
[17179569.184000] ACPI: MCFG (v001 HP     NISSAN   0x06040000 LOHR 0x0000005a) @ 0x3f693f10
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3f693fd8
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x3f693f7e
[17179569.184000] ACPI: SSDT (v001 SataRe SataAhci 0x00001000 INTL 0x20060217) @ 0x3f68d810
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20060217) @ 0x3f68d634
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20060217) @ 0x3f68d13e
[17179569.184000] ACPI: DSDT (v001 HP     NISSAN   0x06040000 INTL 0x20060217) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: 2 duplicate APIC table ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 1019028k/1038848k available (1976k kernel code, 19084k reserved, 606k data, 288k init, 121344k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1596.038 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3195.79 BogoMIPS (lpj=6391590)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 1024K
[17179569.268000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 0000c109 00000000 00000000
[17179569.268000] mtrr: v2.0 (20020519)
[17179569.268000] CPU: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz stepping 08
[17179569.268000] Enabling fast FPU save and restore... done.
[17179569.268000] Enabling unmasked SIMD FPU exception support... done.
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] checking if image is initramfs... it is
[17179569.964000] Freeing initrd memory: 6841k freed
[17179569.972000] ACPI: Looking for DSDT ... not found!
[17179570.008000] ENABLING IO-APIC IRQs
[17179570.008000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.156000] NET: Registered protocol family 16
[17179570.156000] EISA bus registered
[17179570.156000] ACPI: bus type pci registered
[17179570.156000] PCI: PCI BIOS revision 2.10 entry at 0xfd873, last bus=8
[17179570.156000] PCI: Using MMCONFIG
[17179570.156000] ACPI: Subsystem revision 20051216
[17179570.156000] ACPI: Interpreter enabled
[17179570.156000] ACPI: Using IOAPIC for interrupt routing
[17179570.156000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.156000] PCI: Probing PCI hardware (bus 00)
[17179570.180000] Boot video device is 0000:00:02.0
[17179570.180000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.180000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.180000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.184000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.184000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179570.184000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[17179570.184000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.184000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.184000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[17179570.184000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[17179570.184000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179570.184000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179570.188000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179570.188000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[17179570.188000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[17179570.188000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[17179570.228000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.228000] pnp: PnP ACPI init
[17179570.252000] pnp: PnP ACPI: found 10 devices
[17179570.252000] PnPBIOS: Disabled by ACPI PNP
[17179570.252000] PCI: Using ACPI for IRQ routing
[17179570.252000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.252000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.252000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.252000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.252000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.252000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.252000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.252000] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[17179570.272000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.272000] PCI: Bridge: 0000:00:1c.0
[17179570.272000]   IO window: disabled.
[17179570.272000]   MEM window: disabled.
[17179570.272000]   PREFETCH window: disabled.
[17179570.272000] PCI: Bridge: 0000:00:1c.1
[17179570.272000]   IO window: disabled.
[17179570.272000]   MEM window: disabled.
[17179570.272000]   PREFETCH window: disabled.
[17179570.272000] PCI: Bridge: 0000:00:1c.2
[17179570.272000]   IO window: disabled.
[17179570.272000]   MEM window: 50000000-500fffff
[17179570.272000]   PREFETCH window: disabled.
[17179570.272000] PCI: Bridge: 0000:00:1e.0
[17179570.272000]   IO window: 2000-2fff
[17179570.272000]   MEM window: d0100000-d01fffff
[17179570.272000]   PREFETCH window: disabled.
[17179570.272000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.272000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.272000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.272000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.272000] PCI: Enabling device 0000:00:1c.2 (0100 -> 0102)
[17179570.272000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.272000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.272000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.272000] Simple Boot Flag at 0x36 set to 0x1
[17179570.272000] audit: initializing netlink socket (disabled)
[17179570.272000] audit(1161928732.272:1): initialized
[17179570.272000] highmem bounce pool size: 64 pages
[17179570.272000] VFS: Disk quotas dquot_6.5.1
[17179570.272000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.272000] Initializing Cryptographic API
[17179570.272000] io scheduler noop registered
[17179570.272000] io scheduler anticipatory registered
[17179570.272000] io scheduler deadline registered
[17179570.272000] io scheduler cfq registered
[17179578.272000] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[17179578.272000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179578.272000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179578.272000] assign_interrupt_mode Found MSI capability
[17179578.272000] Allocate Port Service[pcie00]
[17179578.272000] Allocate Port Service[pcie02]
[17179578.272000] Allocate Port Service[pcie03]
[17179578.272000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179578.272000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179578.272000] assign_interrupt_mode Found MSI capability
[17179578.272000] Allocate Port Service[pcie00]
[17179578.272000] Allocate Port Service[pcie02]
[17179578.272000] Allocate Port Service[pcie03]
[17179578.272000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179578.272000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179578.272000] assign_interrupt_mode Found MSI capability
[17179578.272000] Allocate Port Service[pcie00]
[17179578.272000] Allocate Port Service[pcie02]
[17179578.272000] Allocate Port Service[pcie03]
[17179578.272000] isapnp: Scanning for PnP cards...
[17179578.628000] isapnp: No Plug & Play device found
[17179578.640000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179578.656000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179578.672000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179578.672000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179578.676000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179578.676000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179578.680000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179578.680000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179578.684000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179578.684000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179578.684000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179578.684000] mice: PS/2 mouse device common for all mice
[17179578.684000] EISA: Probing bus 0 at eisa.0
[17179578.684000] Cannot allocate resource for EISA slot 1
[17179578.684000] Cannot allocate resource for EISA slot 2
[17179578.684000] EISA: Detected 0 cards.
[17179578.684000] NET: Registered protocol family 2
[17179578.728000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179578.728000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179578.728000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179578.728000] TCP: Hash tables configured (established 131072 bind 65536)
[17179578.728000] TCP reno registered
[17179578.728000] TCP bic registered
[17179578.728000] NET: Registered protocol family 1
[17179578.728000] NET: Registered protocol family 8
[17179578.728000] NET: Registered protocol family 20
[17179578.728000] Using IPI Shortcut mode
[17179578.728000] ACPI wakeup devices:
[17179578.728000] LANC PS2K PS2M
[17179578.728000] ACPI: (supports S0 S3 S4 S5)
[17179578.728000] Freeing unused kernel memory: 288k freed
[17179578.748000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179578.772000] vga16fb: initializing
[17179578.772000] vga16fb: mapped to 0xc00a0000
[17179578.900000] Console: switching to colour frame buffer device 80x25
[17179578.900000] fb0: VGA16 VGA frame buffer device
[17179579.920000] Capability LSM initialized
[17179580.028000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179580.028000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179580.040000] ACPI: Thermal Zone [TZ01] (28 C)
[17179580.048000] ACPI: Thermal Zone [TZ02] (0 C)
[17179580.464000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179580.464000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179580.464000] ICH7: chipset revision 1
[17179580.464000] ICH7: not 100% native mode: will probe irqs later
[17179580.464000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179580.464000] Probing IDE interface ide0...
[17179581.200000] hda: PHILIPS DVDRAM SDVD8821H, ATAPI CD/DVD-ROM drive
[17179581.872000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179581.884000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[17179581.884000] Uniform CD-ROM driver Revision: 3.20
[17179581.924000] SCSI subsystem initialized
[17179581.924000] ACPI: bus type scsi registered
[17179581.924000] libata version 1.20 loaded.
[17179581.928000] ahci 0000:00:1f.2: version 1.2
[17179581.928000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
[17179587.748000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179587.748000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[17179587.748000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part
[17179587.748000] ata1: SATA max UDMA/133 cmd 0xF888C500 ctl 0x0 bmdma 0x0 irq 233
[17179587.748000] ata2: SATA max UDMA/133 cmd 0xF888C580 ctl 0x0 bmdma 0x0 irq 233
[17179587.748000] ata3: SATA max UDMA/133 cmd 0xF888C600 ctl 0x0 bmdma 0x0 irq 233
[17179587.748000] ata4: SATA max UDMA/133 cmd 0xF888C680 ctl 0x0 bmdma 0x0 irq 233
[17179587.952000] ata1: dev 0 cfg 00:0c5a 49:2f00 82:306b 83:7c09 84:6003 85:3069 86:3c09 87:6003 88:203f 93:0000
[17179587.952000] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[17179587.952000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe3800
[17179587.996000] ata1: dev 0 configured for UDMA/100
[17179587.996000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe3800
[17179587.996000] scsi0 : ahci
[17179588.200000] ata2: no device found (phy stat 00000000)
[17179588.200000] scsi1 : ahci
[17179588.404000] ata3: no device found (phy stat 00000000)
[17179588.404000] scsi2 : ahci
[17179588.608000] ata4: no device found (phy stat 00000000)
[17179588.608000] scsi3 : ahci
[17179588.608000]   Vendor: ATA       Model: ST98823AS         Rev: 7.24
[17179588.608000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179588.612000] Driver 'sd' needs updating - please use bus_type methods
[17179588.612000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179588.612000] SCSI device sda: drive cache: write back
[17179588.616000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179588.616000] SCSI device sda: drive cache: write back
[17179588.616000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[17179588.656000] sd 0:0:0:0: Attached scsi disk sda
[17179588.972000] usbcore: registered new driver usbfs
[17179588.972000] usbcore: registered new driver hub
[17179588.972000] USB Universal Host Controller Interface driver v2.3
[17179588.972000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 50
[17179588.972000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179588.972000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179588.972000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179588.972000] uhci_hcd 0000:00:1d.0: irq 50, io base 0x00001820
[17179588.976000] hub 1-0:1.0: USB hub found
[17179588.976000] hub 1-0:1.0: 2 ports detected
[17179589.080000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179589.080000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179589.080000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179589.080000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179589.080000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x00001840
[17179589.080000] hub 2-0:1.0: USB hub found
[17179589.080000] hub 2-0:1.0: 2 ports detected
[17179589.184000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179589.184000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179589.184000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179589.184000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179589.184000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001860
[17179589.184000] hub 3-0:1.0: USB hub found
[17179589.184000] hub 3-0:1.0: 2 ports detected
[17179589.288000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179589.288000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179589.288000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179589.288000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179589.288000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00001880
[17179589.288000] hub 4-0:1.0: USB hub found
[17179589.288000] hub 4-0:1.0: 2 ports detected
[17179589.392000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 50
[17179589.392000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179589.392000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179589.392000] ehci_hcd 0000:00:1d.7: debug port 1
[17179589.392000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179589.392000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179589.392000] ehci_hcd 0000:00:1d.7: irq 50, io mem 0xd0544000
[17179589.396000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179589.396000] hub 5-0:1.0: USB hub found
[17179589.396000] hub 5-0:1.0: 8 ports detected
[17179589.424000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179589.520000] Probing IDE interface ide1...
[17179589.928000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17179590.108000] usbcore: registered new driver hiddev
[17179590.124000] input: Logitech USB Mouse as /class/input/input1
[17179590.124000] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.1-2
[17179590.124000] usbcore: registered new driver usbhid
[17179590.124000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179590.136000] Attempting manual resume
[17179590.148000] kjournald starting.  Commit interval 5 seconds
[17179590.148000] EXT3-fs: mounted filesystem with ordered data mode.
[17179600.148000] ts: Compaq touchscreen protocol output
[17179600.232000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179601.652000] Linux agpgart interface v0.101 (c) Dave Jones
[17179601.656000] agpgart: Detected an Intel 945GM Chipset.
[17179601.656000] agpgart: Detected 7932K stolen memory.
[17179601.672000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179602.068000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 58
[17179602.068000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179602.188000] hw_random hardware driver 1.0.0 loaded
[17179602.224000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179602.824000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179603.072000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[17179603.140000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179603.224000] Real Time Clock Driver v1.12
[17179604.688000] 8139too Fast Ethernet driver 0.9.27
[17179604.692000] PCI: Enabling device 0000:08:08.0 (0105 -> 0107)
[17179604.692000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179604.692000] eth0: RealTek RTL8139 at 0xf899c000, 00:16:d4:48:38:24, IRQ 177
[17179604.692000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179605.136000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179605.264000] eth0: link down
[17179606.320000] NET: Registered protocol family 17
[17179608.556000] lp: driver loaded but no devices found
[17179608.604000] Adding 1373516k swap on /dev/sda5.  Priority:-1 extents:1 across:1373516k
[17179608.716000] EXT3 FS on sda3, internal journal
[17179608.860000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179608.860000] md: bitmap version 4.39
[17179609.300000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179609.932000] cdrom: open failed.
[17179616.156000] ACPI: AC Adapter [ACAD] (on-line)
[17179616.228000] ACPI: Battery Slot [BAT1] (battery present)
[17179616.288000] ACPI: Power Button (FF) [PWRF]
[17179616.288000] ACPI: Lid Switch [LID]
[17179616.288000] ACPI: Power Button (CM) [PWRB]
[17179616.400000] ibm_acpi: ec object not found
[17179616.432000] pcc_acpi: loading...
[17179616.520000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179616.520000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[17179621.048000] [drm] Initialized drm 1.0.1 20051102
[17179621.048000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179621.052000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179623.044000] ppdev: user-space parallel port driver
[17179623.332000] apm: BIOS not found.
[17179626.724000] Bluetooth: Core ver 2.8
[17179626.724000] NET: Registered protocol family 31
[17179626.724000] Bluetooth: HCI device and connection manager initialized
[17179626.724000] Bluetooth: HCI socket layer initialized
[17179626.744000] Bluetooth: L2CAP ver 2.8
[17179626.744000] Bluetooth: L2CAP socket layer initialized
[17179626.820000] Bluetooth: RFCOMM socket layer initialized
[17179626.820000] Bluetooth: RFCOMM TTY layer initialized
[17179626.820000] Bluetooth: RFCOMM ver 1.7
[17179698.944000] NET: Registered protocol family 10
[17179698.944000] lo: Disabled Privacy Extensions
[17179698.944000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179698.944000] IPv6 over IPv4 tunneling driver
[17179846.980000] eth0: link down
[17179846.980000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179900.072000] eth0: link down
[17179900.076000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180039.252000] cdrom: This disc doesn't have any tracks I recognize!
[17180039.276000] cdrom: This disc doesn't have any tracks I recognize!
[17180039.296000] cdrom: This disc doesn't have any tracks I recognize!
[17180039.344000] cdrom: This disc doesn't have any tracks I recognize!
[17180039.796000] scsi: unknown opcode 0x01
[17180366.292000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180366.340000] ISO 9660 Extensions: RRIP_1991A

---

### Post by Dennisb1 on 2006-11-03
Any news yet? 
When i upgraded ubuntu to the new version 6.10 i now can see the wireless routers on some program on ubuntu but i still cant connect to it
A: Ubuntu crashes
B: Connection crashes
C: Nuthing happens
:???:

---

### Post by Dennisb1 on 2006-11-04
The things i can copy because the oldest text of the script is already out of my screen:confused: 
```
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 1024K
[17179569.268000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000140 0000c109 00000000 00000000
[17179569.268000] CPU: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz stepping 08
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] Freeing SMP alternatives: 0k freed
[17179569.284000] checking if image is initramfs... it is
[17179569.960000] Freeing initrd memory: 6628k freed
[17179569.960000] ACPI: Core revision 20060707
[17179569.960000] ACPI: Looking for DSDT ... not found!
[17179569.984000] ENABLING IO-APIC IRQs
[17179569.984000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.136000] NET: Registered protocol family 16
[17179570.136000] EISA bus registered
[17179570.136000] ACPI: bus type pci registered
[17179570.136000] PCI: Using MMCONFIG
[17179570.136000] Setting up standard PCI resources
[17179570.136000] ACPI: Interpreter enabled
[17179570.136000] ACPI: Using IOAPIC for interrupt routing
[17179570.140000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.140000] PCI: Probing PCI hardware (bus 00)
[17179570.160000] Boot video device is 0000:00:02.0
[17179570.160000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.160000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.160000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179570.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[17179570.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.164000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.164000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[17179570.164000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[17179570.164000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179570.164000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179570.164000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179570.168000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[17179570.168000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[17179570.168000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[17179570.208000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.208000] pnp: PnP ACPI init
[17179570.232000] pnp: PnP ACPI: found 10 devices
[17179570.232000] PnPBIOS: Disabled by ACPI PNP
[17179570.232000] PCI: Using ACPI for IRQ routing
[17179570.232000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.232000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.232000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.232000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.232000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.232000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.232000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.232000] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[17179570.232000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.232000] PCI: Bridge: 0000:00:1c.0
[17179570.232000]   IO window: disabled.
[17179570.232000]   MEM window: disabled.
[17179570.232000]   PREFETCH window: disabled.
[17179570.232000] PCI: Bridge: 0000:00:1c.1
[17179570.232000]   IO window: disabled.
[17179570.232000]   MEM window: disabled.
[17179570.232000]   PREFETCH window: disabled.
[17179570.232000] PCI: Bridge: 0000:00:1c.2
[17179570.232000]   IO window: disabled.
[17179570.232000]   MEM window: 50000000-500fffff
[17179570.232000]   PREFETCH window: disabled.
[17179570.232000] PCI: Bridge: 0000:00:1e.0
[17179570.232000]   IO window: 2000-2fff
[17179570.232000]   MEM window: d0100000-d01fffff
[17179570.232000]   PREFETCH window: disabled.
[17179570.232000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.232000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.232000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.232000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.232000] PCI: Enabling device 0000:00:1c.2 (0100 -> 0102)
[17179570.232000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.232000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.232000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.232000] NET: Registered protocol family 2
[17179570.268000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.268000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.268000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.268000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.268000] TCP reno registered
[17179570.268000] Simple Boot Flag at 0x36 set to 0x1
[17179570.268000] audit: initializing netlink socket (disabled)
[17179570.268000] audit(1162634393.268:1): initialized
[17179570.268000] highmem bounce pool size: 64 pages
[17179570.268000] VFS: Disk quotas dquot_6.5.1
[17179570.268000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.268000] Initializing Cryptographic API
[17179570.268000] io scheduler noop registered
[17179570.268000] io scheduler anticipatory registered
[17179570.268000] io scheduler deadline registered
[17179570.268000] io scheduler cfq registered (default)
[17179578.268000] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[17179578.268000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179578.268000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179578.268000] assign_interrupt_mode Found MSI capability
[17179578.268000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179578.268000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179578.268000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179578.268000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179578.268000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179578.268000] assign_interrupt_mode Found MSI capability
[17179578.268000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179578.268000] Allocate Port Service[0000:00:1c.1:pcie02]
[17179578.268000] Allocate Port Service[0000:00:1c.1:pcie03]
[17179578.268000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179578.268000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179578.268000] assign_interrupt_mode Found MSI capability
[17179578.268000] Allocate Port Service[0000:00:1c.2:pcie00]
[17179578.268000] Allocate Port Service[0000:00:1c.2:pcie02]
[17179578.268000] Allocate Port Service[0000:00:1c.2:pcie03]
[17179578.268000] isapnp: Scanning for PnP cards...
[17179578.624000] isapnp: No Plug & Play device found
[17179578.644000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179578.644000] mice: PS/2 mouse device common for all mice
[17179578.644000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179578.644000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179578.644000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179578.644000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179578.660000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179578.676000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179578.676000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179578.680000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179578.684000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179578.684000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179578.688000] EISA: Probing bus 0 at eisa.0
[17179578.692000] Cannot allocate resource for EISA slot 1
[17179578.692000] Cannot allocate resource for EISA slot 2
[17179578.692000] EISA: Detected 0 cards.
[17179578.692000] TCP bic registered
[17179578.692000] NET: Registered protocol family 1
[17179578.692000] NET: Registered protocol family 8
[17179578.692000] NET: Registered protocol family 20
[17179578.692000] Using IPI Shortcut mode
[17179578.692000] ACPI: (supports S0 S3 S4 S5)
[17179578.692000] Freeing unused kernel memory: 288k freed
[17179578.760000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179579.804000] Capability LSM initialized
[17179579.836000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179579.836000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179579.836000] ACPI: Getting cpuindex for acpiid 0x1
[17179579.844000] ACPI: Thermal Zone [TZ01] (55 C)
[17179579.844000] ACPI: Thermal Zone [TZ02] (27 C)
[17179580.172000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179580.172000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179580.172000] ICH7: chipset revision 1
[17179580.172000] ICH7: not 100% native mode: will probe irqs later
[17179580.172000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179580.172000] Probing IDE interface ide0...
[17179580.912000] hda: PHILIPS DVDRAM SDVD8821H, ATAPI CD/DVD-ROM drive
[17179581.584000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179581.596000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[17179581.596000] Uniform CD-ROM driver Revision: 3.20
[17179581.656000] SCSI subsystem initialized
[17179581.656000] libata version 1.20 loaded.
[17179581.660000] ahci 0000:00:1f.2: version 1.2
[17179581.660000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
[17179587.480000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179587.480000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[17179587.480000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[17179587.480000] ata1: SATA max UDMA/133 cmd 0xF8842500 ctl 0x0 bmdma 0x0 irq 233
[17179587.480000] ata2: SATA max UDMA/133 cmd 0xF8842580 ctl 0x0 bmdma 0x0 irq 233
[17179587.480000] ata3: SATA max UDMA/133 cmd 0xF8842600 ctl 0x0 bmdma 0x0 irq 233
[17179587.480000] ata4: SATA max UDMA/133 cmd 0xF8842680 ctl 0x0 bmdma 0x0 irq 233
[17179587.856000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179587.856000] ata1: dev 0 cfg 49:2f00 82:7069 83:7c09 84:6023 85:7069 86:3c09 87:6023 88:203f
[17179587.856000] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[17179587.856000] ata1: dev 0 configured for UDMA/100
[17179587.856000] scsi0 : ahci
[17179588.224000] ata2: SATA link down (SStatus 0)
[17179588.224000] scsi1 : ahci
[17179589.144000] ata3: SATA link down (SStatus 0)
[17179589.144000] scsi2 : ahci
[17179589.512000] ata4: SATA link down (SStatus 0)
[17179589.512000] scsi3 : ahci
[17179589.512000]   Vendor: ATA       Model: WDC WD800BEVS-60  Rev: 01.0
[17179589.512000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179589.516000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179589.516000] sda: Write Protect is off
[17179589.516000] sda: Mode Sense: 00 3a 00 00
[17179589.516000] SCSI device sda: drive cache: write back
[17179589.516000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179589.516000] sda: Write Protect is off
[17179589.516000] sda: Mode Sense: 00 3a 00 00
[17179589.516000] SCSI device sda: drive cache: write back
[17179589.516000]  sda: sda1 sda2 sda3
[17179589.876000] sd 0:0:0:0: Attached scsi disk sda
[17179590.124000] Probing IDE interface ide1...
[17179590.164000] usbcore: registered new driver usbfs
[17179590.168000] usbcore: registered new driver hub
[17179590.168000] USB Universal Host Controller Interface driver v3.0
[17179590.168000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 50
[17179590.168000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179590.168000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179590.168000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179590.168000] uhci_hcd 0000:00:1d.0: irq 50, io base 0x00001820
[17179590.168000] usb usb1: configuration #1 chosen from 1 choice
[17179590.172000] hub 1-0:1.0: USB hub found
[17179590.172000] hub 1-0:1.0: 2 ports detected
[17179590.276000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179590.276000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179590.276000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179590.276000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179590.276000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x00001840
[17179590.276000] usb usb2: configuration #1 chosen from 1 choice
[17179590.276000] hub 2-0:1.0: USB hub found
[17179590.276000] hub 2-0:1.0: 2 ports detected
[17179590.380000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179590.380000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179590.380000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179590.380000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179590.380000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001860
[17179590.380000] usb usb3: configuration #1 chosen from 1 choice
[17179590.380000] hub 3-0:1.0: USB hub found
[17179590.380000] hub 3-0:1.0: 2 ports detected
[17179590.484000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179590.484000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179590.484000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179590.484000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179590.484000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00001880
[17179590.484000] usb usb4: configuration #1 chosen from 1 choice
[17179590.484000] hub 4-0:1.0: USB hub found
[17179590.484000] hub 4-0:1.0: 2 ports detected
[17179590.588000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 50
[17179590.588000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179590.588000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179590.588000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179590.588000] ehci_hcd 0000:00:1d.7: debug port 1
[17179590.588000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179590.588000] ehci_hcd 0000:00:1d.7: irq 50, io mem 0xd0544000
[17179590.592000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179590.592000] usb usb5: configuration #1 chosen from 1 choice
[17179590.592000] hub 5-0:1.0: USB hub found
[17179590.592000] hub 5-0:1.0: 8 ports detected
[17179590.620000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179590.936000] usb 5-1: new high speed USB device using ehci_hcd and address 2
[17179591.068000] usb 5-1: configuration #1 chosen from 1 choice
[17179591.252000] usbcore: registered new driver libusual
[17179591.256000] Initializing USB Mass Storage driver...
[17179591.380000] scsi4 : SCSI emulation for USB Mass Storage devices
[17179591.380000] usb-storage: device found at 2
[17179591.380000] usb-storage: waiting for device to settle before scanning
[17179591.380000] usbcore: registered new driver usb-storage
[17179591.380000] USB Mass Storage support registered.
[17179591.628000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17179591.800000] usb 2-2: configuration #1 chosen from 1 choice
[17179591.812000] usbcore: registered new driver hiddev
[17179591.832000] input: Logitech USB Receiver as /class/input/input1
[17179591.832000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[17179591.832000] usbcore: registered new driver usbhid
[17179591.832000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179596.380000] usb-storage: device scan complete
[17179596.380000]   Vendor: HTE72106  Model: 0G9AT00           Rev: 0000
[17179596.380000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179596.384000] SCSI device sdb: 117210240 512-byte hdwr sectors (60012 MB)
[17179596.384000] sdb: Write Protect is off
[17179596.384000] sdb: Mode Sense: 27 00 00 00
[17179596.384000] sdb: assuming drive cache: write through
[17179596.384000] SCSI device sdb: 117210240 512-byte hdwr sectors (60012 MB)
[17179596.384000] sdb: Write Protect is off
[17179596.384000] sdb: Mode Sense: 27 00 00 00
[17179596.384000] sdb: assuming drive cache: write through
[17179596.384000]  sdb: sdb1 sdb2 sdb3 < sdb5 >
[17179596.412000] sd 4:0:0:0: Attached scsi disk sdb
[17179596.636000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179596.636000] EXT3-fs: write access will be enabled during recovery.
[17179597.684000] kjournald starting.  Commit interval 5 seconds
[17179597.684000] EXT3-fs: recovery complete.
[17179597.684000] EXT3-fs: mounted filesystem with ordered data mode.
[17179607.412000] Linux agpgart interface v0.101 (c) Dave Jones
[17179607.416000] agpgart: Detected an Intel 945GM Chipset.
[17179607.416000] agpgart: Detected 7932K stolen memory.
[17179607.432000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179608.020000] hw_random hardware driver 1.0.0 loaded
[17179608.188000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179608.216000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179608.272000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 58
[17179608.272000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179608.388000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[17179608.460000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179608.476000] Real Time Clock Driver v1.12ac
[17179608.824000] 8139too Fast Ethernet driver 0.9.27
[17179608.856000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179608.856000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[17179609.024000] PCI: Enabling device 0000:08:08.0 (0105 -> 0107)
[17179609.024000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179609.024000] eth0: RealTek RTL8139 at 0xf8982000, 00:16:d4:43:74:31, IRQ 177
[17179609.024000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179609.024000] ts: Compaq touchscreen protocol output
[17179609.200000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179609.200000] ieee80211_crypt: registered algorithm 'NULL'
[17179609.204000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179609.204000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179609.236000] bcm43xx driver
[17179609.236000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179609.236000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17179609.924000] eth0: link down
[17179610.980000] NET: Registered protocol family 17
[17179613.972000] lp: driver loaded but no devices found
[17179614.036000] Adding 1220900k swap on /dev/disk/by-uuid/249c3076-b587-4dc5-9d29-82a103417096.  Priority:-1 extents:1 across:1220900k
[17179614.104000] EXT3 FS on sdb1, internal journal
[17179614.232000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179614.232000] md: bitmap version 4.39
[17179614.400000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179617.188000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179617.248000] NTFS volume version 3.1.
[17179617.320000] NTFS volume version 3.1.
[17179617.456000] NTFS volume version 3.1.
[17179619.868000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179619.884000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179619.884000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179619.932000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179619.932000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179619.932000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179619.960000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179619.960000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179619.960000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179619.996000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179620.000000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179620.000000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179620.020000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179620.024000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179620.024000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179620.048000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179620.052000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179620.052000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179621.872000] ACPI: AC Adapter [ACAD] (off-line)
[17179621.964000] ACPI: Battery Slot [BAT1] (battery present)
[17179621.980000] ACPI: Power Button (FF) [PWRF]
[17179621.980000] ACPI Error (evxfevnt-0189): Could not enable SleepButton event [20060707]
[17179621.980000] ACPI Warning (evxface-0146): Could not enable fixed event 3 [20060707]
[17179621.980000] ACPI: Lid Switch [LID]
[17179621.980000] ACPI: Power Button (CM) [PWRB]
[17179622.116000] ibm_acpi: ec object not found
[17179622.144000] pcc_acpi: loading...
[17179622.248000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179622.248000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[17179622.492000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179623.316000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179624.336000] [drm] Initialized drm 1.0.1 20051102
[17179624.340000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179624.340000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179625.448000] apm: BIOS not found.
[17179627.220000] NET: Registered protocol family 10
[17179627.220000] lo: Disabled Privacy Extensions
[17179627.220000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179627.220000] IPv6 over IPv4 tunneling driver
[17179630.736000] Bluetooth: Core ver 2.8
[17179630.736000] NET: Registered protocol family 31
[17179630.736000] Bluetooth: HCI device and connection manager initialized
[17179630.736000] Bluetooth: HCI socket layer initialized
[17179630.768000] Bluetooth: L2CAP ver 2.8
[17179630.768000] Bluetooth: L2CAP socket layer initialized
[17179630.780000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179630.796000] Bluetooth: RFCOMM socket layer initialized
[17179630.796000] Bluetooth: RFCOMM TTY layer initialized
[17179630.796000] Bluetooth: RFCOMM ver 1.7
[17179645.864000] eth0: no IPv6 routers present
[17179671.644000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179671.648000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179671.648000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179671.656000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17179671.676000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17179671.684000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17179671.704000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17179671.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179671.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179671.708000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179671.712000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179671.712000] psmouse.c: issuing reconnect request
[17179692.128000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17179692.132000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179692.152000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17179692.152000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179692.156000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179692.156000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179692.160000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179692.160000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179692.160000] psmouse.c: issuing reconnect request
[17179712.608000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17179712.616000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17179712.616000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179712.620000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179712.620000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179712.620000] psmouse.c: issuing reconnect request
[17179733.236000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17179733.248000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17179733.268000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179733.268000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179733.272000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179733.272000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179733.288000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[17179733.288000] psmouse.c: issuing reconnect request
```

---

### Post by FrankVdb on 2006-11-04
I followed this howto for installing a Windows driver using ndiswrapper on my Acer TravelMate 800 laptop:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

My wireless connection is now faster than under W2K, I just couldn't believe it at first...

---

### Post by Dennisb1 on 2006-11-05
Yes i have tryed this but then on my own way but looks on that page actualy but it ses hardware pressent YES
But when im trying to connect to the network my pc hangs and i need to do a hard reboot...
On start of ubuntu i see some Cannot allocate PCI: 000000 numbers
My wlan device is under this to becaue i know what number it is
How can i fix this?

---

### Post by Dennisb1 on 2006-11-05
[17179570.252000] PCI: Cannot allocate resource region 0 of device 0000:06:00.0 this is it

---

### Post by joopiestropie on 2006-11-15
Hi, I have the same laptop but I'm using Ubuntu edgy. It's working at home and I used this howto. [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

It says that it also works with dapper I didn't test it but I wish you good luck :)
Just follow all the steps and it worked here!

---

### Post by Dennisb1 on 2007-10-01
Finaly after a year or so i got it working with 7.04 :D:D:D:D
Only its 11mbit and not 54mbits...
AND the connection is lost allot of times and connects allot of times to a unsecured network somewhere nextdoor... and i dont want that :(

---

### Post by Ayuthia on 2007-10-01
> **Dennisb1 said:**
> Finaly after a year or so i got it working with 7.04 :D:D:D:D
Only its 11mbit and not 54mbits...
AND the connection is lost allot of times and connects allot of times to a unsecured network somewhere nextdoor... and i dont want that :(
From your message, it looks like you are using the native bcm43xx driver with bcm43xx-fwcutter.  Gutsy has a newer kernel that will provide the 54Mb speed.  I had similar results with my connection and have been using ndiswrapper.  From your prior posts, it looked like you used ndiswrapper once before and had bad results.  Do you recall which driver you used?  You might try sp33008.exe from the HP site.  That seems to bring good results for the HP (most likely Compaq too) laptops.

---

### Post by Dennisb1 on 2007-10-01
Hmmmmm 
Yeah well u used fwcutter again downloaded somewhere on google the .o file and now got this.
I removed the fwcutter after i where done because then yum upgrade works again somehow it wants to download a .o file somewhere on google when i use yum for fwcutter on googlepages.com but that dont exist anymore
Do you have a direct link to that file?

Thanks!

---

### Post by Ayuthia on 2007-10-01
> **Dennisb1 said:**
> Hmmmmm 
Yeah well u used fwcutter again downloaded somewhere on google the .o file and now got this.
I removed the fwcutter after i where done because then yum upgrade works again somehow it wants to download a .o file somewhere on google when i use yum for fwcutter on googlepages.com but that dont exist anymore
Do you have a direct link to that file?

Thanks!
The file is located in /usr/share/bcm43xx-fwcutter.  It is called install_bcm43xx_firmware.sh.  The link should now be:
```
$DL http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
```

You should be able to get the driver by going to that link also.

---

### Post by Dennisb1 on 2007-10-01
Ok i downloaded the file but now what?
sorry im not a big linux user at the moment but i want to switch!

Thanks!!!!!

---

### Post by Ayuthia on 2007-10-01
> **Dennisb1 said:**
> Ok i downloaded the file but now what?
sorry im not a big linux user at the moment but i want to switch!

Thanks!!!!!

Sorry, I think I am confused.  I was thinking that you already had your wireless running at 11Mb.  Is that correct?  If so, that means that the bcm43xx-fwcutter program has already done its job and installed the firmware for you.  You do not need to do this again.  If that is not the case, the easiest route would be to run:
```
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```
It will download the file again, but it will run the bcm43xx-fwcutter process for you and place the firmware in the correct directory.

If you do not want to go that route, you could also try ndiswrapper.

---

### Post by Dennisb1 on 2007-10-01
Well my wlan is working yes!

I only have removed bcm43xx-fwcutter afterwards because my system cant install anything anymore or download upgrades because the fwcutter program wants to download something from a site that dont exist anymore but i will try this im now rebooting to linux to try! 

Thanks!

---

### Post by Dennisb1 on 2007-10-01
Here is the output from the install of bcm43xx-fwcutter:

```
dennis@dennis-linux:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  libnet1 ettercap-common
Gebruik 'apt-get autoremove' om deze te verwijderen.
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  bcm43xx-fwcutter
0 pakketten opgewaardeerd, 1 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
Er moeten 0B/25,6kB aan archieven opgehaald worden.
Na het uitpakken zal er 119kB extra schijfruimte gebruikt worden.
Voorconfigureren van pakketten...
Selecteren van voorheen niet geselecteerd pakket bcm43xx-fwcutter.
(Database inlezen ... 111025 bestanden en mappen geïnstalleerd.)
Uitpakken van bcm43xx-fwcutter (uit .../bcm43xx-fwcutter_1%3a006-1_i386.deb) ...
Instellen van bcm43xx-fwcutter (006-1) ...
--21:23:32--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Herleiden van boredklink.googlepages.com... 72.14.203.118
Verbinding maken met boredklink.googlepages.com|72.14.203.118|:80... verbonden.
HTTP-verzoek is verzonden; wachten op antwoord... 404 Not Found
21:23:32 Fout 404: Not Found.

dpkg: fout bij afhandelen van bcm43xx-fwcutter (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
dennis@dennis-linux:~$ 

```

Yeah sorry its not english hehe

---

### Post by Ayuthia on 2007-10-01
If you update the installer script to show the site that I posted earlier, you should be able to run your updates and it should process without any problems.  The other option is to remove bcm43xx-fwcutter.  That should also take care of your problem.  If I recall, it does not do anything but remove the program.  The files it created in /lib/firmware will remain.

---

### Post by Dennisb1 on 2007-10-01
Ok its done after allot of changes in the file.
When will it be used for my wlan? or is this it just a reboot and done?

---

### Post by Ayuthia on 2007-10-01
> **Dennisb1 said:**
> Ok its done after allot of changes in the file.
When will it be used for my wlan? or is this it just a reboot and done?
It should be just a reboot and done.  You should still get 11Mb.  The only way to get 54Mb in Feisty is to use ndiswrapper.

---

### Post by Dennisb1 on 2007-10-02
... why have i done this then???
It already worked.....

---

### Post by Ayuthia on 2007-10-02
My apologies.  I must have misunderstood you.  I thought that you were trying to get rid of the error message so that you could continue to install packages.  If you are looking for connections higher than 11 Mb, you will have to wait for Gutsy or install ndiswrapper.  If you are having connection problems with your current version, ndiswrapper might solve your problem.

---

