---
title: "CD-Rom Not Showing Up"
date: 2010-10-24
forum: Hardware
---

### Post by dragune185 on 2010-10-24
Hello everyone I recently switched over to Ubuntu 10.04 and have been loving every second of it. I didn't have any issues until recently when a friend of mine asked me to play a game with him. I of course wasn't dual booting but I found an install CD and everything. The only issue now is that my CD-Rom does not appear to be working. 

I have tried: 

```
dmesg|more
```in hopes that I could find where the CD-ROM was. That returned no results that i could tell were helpful. 

I even tried mounting the CD-ROM. But i could not find the "dev" file where the CD-ROM is. 

```
leonkennedy@Leon-Laptop:~$ sudo mount /dev/pkcdvd /media/CD
mount: special device /dev/pkcdvd does not exist
leonkennedy@Leon-Laptop:~$ sudo mount /dev/pktcdvd /media/CD
mount: /dev/pktcdvd is not a block device
leonkennedy@Leon-Laptop:~$ sudo mount /dev/disk /media/CD
mount: /dev/disk is not a block device
leonkennedy@Leon-Laptop:~$ mkdir /media/CD
mkdir: cannot create directory `/media/CD': File exists
leonkennedy@Leon-Laptop:~$ sudo mount /dev/cdrom0 /media/CD
mount: special device /dev/cdrom0 does not exist
leonkennedy@Leon-Laptop:~$ sudo mount /dev/cdrom1 /media/CD
mount: special device /dev/cdrom1 does not exist
leonkennedy@Leon-Laptop:~$ sudo mount /dev/cdrom /media/CD
mount: special device /dev/cdrom does not exist
leonkennedy@Leon-Laptop:~$ 
 
```I even tried make the directory and these were my results. I would post the dmesg file but I think that's it's a little big and I didn't see a spoiler option when posting. 

I restart my computer and try to boot from the CD, and it's not even on the list of places to boot. 

I had an experience with my USB not showing up, but it was still listed in the "Disk Utility" and I could at least adjust things there and got it to working however I can't seem to find it on the computer. 

I am curious if there is another series of code I could possible use to have Ubuntu 10.04 actually recognize my CD-ROM. (I have searched this forum, and the rest of the internet but none of those solutions were working.)

I am using a Toshiba a205-S5748 with no hardware upgrades. 


I thank you for the time.

---

### Post by dragune185 on 2010-10-24
```
leonkennedy@Leon-Laptop:~$ cd /media
leonkennedy@Leon-Laptop:/media$ ls
9A5CF3CF5CF3A463  CD
leonkennedy@Leon-Laptop:/media$ sudo mount CD
[sudo] password for leonkennedy: 
mount: can't find CD in /etc/fstab or /etc/mtab
leonkennedy@Leon-Laptop:/media$ 

```

So after a little bit more searching I came across these few commands. Here is what I get when I try those. Any suggestions on what to try next would be most appreciated.

---

### Post by dragune185 on 2010-10-24
Did a bit more googling all day and tried various things. 

I thought maybe having my dmesg output would be useful. 

```
[    0.323107] pci 0000:0c:04.0:   MEM window: 0x88000000-0x8bffffff
[    0.323114] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0c
[    0.323118] pci 0000:00:1e.0:   IO window: 0x7000-0x7fff
[    0.323126] pci 0000:00:1e.0:   MEM window: 0xfc200000-0xfc2fffff
[    0.323132] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.323158]   alloc irq_desc for 17 on node -1
[    0.323161]   alloc kstat_irqs on node -1
[    0.323170] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.323177] pci 0000:00:1c.0: setting latency timer to 64
[    0.323190]   alloc irq_desc for 16 on node -1
[    0.323192]   alloc kstat_irqs on node -1
[    0.323196] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.323203] pci 0000:00:1c.1: setting latency timer to 64
[    0.323216]   alloc irq_desc for 18 on node -1
[    0.323218]   alloc kstat_irqs on node -1
[    0.323223] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.323229] pci 0000:00:1c.2: setting latency timer to 64
[    0.323241]   alloc irq_desc for 19 on node -1
[    0.323244]   alloc kstat_irqs on node -1
[    0.323248] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.323254] pci 0000:00:1c.3: setting latency timer to 64
[    0.323267] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.323274] pci 0000:00:1c.4: setting latency timer to 64
[    0.323285] pci 0000:00:1e.0: setting latency timer to 64
[    0.323300] pci 0000:0c:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.323308] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.323311] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.323315] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.323318] pci_bus 0000:02: resource 1 mem: [0xf0000000-0xf3ffffff]
[    0.323321] pci_bus 0000:02: resource 2 pref mem [0xce000000-0xcfffffff]
[    0.323325] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.323328] pci_bus 0000:04: resource 1 mem: [0xf4000000-0xf7ffffff]
[    0.323331] pci_bus 0000:04: resource 2 pref mem [0xcc000000-0xcdffffff]
[    0.323334] pci_bus 0000:05: resource 0 io:  [0x4000-0x4fff]
[    0.323337] pci_bus 0000:05: resource 1 mem: [0xf8000000-0xfbffffff]
[    0.323340] pci_bus 0000:05: resource 2 pref mem [0xca000000-0xcbffffff]
[    0.323343] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.323346] pci_bus 0000:06: resource 1 mem: [0xc4000000-0xc7ffffff]
[    0.323350] pci_bus 0000:06: resource 2 pref mem [0xc8000000-0xc9ffffff]
[    0.323353] pci_bus 0000:09: resource 0 io:  [0x6000-0x6fff]
[    0.323356] pci_bus 0000:09: resource 1 mem: [0x84000000-0x841fffff]
[    0.323359] pci_bus 0000:09: resource 2 pref mem [0x84200000-0x843fffff]
[    0.323362] pci_bus 0000:0c: resource 0 io:  [0x7000-0x7fff]
[    0.323365] pci_bus 0000:0c: resource 1 mem: [0xfc200000-0xfc2fffff]
[    0.323368] pci_bus 0000:0c: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.323371] pci_bus 0000:0c: resource 3 io:  [0x00-0xffff]
[    0.323374] pci_bus 0000:0c: resource 4 mem: [0x000000-0xffffffff]
[    0.323377] pci_bus 0000:0d: resource 0 io:  [0x7000-0x70ff]
[    0.323380] pci_bus 0000:0d: resource 1 io:  [0x7400-0x74ff]
[    0.323383] pci_bus 0000:0d: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.323386] pci_bus 0000:0d: resource 3 mem: [0x88000000-0x8bffffff]
[    0.323463] NET: Registered protocol family 2
[    0.323589] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.324060] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.324692] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.325091] TCP: Hash tables configured (established 131072 bind 65536)
[    0.325095] TCP reno registered
[    0.325346] NET: Registered protocol family 1
[    0.325382] pci 0000:00:02.0: Boot video device
[    0.325590] Simple Boot Flag at 0x36 set to 0x1
[    0.325945] cpufreq-nforce2: No nForce2 chipset.
[    0.325979] Scanning for low memory corruption every 60 seconds
[    0.326109] audit: initializing netlink socket (disabled)
[    0.326124] type=2000 audit(1287963275.323:1): initialized
[    0.337807] highmem bounce pool size: 64 pages
[    0.337814] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.339738] VFS: Disk quotas dquot_6.5.2
[    0.339826] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.340524] fuse init (API version 7.13)
[    0.340631] msgmni has been set to 1690
[    0.340918] alg: No test for stdrng (krng)
[    0.340994] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.340998] io scheduler noop registered
[    0.341000] io scheduler anticipatory registered
[    0.341002] io scheduler deadline registered
[    0.341049] io scheduler cfq registered (default)
[    0.341278]   alloc irq_desc for 24 on node -1
[    0.341281]   alloc kstat_irqs on node -1
[    0.341296] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.341310] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.341502]   alloc irq_desc for 25 on node -1
[    0.341504]   alloc kstat_irqs on node -1
[    0.341515] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.341528] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.341713]   alloc irq_desc for 26 on node -1
[    0.341715]   alloc kstat_irqs on node -1
[    0.341726] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.341739] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.341928]   alloc irq_desc for 27 on node -1
[    0.341931]   alloc kstat_irqs on node -1
[    0.341941] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.341954] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.342137]   alloc irq_desc for 28 on node -1
[    0.342139]   alloc kstat_irqs on node -1
[    0.342149] pcieport 0000:00:1c.4: irq 28 for MSI/MSI-X
[    0.342162] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.342294] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.342490] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.342658] ACPI: AC Adapter [ACAD] (on-line)
[    0.342736] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.342782] ACPI: Lid Switch [LID0]
[    0.342837] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.342841] ACPI: Power Button [PWRB]
[    0.342913] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.342916] ACPI: Power Button [PWRF]
[    0.343786] ACPI: SSDT 7f6d87ca 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.344416] ACPI: SSDT 7f6d82ba 0048B (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.347304] Monitor-Mwait will be used to enter C-1 state
[    0.347342] Monitor-Mwait will be used to enter C-2 state
[    0.347350] Marking TSC unstable due to TSC halts in idle
[    0.347434] processor LNXCPU:00: registered as cooling_device0
[    0.347820] Switching to clocksource hpet
[    0.350307] ACPI: SSDT 7f6d8a02 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.350765] ACPI: SSDT 7f6d8745 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.357266] processor LNXCPU:01: registered as cooling_device1
[    0.382331] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.383994] brd: module loaded
[    0.384601] loop: module loaded
[    0.384723] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.384856] ata_piix 0000:00:1f.1: version 2.13
[    0.384880] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.384939] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.385056] scsi0 : ata_piix
[    0.385152] scsi1 : ata_piix
[    0.385893] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.385897] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.386324] Fixed MDIO Bus: probed
[    0.386369] PPP generic driver version 2.4.2
[    0.386424] tun: Universal TUN/TAP device driver, 1.6
[    0.386426] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.386534] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.386564] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.386594] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.386599] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.386642] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.386680] ehci_hcd 0000:00:1a.7: debug port 1
[    0.390559] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.390581] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc504800
[    0.394576] isapnp: Scanning for PnP cards...
[    0.410227] Freeing initrd memory: 7776k freed
[    0.417054] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.417324] usb usb1: configuration #1 chosen from 1 choice
[    0.417361] hub 1-0:1.0: USB hub found
[    0.417374] hub 1-0:1.0: 4 ports detected
[    0.417464]   alloc irq_desc for 23 on node -1
[    0.417467]   alloc kstat_irqs on node -1
[    0.417475] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.417506] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.417510] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.417557] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.417595] ehci_hcd 0000:00:1d.7: debug port 1
[    0.421472] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.421495] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504c00
[    0.437017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.437110] usb usb2: configuration #1 chosen from 1 choice
[    0.437141] hub 2-0:1.0: USB hub found
[    0.437150] hub 2-0:1.0: 6 ports detected
[    0.437233] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.437257] uhci_hcd: USB Universal Host Controller Interface driver
[    0.437305] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.437315] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.437319] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.437357] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.437400] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.437505] usb usb3: configuration #1 chosen from 1 choice
[    0.437538] hub 3-0:1.0: USB hub found
[    0.437546] hub 3-0:1.0: 2 ports detected
[    0.437601]   alloc irq_desc for 21 on node -1
[    0.437603]   alloc kstat_irqs on node -1
[    0.437610] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.437618] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.437622] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.437660] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.437700] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.437808] usb usb4: configuration #1 chosen from 1 choice
[    0.437838] hub 4-0:1.0: USB hub found
[    0.437846] hub 4-0:1.0: 2 ports detected
[    0.437903] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.437911] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.437915] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.437951] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.437982] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.438092] usb usb5: configuration #1 chosen from 1 choice
[    0.438121] hub 5-0:1.0: USB hub found
[    0.438129] hub 5-0:1.0: 2 ports detected
[    0.438182] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.438190] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.438194] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.438233] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.438275] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.438388] usb usb6: configuration #1 chosen from 1 choice
[    0.438417] hub 6-0:1.0: USB hub found
[    0.438425] hub 6-0:1.0: 2 ports detected
[    0.438480] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.438487] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.438492] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.438533] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.438564] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.438671] usb usb7: configuration #1 chosen from 1 choice
[    0.438700] hub 7-0:1.0: USB hub found
[    0.438708] hub 7-0:1.0: 2 ports detected
[    0.438826] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.467922] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.467930] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.468028] mice: PS/2 mouse device common for all mice
[    0.468174] rtc_cmos 00:07: RTC can wake from S4
[    0.468220] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.468256] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.468378] device-mapper: uevent: version 1.0.3
[    0.468502] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.468577] device-mapper: multipath: version 1.1.0 loaded
[    0.468581] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.468712] EISA: Probing bus 0 at eisa.0
[    0.468720] Cannot allocate resource for EISA slot 1
[    0.468724] Cannot allocate resource for EISA slot 2
[    0.468726] Cannot allocate resource for EISA slot 3
[    0.468729] Cannot allocate resource for EISA slot 4
[    0.468731] Cannot allocate resource for EISA slot 5
[    0.468734] Cannot allocate resource for EISA slot 6
[    0.468736] Cannot allocate resource for EISA slot 7
[    0.468743] EISA: Detected 0 cards.
[    0.468894] cpuidle: using governor ladder
[    0.469012] cpuidle: using governor menu
[    0.469558] TCP cubic registered
[    0.469738] NET: Registered protocol family 10
[    0.470301] lo: Disabled Privacy Extensions
[    0.470718] NET: Registered protocol family 17
[    0.471388] Using IPI No-Shortcut mode
[    0.471491] PM: Resume from disk failed.
[    0.471507] registered taskstats version 1
[    0.472195]   Magic number: 14:299:606
[    0.472238] acpi TOS1900:00: hash matches
[    0.472297] rtc_cmos 00:07: setting system clock to 2010-10-24 23:34:36 UTC (1287963276)
[    0.472301] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.472303] EDD information not available.
[    0.539354] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.581833] ACPI: Battery Slot [BAT1] (battery present)
[    0.749296] isapnp: No Plug & Play device found
[    0.749337] Freeing unused kernel memory: 656k freed
[    0.749834] Write protecting the kernel text: 4684k
[    0.749897] Write protecting the kernel read-only data: 1840k
[    0.772049] udev: starting version 151
[    0.868952] ahci 0000:00:1f.2: version 3.0
[    0.868978] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.869041]   alloc irq_desc for 29 on node -1
[    0.869044]   alloc kstat_irqs on node -1
[    0.869058] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.869150] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    0.869154] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    0.869161] ahci 0000:00:1f.2: setting latency timer to 64
[    0.869563] scsi2 : ahci
[    0.874205] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.874236] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.874302] r8169 0000:04:00.0: setting latency timer to 64
[    0.874396]   alloc irq_desc for 30 on node -1
[    0.874399]   alloc kstat_irqs on node -1
[    0.874420] r8169 0000:04:00.0: irq 30 for MSI/MSI-X
[    0.875254] eth0: RTL8101e at 0xf80e6000, 00:1e:ec:33:50:ff, XID 94200000 IRQ 30
[    0.880056] scsi3 : ahci
[    0.893612] ohci1394 0000:0c:04.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.913276] scsi4 : ahci
[    0.913487] ata3: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 29
[    0.913492] ata4: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 29
[    0.913497] ata5: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504200 irq 29
[    0.948130] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fc206000-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    0.961042] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.106376] usb 1-3: configuration #1 chosen from 1 choice
[    1.232050] ata4: SATA link down (SStatus 0 SControl 300)
[    1.232079] ata5: SATA link down (SStatus 0 SControl 300)
[    1.332044] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    1.466409] usb 2-5: configuration #1 chosen from 1 choice
[    1.475225] Initializing USB Mass Storage driver...
[    1.475402] scsi5 : SCSI emulation for USB Mass Storage devices
[    1.475512] usbcore: registered new interface driver usb-storage
[    1.475515] USB Mass Storage support registered.
[    1.475522] usb-storage: device found at 3
[    1.475524] usb-storage: waiting for device to settle before scanning
[    1.512055] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.512701] ACPI Warning for \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    1.512711] ata3.00: _GTF unexpected object type 0x1
[    1.704027] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.886144] usb 5-1: configuration #1 chosen from 1 choice
[    1.900537] usbcore: registered new interface driver hiddev
[    1.904355] input: SONiX Targus Soft-Touch Cordless Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input5
[    1.904474] generic-usb 0003:4168:1004.0001: input,hidraw0: USB HID v1.00 Mouse [SONiX Targus Soft-Touch Cordless Mouse] on usb-0000:00:1d.0-1/input0
[    1.908122] input: SONiX Targus Soft-Touch Cordless Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input6
[    1.908193] generic-usb 0003:4168:1004.0002: input,hidraw1: USB HID v1.00 Device [SONiX Targus Soft-Touch Cordless Mouse] on usb-0000:00:1d.0-1/input1
[    1.908222] usbcore: registered new interface driver usbhid
[    1.908225] usbhid: v2.6:USB HID core driver
[    1.930532] ata3.00: ATA-8: TOSHIBA MK1246GSX, LB213M, max UDMA/100
[    1.930536] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.931549] ata3.00: _GTF unexpected object type 0x1
[    1.931759] ata3.00: configured for UDMA/100
[    1.944157] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1246GS LB21 PQ: 0 ANSI: 5
[    1.944340] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.944470] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.944525] sd 2:0:0:0: [sda] Write Protect is off
[    1.944528] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.944556] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.944717]  sda: sda1 sda2 < sda5 >
[    2.012174] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.224159] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f83ad41a585]
[    2.343229] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.343234] EXT4-fs (sda1): write access will be enabled during recovery
[    6.332504] EXT4-fs (sda1): orphan cleanup on readonly fs
[    6.332515] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 394258
[    6.332595] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 394254
[    6.332620] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 394249
[    6.332641] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 394245
[    6.332661] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 394241
[    6.332681] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 394239
[    6.332704] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 394228
[    6.332766] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262169
[    6.332828] EXT4-fs (sda1): 8 orphan inodes deleted
[    6.332832] EXT4-fs (sda1): recovery complete
[    6.472256] usb-storage: device scan complete
[    6.472823] scsi 5:0:0:0: Direct-Access     USB      DISK 2.0         1.00 PQ: 0 ANSI: 2
[    6.473326] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    6.474193] sd 5:0:0:0: [sdb] 8017920 512-byte logical blocks: (4.10 GB/3.82 GiB)
[    6.474812] sd 5:0:0:0: [sdb] Write Protect is off
[    6.474817] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    6.474820] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    6.477050] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    6.477056]  sdb: sdb1
[    6.480821] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    6.480826] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    6.651895] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   16.931779] udev: starting version 151
[   17.034828] Adding 4805624k swap on /dev/sda5.  Priority:-1 extents:1 across:4805624k 
[   17.364383] type=1505 audit(1287963293.391:2):  operation="profile_load" pid=608 name="/sbin/dhclient3"
[   17.365248] type=1505 audit(1287963293.391:3):  operation="profile_load" pid=608 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.365681] type=1505 audit(1287963293.391:4):  operation="profile_load" pid=608 name="/usr/lib/connman/scripts/dhclient-script"
[   17.523593] Linux video capture interface: v2.00
[   17.525350] tifm_7xx1 0000:0c:04.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   17.537474] Linux agpgart interface v0.103
[   17.556449] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   17.560987] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input7
[   17.561267] usbcore: registered new interface driver uvcvideo
[   17.561557] USB Video Class driver (v0.1.0)
[   17.629159] lp: driver loaded but no devices found
[   17.644682] cfg80211: Calling CRDA to update world regulatory domain
[   17.647423] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   17.647819] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   17.655738] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   17.658463] sdhci: Secure Digital Host Controller Interface driver
[   17.658467] sdhci: Copyright(c) Pierre Ossman
[   17.659059] yenta_cardbus 0000:0c:04.0: CardBus bridge found [1179:ff00]
[   17.659086] yenta_cardbus 0000:0c:04.0: Enabling burst memory read transactions
[   17.659094] yenta_cardbus 0000:0c:04.0: Using CSCINT to route CSC interrupts to PCI
[   17.659097] yenta_cardbus 0000:0c:04.0: Routing CardBus interrupts to PCI
[   17.659105] yenta_cardbus 0000:0c:04.0: TI: mfunc 0x10a01b22, devctl 0x64
[   17.732412] [drm] Initialized drm 1.1.0 20060810
[   17.743267] cfg80211: World regulatory domain updated:
[   17.743273]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.743276]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.743280]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.743283]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.743286]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.743289]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.888796] yenta_cardbus 0000:0c:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   17.888802] yenta_cardbus 0000:0c:04.0: Socket status: 30000006
[   17.888807] pci_bus 0000:0c: Raising subordinate bus# of parent bus (#0c) from #0d to #10
[   17.888819] yenta_cardbus 0000:0c:04.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0x7fff
[   17.888824] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: clean.
[   17.889107] yenta_cardbus 0000:0c:04.0: pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   17.889111] yenta_cardbus 0000:0c:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   17.889482] sdhci-pci 0000:0c:04.3: SDHCI controller found [104c:803c] (rev 0)
[   17.889505] sdhci-pci 0000:0c:04.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   17.889617] Registered led device: mmc0::
[   17.889664] mmc0: SDHCI controller on PCI [0000:0c:04.3] using DMA
[   18.170590] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.170598] i915 0000:00:02.0: setting latency timer to 64
[   18.176094]   alloc irq_desc for 31 on node -1
[   18.176099]   alloc kstat_irqs on node -1
[   18.176111] i915 0000:00:02.0: irq 31 for MSI/MSI-X
[   18.176121] [drm] set up 7M of stolen space
[   18.234720] ath5k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.234736] ath5k 0000:05:00.0: setting latency timer to 64
[   18.234785] ath5k 0000:05:00.0: registered as 'phy0'
[   18.339100] [drm] initialized overlay support
[   18.602475] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   18.618931] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   18.621341] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.622340] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   18.623168] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   18.624221] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.650753] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   18.745647] ath: EEPROM regdomain: 0x65
[   18.745651] ath: EEPROM indicates we should expect a direct regpair map
[   18.745655] ath: Country alpha2 being used: 00
[   18.745657] ath: Regpair used: 0x65
[   18.775094] type=1505 audit(1287963294.799:5):  operation="profile_load" pid=796 name="/usr/share/gdm/guest-session/Xsession"
[   18.777299] type=1505 audit(1287963294.803:6):  operation="profile_replace" pid=797 name="/sbin/dhclient3"
[   18.778108] type=1505 audit(1287963294.803:7):  operation="profile_replace" pid=797 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.778542] type=1505 audit(1287963294.803:8):  operation="profile_replace" pid=797 name="/usr/lib/connman/scripts/dhclient-script"
[   18.782939] type=1505 audit(1287963294.807:9):  operation="profile_load" pid=798 name="/usr/bin/evince"
[   18.793273] type=1505 audit(1287963294.819:10):  operation="profile_load" pid=798 name="/usr/bin/evince-previewer"
[   18.799596] type=1505 audit(1287963294.823:11):  operation="profile_load" pid=798 name="/usr/bin/evince-thumbnailer"
[   18.932603] phy0: Selected rate control algorithm 'minstrel'
[   18.933515] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   18.959477] fb0: inteldrmfb frame buffer device
[   18.959481] registered panic notifier
[   18.972469] acpi device:08: registered as cooling_device2
[   18.973829] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input10
[   18.973991] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.974125] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.052416] r8169: eth0: link down
[   19.052672] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.129687] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.246681] vga16fb: initializing
[   19.246686] vga16fb: mapped to 0xc00a0000
[   19.246692] vga16fb: not registering due to another framebuffer present
[   19.441982] Console: switching to colour frame buffer device 160x50
[   19.445012] ppdev: user-space parallel port driver
[   19.487527]   alloc irq_desc for 22 on node -1
[   19.487531]   alloc kstat_irqs on node -1
[   19.487540] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.487598] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.747756] hda_codec: ALC268: BIOS auto-probing.
[   19.748282] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[  117.691986] wlan0: direct probe to AP 00:1c:df:ca:ec:83 (try 1)
[  117.692053] wlan0: deauthenticating from 00:1c:df:ca:ec:83 by local choice (reason=3)
[  117.692110] wlan0: direct probe to AP 00:1c:df:ca:ec:83 (try 1)
[  117.697334] wlan0: direct probe responded
[  117.697340] wlan0: authenticate with AP 00:1c:df:ca:ec:83 (try 1)
[  117.704025] wlan0: authenticated
[  117.704054] wlan0: associate with AP 00:1c:df:ca:ec:83 (try 1)
[  117.707218] wlan0: RX AssocResp from 00:1c:df:ca:ec:83 (capab=0x411 status=0 aid=1)
[  117.707222] wlan0: associated
[  117.707976] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```Also fstab output:

```
leon@leon-laptop:~$ cat /etc/fstab /etc/mtab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9c4bda09-1cb1-4aae-b111-e4436c76ce54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=53af77f0-27b1-4603-86d6-6f1fff792e17 none            swap    sw              0       0

/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/leon/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=leon 0 0
/dev/sdb1 /media/EA5A-A4E0 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0

```If there is any more information that I can post that would help I will gladly oblige. I am not the most experienced in Linux and Ubuntu.

---

### Post by 3bananas4 on 2010-10-27
had this problem as well on two machines - desktop and laptop. attempted every fix under the sun suggested in the various threads on here and elsewhere to no avail. 

I came across a workaround by chance which resurrected my cd/dvd drives on both machines, namely, to kill the session abruptly rather than shutting down, suspending or logging off. 

For the laptop this was simply a case of letting the session die when the battery ran out, for the desktop it was the even simpler job of yanking the power lead. For both machines, when they were juiced up again, the new session had the drives mounted. Simples.

If it's of any use to anyone reading this, this problem appeared at the same time on both machines and directly after setting them up in a LAN using NTS.

---

