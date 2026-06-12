---
title: "USB device problems"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by Billxyzzy on 2008-12-10
I have an interesting problem with IBEX 64 Bit USB detection
When I used the live CD this problem did not show up.
I am running a dual boot system,  Win Xp and Ibex 8.10 64Bit.
When running windows all usb devices show up and are properly
identified.  In Ubuntu none show up.  Only when running the 
live CD to they show up.

Hardware:
Elitegroup AMD690GM-M2 motherboard
CPU  Athlon dual 4200
2GB ram

Kernel:
2.6.27.7-Generic (this was with the ISO)
2.6.27.9-Generic (Running this now)

Ran the following:
lsusb
tail -f /var/log/messages
dmesg
dmesg

I have not,as yet,  downloaded the alternate ISO.


Looking for suggestions to alter the boot process to 
idendtify USB devices properly.

Ok,  the details:

This is long so prepare for a long read

bill@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
____________________________________________________________________________
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bill@ubuntu:~$ 

bill@ubuntu:~$ tail -f /var/log/messages
Dec  9 17:21:41 ubuntu kernel: [  110.336031] Bluetooth: RFCOMM ver 1.10
Dec  9 17:21:43 ubuntu pcscd: pcscdaemon.c:498:main() pcsc-lite 1.4.102 daemon ready.
Dec  9 17:21:45 ubuntu kernel: [  114.416031] r8169: eth0: link up
Dec  9 17:21:45 ubuntu kernel: [  114.424031] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Dec  9 17:21:45 ubuntu kernel: [  114.424031] [fglrx] Reserved FB block: Unshared offset:ffb7000, size:44000 
Dec  9 17:21:45 ubuntu kernel: [  114.424031] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
Dec  9 17:21:45 ubuntu kernel: [  114.672031] NET: Registered protocol family 17
Dec  9 17:22:00 ubuntu pulseaudio[4922]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  9 17:22:01 ubuntu pulseaudio[4924]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  9 17:22:01 ubuntu pulseaudio[4924]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

Follows dmesg output:

[    0.092005] PCI: 0000:01:00.0 reg 18 64bit mmio: [fdef0000, fdefffff]
[    0.092005] PCI: 0000:01:00.0 reg 20 io port: [ee00, eeff]
[    0.092005] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.092005] pci 0000:01:00.0: supports D1
[    0.092005] pci 0000:01:00.0: supports D2
[    0.092005] PCI: 0000:01:00.1 reg 10 64bit mmio: [fdee0000, fdeeffff]
[    0.092005] pci 0000:01:00.1: supports D1
[    0.092005] pci 0000:01:00.1: supports D2
[    0.092005] PCI: bridge 0000:00:02.0 io port: [e000, efff]
[    0.092005] PCI: bridge 0000:00:02.0 32bit mmio: [fde00000, fdefffff]
[    0.092005] PCI: bridge 0000:00:02.0 64bit mmio pref: [d0000000, dfffffff]
[    0.092005] PCI: 0000:02:05.0 reg 10 io port: [de00, deff]
[    0.092005] PCI: 0000:02:05.0 reg 14 32bit mmio: [fddff000, fddff0ff]
[    0.092005] PCI: 0000:02:05.0 reg 30 32bit mmio: [0, 1ffff]
[    0.092005] pci 0000:02:05.0: supports D1
[    0.092005] pci 0000:02:05.0: supports D2
[    0.092005] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.092005] pci 0000:02:05.0: PME# disabled
[    0.092005] pci 0000:00:14.4: transparent bridge
[    0.092005] PCI: bridge 0000:00:14.4 io port: [d000, dfff]
[    0.092005] PCI: bridge 0000:00:14.4 32bit mmio: [fdd00000, fddfffff]
[    0.092005] PCI: bridge 0000:00:14.4 32bit mmio pref: [fdf00000, fdffffff]
[    0.108006] NET: Registered protocol family 8
[    0.108006] NET: Registered protocol family 20
[    0.108006] NetLabel: Initializing
[    0.108006] NetLabel:  domain hash size = 128
[    0.108006] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.108006] NetLabel:  unlabeled traffic allowed by default
[    0.108006] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.108006]    actual entries 65586
[    0.108006] AppArmor: AppArmor Filesystem Enabled
[    0.108006] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.108006] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.108006] pci 0000:00:02.0:   MEM window: 0xfde00000-0xfdefffff
[    0.108006] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.108006] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.108006] pci 0000:00:14.4:   IO window: 0xd000-0xdfff
[    0.108006] pci 0000:00:14.4:   MEM window: 0xfdd00000-0xfddfffff
[    0.108006] pci 0000:00:14.4:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.108006] pci 0000:00:02.0: setting latency timer to 64
[    0.108006] bus: 00 index 0 io port: [0, ffff]
[    0.108006] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.108006] bus: 01 index 0 io port: [e000, efff]
[    0.108006] bus: 01 index 1 mmio: [fde00000, fdefffff]
[    0.108006] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.108006] bus: 01 index 3 mmio: [0, 0]
[    0.108006] bus: 02 index 0 io port: [d000, dfff]
[    0.108006] bus: 02 index 1 mmio: [fdd00000, fddfffff]
[    0.108006] bus: 02 index 2 mmio: [fdf00000, fdffffff]
[    0.108006] bus: 02 index 3 io port: [0, ffff]
[    0.108006] bus: 02 index 4 mmio: [0, ffffffffffffffff]
[    0.108006] NET: Registered protocol family 2
[    0.144009] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.144009] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.144009] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.144009] TCP: Hash tables configured (established 262144 bind 65536)
[    0.144009] TCP reno registered
[    0.156009] NET: Registered protocol family 1
[    0.156009] checking if image is initramfs... it is
[    0.888031] Freeing initrd memory: 8681k freed
[    0.892031] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.892031] audit: initializing netlink socket (disabled)
[    0.892031] type=2000 audit(1228843190.892:1): initialized
[    0.896031] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.900031] VFS: Disk quotas dquot_6.5.1
[    0.900031] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.900031] msgmni has been set to 4016
[    0.900031] io scheduler noop registered
[    0.900031] io scheduler anticipatory registered
[    0.900031] io scheduler deadline registered
[    0.900031] io scheduler cfq registered (default)
[    1.016031] pci 0000:01:00.0: Boot video device
[    1.016031] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.016031] pcieport-driver 0000:00:02.0: found MSI capability
[    1.016031] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.048031] Linux agpgart interface v0.103
[    1.048031] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.048031] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.052031] brd: module loaded
[    1.052031] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.052031] PNP: No PS/2 controller found. Probing ports directly.
[    1.052031] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.052031] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.056031] mice: PS/2 mouse device common for all mice
[    1.056031] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    1.056031] rtc0: alarms up to one day
[    1.056031] cpuidle: using governor ladder
[    1.056031] cpuidle: using governor menu
[    1.056031] TCP cubic registered
[    1.056031] registered taskstats version 1
[    1.056031]   Magic number: 4:786:339
[    1.056031] tty ttyze: hash matches
[    1.056031] pci 0000:00:13.5: hash matches
[    1.056031] rtc_cmos rtc_cmos: setting system clock to 2008-12-09 17:19:51 UTC (1228843191)
[    1.056031] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.056031] EDD information not available.
[    1.056031] Freeing unused kernel memory: 536k freed
[    1.056031] Write protecting the kernel read-only data: 4348k
[    1.076031] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.240031] fuse init (API version 7.9)
[    1.460031] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    1.604031] SCSI subsystem initialized
[    1.656031] libata version 3.00 loaded.
[    1.680031] usbcore: registered new interface driver usbfs
[    1.680031] usbcore: registered new interface driver hub
[    1.688031] ahci 0000:00:12.0: version 3.0
[    1.688031] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.688031] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.688031] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio 
[    1.700031] usbcore: registered new device driver usb
[    1.716031] scsi0 : ahci
[    1.728031] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.736031] scsi1 : ahci
[    1.760031] scsi2 : ahci
[    1.780031] scsi3 : ahci
[    1.780031] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 11
[    1.780031] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 11
[    1.780031] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 11
[    1.780031] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 11
__________________________________________________________________________________
[    2.432031] ata1: softreset failed (device not ready)
[    2.432031] ata1: failed due to HW bug, retry pmp=0
[    2.596031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.596031] ata1.00: ATA-4: WDC WD136AA, 05.05B05, max UDMA/66
[    2.596031] ata1.00: 26564832 sectors, multi 16: LBA 
[    2.596031] ata1.00: applying bridge limits
[    2.596031] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.600031] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.600031] ata1.00: configured for UDMA/66
[    2.920031] ata2: SATA link down (SStatus 0 SControl 300)
[    3.240031] ata3: SATA link down (SStatus 0 SControl 300)
[    3.560031] ata4: SATA link down (SStatus 0 SControl 300)
[    3.560031] isa bounce pool size: 16 pages
[    3.560031] scsi 0:0:0:0: Direct-Access     ATA      WDC WD136AA      05.0 PQ: 0 ANSI: 5
[    3.560031] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.560031] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.560031] ohci_hcd 0000:00:13.0: irq 11, io mem 0xfe02e000
_____________________________________________________________________
[    3.620031] usb usb1: configuration #1 chosen from 1 choice
[    3.620031] hub 1-0:1.0: USB hub found
[    3.620031] hub 1-0:1.0: 2 ports detected
[    3.724031] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.724031] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.724031] ohci_hcd 0000:00:13.1: irq 11, io mem 0xfe02d000
[    3.784031] usb usb2: configuration #1 chosen from 1 choice
[    3.784031] hub 2-0:1.0: USB hub found
[    3.784031] hub 2-0:1.0: 2 ports detected
[    3.888031] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    3.888031] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.888031] ohci_hcd 0000:00:13.2: irq 11, io mem 0xfe02c000
[    3.948031] usb usb3: configuration #1 chosen from 1 choice
[    3.948031] hub 3-0:1.0: USB hub found
[    3.948031] hub 3-0:1.0: 2 ports detected
[    4.052031] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    4.052031] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    4.052031] ohci_hcd 0000:00:13.3: irq 11, io mem 0xfe02b000
[    4.112031] usb usb4: configuration #1 chosen from 1 choice
[    4.112031] hub 4-0:1.0: USB hub found
[    4.112031] hub 4-0:1.0: 2 ports detected
[    4.320031] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    4.320031] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    4.320031] ohci_hcd 0000:00:13.4: irq 11, io mem 0xfe02a000
[    4.380031] usb usb5: configuration #1 chosen from 1 choice
[    4.380031] hub 5-0:1.0: USB hub found
[    4.380031] hub 5-0:1.0: 2 ports detected
[    4.456031] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    4.484031] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    4.484031] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    4.484031] ehci_hcd 0000:00:13.5: debug port 1
[    4.484031] ehci_hcd 0000:00:13.5: irq 11, io mem 0xfe029000
[    4.496031] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.496031] usb usb6: configuration #1 chosen from 1 choice
[    4.496031] hub 6-0:1.0: USB hub found
[    4.496031] hub 6-0:1.0: 10 ports detected
[    4.704031] scsi4 : pata_atiixp
[    4.704031] scsi5 : pata_atiixp
[    4.704031] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    4.704031] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    5.068031] ata5.00: ATA-8: WDC WD5000AAJB-00YRA0, 12.01C02, max UDMA/100
[    5.068031] ata5.00: 976773168 sectors, multi 16: LBA48 
[    5.068031] ata5.01: ATAPI: SONY    CD-RW  CRX230EE, 2YS8, max UDMA/33
[    5.084031] ata5.00: configured for UDMA/100
[    5.116031] ata5.01: configured for UDMA/33
[    5.272031] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAJB-0 12.0 PQ: 0 ANSI: 5
[    5.272031] scsi 4:0:1:0: CD-ROM            SONY     CD-RW  CRX230EE  2YS8 PQ: 0 ANSI: 5
________________________________________________________________________________________________
[    5.284031] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.284031] eth0: RTL8169sc/8110sc at 0xffffc200008b8000, 00:19:21:47:c6:82, XID 18000000 IRQ 10
[    5.288031] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.288031] scsi 4:0:0:0: Attached scsi generic sg1 type 0
[    5.288031] scsi 4:0:1:0: Attached scsi generic sg2 type 5
[    5.380031] Driver 'sd' needs updating - please use bus_type methods
[    5.380031] sd 0:0:0:0: [sda] 26564832 512-byte hardware sectors (13601 MB)
[    5.380031] sd 0:0:0:0: [sda] Write Protect is off
[    5.380031] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.380031] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.380031] sd 0:0:0:0: [sda] 26564832 512-byte hardware sectors (13601 MB)
[    5.380031] sd 0:0:0:0: [sda] Write Protect is off
[    5.380031] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.380031] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.380031]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.408031]  sda1
[    5.408031] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.408031] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.408031] sd 4:0:0:0: [sdb] Write Protect is off
[    5.408031] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.408031] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.408031] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.408031] sd 4:0:0:0: [sdb] Write Protect is off
[    5.408031] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.408031] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
____________________________________________________________________________________
[    5.408031]  sdb:<3>hub 4-0:1.0: unable to enumerate USB device on port 1
[    5.412031]  sdb1 sdb2 < sdb5 sdb6 >
[    5.436031] sd 4:0:0:0: [sdb] Attached SCSI disk
[    5.444031] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    5.444031] Uniform CD-ROM driver Revision: 3.20
[    5.448031] sr 4:0:1:0: Attached scsi CD-ROM sr0
[    5.920031] usb 4-1: new full speed USB device using ohci_hcd and address 3
[    6.036031] loop: module loaded
[    6.072031] kjournald starting.  Commit interval 5 seconds
[    6.072031] EXT3-fs: mounted filesystem with ordered data mode.
[   11.400031] udevd version 124 started
[   12.080031] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.080031] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.168031] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xfa00, revision 0
[   12.332031] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   12.412031] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.428031] [fglrx] Maximum main memory to use for locked dma buffers: 1882 MBytes.
[   12.432031] [fglrx]   vendor: 1002 device: 7147 count: 1
[   12.432031] [fglrx] ioport: bar 4, base 0xee00, size: 0x100
[   12.432031] pci 0000:01:00.0: setting latency timer to 64
[   12.432031] [fglrx] PAT is enabled successfully!
[   12.432031] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   12.860031] spurious 8259A interrupt: IRQ7.
________________________________________________________________
[   13.212031] usb 4-1: configuration #1 chosen from 1 choice
[   14.232031] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x211f0009
[   14.496031] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   15.368031] irq 11: nobody cared (try booting with the "irqpoll" option)
[   15.368031] Pid: 2230, comm: modprobe Tainted: P          2.6.27-9-generic #1
[   15.368031] 
[   15.368031] Call Trace:
[   15.368031]  <IRQ>  [<ffffffff8029e91b>] __report_bad_irq+0x2b/0x90
[   15.368031]  [<ffffffff8029eab7>] note_interrupt+0x137/0x170
[   15.368031]  [<ffffffff8029f70d>] handle_level_irq+0x11d/0x140
[   15.368031]  [<ffffffff8021417c>] ? call_softirq+0x1c/0x30
[   15.368031]  [<ffffffff80215b16>] do_IRQ+0x86/0x100
[   15.368031]  [<ffffffff80212f0e>] ret_from_intr+0x0/0x29
[   15.368031]  <EOI>  [<ffffffff8034a30c>] ? __sysfs_add_one+0x7c/0xb0
[   15.368031]  [<ffffffff8034a2c9>] ? __sysfs_add_one+0x39/0xb0
[   15.368031]  [<ffffffff8034a49e>] ? sysfs_add_one+0x1e/0x60
[   15.368031]  [<ffffffff8034b593>] ? sysfs_do_create_link+0x113/0x170
[   15.368031]  [<ffffffff8034b623>] ? sysfs_create_link+0x13/0x20
[   15.368031]  [<ffffffff8042df44>] ? device_add+0x234/0x4b0
[   15.368031]  [<ffffffff8042cad0>] ? klist_children_put+0x0/0x20
[   15.368031]  [<ffffffff8042dd11>] ? device_add+0x1/0x4b0
[   15.368031]  [<ffffffff8042e1de>] ? device_register+0x1e/0x30
[   15.368031]  [<ffffffff8042e2de>] ? device_create_vargs+0xee/0x110
[   15.368031]  [<ffffffff8042e350>] ? device_create+0x50/0x60
[   15.368031]  [<ffffffffa01b9529>] ? snd_register_device_for_dev+0xb9/0x170 [snd]
[   15.368031]  [<ffffffffa01b9569>] ? snd_register_device_for_dev+0xf9/0x170 [snd]
[   15.368031]  [<ffffffffa041cec9>] ? snd_pcm_dev_register+0x119/0x270 [snd_pcm]
[   15.368031]  [<ffffffffa041cdb1>] ? snd_pcm_dev_register+0x1/0x270 [snd_pcm]
[   15.368031]  [<ffffffffa01bf719>] ? snd_device_register_all+0x39/0x60 [snd]
[   15.368031]  [<ffffffffa01ba22f>] ? snd_card_register+0x2f/0x170 [snd]
[   15.368031]  [<ffffffffa046c0c7>] ? azx_probe+0x12e/0x1a7 [snd_hda_intel]
[   15.368031]  [<ffffffff803bc100>] ? pci_device_probe+0xe0/0x140
[   15.368031]  [<ffffffff8034b623>] ? sysfs_create_link+0x13/0x20
[   15.368031]  [<ffffffff80430542>] ? really_probe+0x72/0x1a0
[   15.368031]  [<ffffffff804306c0>] ? driver_probe_device+0x50/0x60
[   15.368031]  [<ffffffff8043075b>] ? __driver_attach+0x8b/0x90
[   15.368031]  [<ffffffff804306d0>] ? __driver_attach+0x0/0x90
[   15.368031]  [<ffffffff8042fccb>] ? bus_for_each_dev+0x6b/0xa0
[   15.368031]  [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0
[   15.368031]  [<ffffffffa0099000>] ? alsa_card_azx_init+0x0/0x25 [snd_hda_intel]
[   15.368031]  [<ffffffff804303a1>] ? driver_attach+0x21/0x30
[   15.368031]  [<ffffffff8042f538>] ? bus_add_driver+0x1f8/0x270
[   15.368031]  [<ffffffffa0099000>] ? alsa_card_azx_init+0x0/0x25 [snd_hda_intel]
[   15.368031]  [<ffffffff80430955>] ? driver_register+0x75/0x170
[   15.368031]  [<ffffffffa0099000>] ? alsa_card_azx_init+0x0/0x25 [snd_hda_intel]
[   15.368031]  [<ffffffff803bc402>] ? __pci_register_driver+0x72/0xc0
[   15.368031]  [<ffffffffa0099000>] ? alsa_card_azx_init+0x0/0x25 [snd_hda_intel]
[   15.368031]  [<ffffffffa0099023>] ? alsa_card_azx_init+0x23/0x25 [snd_hda_intel]
[   15.368031]  [<ffffffff8020a041>] ? do_one_initcall+0x41/0x170
[   15.368031]  [<ffffffff8026c261>] ? __blocking_notifier_call_chain+0x21/0x90
[   15.368031]  [<ffffffff8027d085>] ? sys_init_module+0xb5/0x1f0
[   15.368031]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
[   15.368031] 
[   15.368031] handlers:
[   15.368031] [<ffffffffa00cd240>] (ahci_interrupt+0x0/0x114 [ahci])
[   15.368031] [<ffffffffa00a21a0>] (usb_hcd_irq+0x0/0xb0 [usbcore])
[   15.368031] [<ffffffffa00a21a0>] (usb_hcd_irq+0x0/0xb0 [usbcore])
[   15.368031] [<ffffffffa00a21a0>] (usb_hcd_irq+0x0/0xb0 [usbcore])
[   15.368031] [<ffffffffa00a21a0>] (usb_hcd_irq+0x0/0xb0 [usbcore])
[   15.368031] [<ffffffffa00a21a0>] (usb_hcd_irq+0x0/0xb0 [usbcore])
[   15.368031] [<ffffffffa00a21a0>] (usb_hcd_irq+0x0/0xb0 [usbcore])
[   15.368031] Disabling IRQ #11
[   16.184031] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   17.416031] usbcore: registered new interface driver libusual
[   17.428031] Initializing USB Mass Storage driver...
[   17.432031] scsi6 : SCSI emulation for USB Mass Storage devices
[   17.432031] usbcore: registered new interface driver usb-storage
[   17.432031] USB Mass Storage support registered.
[   17.432031] usb-storage: device found at 3
[   17.432031] usb-storage: waiting for device to settle before scanning
[   23.808031] irq 3: nobody cared (try booting with the "irqpoll" option)
[   23.808031] Pid: 0, comm: swapper Tainted: P          2.6.27-9-generic #1
[   23.808031] 
[   23.808031] Call Trace:
[   23.808031]  <IRQ>  [<ffffffff8029e91b>] __report_bad_irq+0x2b/0x90
[   23.808031]  [<ffffffff8029eab7>] note_interrupt+0x137/0x170
[   23.808031]  [<ffffffff8029f70d>] handle_level_irq+0x11d/0x140
[   23.808031]  [<ffffffff80215b16>] do_IRQ+0x86/0x100
[   23.808031]  [<ffffffff80212f0e>] ret_from_intr+0x0/0x29
[   23.808031]  <EOI>  [<ffffffff8022d226>] ? native_safe_halt+0x6/0x10
[   23.808031]  [<ffffffff8021ac35>] ? default_idle+0x55/0x60
[   23.808031]  [<ffffffff8021ac96>] ? c1e_idle+0x56/0x130
[   23.808031]  [<ffffffff8050588a>] ? atomic_notifier_call_chain+0x1a/0x20
[   23.808031]  [<ffffffff80210e95>] ? cpu_idle+0x75/0x110
[   23.808031]  [<ffffffff804f0536>] ? rest_init+0x66/0x70
[   23.808031] 
[   23.808031] handlers:
[   23.808031] [<ffffffffa044c690>] (azx_interrupt+0x0/0x180 [snd_hda_intel])
[   23.808031] Disabling IRQ #3
[   45.732031] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   45.732031] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[   45.732031]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
_____________________________________________________
[   45.732031] ata1.00: status: { DRDY }
[   45.732031] ata1: hard resetting link
[   46.496031] ata1: softreset failed (device not ready)
[   46.496031] ata1: failed due to HW bug, retry pmp=0
[   46.660031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   51.660031] ata1.00: qc timeout (cmd 0xec)
[   51.660031] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   51.660031] ata1.00: revalidation failed (errno=-5)
[   51.660031] ata1: hard resetting link
[   52.424031] ata1: softreset failed (device not ready)
[   52.424031] ata1: failed due to HW bug, retry pmp=0
[   52.588031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   62.588031] ata1.00: qc timeout (cmd 0xec)
[   62.588031] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   62.588031] ata1.00: revalidation failed (errno=-5)
[   62.588031] ata1: hard resetting link
[   63.352031] ata1: softreset failed (device not ready)
[   63.352031] ata1: failed due to HW bug, retry pmp=0
[   63.516031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   93.516031] ata1.00: qc timeout (cmd 0xec)
[   93.516031] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   93.516031] ata1.00: revalidation failed (errno=-5)
[   93.516031] ata1.00: disabled
[   93.516031] ata1: hard resetting link
[   95.008031] ata1: softreset failed (device not ready)
[   95.008031] ata1: failed due to HW bug, retry pmp=0
[   95.172031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   95.172031] ata1: EH complete
[   95.172031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[   95.172031] end_request: I/O error, dev sda, sector 0
[   95.172031] Buffer I/O error on device sda, logical block 0
[   95.172031] Buffer I/O error on device sda, logical block 1
[   95.172031] Buffer I/O error on device sda, logical block 2
[   95.172031] Buffer I/O error on device sda, logical block 3
[   95.172031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[   95.172031] end_request: I/O error, dev sda, sector 0
[   95.172031] Buffer I/O error on device sda, logical block 0
[   95.184031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[   95.184031] end_request: I/O error, dev sda, sector 63
[   95.184031] Buffer I/O error on device sda1, logical block 0
[   95.184031] Buffer I/O error on device sda1, logical block 1
[   95.184031] Buffer I/O error on device sda1, logical block 2
[   95.184031] Buffer I/O error on device sda1, logical block 3
[   95.184031] Buffer I/O error on device sda1, logical block 4
[   95.184031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[   95.184031] end_request: I/O error, dev sda, sector 63
[   95.184031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[   95.184031] end_request: I/O error, dev sda, sector 64
[   96.412031] parport0: PC-style at 0x378 [PCSPP,TRISTATE]
[   96.508031] lp0: using parport0 (polling).
[   97.220031] EXT3 FS on loop0, internal journal
[  106.296031] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[  106.440031] __ratelimit: 35 callbacks suppressed
[  106.440031] type=1505 audit(1228864897.172:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3631
[  106.612031] type=1505 audit(1228864897.344:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3636
[  106.612031] type=1505 audit(1228864897.344:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3636
[  106.752031] ip_tables: (C) 2000-2006 Netfilter Core Team
[  107.368031] powernow_k8: Unknown symbol acpi_processor_notify_smm
[  107.368031] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[  107.368031] powernow_k8: Unknown symbol acpi_processor_register_performance
[  107.400031] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  107.400031] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  107.400031] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  107.400031] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  108.068031] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  108.336031] ppdev: user-space parallel port driver
[  109.464031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.464031] end_request: I/O error, dev sda, sector 0
[  109.464031] Buffer I/O error on device sda, logical block 0
[  109.464031] Buffer I/O error on device sda, logical block 1
[  109.464031] Buffer I/O error on device sda, logical block 2
[  109.464031] Buffer I/O error on device sda, logical block 3
[  109.468031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.468031] end_request: I/O error, dev sda, sector 0
[  109.468031] Buffer I/O error on device sda, logical block 0
[  109.468031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.468031] end_request: I/O error, dev sda, sector 0
[  109.468031] Buffer I/O error on device sda, logical block 0
[  109.488031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.488031] end_request: I/O error, dev sda, sector 63
[  109.488031] Buffer I/O error on device sda1, logical block 0
[  109.488031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.488031] end_request: I/O error, dev sda, sector 84
[  109.488031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.488031] end_request: I/O error, dev sda, sector 85
[  109.488031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.488031] end_request: I/O error, dev sda, sector 63
[  109.492031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.492031] end_request: I/O error, dev sda, sector 0
[  109.492031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.492031] end_request: I/O error, dev sda, sector 8
[  109.492031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.492031] end_request: I/O error, dev sda, sector 0
[  109.492031] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  109.492031] end_request: I/O error, dev sda, sector 0
[  109.956031] Bluetooth: Core ver 2.13
[  109.960031] NET: Registered protocol family 31
[  109.960031] Bluetooth: HCI device and connection manager initialized
[  109.960031] Bluetooth: HCI socket layer initialized
[  109.980031] Bluetooth: L2CAP ver 2.11
[  109.980031] Bluetooth: L2CAP socket layer initialized
[  109.996031] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  109.996031] Bluetooth: BNEP filters: protocol multicast
[  110.032031] Bridge firewalling registered
[  110.032031] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  110.048031] Bluetooth: SCO (Voice Link) ver 0.6
[  110.048031] Bluetooth: SCO socket layer initialized
[  110.336031] Bluetooth: RFCOMM socket layer initialized
[  110.336031] Bluetooth: RFCOMM TTY layer initialized
[  110.336031] Bluetooth: RFCOMM ver 1.10
[  114.416031] r8169: eth0: link up
[  114.424031] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  114.424031] [fglrx] Reserved FB block: Unshared offset:ffb7000, size:44000 
[  114.424031] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[  114.672031] NET: Registered protocol family 17
[  218.150333] ppdev0: registered pardevice
[  218.198357] ppdev0: unregistered pardevice
[  218.266391] ppdev0: registered pardevice
[  218.314415] ppdev0: unregistered pardevice
[  220.387451] ppdev0: registered pardevice
[  220.439477] ppdev0: unregistered pardevice
bill@ubuntu:~$ 

dmesg

I have not,as yet,  downloaded the alternate ISO.

---

### Post by jasdparker on 2008-12-10
I am having a similar problem in Ubuntu 8.04.

I do not dual boot as you do.  I installed Hardy on my entire hard drive.  When I first installed it, my usb hard drive showed up just fine.

I only noticed in the last few weeks that it has disappeared.  Running sudo fdisk doesn't even show my device listed.  It only shows my internal hard drives.

If anyone can help, that would be wonderful.

Thanks in advance.

---

