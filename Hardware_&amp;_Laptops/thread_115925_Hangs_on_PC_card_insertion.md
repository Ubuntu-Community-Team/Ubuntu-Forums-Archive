---
title: "Hangs on PC card insertion"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by qopax on 2006-01-11
I've been trying to solve this problem for days but considering I'm fairly new to linux, I've had very little success.

I have a Gateway Solo 3150 laptop and a wg511 wifi card. Every time I plug it in, the system will freeze until I take the card out, and the laptop resumes whatever it's been doing prior to the insertion. I've just installed linux on it, Xubuntu specifically (which I must say is running damn swiftly on my 366mhz cpu with 190mb ram), so I don't have much of anything installed yet. I'm pretty sure it freezes on the Ubuntu Live-CD as well, so it doesn't seem to be an issue with xfce.

I read a lot about problems with this wifi card, but not much about my issue. I'm pretty sure it's the prism chipset, since it's "made in taiwan" and says v2.0 in extremely small print in the back, plus the serial starts with wg551. It worked perfectly in Windows so it's not a hardware problem.

Google turned up something about having to recompile the kernel with certain drivers, which I only did once, in Gentoo, but I have no idea how to do it in Ubuntu/Debian. I haven't had much success finding a tutorial for Ubuntu, specifically without using Gnome, and I don't even know what drivers/patches would fix my problem. I also don't have any other PC cards, so I have no idea whether this is a particular problem of the wg511, or something having to do with the PCMCIA slot.

I will try downloading Knoppix and see whether the card works with that, and will report back the chipset if it does. Also, I've heard the prism chipset is supported by default in Ubuntu, so any wifi card using it would work out of the box. Is that true?

I greatly appreciate any help or suggestions I can get.

---

### Post by qopax on 2006-01-12
So no one has any idea of what could be causing this problem and how I might solve it?

I tried running knoppix 4.0.2, but it gave me a bunch of hdc errors for some reason. hdc is probably the cdrom drive right? So maybe it's just a bad disc?

I'm going to try burning another copy today. I really would like to use ubuntu, but what's a laptop without wireless access? Might as well use windows.

---

### Post by qopax on 2006-01-12
Ok, the 2nd knoppix cd worked. More accurately, it even connected to the internet on bootup. It says prism gt/duette in lspci, so I assume that it is the prism chipset in my wg511, though it also says rev 01, so I'm not sure whether that means that the card is v1, even though it says v2.0 in very small print on the back, but I guess that makes no difference if the chipset is still prism. 


Still have no idea what to do about ubuntu though. I tried installing linux-wlan-ng since that seems to be for prism2 cards, even though I have no idea whether mine is prism2. I noticed that knoppix used cardmgr in bootup, which, after it was loaded, caused my wifi card to start functioning/blinking. I tried apt-cache search for it, but ubuntu can't seem to find anythng. Is there anything compared to it?

It also seems to hang at hotplug during boot if I don't take it out(it goes along quite happily right after I take out the card though), an issue some other people have been experiencing, so I'll look into that.

I'd use knoppix, but it's way too bloated, and isn't anywhere as simple, clean, and lightweight as Ubuntu(xubuntu), especially for my mom who will be using it.

---

### Post by Lambert on 2006-01-13
After trying to insert the card and removing it what is the output of the command dmesg? Also look in /var/log/syslog for any output.

Also if it's a prismgt chipset it will use the prism54 driver and not linux-wlan-ng driver.

---

### Post by qopax on 2006-01-14
Ok, I removed linux-wlan-ng. Where do I find the prism54 driver, or is it installed on ubuntu be default like I heard? It doesn't seem to be in the repositories.

I installed Ubuntu 'server' though, followed by xubuntu-desktop. I assume most of the hardware capabilities are identical, just the package set is different?

Could it be a faulty install of Ubuntu? Considering Knoppix didn't work the first time I burned it, could something like that have happened?

The output of dmesg doesn't seem to differ after and before I insert the card. It doesn't seem that syslog has anything either. I'll post both anyways if it helps.


roman@solo3150:~$ cat /var/log/syslog
Jan 13 23:38:37 localhost syslogd 1.4.1#17ubuntu3: restart.
Jan 13 23:38:37 localhost anacron[6219]: Job `cron.daily' terminated
Jan 13 23:38:37 localhost anacron[6219]: Normal exit (1 job run)
Jan 13 23:42:54 localhost nagios: SERVICE ALERT: gw;PING;CRITICAL;SOFT;1;CRITICAL - Plugin timed out after 10 seconds
Jan 13 23:43:44 localhost nagios: SERVICE ALERT: gw;PING;OK;SOFT;2;PING OK - Packet loss = 0%, RTA = 0.70 ms
Jan 13 23:58:41 localhost -- MARK --
Jan 14 00:00:00 localhost nagios: LOG ROTATION: DAILY


roman@solo3150:~$ dmesg
[4294667.296000] Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 11:37:10 UTC 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0df4 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000009ffbc00 (usable)
[4294667.296000]  BIOS-e820: 0000000009ffbc00 - 0000000009fffc00 (ACPI data)
[4294667.296000]  BIOS-e820: 0000000009fffc00 - 000000000a000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000ffff0df4 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 159MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 40955
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 36859 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.1 present.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000fd890
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000000 PTL  0x01000000) @ 0x09ffbc00
[4294667.296000] ACPI: FADT (v001 GATEWA PROFILE  0x00000001 PTL  0x20373031) @ 0x09ffbc28
[4294667.296000] ACPI: DSDT (v001 QUANTA SQ2_3.10 0x00000000 MSFT 0x01000007) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x8008
[4294667.296000] Allocating PCI resources starting at 0a000000 (gap: 0a000000:f5ff0df4)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01141000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 367.630 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.619000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.620000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.652000] Memory: 153988k/163820k available (1416k kernel code, 9304k reserved, 762k data, 224k init, 0k highmem)
[4294670.652000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.652000] Calibrating delay loop... 727.04 BogoMIPS (lpj=363520)
[4294670.673000] Security Framework v1.0.0 initialized
[4294670.673000] SELinux:  Disabled at boot.
[4294670.673000] Mount-cache hash table entries: 512
[4294670.673000] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.673000] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.673000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294670.673000] CPU: L2 cache: 256K
[4294670.673000] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294670.673000] CPU: Intel Mobile Pentium II stepping 0a
[4294670.673000] Enabling fast FPU save and restore... done.
[4294670.673000] Checking 'hlt' instruction... OK.
[4294670.677000] Checking for popad bug... OK.
[4294670.677000] checking if image is initramfs... it is
[4294672.847000] Freeing initrd memory: 5141k freed
[4294672.851000] ACPI: Looking for DSDT in initrd... not found!
[4294673.180000]  not found!
[4294673.211000] ACPI: setting ELCR to 0200 (from 0c00)
[4294673.217000] NET: Registered protocol family 16
[4294673.217000] EISA bus registered
[4294673.217000] ACPI: bus type pci registered
[4294673.218000] PCI: PCI BIOS revision 2.10 entry at 0xf512d, last bus=0
[4294673.218000] PCI: Using configuration type 1
[4294673.218000] mtrr: v2.0 (20020519)
[4294673.220000] ACPI: Subsystem revision 20050729
[4294673.290000] ACPI: Interpreter enabled
[4294673.290000] ACPI: Using PIC for interrupt routing
[4294673.293000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[4294673.295000] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[4294673.298000] ACPI: PCI Interrupt Link [LNKD] (IRQs *10)
[4294673.302000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294673.302000] PCI: Probing PCI hardware (bus 00)
[4294673.304000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294673.369000] Boot video device is 0000:00:02.0
[4294673.373000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294673.374000] burst-mode-ec-10-Aug
[4294673.374000] ACPI: Embedded Controller [EC0] (gpe 9)
[4294673.496000] ACPI: Power Resource [PFAN] (off)
[4294673.497000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294673.497000] pnp: PnP ACPI init
[4294673.624000] pnp: PnP ACPI: found 15 devices
[4294673.624000] PnPBIOS: Disabled by ACPI PNP
[4294673.624000] PCI: Using ACPI for IRQ routing
[4294673.624000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294673.630000] pnp: 00:0c: ioport range 0x372-0x373 has been reserved
[4294673.630000] pnp: 00:0c: ioport range 0x398-0x399 has been reserved
[4294673.630000] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[4294673.630000] pnp: 00:0c: ioport range 0x279-0x279 has been reserved
[4294673.630000] pnp: 00:0c: ioport range 0xa79-0xa79 has been reserved
[4294673.632000] audit: initializing netlink socket (disabled)
[4294673.632000] audit: initialized
[4294673.633000] VFS: Disk quotas dquot_6.5.1
[4294673.633000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294673.633000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294673.633000] devfs: boot_options: 0x0
[4294673.633000] Initializing Cryptographic API
[4294673.633000] Limiting direct PCI/PCI transfers.
[4294673.634000] isapnp: Scanning for PnP cards...
[4294673.987000] isapnp: No Plug & Play device found
[4294674.084000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[4294674.086000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294674.086000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294674.086000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294674.086000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294674.087000] ttyS3 at I/O 0x2e8 (irq = 3) is a NS16550A
[4294674.096000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294674.097000] io scheduler noop registered
[4294674.097000] io scheduler anticipatory registered
[4294674.097000] io scheduler deadline registered
[4294674.097000] io scheduler cfq registered
[4294674.099000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294674.100000] EISA: Probing bus 0 at eisa.0
[4294674.100000] Cannot allocate resource for EISA slot 8
[4294674.100000] EISA: Detected 0 cards.
[4294674.100000] NET: Registered protocol family 2
[4294674.110000] IP: routing cache hash table of 1024 buckets, 8Kbytes
[4294674.110000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294674.111000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294674.111000] TCP: Hash tables configured (established 8192 bind 8192)
[4294674.111000] NET: Registered protocol family 8
[4294674.111000] NET: Registered protocol family 20
[4294674.112000] ACPI wakeup devices:
[4294674.112000] USBC
[4294674.112000] ACPI: (supports S0 S1 S3 S5)
[4294674.113000] Freeing unused kernel memory: 224k freed
[4294674.157000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294674.294000] Capability LSM initialized
[4294674.366000] NET: Registered protocol family 1
[4294674.433000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294674.433000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294674.433000] ACPI: bus type ide registered
[4294674.460000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294674.460000] PIIX4: chipset revision 1
[4294674.460000] PIIX4: not 100% native mode: will probe irqs later
[4294674.460000]     ide0: BM-DMA at 0xfcd0-0xfcd7, BIOS settings: hda:pio, hdb:pio
[4294674.460000]     ide1: BM-DMA at 0xfcd8-0xfcdf, BIOS settings: hdc:pio, hdd:pio
[4294674.460000] Probing IDE interface ide0...
[4294674.724000] hda: TOSHIBA MK6412MAT, ATA DISK drive
[4294675.336000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.336000] Probing IDE interface ide1...
[4294676.009000] hdc: MATSHITA CR-175, ATAPI CD/DVD-ROM drive
[4294676.315000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.315000] Probing IDE interface ide2...
[4294676.828000] Probing IDE interface ide3...
[4294677.341000] Probing IDE interface ide4...
[4294677.854000] Probing IDE interface ide5...
[4294678.387000] hda: max request size: 128KiB
[4294678.589000] hda: 12685680 sectors (6495 MB), CHS=13424/15/63, UDMA(33)
[4294678.589000] hda: cache flushes not supported
[4294678.589000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294678.661000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[4294678.661000] Uniform CD-ROM driver Revision: 3.20
[4294679.992000] Attempting manual resume
[4294680.053000] swsusp: Suspend partition has wrong signature?
[4294680.296000] usbcore: registered new driver usbfs
[4294680.296000] usbcore: registered new driver hub
[4294680.303000] USB Universal Host Controller Interface driver v2.2
[4294680.303000] PCI: Enabling device 0000:00:07.2 (0004 -> 0005)
[4294680.306000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294680.306000] PCI: setting IRQ 10 as level-triggered
[4294680.306000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294680.306000] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[4294680.368000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294680.368000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000fce0
[4294680.369000] hub 1-0:1.0: USB hub found
[4294680.369000] hub 1-0:1.0: 2 ports detected
[4294680.534000] PCI: Enabling device 0000:00:0d.0 (0014 -> 0017)
[4294680.537000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[4294680.537000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294680.537000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294680.537000] 0000:00:0d.0: 3Com PCI 3c555 Laptop Hurricane at 0xfc00. Vers LK1.1.19
[4294680.558000]  ***INVALID CHECKSUM 003f*** <6>ACPI: Fan [FAN] (off)
[4294684.000000] ACPI: CPU0 (power states: C1[C1])
[4294684.000000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294684.026000] ACPI: Thermal Zone [THRM] (29 C)
[4294684.280000] Attempting manual resume
[4294684.307000] swsusp: Suspend partition has wrong signature?
[4294684.384000] kjournald starting.  Commit interval 5 seconds
[4294684.384000] EXT3-fs: mounted filesystem with ordered data mode.
[4294687.691000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294696.475000] Adding 289128k swap on /dev/hda5.  Priority:-1 extents:1
[4294696.840000] EXT3 FS on hda1, internal journal
[4294713.227000] parport: PnPBIOS parport detected.
[4294713.227000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294713.336000] lp0: using parport0 (interrupt-driven).
[4294713.470000] mice: PS/2 mouse device common for all mice
[4294713.842000] input: PS/2 Generic Mouse on isa0060/serio1
[4294715.494000] ts: Compaq touchscreen protocol output
[4294719.052000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294720.966000] cdrom: open failed.
[4294725.638000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294725.638000] PCI: setting IRQ 11 as level-triggered
[4294725.638000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294725.638000] nm256: no ac97 is found!
[4294725.638000]   force the driver to load by passing in the module parameter
[4294725.638000]     force_ac97=1
[4294725.638000]   or try sb16 or cs423x drivers instead.
[4294725.638000] ACPI: PCI interrupt for device 0000:00:02.1 disabled
[4294725.638000] NeoMagic 256: probe of 0000:00:02.1 failed with error -6
[4294727.936000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294728.452000] Linux Kernel Card Services
[4294728.453000]   options:  [pci] [cardbus] [pm]
[4294728.526000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294728.526000] Yenta: CardBus bridge found at 0000:00:0a.0 [0099:0000]
[4294728.647000] Yenta: ISA IRQ mask 0x0058, PCI irq 10
[4294728.647000] Socket status: 30000006
[4294731.284000] irda_init()
[4294731.284000] NET: Registered protocol family 23
[4294731.656000] Floppy drive(s): fd0 is 1.44M
[4294731.671000] FDC 0 is a National Semiconductor PC87306
[4294732.630000] Real Time Clock Driver v1.12
[4294732.969000] input: PC Speaker
[4294737.744000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294737.801000] NET: Registered protocol family 17
[4294741.030000] NET: Registered protocol family 10
[4294741.030000] Disabled Privacy Extensions on device c02eb280(lo)
[4294741.031000] IPv6 over IPv4 tunneling driver
[4294743.491000] ACPI: AC Adapter [AC] (on-line)
[4294744.017000] ACPI: Battery Slot [CMB1] (battery present)
[4294744.127000] ACPI: Power Button (FF) [PWRF]
[4294744.127000] ACPI: Sleep Button (CM) [SLPB]
[4294744.687000] ibm_acpi: ec object not found
[4294751.918000] eth0: no IPv6 routers present
[4294766.178000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294766.178000] apm: overridden by ACPI.
[4294768.073000] cs: IO port probe 0x100-0x4ff: excluding 0x220-0x22f 0x330-0x337 0x388-0x38f
[4294768.076000] cs: IO port probe 0xc00-0xcf7: clean.
[4294768.076000] cs: IO port probe 0xa00-0xaff: clean.

---

### Post by qopax on 2006-01-14
Is it possible to install whatever Knoppix uses to manage pcmcia cards? Like I said in a previous post, the card starts blinking and such after cardmgr is loaded in the Knoppix bootup sequence. Is there something like that in debian/ubuntu? It always gets stuck on the hotplug subsystem in ubuntu if I have the card inserted. Is it maybe possible to patch that somehow? Or maybe there is pcmcia configuration somewhere that would enable my pcmcia port to work?

---

### Post by qopax on 2006-01-15
I tried recompiling the kernel with prism54 support using the instructions on the ubuntu wiki, but it had no effect. 

Is it maybe possible to install knoppix without all the applications on it, just with the hardware support? I'd really love to continue using ubuntu but it's showing me no love.

---

### Post by qopax on 2006-01-15
I noticed at installation 
"ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10"

Could IRQ 10 be the pcmcia port and that would be freezing it whenever I inserted the card? Is it possible to disable acpi to test it?

---

### Post by qopax on 2006-01-17
If anyone wants to know, the solution was to put noacpi and acpi=off into the kernel boot option.

---

