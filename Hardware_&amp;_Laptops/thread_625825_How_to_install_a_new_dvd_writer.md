---
title: "How to install a new dvd writer?"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by gibbsuk on 2007-11-28
hi there,

sorry, have just brought a dvd writer and i am having trouble installing it,

Its all plugged in but ubuntu wont recognise it - and now Ubuntu wont recognise my other cd rom either...

i have read about DMA but since its not even finding the drive i dont think this applies.

any help would be greatly appreciate.

---

### Post by megamania on 2007-11-28
A simple solution could be to put a CD into the drive and see if it automounts.

If it does, you can then type in a terminal
```
mount
```
which should show you which device file is mounted to /media/cdrom0 (or something like that). It's usually something like /dev/hdc or /dev/scd0.

After that, you can update your /etc/fstab file.

If the drive doesn't automount, you can try
 ```

dmesg | less

```
to find out the device name, but this may be trickier.

Hope that helps.

---

### Post by timcredible on 2007-11-28
with cd and dvd roms/burners, there's got to be a master and if there's a second one, a slave.  there's a little plastic jumper on the drive that will define this (it will be labeled).  make sure you have one master and one slave, can't have 2 masters or 2 slaves.

---

### Post by gibbsuk on 2007-11-28
ok, thanks for the help, yes i had forgot about the jumpers, afraid that the drive did not come with documentation so i am unsure about where to put the jumper though, is there a standard format?

i have disconected the orginal cd-rom drive for the moment and now when i boot it shows the Drive (WAHEY!) but sadly when i put a disc in i cant mount it.

---

### Post by gibbsuk on 2007-11-28
dmesg | less

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (
Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe70000 (usable)
[    0.000000]  BIOS-e820: 000000001fe70000 - 000000001fe72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fe72000 - 000000001fe93000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fe93000 - 000000001ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 130672) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130672
[    0.000000]   HighMem    130672 ->   130672
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130672
[    0.000000] On node 0 totalpages: 130672
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 988 pages used for memmap
[    0.000000]   Normal zone: 125588 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FEB90 checksum 0
[    0.000000] ACPI: RSDP 000FEB90, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD28B, 0034 (r1 DELL    3000           8 ASL        61)
[    0.000000] ACPI: FACP 000FD2BF, 0074 (r1 DELL    3000           8 ASL        61)
[    0.000000] ACPI: DSDT FFFCF6B6, 24C9 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FE70000, 0040
[    0.000000] ACPI: SSDT FFFD1CBC, 00BA (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD333, 006C (r1 DELL    3000           8 ASL        61)
[    0.000000] ACPI: BOOT 000FD39F, 0028 (r1 DELL    3000           8 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[    0.000000] Built 1 zonelists.  Total pages: 129652
[    0.000000] Kernel command line: root=UUID=1ed04764-d00d-4d20-9dad-7f2829dd4341 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2793.297 MHz processor.
[   10.276811] Console: colour VGA+ 80x25
[   10.277043] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.277250] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.285370] Memory: 506380k/522688k available (2015k kernel code, 15704k reserved, 916k data, 364k init, 0k highmem)
[   10.285380] virtual kernel memory layout:
[   10.285382]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   10.285383]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.285384]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   10.285385]     lowmem  : 0xc0000000 - 0xdfe70000   ( 510 MB)
[   10.285386]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   10.285388]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   10.285389]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   10.285392] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.285430] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.365320] Calibrating delay using timer specific routine.. 5590.71 BogoMIPS (lpj=11181433)
[   10.365344] Security Framework v1.0.0 initialized
[   10.365349] SELinux:  Disabled at boot.
[   10.365362] Mount-cache hash table entries: 512
[   10.365486] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   10.365495] monitor/mwait feature present.
[   10.365497] using mwait in idle threads.
[   10.365504] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   10.365507] CPU: L2 cache: 1024K
[   10.365510] CPU: Hyper-Threading is disabled
[   10.365512] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   10.365522] Compat vDSO mapped to ffffe000.
[   10.365538] Checking 'hlt' instruction... OK.
[   10.381390] SMP alternatives: switching to UP code
[   10.381557] Freeing SMP alternatives: 11k freed
[   10.381840] Early unpacking initramfs... done
[   10.695269] ACPI: Core revision 20070126
[   10.707405] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.731072] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
[   10.731113] Total of 1 processors activated (5590.71 BogoMIPS).
[   10.731246] ENABLING IO-APIC IRQs
[   10.731423] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.876518] Brought up 1 CPUs
[   10.876630] Booting paravirtualized kernel on bare hardware
[   10.876698] Time:  2:18:07  Date: 10/29/107
[   10.876718] NET: Registered protocol family 16
[   10.876804] EISA bus registered
[   10.876819] ACPI: bus type pci registered
[   10.901466] PCI: PCI BIOS revision 2.10 entry at 0xfbbf8, last bus=1
[   10.901468] PCI: Using configuration type 1
[   10.901471] Setting up standard PCI resources
[   10.908249] ACPI: EC: Look up EC in DSDT
[   10.937474] ACPI: Interpreter enabled
[   10.937478] ACPI: (supports S0 S1 S3 S4 S5)
[   10.937503] ACPI: Using IOAPIC for interrupt routing
[   10.965324] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.965346] PCI: Probing PCI hardware (bus 00)
[   10.965828] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   10.965832] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   10.966112] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   10.966184] PCI: Transparent bridge - 0000:00:1e.0
[   10.966209] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.966686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   11.067101] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   11.067420] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   11.067738] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   11.068053] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   11.068374] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   11.068689] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   11.069005] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   11.069324] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   11.069461] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.069471] pnp: PnP ACPI init
[   11.069480] ACPI: bus type pnp registered
[   11.092048] pnp: PnP ACPI: found 10 devices
[   11.092051] ACPI: ACPI bus type pnp unregistered
[   11.092056] PnPBIOS: Disabled by ACPI PNP
[   11.092102] PCI: Using ACPI for IRQ routing
[   11.092106] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.097069] NET: Registered protocol family 8
[   11.097071] NET: Registered protocol family 20
[   11.097129] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   11.097133] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
[   11.097136] pnp: 00:00: iomem range 0x1000000-0x1fe6ffff could not be reserved
[   11.097139] pnp: 00:00: iomem range 0xc0000-0xfffff could not be reserved
[   11.097148] pnp: 00:09: ioport range 0x800-0x85f has been reserved
[   11.097151] pnp: 00:09: ioport range 0xc00-0xc7f has been reserved
[   11.097154] pnp: 00:09: ioport range 0x860-0x8ff could not be reserved
[   11.100115] Time: tsc clocksource has been installed.
[   11.127436] PCI: Bridge: 0000:00:1e.0
[   11.127440]   IO window: d000-dfff
[   11.127446]   MEM window: fea00000-feafffff
[   11.127451]   PREFETCH window: disabled.
[   11.127465] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.127475] NET: Registered protocol family 2
[   11.164042] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   11.164078] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   11.164195] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   11.164263] TCP: Hash tables configured (established 16384 bind 16384)
[   11.164266] TCP reno registered
[   11.176124] checking if image is initramfs... it is
[   11.627258] Switched to high resolution mode on CPU 0
[   11.790060] Freeing initrd memory: 7327k freed
[   11.790185] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   11.790188] Simple Boot Flag at 0x7a set to 0x1
[   11.790525] audit: initializing netlink socket (disabled)
[   11.790541] audit(1196302687.212:1): initialized
[   11.792713] VFS: Disk quotas dquot_6.5.1
[   11.792766] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.792862] io scheduler noop registered
[   11.792865] io scheduler anticipatory registered
[   11.792867] io scheduler deadline registered
[   11.792883] io scheduler cfq registered (default)
[   11.792898] Boot video device is 0000:00:02.0
[   11.793106] isapnp: Scanning for PnP cards...
[   12.144470] isapnp: No Plug & Play device found
[   12.170816] Real Time Clock Driver v1.12ac
[   12.170907] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.171003] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.171706] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.172443] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.172661] input: Macintosh mouse button emulation as /class/input/input0
[   12.172789] PNP: No PS/2 controller found. Probing ports directly.
[   12.175949] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.175955] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.176139] mice: PS/2 mouse device common for all mice
[   12.176256] EISA: Probing bus 0 at eisa.0
[   12.176294] EISA: Detected 0 cards.
[   12.176381] TCP cubic registered
[   12.176393] NET: Registered protocol family 1
[   12.176416] Using IPI No-Shortcut mode
[   12.176561]   Magic number: 15:689:309
[   12.176603]   hash matches device ttyxc
[   12.176740]   hash matches device tty38
[   12.177010] Freeing unused kernel memory: 364k freed
[   13.384392] AppArmor: AppArmor initialized<5>audit(1196302688.712:2):  type=1505 info="AppArmor initialized" pid=1163
[   13.686826] fuse init (API version 7.8)
[   13.691376] Failure registering capabilities with primary security module.
[   13.795298] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.446175] usbcore: registered new interface driver usbfs
[   23.446203] usbcore: registered new interface driver hub
[   23.446227] usbcore: registered new device driver usb
[   23.447061] USB Universal Host Controller Interface driver v3.0
[   23.447129] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.447141] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.447146] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.447272] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.447298] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   23.447414] usb usb1: configuration #1 chosen from 1 choice
[   23.447455] hub 1-0:1.0: USB hub found
[   23.447462] hub 1-0:1.0: 2 ports detected
[   23.555419] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   23.555433] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.555437] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.555463] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.555491] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[   23.555597] usb usb2: configuration #1 chosen from 1 choice
[   23.555626] hub 2-0:1.0: USB hub found
[   23.555634] hub 2-0:1.0: 2 ports detected
[   23.659206] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   23.659219] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.659224] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.659252] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 3
[   23.659276] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[   23.659377] usb usb3: configuration #1 chosen from 1 choice
[   23.659406] hub 3-0:1.0: USB hub found
[   23.659412] hub 3-0:1.0: 2 ports detected
[   23.715115] SCSI subsystem initialized
[   23.720901] libata version 2.21 loaded.
[   23.763486] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 18
[   23.763501] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.763505] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.763536] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   23.763573] ehci_hcd 0000:00:1d.7: debug port 1
[   23.763580] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   23.763591] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80800
[   23.794862] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   23.794877] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.794983] usb usb4: configuration #1 chosen from 1 choice
[   23.795019] hub 4-0:1.0: USB hub found
 23.795028] hub 4-0:1.0: 8 ports detected
[   23.864498] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   23.864502] e100: Copyright(c) 1999-2006 Intel Corporation
[   23.899033] ata_piix 0000:00:1f.1: version 2.11
[   23.899057] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   23.899094] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.899193] scsi0 : ata_piix
[   23.899237] scsi1 : ata_piix
[   23.899264] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   23.899268] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   24.054191] FDC 0 is a post-1991 82077
[   24.118711] ata1.00: ATA-6: ST380011A, 8.16, max UDMA/100
[   24.118715] ata1.00: 156250000 sectors, multi 8: LBA48 
[   24.134685] ata1.00: configured for UDMA/100
[   24.453968] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S202H, SB00, max UDMA/66
[   24.453977] ata2.00: limited to UDMA/33 due to 40-wire cable
[   24.625693] ata2.00: configured for UDMA/33
[   24.633471] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.16 PQ: 0 ANSI: 5
[   24.634223] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202H  SB00 PQ: 0 ANSI: 5
[   24.637037] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   24.656591] e100: eth0: e100_probe: addr 0xfeaf7000, irq 20, MAC addr 00:13:20:6B:9B:B5
[   24.853119] sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   24.857097] sd 0:0:0:0: [sda] Write Protect is off
[   24.857101] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.861095] usb 4-3: new high speed USB device using ehci_hcd and address 4
[   24.861203] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.865183] sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   24.869060] sd 0:0:0:0: [sda] Write Protect is off
[   24.869063] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.877047] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.877052]  sda: sda1 sda2 < sda5 >
[   24.916286] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.921005] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.921028] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   24.933415] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.933420] Uniform CD-ROM driver Revision: 3.20
[   24.933475] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.997534] usb 4-3: configuration #1 chosen from 1 choice
[   25.240449] usb 4-4: new high speed USB device using ehci_hcd and address 5
[   25.374188] usb 4-4: configuration #1 chosen from 1 choice
[   25.611818] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   25.787005] usb 1-1: configuration #1 chosen from 1 choice
[   26.027120] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   26.201218] usb 1-2: configuration #1 chosen from 1 choice
[   26.220272] usbcore: registered new interface driver libusual
[   26.228508] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.228513] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.230356] Initializing USB Mass Storage driver...
[   26.230429] scsi2 : SCSI emulation for USB Mass Storage devices
[   26.230476] usb-storage: device found at 4
[   26.230478] usb-storage: waiting for device to settle before scanning
[   26.230512] scsi3 : SCSI emulation for USB Mass Storage devices
[   26.230549] usb-storage: device found at 5
[   26.230551] usb-storage: waiting for device to settle before scanning
[   26.230568] usbcore: registered new interface driver usb-storage
[   26.230571] USB Mass Storage support registered.
[   26.231954] usbcore: registered new interface driver hiddev
[   26.244247] input: Logitech Optical USB Mouse as /class/input/input1
[   26.244272] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[   26.259203] input: Dell Dell USB Keyboard as /class/input/input2
[   26.259212] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-2
[   26.259224] usbcore: registered new interface driver usbhid
[   26.259227] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.527388] Attempting manual resume
[   26.527393] swsusp: Resume From Partition 8:5
[   26.527395] PM: Checking swsusp image.
[   26.630114] PM: Resume from disk failed.
[   27.540637] kjournald starting.  Commit interval 5 seconds
[   27.540649] EXT3-fs: mounted filesystem with ordered data mode.
[   31.218564] usb-storage: device scan complete
[   31.218808] usb-storage: device scan complete
[   31.222451] scsi 2:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[   31.254392] scsi 3:0:0:0: Direct-Access     WDC WD12 00BB-00RDA0      20.0 PQ: 0 ANSI: 0
[   31.274346] sd 3:0:0:0: [sdb] 234441647 512-byte hardware sectors (120034 MB)
[   31.275312] sd 3:0:0:0: [sdb] Write Protect is off
[   31.275315] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   31.275318] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   31.278337] sd 3:0:0:0: [sdb] 234441647 512-byte hardware sectors (120034 MB)
[   31.279304] sd 3:0:0:0: [sdb] Write Protect is off
[   31.279307] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   31.279309] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   31.279314]  sdb: sdb1
[   31.298366] sd 3:0:0:0: [sdb] Attached SCSI disk
[   31.298415] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   31.302328] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   31.302363] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   42.661506] Linux agpgart interface v0.102 (c) Dave Jones
[   42.810423] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.914458] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.930311] agpgart: Detected an Intel 865 Chipset.
[   42.930702] agpgart: Detected 892K stolen memory.
[   42.947293] agpgart: AGP aperture is 128M @ 0xe8000000
[   42.963140] iTCO_vendor_support: vendor-support=0
[   42.965407] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   42.966539] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   42.966770] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   43.212791] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   43.212795]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   43.212797]  you are certain that your <4>intel_rng: system has a functional
[   43.212798]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   43.212798]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   43.222854] input: PC Speaker as /class/input/input3
[   43.363716] parport_pc 00:08: reported by Plug and Play ACPI
[   43.363767] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   43.555195] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0819
[   43.555217] usbcore: registered new interface driver usblp
[   43.555221] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   43.987808] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 17 (level, low) -> IRQ 21
[   44.076286] ieee80211_init: failed to initialize WME (err=-17)
[   44.101169] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   44.101222] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   44.101266] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   44.101337] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   44.113826] wmaster0: Selected rate control algorithm 'simple'
[   44.191664] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   44.191685] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   44.612011] intel8x0_measure_ac97_clock: measured 52387 usecs
[   44.612015] intel8x0: clocking to 48000
[   45.686990] lp0: using parport0 (interrupt-driven).
[   45.737074] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   46.026349] EXT3 FS on sda1, internal journal
[   48.867323] No dock devices found.
[   48.971178] input: Power Button (FF) as /class/input/input4
[   48.975323] ACPI: Power Button (FF) [PWRF]
[   49.012653] input: Power Button (CM) as /class/input/input5
[   49.016780] ACPI: Power Button (CM) [VBTN]
[   50.634585] ppdev: user-space parallel port driver
[   50.646017] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   51.209992] NET: Registered protocol family 10
[   51.210156] lo: Disabled Privacy Extensions
[   51.210318] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.875162] audit(1196302727.961:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4970 profile="/usr/sbin/cupsd"
[   52.015399] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   52.015405] apm: overridden by ACPI.
[   52.829807] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   53.041534] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   53.073928] NFSD: starting 90-second grace period
[   54.764152] Failure registering capabilities with primary security module.
[   55.028217] Bluetooth: Core ver 2.11
[   55.028478] NET: Registered protocol family 31
[   55.028481] Bluetooth: HCI device and connection manager initialized
[   55.028485] Bluetooth: HCI socket layer initialized
[   55.039247] Bluetooth: L2CAP ver 2.8
[   55.039253] Bluetooth: L2CAP socket layer initialized
[   55.091468] Bluetooth: RFCOMM socket layer initialized
[   55.091708] Bluetooth: RFCOMM TTY layer initialized
[   55.091712] Bluetooth: RFCOMM ver 1.8
[   57.642766] [drm] Initialized drm 1.1.0 20060810
[   57.701834] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   57.704215] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   59.834413] NET: Registered protocol family 17
[   74.189911] eth0: no IPv6 routers present
(END) 


[   10.285388]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   10.285389]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   10.285392] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.285430] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.365320] Calibrating delay using timer specific routine.. 5590.71 BogoMIPS (lpj=11181433)
[   10.365344] Security Framework v1.0.0 initialized
[   10.365349] SELinux:  Disabled at boot.
[   10.365362] Mount-cache hash table entries: 512
[   10.365486] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   10.365495] monitor/mwait feature present.
[   10.365497] using mwait in idle threads.
[   10.365504] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   10.365507] CPU: L2 cache: 1024K
[   10.365510] CPU: Hyper-Threading is disabled

---

### Post by gibbsuk on 2007-12-02
OK - now i have disconnected the old Cd-rom the new DVD writer is showing up but when i put a cd or dvd in i cant mount anything...


Any ideas would be greatly appreciated.

thanks

---

### Post by PmDematagoda on 2007-12-02
Sorry, could you please elaborate when you say:-

> the new DVD writer is showing up

---

### Post by gibbsuk on 2007-12-02
Hi sorry - when i go to places> computer i can see a cd-rw/dvd+-rw drive icon
but when i place a cd or dvd in the drive nothing happens when i right click > mount

---

### Post by PmDematagoda on 2007-12-02
Could you post the results of:-
```

cat /etc/fstab
```

---

### Post by gibbsuk on 2007-12-02
dave@dave-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1ed04764-d00d-4d20-9dad-7f2829dd4341 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=9bf686ed-3330-4cf7-a6e5-35c84b293766 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
dave@dave-desktop:~$

---

### Post by PmDematagoda on 2007-12-02
Ok, post what you get in the terminal when trying this:-

```
sudo mount /dev/scd0 /media/cdrom0
```

---

### Post by gibbsuk on 2007-12-02
sorry just realized that i wasn't very clear before - when i right click on the drive - i get "unable to mount  - properly no media in drive"

---

### Post by gibbsuk on 2007-12-02
"no medium found" - ive double checked - there is a cd in the drive

---

### Post by megamania on 2007-12-02
If I understand correctly, you changed cdroms (you took the old one out and installed the new one).
So the line
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```
in fstab is probably related to the old drive. You can try to edit the file and put a # in front of that line in order to comment that out.
Then reboot or enter "mount -a" from a terminal, and try to see if it reads a cd when it is inserted.

Not sure at all this will solve your problem - I'm still learning and just trying to help...

---

### Post by gibbsuk on 2007-12-03
thank you for the response.

ok - i commented out the line in the fstab and rebooted but when i do "mount -a" nothing happens - it just goes back to dave@desktop:

when i try and mount via "computer" i still get - unable to mount - probably no media in drive 

anu other ideas?

---

### Post by megamania on 2007-12-04
> **gibbsuk said:**
> thank you for the response.

ok - i commented out the line in the fstab and rebooted but when i do "mount -a" nothing happens - it just goes back to dave@desktop:

when i try and mount via "computer" i still get - unable to mount - probably no media in drive 

anu other ideas?
the command "mount -a" just forces a re-read of your fstab file, so it's normal that "nothing happens" - no output means that the command was correctly executed.

Now, if you insert a cd in the cd reader, does it automount? 

You can also try these commands and see if one of them works for you (you may have to change the mount point to mnt/cdrom or to an existing directory):
```

sudo mount /dev/cdrom /media/cdrom
sudo mount /dev/scd0 /media/cdrom
sudo mount /dev/hdc /media/cdrom
```

Also, I googled for your problem and found a graphical mount tool here: [http://home.ubalt.edu/abento/linux/terminal/mount.html](http://home.ubalt.edu/abento/linux/terminal/mount.html)

It's in the repos, so you can install it with
```
sudo apt-get install usermode
```
and then run it with "usermount" from a shell. Apparently, it's pretty straightforward. I've never used it though.

Hope that helps.

---

### Post by gibbsuk on 2007-12-08
hi there,
ok when i run "mount -a" the cd is still not mounted
I tired the three commnads you suggested but they do not mount the cd either.

i tried to install usermode but i sia di already have the latest version - to you know how i would run it?


i have been thinking - is there away to deleted all the the configuration for the old cd-rom and new dvd writer and start again?

---

### Post by Yellow Pasque on 2007-12-08
Can you run this command and give output?
```
sudo lshw -C disk
```

---

