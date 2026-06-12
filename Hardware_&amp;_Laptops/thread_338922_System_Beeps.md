---
title: "System Beeps"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by DapperMe17 on 2007-01-15
Ubuntu Edgy


Just after the Ubuntu splash (progress meter) screen and before the Ubuntu login screen, I am experiencing a short series of system beeps.


They seem to have appeared after I tried to install a USB 2.0 card. I have since removed that card.

I have an Award Bios. I have checked all PCI and AGP cards for proper seating, etc. I have reflashed the Bios as well, with no trouble.

Note...I'm experiencing absolutely no troubles with any of the PCI, or AGP card(s) performance



Could these be normal beeps during the loading of Ubuntu??? ](*,) 


Would any hardware conflicts come up in Device Manager?

---

### Post by bigken on 2007-01-15
beeps are usually bios codes for hardware errors I would also reseat the ram

---

### Post by DapperMe17 on 2007-01-15
The series sequence would indicate video card trouble, although I'm not experiencing any issues with video. I have also tried another AGP video card, which works just fine. But unfortunately, same beeps.

1 long-2 short-2short   (the last beep is a deeper tone than the previous 4)

---

### Post by bigken on 2007-01-15
you could try shorting the cmos battery and reset the bios

---

### Post by DapperMe17 on 2007-01-15
I've reflashed the Bios...I'll try to reset in the bios.

Although, I don't know how to short the cmos battery.

---

### Post by bigken on 2007-01-15
there 2 ways jumper or just pull the battery for 10 mins 


it could be a bad chechsum error where this should clear it ;)

---

### Post by DapperMe17 on 2007-01-15
I pulled the power cord & pulled the battery....although for only a couple of minutes.

I then booted to Bios. The current Bios version is still present, however the date and time were completely reset among other settings.

Unfortunately, I still get the beeps.  (By the way, the full amount of RAM is correctly being used) 


Contrary to your advise, could these be Ubuntu load errors? 

If I posted a startup "log", could that help ID the problem?

---

### Post by bigken on 2007-01-15
what is the beep sequence ?

yes you could post as others may have ideas

---

### Post by DapperMe17 on 2007-01-15
Bios is Asus Kestrel-U (HP)

Sequence is 1-2-2-1

I wonder if it could be an error with Ubuntu on the HD...I can run Damn Small Linux  LiveCD with no error beeps whatsoever...?



Startup log is.........



Jan 15 02:26:57 xxx-desktop syslogd 1.4.1#18ubuntu6: restart.
Jan 15 02:26:58 xxx-desktop kernel: Inspecting /boot/System.map-2.6.17-10-generic
Jan 15 02:26:58 xxx-desktop kernel: Loaded 22826 symbols from /boot/System.map-2.6.17-10-generic.
Jan 15 02:26:58 xxx-desktop kernel: Symbols match kernel version 2.6.17.
Jan 15 02:26:58 xxx-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] BIOS-provided physical RAM map:
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 0000000017ffd000 (usable)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]  BIOS-e820: 0000000017ffd000 - 0000000017fff000 (ACPI data)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]  BIOS-e820: 0000000017fff000 - 0000000018000000 (ACPI NVS)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] 0MB HIGHMEM available.
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] 383MB LOWMEM available.
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] On node 0 totalpages: 98301
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000]   Normal zone: 94205 pages, LIFO batch:31
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] DMI 2.0 present.
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f6f00
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] ACPI: RSDT (v001 ASUS   Kestrel  0x00000000  0x00000000) @ 0x17ffd000
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] ACPI: FADT (v001 ASUS   Kestrel  0x00000000  0x00000000) @ 0x17ffd080
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] ACPI: BOOT (v001 ASUS   Kestrel  0x00000000  0x00000000) @ 0x17ffd040
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] ACPI: DSDT (v001   ASUS KESTREL  0x00001000 MSFT 0x0100000a) @ 0x00000000
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0xe408
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7ff0000)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Built 1 zonelists
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] mapped APIC to ffffd000 (0130a000)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Enabling fast FPU save and restore... done.
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Enabling unmasked SIMD FPU exception support... done.
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Initializing CPU#0
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Detected 598.599 MHz processor.
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Using pmtmr for high-res timesource
Jan 15 02:26:58 xxx-desktop kernel: [17179569.184000] Console: colour VGA+ 80x25
Jan 15 02:26:58 xxx-desktop kernel: [17179570.956000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 15 02:26:58 xxx-desktop kernel: [17179570.960000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 15 02:26:58 xxx-desktop kernel: [17179571.012000] Memory: 380008k/393204k available (1910k kernel code, 12576k reserved, 1069k data, 308k init, 0k highmem)
Jan 15 02:26:58 xxx-desktop kernel: [17179571.012000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] Calibrating delay using timer specific routine.. 1198.57 BogoMIPS (lpj=2397154)
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] Security Framework v1.0.0 initialized
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] SELinux:  Disabled at boot.
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] Mount-cache hash table entries: 512
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] CPU: L1 I cache: 16K, L1 D cache: 16K
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] CPU: L2 cache: 256K
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
Jan 15 02:26:58 xxx-desktop kernel: [17179571.092000] Checking 'hlt' instruction... OK.
Jan 15 02:26:58 xxx-desktop kernel: [17179571.108000] SMP alternatives: switching to UP code
Jan 15 02:26:58 xxx-desktop kernel: [17179571.108000] Freeing SMP alternatives: 16k freed
Jan 15 02:26:58 xxx-desktop kernel: [17179571.108000] checking if image is initramfs... it is
Jan 15 02:26:58 xxx-desktop kernel: [17179572.712000] Freeing initrd memory: 5322k freed
Jan 15 02:26:58 xxx-desktop kernel: [17179572.712000] ACPI: Core revision 20060707
Jan 15 02:26:58 xxx-desktop kernel: [17179572.712000] ACPI: Looking for DSDT ... not found!
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] ACPI: setting ELCR to 0200 (from 0e00)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] CPU0: Intel Pentium III (Coppermine) stepping 01
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] SMP motherboard not detected.
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] Local APIC not detected. Using dummy APIC emulation.
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] Brought up 1 CPUs
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] migration_cost=0
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] NET: Registered protocol family 16
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] EISA bus registered
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] ACPI: bus type pci registered
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] PCI: PCI BIOS revision 2.10 entry at 0xf0510, last bus=1
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] PCI: Using configuration type 1
Jan 15 02:26:58 xxx-desktop kernel: [17179572.716000] Setting up standard PCI resources
Jan 15 02:26:58 xxx-desktop kernel: [17179572.728000] ACPI: Interpreter enabled
Jan 15 02:26:58 xxx-desktop kernel: [17179572.728000] ACPI: Using PIC for interrupt routing
Jan 15 02:26:58 xxx-desktop kernel: [17179572.728000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.728000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.732000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.732000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.732000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.732000] PCI: Probing PCI hardware (bus 00)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.732000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Jan 15 02:26:58 xxx-desktop kernel: [17179572.736000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
Jan 15 02:26:58 xxx-desktop kernel: [17179572.736000] Boot video device is 0000:01:00.0
Jan 15 02:26:58 xxx-desktop kernel: [17179572.736000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 15 02:26:58 xxx-desktop kernel: [17179572.744000] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 15 02:26:58 xxx-desktop kernel: [17179572.744000] pnp: PnP ACPI init
Jan 15 02:26:58 xxx-desktop kernel: [17179572.752000] pnp: PnP ACPI: found 13 devices
Jan 15 02:26:58 xxx-desktop kernel: [17179572.752000] PnPBIOS: Disabled by ACPI PNP
Jan 15 02:26:58 xxx-desktop kernel: [17179572.752000] PCI: Using ACPI for IRQ routing
Jan 15 02:26:58 xxx-desktop kernel: [17179572.752000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jan 15 02:26:58 xxx-desktop kernel: [17179572.776000] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
Jan 15 02:26:58 xxx-desktop kernel: [17179572.776000] pnp: 00:02: ioport range 0xe800-0xe80f has been reserved
Jan 15 02:26:58 xxx-desktop kernel: [17179572.776000] PCI: Bridge: 0000:00:01.0
Jan 15 02:26:58 xxx-desktop kernel: [17179572.776000]   IO window: disabled.
Jan 15 02:26:58 xxx-desktop kernel: [17179572.776000]   MEM window: d6000000-d7efffff
Jan 15 02:26:58 xxx-desktop kernel: [17179572.776000]   PREFETCH window: d7f00000-e3ffffff
Jan 15 02:26:58 xxx-desktop kernel: [17179572.776000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Jan 15 02:26:58 xxx-desktop kernel: [17179572.776000] NET: Registered protocol family 2
Jan 15 02:26:58 xxx-desktop kernel: [17179572.816000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.816000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.816000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.816000] TCP: Hash tables configured (established 16384 bind 8192)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.816000] TCP reno registered
Jan 15 02:26:58 xxx-desktop kernel: [17179572.816000] Simple Boot Flag at 0x3a set to 0x1
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] audit: initializing netlink socket (disabled)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] audit(1168849558.820:1): initialized
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] VFS: Disk quotas dquot_6.5.1
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] Initializing Cryptographic API
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] io scheduler noop registered
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] io scheduler anticipatory registered
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] io scheduler deadline registered
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] io scheduler cfq registered (default)
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] Activating ISA DMA hang workarounds.
Jan 15 02:26:58 xxx-desktop kernel: [17179572.820000] isapnp: Scanning for PnP cards...
Jan 15 02:26:58 xxx-desktop kernel: [17179573.176000] isapnp: No Plug & Play device found
Jan 15 02:26:58 xxx-desktop kernel: [17179573.260000] Real Time Clock Driver v1.12ac
Jan 15 02:26:58 xxx-desktop kernel: [17179573.260000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jan 15 02:26:58 xxx-desktop kernel: [17179573.260000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 15 02:26:58 xxx-desktop kernel: [17179573.260000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jan 15 02:26:58 xxx-desktop kernel: [17179573.260000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 15 02:26:58 xxx-desktop kernel: [17179573.264000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jan 15 02:26:58 xxx-desktop kernel: [17179573.264000] mice: PS/2 mouse device common for all mice
Jan 15 02:26:58 xxx-desktop kernel: [17179573.264000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan 15 02:26:58 xxx-desktop kernel: [17179573.264000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan 15 02:26:58 xxx-desktop kernel: [17179573.264000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan 15 02:26:58 xxx-desktop kernel: [17179573.268000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 15 02:26:58 xxx-desktop kernel: [17179573.268000] serio: i8042 AUX port at x60,0x64 irq 12
Jan 15 02:26:58 xxx-desktop kernel: [17179573.268000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 15 02:26:58 xxx-desktop kernel: [17179573.268000] EISA: Probing bus 0 at eisa.0
Jan 15 02:26:58 xxx-desktop kernel: [17179573.268000] EISA: Detected 0 cards.
Jan 15 02:26:58 xxx-desktop kernel: [17179573.272000] TCP bic registered
Jan 15 02:26:58 xxx-desktop kernel: [17179573.272000] NET: Registered protocol family 1
Jan 15 02:26:58 xxx-desktop kernel: [17179573.272000] NET: Registered protocol family 8
Jan 15 02:26:58 xxx-desktop kernel: [17179573.272000] NET: Registered protocol family 20
Jan 15 02:26:58 xxx-desktop kernel: [17179573.272000] Using IPI No-Shortcut mode
Jan 15 02:26:58 xxx-desktop kernel: [17179573.272000] ACPI: (supports S0 S1 S5)
Jan 15 02:26:58 xxx-desktop kernel: [17179573.272000] Freeing unused kernel memory: 308k freed
Jan 15 02:26:58 xxx-desktop kernel: [17179573.300000] input: AT Translated Set 2 keyboard as /class/input/input0
Jan 15 02:26:58 xxx-desktop kernel: [17179574.596000] Capability LSM initialized
Jan 15 02:26:58 xxx-desktop kernel: [17179574.728000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jan 15 02:26:58 xxx-desktop kernel: [17179576.260000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
Jan 15 02:26:58 xxx-desktop kernel: [17179576.260000] VP_IDE: chipset revision 6
Jan 15 02:26:58 xxx-desktop kernel: [17179576.260000] VP_IDE: not 100%% native mode: will probe irqs later
Jan 15 02:26:58 xxx-desktop kernel: [17179576.260000] VP_IDE: VIA vt82c596b (rev 11) IDE UDMA66 controller on pci0000:00:07.1
Jan 15 02:26:58 xxx-desktop kernel: [17179576.260000]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:pio
Jan 15 02:26:58 xxx-desktop kernel: [17179576.260000]     ide1: BM-DMA at 808-0xd80f, BIOS settings: hdc:DMA, hdd:DMA
Jan 15 02:26:58 xxx-desktop kernel: [17179576.260000] Probing IDE interface ide0...
Jan 15 02:26:58 xxx-desktop kernel: [17179576.676000] hda: Maxtor 93073U6, ATA DISK drive
Jan 15 02:26:58 xxx-desktop kernel: [17179577.348000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jan 15 02:26:58 xxx-desktop kernel: [17179577.348000] Probing IDE interface ide1...
Jan 15 02:26:58 xxx-desktop kernel: [17179578.212000] hdc: R/RW 4x4x24, ATAPI CD/DVD-ROM drive
Jan 15 02:26:58 xxx-desktop kernel: [17179578.996000] hdd: TOSHIBA DVD-ROM SD-M1302, ATAPI CD/DVD-ROM drive
Jan 15 02:26:58 xxx-desktop kernel: [17179579.052000] ide1 at 0x170-0x177,0x376 on irq 15
Jan 15 02:26:58 xxx-desktop kernel: [17179579.076000] hda: max request size: 128KiB
Jan 15 02:26:58 xxx-desktop kernel: [17179579.124000] hda: 60030432 sectors (30735 MB) w/2048KiB Cache, CHS=59554/16/63, UDMA(66)
Jan 15 02:26:58 xxx-desktop kernel: [17179579.124000] hda: cache flushes not supported
Jan 15 02:26:58 xxx-desktop kernel: [17179579.124000]  hda: hda1 hda2 < hda5 >
Jan 15 02:26:58 xxx-desktop kernel: [17179579.220000] hdc: ATAPI 24X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
Jan 15 02:26:58 xxx-desktop kernel: [17179579.220000] Uniform CD-ROM driver Revision: 3.20
Jan 15 02:26:58 xxx-desktop kernel: [17179579.228000] hdd: ATAPI 40X DVD-ROM drive, 256kB Cache, UDMA(33)
Jan 15 02:26:58 xxx-desktop kernel: [17179579.752000] usbcore: registered new driver usbfs
Jan 15 02:26:58 xxx-desktop kernel: [17179579.752000] usbcore: registered new driver hub
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] USB Universal Host Controller Interface driver v3.0
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] PCI: setting IRQ 9 as level-triggered
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] uhci_hcd 0000:00:07.2: UHCI Host Controller
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000d400
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] usb usb1: configuration #1 chosen from 1 choice
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] hub 1-0:1.0: USB hub found
Jan 15 02:26:58 xxx-desktop kernel: [17179579.760000] hub 1-0:1.0: 2 ports detected
Jan 15 02:26:58 xxx-desktop kernel: [17179579.960000] Attempting manual resume
Jan 15 02:26:58 xxx-desktop kernel: [17179580.008000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jan 15 02:26:58 xxx-desktop kernel: [17179580.008000] EXT3-fs: write access will be enabled during recovery.
Jan 15 02:26:58 xxx-desktop kernel: [17179580.112000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Jan 15 02:26:58 xxx-desktop kernel: [17179580.284000] usb 1-1: configuration #1 chosen from 1 choice
Jan 15 02:26:58 xxx-desktop kernel: [17179580.524000] usb 1-2: new full speed USB device using uhci_hcd and address 3
Jan 15 02:26:58 xxx-desktop kernel: [17179580.864000] usb 1-2: configuration #1 chosen from 1 choice
Jan 15 02:26:58 xxx-desktop kernel: [17179597.236000] kjournald starting.  Commit interval 5 seconds
Jan 15 02:26:58 xxx-desktop kernel: [17179597.236000] EXT3-fs: hda1: orphan cleanup on readonly fs
Jan 15 02:26:58 xxx-desktop kernel: [17179597.236000] ext3_orphan_cleanup: deleting unreferenced inode 1177736
Jan 15 02:26:58 xxx-desktop kernel: [17179597.236000] ext3_orphan_cleanup: deleting unreferenced inode 1177726
Jan 15 02:26:58 xxx-desktop kernel: [17179597.236000] EXT3-fs: hda1: 2 orphan inodes deleted
Jan 15 02:26:58 xxx-desktop kernel: [17179597.236000] EXT3-fs: recovery complete.
Jan 15 02:26:58 xxx-desktop kernel: [17179597.260000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 15 02:26:58 xxx-desktop kernel: [17179612.164000] Linux agpgart interface v0.101 (c) Dave Jones
Jan 15 02:26:58 xxx-desktop kernel: [17179612.192000] agpgart: Detected VIA Apollo Pro 133 chipset
Jan 15 02:26:58 xxx-desktop kernel: [17179612.196000] agpgart: AGP aperture is 64M @ 0xe4000000
Jan 15 02:26:58 xxx-desktop kernel: [17179612.228000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 15 02:26:58 xxx-desktop kernel: [17179612.244000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 15 02:26:58 xxx-desktop kernel: [17179614.064000] 8139too Fast Ethernet driver 0.9.27
Jan 15 02:26:58 xxx-desktop kernel: [17179614.064000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
Jan 15 02:26:58 xxx-desktop kernel: [17179614.064000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
Jan 15 02:26:58 xxx-desktop kernel: [17179614.064000] eth0: RealTek RTL8139 at 0xd88de000, 00:10:b5:3e:4c:8c, IRQ 9
Jan 15 02:26:58 xxx-desktop kernel: [17179614.064000] eth0:  Identified 8139 chip type 'RTL-8139B'
Jan 15 02:26:58 xxx-desktop kernel: [17179615.196000] Floppy drive(s): fd0 is 1.44M
Jan 15 02:26:58 xxx-desktop kernel: [17179615.212000] FDC 0 is a post-1991 82077
Jan 15 02:26:58 xxx-desktop kernel: [17179615.232000] input: PC Speaker as /class/input/input1
Jan 15 02:26:58 xxx-desktop kernel: [17179615.360000] nvidia: module license 'NVIDIA' taints kernel.
Jan 15 02:26:58 xxx-desktop kernel: [17179615.384000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Jan 15 02:26:58 xxx-desktop kernel: [17179615.384000] PCI: setting IRQ 11 as level-triggered
Jan 15 02:26:58 xxx-desktop kernel: [17179615.384000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jan 15 02:26:58 xxx-desktop kernel: [17179615.388000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan 15 02:26:58 xxx-desktop kernel: [17179615.992000] logips2pp: Detected unknown logitech mouse model 62
Jan 15 02:26:58 xxx-desktop kernel: [17179616.472000] parport: PnPBIOS parport detected.
Jan 15 02:26:58 xxx-desktop kernel: [17179616.472000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Jan 15 02:26:58 xxx-desktop kernel: [17179616.488000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
Jan 15 02:26:58 xxx-desktop kernel: [17179616.828000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
Jan 15 02:26:58 xxx-desktop kernel: [17179616.828000] PCI: setting IRQ 10 as level-triggered
Jan 15 02:26:58 xxx-desktop kernel: [17179616.828000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Jan 15 02:26:58 xxx-desktop kernel: [17179617.644000] AC'97 0 analog subsections not ready
Jan 15 02:26:58 xxx-desktop kernel: [17179617.668000] gameport:  is , io 0x200, speed 1011kHz
Jan 15 02:26:58 xxx-desktop kernel: [17179618.004000] ts: Compaq touchscreen protocol output
Jan 15 02:26:58 xxx-desktop kernel: [17179618.056000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7804
Jan 15 02:26:58 xxx-desktop kernel: [17179618.056000] usbcore: registered new driver usblp
Jan 15 02:26:58 xxx-desktop kernel: [17179618.056000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Jan 15 02:26:58 xxx-desktop kernel: [17179619.132000] lp0: using parport0 (interrupt-driven).
Jan 15 02:26:58 xxx-desktop kernel: [17179619.228000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Jan 15 02:26:58 xxx-desktop kernel: [17179619.400000] usb 1-2: reset full speed USB device using uhci_hcd and address 3
Jan 15 02:26:58 xxx-desktop kernel: [17179619.852000] ndiswrapper: driver rt2500usb () loaded
Jan 15 02:26:58 xxx-desktop kernel: [17179621.008000] wlan0: vendor: 'Ralink Technology Inc.'
Jan 15 02:26:58 xxx-desktop kernel: [17179621.008000] wlan0: ethernet device 00:18:39:03:80:7a using NDIS driver rt2500usb, 13B1:000D.0.conf
Jan 15 02:26:58 xxx-desktop kernel: [17179621.012000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan 15 02:26:58 xxx-desktop kernel: [17179621.016000] usbcore: registered new driver ndiswrapper
Jan 15 02:26:58 xxx-desktop kernel: [17179621.232000] Adding 1124508k swap on /dev/disk/by-uuid/7e90a1be-1275-4328-b7e8-4943bdca9933.  Priority:-1 extents:1 across:1124508k
Jan 15 02:26:58 xxx-desktop kernel: [17179621.512000] NET: Registered protocol family 17
Jan 15 02:26:58 xxx-desktop kernel: [17179621.696000] EXT3 FS on hda1, internal journal
Jan 15 02:26:58 xxx-desktop kernel: [17179626.036000] ACPI: Power Button (FF) [PWRF]
Jan 15 02:26:58 xxx-desktop kernel: [17179626.508000] ibm_acpi: ec object not found
Jan 15 02:26:58 xxx-desktop kernel: [17179626.608000] pcc_acpi: loading...
Jan 15 02:26:58 xxx-desktop usbmgr[3871]: start 1.0.0
Jan 15 02:26:59 xxx-desktop dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Jan 15 02:26:59 xxx-desktop usbmgr[3875]: "hid" was loaded
Jan 15 02:26:59 xxx-desktop usbmgr[3875]: "usbhid" was loaded
Jan 15 02:26:59 xxx-desktop usbmgr[3875]: "usbmouse" was loaded
Jan 15 02:26:59 xxx-desktop usbmgr[3875]: "mousedev" was loaded
Jan 15 02:26:59 xxx-desktop usbmgr[3875]: class:0x9 subclass:0x0 protocol:0x0
Jan 15 02:26:59 xxx-desktop usbmgr[3875]: USB device is matched the configuration
Jan 15 02:27:00 xxx-desktop usbmgr[3875]: "none" isn't loaded
Jan 15 02:27:00 xxx-desktop usbmgr[3875]: vendor:0x3f0 product:0x7804
Jan 15 02:27:00 xxx-desktop usbmgr[3875]: class:0x7 subclass:0x1 protocol:0x2
Jan 15 02:27:00 xxx-desktop usbmgr[3875]: USB device is matched the configuration
Jan 15 02:27:00 xxx-desktop usbmgr[3875]: "usblp" was loaded
Jan 15 02:27:00 xxx-desktop usbmgr[3875]: vendor:0x13b1 product:0xd
Jan 15 02:27:00 xxx-desktop usbmgr[3875]: class:0xff subclass:0xff protocol:0xff
Jan 15 02:27:01 xxx-desktop usbmgr[3875]: USB device isn't matched the configuration
Jan 15 02:27:01 xxx-desktop kernel: [17179631.808000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
Jan 15 02:27:01 xxx-desktop kernel: [17179631.808000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
Jan 15 02:27:01 xxx-desktop kernel: [17179631.808000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
Jan 15 02:27:02 xxx-desktop hpiod: 1.6.9 accepting connections at 2208... 
Jan 15 02:27:08 xxx-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan 15 02:27:08 xxx-desktop kernel: [17179638.292000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jan 15 02:27:08 xxx-desktop kernel: [17179638.292000] apm: overridden by ACPI.
Jan 15 02:27:13 xxx-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11

---

### Post by bigken on 2007-01-15
yes could be right about it being a linux thing 

if it were a bios error you would not get past the post screen 


have you tried boot in safe mode ?

---

### Post by DapperMe17 on 2007-01-15
Thanks, Bigken.


Is there a way I can attempt a correction with the Ubuntu LiveCD, without completely reinstalling from scratch?

---

### Post by bigken on 2007-01-16
you could give it a go it cant hurt 

also have you googled the problem

---

