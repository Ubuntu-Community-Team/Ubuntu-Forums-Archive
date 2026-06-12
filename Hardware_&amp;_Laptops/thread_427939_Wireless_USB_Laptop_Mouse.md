---
title: "Wireless USB Laptop Mouse"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by c0ldfusi0n on 2007-04-29
Hey people.

First of all, thanks for taking the time to read. I check this forum regularly when i have issues with my Ubuntu system and it's a great help. Usually however, i can just google my problem and fix it with the results i find, but this time it's not the case.

I have a Dell Inspiron 1501 Laptop on which i have recently clean installed Feisty. I have two problems with it, one of which i will speak here seeing as the other seems to be quite popular and i might eventually be able to fix it myself.

So my problem is, as the topic states, with a wireless USB mouse for my laptop. You know the kind... it's small, has an embedded usb key-like device that you pop out of the mouse and plug into your computer, which then activates the mouse and acts as the wireless signal relay. I can't find it on the Creative site, but it's a Creative Labs, at least that's what lsusb tells me.

Okay so here's the problem. When i had edgy, it worked fine. The first time i plugged it with Feisty, it worked fine too. However now it doesn't work. The only thing i can see that i modified is my xorg.conf file, which was modified according to [this guide](http://ubuntu1501.blogspot.com/2007/04/configure-synaptic-touchpad-settngs.html) (link) to use Qsynaptics. Therefore the only thing that i have done is install qsynaptics via aptitude and added a  *Option "SHMConfig" "on"* to my xorg.conf's InputDevice section for the Synaptics Touchpad.

I have no idea why it stopped working. I contacted the author of Qsynaptics to ask if it would be possible that his software interferes in some way, and he said he would be surprised, and that it's most likely my xorg driver.

Any help is appreciated.


Note: Here's some extra info:
pluc@pLaptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 001 Device 001: ID 0000:0000
pluc@pLaptop:~$ ls /dev/input/mouse*
/dev/input/mouse0  /dev/input/mouse1  /dev/input/mouse2

---

### Post by c0ldfusi0n on 2007-04-30
If that can help, this is the output of dmesg:


[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=5d0e2fe8-9a4d-4ef9-9f3a-6ae39b571d7c ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e70000 (usable)
[    0.000000]  BIOS-e820: 0000000037e70000 - 0000000037e81000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e81000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 228976) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00000000000f8750
[    0.000000] ACPI: RSDT (v001 DELL    M08     0x06040000  LTP 0x00000000) @ 0x0000000037e7a60c
[    0.000000] ACPI: FADT (v001 ATI    Bowfin   0x06040000 ATI 0x000f4240) @ 0x0000000037e80c4d
[    0.000000] ACPI: TCPA (v002 AMD             0x06040000 PTEC 0x00000000) @ 0x0000000037e80cc1
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x0000000037e80cf3
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x0000000037e80e08
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x0000000037e80e4e
[    0.000000] ACPI: SLIC (v001 DELL    M08     0x06040000  LTP 0x00000000) @ 0x0000000037e80e8a
[    0.000000] ACPI: DSDT (v001    ATI    SB600 0x06040000 MSFT 0x03000000) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 0000000037e70000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 228976) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-0000000037e70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   228976
[    0.000000] On node 0 totalpages: 228877
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1086 pages reserved
[    0.000000]   DMA zone: 2855 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3074 pages used for memmap
[    0.000000]   DMA32 zone: 221806 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009d000 - 000000000009e000
[    0.000000] Nosave address range: 000000000009e000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000ce000
[    0.000000] Nosave address range: 00000000000ce000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 224661
[    0.000000] Kernel command line: root=UUID=5d0e2fe8-9a4d-4ef9-9f3a-6ae39b571d7c ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   14.603596] Console: colour VGA+ 80x25
[   14.604083] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.604772] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.604879] Checking aperture...
[   14.604882] CPU 0: aperture @ 8932000000 size 32 MB
[   14.604884] Aperture too small (32 MB)
[   14.615279] No AGP bridge found
[   14.622702] Memory: 889680k/915904k available (2217k kernel code, 25828k reserved, 1162k data, 304k init)
[   14.700686] Calibrating delay using timer specific routine.. 3993.74 BogoMIPS (lpj=7987480)
[   14.700743] Security Framework v1.0.0 initialized
[   14.700749] SELinux:  Disabled at boot.
[   14.700773] Mount-cache hash table entries: 256
[   14.700912] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.700915] CPU: L2 Cache: 512K (64 bytes/line)
[   14.700917] CPU 0/0 -> Node 0
[   14.700937] SMP alternatives: switching to UP code
[   14.701092] Freeing SMP alternatives: 24k freed
[   14.701201] Early unpacking initramfs... done
[   15.027274] ACPI: Core revision 20060707
[   15.030418] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.107320] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   16.147384] Using local APIC timer interrupts.
[   16.197484] result 12469124
[   16.197486] Detected 12.469 MHz APIC timer.
[   16.199982] Brought up 1 CPUs
[   16.200023] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   16.200026] time.c: Detected 1995.057 MHz processor.
[   16.200318] Time: 18:29:29  Date: 03/29/107
[   16.200350] NET: Registered protocol family 16
[   16.200425] ACPI: bus type pci registered
[   16.200432] PCI: Using configuration type 1
[   16.206163] ACPI: Interpreter enabled
[   16.206166] ACPI: Using IOAPIC for interrupt routing
[   16.206602] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.206606] PCI: Probing PCI hardware (bus 00)
[   16.208378] Boot video device is 0000:01:05.0
[   16.208898] PCI: Transparent bridge - 0000:00:14.4
[   16.208938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.212155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   16.212402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   16.214012] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   16.214242] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   16.214472] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   16.214701] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   16.214931] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   16.215162] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   16.215392] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   16.215619] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   16.215851] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   16.221234] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.221458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.224546] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.224559] pnp: PnP ACPI init
[   16.228000] pnp: PnP ACPI: found 10 devices
[   16.228050] PCI: Using ACPI for IRQ routing
[   16.228053] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.228060] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   16.228062] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   16.228161] NET: Registered protocol family 8
[   16.228163] NET: Registered protocol family 20
[   16.228443] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   16.228446] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   16.228696] PCI: Bridge: 0000:00:01.0
[   16.228699]   IO window: 9000-9fff
[   16.228702]   MEM window: c0100000-c01fffff
[   16.228705]   PREFETCH window: c8000000-cfffffff
[   16.228708] PCI: Bridge: 0000:00:05.0
[   16.228709]   IO window: disabled.
[   16.228711]   MEM window: disabled.
[   16.228713]   PREFETCH window: disabled.
[   16.228716] PCI: Bridge: 0000:00:06.0
[   16.228717]   IO window: disabled.
[   16.228720]   MEM window: c0200000-c02fffff
[   16.228722]   PREFETCH window: disabled.
[   16.228725] PCI: Bridge: 0000:00:14.4
[   16.228726]   IO window: disabled.
[   16.228732]   MEM window: c0300000-c03fffff
[   16.228735]   PREFETCH window: disabled.
[   16.228753] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   16.228759] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.228839] NET: Registered protocol family 2
[   16.263979] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   16.264179] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   16.265171] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.265638] TCP: Hash tables configured (established 131072 bind 65536)
[   16.265641] TCP reno registered
[   16.276033] checking if image is initramfs... it is
[   16.885597] Freeing initrd memory: 7305k freed
[   16.889695] audit: initializing netlink socket (disabled)
[   16.889707] audit(1177871368.176:1): initialized
[   16.889835] VFS: Disk quotas dquot_6.5.1
[   16.889851] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.889897] io scheduler noop registered
[   16.889899] io scheduler anticipatory registered
[   16.889901] io scheduler deadline registered
[   16.889912] io scheduler cfq registered (default)
[   16.890145] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   16.890164] assign_interrupt_mode Found MSI capability
[   16.890167] Allocate Port Service[0000:00:05.0:pcie00]
[   16.890196] Allocate Port Service[0000:00:05.0:pcie02]
[   16.890252] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.890270] assign_interrupt_mode Found MSI capability
[   16.890273] Allocate Port Service[0000:00:06.0:pcie00]
[   16.890300] Allocate Port Service[0000:00:06.0:pcie02]
[   16.911375] Real Time Clock Driver v1.12ac
[   16.911415] Linux agpgart interface v0.102 (c) Dave Jones
[   16.911418] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.911978] mice: PS/2 mouse device common for all mice
[   16.912440] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.912623] input: Macintosh mouse button emulation as /class/input/input0
[   16.912656] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.912660] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.912925] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.916050] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.916056] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.916141] TCP cubic registered
[   16.916148] NET: Registered protocol family 1
[   16.916291] ACPI: (supports S0 S3 S4 S5)
[   16.916332]   Magic number: 3:4:495
[   16.916453] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.916526] Freeing unused kernel memory: 304k freed
[   16.947230] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.096403] Capability LSM initialized
[   18.319087] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.319093] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.319100] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   18.618788] ACPI: Thermal Zone [THRM] (57 C)
[   19.202357] SCSI subsystem initialized
[   19.207504] libata version 2.20 loaded.
[   19.208902] ahci 0000:00:12.0: version 2.1
[   19.208926] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   19.224305] usbcore: registered new interface driver usbfs
[   19.224326] usbcore: registered new interface driver hub
[   19.224345] usbcore: registered new device driver usb
[   19.225067] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller
(OHCI) Driver
[   20.210015] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   20.210020] ahci 0000:00:12.0: flags: 64bit ncq ilck pm led clo pmp pio slum part
[   20.210128] ata1: SATA max UDMA/133 cmd 0xffffc20000012100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   20.210206] ata2: SATA max UDMA/133 cmd 0xffffc20000012180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   20.210284] ata3: SATA max UDMA/133 cmd 0xffffc20000012200 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   20.210365] ata4: SATA max UDMA/133 cmd 0xffffc20000012280 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   20.210377] scsi0 : ahci
[   20.693749] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.694658] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   20.694663] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC74P, max UDMA/100
[   20.694666] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   20.695719] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   20.695722] ata1.00: configured for UDMA/100
[   20.695733] scsi1 : ahci
[   21.005583] ata2: SATA link down (SStatus 0 SControl 300)
[   21.005600] scsi2 : ahci
[   21.317427] ata3: SATA link down (SStatus 0 SControl 300)
[   21.317443] scsi3 : ahci
[   21.629271] ata4: SATA link down (SStatus 0 SControl 300)
[   21.629374] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[   21.630932] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.630947] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   21.631196] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   21.631217] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0005000
[   21.639293] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   21.639305] sda: Write Protect is off
[   21.639308] sda: Mode Sense: 00 3a 00 00
[   21.639320] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.639371] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   21.639379] sda: Write Protect is off
[   21.639380] sda: Mode Sense: 00 3a 00 00
[   21.639392] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.639398]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[   21.685387] hub 1-0:1.0: USB hub found
[   21.685397] hub 1-0:1.0: 2 ports detected
[   21.789295] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   21.789311] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   21.789330] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   21.789349] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000
[   21.845281] usb usb2: configuration #1 chosen from 1 choice
[   21.845304] hub 2-0:1.0: USB hub found
[   21.845315] hub 2-0:1.0: 2 ports detected
[   21.949224] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.949240] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   21.949262] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   21.949280] ohci_hcd 0000:00:13.2: irq 18, io mem 0xc0007000
[   22.005207] usb usb3: configuration #1 chosen from 1 choice
[   22.005234] hub 3-0:1.0: USB hub found
[   22.005243] hub 3-0:1.0: 2 ports detected
[   22.045274]  sda1 sda2 < sda5 >
[   22.071907] sd 0:0:0:0: Attached scsi disk sda
[   22.075165] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.109145] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   22.109163] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   22.109185] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   22.109201] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0008000
[   22.165119] usb usb4: configuration #1 chosen from 1 choice
[   22.165147] hub 4-0:1.0: USB hub found
[   22.165158] hub 4-0:1.0: 2 ports detected
[   22.269066] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   22.269084] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   22.269106] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   22.269122] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0009000
[   22.292151] Attempting manual resume
[   22.292154] swsusp: Resume From Partition 8:5
[   22.292156] PM: Checking swsusp image.
[   22.292334] PM: Resume from disk failed.
[   22.325049] usb usb5: configuration #1 chosen from 1 choice
[   22.325075] hub 5-0:1.0: USB hub found
[   22.325086] hub 5-0:1.0: 2 ports detected
[   22.341017] kjournald starting.  Commit interval 5 seconds
[   22.341028] EXT3-fs: mounted filesystem with ordered data mode.
[   22.429088] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   22.429104] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   22.429127] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   22.429169] ehci_hcd 0000:00:13.5: debug port 1
[   22.429184] ehci_hcd 0000:00:13.5: irq 19, io mem 0xc0004400
[   22.429195] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.429265] usb usb6: configuration #1 chosen from 1 choice
[   22.429286] hub 6-0:1.0: USB hub found
[   22.429292] hub 6-0:1.0: 10 ports detected
[   22.533040] b44.c:v1.01 (Jun 16, 2006)
[   22.533064] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   22.536667] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:58:66:ab
[   35.171312] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.175956] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.186726] NET: Registered protocol family 17
[   35.285313] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[   35.285328] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   35.285338] SB600_PATA: chipset revision 0
[   35.285341] SB600_PATA: not 100% native mode: will probe irqs later
[   35.285349]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[   35.285360] Probing IDE interface ide0...
[   35.704258] sdhci: Secure Digital Host Controller Interface driver
[   35.704262] sdhci: Copyright(c) Pierre Ossman
[   35.827588] input: PC Speaker as /class/input/input2
[   36.030658] hda: Optiarc DVD+/-RW AD-5540A, ATAPI CD/DVD-ROM drive
[   36.090274] b44: eth0: Link is up at 100 Mbps, full duplex.
[   36.090278] b44: eth0: Flow control is off for TX and off for RX.
[   36.556596] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   36.594215] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   36.704405] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   36.713747] sdhci: SDHCI controller found at 0000:08:01.0 [1180:0822] (rev 19)
[   36.713772] ACPI: PCI Interrupt 0000:08:01.0[B] -> GSI 20 (level, low) -> IRQ 20
[   36.713858] mmc0: SDHCI at 0xc0302000 irq 20 DMA
[   36.723540] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   36.781191] hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   36.781199] Uniform CD-ROM driver Revision: 3.20
[   37.375988] fuse init (API version 7.8)
[   37.473100] lp: driver loaded but no devices found
[   37.521442] Adding 2626588k swap on /dev/disk/by-uuid/ae138eab-148c-4b2f-8360-9e5177fab653.  Priority:-1 extents:1 across:2626588k
[   37.652485] EXT3 FS on sda1, internal journal
[   41.481118] ndiswrapper version 1.42 loaded (smp=yes)
[   41.577492] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   41.579193] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   41.579423] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   41.579453] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   41.582644] ndiswrapper: using IRQ 18
[   41.939297] wlan0: ethernet device 00:19:7d:94:a7:55 using NDIS
driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
[   41.939332] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   41.942246] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   41.950091] usbcore: registered new interface driver ndiswrapper
[   43.257809] NET: Registered protocol family 10
[   43.257895] lo: Disabled Privacy Extensions
[   43.259560] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   46.486469] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   46.566130] Using specific hotkey driver
[   46.654166] input: Power Button (FF) as /class/input/input4
[   46.658078] ACPI: Power Button (FF) [PWRF]
[   46.682513] input: Power Button (CM) as /class/input/input5
[   46.686409] ACPI: Power Button (CM) [PWRB]
[   46.710743] input: Sleep Button (CM) as /class/input/input6
[   46.714621] ACPI: Sleep Button (CM) [SLPB]
[   46.738957] input: Lid Switch as /class/input/input7
[   46.742826] ACPI: Lid Switch [LID]
[   46.756487] ACPI: AC Adapter [ACAD] (on-line)
[   46.769820] No dock devices found.
[   46.783425] ibm_acpi: ec object not found
[   46.852924] ACPI: Battery Slot [BAT1] (battery present)
[   46.891669] wmi_add device=ffff8100361f7800
[   46.891673] calling WQBA
[   46.918063] pcc_acpi: loading...
[   47.079245] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
[   47.079286] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[   47.079288] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   47.079291] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   47.079293] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   53.374607] [fglrx] Maximum main memory to use for locked dma buffers: 796 MBytes.
[   53.374892] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   53.412641] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   54.047442] ppdev: user-space parallel port driver
[   55.499573] [fglrx] total      GART = 130023424
[   55.499579] [fglrx] free       GART = 114032640
[   55.499582] [fglrx] max single GART = 114032640
[   55.499584] [fglrx] total      LFB  = 134217728
[   55.499586] [fglrx] free       LFB  = 119828480
[   55.499588] [fglrx] max single LFB  = 119828480
[   55.499590] [fglrx] total      Inv  = 0
[   55.499591] [fglrx] free       Inv  = 0
[   55.499593] [fglrx] max single Inv  = 0
[   55.499595] [fglrx] total      TIM  = 0
[   56.981340] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   57.116493] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   57.136540] NFSD: starting 90-second grace period
[   59.569725] hda-intel: Invalid position buffer, using LPIB read method instead.
[   59.642099] Bluetooth: Core ver 2.11
[   59.642145] NET: Registered protocol family 31
[   59.642146] Bluetooth: HCI device and connection manager initialized
[   59.642150] Bluetooth: HCI socket layer initialized
[   59.670870] Bluetooth: L2CAP ver 2.8
[   59.670874] Bluetooth: L2CAP socket layer initialized
[   59.984982] Bluetooth: RFCOMM socket layer initialized
[   59.984993] Bluetooth: RFCOMM TTY layer initialized
[   59.984995] Bluetooth: RFCOMM ver 1.8
[   61.772866] eth0: no IPv6 routers present
[   70.462093] heliodor[5734]: segfault at 0000000000000004 rip 00002ace1eb3c26f rsp 00007fff8fbabd70 error 4
[   83.549928] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   83.635162] usb 2-1: configuration #1 chosen from 1 choice
[   83.718948] usbcore: registered new interface driver hiddev
[   83.723409] input: HID 062a:0000 as /class/input/input8
[   83.723977] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:13.1-1
[   83.724187] usbcore: registered new interface driver usbhid
[   83.724348] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  195.960545] [fglrx] PCIe has already been initialized. Reinitializing ...
[  195.967540] [fglrx] total      GART = 130023424
[  195.967547] [fglrx] free       GART = 114032640
[  195.967550] [fglrx] max single GART = 114032640
[  195.967552] [fglrx] total      LFB  = 134217728
[  195.967554] [fglrx] free       LFB  = 119828480
[  195.967556] [fglrx] max single LFB  = 119828480
[  195.967558] [fglrx] total      Inv  = 0
[  195.967559] [fglrx] free       Inv  = 0
[  195.967561] [fglrx] max single Inv  = 0
[  195.967563] [fglrx] total      TIM  = 0
[  204.574006] heliodor[6277]: segfault at 0000000000000004 rip 00002b0f975e826f rsp 00007fff17100280 error 4
[  213.207036] usb 2-1: USB disconnect, address 2
[  215.567358] usb 2-1: new low speed USB device using ohci_hcd and address 3
[  215.652586] usb 2-1: configuration #1 chosen from 1 choice
[  215.655791] input: HID 062a:0000 as /class/input/input9
[  215.655843] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:13.1-1
[  326.229132] APIC error on CPU0: 00(40)
[ 1448.737423] usb 2-1: USB disconnect, address 3
[ 2237.175781] APIC error on CPU0: 40(40)
[ 3257.035566] APIC error on CPU0: 40(40)
[ 3500.757941] APIC error on CPU0: 40(40)
[ 3599.709555] usb 2-1: new low speed USB device using ohci_hcd and address 4
[ 3599.794786] usb 2-1: configuration #1 chosen from 1 choice
[ 3599.797989] input: HID 062a:0000 as /class/input/input10
[ 3599.798042] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:13.1-1
[ 3602.040232] usb 2-1: USB disconnect, address 4
[ 5123.010456] APIC error on CPU0: 40(40)
[ 5795.251270] APIC error on CPU0: 40(40)
[ 6050.400086] APIC error on CPU0: 40(40)
[ 6473.609100] APIC error on CPU0: 40(40)
[ 7737.120718] Losing some ticks... checking if CPU frequency changed.
[ 7818.090717] APIC error on CPU0: 40(40)
[ 8241.299731] APIC error on CPU0: 40(40)
[ 8577.420147] APIC error on CPU0: 40(40)
[ 8994.512149] APIC error on CPU0: 40(40)
[ 9442.480255] APIC error on CPU0: 40(40)
[11273.848701] usb 1-1: new low speed USB device using ohci_hcd and address 2
[11273.933932] usb 1-1: configuration #1 chosen from 1 choice
[11273.937137] input: HID 062a:0000 as /class/input/input11
[11273.937190] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:13.0-1
[11587.136833] APIC error on CPU0: 40(40)
[11617.065217] usb 1-1: USB disconnect, address 2
[12469.332931] APIC error on CPU0: 40(40)
[12645.176520] APIC error on CPU0: 40(40)
[13236.445747] APIC error on CPU0: 40(40)
[13740.626350] APIC error on CPU0: 40(40)
[14157.718353] APIC error on CPU0: 40(40)
[15340.256792] APIC error on CPU0: 40(40)
[16771.827019] APIC error on CPU0: 40(40)
[16777.944027] APIC error on CPU0: 40(40)
[17453.285717] APIC error on CPU0: 40(40)
[17612.128035] APIC error on CPU0: 40(40)
[19140.644447] APIC error on CPU0: 40(40)
[19890.116290] APIC error on CPU0: 40(40)
[20562.357102] APIC error on CPU0: 40(40)
[22023.722363] APIC error on CPU0: 40(40)
[22081.015942] APIC error on CPU0: 40(40)
[22927.433967] APIC error on CPU0: 40(40)
[24243.417548] APIC error on CPU0: 40(40)
[24870.979401] APIC error on CPU0: 40(40)
[25031.245022] APIC error on CPU0: 40(40)
[25186.800942] APIC error on CPU0: 40(40)
[25871.546034] APIC error on CPU0: 40(40)
[26443.844204] b44: eth0: Link is down.
[26445.043643] b44: eth0: Link is up at 100 Mbps, full duplex.
[26445.043647] b44: eth0: Flow control is off for TX and off for RX.
[26445.044298] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[26447.442439] b44: eth0: Link is down.
[26452.639936] b44: eth0: Link is up at 100 Mbps, full duplex.
[26452.639940] b44: eth0: Flow control is off for TX and off for RX.
[26452.639987] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[26458.286708] eth0: no IPv6 routers present
[26887.941563] APIC error on CPU0: 40(40)


Thanks.

---

### Post by c0ldfusi0n on 2007-04-30
Here's the output of dmesg when i plug the mouse:

[39086.485225] usb 2-1: new low speed USB device using ohci_hcd and address 5
[39086.570473] usb 2-1: configuration #1 chosen from 1 choice
[39086.686001] input: HID 062a:0000 as /class/input/input12
[39086.686053] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:13.1-1 


Still waiting for some help guys.

---

### Post by c0ldfusi0n on 2007-05-18
Must be in the wrong forum.

---

### Post by tyfj on 2007-07-01
I got the same condition, and it looks this cause trouble:

 152.656000] usb 3-2: new low speed USB device using uhci_hcd and address 3

maybe low speed USB can not be supported by Feisty ?

Any way, who can help?

---

