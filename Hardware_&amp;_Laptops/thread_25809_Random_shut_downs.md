---
title: "Random shut downs"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by Jon E on 2005-04-10
My laptop is randomly shutting down - I took a look at my /var/log/messages and didn't really find anything useful but I figured I'd paste some here and maybe someone had any ideas:

Apr 10 12:34:32 ubuntu shutdown[14937]: shutting down for system halt
Apr 10 12:34:34 ubuntu gconfd (jon-8190): Received signal 15, shutting down cleanly
Apr 10 12:34:34 ubuntu gconfd (jon-8190): Exiting
Apr 10 12:34:36 ubuntu kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr 10 12:34:36 ubuntu kernel: apm: disabled on user request.
Apr 10 12:34:40 ubuntu kernel: Kernel logging (proc) stopped.
Apr 10 12:34:40 ubuntu kernel: Kernel log daemon terminating.
Apr 10 12:34:40 ubuntu exiting on signal 15
Apr 10 16:21:12 ubuntu syslogd 1.4.1#16ubuntu6: restart.


Apr 10 18:01:12 ubuntu -- MARK --
Apr 10 18:16:25 ubuntu shutdown[9313]: shutting down for system halt
Apr 10 18:16:28 ubuntu gconfd (jon-8186): Received signal 15, shutting down cleanly
Apr 10 18:16:28 ubuntu gconfd (jon-8186): Exiting
Apr 10 18:16:29 ubuntu kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr 10 18:16:29 ubuntu kernel: apm: disabled on user request.
Apr 10 18:16:32 ubuntu kernel: Kernel logging (proc) stopped.
Apr 10 18:16:32 ubuntu kernel: Kernel log daemon terminating.
Apr 10 18:16:32 ubuntu exiting on signal 15

Apr 10 16:21:12 ubuntu kernel: Inspecting /boot/System.map-2.6.10-5-386

It seems to do it after a bit of inactivity (i'm usually away from the computer when it does it, and it has done it twice) but that's the only trend I notice; I'm not sure if the laptop is over heating or just randomly shutting down.  The laptop is no where near hot so I don't think it is that but I haven't a clue.

I'm running on a Gateway M675X - if anyone needs anymore details just let me know.

---

### Post by Jon E on 2005-04-11
Happened again; not exactly sure what's relevant but I'll paste more of my message log; would appreciate any insight because I won't be able to use it if it continues to shut my system down, and I'd be pretty disappointed because I really like it up to this point.

Apr 10 19:06:15 ubuntu syslogd 1.4.1#16ubuntu6: restart.
Apr 10 19:06:15 ubuntu kernel: Inspecting /boot/System.map-2.6.10-5-386
Apr 10 19:06:15 ubuntu kernel: Loaded 27514 symbols from /boot/System.map-2.6.10-5-386.
Apr 10 19:06:15 ubuntu kernel: Symbols match kernel version 2.6.10.
Apr 10 19:06:15 ubuntu kernel: No module symbols loaded - kernel modules not enabled.
Apr 10 19:06:15 ubuntu kernel: BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 0000000000100000 - 000000003ff70000 (usable)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 000000003ff70000 - 000000003ff7b000 (ACPI data)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 000000003ff7b000 - 000000003ff80000 (ACPI NVS)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Apr 10 19:06:15 ubuntu kernel:  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr 10 19:06:15 ubuntu kernel: Warning only 896MB will be used.
Apr 10 19:06:15 ubuntu kernel: Use a HIGHMEM enabled kernel.
Apr 10 19:06:15 ubuntu kernel: 896MB LOWMEM available.
Apr 10 19:06:15 ubuntu kernel: found SMP MP-table at 000f6db0
Apr 10 19:06:15 ubuntu kernel: DMI present.
Apr 10 19:06:15 ubuntu kernel: ACPI: PM-Timer IO Port: 0x1008
Apr 10 19:06:15 ubuntu kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 10 19:06:15 ubuntu kernel: Processor #0 15:2 APIC version 20
Apr 10 19:06:15 ubuntu kernel: ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 10 19:06:15 ubuntu kernel: Processor #1 15:2 APIC version 20
Apr 10 19:06:15 ubuntu kernel: WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
Apr 10 19:06:15 ubuntu kernel: ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 10 19:06:15 ubuntu kernel: ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 10 19:06:15 ubuntu kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 10 19:06:15 ubuntu kernel: IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 10 19:06:15 ubuntu kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 10 19:06:15 ubuntu kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 10 19:06:15 ubuntu kernel: Using ACPI (MADT) for SMP configuration information
Apr 10 19:06:15 ubuntu kernel: Built 1 zonelists
Apr 10 19:06:15 ubuntu kernel: Kernel command line: root=/dev/hda2 ro quiet splash
Apr 10 19:06:15 ubuntu kernel: Initializing CPU#0
Apr 10 19:06:15 ubuntu kernel: PID hash table entries: 4096 (order: 12, 65536 bytes)
Apr 10 19:06:15 ubuntu kernel: Detected 2993.621 MHz processor.
Apr 10 19:06:15 ubuntu kernel: Using pmtmr for high-res timesource
Apr 10 19:06:15 ubuntu kernel: Console: colour VGA+ 80x25
Apr 10 19:06:15 ubuntu kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 10 19:06:15 ubuntu kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 10 19:06:15 ubuntu kernel: Memory: 902044k/917504k available (1436k kernel code, 14928k reserved, 754k data, 224k init, 0k highmem)
Apr 10 19:06:15 ubuntu kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 10 19:06:15 ubuntu kernel: Security Framework v1.0.0 initialized
Apr 10 19:06:15 ubuntu kernel: SELinux:  Disabled at boot.
Apr 10 19:06:15 ubuntu kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Apr 10 19:06:15 ubuntu kernel: CPU: Trace cache: 12K uops, L1 D cache: 8K
Apr 10 19:06:15 ubuntu kernel: CPU: L2 cache: 512K
Apr 10 19:06:15 ubuntu kernel: CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
Apr 10 19:06:15 ubuntu kernel: Enabling fast FPU save and restore... done.
Apr 10 19:06:15 ubuntu kernel: Enabling unmasked SIMD FPU exception support... done.
Apr 10 19:06:15 ubuntu kernel: Checking 'hlt' instruction... OK.
Apr 10 19:06:15 ubuntu kernel: Checking for popad bug... OK.
Apr 10 19:06:15 ubuntu kernel: ACPI: Looking for DSDT in initrd... not found!
Apr 10 19:06:15 ubuntu kernel: ENABLING IO-APIC IRQs
Apr 10 19:06:15 ubuntu kernel: ..TIMER: vector=0x31 pin1=0 pin2=-1
Apr 10 19:06:15 ubuntu kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Apr 10 19:06:15 ubuntu kernel: Freeing initrd memory: 4248k freed
Apr 10 19:06:15 ubuntu kernel: NET: Registered protocol family 16
Apr 10 19:06:15 ubuntu kernel: EISA bus registered
Apr 10 19:06:15 ubuntu kernel: PCI: PCI BIOS revision 2.10 entry at 0xfd952, last bus=3
Apr 10 19:06:15 ubuntu kernel: PCI: Using configuration type 1
Apr 10 19:06:15 ubuntu kernel: mtrr: v2.0 (20020519)
Apr 10 19:06:15 ubuntu kernel: ACPI: Subsystem revision 20050211
Apr 10 19:06:15 ubuntu kernel: ACPI: Interpreter enabled
Apr 10 19:06:15 ubuntu kernel: ACPI: Using IOAPIC for interrupt routing
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Apr 10 19:06:15 ubuntu kernel: PCI: Probing PCI hardware (bus 00)
Apr 10 19:06:15 ubuntu kernel: PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Apr 10 19:06:15 ubuntu kernel: PCI: Transparent bridge - 0000:00:1e.0
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 10) *0
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
Apr 10 19:06:15 ubuntu kernel: ACPI: Device [FDDA] status [00000008]: functional but not present; setting present
Apr 10 19:06:15 ubuntu kernel: ACPI: Embedded Controller [EC0] (gpe 29)
Apr 10 19:06:15 ubuntu kernel: ACPI: Device [SLAV] status [00000008]: functional but not present; setting present
Apr 10 19:06:15 ubuntu kernel: ACPI: Power Resource [PFN0] (off)
Apr 10 19:06:15 ubuntu kernel: ACPI: Power Resource [PFN3] (off)
Apr 10 19:06:15 ubuntu kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 10 19:06:15 ubuntu kernel: pnp: PnP ACPI init
Apr 10 19:06:15 ubuntu kernel: pnp: PnP ACPI: found 10 devices
Apr 10 19:06:15 ubuntu kernel: PnPBIOS: Disabled by ACPI PNP
Apr 10 19:06:15 ubuntu kernel: PCI: Using ACPI for IRQ routing
Apr 10 19:06:15 ubuntu kernel: ** PCI interrupts are no longer routed automatically.  If this
Apr 10 19:06:15 ubuntu kernel: ** causes a device to stop working, it is probably because the
Apr 10 19:06:15 ubuntu kernel: ** driver failed to call pci_enable_device().  As a temporary
Apr 10 19:06:15 ubuntu kernel: ** workaround, the "pci=routeirq" argument restores the old
Apr 10 19:06:15 ubuntu kernel: ** behavior.  If this argument makes the device work again,
Apr 10 19:06:15 ubuntu kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
Apr 10 19:06:15 ubuntu kernel: ** so I can fix the driver.
Apr 10 19:06:15 ubuntu kernel: Simple Boot Flag at 0x36 set to 0x1
Apr 10 19:06:15 ubuntu kernel: audit: initializing netlink socket (disabled)
Apr 10 19:06:15 ubuntu kernel: VFS: Disk quotas dquot_6.5.1
Apr 10 19:06:15 ubuntu kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 10 19:06:15 ubuntu kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Apr 10 19:06:15 ubuntu kernel: devfs: boot_options: 0x0
Apr 10 19:06:15 ubuntu kernel: Initializing Cryptographic API
Apr 10 19:06:15 ubuntu kernel: isapnp: Scanning for PnP cards...
Apr 10 19:06:15 ubuntu kernel: isapnp: No Plug & Play device found
Apr 10 19:06:15 ubuntu kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 10 19:06:15 ubuntu kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 10 19:06:15 ubuntu kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
Apr 10 19:06:15 ubuntu kernel: io scheduler noop registered
Apr 10 19:06:15 ubuntu kernel: io scheduler anticipatory registered
Apr 10 19:06:15 ubuntu kernel: VFS: Mounted root (cramfs filesystem) readonly.
Apr 10 19:06:15 ubuntu kernel: Freeing unused kernel memory: 224k freed
Apr 10 19:06:15 ubuntu kernel: ACPI: Fan [FAN0] (off)
Apr 10 19:06:15 ubuntu kernel: ACPI: Fan [FAN3] (off)
Apr 10 19:06:15 ubuntu kernel: ACPI: Thermal Zone [THRM] (41 C)
Apr 10 19:06:15 ubuntu kernel: ACPI: Thermal Zone [THR2] (34 C)
Apr 10 19:06:15 ubuntu kernel: NET: Registered protocol family 1
Apr 10 19:06:15 ubuntu kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 10 19:06:15 ubuntu kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 10 19:06:15 ubuntu kernel: ICH5: IDE controller at PCI slot 0000:00:1f.1
Apr 10 19:06:15 ubuntu kernel: PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Apr 10 19:06:15 ubuntu kernel: ICH5: chipset revision 2
Apr 10 19:06:15 ubuntu kernel: ICH5: not 100%% native mode: will probe irqs later
Apr 10 19:06:15 ubuntu kernel:     ide0: BM-DMA at 0x1880-0x1887, BIOS settings: hda:pio, hdb:pio
Apr 10 19:06:15 ubuntu kernel:     ide1: BM-DMA at 0x1888-0x188f, BIOS settings: hdc:pio, hdd:pio
Apr 10 19:06:15 ubuntu kernel: hda: HTS548060M9AT00, ATA DISK drive
Apr 10 19:06:15 ubuntu kernel: elevator: using anticipatory as default io scheduler
Apr 10 19:06:15 ubuntu kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 10 19:06:15 ubuntu kernel: hda: max request size: 1024KiB
Apr 10 19:06:15 ubuntu kernel: hda: 117210240 sectors (60011 MB) w/7877KiB Cache, CHS=16383/255/63, UDMA(100)
Apr 10 19:06:15 ubuntu kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Apr 10 19:06:15 ubuntu kernel: hdc: TOSHIBA DVD-ROM SD-R6112, ATAPI CD/DVD-ROM drive
Apr 10 19:06:15 ubuntu kernel: ide1 at 0x170-0x177,0x376 on irq 15
Apr 10 19:06:15 ubuntu kernel: Stopping tasks: ==|
Apr 10 19:06:15 ubuntu kernel: Freeing memory...  ^H-^H\^H|^H/^Hdone (455 pages freed)
Apr 10 19:06:15 ubuntu kernel: Restarting tasks... done
Apr 10 19:06:15 ubuntu kernel: EXT3-fs: mounted filesystem with ordered data mode.
Apr 10 19:06:15 ubuntu kernel: kjournald starting.  Commit interval 5 seconds
Apr 10 19:06:15 ubuntu kernel: Adding 1228932k swap on /dev/hda5.  Priority:-1 extents:1
Apr 10 19:06:15 ubuntu kernel: EXT3 FS on hda2, internal journal
Apr 10 19:06:15 ubuntu kernel: hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Apr 10 19:06:15 ubuntu kernel: Uniform CD-ROM driver Revision: 3.20
Apr 10 19:06:15 ubuntu kernel: parport: PnPBIOS parport detected.
Apr 10 19:06:15 ubuntu kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 10 19:06:15 ubuntu kernel: lp0: using parport0 (interrupt-driven).
Apr 10 19:06:15 ubuntu kernel: mice: PS/2 mouse device common for all mice
Apr 10 19:06:15 ubuntu kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Apr 10 19:06:15 ubuntu kernel: ts: Compaq touchscreen protocol output
Apr 10 19:06:15 ubuntu kernel: Linux Kernel Card Services
Apr 10 19:06:15 ubuntu kernel:   options:  [pci] [cardbus] [pm]
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 10 19:06:15 ubuntu kernel: Yenta: CardBus bridge found at 0000:03:01.0 [107b:0601]
Apr 10 19:06:15 ubuntu kernel: Yenta: ISA IRQ mask 0x0c38, PCI irq 17
Apr 10 19:06:15 ubuntu kernel: Socket status: 30000006
Apr 10 19:06:15 ubuntu kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
Apr 10 19:06:15 ubuntu kernel: ACPI: PCI interrupt 0000:03:01.1[A] -> GSI 17 (level, low) -> IRQ 17
Apr 10 19:06:15 ubuntu kernel: ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[e0306000-e03067ff]  Max Packet=[2048]
Apr 10 19:06:15 ubuntu kernel: e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
Apr 10 19:06:15 ubuntu kernel:   Vendor: USB2.0    Model: CardReader CF RW  Rev: 0.0>
Apr 10 19:06:15 ubuntu kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 10 19:06:15 ubuntu kernel:   Vendor: USB2.0    Model: CardReader Combo  Rev: 0.0>
Apr 10 19:06:15 ubuntu kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 10 19:06:15 ubuntu kernel: Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Apr 10 19:06:15 ubuntu kernel: Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 1
Apr 10 19:06:15 ubuntu kernel: NET: Registered protocol family 10
Apr 10 19:06:15 ubuntu kernel: Disabled Privacy Extensions on device c02f0500(lo)
Apr 10 19:06:15 ubuntu kernel: IPv6 over IPv4 tunneling driver
Apr 10 19:06:15 ubuntu kernel: ACPI: AC Adapter [ACAD] (on-line)
Apr 10 19:06:21 ubuntu kernel: ACPI: Battery Slot [BAT1] (battery present)
Apr 10 19:06:21 ubuntu kernel: ACPI: Power Button (FF) [PWRF]
Apr 10 19:06:21 ubuntu kernel: ACPI: Lid Switch [LID]
Apr 10 19:06:21 ubuntu kernel: ACPI: Sleep Button (CM) [SLPB]
Apr 10 19:06:21 ubuntu kernel: ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Apr 10 19:06:21 ubuntu kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr 10 19:06:21 ubuntu kernel: apm: overridden by ACPI.
Apr 10 19:06:22 ubuntu kernel: cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
Apr 10 19:06:22 ubuntu kernel: cs: IO port probe 0x0800-0x08ff: clean.
Apr 10 19:26:15 ubuntu -- MARK --
Apr 10 19:46:15 ubuntu -- MARK --
Apr 10 20:06:15 ubuntu -- MARK --
Apr 10 20:26:15 ubuntu -- MARK --
Apr 10 20:46:15 ubuntu -- MARK --
Apr 10 21:06:15 ubuntu -- MARK --
Apr 10 21:07:05 ubuntu shutdown[9363]: shutting down for system halt
Apr 10 21:07:06 ubuntu gconfd (jon-8189): Received signal 15, shutting down cleanly
Apr 10 21:07:06 ubuntu gconfd (jon-8189): Exiting
Apr 10 21:07:09 ubuntu kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr 10 21:07:09 ubuntu kernel: apm: disabled on user request.
Apr 10 21:07:12 ubuntu kernel: Kernel logging (proc) stopped.
Apr 10 21:07:12 ubuntu kernel: Kernel log daemon terminating.
Apr 10 21:07:12 ubuntu exiting on signal 15
Apr 10 21:16:17 ubuntu syslogd 1.4.1#16ubuntu6: restart.
Apr 10 21:16:17 ubuntu kernel: Inspecting /boot/System.map-2.6.10-5-386
Apr 10 21:16:17 ubuntu kernel: Loaded 27514 symbols from /boot/System.map-2.6.10-5-386.
Apr 10 21:16:17 ubuntu kernel: Symbols match kernel version 2.6.10.
Apr 10 21:16:17 ubuntu kernel: No module symbols loaded - kernel modules not enabled.

---

### Post by Jon E on 2005-04-14
Anyone?

---

### Post by ca1igola on 2005-04-24
I noticed the same problem too: I've hoary running on an ASUS m6ne.
I also noticed that battery can't recharge when computer is on; the orange led (recharging status led) doesn't light up untill the computer is off, and the battery icon too seems agree: the percentage of charge doesn't change.
So, if anyone has any idea... thanks

CA

---

### Post by snaga on 2005-05-06
I wish I had an answer. My Toshiba A75 is doing the same thing.

For me it seems like it happens when I am working the computer a bit hard.

Very frustrating. My guess is that its something to do with ACPI. This is a dual-boot machine, but I don't run windows much. It _has_ happened a time or two under windows.

---

### Post by airhead on 2005-05-08
You might like to check out this thread: [http://ubuntuforums.org/showthread.php?t=31295](http://ubuntuforums.org/showthread.php?t=31295)

---

### Post by smurky on 2005-06-24
I was having similar problems on an hp pavilion ze5270. The problem in my case was that I was running JACK on a journalling file system. There is a workaround, adding the line:

         none  /dev/shm  tmpfs defaults 0 0 

to your /etc/fstab. However, after my most recent round of frustration and consequent reinstallation I'm getting much better results on an ext2fs. Much lower latency, no overheating, no shutdowns. Regarding screensavers the little ants running round the moebius strip are making me dizzy. My laptop runs a little louder and hotter, so if I'm not using it for audio I use powernowd which keeps things cool and quiet.

---

### Post by Jon E on 2005-08-06
[QUOTE=airhead]You might like to check out this thread: [http://ubuntuforums.org/showthread.php?t=31295](http://ubuntuforums.org/showthread.php?t=31295)[/QUOTE]

I'm not sure why it took me so long to check back at this thread; but I reinstalled ubuntu a few days ago and was STILL having the same issue, ended up reading your thread, disabled the screensaver and it has worked like a charm since then.  Thank you. :D

---

### Post by Synner on 2005-08-07
Just a thought, but how many of you have *never* cleaned your heatsink vent?  I was having this problem before, in windows and ubuntu, so I took the keyboard off, took out the cpu fan, and there was a massive buildup of dust and lint...but from the outside, the vent looked ok.  There could be just enough in there that the consistent load from the screen saver might be overheating the system....maybe.

---

### Post by mack75 on 2007-03-01
Hi:

May be too late.

But the Synner's answer is right. 

I've a Toshiba Satellite A75 with dual booting Winbugs and Linux, and when the heatsink are very dirty, the fans don't stop, all the time are working in Winbugs, but on Linux the system shutdown or freeze up. I've installed some distributions on my Laptop, like RedHat, SuSE, Gentoo, Ubuntu, Knoppix, Debian, but when the heatsink are dirty and the processor's load is very high all of them fail up.

The solution: clean up the heatsink carefully.

The instructions for disassembling Toshiba Laps are in: [http://www.irisvista.com/]("http://www.irisvista.com/")

Enjoy it.

Regards :)

---

