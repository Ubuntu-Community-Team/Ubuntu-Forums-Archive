---
title: "After upgrading to dapper having intermittent boot issues"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by cracker on 2006-07-19
I have Ubuntu installed on a stripped Dell Inspiron 6000 notebook. Everything functions correctly, and when it boots, its great. However, every time I reboot, it hangs during boot. This error shows on tty1 among the kernel loading messages:

```
[17179573.516000] PCI: Failed to allocate I/O resource #7:1000@10000 for 0000:00:1e.0
```

I always have to reboot twice, because it hangs in one of two places during boot--either 

```
 * Loading manual drives...
```

 or 

```
 * Starting Hardware Abstraction Layer hald...
```

I did not have this problem with Breezy. I upgraded to Dapper via Update Manager, and I've had rebooting issues since then. It always works on the second try. Is there anything I can do other than start over?

Here is lspci:

```
ryan@delli6000:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:03:01.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
0000:04:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```


And here is dmesg:

```
ryan@delli6000:~$ dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000f7d3800 (usable)
[17179569.184000]  BIOS-e820: 000000000f7d3800 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 247MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 63443
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 59347 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc9b0
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d50217 ASL  0x00000061) @ 0x0f7d4425
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d50217 ASL  0x00000061) @ 0x0f7d4c00
[17179569.184000] ACPI: MADT (v001 DELL    CPi R   0x27d50217 ASL  0x00000047) @ 0x0f7d5400
[17179569.184000] ACPI: MCFG (v016 DELL    CPi R   0x27d50217 ASL  0x00000061) @ 0x0f7d53c0
[17179569.184000] ACPI: BOOT (v001 DELL    CPi R   0x27d50217 ASL  0x00000061) @ 0x0f7d4fc0
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x0f7d465c
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x0f7d4461
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:d0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 1296.938 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.276000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.276000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.280000] Memory: 241076k/253772k available (1976k kernel code, 12096k reserved, 606k data, 288k init, 0k highmem)
[17179572.280000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.360000] Calibrating delay using timer specific routine.. 2597.58 BogoMIPS (lpj=5195162)
[17179572.360000] Security Framework v1.0.0 initialized
[17179572.360000] SELinux:  Disabled at boot.
[17179572.360000] Mount-cache hash table entries: 512
[17179572.360000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179572.360000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179572.360000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.360000] CPU: L2 cache: 1024K
[17179572.360000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[17179572.360000] mtrr: v2.0 (20020519)
[17179572.360000] CPU: Intel(R) Celeron(R) M processor         1.30GHz stepping 08
[17179572.360000] Enabling fast FPU save and restore... done.
[17179572.360000] Enabling unmasked SIMD FPU exception support... done.
[17179572.360000] Checking 'hlt' instruction... OK.
[17179572.376000] checking if image is initramfs... it is
[17179573.176000] Freeing initrd memory: 6617k freed
[17179573.192000] ACPI: Looking for DSDT ... not found!
[17179573.196000] ENABLING IO-APIC IRQs
[17179573.196000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.340000] NET: Registered protocol family 16
[17179573.340000] EISA bus registered
[17179573.340000] ACPI: bus type pci registered
[17179573.356000] PCI: PCI BIOS revision 2.10 entry at 0xfbaae, last bus=4
[17179573.356000] PCI: Using MMCONFIG
[17179573.356000] ACPI: Subsystem revision 20051216
[17179573.376000] ACPI: Interpreter enabled
[17179573.376000] ACPI: Using IOAPIC for interrupt routing
[17179573.376000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.376000] PCI: Probing PCI hardware (bus 00)
[17179573.376000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.396000] Boot video device is 0000:00:02.0
[17179573.396000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179573.396000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[17179573.396000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179573.396000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.396000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.420000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179573.420000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[17179573.420000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[17179573.420000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[17179573.424000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.424000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.424000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.424000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179573.424000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.424000] pnp: PnP ACPI init
[17179573.448000] pnp: PnP ACPI: found 11 devices
[17179573.448000] PnPBIOS: Disabled by ACPI PNP
[17179573.448000] PCI: Using ACPI for IRQ routing
[17179573.448000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.488000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[17179573.488000] pnp: 00:01: ioport range 0x1000-0x1005 could not be reserved
[17179573.488000] pnp: 00:01: ioport range 0x1008-0x100f could not be reserved
[17179573.488000] pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
[17179573.488000] pnp: 00:02: ioport range 0x1006-0x1007 has been reserved
[17179573.488000] pnp: 00:02: ioport range 0x100a-0x1059 could not be reserved
[17179573.488000] pnp: 00:02: ioport range 0x1060-0x107f has been reserved
[17179573.488000] pnp: 00:02: ioport range 0x1080-0x10bf has been reserved
[17179573.488000] pnp: 00:02: ioport range 0x10c0-0x10df has been reserved
[17179573.488000] pnp: 00:07: ioport range 0x900-0x90f has been reserved
[17179573.488000] pnp: 00:07: ioport range 0x910-0x91f has been reserved
[17179573.488000] pnp: 00:07: ioport range 0x920-0x92f has been reserved
[17179573.488000] pnp: 00:07: ioport range 0x930-0x93f has been reserved
[17179573.488000] pnp: 00:07: ioport range 0x940-0x97f has been reserved
[17179573.488000] pnp: 00:0a: ioport range 0x7b0-0x7bb has been reserved
[17179573.488000] pnp: 00:0a: ioport range 0x7c0-0x7df has been reserved
[17179573.488000] pnp: 00:0a: ioport range 0xbb0-0xbbb has been reserved
[17179573.488000] pnp: 00:0a: ioport range 0xbc0-0xbdf has been reserved
[17179573.488000] pnp: 00:0a: ioport range 0xfb0-0xfbb has been reserved
[17179573.488000] pnp: 00:0a: ioport range 0xfc0-0xfdf has been reserved
[17179573.488000] pnp: 00:0a: ioport range 0x13b0-0x13bb has been reserved
[17179573.488000] pnp: 00:0a: ioport range 0x13c0-0x13df has been reserved
[17179573.488000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179573.488000] PCI: Failed to allocate I/O resource #7:1000@10000 for 0000:00:1e.0
[17179573.488000] PCI: Bus 4, cardbus bridge: 0000:03:01.0
[17179573.488000]   IO window: 00001400-000014ff
[17179573.488000]   IO window: 00001800-000018ff
[17179573.488000]   PREFETCH window: 20000000-21ffffff
[17179573.488000]   MEM window: 22000000-23ffffff
[17179573.488000] PCI: Bridge: 0000:00:1e.0
[17179573.488000]   IO window: disabled.
[17179573.488000]   MEM window: dfd00000-dfdfffff
[17179573.488000]   PREFETCH window: 20000000-21ffffff
[17179573.488000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.488000] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
[17179573.488000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179573.488000] Simple Boot Flag at 0x79 set to 0x1
[17179573.488000] audit: initializing netlink socket (disabled)
[17179573.488000] audit(1153346425.488:1): initialized
[17179573.488000] VFS: Disk quotas dquot_6.5.1
[17179573.488000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.488000] Initializing Cryptographic API
[17179573.488000] io scheduler noop registered
[17179573.488000] io scheduler anticipatory registered
[17179573.488000] io scheduler deadline registered
[17179573.488000] io scheduler cfq registered
[17179573.488000] isapnp: Scanning for PnP cards...
[17179573.844000] isapnp: No Plug & Play device found
[17179573.860000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.864000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.864000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.864000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.868000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 177
[17179573.868000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179573.868000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.868000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.868000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.868000] mice: PS/2 mouse device common for all mice
[17179573.868000] EISA: Probing bus 0 at eisa.0
[17179573.868000] Cannot allocate resource for EISA slot 1
[17179573.868000] EISA: Detected 0 cards.
[17179573.868000] NET: Registered protocol family 2
[17179573.876000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.908000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)[17179573.908000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.908000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.908000] TCP: Hash tables configured (established 8192 bind 8192)
[17179573.908000] TCP reno registered
[17179573.908000] TCP bic registered
[17179573.908000] NET: Registered protocol family 1
[17179573.908000] NET: Registered protocol family 8
[17179573.908000] NET: Registered protocol family 20
[17179573.908000] Using IPI Shortcut mode
[17179573.908000] ACPI wakeup devices:
[17179573.908000]  LID PBTN PCI0 USB0 USB1 USB2 USB4 USB3 MODM PCIE
[17179573.908000] ACPI: (supports S0 S3 S4 S5)
[17179573.908000] Freeing unused kernel memory: 288k freed
[17179573.960000] vga16fb: initializing
[17179573.960000] vga16fb: mapped to 0xc00a0000
[17179574.092000] Console: switching to colour frame buffer device 80x25
[17179574.092000] fb0: VGA16 VGA frame buffer device
[17179575.164000] Capability LSM initialized
[17179575.288000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.288000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.292000] ACPI: Thermal Zone [THM] (43 C)
[17179575.728000] SCSI subsystem initialized
[17179575.728000] ACPI: bus type scsi registered
[17179575.728000] libata version 1.20 loaded.
[17179575.732000] ahci 0000:00:1f.2: version 1.2
[17179575.732000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 177
[17179575.732000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[17179575.732000] ahci: probe of 0000:00:1f.2 failed with error -12
[17179575.732000] ata_piix 0000:00:1f.2: version 1.05
[17179575.732000] ata_pci_init_one: pci_dev class+intf: 0x10180
[17179575.732000] ata_pci_init_one: NO_LEGACY == 0
[17179575.732000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 177
[17179575.732000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179575.732000] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xBFA0 irq 14
[17179575.896000] ata1: dev 0 cfg 00:0040 49:2f00 82:7c6b 83:5b08 84:4003 85:7c69 86:1a08 87:4003 88:203f 93:604b
[17179575.896000] ata1: dev 0 ATA-6, max UDMA/100, 78140160 sectors: LBA
[17179575.896000] ata1(0): applying bridge limits
[17179575.896000] ata_acpi_push_id: skipping for PATA mode
[17179575.896000] ata1: dev 0 configured for UDMA/100
[17179575.896000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179575.896000] pata_get_dev_handle: dev_handle: 0xcf7bc2e0, parent_handle: 0xcf141b20
[17179575.896000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xce1a7800, *handle=0xcf7bc2e0
[17179575.896000] do_drive_get_GTF:   drive w/ adr=0: v: 0x00000000
[17179575.896000] scsi0 : ata_piix
[17179575.896000]   Vendor: ATA       Model: TOSHIBA MK4026GA  Rev: PA10
[17179575.896000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179575.896000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179575.896000] pata_get_dev_handle: dev_handle: 0xcf7bc2e0, parent_handle: 0xcf141b20
[17179575.896000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xce1a7800, *handle=0xcf7bc2e0
[17179575.896000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
[17179576.216000] ata2: dev 0 cfg 00:85c0 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407 93:0000
[17179576.216000] ata2: dev 0 ATAPI, max UDMA/33
[17179576.216000] ata_acpi_push_id: skipping for PATA mode
[17179576.216000] ata2: dev 0 configured for UDMA/33
[17179576.216000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.216000] pata_get_dev_handle: dev_handle: 0xcf7bc2e0, parent_handle: 0xcf141b20
[17179576.216000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xce1a7800, *handle=0xcf7bc2e0
[17179576.216000] do_drive_get_GTF:   drive w/ adr=0: v: 0x00000000
[17179576.216000] scsi1 : ata_piix
[17179576.220000]   Vendor: HL-DT-ST  Model: DVD-ROM GDR8082N  Rev: 0106
[17179576.220000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179576.220000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179576.220000] pata_get_dev_handle: dev_handle: 0xcf7bc2e0, parent_handle: 0xcf141b20
[17179576.220000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xce1a7800, *handle=0xcf7bc2e0
[17179576.232000] Driver 'sd' needs updating - please use bus_type methods
[17179576.248000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17179576.248000] SCSI device sda: drive cache: write back
[17179576.252000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17179576.252000] SCSI device sda: drive cache: write back
[17179576.252000]  sda: sda1 sda2
[17179576.340000] sd 0:0:0:0: Attached scsi disk sda
[17179576.484000] usbcore: registered new driver usbfs
[17179576.484000] usbcore: registered new driver hub
[17179576.488000] USB Universal Host Controller Interface driver v2.3
[17179576.488000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179576.488000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.488000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.488000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.488000] uhci_hcd 0000:00:1d.0: irq 193, io base 0x0000bf80
[17179576.488000] hub 1-0:1.0: USB hub found
[17179576.488000] hub 1-0:1.0: 2 ports detected
[17179576.572000] ieee1394: Initialized config rom entry `ip1394'
[17179576.592000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179576.592000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179576.592000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179576.592000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179576.592000] uhci_hcd 0000:00:1d.1: irq 177, io base 0x0000bf60
[17179576.592000] hub 2-0:1.0: USB hub found
[17179576.592000] hub 2-0:1.0: 2 ports detected
[17179576.696000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 201
[17179576.696000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.696000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.696000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.696000] uhci_hcd 0000:00:1d.2: irq 201, io base 0x0000bf40
[17179576.696000] hub 3-0:1.0: USB hub found
[17179576.696000] hub 3-0:1.0: 2 ports detected
[17179576.800000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 169
[17179576.800000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179576.800000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179576.800000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179576.800000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000bf20
[17179576.800000] hub 4-0:1.0: USB hub found
[17179576.800000] hub 4-0:1.0: 2 ports detected
[17179576.904000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 193
[17179576.904000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179576.904000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179576.904000] ehci_hcd 0000:00:1d.7: debug port 1
[17179576.904000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179576.904000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179576.904000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xffa80800
[17179576.908000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.908000] hub 5-0:1.0: USB hub found
[17179576.908000] hub 5-0:1.0: 8 ports detected
[17179577.012000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179577.012000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 201
[17179577.064000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[201]  MMIO=[dfdfd800-dfdfdfff]  Max Packet=[2048]
[17179577.104000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179577.104000] ide0: ports already in use, skipping probe
[17179577.104000] ide1: I/O resource 0x170-0x177 not free.
[17179577.104000] ide1: ports already in use, skipping probe
[17179577.120000] Attempting manual resume
[17179577.180000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.196000] kjournald starting.  Commit interval 5 seconds
[17179578.344000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[4a4fc000017248e1]
[17179589.916000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179589.916000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179589.992000] sr0: scsi3-mmc drive: 10x/24x cd/rw xa/form2 cdda tray
[17179589.992000] Uniform CD-ROM driver Revision: 3.20
[17179589.992000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179591.180000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.212000] Real Time Clock Driver v1.12
[17179591.252000] input: PC Speaker as /class/input/input1
[17179591.276000] agpgart: Detected an Intel 915GM Chipset.
[17179591.276000] agpgart: Detected 7932K stolen memory.
[17179591.296000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179591.464000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 193
[17179591.464000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179591.640000] hw_random: cannot enable RNG, aborting
[17179591.704000] input: PS/2 Mouse as /class/input/input2
[17179591.724000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179592.260000] ts: Compaq touchscreen protocol output
[17179592.284000] intel8x0_measure_ac97_clock: measured 4291745656 usecs
[17179592.284000] intel8x0: measured clock 0 rejected
[17179592.284000] intel8x0: clocking to 48000
[17179592.288000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179592.288000] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0188]
[17179592.288000] b44.c:v0.97 (Nov 30, 2005)
[17179592.288000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 201
[17179592.292000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:11:43:77:52:a1
[17179592.416000] Yenta: ISA IRQ mask 0x04b8, PCI irq 169
[17179592.416000] Socket status: 30000820
[17179592.416000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[17179592.416000] pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[17179592.416000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
[17179592.784000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179592.784000] sdhci: Copyright(c) Pierre Ossman
[17179592.784000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 177
[17179592.848000] sdhci: ============== REGISTER DUMP ==============
[17179592.848000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
[17179592.848000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179592.848000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179592.848000] sdhci: Present:  0x01f20000 | Host ctl: 0x00000000
[17179592.848000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179592.848000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[17179592.848000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179592.848000] sdhci: Int enab: 0xe1ff00cf | Sig enab: 0xe1ff00cf
[17179592.848000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179592.848000] sdhci: Caps:     0x01e021a1 | Max curr: 0x00000040
[17179592.848000] sdhci: ===========================================
[17179592.896000] mmc0: SDHCI at 0xdfdfd700 irq 177 DMA
[17179593.276000] pccard: CardBus card inserted into slot 0
[17179593.336000] cs: IO port probe 0x100-0x4ff: excluding 0x370-0x377 0x3f0-0x3f7
[17179593.340000] cs: IO port probe 0xc00-0xcf7: clean.
[17179593.340000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.680000] lp: driver loaded but no devices found
[17179593.756000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179593.756000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179593.756000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179593.800000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179593.904000] ndiswrapper: driver lstinds () loaded
[17179593.904000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
[17179593.904000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179593.904000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[17179594.596000] ndiswrapper (IoCreateUnprotectedSymbolicLink:744): --UNIMPLEMENTED--
[17179594.596000] ndiswrapper: using irq 169
[17179594.728000] NET: Registered protocol family 17
[17179595.636000] wlan0: vendor: 'TNET1130'
[17179595.636000] wlan0: ndiswrapper ethernet device 00:12:17:20:4b:a5 using driver lstinds, 104C:9066:1737:0033.5.conf
[17179595.636000] wlan0: encryption modes supported: WEP; TKIP with WPA
[17179595.744000] eth1394: $Rev: 1312 $ Ben Collins <bcollins@debian.org>
[17179595.744000] eth1394: eth1: IEEE-1394 IPv4 over 1394 Ethernet (fw-host0)
[17179595.816000] Adding 498004k swap on /dev/sda2.  Priority:-1 extents:1 across:498004k
[17179595.976000] EXT3 FS on sda1, internal journal
[17179596.232000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179596.232000] md: bitmap version 4.39
[17179596.824000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179597.524000] cdrom: open failed.
[17179598.244000] NET: Registered protocol family 10
[17179598.244000] lo: Disabled Privacy Extensions
[17179598.244000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179598.244000] IPv6 over IPv4 tunneling driver
[17179600.528000] ACPI: AC Adapter [AC] (on-line)
[17179600.808000] ACPI: Battery Slot [BAT0] (battery present)
[17179600.900000] ACPI: Lid Switch [LID]
[17179600.900000] ACPI: Power Button (CM) [PBTN]
[17179600.900000] ACPI: Sleep Button (CM) [SBTN]
[17179601.004000] ibm_acpi: ec object not found
[17179601.036000] pcc_acpi: loading...
[17179601.140000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179601.140000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179601.140000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)[17179607.344000] ppdev: user-space parallel port driver
[17179608.872000] [drm] Initialized drm 1.0.1 20051102
[17179608.908000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179608.908000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179609.020000] wlan0: no IPv6 routers present
[17179611.416000] apm: BIOS not found.
[17179612.616000] Bluetooth: Core ver 2.8
[17179612.616000] NET: Registered protocol family 31
[17179612.616000] Bluetooth: HCI device and connection manager initialized
[17179612.616000] Bluetooth: HCI socket layer initialized
[17179612.660000] Bluetooth: L2CAP ver 2.8
[17179612.660000] Bluetooth: L2CAP socket layer initialized
[17179612.772000] Bluetooth: RFCOMM socket layer initialized
[17179612.772000] Bluetooth: RFCOMM TTY layer initialized
[17179612.772000] Bluetooth: RFCOMM ver 1.7

```

---

