---
title: "how can i mount an ntfs external drive?"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by waynebruce on 2007-06-16
Hey there, I just need to know how to detect and mount my external ntfs drive.  I plugged it in and it's not being auto mounted and such.

---

### Post by ryanVickers on 2007-06-16
Have you looked in system > Preferences > Removable Drives and Media?

You can usually configure what you want to load automatically.

---

### Post by waynebruce on 2007-06-17
yeah, I tried that already (and again just in case), still nothing.  I would like to just manually mount it but a) i don't know the mount commands to type in terminal and b) I don't know the drive label (eg sbd1 or hda2 or whatever).

---

### Post by ryanVickers on 2007-06-17
ok, the command is sudo mount /dev/sda1

of course it's probably not sda1, but you know... Look in gparted with the drive plugged in to find what it's being called

---

### Post by waynebruce on 2007-06-17
hmmms, gparted doesn't seem to have anything on there but my internal drive.

---

### Post by waynebruce on 2007-06-17
when I run "sudo fdisk -l" I get this:



Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241135618+  83  Linux
/dev/sda2           30021       30394     3004155    5  Extended
/dev/sda5           30021       30394     3004123+  82  Linux swap / Solaris

That's just my internal drive (i don't know if that's obvious or not, sorry).  The external drive runs through usb 2.0 connections.  The usb's work for my ipod, psp, and everything pretty much except external harddrives.  The first day I installed Ubuntu I had external harddrive access, then i removed the drive without properly unmounting it.  I THEN took the drive to a friend's house with Windows 2000 and properly unmounted the drive but now I don't even get error messages when mounting, Ubuntu just seems to not be detecting it at all.  Helps please mates.

---

### Post by waynebruce on 2007-06-17
Hey can someone help please?!!!!  (I'm making one of those begging faces)

---

### Post by ryanVickers on 2007-06-17
Did you put the drive in the case yourself or was it pre-built?  Actually, regardless of this, it may not be seated in the "plug" in the case.  Open it up and see if it's plugged in good - be careful though!

---

### Post by fdrake on 2007-06-17
first need to be sure its listed as usb device,type:
lsusb 
do you see the name (company manufacture)of your ext. driver??

---

### Post by waynebruce on 2007-06-18
A) The drive was pre-built, a Maxtor 80 gb that works perfect on Windows just not on Ubuntu it seems.


```
christopher@christopher-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 [/CODE


So I believe it isn't being detected?  It powers up still and everything.  This is "dmesg" before plugging it in (the usb device i sonnected/disconnected was a playstation pocket):

[CODE][    0.000000] copy_e820_map() start: 000000003f7f0000 size: 0000000000010000 end: 000000003f800000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000480000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7c0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7c0000 - 000000003f7ce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7ce000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 260032) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   260032
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   260032
[    0.000000] On node 0 totalpages: 260032
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30417 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb5f0
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x02000502 MSFT 0x00000097) @ 0x3f7c0000
[    0.000000] ACPI: FADT (v001 A M I  OEMFACP  0x02000502 MSFT 0x00000097) @ 0x3f7c0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x02000502 MSFT 0x00000097) @ 0x3f7c0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x02000502 MSFT 0x00000097) @ 0x3f7ce040
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x02000502 MSFT 0x00000097) @ 0x3f7c47f0
[    0.000000] ACPI: DSDT (v001  A0005 A0005073 0x00000073 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:c0380000)
[    0.000000] Detected 3065.711 MHz processor.
[   19.267418] Built 1 zonelists.  Total pages: 258001
[   19.267422] Kernel command line: root=UUID=0c6e2500-8208-46f7-ab3b-e869ffa703b6 ro quiet splash
[   19.267576] mapped APIC to ffffd000 (fee00000)
[   19.267578] mapped IOAPIC to ffffc000 (fec00000)
[   19.267581] Enabling fast FPU save and restore... done.
[   19.267584] Enabling unmasked SIMD FPU exception support... done.
[   19.267592] Initializing CPU#0
[   19.267657] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   19.269762] Console: colour VGA+ 80x25
[   19.270120] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   19.270480] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.290431] Memory: 1019936k/1040128k available (1992k kernel code, 19396k reserved, 900k data, 328k init, 122624k highmem)
[   19.290441] virtual kernel memory layout:
[   19.290442]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   19.290443]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.290444]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   19.290445]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   19.290446]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   19.290447]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   19.290448]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   19.290453] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.367658] Calibrating delay using timer specific routine.. 6136.82 BogoMIPS (lpj=12273651)
[   19.367700] Security Framework v1.0.0 initialized
[   19.367706] SELinux:  Disabled at boot.
[   19.367722] Mount-cache hash table entries: 512
[   19.367857] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000451d 00000000 00000000
[   19.367866] monitor/mwait feature present.
[   19.367867] using mwait in idle threads.
[   19.367874] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   19.367877] CPU: L2 cache: 1024K
[   19.367879] CPU: Hyper-Threading is disabled
[   19.367881] CPU: After all inits, caps: bfebfbff 00100000 00000000 00003180 0000451d 00000000 00000000
[   19.367893] Compat vDSO mapped to ffffe000.
[   19.367897] Remapping vsyscall page to ffffe000
[   19.367912] Checking 'hlt' instruction... OK.
[   19.383753] SMP alternatives: switching to UP code
[   19.383955] Freeing SMP alternatives: 11k freed
[   19.384150] Early unpacking initramfs... done
[   19.653306] ACPI: Core revision 20060707
[   19.653459] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   19.666939] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 01
[   19.666977] Total of 1 processors activated (6136.82 BogoMIPS).
[   19.667128] ENABLING IO-APIC IRQs
[   19.667307] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.811677] Brought up 1 CPUs
[   19.811900] Booting paravirtualized kernel on bare hardware
[   19.811970] Time: 20:27:13  Date: 05/17/107
[   19.811993] NET: Registered protocol family 16
[   19.812069] EISA bus registered
[   19.812074] ACPI: bus type pci registered
[   19.812340] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   19.812343] PCI: Using configuration type 1
[   19.812344] Setting up standard PCI resources
[   19.825344] ACPI: Interpreter enabled
[   19.825348] ACPI: Using IOAPIC for interrupt routing
[   19.826413] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.826422] PCI: Probing PCI hardware (bus 00)
[   19.826729] Boot video device is 0000:00:02.0
[   19.827176] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   19.827180] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   19.827696] PCI: Transparent bridge - 0000:00:1e.0
[   19.827736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.830197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   19.836099] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.836354] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.836609] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   19.836866] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   19.837120] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   19.837373] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   19.837623] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   19.837878] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   19.837972] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.837982] pnp: PnP ACPI init
[   19.842105] pnp: PnP ACPI: found 16 devices
[   19.842110] PnPBIOS: Disabled by ACPI PNP
[   19.842157] PCI: Using ACPI for IRQ routing
[   19.842160] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.854167] NET: Registered protocol family 8
[   19.854169] NET: Registered protocol family 20
[   19.855155] pnp: 00:07: ioport range 0x680-0x6ff has been reserved
[   19.855455] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   19.855460] PCI: Bridge: 0000:00:1c.0
[   19.855463]   IO window: d000-dfff
[   19.855468]   MEM window: disabled.
[   19.855472]   PREFETCH window: disabled.
[   19.855479] PCI: Bridge: 0000:00:1e.0
[   19.855482]   IO window: e000-efff
[   19.855488]   MEM window: cff00000-cfffffff
[   19.855492]   PREFETCH window: disabled.
[   19.855519] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.855526] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.855538] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.855558] NET: Registered protocol family 2
[   19.891693] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.891830] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.892421] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.892753] TCP: Hash tables configured (established 131072 bind 65536)
[   19.892756] TCP reno registered
[   19.903778] checking if image is initramfs... it is
[   20.423984] Freeing initrd memory: 6766k freed
[   20.424419] audit: initializing netlink socket (disabled)
[   20.424432] audit(1182112033.228:1): initialized
[   20.424500] highmem bounce pool size: 64 pages
[   20.424550] VFS: Disk quotas dquot_6.5.1
[   20.424567] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.424613] io scheduler noop registered
[   20.424616] io scheduler anticipatory registered
[   20.424618] io scheduler deadline registered
[   20.424627] io scheduler cfq registered (default)
[   20.424833] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.424879] assign_interrupt_mode Found MSI capability
[   20.424882] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.424915] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.425076] isapnp: Scanning for PnP cards...
[   20.777025] isapnp: No Plug & Play device found
[   20.801357] Real Time Clock Driver v1.12ac
[   20.801410] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.802052] mice: PS/2 mouse device common for all mice
[   20.802625] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.802860] input: Macintosh mouse button emulation as /class/input/input0
[   20.802894] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.802898] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.803090] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   20.803094] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   20.806248] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.806254] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.806389] EISA: Probing bus 0 at eisa.0
[   20.806418] EISA: Detected 0 cards.
[   20.836496] TCP cubic registered
[   20.836503] NET: Registered protocol family 1
[   20.836526] Using IPI No-Shortcut mode
[   20.836586] ACPI: (supports S0 S1 S3 S4 S5)
[   20.836630]   Magic number: 11:325:498
[   20.836953] Freeing unused kernel memory: 328k freed
[   20.839579] Time: tsc clocksource has been installed.
[   20.855137] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.057545] Capability LSM initialized
[   22.094389] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.094399] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.513711] usbcore: registered new interface driver usbfs
[   22.513733] usbcore: registered new interface driver hub
[   22.513754] usbcore: registered new device driver usb
[   22.514563] USB Universal Host Controller Interface driver v3.0
[   22.514607] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   22.514618] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.514622] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.514751] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.514778] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000c400
[   22.514878] usb usb1: configuration #1 chosen from 1 choice
[   22.514904] hub 1-0:1.0: USB hub found
[   22.514912] hub 1-0:1.0: 2 ports detected
[   22.578919] ieee1394: Initialized config rom entry `ip1394'
[   22.588433] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.619412] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   22.619424] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.619428] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.619453] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.619489] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000c480
[   22.619574] usb usb2: configuration #1 chosen from 1 choice
[   22.619600] hub 2-0:1.0: USB hub found
[   22.619606] hub 2-0:1.0: 2 ports detected
[   22.727389] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   22.727401] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.727405] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.727428] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.727456] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000c800
[   22.727554] usb usb3: configuration #1 chosen from 1 choice
[   22.727583] hub 3-0:1.0: USB hub found
[   22.727590] hub 3-0:1.0: 2 ports detected
[   22.835330] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   22.835343] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   22.835347] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.835370] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.835400] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c880
[   22.835493] usb usb4: configuration #1 chosen from 1 choice
[   22.835522] hub 4-0:1.0: USB hub found
[   22.835529] hub 4-0:1.0: 2 ports detected
[   22.945042] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[   22.945061] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.945065] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.945098] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   22.945136] ehci_hcd 0000:00:1d.7: debug port 1
[   22.945143] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.945150] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xcfe37c00
[   22.949038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.949114] usb usb5: configuration #1 chosen from 1 choice
[   22.949141] hub 5-0:1.0: USB hub found
[   22.949149] hub 5-0:1.0: 8 ports detected
[   22.967232] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   23.061130] SCSI subsystem initialized
[   23.066469] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.119314] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[cffff800-cfffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   23.125143] libata version 2.20 loaded.
[   23.126410] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   23.126413] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[   23.132364] 8139too Fast Ethernet driver 0.9.28
[   23.132410] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[   23.132772] eth0: RealTek RTL8139 at 0xf8848400, 00:11:d8:99:e9:cc, IRQ 21
[   23.132775] eth0:  Identified 8139 chip type 'RTL-8101'
[   23.134517] ata_piix 0000:00:1f.1: version 2.10ac1
[   23.134530] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   23.134545] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.135200] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   23.135232] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   23.135251] scsi0 : ata_piix
[   23.619370] ata1.00: ATAPI, max UDMA/66
[   23.619374] ata1.01: ATAPI, max UDMA/33
[   23.619380] ata1.00: limited to UDMA/33 due to 40-wire cable
[   23.787345] ata1.00: configured for UDMA/33
[   23.823086] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   23.955323] ata1.01: configured for UDMA/33
[   23.955335] scsi1 : ata_piix
[   23.955524] ata2: port disabled. ignoring.
[   23.956306] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1633S BPSA PQ: 0 ANSI: 5
[   23.956881] scsi 0:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B402 PQ: 0 ANSI: 5
[   23.958183] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   23.958208] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   23.958225] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.958261] ata3: SATA max UDMA/133 cmd 0x0001c080 ctl 0x0001c002 bmdma 0x0001b800 irq 18
[   23.958288] ata4: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001b882 bmdma 0x0001b808 irq 18
[   23.958297] scsi2 : ata_piix
[   24.002430] usb 2-1: configuration #1 chosen from 1 choice
[   24.161656] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
[   24.161664] ata3.00: ATA-7: ST3250824AS, 3.ADH, max UDMA/133
[   24.161667] ata3.00: 488281250 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   24.228278] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
[   24.228283] ata3.00: configured for UDMA/133
[   24.228294] scsi3 : ata_piix
[   24.247032] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   24.397148] ATA: abnormal status 0x7F on port 0x0001bc07
[   24.397278] scsi 2:0:0:0: Direct-Access     ATA      ST3250824AS      3.AD PQ: 0 ANSI: 5
[   24.411147] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000014eb83]
[   24.428106] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   24.428111] Uniform CD-ROM driver Revision: 3.20
[   24.428244] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   24.432332] usb 4-1: configuration #1 chosen from 1 choice
[   24.432816] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   24.432954] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   24.435400] usbcore: registered new interface driver hiddev
[   24.437066] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   24.437085] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   24.437104] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[   24.442189] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[   24.442204] sda: Write Protect is off
[   24.442207] sda: Mode Sense: 00 3a 00 00
[   24.442225] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.442276] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[   24.442287] sda: Write Protect is off
[   24.442289] sda: Mode Sense: 00 3a 00 00
[   24.442306] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.442309]  sda:<6>input: Logitech Optical USB Mouse as /class/input/input2
[   24.448459] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1
[   24.448476] usbcore: registered new interface driver usbhid
[   24.448479] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   24.455561] usbcore: registered new interface driver libusual
[   24.458918] Initializing USB Mass Storage driver...
[   24.462752]  sda1 sda2 <<6>scsi4 : SCSI emulation for USB Mass Storage devices
[   24.463058] usbcore: registered new interface driver usb-storage
[   24.463062] USB Mass Storage support registered.
[   24.463304] usb-storage: device found at 2
[   24.463307] usb-storage: waiting for device to settle before scanning
[   24.481613]  sda5 >
[   24.482021] sd 2:0:0:0: Attached scsi disk sda
[   24.602548] Attempting manual resume
[   24.602553] swsusp: Resume From Partition 8:5
[   24.602554] PM: Checking swsusp image.
[   24.602751] PM: Resume from disk failed.
[   24.634446] kjournald starting.  Commit interval 5 seconds
[   24.634456] EXT3-fs: mounted filesystem with ordered data mode.
[   29.463727] usb-storage: device scan complete
[   29.466719] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   29.469722] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   29.472719] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   29.475719] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   29.518738] sd 4:0:0:0: Attached scsi removable disk sdb
[   29.518779] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   29.562352] sd 4:0:0:1: Attached scsi removable disk sdc
[   29.562401] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   29.605748] sd 4:0:0:2: Attached scsi removable disk sdd
[   29.605795] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   29.648757] sd 4:0:0:3: Attached scsi removable disk sde
[   29.648805] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   31.872096] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   33.400371] NET: Registered protocol family 17
[   33.580216] iTCO_vendor_support: vendor-support=0
[   33.581236] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   33.581327] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   33.581369] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.602217] intel_rng: FWH not detected
[   33.855519] Linux agpgart interface v0.102 (c) Dave Jones
[   33.867160] agpgart: Detected an Intel 915G Chipset.
[   33.867357] agpgart: Detected 7932K stolen memory.
[   33.883680] agpgart: AGP aperture is 256M @ 0xd0000000
[   34.151198] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.153884] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.491205] input: PC Speaker as /class/input/input3
[   34.571843] parport: PnPBIOS parport detected.
[   34.571901] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   34.764866] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.764883] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   82.612158] fuse init (API version 7.8)
[   82.633029] lp0: using parport0 (interrupt-driven).
[   82.679568] Adding 3004112k swap on /dev/disk/by-uuid/dc7a9ea8-6d9a-49e7-a2eb-09d3dc4480a6.  Priority:-1 extents:1 across:3004112k
[  323.334439] EXT3 FS on sda1, internal journal
[  323.683361] NET: Registered protocol family 10
[  323.683448] lo: Disabled Privacy Extensions
[  328.905712] No dock devices found.
[  328.963159] ibm_acpi: ec object not found
[  328.996963] Using specific hotkey driver
[  329.125091] input: Power Button (FF) as /class/input/input4
[  329.129293] ACPI: Power Button (FF) [PWRF]
[  329.159784] input: Power Button (CM) as /class/input/input5
[  329.163930] ACPI: Power Button (CM) [PWRB]
[  329.259987] pcc_acpi: loading...
[  333.750041] ppdev: user-space parallel port driver
[  333.868891] [drm] Initialized drm 1.1.0 20060810
[  333.883108] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  333.883705] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  337.365987] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  337.365992] apm: overridden by ACPI.
[  338.057339] Bluetooth: Core ver 2.11
[  338.108072] NET: Registered protocol family 31
[  338.108077] Bluetooth: HCI device and connection manager initialized
[  338.108081] Bluetooth: HCI socket layer initialized
[  338.160073] Bluetooth: L2CAP ver 2.8
[  338.160078] Bluetooth: L2CAP socket layer initialized
[  338.340045] Bluetooth: RFCOMM socket layer initialized
[  338.340285] Bluetooth: RFCOMM TTY layer initialized
[  338.340289] Bluetooth: RFCOMM ver 1.8
[  349.685558] eth0: no IPv6 routers present
[  650.519534] usb 5-6: new high speed USB device using ehci_hcd and address 4
[  650.631519] usb 5-6: device descriptor read/64, error -71
[  650.847489] usb 5-6: device descriptor read/64, error -71
[  651.063459] usb 5-6: new high speed USB device using ehci_hcd and address 5
[  651.175446] usb 5-6: device descriptor read/64, error -71
[  651.391412] usb 5-6: device descriptor read/64, error -71
[  651.607382] usb 5-6: new high speed USB device using ehci_hcd and address 6
[  652.015322] usb 5-6: device not accepting address 6, error -71
[  652.127311] usb 5-6: new high speed USB device using ehci_hcd and address 7
[  652.535250] usb 5-6: device not accepting address 7, error -71
[30746.870872] usb 5-5: new high speed USB device using ehci_hcd and address 8
[30747.003657] usb 5-5: configuration #1 chosen from 1 choice
[30747.003774] scsi5 : SCSI emulation for USB Mass Storage devices
[30747.003827] usb-storage: device found at 8
[30747.003829] usb-storage: waiting for device to settle before scanning
[30752.006295] usb-storage: device scan complete
[30752.006794] scsi 5:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[30752.009018] SCSI device sdf: 1947648 512-byte hdwr sectors (997 MB)
[30752.009517] sdf: Write Protect is off
[30752.009521] sdf: Mode Sense: 00 6a 20 00
[30752.009523] sdf: assuming drive cache: write through
[30752.011643] SCSI device sdf: 1947648 512-byte hdwr sectors (997 MB)
[30752.012142] sdf: Write Protect is off
[30752.012145] sdf: Mode Sense: 00 6a 20 00
[30752.012147] sdf: assuming drive cache: write through
[30752.012150]  sdf: sdf1
[30752.013464] sd 5:0:0:0: Attached scsi removable disk sdf
[30752.013513] sd 5:0:0:0: Attached scsi generic sg7 type 0
[30972.159412] usb 5-5: USB disconnect, address 8
[31003.698997] usb 5-5: new high speed USB device using ehci_hcd and address 9
[31003.831875] usb 5-5: configuration #1 chosen from 1 choice
[31003.831991] scsi6 : SCSI emulation for USB Mass Storage devices
[31003.832043] usb-storage: device found at 9
[31003.832045] usb-storage: waiting for device to settle before scanning
[31008.830511] usb-storage: device scan complete
[31008.831011] scsi 6:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[31008.833234] SCSI device sdf: 1947648 512-byte hdwr sectors (997 MB)
[31008.833733] sdf: Write Protect is off
[31008.833737] sdf: Mode Sense: 00 6a 20 00
[31008.833739] sdf: assuming drive cache: write through
[31008.838734] SCSI device sdf: 1947648 512-byte hdwr sectors (997 MB)
[31008.839232] sdf: Write Protect is off
[31008.839236] sdf: Mode Sense: 00 6a 20 00
[31008.839238] sdf: assuming drive cache: write through
[31008.839241]  sdf: sdf1
[31008.840555] sd 6:0:0:0: Attached scsi removable disk sdf
[31008.840600] sd 6:0:0:0: Attached scsi generic sg7 type 0
[31520.794785] usb 5-5: USB disconnect, address 9 
```

---

### Post by waynebruce on 2007-06-18
...and this is after I plug it in:
 
```
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x02000502 MSFT 0x00000097) @ 0x3f7ce040
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x02000502 MSFT 0x00000097) @ 0x3f7c47f0
[    0.000000] ACPI: DSDT (v001  A0005 A0005073 0x00000073 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:c0380000)
[    0.000000] Detected 3065.711 MHz processor.
[   19.267418] Built 1 zonelists.  Total pages: 258001
[   19.267422] Kernel command line: root=UUID=0c6e2500-8208-46f7-ab3b-e869ffa703b6 ro quiet splash
[   19.267576] mapped APIC to ffffd000 (fee00000)
[   19.267578] mapped IOAPIC to ffffc000 (fec00000)
[   19.267581] Enabling fast FPU save and restore... done.
[   19.267584] Enabling unmasked SIMD FPU exception support... done.
[   19.267592] Initializing CPU#0
[   19.267657] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   19.269762] Console: colour VGA+ 80x25
[   19.270120] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   19.270480] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.290431] Memory: 1019936k/1040128k available (1992k kernel code, 19396k reserved, 900k data, 328k init, 122624k highmem)
[   19.290441] virtual kernel memory layout:
[   19.290442]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   19.290443]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.290444]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   19.290445]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   19.290446]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   19.290447]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   19.290448]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   19.290453] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.367658] Calibrating delay using timer specific routine.. 6136.82 BogoMIPS (lpj=12273651)
[   19.367700] Security Framework v1.0.0 initialized
[   19.367706] SELinux:  Disabled at boot.
[   19.367722] Mount-cache hash table entries: 512
[   19.367857] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000451d 00000000 00000000
[   19.367866] monitor/mwait feature present.
[   19.367867] using mwait in idle threads.
[   19.367874] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   19.367877] CPU: L2 cache: 1024K
[   19.367879] CPU: Hyper-Threading is disabled
[   19.367881] CPU: After all inits, caps: bfebfbff 00100000 00000000 00003180 0000451d 00000000 00000000
[   19.367893] Compat vDSO mapped to ffffe000.
[   19.367897] Remapping vsyscall page to ffffe000
[   19.367912] Checking 'hlt' instruction... OK.
[   19.383753] SMP alternatives: switching to UP code
[   19.383955] Freeing SMP alternatives: 11k freed
[   19.384150] Early unpacking initramfs... done
[   19.653306] ACPI: Core revision 20060707
[   19.653459] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   19.666939] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 01
[   19.666977] Total of 1 processors activated (6136.82 BogoMIPS).
[   19.667128] ENABLING IO-APIC IRQs
[   19.667307] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.811677] Brought up 1 CPUs
[   19.811900] Booting paravirtualized kernel on bare hardware
[   19.811970] Time: 20:27:13  Date: 05/17/107
[   19.811993] NET: Registered protocol family 16
[   19.812069] EISA bus registered
[   19.812074] ACPI: bus type pci registered
[   19.812340] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   19.812343] PCI: Using configuration type 1
[   19.812344] Setting up standard PCI resources
[   19.825344] ACPI: Interpreter enabled
[   19.825348] ACPI: Using IOAPIC for interrupt routing
[   19.826413] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.826422] PCI: Probing PCI hardware (bus 00)
[   19.826729] Boot video device is 0000:00:02.0
[   19.827176] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   19.827180] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   19.827696] PCI: Transparent bridge - 0000:00:1e.0
[   19.827736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.830197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   19.836099] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.836354] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   19.836609] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   19.836866] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   19.837120] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   19.837373] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   19.837623] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   19.837878] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   19.837972] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.837982] pnp: PnP ACPI init
[   19.842105] pnp: PnP ACPI: found 16 devices
[   19.842110] PnPBIOS: Disabled by ACPI PNP
[   19.842157] PCI: Using ACPI for IRQ routing
[   19.842160] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.854167] NET: Registered protocol family 8
[   19.854169] NET: Registered protocol family 20
[   19.855155] pnp: 00:07: ioport range 0x680-0x6ff has been reserved
[   19.855455] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   19.855460] PCI: Bridge: 0000:00:1c.0
[   19.855463]   IO window: d000-dfff
[   19.855468]   MEM window: disabled.
[   19.855472]   PREFETCH window: disabled.
[   19.855479] PCI: Bridge: 0000:00:1e.0
[   19.855482]   IO window: e000-efff
[   19.855488]   MEM window: cff00000-cfffffff
[   19.855492]   PREFETCH window: disabled.
[   19.855519] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.855526] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.855538] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.855558] NET: Registered protocol family 2
[   19.891693] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.891830] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.892421] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.892753] TCP: Hash tables configured (established 131072 bind 65536)
[   19.892756] TCP reno registered
[   19.903778] checking if image is initramfs... it is
[   20.423984] Freeing initrd memory: 6766k freed
[   20.424419] audit: initializing netlink socket (disabled)
[   20.424432] audit(1182112033.228:1): initialized
[   20.424500] highmem bounce pool size: 64 pages
[   20.424550] VFS: Disk quotas dquot_6.5.1
[   20.424567] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.424613] io scheduler noop registered
[   20.424616] io scheduler anticipatory registered
[   20.424618] io scheduler deadline registered
[   20.424627] io scheduler cfq registered (default)
[   20.424833] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.424879] assign_interrupt_mode Found MSI capability
[   20.424882] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.424915] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.425076] isapnp: Scanning for PnP cards...
[   20.777025] isapnp: No Plug & Play device found
[   20.801357] Real Time Clock Driver v1.12ac
[   20.801410] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.802052] mice: PS/2 mouse device common for all mice
[   20.802625] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.802860] input: Macintosh mouse button emulation as /class/input/input0
[   20.802894] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.802898] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.803090] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   20.803094] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   20.806248] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.806254] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.806389] EISA: Probing bus 0 at eisa.0
[   20.806418] EISA: Detected 0 cards.
[   20.836496] TCP cubic registered
[   20.836503] NET: Registered protocol family 1
[   20.836526] Using IPI No-Shortcut mode
[   20.836586] ACPI: (supports S0 S1 S3 S4 S5)
[   20.836630]   Magic number: 11:325:498
[   20.836953] Freeing unused kernel memory: 328k freed
[   20.839579] Time: tsc clocksource has been installed.
[   20.855137] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.057545] Capability LSM initialized
[   22.094389] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.094399] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   22.513711] usbcore: registered new interface driver usbfs
[   22.513733] usbcore: registered new interface driver hub
[   22.513754] usbcore: registered new device driver usb
[   22.514563] USB Universal Host Controller Interface driver v3.0
[   22.514607] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   22.514618] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.514622] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.514751] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.514778] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000c400
[   22.514878] usb usb1: configuration #1 chosen from 1 choice
[   22.514904] hub 1-0:1.0: USB hub found
[   22.514912] hub 1-0:1.0: 2 ports detected
[   22.578919] ieee1394: Initialized config rom entry `ip1394'
[   22.588433] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.619412] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   22.619424] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.619428] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.619453] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.619489] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000c480
[   22.619574] usb usb2: configuration #1 chosen from 1 choice
[   22.619600] hub 2-0:1.0: USB hub found
[   22.619606] hub 2-0:1.0: 2 ports detected
[   22.727389] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   22.727401] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.727405] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.727428] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.727456] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000c800
[   22.727554] usb usb3: configuration #1 chosen from 1 choice
[   22.727583] hub 3-0:1.0: USB hub found
[   22.727590] hub 3-0:1.0: 2 ports detected
[   22.835330] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   22.835343] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   22.835347] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.835370] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.835400] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c880
[   22.835493] usb usb4: configuration #1 chosen from 1 choice
[   22.835522] hub 4-0:1.0: USB hub found
[   22.835529] hub 4-0:1.0: 2 ports detected
[   22.945042] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[   22.945061] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.945065] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.945098] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   22.945136] ehci_hcd 0000:00:1d.7: debug port 1
[   22.945143] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.945150] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xcfe37c00
[   22.949038] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.949114] usb usb5: configuration #1 chosen from 1 choice
[   22.949141] hub 5-0:1.0: USB hub found
[   22.949149] hub 5-0:1.0: 8 ports detected
[   22.967232] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   23.061130] SCSI subsystem initialized
[   23.066469] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.119314] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[cffff800-cfffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   23.125143] libata version 2.20 loaded.
[   23.126410] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   23.126413] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[   23.132364] 8139too Fast Ethernet driver 0.9.28
[   23.132410] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[   23.132772] eth0: RealTek RTL8139 at 0xf8848400, 00:11:d8:99:e9:cc, IRQ 21
[   23.132775] eth0:  Identified 8139 chip type 'RTL-8101'
[   23.134517] ata_piix 0000:00:1f.1: version 2.10ac1
[   23.134530] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   23.134545] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.135200] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   23.135232] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   23.135251] scsi0 : ata_piix
[   23.619370] ata1.00: ATAPI, max UDMA/66
[   23.619374] ata1.01: ATAPI, max UDMA/33
[   23.619380] ata1.00: limited to UDMA/33 due to 40-wire cable
[   23.787345] ata1.00: configured for UDMA/33
[   23.823086] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   23.955323] ata1.01: configured for UDMA/33
[   23.955335] scsi1 : ata_piix
[   23.955524] ata2: port disabled. ignoring.
[   23.956306] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1633S BPSA PQ: 0 ANSI: 5
[   23.956881] scsi 0:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B402 PQ: 0 ANSI: 5
[   23.958183] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   23.958208] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   23.958225] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.958261] ata3: SATA max UDMA/133 cmd 0x0001c080 ctl 0x0001c002 bmdma 0x0001b800 irq 18
[   23.958288] ata4: SATA max UDMA/133 cmd 0x0001bc00 ctl 0x0001b882 bmdma 0x0001b808 irq 18
[   23.958297] scsi2 : ata_piix
[   24.002430] usb 2-1: configuration #1 chosen from 1 choice
[   24.161656] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
[   24.161664] ata3.00: ATA-7: ST3250824AS, 3.ADH, max UDMA/133
[   24.161667] ata3.00: 488281250 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   24.228278] ata3.00: ata_hpa_resize 1: sectors = 488281250, hpa_sectors = 488281250
[   24.228283] ata3.00: configured for UDMA/133
[   24.228294] scsi3 : ata_piix
[   24.247032] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   24.397148] ATA: abnormal status 0x7F on port 0x0001bc07
[   24.397278] scsi 2:0:0:0: Direct-Access     ATA      ST3250824AS      3.AD PQ: 0 ANSI: 5
[   24.411147] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000014eb83]
[   24.428106] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   24.428111] Uniform CD-ROM driver Revision: 3.20
[   24.428244] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   24.432332] usb 4-1: configuration #1 chosen from 1 choice
[   24.432816] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   24.432954] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   24.435400] usbcore: registered new interface driver hiddev
[   24.437066] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   24.437085] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   24.437104] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[   24.442189] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[   24.442204] sda: Write Protect is off
[   24.442207] sda: Mode Sense: 00 3a 00 00
[   24.442225] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.442276] SCSI device sda: 488281250 512-byte hdwr sectors (250000 MB)
[   24.442287] sda: Write Protect is off
[   24.442289] sda: Mode Sense: 00 3a 00 00
[   24.442306] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.442309]  sda:<6>input: Logitech Optical USB Mouse as /class/input/input2
[   24.448459] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1
[   24.448476] usbcore: registered new interface driver usbhid
[   24.448479] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   24.455561] usbcore: registered new interface driver libusual
[   24.458918] Initializing USB Mass Storage driver...
[   24.462752]  sda1 sda2 <<6>scsi4 : SCSI emulation for USB Mass Storage devices
[   24.463058] usbcore: registered new interface driver usb-storage
[   24.463062] USB Mass Storage support registered.
[   24.463304] usb-storage: device found at 2
[   24.463307] usb-storage: waiting for device to settle before scanning
[   24.481613]  sda5 >
[   24.482021] sd 2:0:0:0: Attached scsi disk sda
[   24.602548] Attempting manual resume
[   24.602553] swsusp: Resume From Partition 8:5
[   24.602554] PM: Checking swsusp image.
[   24.602751] PM: Resume from disk failed.
[   24.634446] kjournald starting.  Commit interval 5 seconds
[   24.634456] EXT3-fs: mounted filesystem with ordered data mode.
[   29.463727] usb-storage: device scan complete
[   29.466719] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   29.469722] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   29.472719] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   29.475719] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   29.518738] sd 4:0:0:0: Attached scsi removable disk sdb
[   29.518779] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   29.562352] sd 4:0:0:1: Attached scsi removable disk sdc
[   29.562401] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   29.605748] sd 4:0:0:2: Attached scsi removable disk sdd
[   29.605795] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   29.648757] sd 4:0:0:3: Attached scsi removable disk sde
[   29.648805] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   31.872096] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   33.400371] NET: Registered protocol family 17
[   33.580216] iTCO_vendor_support: vendor-support=0
[   33.581236] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   33.581327] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   33.581369] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.602217] intel_rng: FWH not detected
[   33.855519] Linux agpgart interface v0.102 (c) Dave Jones
[   33.867160] agpgart: Detected an Intel 915G Chipset.
[   33.867357] agpgart: Detected 7932K stolen memory.
[   33.883680] agpgart: AGP aperture is 256M @ 0xd0000000
[   34.151198] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.153884] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.491205] input: PC Speaker as /class/input/input3
[   34.571843] parport: PnPBIOS parport detected.
[   34.571901] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   34.764866] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.764883] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   82.612158] fuse init (API version 7.8)
[   82.633029] lp0: using parport0 (interrupt-driven).
[   82.679568] Adding 3004112k swap on /dev/disk/by-uuid/dc7a9ea8-6d9a-49e7-a2eb-09d3dc4480a6.  Priority:-1 extents:1 across:3004112k
[  323.334439] EXT3 FS on sda1, internal journal
[  323.683361] NET: Registered protocol family 10
[  323.683448] lo: Disabled Privacy Extensions
[  328.905712] No dock devices found.
[  328.963159] ibm_acpi: ec object not found
[  328.996963] Using specific hotkey driver
[  329.125091] input: Power Button (FF) as /class/input/input4
[  329.129293] ACPI: Power Button (FF) [PWRF]
[  329.159784] input: Power Button (CM) as /class/input/input5
[  329.163930] ACPI: Power Button (CM) [PWRB]
[  329.259987] pcc_acpi: loading...
[  333.750041] ppdev: user-space parallel port driver
[  333.868891] [drm] Initialized drm 1.1.0 20060810
[  333.883108] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  333.883705] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  337.365987] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  337.365992] apm: overridden by ACPI.
[  338.057339] Bluetooth: Core ver 2.11
[  338.108072] NET: Registered protocol family 31
[  338.108077] Bluetooth: HCI device and connection manager initialized
[  338.108081] Bluetooth: HCI socket layer initialized
[  338.160073] Bluetooth: L2CAP ver 2.8
[  338.160078] Bluetooth: L2CAP socket layer initialized
[  338.340045] Bluetooth: RFCOMM socket layer initialized
[  338.340285] Bluetooth: RFCOMM TTY layer initialized
[  338.340289] Bluetooth: RFCOMM ver 1.8
[  349.685558] eth0: no IPv6 routers present
[  650.519534] usb 5-6: new high speed USB device using ehci_hcd and address 4
[  650.631519] usb 5-6: device descriptor read/64, error -71
[  650.847489] usb 5-6: device descriptor read/64, error -71
[  651.063459] usb 5-6: new high speed USB device using ehci_hcd and address 5
[  651.175446] usb 5-6: device descriptor read/64, error -71
[  651.391412] usb 5-6: device descriptor read/64, error -71
[  651.607382] usb 5-6: new high speed USB device using ehci_hcd and address 6
[  652.015322] usb 5-6: device not accepting address 6, error -71
[  652.127311] usb 5-6: new high speed USB device using ehci_hcd and address 7
[  652.535250] usb 5-6: device not accepting address 7, error -71
[30746.870872] usb 5-5: new high speed USB device using ehci_hcd and address 8
[30747.003657] usb 5-5: configuration #1 chosen from 1 choice
[30747.003774] scsi5 : SCSI emulation for USB Mass Storage devices
[30747.003827] usb-storage: device found at 8
[30747.003829] usb-storage: waiting for device to settle before scanning
[30752.006295] usb-storage: device scan complete
[30752.006794] scsi 5:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[30752.009018] SCSI device sdf: 1947648 512-byte hdwr sectors (997 MB)
[30752.009517] sdf: Write Protect is off
[30752.009521] sdf: Mode Sense: 00 6a 20 00
[30752.009523] sdf: assuming drive cache: write through
[30752.011643] SCSI device sdf: 1947648 512-byte hdwr sectors (997 MB)
[30752.012142] sdf: Write Protect is off
[30752.012145] sdf: Mode Sense: 00 6a 20 00
[30752.012147] sdf: assuming drive cache: write through
[30752.012150]  sdf: sdf1
[30752.013464] sd 5:0:0:0: Attached scsi removable disk sdf
[30752.013513] sd 5:0:0:0: Attached scsi generic sg7 type 0
[30972.159412] usb 5-5: USB disconnect, address 8
[31003.698997] usb 5-5: new high speed USB device using ehci_hcd and address 9
[31003.831875] usb 5-5: configuration #1 chosen from 1 choice
[31003.831991] scsi6 : SCSI emulation for USB Mass Storage devices
[31003.832043] usb-storage: device found at 9
[31003.832045] usb-storage: waiting for device to settle before scanning
[31008.830511] usb-storage: device scan complete
[31008.831011] scsi 6:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[31008.833234] SCSI device sdf: 1947648 512-byte hdwr sectors (997 MB)
[31008.833733] sdf: Write Protect is off
[31008.833737] sdf: Mode Sense: 00 6a 20 00
[31008.833739] sdf: assuming drive cache: write through
[31008.838734] SCSI device sdf: 1947648 512-byte hdwr sectors (997 MB)
[31008.839232] sdf: Write Protect is off
[31008.839236] sdf: Mode Sense: 00 6a 20 00
[31008.839238] sdf: assuming drive cache: write through
[31008.839241]  sdf: sdf1
[31008.840555] sd 6:0:0:0: Attached scsi removable disk sdf
[31008.840600] sd 6:0:0:0: Attached scsi generic sg7 type 0
[31520.794785] usb 5-5: USB disconnect, address 9
[36720.104362] usb 5-5: new high speed USB device using ehci_hcd and address 10
[36720.216347] usb 5-5: device descriptor read/64, error -71
[36720.432314] usb 5-5: device descriptor read/64, error -71
[36720.648287] usb 5-5: new high speed USB device using ehci_hcd and address 11
[36720.760275] usb 5-5: device descriptor read/64, error -71
[36720.976240] usb 5-5: device descriptor read/64, error -71
[36721.192211] usb 5-5: new high speed USB device using ehci_hcd and address 12
[36721.212664] usb 5-5: device descriptor read/all, error -71
[36721.328190] usb 5-5: new high speed USB device using ehci_hcd and address 13
[36721.369861] usb 5-5: configuration #1 chosen from 1 choice
[36721.370107] scsi7 : SCSI emulation for USB Mass Storage devices
[36721.370229] usb-storage: device found at 13
[36721.370231] usb-storage: waiting for device to settle before scanning
[36726.367615] usb-storage: device scan complete
[36726.479471] usb 5-5: reset high speed USB device using ehci_hcd and address 13
[36726.591453] usb 5-5: device descriptor read/64, error -71
[36726.807429] usb 5-5: device descriptor read/64, error -71
[36727.023400] usb 5-5: reset high speed USB device using ehci_hcd and address 13
[36727.135381] usb 5-5: device descriptor read/64, error -71
[36727.351347] usb 5-5: device descriptor read/64, error -71
[36727.567323] usb 5-5: reset high speed USB device using ehci_hcd and address 13
[36727.975260] usb 5-5: device not accepting address 13, error -71
[36728.087245] usb 5-5: reset high speed USB device using ehci_hcd and address 13
[36728.495187] usb 5-5: device not accepting address 13, error -71
[36728.495216] usb 5-5: USB disconnect, address 13
[36728.611179] usb 5-5: new high speed USB device using ehci_hcd and address 14
[36728.723155] usb 5-5: device descriptor read/64, error -71
[36728.939159] usb 5-5: device descriptor read/64, error -71
[36729.155100] usb 5-5: new high speed USB device using ehci_hcd and address 15
[36729.267088] usb 5-5: device descriptor read/64, error -71
[36729.483050] usb 5-5: device descriptor read/64, error -71
[36729.699021] usb 5-5: new high speed USB device using ehci_hcd and address 16
[36730.106962] usb 5-5: device not accepting address 16, error -71
[36730.218949] usb 5-5: new high speed USB device using ehci_hcd and address 17
[36730.626888] usb 5-5: device not accepting address 17, error -71 [
```

Thank you for giving me some of your time.

---

### Post by waynebruce on 2007-06-18
hey someone help please, i would really like to fix this in Ubuntu as opposed to reinstalling Windows.

---

### Post by fdrake on 2007-06-18
what's your output when u type "mount"??
check this link, similar to your case
[http://ubuntuforums.org/showthread.php?t=386173&highlight=usb+drive](http://ubuntuforums.org/showthread.php?t=386173&highlight=usb+drive)

---

### Post by waynebruce on 2007-06-18
I get this:

```
 christopher@christopher-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw) 
```

---

### Post by fdrake on 2007-06-18
do you have a live cd. can it recognize the ext driver? try edgy or dapper. the problem may be a kernel update.

---

### Post by pavan_bitsgoa on 2007-06-19
well exactly i do have the same problem my ntfs external drive just is not recognize

it was automounted on ubuntu proeviously when i dint install ntfs configuration tool
but frm the time i installed it my external drive is not recognized

im pretty sure that my hard disk is perffectly workin (coz it worked on the same comp)
also my phone is recognized 

so i guess thers nothin wrong with my hard disk but it some how just not recognized by ubuntu thats it
so can some one help me out
thank you

---

### Post by waynebruce on 2007-06-19
Well i can access the drive but now I can't eject it.... thank god or allah or buddha or satan or whoever the guy that invented it for multiple usb ports I guess. ;)

[http://www.linuxquestions.org/questions/showthread.php?p=2792799#post2792799](http://www.linuxquestions.org/questions/showthread.php?p=2792799#post2792799)

---

### Post by fdrake on 2007-06-19
> **waynebruce said:**
> Well i can access the drive but now I can't eject it.... thank god or allah or buddha or satan or whoever the guy that invented it for multiple usb ports I guess. ;)

[http://www.linuxquestions.org/questions/showthread.php?p=2792799#post2792799](http://www.linuxquestions.org/questions/showthread.php?p=2792799#post2792799)

u cannot eject it for 2 reasons:
1. because u don't have permission to eject it., try sudo umount    /media/<your drivers name>
2. because it's busy , a program is using it or one of its files.. check with the system monitor ( or type ps -u <your username> ) if there is a program that is using it.

---

### Post by waynebruce on 2007-06-19
Okay, you f'ing rock man.  Thank you  (and everyone) for helping me out with this.  I finally am starting to not miss Windows with Photoshop and Counter Strike.

---

