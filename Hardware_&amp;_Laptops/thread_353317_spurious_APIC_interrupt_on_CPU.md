---
title: "spurious APIC interrupt on CPU"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by masticate on 2007-02-04
Hi guys,

My computer freezes up when ever there is heavy CPU usage.

So I checked my [COLOR="Red"]**/var/log/messages**[/COLOR], and I noticed a lot of 

```

 kernel: [17180667.728000] spurious APIC interrupt on CPU#0, should never happen.

```

1) Is my CPU going bad? 
2) Are there any good documentation on this?
3) Are there any tests I can run?
4) Any other log files I should look at?


/var/log/messages:
```

Feb  4 12:54:36 deimos syslogd 1.4.1#18ubuntu6: restart.
Feb  4 12:54:36 deimos kernel: Inspecting /boot/System.map-2.6.17-10-generic
Feb  4 12:54:36 deimos kernel: Loaded 22826 symbols from /boot/System.map-2.6.17-10-generic.
Feb  4 12:54:36 deimos kernel: Symbols match kernel version 2.6.17.
Feb  4 12:54:36 deimos kernel: No module symbols loaded - kernel modules not enabled. 
Feb  4 12:54:36 deimos kernel: [17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
Feb  4 12:54:36 deimos kernel: [17179569.184000] BIOS-provided physical RAM map:
Feb  4 12:54:36 deimos kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Feb  4 12:54:36 deimos kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb  4 12:54:36 deimos kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Feb  4 12:54:36 deimos kernel: [17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
Feb  4 12:54:36 deimos kernel: [17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
Feb  4 12:54:36 deimos kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb  4 12:54:36 deimos kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb  4 12:54:36 deimos kernel: [17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb  4 12:54:36 deimos kernel: [17179569.184000] 127MB HIGHMEM available.
Feb  4 12:54:36 deimos kernel: [17179569.184000] 896MB LOWMEM available.
Feb  4 12:54:36 deimos kernel: [17179569.184000] DMI 2.2 present.
Feb  4 12:54:36 deimos kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x4008
Feb  4 12:54:36 deimos kernel: [17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Feb  4 12:54:36 deimos kernel: [17179569.184000] Built 1 zonelists
Feb  4 12:54:36 deimos kernel: [17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
Feb  4 12:54:36 deimos kernel: [17179569.184000] Found and enabled local APIC!
Feb  4 12:54:36 deimos kernel: [17179569.184000] Enabling fast FPU save and restore... done.
Feb  4 12:54:36 deimos kernel: [17179569.184000] Enabling unmasked SIMD FPU exception support... done.
Feb  4 12:54:36 deimos kernel: [17179569.184000] Initializing CPU#0
Feb  4 12:54:36 deimos kernel: [17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb  4 12:54:36 deimos kernel: [17179569.184000] Detected 1600.906 MHz processor.
Feb  4 12:54:36 deimos kernel: [17179569.184000] Using pmtmr for high-res timesource
Feb  4 12:54:36 deimos kernel: [17179569.184000] Console: colour VGA+ 80x25
Feb  4 12:54:36 deimos kernel: [17179572.632000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb  4 12:54:36 deimos kernel: [17179572.636000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb  4 12:54:36 deimos kernel: [17179572.676000] Memory: 1029636k/1048512k available (1910k kernel code, 18100k reserved, 1069k data, 308k init, 131008k highmem)
Feb  4 12:54:36 deimos kernel: [17179572.676000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb  4 12:54:36 deimos kernel: [17179572.756000] Calibrating delay using timer specific routine.. 3204.88 BogoMIPS (lpj=6409778)
Feb  4 12:54:36 deimos kernel: [17179572.756000] Security Framework v1.0.0 initialized
Feb  4 12:54:36 deimos kernel: [17179572.756000] SELinux:  Disabled at boot.
Feb  4 12:54:36 deimos kernel: [17179572.756000] Mount-cache hash table entries: 512
Feb  4 12:54:36 deimos kernel: [17179572.756000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb  4 12:54:36 deimos kernel: [17179572.756000] CPU: L2 Cache: 256K (64 bytes/line)
Feb  4 12:54:36 deimos kernel: [17179572.756000] Checking 'hlt' instruction... OK.
Feb  4 12:54:36 deimos kernel: [17179572.772000] SMP alternatives: switching to UP code
Feb  4 12:54:36 deimos kernel: [17179572.772000] Freeing SMP alternatives: 16k freed
Feb  4 12:54:36 deimos kernel: [17179572.772000] checking if image is initramfs... it is
Feb  4 12:54:36 deimos kernel: [17179573.352000] Freeing initrd memory: 5326k freed
Feb  4 12:54:36 deimos kernel: [17179573.352000] ACPI: Core revision 20060707
Feb  4 12:54:36 deimos kernel: [17179573.428000] ACPI: Looking for DSDT ... not found!
Feb  4 12:54:36 deimos kernel: [17179573.428000] ACPI: setting ELCR to 0200 (from 1e00)
Feb  4 12:54:36 deimos kernel: [17179573.540000] CPU0: AMD Athlon(tm) XP 1900+ stepping 02
Feb  4 12:54:36 deimos kernel: [17179573.540000] SMP motherboard not detected.
Feb  4 12:54:36 deimos kernel: [17179573.644000] Brought up 1 CPUs
Feb  4 12:54:36 deimos kernel: [17179573.644000] migration_cost=0
Feb  4 12:54:36 deimos kernel: [17179573.644000] NET: Registered protocol family 16
Feb  4 12:54:36 deimos kernel: [17179573.644000] EISA bus registered
Feb  4 12:54:36 deimos kernel: [17179573.644000] ACPI: bus type pci registered
Feb  4 12:54:36 deimos kernel: [17179573.724000] PCI: PCI BIOS revision 2.10 entry at 0xfb4d0, last bus=1
Feb  4 12:54:36 deimos kernel: [17179573.724000] PCI: Using configuration type 1
Feb  4 12:54:36 deimos kernel: [17179573.724000] Setting up standard PCI resources
Feb  4 12:54:36 deimos kernel: [17179573.752000] ACPI: Interpreter enabled
Feb  4 12:54:36 deimos kernel: [17179573.752000] ACPI: Using PIC for interrupt routing
Feb  4 12:54:36 deimos kernel: [17179573.756000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb  4 12:54:36 deimos kernel: [17179573.756000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Feb  4 12:54:36 deimos kernel: [17179573.756000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
Feb  4 12:54:36 deimos kernel: [17179573.776000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Feb  4 12:54:36 deimos kernel: [17179573.776000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
Feb  4 12:54:36 deimos kernel: [17179573.776000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Feb  4 12:54:36 deimos kernel: [17179573.776000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
Feb  4 12:54:36 deimos kernel: [17179573.776000] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Feb  4 12:54:36 deimos kernel: [17179573.780000] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Feb  4 12:54:36 deimos kernel: [17179573.780000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
Feb  4 12:54:36 deimos kernel: [17179573.780000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0, disabled.
Feb  4 12:54:36 deimos kernel: [17179573.784000] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb  4 12:54:36 deimos kernel: [17179573.784000] pnp: PnP ACPI init
Feb  4 12:54:36 deimos kernel: [17179573.788000] pnp: PnP ACPI: found 12 devices
Feb  4 12:54:36 deimos kernel: [17179573.788000] PnPBIOS: Disabled by ACPI PNP
Feb  4 12:54:36 deimos kernel: [17179573.788000] PCI: Using ACPI for IRQ routing
Feb  4 12:54:36 deimos kernel: [17179573.788000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Feb  4 12:54:36 deimos kernel: [17179573.808000] PCI: Bridge: 0000:00:01.0
Feb  4 12:54:36 deimos kernel: [17179573.808000]   IO window: disabled.
Feb  4 12:54:36 deimos kernel: [17179573.808000]   MEM window: e6000000-e7ffffff
Feb  4 12:54:36 deimos kernel: [17179573.808000]   PREFETCH window: d0000000-d7ffffff
Feb  4 12:54:36 deimos kernel: [17179573.808000] NET: Registered protocol family 2
Feb  4 12:54:36 deimos kernel: [17179573.848000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb  4 12:54:36 deimos kernel: [17179573.848000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb  4 12:54:36 deimos kernel: [17179573.848000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb  4 12:54:36 deimos kernel: [17179573.852000] TCP: Hash tables configured (established 131072 bind 65536)
Feb  4 12:54:36 deimos kernel: [17179573.852000] TCP reno registered
Feb  4 12:54:36 deimos kernel: [17179573.852000] audit: initializing netlink socket (disabled)
Feb  4 12:54:36 deimos kernel: [17179573.852000] audit(1170611652.852:1): initialized
Feb  4 12:54:36 deimos kernel: [17179573.852000] highmem bounce pool size: 64 pages
Feb  4 12:54:36 deimos kernel: [17179573.852000] VFS: Disk quotas dquot_6.5.1
Feb  4 12:54:36 deimos kernel: [17179573.852000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb  4 12:54:36 deimos kernel: [17179573.852000] Initializing Cryptographic API
Feb  4 12:54:36 deimos kernel: [17179573.852000] io scheduler noop registered
Feb  4 12:54:36 deimos kernel: [17179573.852000] io scheduler anticipatory registered
Feb  4 12:54:36 deimos kernel: [17179573.852000] io scheduler deadline registered
Feb  4 12:54:36 deimos kernel: [17179573.852000] io scheduler cfq registered (default)
Feb  4 12:54:36 deimos kernel: [17179573.852000] isapnp: Scanning for PnP cards...
Feb  4 12:54:36 deimos kernel: [17179574.208000] isapnp: No Plug & Play device found
Feb  4 12:54:36 deimos kernel: [17179574.232000] Real Time Clock Driver v1.12ac
Feb  4 12:54:36 deimos kernel: [17179574.232000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Feb  4 12:54:36 deimos kernel: [17179574.232000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  4 12:54:36 deimos kernel: [17179574.232000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  4 12:54:36 deimos kernel: [17179574.236000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb  4 12:54:36 deimos kernel: [17179574.236000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Feb  4 12:54:36 deimos kernel: [17179574.236000] mice: PS/2 mouse device common for all mice
Feb  4 12:54:36 deimos kernel: [17179574.236000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Feb  4 12:54:36 deimos kernel: [17179574.236000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb  4 12:54:36 deimos kernel: [17179574.236000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb  4 12:54:36 deimos kernel: [17179574.236000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Feb  4 12:54:36 deimos kernel: [17179574.236000] PNP: PS/2 controller doesn't have AUX irq; using default 12
Feb  4 12:54:36 deimos kernel: [17179574.236000] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb  4 12:54:36 deimos kernel: [17179574.236000] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  4 12:54:36 deimos kernel: [17179574.236000] EISA: Probing bus 0 at eisa.0
Feb  4 12:54:36 deimos kernel: [17179574.236000] Cannot allocate resource for EISA slot 4
Feb  4 12:54:36 deimos kernel: [17179574.236000] EISA: Detected 0 cards.
Feb  4 12:54:36 deimos kernel: [17179574.236000] TCP bic registered
Feb  4 12:54:36 deimos kernel: [17179574.236000] NET: Registered protocol family 1
Feb  4 12:54:36 deimos kernel: [17179574.236000] NET: Registered protocol family 8
Feb  4 12:54:36 deimos kernel: [17179574.236000] NET: Registered protocol family 20
Feb  4 12:54:36 deimos kernel: [17179574.236000] Using IPI No-Shortcut mode
Feb  4 12:54:36 deimos kernel: [17179574.236000] ACPI: (supports S0 S1 S4 S5)
Feb  4 12:54:36 deimos kernel: [17179574.240000] Freeing unused kernel memory: 308k freed
Feb  4 12:54:36 deimos kernel: [17179574.288000] input: AT Translated Set 2 keyboard as /class/input/input0
Feb  4 12:54:36 deimos kernel: [17179575.388000] Capability LSM initialized
Feb  4 12:54:36 deimos kernel: [17179575.428000] ACPI: Fan [FAN] (on)
Feb  4 12:54:36 deimos kernel: [17179575.432000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Feb  4 12:54:36 deimos kernel: [17179575.432000] ACPI: Processor [CPU0] (supports 2 throttling states)
Feb  4 12:54:36 deimos kernel: [17179575.436000] ACPI: Thermal Zone [THRM] (29 C)
Feb  4 12:54:36 deimos kernel: [17179576.060000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
Feb  4 12:54:36 deimos kernel: [17179576.060000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Feb  4 12:54:36 deimos kernel: [17179576.060000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb  4 12:54:36 deimos kernel: [17179576.060000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 11
Feb  4 12:54:36 deimos kernel: [17179576.060000] VP_IDE: chipset revision 6
Feb  4 12:54:36 deimos kernel: [17179576.060000] VP_IDE: not 100%% native mode: will probe irqs later
Feb  4 12:54:36 deimos kernel: [17179576.060000] VP_IDE: VIA vt8233a (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Feb  4 12:54:36 deimos kernel: [17179576.060000]     ide0: BM-DMA at 0xdc00-0xdc07, BIOS settings: hda:DMA, hdb:pio
Feb  4 12:54:36 deimos kernel: [17179576.060000]     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings: hdc:DMA, hdd:pio
Feb  4 12:54:36 deimos kernel: [17179576.492000] hda: SAMSUNG SP2514N, ATA DISK drive
Feb  4 12:54:36 deimos kernel: [17179577.216000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb  4 12:54:36 deimos kernel: [17179577.648000] hdc: IRQ probe failed (0xffffbcf8)
Feb  4 12:54:36 deimos kernel: [17179578.240000] hdc: TSSTcorpCD/DVDW SH-S162A, ATAPI CD/DVD-ROM drive
Feb  4 12:54:36 deimos kernel: [17179578.920000] ide1 at 0x170-0x177,0x376 on irq 15
Feb  4 12:54:36 deimos kernel: [17179578.928000] hda: max request size: 512KiB
Feb  4 12:54:36 deimos kernel: [17179578.940000] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
Feb  4 12:54:36 deimos kernel: [17179578.940000] hda: cache flushes supported
Feb  4 12:54:36 deimos kernel: [17179578.940000]  hda: hda1 hda2 <<7>APIC error on CPU0: 01(01)
Feb  4 12:54:36 deimos kernel: [17179578.968000]  hda5 >
Feb  4 12:54:36 deimos kernel: [17179578.980000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb  4 12:54:36 deimos kernel: [17179578.980000] Uniform CD-ROM driver Revision: 3.20
Feb  4 12:54:36 deimos kernel: [17179579.188000] usbcore: registered new driver usbfs
Feb  4 12:54:36 deimos kernel: [17179579.188000] usbcore: registered new driver hub
Feb  4 12:54:36 deimos kernel: [17179579.188000] USB Universal Host Controller Interface driver v3.0
Feb  4 12:54:36 deimos kernel: [17179579.188000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
Feb  4 12:54:36 deimos kernel: [17179579.188000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Feb  4 12:54:36 deimos kernel: [17179579.188000] uhci_hcd 0000:00:11.2: UHCI Host Controller
Feb  4 12:54:36 deimos kernel: [17179579.188000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
Feb  4 12:54:36 deimos kernel: [17179579.188000] uhci_hcd 0000:00:11.2: irq 10, io base 0x0000e000
Feb  4 12:54:36 deimos kernel: [17179579.188000] usb usb1: configuration #1 chosen from 1 choice
Feb  4 12:54:36 deimos kernel: [17179579.188000] hub 1-0:1.0: USB hub found
Feb  4 12:54:36 deimos kernel: [17179579.188000] hub 1-0:1.0: 2 ports detected
Feb  4 12:54:36 deimos kernel: [17179579.292000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Feb  4 12:54:36 deimos kernel: [17179579.292000] uhci_hcd 0000:00:11.3: UHCI Host Controller
Feb  4 12:54:36 deimos kernel: [17179579.292000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
Feb  4 12:54:36 deimos kernel: [17179579.292000] uhci_hcd 0000:00:11.3: irq 10, io base 0x0000e400
Feb  4 12:54:36 deimos kernel: [17179579.292000] usb usb2: configuration #1 chosen from 1 choice
Feb  4 12:54:36 deimos kernel: [17179579.292000] hub 2-0:1.0: USB hub found
Feb  4 12:54:36 deimos kernel: [17179579.292000] hub 2-0:1.0: 2 ports detected
Feb  4 12:54:36 deimos kernel: [17179579.464000] Attempting manual resume
Feb  4 12:54:36 deimos kernel: [17179579.480000] EXT3-fs: INFO: recovery required on readonly filesystem.
Feb  4 12:54:36 deimos kernel: [17179579.480000] EXT3-fs: write access will be enabled during recovery.
Feb  4 12:54:36 deimos kernel: [17179579.536000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Feb  4 12:54:36 deimos kernel: [17179579.712000] usb 1-1: configuration #1 chosen from 1 choice
Feb  4 12:54:36 deimos kernel: [17179580.096000] usbcore: registered new driver hiddev
Feb  4 12:54:36 deimos kernel: [17179580.112000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
Feb  4 12:54:36 deimos kernel: [17179580.112000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:11.2-1
Feb  4 12:54:36 deimos kernel: [17179580.112000] usbcore: registered new driver usbhid
Feb  4 12:54:36 deimos kernel: [17179580.112000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Feb  4 12:54:36 deimos kernel: [17179581.356000] kjournald starting.  Commit interval 5 seconds
Feb  4 12:54:36 deimos kernel: [17179581.356000] EXT3-fs: hda1: orphan cleanup on readonly fs
Feb  4 12:54:36 deimos kernel: [17179581.356000] EXT3-fs: hda1: 5 orphan inodes deleted
Feb  4 12:54:36 deimos kernel: [17179581.356000] EXT3-fs: recovery complete.
Feb  4 12:54:36 deimos kernel: [17179581.372000] EXT3-fs: mounted filesystem with ordered data mode.
Feb  4 12:54:36 deimos kernel: [17179589.804000] NET: Registered protocol family 23
Feb  4 12:54:36 deimos kernel: [17179590.056000] parport: PnPBIOS parport detected.
Feb  4 12:54:36 deimos kernel: [17179590.056000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb  4 12:54:36 deimos kernel: [17179590.092000] Linux Tulip driver version 1.1.14 (May 6, 2006)
Feb  4 12:54:36 deimos kernel: [17179590.092000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Feb  4 12:54:36 deimos kernel: [17179590.092000] tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
Feb  4 12:54:36 deimos kernel: [17179590.092000] tulip0:  MII transceiver #2 config 1000 status 7849 advertising 05e1.
Feb  4 12:54:36 deimos kernel: [17179590.096000] tulip0:  MII transceiver #3 config 1000 status 7849 advertising 05e1.
Feb  4 12:54:36 deimos kernel: [17179590.096000] tulip0:  MII transceiver #4 config 1000 status 7849 advertising 05e1.
Feb  4 12:54:36 deimos kernel: [17179590.096000] eth0: ADMtek Comet rev 17 at Port 0xd000, 00:04:5A:69:06:F5, IRQ 10.
Feb  4 12:54:36 deimos kernel: [17179590.148000] Linux agpgart interface v0.101 (c) Dave Jones
Feb  4 12:54:36 deimos kernel: [17179590.188000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  4 12:54:36 deimos kernel: [17179590.272000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  4 12:54:36 deimos kernel: [17179590.452000] nvidia: module license 'NVIDIA' taints kernel.
Feb  4 12:54:36 deimos kernel: [17179590.464000] PCI: Enabling device 0000:00:0f.0 (0000 -> 0002)
Feb  4 12:54:36 deimos kernel: [17179590.464000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
Feb  4 12:54:36 deimos kernel: [17179590.464000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
Feb  4 12:54:36 deimos kernel: [17179590.464000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb  4 12:54:36 deimos kernel: [17179590.468000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Feb  4 12:54:36 deimos kernel: [17179590.772000] Floppy drive(s): fd0 is 1.44M
Feb  4 12:54:36 deimos kernel: [17179590.788000] FDC 0 is a post-1991 82077
Feb  4 12:54:36 deimos kernel: [17179590.892000] gameport: EMU10K1 is pci0000:00:10.1/gameport0, io 0xd800, speed 1193kHz
Feb  4 12:54:36 deimos kernel: [17179590.952000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
Feb  4 12:54:36 deimos kernel: [17179590.956000] agpgart: AGP aperture is 64M @ 0xe0000000
Feb  4 12:54:36 deimos kernel: [17179590.996000] input: PC Speaker as /class/input/input2
Feb  4 12:54:36 deimos kernel: [17179591.452000] ts: Compaq touchscreen protocol output
Feb  4 12:54:36 deimos kernel: [17179591.740000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb  4 12:54:36 deimos kernel: [17179591.992000] lp0: using parport0 (interrupt-driven).
Feb  4 12:54:36 deimos kernel: [17179592.040000] Adding 3028212k swap on /dev/disk/by-uuid/1db8579b-09dc-4159-934b-6ca0de82d1d6.  Priority:-1 extents:1 across:3028212k
Feb  4 12:54:36 deimos kernel: [17179592.092000] EXT3 FS on hda1, internal journal
Feb  4 12:54:36 deimos kernel: [17179592.300000] NET: Registered protocol family 17
Feb  4 12:54:36 deimos kernel: [17179594.252000] eth0: Setting full-duplex based on MII#1 link partner capability of 41e1.
Feb  4 12:54:36 deimos kernel: [17179594.276000] NET: Registered protocol family 10
Feb  4 12:54:36 deimos kernel: [17179594.276000] lo: Disabled Privacy Extensions
Feb  4 12:54:36 deimos kernel: [17179594.276000] IPv6 over IPv4 tunneling driver
Feb  4 12:54:36 deimos kernel: [17179599.328000] ACPI: Power Button (FF) [PWRF]
Feb  4 12:54:36 deimos kernel: [17179599.328000] ACPI: Power Button (CM) [PWRB]
Feb  4 12:54:36 deimos kernel: [17179599.328000] ACPI: Sleep Button (CM) [SLPB]
Feb  4 12:54:36 deimos kernel: [17179599.540000] pcc_acpi: loading...
Feb  4 12:54:38 deimos kernel: [17179602.132000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Feb  4 12:54:38 deimos kernel: [17179602.132000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
Feb  4 12:54:38 deimos kernel: [17179602.132000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
Feb  4 12:54:38 deimos hpiod: 1.6.9 accepting connections at 2208... 
Feb  4 12:54:43 deimos kernel: [17179607.400000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Feb  4 12:54:43 deimos kernel: [17179607.400000] apm: overridden by ACPI.
Feb  4 12:54:45 deimos kernel: [17179610.012000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:54:47 deimos kernel: [17179611.900000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Feb  4 12:54:47 deimos kernel: [17179612.000000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Feb  4 12:54:47 deimos kernel: [17179612.024000] NFSD: starting 90-second grace period
Feb  4 12:54:48 deimos kernel: [17179612.964000] bridge-eth0: already up
Feb  4 12:54:49 deimos kernel: [17179613.296000] Bluetooth: Core ver 2.8
Feb  4 12:54:49 deimos kernel: [17179613.296000] NET: Registered protocol family 31
Feb  4 12:54:49 deimos kernel: [17179613.296000] Bluetooth: HCI device and connection manager initialized
Feb  4 12:54:49 deimos kernel: [17179613.296000] Bluetooth: HCI socket layer initialized
Feb  4 12:54:49 deimos kernel: [17179613.324000] Bluetooth: L2CAP ver 2.8
Feb  4 12:54:49 deimos kernel: [17179613.324000] Bluetooth: L2CAP socket layer initialized
Feb  4 12:54:49 deimos kernel: [17179613.368000] Bluetooth: RFCOMM socket layer initialized
Feb  4 12:54:49 deimos kernel: [17179613.368000] Bluetooth: RFCOMM TTY layer initialized
Feb  4 12:54:49 deimos kernel: [17179613.368000] Bluetooth: RFCOMM ver 1.7
Feb  4 12:55:03 deimos kernel: [17179627.928000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:55:11 deimos kernel: [17179636.080000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:55:46 deimos kernel: [17179670.844000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:56:38 deimos kernel: [17179722.944000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:56:51 deimos kernel: [17179735.244000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:56:56 deimos kernel: [17179740.956000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:57:00 deimos kernel: [17179744.724000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:57:48 deimos kernel: [17179793.116000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:57:50 deimos kernel: [17179794.164000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:58:13 deimos kernel: [17179817.728000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:58:15 deimos kernel: [17179819.712000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:59:06 deimos kernel: [17179870.916000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 12:59:13 deimos kernel: [17179877.928000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:00:15 deimos kernel: [17179939.852000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:00:16 deimos kernel: [17179940.248000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:00:22 deimos kernel: [17179947.056000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:00:29 deimos kernel: [17179953.884000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:00:30 deimos kernel: [17179955.032000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:01:07 deimos kernel: [17179991.836000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:01:13 deimos kernel: [17179997.920000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:01:18 deimos kernel: [17180002.684000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:01:40 deimos kernel: [17180024.656000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:02:06 deimos kernel: [17180051.100000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:02:11 deimos kernel: [17180056.044000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:05:16 deimos kernel: [17180240.360000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:05:43 deimos kernel: [17180267.732000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:05:47 deimos kernel: [17180271.724000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:06:11 deimos kernel: [17180295.972000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:06:37 deimos kernel: [17180321.948000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:06:39 deimos kernel: [17180323.412000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:06:44 deimos kernel: [17180328.312000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:07:04 deimos kernel: [17180348.988000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:07:27 deimos kernel: [17180372.040000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:08:40 deimos kernel: [17180444.764000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:08:40 deimos kernel: [17180444.920000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:08:51 deimos kernel: [17180456.096000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:09:37 deimos kernel: [17180501.336000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:10:24 deimos kernel: [17180548.740000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:10:44 deimos gconfd (ashok-4802): starting (version 2.16.0), pid 4802 user 'ashok'
Feb  4 13:10:44 deimos gconfd (ashok-4802): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  4 13:10:44 deimos gconfd (ashok-4802): Resolved address "xml:readwrite:/home/ashok/.gconf" to a writable configuration source at position 1
Feb  4 13:10:44 deimos gconfd (ashok-4802): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  4 13:10:44 deimos gconfd (ashok-4802): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb  4 13:10:44 deimos gconfd (ashok-4802): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb  4 13:10:45 deimos kernel: [17180569.884000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:10:50 deimos gconfd (ashok-4802): Resolved address "xml:readwrite:/home/ashok/.gconf" to a writable configuration source at position 0
Feb  4 13:11:56 deimos kernel: [17180640.240000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:12:00 deimos kernel: [17180644.528000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:12:03 deimos kernel: [17180647.844000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:12:08 deimos kernel: [17180653.040000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:12:23 deimos kernel: [17180667.728000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:12:36 deimos kernel: [17180681.200000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:12:40 deimos kernel: [17180684.332000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:13:16 deimos kernel: [17180720.956000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:13:28 deimos kernel: [17180732.944000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:14:11 deimos kernel: [17180776.172000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:14:25 deimos kernel: [17180790.116000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:14:26 deimos kernel: [17180790.960000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:14:32 deimos kernel: [17180797.072000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:14:40 deimos kernel: [17180804.252000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:14:59 deimos kernel: [17180823.380000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:15:09 deimos kernel: [17180833.848000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:15:28 deimos kernel: [17180852.312000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:16:07 deimos kernel: [17180891.792000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:16:15 deimos kernel: [17180899.424000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:16:28 deimos kernel: [17180912.828000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:16:56 deimos kernel: [17180941.140000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:17:40 deimos kernel: [17180985.192000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:17:46 deimos kernel: [17180990.856000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:18:10 deimos kernel: [17181014.976000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:18:10 deimos kernel: [17181015.728000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:18:19 deimos kernel: [17181024.212000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:19:07 deimos kernel: [17181072.792000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:19:21 deimos kernel: [17181086.096000] spurious APIC interrupt on CPU#0, should never happen.
Feb  4 13:19:33 deimos kernel: [17181098.024000] spurious APIC interrupt on CPU#0, should never happen.

```

---

### Post by TheTank on 2007-07-20
I am getting the same problems.
I have tried a solution, by adding 'noapic pollirq' but did not work.

Can anyone help?

---

