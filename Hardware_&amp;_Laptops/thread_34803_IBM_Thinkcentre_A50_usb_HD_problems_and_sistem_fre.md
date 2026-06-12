---
title: "IBM Thinkcentre A50: usb HD problems and sistem freeze"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by maxter on 2005-05-16
i installed ubuntu on a ibm thinkcentre a50.
all worked fine, but when i try to format an external maxtor 200 GB HD, mkfs start to format the disk, but then hang up.
i formatted the same disk with another ibm box (xseries 206) running sarge, without problems, then i plugged again the usb disk to the ubuntu box, but if i try to copy large files to the usb disk it freeze after a few GB.
the sistem then becomes unstable.

another problem i found was that leaving on the pc during the night, make it freeze completly (reboot required)
i tried both with 2.6.10 and 2.6.11 kernel...

any hint or suggestion?

many thanks

---

### Post by maxter on 2005-05-17
here in attachment my /var/log/messages file.

i cutted the file because the last 9 lines are repeated many times (untill i stopped the system with the power switch).

the only stange things i found is an acpi error

i will try to disable acpi to see what will happen

i will post the code in two two times due to forum's message size limit.

```


May 16 17:17:56 localhost kernel: Intel machine check reporting enabled on CPU#0.
May 16 17:17:56 localhost kernel: CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
May 16 17:17:56 localhost kernel: CPU0: Thermal monitoring enabled
May 16 17:17:56 localhost kernel: CPU: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 09
May 16 17:17:56 localhost kernel: Enabling fast FPU save and restore... done.
May 16 17:17:56 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
May 16 17:17:56 localhost kernel: Checking 'hlt' instruction... OK.
May 16 17:17:56 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
May 16 17:17:56 localhost kernel: ACPI: setting ELCR to 0200 (from 0e28)
May 16 17:17:56 localhost kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
May 16 17:17:56 localhost kernel: Freeing initrd memory: 4524k freed
May 16 17:17:56 localhost kernel: NET: Registered protocol family 16
May 16 17:17:56 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfd98d, last bus=3
May 16 17:17:56 localhost kernel: PCI: Using configuration type 1
May 16 17:17:56 localhost kernel: mtrr: v2.0 (20020519)
May 16 17:17:56 localhost kernel: ACPI: Subsystem revision 20050211
May 16 17:17:56 localhost kernel: ACPI: Interpreter enabled
May 16 17:17:56 localhost kernel: ACPI: Using PIC for interrupt routing
May 16 17:17:56 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
May 16 17:17:56 localhost kernel: PCI: Probing PCI hardware (bus 00)
May 16 17:17:56 localhost kernel: PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
May 16 17:17:56 localhost kernel: PCI: Transparent bridge - 0000:00:1e.0
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 9 10 11 12 14 15)
May 16 17:17:56 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
May 16 17:17:56 localhost kernel: pnp: PnP ACPI init
May 16 17:17:56 localhost kernel: pnp: PnP ACPI: found 14 devices
May 16 17:17:56 localhost kernel: PnPBIOS: Disabled by ACPI PNP
May 16 17:17:56 localhost kernel: PCI: Using ACPI for IRQ routing
May 16 17:17:56 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
May 16 17:17:56 localhost kernel: ** causes a device to stop working, it is probably because the
May 16 17:17:56 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
May 16 17:17:56 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
May 16 17:17:56 localhost kernel: ** behavior.  If this argument makes the device work again,
May 16 17:17:56 localhost kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
May 16 17:17:56 localhost kernel: ** so I can fix the driver.
May 16 17:17:56 localhost kernel: Simple Boot Flag at 0x35 set to 0x1
May 16 17:17:56 localhost kernel: audit: initializing netlink socket (disabled)
May 16 17:17:56 localhost kernel: VFS: Disk quotas dquot_6.5.1
May 16 17:17:56 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 16 17:17:56 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
May 16 17:17:56 localhost kernel: devfs: boot_options: 0x0
May 16 17:17:56 localhost kernel: Initializing Cryptographic API
May 16 17:17:56 localhost kernel: isapnp: Scanning for PnP cards...
May 16 17:17:56 localhost kernel: isapnp: No Plug & Play device found
May 16 17:17:56 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
May 16 17:17:56 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
May 16 17:17:56 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
May 16 17:17:56 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 16 17:17:56 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 16 17:17:56 localhost kernel: io scheduler noop registered
May 16 17:17:56 localhost kernel: io scheduler anticipatory registered
May 16 17:17:56 localhost kernel: io scheduler deadline registered
May 16 17:17:56 localhost kernel: io scheduler cfq registered
May 16 17:17:56 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
May 16 17:17:56 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
May 16 17:17:56 localhost kernel: NET: Registered protocol family 2
May 16 17:17:56 localhost kernel: IP: routing cache hash table of 4096 buckets, 32Kbytes
May 16 17:17:56 localhost kernel: TCP: Hash tables configured (established 32768 bind 65536)
May 16 17:17:56 localhost kernel: NET: Registered protocol family 8
May 16 17:17:56 localhost kernel: NET: Registered protocol family 20
May 16 17:17:56 localhost kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
May 16 17:17:56 localhost kernel:  Strange, kseriod not stopped
May 16 17:17:56 localhost kernel:  done
May 16 17:17:56 localhost kernel: ACPI wakeup devices: 
May 16 17:17:56 localhost kernel: USB1 USB2 USB3 USB4 USBE SLOT  KBC COMA 
May 16 17:17:56 localhost kernel: ACPI: (supports S0 S1 S3 S4 S5)
May 16 17:17:56 localhost kernel: RAMDISK: cramfs filesystem found at block 0
May 16 17:17:56 localhost kernel: RAMDISK: Loading 4524KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
May 16 17:17:56 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
May 16 17:17:56 localhost kernel: Freeing unused kernel memory: 164k freed
May 16 17:17:56 localhost kernel: ACPI: Processor [CPU0] (supports 8 throttling states)
May 16 17:17:56 localhost kernel: ACPI: Thermal Zone [THM0] (57 C)
May 16 17:17:56 localhost kernel: NET: Registered protocol family 1
May 16 17:17:56 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May 16 17:17:56 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May 16 17:17:56 localhost kernel: ICH5: IDE controller at PCI slot 0000:00:1f.1
May 16 17:17:56 localhost kernel: PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
May 16 17:17:56 localhost kernel: ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
May 16 17:17:56 localhost kernel: PCI: setting IRQ 5 as level-triggered
May 16 17:17:56 localhost kernel: ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 5 (level, low) -> IRQ 5
May 16 17:17:56 localhost kernel: ICH5: chipset revision 2
May 16 17:17:56 localhost kernel: ICH5: not 100%% native mode: will probe irqs later
May 16 17:17:56 localhost kernel:     ide0: BM-DMA at 0x1880-0x1887, BIOS settings: hda:pio, hdb:pio
May 16 17:17:56 localhost kernel:     ide1: BM-DMA at 0x1888-0x188f, BIOS settings: hdc:pio, hdd:pio
May 16 17:17:56 localhost kernel: hda: IC35L090AVV207-0, ATA DISK drive
May 16 17:17:56 localhost kernel: hdb: IC35L060AVV207-0, ATA DISK drive
May 16 17:17:56 localhost kernel: elevator: using anticipatory as default io scheduler
May 16 17:17:56 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May 16 17:17:56 localhost kernel: hda: max request size: 1024KiB
May 16 17:17:56 localhost kernel: hda: 156312576 sectors (80032 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
May 16 17:17:56 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
May 16 17:17:56 localhost kernel: hdb: max request size: 1024KiB
May 16 17:17:56 localhost kernel: hdb: 80418240 sectors (41174 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
May 16 17:17:56 localhost kernel:  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 p6 >
May 16 17:17:56 localhost kernel: hdc: PHILIPS CDRW48A, ATAPI CD/DVD-ROM drive
May 16 17:17:56 localhost kernel: hdd: HL-DT-ST RW/DVD GCC-4480B, ATAPI CD/DVD-ROM drive
May 16 17:17:56 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
May 16 17:17:56 localhost kernel: Stopping tasks: ==|
May 16 17:17:56 localhost kernel: Freeing memory...  ^H-^H\^H|^H/^Hdone (463 pages freed)
May 16 17:17:56 localhost kernel: Restarting tasks... done
May 16 17:17:56 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
May 16 17:17:56 localhost kernel: EXT3-fs: write access will be enabled during recovery.
May 16 17:17:56 localhost kernel: EXT3-fs: hdb1: orphan cleanup on readonly fs
May 16 17:17:56 localhost kernel: EXT3-fs: hdb1: 2 orphan inodes deleted
May 16 17:17:56 localhost kernel: EXT3-fs: recovery complete.
May 16 17:17:56 localhost kernel: kjournald starting.  Commit interval 5 seconds
May 16 17:17:56 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
May 16 17:17:56 localhost kernel: Adding 497972k swap on /dev/hdb5.  Priority:-1 extents:1
May 16 17:17:56 localhost kernel: EXT3 FS on hdb1, internal journal
May 16 17:17:56 localhost kernel: hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
May 16 17:17:56 localhost kernel: Uniform CD-ROM driver Revision: 3.20
May 16 17:17:56 localhost kernel: hdd: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache
May 16 17:17:56 localhost kernel: parport: PnPBIOS parport detected.
May 16 17:17:56 localhost kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May 16 17:17:56 localhost kernel: lp0: using parport0 (interrupt-driven).
May 16 17:17:56 localhost kernel: mice: PS/2 mouse device common for all mice
May 16 17:17:56 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
May 16 17:17:56 localhost kernel: Capability LSM initialized
May 16 17:17:56 localhost kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
May 16 17:17:56 localhost kernel: ts: Compaq touchscreen protocol output
May 16 17:17:56 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
May 16 17:17:56 localhost kernel: cdrom: open failed.
May 16 17:17:56 localhost kernel: cdrom: open failed.
May 16 17:17:56 localhost kernel: kjournald starting.  Commit interval 5 seconds
May 16 17:17:56 localhost kernel: EXT3 FS on hdb6, internal journal
May 16 17:17:56 localhost kernel: EXT3-fs: recovery complete.
May 16 17:17:56 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
May 16 17:17:56 localhost kernel: Real Time Clock Driver v1.12
May 16 17:17:56 localhost kernel: input: PC Speaker
May 16 17:17:56 localhost kernel: inserting floppy driver for 2.6.10-5-686
May 16 17:17:56 localhost kernel: Floppy drive(s): fd0 is 1.44M
May 16 17:17:56 localhost kernel: FDC 0 is a post-1991 82077
May 16 17:17:56 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
May 16 17:17:56 localhost kernel: agpgart: Detected an Intel 865 Chipset.
May 16 17:17:56 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
May 16 17:17:56 localhost kernel: agpgart: AGP aperture is 256M @ 0xd0000000
May 16 17:17:56 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
May 16 17:17:56 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 16 17:17:56 localhost kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 16 17:17:56 localhost kernel: usbcore: registered new driver usbfs
May 16 17:17:56 localhost kernel: usbcore: registered new driver hub
May 16 17:17:56 localhost kernel: USB Universal Host Controller Interface driver v2.2
May 16 17:17:56 localhost kernel: ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.0: irq 11, io base 0x1800
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May 16 17:17:56 localhost kernel: hub 1-0:1.0: USB hub found
May 16 17:17:56 localhost kernel: hub 1-0:1.0: 2 ports detected
May 16 17:17:56 localhost kernel: ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 10 (level, low) -> IRQ 10
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.1: irq 10, io base 0x1820
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May 16 17:17:56 localhost kernel: hub 2-0:1.0: USB hub found
May 16 17:17:56 localhost kernel: hub 2-0:1.0: 2 ports detected
May 16 17:17:56 localhost kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 5 (level, low) -> IRQ 5
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.2: irq 5, io base 0x1840
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May 16 17:17:56 localhost kernel: hub 3-0:1.0: USB hub found
May 16 17:17:56 localhost kernel: hub 3-0:1.0: 2 ports detected
May 16 17:17:56 localhost kernel: ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 11 (level, low) -> IRQ 11
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.3: irq 11, io base 0x1860
May 16 17:17:56 localhost kernel: uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
May 16 17:17:56 localhost kernel: hub 4-0:1.0: USB hub found
May 16 17:17:56 localhost kernel: hub 4-0:1.0: 2 ports detected
May 16 17:17:56 localhost kernel: usb 3-1: new full speed USB device using uhci_hcd and address 2
May 16 17:17:56 localhost kernel: ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 3 (level, low) -> IRQ 3
May 16 17:17:56 localhost kernel: ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
May 16 17:17:56 localhost kernel: ehci_hcd 0000:00:1d.7: irq 3, pci mem 0xc0000000
May 16 17:17:56 localhost kernel: ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
May 16 17:17:56 localhost kernel: ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
May 16 17:17:56 localhost kernel: hub 5-0:1.0: USB hub found
May 16 17:17:56 localhost kernel: hub 5-0:1.0: 8 ports detected
May 16 17:17:56 localhost kernel: usb 5-1: new high speed USB device using ehci_hcd and address 2
May 16 17:17:56 localhost kernel: SCSI subsystem initialized
May 16 17:17:56 localhost kernel: Initializing USB Mass Storage driver...
May 16 17:17:56 localhost kernel: usb 5-7: new high speed USB device using ehci_hcd and address 4
May 16 17:17:56 localhost kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 9 (level, low) -> IRQ 9
May 16 17:17:56 localhost kernel: usb 5-8: new high speed USB device using ehci_hcd and address 5
May 16 17:17:56 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage devices
May 16 17:17:56 localhost kernel: scsi1 : SCSI emulation for USB Mass Storage devices
May 16 17:17:56 localhost kernel: intel8x0_measure_ac97_clock: measured 49025 usecs
May 16 17:17:56 localhost kernel: intel8x0: clocking to 48000
May 16 17:17:56 localhost kernel: scsi2 : SCSI emulation for USB Mass Storage devices
May 16 17:17:56 localhost kernel: usbcore: registered new driver usb-storage
May 16 17:17:56 localhost kernel: USB Mass Storage support registered.
May 16 17:17:56 localhost kernel: e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
May 16 17:17:56 localhost kernel: e100: Copyright(c) 1999-2004 Intel Corporation
May 16 17:17:56 localhost kernel: ACPI: PCI interrupt 0000:03:08.0[A] -> GSI 9 (level, low) -> IRQ 9
May 16 17:17:56 localhost kernel: e100: eth0: e100_probe: addr 0xc0200000, irq 9, MAC addr 00:09:6B:C7:1D:24
May 16 17:17:56 localhost kernel: e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
May 16 17:17:56 localhost kernel: usb 3-1: new full speed USB device using uhci_hcd and address 4
May 16 17:17:56 localhost kernel: Linux video capture interface: v1.00
May 16 17:17:56 localhost kernel: pwc Philips webcam module version 10.0.6-unofficial loaded.
May 16 17:17:56 localhost kernel: pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
May 16 17:17:56 localhost kernel: pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
May 16 17:17:56 localhost kernel: pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
May 16 17:17:56 localhost kernel: pwc Trace options: 0x00a1
May 16 17:17:56 localhost kernel: usb 3-1: modprobe timed out on ep0out
May 16 17:17:56 localhost kernel: usb 3-1: modprobe timed out on ep0in
May 16 17:17:56 localhost kernel: usbcore: registered new driver snd-usb-audio
May 16 17:17:56 localhost kernel: pwc Philips PCVC730K (ToUCam Fun)/PCVC830 (ToUCam II) USB webcam detected.
May 16 17:17:56 localhost kernel: pwc Registered as /dev/video0.
May 16 17:17:56 localhost kernel: usbcore: registered new driver Philips webcam
May 16 17:17:56 localhost kernel: NET: Registered protocol family 10
May 16 17:17:56 localhost kernel: Disabled Privacy Extensions on device c0313ce0(lo)
May 16 17:17:56 localhost kernel: IPv6 over IPv4 tunneling driver
May 16 17:17:56 localhost kernel:   Vendor: Maxtor    Model: OneTouch          Rev: 0201
May 16 17:17:56 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
May 16 17:17:56 localhost kernel:   Vendor: Maxtor    Model: OneTouch          Rev: 0201
May 16 17:17:56 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
May 16 17:17:56 localhost kernel: SCSI device sda: 398295040 512-byte hdwr sectors (203927 MB)
May 16 17:17:56 localhost kernel: SCSI device sda: 398295040 512-byte hdwr sectors (203927 MB)
May 16 17:17:56 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1
May 16 17:17:56 localhost kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
May 16 17:17:56 localhost kernel: SCSI device sdb: 160084992 512-byte hdwr sectors (81964 MB)
May 16 17:17:56 localhost kernel: SCSI device sdb: 160084992 512-byte hdwr sectors (81964 MB)
May 16 17:17:56 localhost kernel:  /dev/scsi/host1/bus0/target0/lun0: p1
May 16 17:17:56 localhost kernel: Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
May 16 17:17:56 localhost kernel:   Vendor: FREECOM_  Model: DVD+/-RW16B9      Rev: 2.46
May 16 17:17:56 localhost kernel:   Type:   CD-ROM                             ANSI SCSI revision: 00
May 16 17:17:56 localhost kernel: sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 16 17:17:56 localhost kernel: Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
May 16 17:17:56 localhost kernel: Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 0
May 16 17:17:56 localhost kernel: Attached scsi generic sg2 at scsi2, channel 0, id 0, lun 0,  type 5
May 16 17:17:57 localhost hal.hotplug[3955]: timout(10000 ms) waiting for /bus/pci/slots 
May 16 17:17:57 localhost pci.agent[7890]: Bad PCI agent invocation
May 16 17:17:57 localhost kernel: ACPI: Power Button (FF) [PWRF]
May 16 17:17:58 localhost kernel: IBM machine detected. Enabling interrupts during APM calls.
May 16 17:17:58 localhost kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 16 17:17:58 localhost kernel: apm: overridden by ACPI.
May 16 17:17:59 localhost kernel: fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
May 16 17:17:59 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
May 16 17:17:59 localhost kernel: ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 11 (level, low) -> IRQ 11
May 16 17:17:59 localhost kernel: [fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
May 16 17:17:59 localhost kernel: Fire GL built-in AGP-support
May 16 17:17:59 localhost kernel: Based on agpgart interface v0.99 (c) Jeff Hartmann
May 16 17:17:59 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
May 16 17:17:59 localhost kernel: agpgart: Detected an Intel 865G Chipset, no integrated grapics found.
May 16 17:17:59 localhost kernel: agpgart: Detected Intel i865G chipset
May 16 17:17:59 localhost kernel: agpgart: AGP aperture is 256M @ 0xd0000000
May 16 17:17:59 localhost kernel: Power management callback for AGP chipset installed
May 16 17:17:59 localhost kernel: [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
May 16 17:17:59 localhost kernel: AGP: Found 2 AGPv3 devices
May 16 17:17:59 localhost kernel: AGP: Doing enable for AGPv3
May 16 17:17:59 localhost kernel: agpgart: Found an AGP 3.0 compliant device. 
May 16 17:17:59 localhost kernel: [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
May 16 17:17:59 localhost kernel: [fglrx] free  AGP = 256126976
May 16 17:17:59 localhost kernel: [fglrx] max   AGP = 256126976
May 16 17:17:59 localhost kernel: [fglrx] free  LFB = 122679296
May 16 17:17:59 localhost kernel: [fglrx] max   LFB = 122679296
May 16 17:17:59 localhost kernel: [fglrx] free  Inv = 134217728
May 16 17:17:59 localhost kernel: [fglrx] max   Inv = 134217728
May 16 17:17:59 localhost kernel: [fglrx] total Inv = 134217728
May 16 17:17:59 localhost kernel: [fglrx] total TIM = 0
May 16 17:17:59 localhost kernel: [fglrx] total FB  = 0
May 16 17:17:59 localhost kernel: [fglrx] total AGP = 65536
May 16 17:17:59 localhost kernel: pwc Failed to set LED on/off time.
May 16 17:18:14 localhost gconfd (max-8872): Inizializzazione (versione 2.10.0), pid 8872, utente 'max'
May 16 17:18:14 localhost gconfd (max-8872): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.mandatory" Ã¨ stato risolta ad una fonte di configurazione in sola lettura in posizione 0

```

---

### Post by maxter on 2005-05-17
```

May 16 17:18:14 localhost gconfd (max-8872): L'indirizzo "xml:readwrite:/home/max/.gconf" Ã¨ stato risolto ad una fonte di configurazione scrivibile in posizione 1
May 16 17:18:14 localhost gconfd (max-8872): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.defaults" Ã¨ stato risolta ad una fonte di configurazione in sola lettura in posizione 2
May 16 17:18:22 localhost gconfd (max-8872): L'indirizzo "xml:readwrite:/home/max/.gconf" Ã¨ stato risolto ad una fonte di configurazione scrivibile in posizione 0
May 16 17:18:23 localhost kernel: NTFS driver 2.1.22 [Flags: R/O MODULE].
May 16 17:18:23 localhost kernel: NTFS volume version 3.1.
May 16 17:21:31 localhost gconfd (root-9104): Inizializzazione (versione 2.10.0), pid 9104, utente 'root'
May 16 17:21:31 localhost gconfd (root-9104): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.mandatory" Ã¨ stato risolta ad una fonte di configurazione in sola lettura in posizione 0
May 16 17:21:31 localhost gconfd (root-9104): L'indirizzo "xml:readwrite:/root/.gconf" Ã¨ stato risolto ad una fonte di configurazione scrivibile in posizione 1
May 16 17:21:31 localhost gconfd (root-9104): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.defaults" Ã¨ stato risolta ad una fonte di configurazione in sola lettura in posizione 2
May 16 17:22:31 localhost gconfd (root-9104): Ricevuto SIGHUP, nuovo caricamento di tutti i database
May 16 17:22:31 localhost gconfd (root-9104): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.mandatory" Ã¨ stato risolta ad una fonte di configurazione in sola lettura in posizione 0
May 16 17:22:31 localhost gconfd (root-9104): L'indirizzo "xml:readwrite:/root/.gconf" Ã¨ stato risolto ad una fonte di configurazione scrivibile in posizione 1
May 16 17:22:31 localhost gconfd (root-9104): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.defaults" Ã¨ stato risolta ad una fonte di configurazione in sola lettura in posizione 2
May 16 17:28:25 localhost gconfd (max-8872): Uscita
May 16 17:28:26 localhost shutdown[7581]: shutting down for system reboot
May 16 17:28:29 localhost kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 16 17:28:29 localhost kernel: apm: disabled on user request.
May 16 17:28:32 localhost kernel: Kernel logging (proc) stopped.
May 16 17:28:32 localhost kernel: Kernel log daemon terminating.
May 16 17:28:32 localhost exiting on signal 15
May 16 17:29:30 localhost syslogd 1.4.1#16ubuntu6: restart.
May 16 17:29:30 localhost kernel: Inspecting /boot/System.map-2.6.11-1-686
May 16 17:29:31 localhost kernel: Loaded 27088 symbols from /boot/System.map-2.6.11-1-686.
May 16 17:29:31 localhost kernel: Symbols match kernel version 2.6.11.
May 16 17:29:31 localhost kernel: No module symbols loaded - kernel modules not enabled. 
May 16 17:29:31 localhost kernel: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
May 16 17:29:31 localhost kernel: CPU: Trace cache: 12K uops, L1 D cache: 8K
May 16 17:29:31 localhost kernel: CPU: L2 cache: 512K
May 16 17:29:31 localhost kernel: Intel machine check architecture supported.
May 16 17:29:31 localhost kernel: Intel machine check reporting enabled on CPU#0.
May 16 17:29:31 localhost kernel: CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
May 16 17:29:31 localhost kernel: CPU0: Thermal monitoring enabled
May 16 17:29:31 localhost kernel: CPU: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 09
May 16 17:29:31 localhost kernel: Enabling fast FPU save and restore... done.
May 16 17:29:31 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
May 16 17:29:31 localhost kernel: Checking 'hlt' instruction... OK.
May 16 17:29:31 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
May 16 17:29:31 localhost kernel: ENABLING IO-APIC IRQs
May 16 17:29:31 localhost kernel: ..TIMER: vector=0x31 pin1=2 pin2=-1
May 16 17:29:31 localhost kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
May 16 17:29:31 localhost kernel: Freeing initrd memory: 4536k freed
May 16 17:29:31 localhost kernel: NET: Registered protocol family 16
May 16 17:29:31 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfd98d, last bus=3
May 16 17:29:31 localhost kernel: PCI: Using configuration type 1
May 16 17:29:31 localhost kernel: mtrr: v2.0 (20020519)
May 16 17:29:31 localhost kernel: ACPI: Subsystem revision 20050125
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USB1._PRW] (Node dfaea420), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.USB1._PRW] (Node dfaea420), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USB2._PRW] (Node dfaea300), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.USB2._PRW] (Node dfaea300), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USB3._PRW] (Node dfaea1e0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.USB3._PRW] (Node dfaea1e0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USB4._PRW] (Node dfaeafa0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.USB4._PRW] (Node dfaeafa0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USBE._PRW] (Node dfaeaee0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.USBE._PRW] (Node dfaeaee0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel: ACPI: Interpreter enabled
May 16 17:29:31 localhost kernel: ACPI: Using IOAPIC for interrupt routing
May 16 17:29:31 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
May 16 17:29:31 localhost kernel: PCI: Probing PCI hardware (bus 00)
May 16 17:29:31 localhost kernel: PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
May 16 17:29:31 localhost kernel: PCI: Transparent bridge - 0000:00:1e.0
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USB1._PRW] (Node dfaea420), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USB2._PRW] (Node dfaea300), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USB3._PRW] (Node dfaea1e0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USB4._PRW] (Node dfaeafa0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_SB_.PCI0.USBE._PRW] (Node dfaeaee0), AE_AML_NO_RETURN_VALUE
May 16 17:29:31 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May 16 17:29:31 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May 16 17:29:31 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May 16 17:29:31 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May 16 17:29:31 localhost kernel: ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May 16 17:29:31 localhost kernel: ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 16 17:29:31 localhost kernel: ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
May 16 17:29:31 localhost kernel: ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 9 10 11 12 14 15)
May 16 17:29:31 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
May 16 17:29:31 localhost kernel: pnp: PnP ACPI init
May 16 17:29:31 localhost kernel: pnp: PnP ACPI: found 14 devices
May 16 17:29:31 localhost kernel: PnPBIOS: Disabled by ACPI PNP
May 16 17:29:31 localhost kernel: PCI: Using ACPI for IRQ routing
May 16 17:29:31 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
May 16 17:29:31 localhost kernel: ** causes a device to stop working, it is probably because the
May 16 17:29:31 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
May 16 17:29:31 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
May 16 17:29:31 localhost kernel: ** behavior.  If this argument makes the device work again,
May 16 17:29:31 localhost kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
May 16 17:29:31 localhost kernel: ** so I can fix the driver.
May 16 17:29:31 localhost kernel: Simple Boot Flag at 0x35 set to 0x1
May 16 17:29:31 localhost kernel: audit: initializing netlink socket (disabled)
May 16 17:29:31 localhost kernel: VFS: Disk quotas dquot_6.5.1
May 16 17:29:31 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 16 17:29:31 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
May 16 17:29:31 localhost kernel: devfs: boot_options: 0x0
May 16 17:29:31 localhost kernel: Initializing Cryptographic API
May 16 17:29:31 localhost kernel: isapnp: Scanning for PnP cards...
May 16 17:29:31 localhost kernel: isapnp: No Plug & Play device found
May 16 17:29:31 localhost kernel: inotify device minor=63
May 16 17:29:31 localhost kernel: ACPI: PS/2 Keyboard Controller [KBC] at I/O 0x60, 0x64, irq 1
May 16 17:29:31 localhost kernel: ACPI: PS/2 Mouse Controller [PSM] at irq 12
May 16 17:29:31 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
May 16 17:29:31 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
May 16 17:29:31 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
May 16 17:29:31 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 16 17:29:31 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 16 17:29:31 localhost kernel: io scheduler noop registered
May 16 17:29:31 localhost kernel: io scheduler anticipatory registered
May 16 17:29:31 localhost kernel: io scheduler deadline registered
May 16 17:29:31 localhost kernel: io scheduler cfq registered
May 16 17:29:31 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
May 16 17:29:31 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
May 16 17:29:31 localhost kernel: NET: Registered protocol family 2
May 16 17:29:31 localhost kernel: IP: routing cache hash table of 4096 buckets, 32Kbytes
May 16 17:29:31 localhost kernel: TCP established hash table entries: 32768 (order: 6, 262144 bytes)
May 16 17:29:31 localhost kernel: TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
May 16 17:29:31 localhost kernel: TCP: Hash tables configured (established 32768 bind 32768)
May 16 17:29:31 localhost kernel: NET: Registered protocol family 8
May 16 17:29:31 localhost kernel: NET: Registered protocol family 20
May 16 17:29:31 localhost kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
May 16 17:29:31 localhost kernel:  Strange, kseriod not stopped
May 16 17:29:31 localhost kernel:  done
May 16 17:29:31 localhost kernel: ACPI wakeup devices: 
May 16 17:29:31 localhost kernel: SLOT  KBC COMA 
May 16 17:29:31 localhost kernel: ACPI: (supports S0 S1 S3 S4 S5)
May 16 17:29:31 localhost kernel: RAMDISK: cramfs filesystem found at block 0
May 16 17:29:31 localhost kernel: RAMDISK: Loading 4536KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^Hdone.
May 16 17:29:31 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
May 16 17:29:31 localhost kernel: Freeing unused kernel memory: 164k freed
May 16 17:29:31 localhost kernel: ACPI: Processor [CPU0] (supports 8 throttling states)
May 16 17:29:31 localhost kernel: ACPI: Thermal Zone [THM0] (57 C)
May 16 17:29:31 localhost kernel: NET: Registered protocol family 1
May 16 17:29:31 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May 16 17:29:31 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May 16 17:29:31 localhost kernel: ICH5: IDE controller at PCI slot 0000:00:1f.1
May 16 17:29:31 localhost kernel: PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
May 16 17:29:31 localhost kernel: ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
May 16 17:29:31 localhost kernel: ICH5: chipset revision 2
May 16 17:29:31 localhost kernel: ICH5: not 100%% native mode: will probe irqs later
May 16 17:29:31 localhost kernel:     ide0: BM-DMA at 0x1880-0x1887, BIOS settings: hda:pio, hdb:pio
May 16 17:29:31 localhost kernel:     ide1: BM-DMA at 0x1888-0x188f, BIOS settings: hdc:pio, hdd:pio
May 16 17:29:31 localhost kernel: hda: IC35L090AVV207-0, ATA DISK drive
May 16 17:29:31 localhost kernel: hdb: IC35L060AVV207-0, ATA DISK drive
May 16 17:29:31 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May 16 17:29:31 localhost kernel: hda: max request size: 1024KiB
May 16 17:29:31 localhost kernel: hda: 156312576 sectors (80032 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
May 16 17:29:31 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
May 16 17:29:31 localhost kernel: hdb: max request size: 1024KiB
May 16 17:29:31 localhost kernel: hdb: 80418240 sectors (41174 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
May 16 17:29:31 localhost kernel:  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 p6 >
May 16 17:29:31 localhost kernel: hdc: PHILIPS CDRW48A, ATAPI CD/DVD-ROM drive
May 16 17:29:31 localhost kernel: hdd: HL-DT-ST RW/DVD GCC-4480B, ATAPI CD/DVD-ROM drive
May 16 17:29:31 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
May 16 17:29:31 localhost kernel: Stopping tasks: ==|
May 16 17:29:31 localhost kernel: Freeing memory...  ^H-^H\^H|^H/^Hdone (466 pages freed)
May 16 17:29:31 localhost kernel: Restarting tasks... done
May 16 17:29:31 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
May 16 17:29:31 localhost kernel: kjournald starting.  Commit interval 5 seconds
May 16 17:29:31 localhost kernel: Adding 497972k swap on /dev/hdb5.  Priority:-1 extents:1
May 16 17:29:31 localhost kernel: EXT3 FS on hdb1, internal journal
May 16 17:29:31 localhost kernel: hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
May 16 17:29:31 localhost kernel: Uniform CD-ROM driver Revision: 3.20
May 16 17:29:31 localhost kernel: hdd: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache
May 16 17:29:31 localhost kernel: parport: PnPBIOS parport detected.
May 16 17:29:31 localhost kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May 16 17:29:31 localhost kernel: lp0: using parport0 (interrupt-driven).
May 16 17:29:31 localhost kernel: mice: PS/2 mouse device common for all mice
May 16 17:29:31 localhost kernel: input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
May 16 17:29:31 localhost kernel: Capability LSM initialized
May 16 17:29:31 localhost kernel: device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
May 16 17:29:31 localhost kernel: ts: Compaq touchscreen protocol output
May 16 17:29:31 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
May 16 17:29:31 localhost kernel: cdrom: open failed.
May 16 17:29:31 localhost kernel: cdrom: open failed.
May 16 17:29:31 localhost kernel: kjournald starting.  Commit interval 5 seconds
May 16 17:29:31 localhost kernel: EXT3 FS on hdb6, internal journal
May 16 17:29:31 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
May 16 17:29:31 localhost kernel: Real Time Clock Driver v1.12
May 16 17:29:31 localhost kernel: input: PC Speaker
May 16 17:29:31 localhost kernel: Floppy drive(s): fd0 is 1.44M
May 16 17:29:31 localhost kernel: FDC 0 is a post-1991 82077
May 16 17:29:31 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
May 16 17:29:31 localhost kernel: agpgart: Detected an Intel 865 Chipset.
May 16 17:29:31 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
May 16 17:29:31 localhost kernel: agpgart: AGP aperture is 256M @ 0xd0000000
May 16 17:29:31 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
May 16 17:29:31 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 16 17:29:31 localhost kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 16 17:29:31 localhost kernel: usbcore: registered new driver usbfs
May 16 17:29:31 localhost kernel: usbcore: registered new driver hub
May 16 17:29:31 localhost kernel: USB Universal Host Controller Interface driver v2.2
May 16 17:29:31 localhost kernel: ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.0: irq 16, io base 0x1800
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May 16 17:29:31 localhost kernel: hub 1-0:1.0: USB hub found
May 16 17:29:31 localhost kernel: hub 1-0:1.0: 2 ports detected
May 16 17:29:31 localhost kernel: ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.1: irq 19, io base 0x1820
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May 16 17:29:31 localhost kernel: hub 2-0:1.0: USB hub found
May 16 17:29:31 localhost kernel: hub 2-0:1.0: 2 ports detected
May 16 17:29:31 localhost kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.2: irq 18, io base 0x1840
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May 16 17:29:31 localhost kernel: hub 3-0:1.0: USB hub found
May 16 17:29:31 localhost kernel: hub 3-0:1.0: 2 ports detected
May 16 17:29:31 localhost kernel: ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.3: irq 16, io base 0x1860
May 16 17:29:31 localhost kernel: uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
May 16 17:29:31 localhost kernel: hub 4-0:1.0: USB hub found
May 16 17:29:31 localhost kernel: hub 4-0:1.0: 2 ports detected
May 16 17:29:31 localhost kernel: usb 3-1: new full speed USB device using uhci_hcd and address 2
May 16 17:29:31 localhost kernel: ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
May 16 17:29:31 localhost kernel: ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
May 16 17:29:31 localhost kernel: ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xc0000000
May 16 17:29:31 localhost kernel: ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
May 16 17:29:31 localhost kernel: ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
May 16 17:29:31 localhost kernel: hub 5-0:1.0: USB hub found
May 16 17:29:31 localhost kernel: hub 5-0:1.0: 8 ports detected
May 16 17:29:31 localhost kernel: Linux video capture interface: v1.00
May 16 17:29:31 localhost kernel: pwc Philips webcam module version 10.0.6-unofficial loaded.
May 16 17:29:31 localhost kernel: pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
May 16 17:29:31 localhost kernel: pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
May 16 17:29:31 localhost kernel: pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
May 16 17:29:31 localhost kernel: pwc Trace options: 0x00a1
May 16 17:29:31 localhost kernel: usb 5-1: new high speed USB device using ehci_hcd and address 2
May 16 17:29:31 localhost kernel: SCSI subsystem initialized
May 16 17:29:31 localhost kernel: Initializing USB Mass Storage driver...
May 16 17:29:31 localhost kernel: usb 5-7: new high speed USB device using ehci_hcd and address 4
May 16 17:29:31 localhost kernel: usb 5-8: new high speed USB device using ehci_hcd and address 5
May 16 17:29:31 localhost kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
May 16 17:29:31 localhost kernel: pwc Philips PCVC730K (ToUCam Fun)/PCVC830 (ToUCam II) USB webcam detected.
May 16 17:29:31 localhost kernel: pwc Registered as /dev/video0.
May 16 17:29:31 localhost kernel: usbcore: registered new driver Philips webcam
May 16 17:29:31 localhost kernel: snd-usb-audio: probe of 3-1:1.1 failed with error -5
May 16 17:29:31 localhost kernel: usbcore: registered new driver snd-usb-audio
May 16 17:29:31 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage devices
May 16 17:29:31 localhost kernel: scsi1 : SCSI emulation for USB Mass Storage devices
May 16 17:29:31 localhost kernel: intel8x0_measure_ac97_clock: measured 49797 usecs
May 16 17:29:31 localhost kernel: intel8x0: clocking to 48000
May 16 17:29:31 localhost kernel: scsi2 : SCSI emulation for USB Mass Storage devices
May 16 17:29:31 localhost kernel: usbcore: registered new driver usb-storage
May 16 17:29:31 localhost kernel: USB Mass Storage support registered.
May 16 17:29:31 localhost kernel: e100: Intel(R) PRO/100 Network Driver, 3.3.6-k2-NAPI
May 16 17:29:31 localhost kernel: e100: Copyright(c) 1999-2004 Intel Corporation
May 16 17:29:31 localhost kernel: usb 3-1: USB disconnect, address 2
May 16 17:29:31 localhost kernel: ACPI: PCI interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 20
May 16 17:29:31 localhost kernel: e100: eth0: e100_probe: addr 0xc0200000, irq 20, MAC addr 00:09:6B:C7:1D:24
May 16 17:29:31 localhost kernel: usb 3-1: new full speed USB device using uhci_hcd and address 3
May 16 17:29:31 localhost kernel: e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
May 16 17:29:31 localhost kernel: pwc Philips PCVC730K (ToUCam Fun)/PCVC830 (ToUCam II) USB webcam detected.
May 16 17:29:31 localhost kernel: pwc Registered as /dev/video0.
May 16 17:29:31 localhost kernel: usb 3-1: khubd timed out on ep0out
May 16 17:29:31 localhost kernel:   Vendor: Maxtor    Model: OneTouch          Rev: 0201
May 16 17:29:31 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
May 16 17:29:31 localhost kernel:   Vendor: Maxtor    Model: OneTouch          Rev: 0201
May 16 17:29:31 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
May 16 17:29:31 localhost kernel: SCSI device sda: 398295040 512-byte hdwr sectors (203927 MB)
May 16 17:29:31 localhost kernel: SCSI device sda: 398295040 512-byte hdwr sectors (203927 MB)
May 16 17:29:31 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1
May 16 17:29:31 localhost kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
May 16 17:29:31 localhost kernel: SCSI device sdb: 160084992 512-byte hdwr sectors (81964 MB)
May 16 17:29:31 localhost kernel: SCSI device sdb: 160084992 512-byte hdwr sectors (81964 MB)
May 16 17:29:31 localhost kernel:  /dev/scsi/host1/bus0/target0/lun0:<5>  Vendor: FREECOM_  Model: DVD+/-RW16B9      Rev: 2.46
May 16 17:29:31 localhost kernel:   Type:   CD-ROM                             ANSI SCSI revision: 00
May 16 17:29:31 localhost kernel:  p1
May 16 17:29:31 localhost kernel: Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
May 16 17:29:31 localhost kernel: NET: Registered protocol family 10
May 16 17:29:31 localhost kernel: Disabled Privacy Extensions on device c03189a0(lo)
May 16 17:29:31 localhost kernel: IPv6 over IPv4 tunneling driver
May 16 17:29:31 localhost kernel: sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 16 17:29:31 localhost kernel: Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
May 16 17:29:31 localhost kernel: Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 0
May 16 17:29:31 localhost kernel: Attached scsi generic sg2 at scsi2, channel 0, id 0, lun 0,  type 5
May 16 17:29:31 localhost hal.hotplug[3711]: timout(10000 ms) waiting for /bus/pci/slots 
May 16 17:29:31 localhost pci.agent[7175]: Bad PCI agent invocation
May 16 17:29:32 localhost kernel: ACPI: Power Button (FF) [PWRF]
May 16 17:29:32 localhost kernel: IBM machine detected. Enabling interrupts during APM calls.
May 16 17:29:32 localhost kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 16 17:29:32 localhost kernel: apm: overridden by ACPI.
May 16 17:29:34 localhost kernel: pwc Failed to set LED on/off time.
May 16 17:29:50 localhost gconfd (max-8287): Inizializzazione (versione 2.10.0), pid 8287, utente 'max'
May 16 17:29:50 localhost gconfd (max-8287): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.mandatory" Ã¨ stato risolta ad una fonte di configurazione in sola lettura in posizione 0
May 16 17:29:50 localhost gconfd (max-8287): L'indirizzo "xml:readwrite:/home/max/.gconf" Ã¨ stato risolto ad una fonte di configurazione scrivibile in posizione 1
May 16 17:29:50 localhost gconfd (max-8287): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.defaults" Ã¨ stato risolta ad una fonte di configurazione in sola lettura in posizione 2
May 16 17:29:57 localhost gconfd (max-8287): L'indirizzo "xml:readwrite:/home/max/.gconf" Ã¨ stato risolto ad una fonte di configurazione scrivibile in posizione 0
May 16 17:29:58 localhost kernel: NTFS driver 2.1.22 [Flags: R/O MODULE].
May 16 17:29:58 localhost kernel: NTFS volume version 3.1.
May 16 17:30:01 localhost kernel:  [schedule+1293/1298] schedule+0x50d/0x512
May 16 17:30:01 localhost kernel:  [__get_free_pages+51/63] __get_free_pages+0x33/0x3f
May 16 17:30:01 localhost kernel:  [schedule_timeout+99/183] schedule_timeout+0x63/0xb7
May 16 17:30:01 localhost kernel:  [process_timeout+0/9] process_timeout+0x0/0x9
May 16 17:30:01 localhost kernel:  [do_poll+161/192] do_poll+0xa1/0xc0
May 16 17:30:01 localhost kernel:  [sys_poll+335/527] sys_poll+0x14f/0x20f
May 16 17:30:01 localhost kernel:  [sys_gettimeofday+59/127] sys_gettimeofday+0x3b/0x7f
May 16 17:30:01 localhost kernel:  [__pollwait+0/198] __pollwait+0x0/0xc6
May 16 17:30:01 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75



```

---

### Post by DavidGoodwin on 2005-10-20
Hi,

Make sure you've booted the box with the "noapic" and "apic=off" kernel command line options; without these you'll find it (the A50) freezes regularly (at least on the newer revisions this is true)

---

### Post by Thruston on 2006-09-27
That should be "acpi=off" of course.  APIC is not the same as ACPI.

IBM A50 users should also probably upgrade their BIOS to the latest level from IBM PC support.  At least that has helped mine (an 8084-7GG model).

Toby

---

### Post by Thruston on 2006-10-30
The BIOS might help you but it was fairly irrelevant to my system, it just took longer before it froze. 

The only remedy is to add acpi=off and noapic to your boot parameters in /boot/grub/menu.lst

I also note with disgust that the Edgy upgrade does *not* preserve these boot parameters, so I have to add them again (as my system is now frozen again just after I have completed upgrading. :-(

---

### Post by papayiya on 2007-09-24
This thread helped me bigtime..
As for your problem of not preserving the boot parameters, follow this article here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

