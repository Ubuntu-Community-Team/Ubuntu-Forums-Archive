---
title: "Hotplug subsystem hangs on boot"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by benteppe on 2005-04-17
Hello, 

I installed Kubuntu 5.04 Hoary a few days ago and it's been running OK so far, until I booted WinXP once: since then, Kubuntu hangs on boot at "starting hotplug subsystem" (bloody windoze - even manages to screw up another OS!!!). 

I've been through dozens of posts here and there, looked on Google, and tried a few fixes (noapic and nolapic on boot - still hangs and on top of that I can't get the network working; disabling ACPI in BIOS - same result; blacklisting 2 or 3 modules in etc/hotplug/blacklist - no effect). 

So for now I manage to get the system going by hitting ctrl+C some 4 to 5 seconds after the "starting hotplug subsystem..." appears (if I hit too early, it kills the processes before the network card is plugged, as far as I understand, and if I hit it too late, it has no effect and I have to reboot).

My question is: when I hit ctrl+C, it seems that it kills ONE process (the one that was hanging) and the system continues to boot as normal. I know I can make sure that this very process doesn't get loaded in the first place, by adding it into the blacklist, but the thing is... how do I know which process I've killed ? There's no such log as "hotplug" in my var/log directory...

Can anyone help ? 

Thanks in advance, 

Ben

---

### Post by kleeman on 2005-04-17
According to the documentation here:
[http://linux-hotplug.sourceforge.net/](http://linux-hotplug.sourceforge.net/)
You need to look in /var/log/messages for errors.
The site above has some other useful docs as well....

---

### Post by benteppe on 2005-04-19
Hi, thanks for your help. I've looked in the message file, here's the output:



Apr 19 10:43:29 localhost kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
Apr 19 10:43:29 localhost kernel: BIOS-provided physical RAM map:
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 19 10:43:29 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Apr 19 10:43:29 localhost kernel: 511MB LOWMEM available.
Apr 19 10:43:29 localhost kernel: found SMP MP-table at 000f4820
Apr 19 10:43:29 localhost kernel: DMI 2.2 present.
Apr 19 10:43:29 localhost kernel: ACPI: PM-Timer IO Port: 0x4008
Apr 19 10:43:29 localhost kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 19 10:43:29 localhost kernel: Processor #0 6:10 APIC version 16
Apr 19 10:43:29 localhost kernel: ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 19 10:43:29 localhost kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 19 10:43:29 localhost kernel: IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Apr 19 10:43:29 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 19 10:43:29 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
Apr 19 10:43:29 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 19 10:43:29 localhost kernel: Using ACPI (MADT) for SMP configuration information
Apr 19 10:43:29 localhost kernel: Built 1 zonelists
Apr 19 10:43:29 localhost kernel: Kernel command line: root=/dev/hda4 ro quiet splash
Apr 19 10:43:29 localhost kernel: Initializing CPU#0
Apr 19 10:43:29 localhost kernel: PID hash table entries: 2048 (order: 11, 32768 bytes)
Apr 19 10:43:29 localhost kernel: Detected 2100.040 MHz processor.
Apr 19 10:43:29 localhost kernel: Using pmtmr for high-res timesource
Apr 19 10:43:29 localhost kernel: Console: colour VGA+ 80x25
Apr 19 10:43:29 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 19 10:43:29 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 19 10:43:29 localhost kernel: Memory: 511772k/524224k available (1436k kernel code, 11808k reserved, 754k data, 224k init, 0k highmem)
Apr 19 10:43:29 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 19 10:43:29 localhost kernel: Security Framework v1.0.0 initialized
Apr 19 10:43:29 localhost kernel: SELinux:  Disabled at boot.
Apr 19 10:43:29 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Apr 19 10:43:29 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Apr 19 10:43:29 localhost kernel: CPU: L2 Cache: 512K (64 bytes/line)
Apr 19 10:43:29 localhost kernel: CPU: AMD Athlon(tm) XP 2800+ stepping 00
Apr 19 10:43:29 localhost kernel: Enabling fast FPU save and restore... done.
Apr 19 10:43:29 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Apr 19 10:43:29 localhost kernel: Checking 'hlt' instruction... OK.
Apr 19 10:43:29 localhost kernel: Checking for popad bug... OK.
Apr 19 10:43:29 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
Apr 19 10:43:29 localhost kernel: ENABLING IO-APIC IRQs
Apr 19 10:43:29 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=-1
Apr 19 10:43:29 localhost kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Apr 19 10:43:29 localhost kernel: Freeing initrd memory: 4248k freed
Apr 19 10:43:29 localhost kernel: NET: Registered protocol family 16
Apr 19 10:43:29 localhost kernel: EISA bus registered
Apr 19 10:43:29 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfb3a0, last bus=1
Apr 19 10:43:29 localhost kernel: PCI: Using configuration type 1
Apr 19 10:43:29 localhost kernel: mtrr: v2.0 (20020519)
Apr 19 10:43:29 localhost kernel: ACPI: Subsystem revision 20050211
Apr 19 10:43:29 localhost kernel: ACPI: Interpreter enabled
Apr 19 10:43:29 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Apr 19 10:43:29 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Apr 19 10:43:29 localhost kernel: PCI: Probing PCI hardware (bus 00)
Apr 19 10:43:29 localhost kernel: PCI: Via IRQ fixup
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
Apr 19 10:43:29 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 19 10:43:29 localhost kernel: pnp: PnP ACPI init
Apr 19 10:43:29 localhost kernel: pnp: PnP ACPI: found 15 devices
Apr 19 10:43:29 localhost kernel: PnPBIOS: Disabled by ACPI PNP
Apr 19 10:43:29 localhost kernel: PCI: Using ACPI for IRQ routing
Apr 19 10:43:29 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
Apr 19 10:43:29 localhost kernel: ** causes a device to stop working, it is probably because the
Apr 19 10:43:29 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
Apr 19 10:43:29 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
Apr 19 10:43:29 localhost kernel: ** behavior.  If this argument makes the device work again,
Apr 19 10:43:29 localhost kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
Apr 19 10:43:29 localhost kernel: ** so I can fix the driver.
Apr 19 10:43:29 localhost kernel: pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
Apr 19 10:43:29 localhost kernel: pnp: 00:01: ioport range 0x5000-0x500f has been reserved
Apr 19 10:43:29 localhost kernel: audit: initializing netlink socket (disabled)
Apr 19 10:43:29 localhost kernel: VFS: Disk quotas dquot_6.5.1
Apr 19 10:43:29 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 19 10:43:29 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Apr 19 10:43:29 localhost kernel: devfs: boot_options: 0x0
Apr 19 10:43:29 localhost kernel: Initializing Cryptographic API
Apr 19 10:43:29 localhost kernel: isapnp: Scanning for PnP cards...
Apr 19 10:43:29 localhost kernel: isapnp: No Plug & Play device found
Apr 19 10:43:29 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 19 10:43:29 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 19 10:43:29 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Apr 19 10:43:29 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 19 10:43:29 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 19 10:43:29 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 19 10:43:29 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 19 10:43:29 localhost kernel: io scheduler noop registered
Apr 19 10:43:29 localhost kernel: io scheduler anticipatory registered
Apr 19 10:43:29 localhost kernel: io scheduler deadline registered
Apr 19 10:43:29 localhost kernel: io scheduler cfq registered
Apr 19 10:43:29 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Apr 19 10:43:29 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Apr 19 10:43:29 localhost kernel: EISA: Probing bus 0 at eisa0
Apr 19 10:43:29 localhost kernel: Cannot allocate resource for EISA slot 4
Apr 19 10:43:29 localhost kernel: Cannot allocate resource for EISA slot 5
Apr 19 10:43:29 localhost kernel: EISA: Detected 0 cards.
Apr 19 10:43:29 localhost kernel: NET: Registered protocol family 2
Apr 19 10:43:29 localhost kernel: IP: routing cache hash table of 4096 buckets, 32Kbytes
Apr 19 10:43:29 localhost kernel: TCP: Hash tables configured (established 32768 bind 65536)
Apr 19 10:43:29 localhost kernel: NET: Registered protocol family 8
Apr 19 10:43:29 localhost kernel: NET: Registered protocol family 20
Apr 19 10:43:29 localhost kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
Apr 19 10:43:29 localhost kernel:  Strange, kseriod not stopped
Apr 19 10:43:29 localhost kernel:  done
Apr 19 10:43:29 localhost kernel: ACPI wakeup devices: 
Apr 19 10:43:29 localhost kernel: SLPB PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 UAR1 ECP1 
Apr 19 10:43:29 localhost kernel: ACPI: (supports S0 S3 S4 S5)
Apr 19 10:43:29 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Apr 19 10:43:29 localhost kernel: RAMDISK: Loading 4248KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^Hdone.
Apr 19 10:43:29 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Apr 19 10:43:29 localhost kernel: Freeing unused kernel memory: 224k freed
Apr 19 10:43:29 localhost kernel: ACPI: CPU0 (power states: C1[C1] C2[C2])
Apr 19 10:43:29 localhost kernel: NET: Registered protocol family 1
Apr 19 10:43:29 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 19 10:43:29 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 19 10:43:29 localhost kernel: VP_IDE: IDE controller at PCI slot 0000:00:11.1
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Apr 19 10:43:29 localhost kernel: ACPI: PCI interrupt 0000:00:11.1[A] -> GSI 20 (level, low) -> IRQ 20
Apr 19 10:43:29 localhost kernel: VP_IDE: chipset revision 6
Apr 19 10:43:29 localhost kernel: VP_IDE: not 100%% native mode: will probe irqs later
Apr 19 10:43:29 localhost kernel: VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Apr 19 10:43:29 localhost kernel:     ide0: BM-DMA at 0xe400-0xe407, BIOS settings: hda:DMA, hdb:pio
Apr 19 10:43:29 localhost kernel:     ide1: BM-DMA at 0xe408-0xe40f, BIOS settings: hdc:DMA, hdd:DMA
Apr 19 10:43:29 localhost kernel: hda: ST3120025A, ATA DISK drive
Apr 19 10:43:29 localhost kernel: elevator: using anticipatory as default io scheduler
Apr 19 10:43:29 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 19 10:43:29 localhost kernel: hda: max request size: 1024KiB
Apr 19 10:43:29 localhost kernel: hda: 234441648 sectors (120034 MB) w/1024KiB Cache, CHS=16383/255/63, UDMA(100)
Apr 19 10:43:29 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
Apr 19 10:43:29 localhost kernel: hdc: DVD-ROM BDV316C, ATAPI CD/DVD-ROM drive
Apr 19 10:43:29 localhost kernel: hdd: DVD-RW IDE1004, ATAPI CD/DVD-ROM drive
Apr 19 10:43:29 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Apr 19 10:43:29 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 19 10:43:29 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Apr 19 10:43:29 localhost kernel: EXT3-fs: recovery complete.
Apr 19 10:43:29 localhost kernel: kjournald starting.  Commit interval 5 seconds
Apr 19 10:43:29 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Apr 19 10:43:29 localhost kernel: EXT3 FS on hda4, internal journal
Apr 19 10:43:29 localhost kernel: hdc: ATAPI 1X DVD-ROM drive, 512kB Cache
Apr 19 10:43:29 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Apr 19 10:43:29 localhost kernel: hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Apr 19 10:43:29 localhost kernel: parport: PnPBIOS parport detected.
Apr 19 10:43:29 localhost kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 19 10:43:29 localhost kernel: lp0: using parport0 (interrupt-driven).
Apr 19 10:43:29 localhost kernel: mice: PS/2 mouse device common for all mice
Apr 19 10:43:29 localhost kernel: input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
Apr 19 10:43:29 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Apr 19 10:43:29 localhost kernel: nvidia: module license 'NVIDIA' taints kernel.
Apr 19 10:43:29 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 19 10:43:29 localhost kernel: NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
Apr 19 10:43:29 localhost kernel: ts: Compaq touchscreen protocol output
Apr 19 10:43:29 localhost kernel: Capability LSM initialized
Apr 19 10:43:29 localhost kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
Apr 19 10:43:29 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Apr 19 10:43:29 localhost kernel: cdrom: open failed.
Apr 19 10:43:29 localhost kernel: cdrom: open failed.
Apr 19 10:43:29 localhost kernel: NTFS driver 2.1.22 [Flags: R/O MODULE].
Apr 19 10:43:29 localhost kernel: NTFS volume version 3.1.
Apr 19 10:43:29 localhost kernel: Real Time Clock Driver v1.12
Apr 19 10:43:29 localhost kernel: input: PC Speaker
Apr 19 10:43:29 localhost kernel: inserting floppy driver for 2.6.10-5-386
Apr 19 10:43:29 localhost kernel: FDC 0 is a post-1991 82077
Apr 19 10:43:29 localhost kernel: agpgart: Detected VIA KT400/KT400A/KT600 chipset
Apr 19 10:43:29 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
Apr 19 10:43:29 localhost kernel: agpgart: AGP aperture is 256M @ 0xc0000000
Apr 19 10:43:29 localhost kernel: 8139too Fast Ethernet driver 0.9.27
Apr 19 10:43:29 localhost kernel: ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) -> IRQ 19
Apr 19 10:43:29 localhost kernel: eth0: RealTek RTL8139 at 0xd400, 00:50:70:34:96:cd, IRQ 19
Apr 19 10:43:29 localhost kernel: 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Apr 19 10:43:29 localhost kernel: usbcore: registered new driver usbfs
Apr 19 10:43:29 localhost kernel: usbcore: registered new driver hub
Apr 19 10:43:29 localhost kernel: USB Universal Host Controller Interface driver v2.2
Apr 19 10:43:29 localhost kernel: ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Apr 19 10:43:29 localhost kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.0: irq 21, io base 0xd800
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Apr 19 10:43:29 localhost kernel: hub 1-0:1.0: USB hub found
Apr 19 10:43:29 localhost kernel: hub 1-0:1.0: 2 ports detected
Apr 19 10:43:29 localhost kernel: ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.1: irq 21, io base 0xdc00
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Apr 19 10:43:29 localhost kernel: hub 2-0:1.0: USB hub found
Apr 19 10:43:29 localhost kernel: hub 2-0:1.0: 2 ports detected
Apr 19 10:43:29 localhost kernel: ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.2: irq 21, io base 0xe000
Apr 19 10:43:29 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Apr 19 10:43:29 localhost kernel: hub 3-0:1.0: USB hub found
Apr 19 10:43:29 localhost kernel: hub 3-0:1.0: 2 ports detected
Apr 19 10:43:29 localhost kernel: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 19 10:43:29 localhost kernel: usb 3-1: new full speed USB device using uhci_hcd and address 2
Apr 19 10:43:29 localhost kernel: SCSI subsystem initialized
Apr 19 10:43:29 localhost kernel: Initializing USB Mass Storage driver...
Apr 19 10:43:29 localhost kernel: NET: Registered protocol family 17
Apr 19 10:43:29 localhost kernel: NET: Registered protocol family 10
Apr 19 10:43:29 localhost kernel: Disabled Privacy Extensions on device c02f0500(lo)
Apr 19 10:43:29 localhost kernel: IPv6 over IPv4 tunneling driver
Apr 19 10:43:30 localhost kernel: ACPI: Power Button (FF) [PWRF]
Apr 19 10:43:30 localhost kernel: ACPI: Sleep Button (CM) [SLPB]
Apr 19 10:43:30 localhost kernel: apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Apr 19 10:43:30 localhost kernel: apm: overridden by ACPI.
Apr 19 10:43:35 localhost kernel: agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Apr 19 10:43:35 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Apr 19 10:43:35 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Apr 19 10:43:35 localhost kernel: agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Apr 19 10:43:35 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Apr 19 10:43:35 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Apr 19 10:55:24 localhost exiting on signal 15
Apr 19 10:55:25 localhost syslogd 1.4.1#16ubuntu6: restart.
Apr 19 10:55:26 localhost exiting on signal 15


I'm not very good at this, so the only thing I notice is thise two lines:

Apr 19 10:43:30 localhost kernel: apm: overridden by ACPI.
Apr 19 10:43:35 localhost kernel: agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.

...which show that the apm/acpi related task is taking 5 seconds, more or less the time I usually wait before hitting ctrl+c once hotplug hangs. Could that be a hint, or did I miss something altogether ? 

Thanks again,

Ben

---

### Post by kleeman on 2005-04-19
Looks like this is the offending line:

Apr 19 10:43:35 localhost kernel: agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

This may be associated with the graphics card. Do you have agp enabled or whatever?

---

### Post by benteppe on 2005-04-19
I suppose the only way to find out if AGP is enabled is to reboot and look in the BIOS, right ? Or is there a way to find out without doing that (I'm in the middle of a large download so it'll be a couple of hours before I can reboot) ? 

The graphics card works fine, OpenGL included. Is that going to change if I enable / disable AGP ?

---

### Post by benteppe on 2005-04-19
That's weird: I went in the BIOS and AGP was disabled... I enabled it but it had no effect. So I then disabled it again. Does that mean that somehow the OS is overriding the BIOS and enabling AGP ? If that's the case and that's what is causing the hang, how do I disable it ? 

Thanks in advance!

Ben

---

### Post by kleeman on 2005-04-19
What kind of graphics card have you got? I know there are sometimes issues with ATI cards and 
agpgart (this can be checked out by googling around a bit). Does /etc/X11/xorg.conf show the fglxr 
driver? You may want to fiddle around with the options in this file (I think there is a proprietary 
graphics drivers howto around this forum somewhere).

---

### Post by benteppe on 2005-04-20
Below is a copy of xorg.conf. As you can see, no fglxr driver. 
Regarding the graphics device, it's a nVidia GeForce FX, not an ATI. 
Are you positive it's the graphics that cause the problem ?

Ben



# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "keyboard"
 Option  "CoreKeyboard"
 Option  "XkbRules" "xorg"
 Option  "XkbModel" "pc105"
 Option  "XkbLayout" "fr-latin9"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection

Section "Device"
 Identifier "NVIDIA Corporation NV34 [GeForce FX 5200]"
 Driver  "nvidia"
 BusID  "PCI:1:0:0"
EndSection

Section "Monitor"
 Identifier "CPT CL-150G"
 Option  "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "NVIDIA Corporation NV34 [GeForce FX 5200]"
 Monitor  "CPT CL-150G"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by benteppe on 2005-04-20
2 more things, which may be connected to this issue or not (if definitely note, I'll put a new post about them):
- I tried to re-install Ubuntu Hoary and the install hangs at "setting up USB system" or something like that. Strange, considering there was no problem with the first install!
- when I finally get into KDE on my existing Ubuntu Hoary, I get an error about sound.
- same again, if I run, say, Tuxracer, the following comes up in console:
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:387:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:945:(snd_func_refer) error evaluating name
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3932:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM default
open /dev/sequencer: No such file or directory


Could this be the cause of the problem, or is it only due to the fact that I stop hotplug at startup ?

---

### Post by kleeman on 2005-04-20
OK you've got me ;-) If you can't install I would suggest lodging a bug report and see whether the devs can suggest something.

---

### Post by hshen on 2005-06-09
[QUOTE=kleeman]OK you've got me ;-) If you can't install I would suggest lodging a bug report and see whether the devs can suggest something.[/QUOTE]

I have similar hotplug subsystem hang problem. I spent quite sometime to figure that the pci.rc hangs when it loads a driver for TI Cardbus Controller. Where should I report this kind of bug?

Thanks!
hshen

---

### Post by FLeiXiuS on 2005-06-10
You may want to try disabling acpi.

In the grub configuration, add "acpi=off noapic" to the end kernel boot arguments.

---

### Post by Mustard on 2006-04-16
The nvidia graphics card I see in the xorg.conf is the same model as mine.  I'm pretty sure it supports AGP 8x.  My motherboard doesnt support 8x AGP, so mine is setup for 4x.

If you feel like getting your hands dirty, I wonder whether you might get some benefit from reseating some of your PCI cards in different slots. It is complaining a bit about IRQs in the system log.  My system decided to crap itself the other day, after I updated my bios, and started locking up with sound loops at gdm login.  Moving the sound card to a different slot half solved the problem.  Now my sound is working, but the tv card is on the blink now. It's complaining about not having resources to allocate to it. When I get desperate enough, I'm going to move the tv tuner card to a different slot and see if I can get them both working at the same time, but I'm too lazy to bother with it atm. :)

With regards to BIOS settings you can try to turn off some of the power management features in BIOS, and even try disabling an ports that you are not currently using to free up some IRQ's.  I usually disable one of my serial ports and the parallel port, as I don't use them for anything.

I think the above suggestion to disable acpi is a good idea too.

---

