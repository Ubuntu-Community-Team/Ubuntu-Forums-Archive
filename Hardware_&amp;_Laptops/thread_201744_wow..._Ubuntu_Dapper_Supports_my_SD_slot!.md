---
title: "wow... Ubuntu Dapper Supports my SD slot!"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by Antman on 2006-06-22
On a whim, I inserted my SD card into my laptop (HP/Compaq nc6220) and guess what, it mounted it and put a cute (yes, I said cute) SD icon on my desktop. :mrgreen: 

Very surprised since I thought only kernel 2.6.17+ supported it. I guess they tweaked the kernel.
[IMG]http://www.learnezway.com/Screenshot.png[/IMG]

---

### Post by mradecic on 2006-06-22
well thats not fair...my dell 700m doesnt support :neutral:

---

### Post by mic74 on 2006-06-23
Publish, please, the Yours kernel config

---

### Post by tribaal on 2006-06-23
Same here, my SD card drive worked out of the box like a breeze, although I was expecting it not to.

Nice :)

- trib'

---

### Post by Kanhorta on 2006-06-23
Card reader not working in my Toshiba M50-137 :(

---

### Post by mkaragia on 2006-06-23
Doesn't work on my Aspire 5651WLMi](*,) ](*,)

---

### Post by n00blar on 2006-06-23
Yeah, no workie on the DELL Inspiron 700m :(

---

### Post by Antman on 2006-06-25
[QUOTE=mic74]Publish, please, the Yours kernel config[/QUOTE]

Is this what you are looking for?
```
thomas@nc6220:~$ dmesg
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003f7d0000 (usable)
[17179569.184000]  BIOS-e820: 000000003f7d0000 - 000000003f7efc00 (reserved)
[17179569.184000]  BIOS-e820: 000000003f7efc00 - 000000003f7fb000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003f7fb000 - 000000003f800000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 119MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 260048
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 30672 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000fe270
[17179569.184000] ACPI: RSDT (v001 HP     0944     0x24100520 HP   0x00000001) @ 0x3f7efc84
[17179569.184000] ACPI: FADT (v002 HP     0944     0x00000002 HP   0x00000001) @ 0x3f7efc00
[17179569.184000] ACPI: MADT (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x3f7efcb8
[17179569.184000] ACPI: MCFG (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x3f7efd14
[17179569.184000] ACPI: SSDT (v001 HP       HPQPpc 0x00001001 MSFT 0x0100000e) @ 0x3f7f7fca
[17179569.184000] ACPI: DSDT (v001 HP       nc6200 0x00010000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfec01000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3f800000:a0800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fec01000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 798.179 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.224000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.224000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.272000] Memory: 1020500k/1040192k available (1976k kernel code, 18868k reserved, 606k data, 288k init, 122688k highmem)
[17179571.272000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.352000] Calibrating delay using timer specific routine.. 1598.74 BogoMIPS (lpj=3197496)
[17179571.352000] Security Framework v1.0.0 initialized
[17179571.352000] SELinux:  Disabled at boot.
[17179571.352000] Mount-cache hash table entries: 512
[17179571.352000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[17179571.352000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[17179571.352000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179571.352000] CPU: L2 cache: 2048K
[17179571.352000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000180 00000000 00000000
[17179571.352000] mtrr: v2.0 (20020519)
[17179571.352000] CPU: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[17179571.352000] Enabling fast FPU save and restore... done.
[17179571.352000] Enabling unmasked SIMD FPU exception support... done.
[17179571.352000] Checking 'hlt' instruction... OK.
[17179571.368000] checking if image is initramfs... it is
[17179572.656000] Freeing initrd memory: 6614k freed
[17179572.664000] ACPI: Looking for DSDT ... not found!
[17179572.732000] ENABLING IO-APIC IRQs
[17179572.736000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.876000] HP Laptop series board detected. Selecting BIOS-method for reboots.
[17179572.876000] NET: Registered protocol family 16
[17179572.876000] EISA bus registered
[17179572.876000] ACPI: bus type pci registered
[17179572.876000] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=32
[17179572.876000] PCI: Using MMCONFIG
[17179572.876000] ACPI: Subsystem revision 20051216
[17179572.908000] ACPI: Interpreter enabled
[17179572.908000] ACPI: Using IOAPIC for interrupt routing
[17179572.908000] ACPI: PCI Root Bridge [C002] (0000:00)
[17179572.908000] PCI: Probing PCI hardware (bus 00)
[17179572.908000] ACPI: Assume root bridge [\_SB_.C002] bus is 0
[17179572.924000] Boot video device is 0000:00:02.0
[17179572.924000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179572.924000] PCI quirk: region 1100-113f claimed by ICH6 GPIO
[17179572.924000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.928000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.928000] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[17179573.000000] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C06D._PRT]
[17179573.004000] ACPI: Power Resource [C1CB] (on)
[17179573.004000] ACPI: Embedded Controller [C004] (gpe 16) interrupt mode.
[17179573.012000] ACPI: Power Resource [C1A5] (on)
[17179573.016000] ACPI: Power Resource [C1AD] (on)
[17179573.016000] ACPI: Power Resource [C1B4] (on)
[17179573.020000] ACPI: Power Resource [C1C4] (on)
[17179573.024000] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C006._PRT]
[17179573.024000] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C0DE._PRT]
[17179573.028000] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[17179573.028000] ACPI: PCI Interrupt Link [C0DB] (IRQs 10 *11)
[17179573.028000] ACPI: PCI Interrupt Link [C0DC] (IRQs 10 *11)
[17179573.032000] ACPI: PCI Interrupt Link [C0DD] (IRQs *10 11)
[17179573.032000] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[17179573.032000] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 *11)
[17179573.032000] ACPI: PCI Interrupt Link [C0F2] (IRQs *10 11)
[17179573.040000] ACPI: Power Resource [C267] (off)
[17179573.040000] ACPI: Power Resource [C268] (off)
[17179573.040000] ACPI: Power Resource [C269] (off)
[17179573.040000] ACPI: Power Resource [C26A] (off)
[17179573.040000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.040000] pnp: PnP ACPI init
[17179573.056000] pnp: PnP ACPI: found 16 devices
[17179573.056000] PnPBIOS: Disabled by ACPI PNP
[17179573.056000] PCI: Using ACPI for IRQ routing
[17179573.056000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.056000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179573.056000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179573.056000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179573.168000] pnp: 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[17179573.168000] pnp: 00:0d: ioport range 0x1000-0x107f could not be reserved
[17179573.168000] pnp: 00:0d: ioport range 0x1100-0x113f has been reserved
[17179573.168000] pnp: 00:0d: ioport range 0x1200-0x121f has been reserved
[17179573.168000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179573.168000] PCI: Bridge: 0000:00:1c.0
[17179573.168000]   IO window: disabled.
[17179573.168000]   MEM window: d0000000-d03fffff
[17179573.168000]   PREFETCH window: disabled.
[17179573.168000] PCI: Bridge: 0000:00:1c.1
[17179573.168000]   IO window: disabled.
[17179573.168000]   MEM window: disabled.
[17179573.168000]   PREFETCH window: disabled.
[17179573.168000] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[17179573.168000]   IO window: 00003000-000030ff
[17179573.168000]   IO window: 00003400-000034ff
[17179573.168000]   PREFETCH window: 40000000-41ffffff
[17179573.168000]   MEM window: 42000000-43ffffff
[17179573.168000] PCI: Bridge: 0000:00:1e.0
[17179573.168000]   IO window: 3000-3fff
[17179573.168000]   MEM window: d0400000-d07fffff
[17179573.168000]   PREFETCH window: 40000000-41ffffff
[17179573.168000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.168000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.168000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179573.168000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179573.168000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.168000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179573.172000] audit: initializing netlink socket (disabled)
[17179573.172000] audit(1151258644.172:1): initialized
[17179573.172000] highmem bounce pool size: 64 pages
[17179573.172000] VFS: Disk quotas dquot_6.5.1
[17179573.172000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.172000] Initializing Cryptographic API
[17179573.172000] io scheduler noop registered
[17179573.172000] io scheduler anticipatory registered
[17179573.172000] io scheduler deadline registered
[17179573.172000] io scheduler cfq registered
[17179573.172000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.172000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.172000] assign_interrupt_mode Found MSI capability
[17179573.172000] Allocate Port Service[pcie00]
[17179573.172000] Allocate Port Service[pcie02]
[17179573.172000] Allocate Port Service[pcie03]
[17179573.172000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179573.172000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179573.172000] assign_interrupt_mode Found MSI capability
[17179573.172000] Allocate Port Service[pcie00]
[17179573.172000] Allocate Port Service[pcie02]
[17179573.172000] Allocate Port Service[pcie03]
[17179573.172000] isapnp: Scanning for PnP cards...
[17179573.528000] isapnp: No Plug & Play device found
[17179573.552000] PNP: PS/2 Controller [PNP0303:C1C1,PNP0f13:C1C2] at 0x60,0x64 irq 1,12
[17179573.552000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179573.552000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179573.552000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179573.552000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179573.552000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179573.552000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.552000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.552000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.552000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[17179573.556000] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.556000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 22 (level, low) -> IRQ 217
[17179573.556000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179573.556000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.556000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.556000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.560000] mice: PS/2 mouse device common for all mice
[17179573.560000] EISA: Probing bus 0 at eisa.0
[17179573.560000] Cannot allocate resource for EISA slot 1
[17179573.560000] Cannot allocate resource for EISA slot 2
[17179573.560000] Cannot allocate resource for EISA slot 3
[17179573.560000] Cannot allocate resource for EISA slot 5
[17179573.560000] EISA: Detected 0 cards.
[17179573.560000] NET: Registered protocol family 2
[17179573.592000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.596000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.596000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.596000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.596000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.596000] TCP reno registered
[17179573.596000] TCP bic registered
[17179573.596000] NET: Registered protocol family 1
[17179573.596000] NET: Registered protocol family 8
[17179573.596000] NET: Registered protocol family 20
[17179573.596000] Using IPI Shortcut mode
[17179573.596000] ACPI wakeup devices:
[17179573.596000] C06D C0BE C0C5 C0C6 C0C8 C006 C007 C0DE C1CE
[17179573.596000] ACPI: (supports S0 S3 S4 S5)
[17179573.596000] Freeing unused kernel memory: 288k freed
[17179573.680000] vga16fb: initializing
[17179573.680000] vga16fb: mapped to 0xc00a0000
[17179573.800000] Console: switching to colour frame buffer device 80x25
[17179573.800000] fb0: VGA16 VGA frame buffer device
[17179574.908000] Capability LSM initialized
[17179574.960000] ACPI: Fan [C26B] (off)
[17179574.960000] ACPI: Fan [C26C] (off)
[17179574.960000] ACPI: Fan [C26D] (off)
[17179574.960000] ACPI: Fan [C26E] (off)
[17179574.968000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.968000] ACPI: Processor [C000] (supports 8 throttling states)
[17179574.988000] ACPI: Thermal Zone [TZ1] (44 C)
[17179575.004000] ACPI: Thermal Zone [TZ2] (43 C)
[17179575.016000] ACPI: Thermal Zone [TZ3] (31 C)
[17179575.732000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179575.732000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[17179575.732000] ICH6: chipset revision 3
[17179575.732000] ICH6: not 100% native mode: will probe irqs later
[17179575.732000]     ide0: BM-DMA at 0x2580-0x2587, BIOS settings: hda:DMA, hdb:DMA
[17179575.732000] Probing IDE interface ide0...
[17179576.020000] hda: FUJITSU MHV2040AH, ATA DISK drive
[17179576.468000] hdb: UJDA765aDVD/CDRW, ATAPI CD/DVD-ROM drive
[17179576.524000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.608000] hda: max request size: 128KiB
[17179576.608000] hda: 78140160 sectors (40007 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.620000] hda: cache flushes supported
[17179576.620000]  hda: hda1 hda2 < hda5 >
[17179576.660000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, (U)DMA
[17179576.660000] Uniform CD-ROM driver Revision: 3.20
[17179576.948000] usbcore: registered new driver usbfs
[17179576.948000] usbcore: registered new driver hub
[17179576.952000] USB Universal Host Controller Interface driver v2.3
[17179576.952000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 225
[17179576.952000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.952000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.952000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.952000] uhci_hcd 0000:00:1d.0: irq 225, io base 0x00002000
[17179576.952000] hub 1-0:1.0: USB hub found
[17179576.952000] hub 1-0:1.0: 2 ports detected
[17179577.056000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 177
[17179577.056000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.056000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.056000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.056000] uhci_hcd 0000:00:1d.1: irq 177, io base 0x00002020
[17179577.056000] hub 2-0:1.0: USB hub found
[17179577.056000] hub 2-0:1.0: 2 ports detected
[17179577.160000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179577.160000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.160000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.160000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.160000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00002040
[17179577.160000] hub 3-0:1.0: USB hub found
[17179577.160000] hub 3-0:1.0: 2 ports detected
[17179577.264000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 225
[17179577.264000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.264000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.264000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.264000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179577.264000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179577.264000] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xd0980000
[17179577.268000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.268000] hub 4-0:1.0: USB hub found
[17179577.268000] hub 4-0:1.0: 8 ports detected
[17179577.400000] Probing IDE interface ide1...
[17179577.904000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179577.988000] Attempting manual resume
[17179578.044000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.128000] kjournald starting.  Commit interval 5 seconds
[17179588.744000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.748000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.196000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.200000] agpgart: Detected an Intel 915GM Chipset.
[17179589.200000] agpgart: Detected 7932K stolen memory.
[17179589.216000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179589.448000] hw_random: RNG not detected
[17179589.752000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 21 (level, low) -> IRQ 233
[17179589.752000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179590.104000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000
[17179590.104000] serio: Synaptics pass-through port at isa0060/serio4/input0
[17179590.148000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179590.572000] intel8x0_measure_ac97_clock: measured 55442 usecs
[17179590.572000] intel8x0: clocking to 48000
[17179591.000000] tg3.c:v3.47 (Dec 28, 2005)
[17179591.000000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179591.000000] PCI: Setting latency timer of device 0000:10:00.0 to 64
[17179591.024000] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:15:60:ad:0c:25
[17179591.024000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[17179591.024000] eth0: dma_rwctrl[76180000]
[17179591.048000] Real Time Clock Driver v1.12
[17179591.076000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179591.076000] Yenta: CardBus bridge found at 0000:02:06.0 [103c:0944]
[17179591.076000] Yenta: Enabling burst memory read transactions
[17179591.076000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179591.076000] Yenta: Routing CardBus interrupts to PCI
[17179591.076000] Yenta TI: socket 0000:02:06.0, mfunc 0x01111b22, devctl 0x64
[17179591.080000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17179591.084000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17179591.084000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179591.104000] parport: PnPBIOS parport detected.
[17179591.104000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179591.112000] input: PC Speaker as /class/input/input2
[17179591.116000] ieee80211_crypt: registered algorithm 'NULL'
[17179591.120000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179591.120000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179591.152000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179591.152000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179591.152000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179591.152000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 233
[17179591.152000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179591.160000] Bluetooth: Core ver 2.8
[17179591.160000] NET: Registered protocol family 31
[17179591.160000] Bluetooth: HCI device and connection manager initialized
[17179591.160000] Bluetooth: HCI socket layer initialized
[17179591.192000] Bluetooth: HCI USB driver ver 2.9
[17179591.196000] usbcore: registered new driver hci_usb
[17179591.308000] Yenta: ISA IRQ mask 0x0c78, PCI irq 185
[17179591.308000] Socket status: 30000006
[17179591.308000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[17179591.308000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179591.308000] cs: IO port probe 0x3000-0x3fff: clean.
[17179591.308000] pcmcia: parent PCI bridge Memory window: 0xd0400000 - 0xd07fffff
[17179591.308000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x41ffffff
[17179591.392000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179591.392000] sdhci: Copyright(c) Pierre Ossman
[17179591.656000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179591.728000] ACPI: PCI Interrupt 0000:02:06.4[C] -> GSI 22 (level, low) -> IRQ 217
[17179591.776000] sdhci: ============== REGISTER DUMP ==============
[17179591.776000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179591.776000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179591.776000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179591.776000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179591.776000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179591.776000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179591.776000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179591.776000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179591.776000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179591.776000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179591.776000] sdhci: ===========================================
[17179591.824000] mmc0: SDHCI at 0xd0404000 irq 217 DMA
[17179591.924000] sdhci: ============== REGISTER DUMP ==============
[17179591.924000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179591.924000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179591.924000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179591.924000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179591.924000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179591.924000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179591.924000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179591.924000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179591.924000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179591.924000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179591.924000] sdhci: ===========================================
[17179591.976000] mmc1: SDHCI at 0xd0405000 irq 217 DMA
[17179592.072000] sdhci: ============== REGISTER DUMP ==============
[17179592.072000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179592.072000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179592.072000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179592.072000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179592.072000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179592.072000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179592.072000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179592.072000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179592.072000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179592.072000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[17179592.072000] sdhci: ===========================================
[17179592.124000] mmc2: SDHCI at 0xd0406000 irq 217 DMA
[17179592.268000] tpm_inf_pnp 00:05: Found C1B6 with ID IFX0101
[17179592.268000] tpm_inf_pnp 00:05: TPM found: config base 0x560, io base 0x570, chip version 0006, vendor id 15d1 (Infineon), product id 0006 (SLD 9630 TT 1.1)
[17179592.668000] ts: Compaq touchscreen protocol output
[17179594.016000] cs: IO port probe 0x100-0x3af: clean.
[17179594.016000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179594.016000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.016000] cs: IO port probe 0xc00-0xcf7: clean.
[17179594.020000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.972000] input: PS/2 Generic Mouse as /class/input/input3
[17179595.824000] lp0: using parport0 (interrupt-driven).
[17179595.904000] Adding 1622524k swap on /dev/hda5.  Priority:-1 extents:1 across:1622524k
[17179596.044000] EXT3 FS on hda1, internal journal
[17179596.324000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179596.324000] md: bitmap version 4.39
[17179596.892000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179597.628000] cdrom: open failed.
[17179599.708000] ACPI: AC Adapter [C172] (off-line)
[17179599.740000] ACPI: Battery Slot [C174] (battery present)
[17179599.740000] ACPI: Battery Slot [C173] (battery absent)
[17179599.872000] ACPI: Power Button (FF) [PWRF]
[17179599.872000] ACPI: Sleep Button (CM) [C1EC]
[17179599.872000] ACPI: Lid Switch [C1ED]
[17179600.040000] ibm_acpi: ec object not found
[17179600.084000] pcc_acpi: loading...
[17179600.152000] wmi_add device=dfe81c00
[17179600.152000] calling WQBA
[17179600.236000] ACPI: Video Device [C05A] (multi-head: yes  rom: no  post: no)
[17179604.900000] [drm] Initialized drm 1.0.1 20051102
[17179604.904000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179604.904000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179606.664000] ppdev: user-space parallel port driver
[17179607.208000] apm: BIOS not found.
[17179611.656000] Bluetooth: L2CAP ver 2.8
[17179611.656000] Bluetooth: L2CAP socket layer initialized
[17179611.860000] Bluetooth: RFCOMM socket layer initialized
[17179611.860000] Bluetooth: RFCOMM TTY layer initialized
[17179611.860000] Bluetooth: RFCOMM ver 1.7
[17179620.376000] NET: Registered protocol family 10
[17179620.376000] lo: Disabled Privacy Extensions
[17179620.376000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179620.376000] IPv6 over IPv4 tunneling driver
[17179620.384000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
[17179630.436000] eth1: no IPv6 routers present
[17179634.052000] NET: Registered protocol family 17
[17179637.772000] ieee80211_crypt: registered algorithm 'TKIP'
[17179652.964000] eth1: no IPv6 routers present
[17187435.300000] TKIP: replay detected: STA=00:0c:e5:50:0e:99 previous TSC 000000001e53 received TSC 000000001e52
[17187435.300000] TKIP: replay detected: STA=00:0c:e5:50:0e:99 previous TSC 000000001e58 received TSC 000000001e56
[17187435.304000] TKIP: replay detected: STA=00:0c:e5:50:0e:99 previous TSC 000000001e59 received TSC 000000001e57
[17187435.308000] TKIP: replay detected: STA=00:0c:e5:50:0e:99 previous TSC 000000001e6b received TSC 000000001e69
[17187435.308000] TKIP: replay detected: STA=00:0c:e5:50:0e:99 previous TSC 000000001e6c received TSC 000000001e6a
[17188036.760000] TKIP: replay detected: STA=00:0c:e5:50:0e:99 previous TSC 00000001b93f received TSC 00000001b93d
[17188036.764000] TKIP: replay detected: STA=00:0c:e5:50:0e:99 previous TSC 00000001b940 received TSC 00000001b93e
[17188740.112000] mmcblk0: mmc2:a95c SD256 247040KiB <NULL>
[17188740.112000]  mmcblk0: p1
[17188741.032000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

---

### Post by jive_turkey on 2006-06-25
Ubuntu still wont recognize the sd reader on my 700m, bummer!

---

### Post by Tumdian on 2006-06-26
yeppp! supported my sd card reader on my HP Dv4030us just fine!

---

### Post by blakegrover on 2006-06-26
Mine was supported also - Dell Inspiron 9300 :)

---

### Post by Karbonik on 2006-06-26
Not working on my Presario R3000

Which apparently is actually 3200, but whatever, yet another reason not to buy Compaq ever again, if they can't even figure out their own shoyt

Kernel 2.6.15-25-386
KDE 3.5.3

Shows up in System Settings as:
Optical Disk SD-R6252   
mountpoint :  /media/cdrom0  
vfat  ###changed manually from Auomatic
/dev/hdc  

The problem I keep getting is that it won't enable - "no media found"

I already went thru and changed the permissions, set it as user-mountable, but no dice.

Any suggestions?

---

### Post by kd5ftn on 2006-06-26
I also found that my SD slot works right out of the box.

Dapper Drake on a Fujitsu N6010

---

### Post by jturnbul on 2006-06-27
doesnt work on toshiba M30.  

Questio, Im no linux guru, but hasnt SD been out for years now.  How has the people who develop the kernel not taken care of supporting SD cards.  They are one of the most common portable storage mediums.  I cant believe I have to boot to XP just to get something on to my SD card

---

### Post by clooch on 2006-06-27
[QUOTE=jturnbul]doesnt work on toshiba M30.  

Questio, Im no linux guru, but hasnt SD been out for years now.  How has the people who develop the kernel not taken care of supporting SD cards.  They are one of the most common portable storage mediums.  I cant believe I have to boot to XP just to get something on to my SD card[/QUOTE]
sorry my zv5410us is not readig sd cards either

---

### Post by jturnbul on 2006-06-27
question for those whose SD reader does work... could you please post which dev it gets mounted under.  My USB thumb drives mount under sda(X), what does the SD card mount as???  Maybe I can try to mount it manually, just not sure how it gets recognized

---

### Post by CrunchyDoodle on 2006-06-27
I checked the Device Manager and it said /dev/mmcblk0p1.

Bye.     :cool:

---

### Post by doog on 2006-06-28
FYI, many of the HP/Compaq laptops use a TI chip for the builtin SD card reader and Ubuntu patched the 2.6.15 kernel to get this working.  For those who want to build a default kernel or know how patches work, here's what I used to patch the 2.6.17 kernel.org kernel with to enable the TI cardread chip in my Compaq R4000:

```
--- linux-2.6.17/drivers/mmc/sdhci.c	2006-06-03 23:03:10.000000000 -0400
+++ linux-2.6.17/drivers/mmc/sdhci.c	2006-06-13 16:44:51.000000000 -0400
@@ -1140,6 +1140,22 @@
 	mmc_free_host(mmc);
 }
 
+static void __devinit fudge_ti(struct pci_dev *pdev)
+{
+	struct pci_dev *controller;
+	u8 config;
+
+	controller = pci_find_device(PCI_VENDOR_ID_TI, 0x8033, NULL);
+	if (!controller)
+		controller = pci_find_device(PCI_VENDOR_ID_TI, 0xac8f, NULL);
+	if (!controller)
+		return;
+
+	pci_read_config_byte(controller, 0x4c, &config);
+	config |= 0x02;
+	pci_write_config_byte(controller, 0x4c, config);
+}
+
 static int __devinit sdhci_probe(struct pci_dev *pdev,
 	const struct pci_device_id *ent)
 {
@@ -1152,6 +1168,10 @@
 
 	DBG("found at %s\n", pci_name(pdev));
 
+	if (pdev->vendor == PCI_VENDOR_ID_TI) {
+		fudge_ti(pdev);
+	}
+
 	ret = pci_read_config_byte(pdev, PCI_SLOT_INFO, &slots);
 	if (ret)
 		return ret;

```

---

### Post by EpicCrusadr on 2006-06-28
On my Toshiba m55, if I plug in a SD card it is recognized, but xD cards are not. I'm not sure about Memory Sticks.

---

### Post by xrchris on 2006-06-28
My Rock Xtreme CT (Clevo M570) supports CF and SD cards out of the box but does not read memorystick or memorystick duos even though i am using exactly the same hardware.

---

### Post by doog on 2006-06-29
I think it's ONLY SD card folks. It could be that OTHER memory stiks don't work because the fix patches the file sdhci.c and not memorystickhci.c, xdhci.c, or smhdi.c.  You might want to check with the kernel.org group to see what all is currently supported, what's getting supported, and what's not getting supported down the road.

---

### Post by GoodPanos on 2006-06-29
Impressive!!  Mine worked right of the back too.  =D>  I have a Dell Inspiron 6000

---

### Post by LPent on 2006-06-29
I can confirm it works on my Asus A6Vm as well. :D

---

### Post by iimre on 2006-07-08
No luck with nc6000 :(
Have you any special settings (udev etc.)?

---

### Post by loko on 2006-07-08
For me it works with a Asus W5F,

BUT:

Only SD-Cards work in the Cardreader while MMC-Cards, which are nearly the same don't work.

I wish MMC-Cards would also work.


Can anybody confirm this-?

---

### Post by mabhatter on 2006-08-16
> **jturnbul said:**
> doesnt work on toshiba M30.  

Questio, Im no linux guru, but hasnt SD been out for years now.  How has the people who develop the kernel not taken care of supporting SD cards.  They are one of the most common portable storage mediums.  I cant believe I have to boot to XP just to get something on to my SD card

just pick up a cheap card reader.  I find the mini single card ones work the best.  It's just the reader built in that it can't read, not SD cards in general.

---

### Post by chele on 2006-08-17
> **jturnbul said:**
> doesnt work on toshiba M30.  

Questio, Im no linux guru, but hasnt SD been out for years now.  How has the people who develop the kernel not taken care of supporting SD cards.  They are one of the most common portable storage mediums.  I cant believe I have to boot to XP just to get something on to my SD cardThe card reader built into your Toshiba is secret, the manufacturer will not publish the specification's  that would enable the Linux kernel hackers can build a driver. 

[-X No need to use XP, an external USB card reader can be used until such time as a driver for your built-in reader can be hacked together.

---

### Post by ronintiger on 2006-08-20
Hi!

The SD card reader works fine on my Asus W5F. 
I wasn't expecting it to work.. in the first place. :-D

---

### Post by knubbe on 2006-08-23
My 64mb card worked like a charm, but the 2gb card doesnt work at all ](*,)

i have a Dell inspiron 6000. Anyone knows if its possible to mount 2gb-cards?

---

### Post by kekojeep on 2006-08-24
> **clooch said:**
> sorry my zv5410us is not readig sd cards either

Neither is my HP zv5466us.. still gotta boot to XP to use SD cards..

---

