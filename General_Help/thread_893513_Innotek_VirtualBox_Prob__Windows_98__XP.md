---
title: "Innotek VirtualBox Prob:  Windows 98 / XP"
date: 2008-08-18
forum: General Help
---

### Post by robelliott2125 on 2008-08-18
Hey guys,

Just trying to run 98 in a VirtualBox, but having a problem...

I've setup the VHDD, and ensured all the settings are correct, but getting the following error (please see attached image).

With the error, I try both:

```

robert@robert-desktop:~$ /etc/init.d/vboxdrv start
open: Permission denied
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Module vboxdrv not found.

open: Permission denied
 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

```

and

```

robert@robert-desktop:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

```

With the above messages, I've tried dmesg, as it says, and it comes up with stuff I'm unsure about.

Forgive me, I'm still learning Ubuntu.

```

robert@robert-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-15-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Jul 11 19:25:33 UTC 2008 (Ubuntu 2.6.22-15.56-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f6f0000 (usable)
[    0.000000]  BIOS-e820: 000000002f6f0000 - 000000002f6fb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f6fb000 - 000000002f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002f700000 - 000000002f780000 (usable)
[    0.000000]  BIOS-e820: 000000002f780000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 194432) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194432
[    0.000000]   HighMem    194432 ->   194432
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194432
[    0.000000] On node 0 totalpages: 194432
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1487 pages used for memmap
[    0.000000]   Normal zone: 188849 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7B40 checksum 0
[    0.000000] ACPI: RSDP 000F7B40, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 2F6F82D7, 0030 (r1 PTLTD    RSDT    6040001  LTP        0)
[    0.000000] ACPI: FACP 2F6F8307, 0074 (r1 FSC    D145X     6040001         F4240)
[    0.000000] ACPI: DSDT 2F6F837B, 2C03 (r1 FSC    D145X     6040001 MSFT  100000E)
[    0.000000] ACPI: FACS 2F6FBFC0, 0040
[    0.000000] ACPI: APIC 2F6FAF7E, 005A (r1 FSC         APIC    6040001  CSF        0)
[    0.000000] ACPI: BOOT 2F6FAFD8, 0028 (r1 PTLTD  $SBFTBL$  6040001  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0xf008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Built 1 zonelists.  Total pages: 192913
[    0.000000] Kernel command line: root=UUID=701b17f6-0c56-4e57-88f7-35fa036c075f ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2592.481 MHz processor.
[    9.212740] Console: colour VGA+ 80x25
[    9.213579] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.214920] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.232267] Memory: 759180k/777728k available (2016k kernel code, 17812k reserved, 919k data, 364k init, 0k highmem)
[    9.232280] virtual kernel memory layout:
[    9.232281]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    9.232282]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.232283]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
[    9.232284]     lowmem  : 0xc0000000 - 0xef780000   ( 759 MB)
[    9.232285]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    9.232287]       .data : 0xc02f8046 - 0xc03dde84   ( 919 kB)
[    9.232288]       .text : 0xc0100000 - 0xc02f8046   (2016 kB)
[    9.232291] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.232332] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    9.312156] Calibrating delay using timer specific routine.. 5189.37 BogoMIPS (lpj=10378741)
[    9.312189] Security Framework v1.0.0 initialized
[    9.312198] SELinux:  Disabled at boot.
[    9.312214] Mount-cache hash table entries: 512
[    9.312400] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[    9.312417] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    9.312420] CPU: L2 cache: 128K
[    9.312423] CPU: Hyper-Threading is disabled
[    9.312427] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[    9.312441] Compat vDSO mapped to ffffe000.
[    9.312461] Checking 'hlt' instruction... OK.
[    9.328258] SMP alternatives: switching to UP code
[    9.328636] Freeing SMP alternatives: 11k freed
[    9.329028] Early unpacking initramfs... done
[    9.671127] ACPI: Core revision 20070126
[    9.671201] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.673482] CPU0: Intel(R) Celeron(R) CPU 2.60GHz stepping 09
[    9.673527] Total of 1 processors activated (5189.37 BogoMIPS).
[    9.673668] ENABLING IO-APIC IRQs
[    9.673862] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.818994] Brought up 1 CPUs
[    9.819198] Booting paravirtualized kernel on bare hardware
[    9.819291] Time: 15:03:52  Date: 07/18/108
[    9.819331] NET: Registered protocol family 16
[    9.819517] EISA bus registered
[    9.819541] ACPI: bus type pci registered
[    9.819627] PCI: PCI BIOS revision 2.10 entry at 0xfd92b, last bus=2
[    9.819630] PCI: Using configuration type 1
[    9.819632] Setting up standard PCI resources
[    9.824903] ACPI: EC: Look up EC in DSDT
[    9.826780] ACPI: Interpreter enabled
[    9.826785] ACPI: (supports S0 S1 S4 S5)
[    9.826808] ACPI: Using IOAPIC for interrupt routing
[    9.834830] ACPI: Device [LPT] status [00000008]: functional but not present; setting present
[    9.835195] ACPI: Device [ECP] status [00000008]: functional but not present; setting present
[    9.835517] ACPI: Device [COM1] status [00000008]: functional but not present; setting present
[    9.835842] ACPI: Device [COM2] status [00000008]: functional but not present; setting present
[    9.836445] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.836460] PCI: Probing PCI hardware (bus 00)
[    9.837010] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    9.837013] * this clock source is slow. If you are sure your timer does not have
[    9.837014] * this bug, please use "acpi_pm_good" to disable the workaround
[    9.837062] PCI quirk: region f000-f07f claimed by ICH4 ACPI/GPIO/TCO
[    9.837066] PCI quirk: region f180-f1bf claimed by ICH4 GPIO
[    9.837475] PCI: Transparent bridge - 0000:00:1e.0
[    9.837509] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.837724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIH._PRT]
[    9.840852] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.840982] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    9.841105] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    9.841229] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    9.841340] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.841454] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.841582] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.841709] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.841942] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.841967] pnp: PnP ACPI init
[    9.841985] ACPI: bus type pnp registered
[    9.844596] pnp: PnP ACPI: found 10 devices
[    9.844603] ACPI: ACPI bus type pnp unregistered
[    9.844610] PnPBIOS: Disabled by ACPI PNP
[    9.844728] PCI: Using ACPI for IRQ routing
[    9.844733] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.849344] NET: Registered protocol family 8
[    9.849348] NET: Registered protocol family 20
[    9.850836] Time: tsc clocksource has been installed.
[    9.880402] PCI: Bridge: 0000:00:1e.0
[    9.880408]   IO window: 3000-3fff
[    9.880414]   MEM window: d0100000-d01fffff
[    9.880419]   PREFETCH window: 40000000-400fffff
[    9.880436] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.880456] NET: Registered protocol family 2
[    9.918726] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.918978] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    9.921380] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.922231] TCP: Hash tables configured (established 131072 bind 65536)
[    9.922237] TCP reno registered
[    9.930837] checking if image is initramfs... it is
[   10.381519] Switched to high resolution mode on CPU 0
[   10.572620] Freeing initrd memory: 7058k freed
[   10.572822] Simple Boot Flag at 0x69 set to 0x1
[   10.573434] audit: initializing netlink socket (disabled)
[   10.573456] audit(1219071832.016:1): initialized
[   10.578710] VFS: Disk quotas dquot_6.5.1
[   10.578861] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.579107] io scheduler noop registered
[   10.579113] io scheduler anticipatory registered
[   10.579115] io scheduler deadline registered
[   10.579161] io scheduler cfq registered (default)
[   10.579181] Boot video device is 0000:00:02.0
[   10.579613] isapnp: Scanning for PnP cards...
[   10.932962] isapnp: No Plug & Play device found
[   11.060229] Real Time Clock Driver v1.12ac
[   11.060441] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.064116] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.064415] input: Macintosh mouse button emulation as /class/input/input0
[   11.064639] PNP: PS/2 Controller [PNP0303:KEYB,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.066935] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.066942] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.067420] mice: PS/2 mouse device common for all mice
[   11.067780] EISA: Probing bus 0 at eisa.0
[   11.067792] Cannot allocate resource for EISA slot 1
[   11.067795] Cannot allocate resource for EISA slot 2
[   11.067797] Cannot allocate resource for EISA slot 3
[   11.067817] EISA: Detected 0 cards.
[   11.067949] TCP cubic registered
[   11.067979] NET: Registered protocol family 1
[   11.068018] Using IPI No-Shortcut mode
[   11.068296]   Magic number: 4:468:83
[   11.069062] Freeing unused kernel memory: 364k freed
[   11.127667] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.425190] AppArmor: AppArmor initialized<5>audit(1219071834.016:2):  type=1505 info="AppArmor initialized" pid=1177
[   12.437350] fuse init (API version 7.8)
[   12.447891] Failure registering capabilities with primary security module.
[   13.520151] usbcore: registered new interface driver usbfs
[   13.520204] usbcore: registered new interface driver hub
[   13.520267] usbcore: registered new device driver usb
[   13.521546] USB Universal Host Controller Interface driver v3.0
[   13.521653] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.521671] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.521676] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.521934] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.521974] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001000
[   13.522192] usb usb1: configuration #1 chosen from 1 choice
[   13.522245] hub 1-0:1.0: USB hub found
[   13.522261] hub 1-0:1.0: 2 ports detected
[   13.609217] SCSI subsystem initialized
[   13.616484] libata version 2.21 loaded.
[   13.625412] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   13.625428] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.625433] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.625489] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.625523] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001400
[   13.625690] usb usb2: configuration #1 chosen from 1 choice
[   13.625737] hub 2-0:1.0: USB hub found
[   13.625754] hub 2-0:1.0: 2 ports detected
[   13.647920] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   13.729119] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.729135] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.729139] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.729185] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.729221] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001800
[   13.729404] usb usb3: configuration #1 chosen from 1 choice
[   13.729459] hub 3-0:1.0: USB hub found
[   13.729473] hub 3-0:1.0: 2 ports detected
[   13.833817] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   13.833842] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.833846] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.833913] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   13.833965] ehci_hcd 0000:00:1d.7: debug port 1
[   13.833974] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   13.833989] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0080000
[   13.864617] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   13.864641] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.864862] usb usb4: configuration #1 chosen from 1 choice
[   13.864921] hub 4-0:1.0: USB hub found
[   13.864939] hub 4-0:1.0: 6 ports detected
[   13.884187] FDC 0 is a post-1991 82077
[   13.968861] ata_piix 0000:00:1f.1: version 2.11
[   13.968887] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   13.968897] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   13.968952] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.969110] scsi0 : ata_piix
[   13.969219] scsi1 : ata_piix
[   13.969373] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00012800 irq 14
[   13.969377] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00012808 irq 15
[   14.140947] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
[   14.140952] ata1.00: 78165360 sectors, multi 16: LBA 
[   14.141641] ata1.01: ATA-4: WDC WD136AA, 82.10A82, max UDMA/66
[   14.141644] ata1.01: 26564832 sectors, multi 16: LBA 
[   14.141652] ata1.01: limited to UDMA/33 due to 40-wire cable
[   14.156937] ata1.00: configured for UDMA/100
[   14.172645] ata1.01: configured for UDMA/33
[   14.336753] ata2.01: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
[   14.336759] ata2.01: 78165360 sectors, multi 16: LBA 
[   14.352620] ata2.01: configured for UDMA/100
[   14.352800] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-11CP 06.0 PQ: 0 ANSI: 5
[   14.353659] scsi 0:0:1:0: Direct-Access     ATA      WDC WD136AA      82.1 PQ: 0 ANSI: 5
[   14.354506] scsi 1:0:1:0: Direct-Access     ATA      WDC WD400EB-11CP 06.0 PQ: 0 ANSI: 5
[   14.357401] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 23 (level, low) -> IRQ 19
[   14.358048] tulip0:  MII transceiver #1 config 1000 status 7849 advertising 01e1.
[   14.364685] eth0: ADMtek Comet rev 17 at Port 0x3000, 00:30:05:62:F2:63, IRQ 19.
[   14.364907] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 17 (level, low) -> IRQ 20
[   14.364917] 3c59x: Donald Becker and others.
[   14.364929] 0000:02:05.0: 3Com PCI 3c905 Boomerang 100baseTx at 00013400.
[   14.411206] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   14.412049] sd 0:0:0:0: [sda] Write Protect is off
[   14.412055] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.412110] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.412231] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   14.412251] sd 0:0:0:0: [sda] Write Protect is off
[   14.412254] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.412282] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.412291]  sda: sda1 sda2 sda3 sda4
[   14.433968] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.434399] sd 0:0:1:0: [sdb] 26564832 512-byte hardware sectors (13601 MB)
[   14.434421] sd 0:0:1:0: [sdb] Write Protect is off
[   14.434424] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   14.434452] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.434577] sd 0:0:1:0: [sdb] 26564832 512-byte hardware sectors (13601 MB)
[   14.434596] sd 0:0:1:0: [sdb] Write Protect is off
[   14.434599] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   14.434625] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.434630]  sdb: sdb1 sdb2 < sdb5 >
[   14.460002] sd 0:0:1:0: [sdb] Attached SCSI disk
[   14.460431] sd 1:0:1:0: [sdc] 78165360 512-byte hardware sectors (40021 MB)
[   14.460455] sd 1:0:1:0: [sdc] Write Protect is off
[   14.460458] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   14.460486] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.460599] sd 1:0:1:0: [sdc] 78165360 512-byte hardware sectors (40021 MB)
[   14.460618] sd 1:0:1:0: [sdc] Write Protect is off
[   14.460622] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   14.460647] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.460652]  sdc: sdc1
[   14.477375] sd 1:0:1:0: [sdc] Attached SCSI disk
[   14.485874] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.486249] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   14.486628] sd 1:0:1:0: Attached scsi generic sg2 type 0
[   14.494962] usb 4-6: new high speed USB device using ehci_hcd and address 3
[   14.675163] usb 4-6: configuration #2 chosen from 1 choice
[   14.913866] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   15.090916] usb 1-1: configuration #1 chosen from 1 choice
[   15.094946] usbcore: registered new interface driver libusual
[   15.105066] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.105073] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.109740] Initializing USB Mass Storage driver...
[   15.109880] scsi2 : SCSI emulation for USB Mass Storage devices
[   15.109995] usb-storage: device found at 3
[   15.109998] usb-storage: waiting for device to settle before scanning
[   15.110038] usbcore: registered new interface driver usb-storage
[   15.110042] USB Mass Storage support registered.
[   15.140586] usbcore: registered new interface driver hiddev
[   15.155526] input: Logitech Logitech USB Optical Mouse as /class/input/input2
[   15.155895] input: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:1d.0-1
[   15.155919] usbcore: registered new interface driver usbhid
[   15.155924] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   15.313759] kjournald starting.  Commit interval 5 seconds
[   15.313784] EXT3-fs: mounted filesystem with ordered data mode.
[   20.096760] usb-storage: device scan complete
[   20.097753] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-110D 1.41 PQ: 0 ANSI: 0
[   20.098560] scsi 2:0:0:0: Attached scsi generic sg3 type 5
[   26.107479] eth1:  setting full-duplex.
[   27.568707] NET: Registered protocol family 10
[   27.568871] lo: Disabled Privacy Extensions
[   28.768840] Linux agpgart interface v0.102 (c) Dave Jones
[   28.820134] agpgart: Detected an Intel 830M Chipset.
[   28.820247] agpgart: Detected 8060K stolen memory.
[   28.839676] agpgart: AGP aperture is 128M @ 0xd8000000
[   28.910022] intel_rng: FWH not detected
[   28.930548] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.932961] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.964712] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   29.057628] iTCO_vendor_support: vendor-support=0
[   29.059218] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   29.059373] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0xf060)
[   29.059468] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   29.979442] input: PC Speaker as /class/input/input3
[   30.216934] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   30.216941] Uniform CD-ROM driver Revision: 3.20
[   30.217419] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   30.418749] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   30.418785] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   30.741240] intel8x0_measure_ac97_clock: measured 54805 usecs
[   30.741245] intel8x0: clocking to 48000
[   31.658125] lp: driver loaded but no devices found
[   32.365324] EXT3 FS on sda2, internal journal
[   33.173244] kjournald starting.  Commit interval 5 seconds
[   33.173455] EXT3 FS on sda3, internal journal
[   33.173463] EXT3-fs: mounted filesystem with ordered data mode.
[   36.283727] No dock devices found.
[   36.357534] input: Power Button (FF) as /class/input/input4
[   36.364521] ACPI: Power Button (FF) [PWRF]
[   36.402692] input: Power Button (CM) as /class/input/input5
[   36.409592] ACPI: Power Button (CM) [PWRB]
[   38.409570] eth1: no IPv6 routers present
[   39.207373] Failure registering capabilities with primary security module.
[   39.600858] ppdev: user-space parallel port driver
[   40.079428] audit(1219071862.350:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4890 profile="/usr/sbin/cupsd"
[   40.246567] apm: BIOS not found.
[   42.045270] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   42.148124] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   42.159878] NFSD: starting 90-second grace period
[   45.225360] [drm] Initialized drm 1.1.0 20060810
[   45.282710] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.286778] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  101.494604] UDF-fs: No VRS found
[  101.522554] ISO 9660 Extensions: Microsoft Joliet Level 3
[  101.901386] ISOFS: changing to secondary root
[  212.688020] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  212.688032] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  212.688037] Info fld=0x3fd
[  212.688039] sr 2:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  212.688046] end_request: I/O error, dev sr0, sector 4084
[  212.688095] ISOFS: unable to read i-node block

```

I hope someone can help with this...

Only reason I'm trying 98, is so I can try running a game...

Unless someone knows if I can run the game without a cd in WINE (the game is Theme Hospital), to which I've been having problems within VBox XP.

Thanks guys,

---

### Post by robelliott2125 on 2008-08-18
Apologies if this should be somewhere else, please feel free to move it.

---

### Post by Ryadt on 2008-08-18
Are you running the virtualbox of the repos?

---

### Post by robelliott2125 on 2008-08-18
> **Ryadt said:**
> Are you running the virtualbox of the repos?

I found the VBox within Add / Remove, so I would say yes, if that of course is the repos.

I'm unsure.  :/

I did have it all working ok, but i hadn't used Vbox for so long, and got the urge to play Theme Hosp when bored, but the probs with running Theme Hosp annoyed me (to which i couldn't find a way to solve it) and thought I'd try instead on 98 (since Compatability Mode failed me).

---

### Post by Ryadt on 2008-08-18
> **robelliott2125 said:**
> I found the VBox within Add / Remove, so I would say yes, if that of course is the repos.

I'm unsure.  :/

I did have it all working ok, but i hadn't used Vbox for so long, and got the urge to play Theme Hosp when bored, but the probs with running Theme Hosp annoyed me (to which i couldn't find a way to solve it) and thought I'd try instead on 98 (since Compatability Mode failed me).
Uninstall the virtualbox you are running and follow this guide to install the latest one.[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

---

### Post by fiddledd on 2008-08-18
Not used VirtualBox on Linux for ages, but I seem to remember a similar error that was solved by adding myself to the vboxusers  group.

---

### Post by robelliott2125 on 2008-08-18
> **Ryadt said:**
> Uninstall the virtualbox you are running and follow this guide to install the latest one.[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

Gah!

Thank you for the above, downloaded the deb, started to install (step two) and got the following (see attachment).

About to remove Innoteks, and try again...

---

### Post by robelliott2125 on 2008-08-18
> **fiddledd said:**
> Not used VirtualBox on Linux for ages, but I seem to remember a similar error that was solved by adding myself to the vboxusers  group.

Yeah, thats generally the first error I get when i've reinstalled etc (not reinstalled for ages, thanks to UF.org!).

I did check to see if i was in the users, and both root and myself are setup as the Vbox users.

Just finished removing Innoteks, so going to try again...

---

### Post by Ryadt on 2008-08-18
> **robelliott2125 said:**
> Gah!

Thank you for the above, downloaded the deb, started to install (step two) and got the following (see attachment).

About to remove Innoteks, and try again...

Try ```
sudo apt-get install libc6
```

---

### Post by robelliott2125 on 2008-08-18
Still getting the same error... 

I've just quickly gone into Synaptec and searched libc6, and reinstalling them as I type this.

Hopefully this may solve my problem with the deb.

---

### Post by robelliott2125 on 2008-08-18
> **Ryadt said:**
> Try ```
sudo apt-get install libc6
```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm not having any luck with this now...

Having reinstalled the libc6 packages which were in my synaptec, along with trying console, i'm getting nowhere.
The file still will not install...

Any other ideas?

---

### Post by Ryadt on 2008-08-18
> **robelliott2125 said:**
> ```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm not having any luck with this now...

Having reinstalled the libc6 packages which were in my synaptec, along with trying console, i'm getting nowhere.
The file still will not install...

Any other ideas?
Try updating```
sudo apt-get update
```
then re-run the installation.

---

### Post by robelliott2125 on 2008-08-18
> **Ryadt said:**
> Try updating```
sudo apt-get update
```
then re-run the installation.

Just tried that, nothing.

Going to restart once a file has finished unpacking.

See if that works...  Will let you know in a few minutes.

---

### Post by robelliott2125 on 2008-08-18
Just finished restarting, and no joys.  Still getting the same error.

Is there anything else I could try?

---

### Post by Master Chief on 2008-08-18
> **robelliott2125 said:**
> Just finished restarting, and no joys.  Still getting the same error.

Is there anything else I could try?

VirtualBox v1.6.2 installed from within the Synaptic Package Manager must work, and will take care of all necessary dependencies for you.

You can upgrade to version 1.6.4 after everything works, but don't forget to reboot after the installation.

p.s. Why do you start VirtualBox from the command line, instead of the Applications -> System Tools menu?

---

### Post by robelliott2125 on 2008-08-18
> **Master Chief said:**
> VirtualBox v1.6.2 installed from within the Synaptic Package Manager must work, and will take care of all necessary dependencies for you.

You can upgrade to version 1.6.4 after everything works, but don't forget to reboot after the installation.

p.s. Why do you start VirtualBox from the command line, instead of the Applications -> System Tools menu?

I don't normally, i'm new to linux / ubuntu, so as much as I use the GUI, I also like using the command line too.

When VBox kept failing with the error I showed on the first post, I was mearly following what it kept telling me to do.  So I've tried giving as much info as possible.

About to try your way M. Chief.  Thanks for the suggestion, and keep on with Halo dude!  :D

---

### Post by robelliott2125 on 2008-08-18
Ryadt, I've just realised why the deb install isn't working...

Its for Hardy, and I'm running Gutsy.

I'm going to quickly google to see if theres a deb for gutsy.

Master Chief, the way you recommended, is for Innotek's Virtualbox, which has reinstalled, but the same problem is coming up when trying to start the box up.

---

### Post by Master Chief on 2008-08-18
In that case this should work (for the Open Source Edition):

```
sudo apt-get update
sudo apt-get install virtualbox-ose virtualbox-ose-source
sudo apt-get install module-assistant
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo modprobe vboxdrv
sudo gedit /etc/modules
vboxdrv
sudo adduser [your username] vboxusers
```

At least that's what I found on one of my old harddisks ;)

---

### Post by robelliott2125 on 2008-08-18
> **Master Chief said:**
> In that case this should work (for the Open Source Edition):

```
sudo apt-get update
sudo apt-get install virtualbox-ose virtualbox-ose-source
sudo apt-get install module-assistant
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo modprobe vboxdrv
sudo gedit /etc/modules
vboxdrv
sudo adduser [your username] vboxusers
```

At least that's what I found on one of my old harddisks ;)

Hey bud,

All the steps were working fine, until I got to ```
sudo modprobe vboxdrv
```

When that was entered, i got back:

```
robert@robert-desktop:~$ sudo modprobe vboxdrv
FATAL: Module vboxdrv not found.

```

---

### Post by robelliott2125 on 2008-08-18
Anyone???

---

### Post by Ryadt on 2008-08-18
Sorry but is there any reason why you are not using Hardy?

---

### Post by robelliott2125 on 2008-08-18
At the minute, not really.

When it was originally released, I did have a few problems, with the likes of my hardware, then Firefox 3 wasn't compatible with some of my add-ons.

I've actually been considering upgrading, since i've given it enough time to be all sorted...  (Goes off to upgrade).

Will see you in a bit then dude.  :D

---

### Post by Ryadt on 2008-08-18
All the best...;)

---

### Post by Master Chief on 2008-08-18
You are using the 2.6.22-15-generic kernel and thus 
*virtualbox-ose-modules-generic* needs to be install too.  Do you have that installed?

Do not install the 2.6.24-21-generic kernel in hardy, or you will run into similar problems: 
[http://ubuntuforums.org/showthread.php?t=893830](http://ubuntuforums.org/showthread.php?t=893830)

---

### Post by robelliott2125 on 2008-08-19
> **Master Chief said:**
> You are using the 2.6.22-15-generic kernel and thus 
*virtualbox-ose-modules-generic* needs to be install too.  Do you have that installed?

Do not install the 2.6.24-21-generic kernel in hardy, or you will run into similar problems: 
[http://ubuntuforums.org/showthread.php?t=893830](http://ubuntuforums.org/showthread.php?t=893830)

Thanks MasterChief.

Having gone through so much hell on trying to upgrade, i've had to fully reinstall my OS.

I've now installed Hardy, but my problem has now gotten seemingly bigger.

I still had the .deb from last night on my desktop, so I've installed it, and reinstalled, but nothing.

I've had to reinstall from my Add / Remove, for it to show up in my Applications > System Tools menu, however i've not used it yet, since i'm trying to solve other problems.

Gah I hate reinstalling my OS!

---

