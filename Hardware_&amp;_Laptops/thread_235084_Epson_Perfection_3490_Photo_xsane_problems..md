---
title: "Epson Perfection 3490 Photo xsane problems."
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by lonrot on 2006-08-12
I've found the firmware file needed and placed it on usr/share/sane/snapscan.
esfw32.bin.

Also did these steps:

```
lonrot@MELOMANO:~$ scanimage -L 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
lonrot@MELOMANO:~$ sane-find-scanner 
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:005:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
lonrot@MELOMANO:~$

```

Also I found this guide, which I have found myself clueless. I don't know what is "machine$", etc:

```
   1.  detect your scanner device

      machine# tools/find-scanner
         find-scanner: found scanner "AGFA SNAPSCAN 310 1.20" at device
         /dev/XXXXX 

   2. if you want your scanner to be recognized easily, create a link. For SCSI scanners use:

      machine# ln -s /dev/XXXXX /dev/scanner

      For USB scanners use:

      machine# ln -s /dev/XXXXX /dev/usbscanner

   3. you should now scan using xscanimage

      machine$ xscanimage
```

When I run xsane I get this error (as user or root):
Failed to open device snapscan:lubusb:005:002
Invalid argument.

Some help would be greatly apreaciated.

Thanks.

---

### Post by zxee on 2006-08-12
The machine# in the information you posted just refers to your computer id aka what you see when you 1st open your terminal. It's telling you to create a link to your scanner. I see that support for your model is not complete
[http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=perfection+3490&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=perfection+3490&bus=any&v=&p=)
although it seems that it should work.
Take a  look at the output of dmesg and/or post it here. If dmesg tells you a dev/xxx address for the scanner you can use the instructions you have to create a link. Hope that helps.

---

### Post by lonrot on 2006-08-13
```
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fc140
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa4d0
[17179569.184000] ACPI: RSDT (v001 AMIINT VIA_K8   0x00000010 MSFT 0x00000097) @ 0x3fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT VIA_K8   0x00000011 MSFT 0x00000097) @ 0x3fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT VIA_K8   0x00000009 MSFT 0x00000097) @ 0x3fff00c0
[17179569.184000] ACPI: DSDT (v001    VIA   VIA_K8 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdc2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2200.428 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.324000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.324000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179570.344000] Memory: 1028816k/1048512k available (1976k kernel code, 18936k reserved, 606k data, 288k init, 131008k highmem)
[17179570.344000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.424000] Calibrating delay using timer specific routine.. 4405.29 BogoMIPS (lpj=8810595)
[17179570.424000] Security Framework v1.0.0 initialized
[17179570.424000] SELinux:  Disabled at boot.
[17179570.424000] Mount-cache hash table entries: 512
[17179570.424000] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179570.424000] CPU: After vendor identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179570.424000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.424000] CPU: L2 Cache: 512K (64 bytes/line)
[17179570.424000] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[17179570.424000] mtrr: v2.0 (20020519)
[17179570.424000] CPU: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[17179570.424000] Enabling fast FPU save and restore... done.
[17179570.424000] Enabling unmasked SIMD FPU exception support... done.
[17179570.424000] Checking 'hlt' instruction... OK.
[17179570.440000] checking if image is initramfs... it is
[17179570.892000] Freeing initrd memory: 6617k freed
[17179570.900000] ACPI: Looking for DSDT ... not found!
[17179570.900000] ENABLING IO-APIC IRQs
[17179570.900000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.048000] NET: Registered protocol family 16
[17179571.048000] EISA bus registered
[17179571.048000] ACPI: bus type pci registered
[17179571.048000] PCI: PCI BIOS revision 2.10 entry at 0xfda81, last bus=1
[17179571.048000] PCI: Using configuration type 1
[17179571.048000] ACPI: Subsystem revision 20051216
[17179571.048000] ACPI: Interpreter enabled
[17179571.048000] ACPI: Using IOAPIC for interrupt routing
[17179571.052000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.052000] PCI: Probing PCI hardware (bus 00)
[17179571.052000] Boot video device is 0000:01:00.0
[17179571.052000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.072000] ACPI: Power Resource [URP1] (off)
[17179571.072000] ACPI: Power Resource [URP2] (off)
[17179571.072000] ACPI: Power Resource [FDDP] (off)
[17179571.072000] ACPI: Power Resource [LPTP] (off)
[17179571.072000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179571.072000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179571.072000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179571.072000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179571.072000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.072000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.076000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.076000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179571.076000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.076000] pnp: PnP ACPI init
[17179571.076000] pnp: PnP ACPI: found 9 devices
[17179571.076000] PnPBIOS: Disabled by ACPI PNP
[17179571.076000] PCI: Using ACPI for IRQ routing
[17179571.076000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.080000] PCI: Bridge: 0000:00:01.0
[17179571.080000]   IO window: disabled.
[17179571.080000]   MEM window: cde00000-cfefffff
[17179571.080000]   PREFETCH window: add00000-cdcfffff
[17179571.080000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.080000] audit: initializing netlink socket (disabled)
[17179571.080000] audit(1155473713.080:1): initialized
[17179571.080000] highmem bounce pool size: 64 pages
[17179571.080000] VFS: Disk quotas dquot_6.5.1
[17179571.080000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.080000] Initializing Cryptographic API
[17179571.080000] io scheduler noop registered
[17179571.080000] io scheduler anticipatory registered
[17179571.080000] io scheduler deadline registered
[17179571.080000] io scheduler cfq registered
[17179571.080000] isapnp: Scanning for PnP cards...
[17179571.436000] isapnp: No Plug & Play device found
[17179571.444000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179571.444000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.444000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.444000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.444000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.444000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.448000] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.448000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.448000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.448000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.448000] mice: PS/2 mouse device common for all mice
[17179571.448000] EISA: Probing bus 0 at eisa.0
[17179571.448000] EISA: Detected 0 cards.
[17179571.448000] NET: Registered protocol family 2
[17179571.488000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.488000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179571.488000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.488000] TCP: Hash tables configured (established 262144 bind 65536)
[17179571.488000] TCP reno registered
[17179571.488000] TCP bic registered
[17179571.488000] NET: Registered protocol family 1
[17179571.488000] NET: Registered protocol family 8
[17179571.488000] NET: Registered protocol family 20
[17179571.488000] Using IPI Shortcut mode
[17179571.488000] ACPI wakeup devices:
[17179571.488000] PCI0 UAR1 USB1 USB2 USB3 USB4 EHCI USBD  AC9  MC9 ILAN SLPB
[17179571.488000] ACPI: (supports S0 S1 S4 S5)
[17179571.488000] Freeing unused kernel memory: 288k freed
[17179571.528000] vga16fb: initializing
[17179571.528000] vga16fb: mapped to 0xc00a0000
[17179571.660000] Console: switching to colour frame buffer device 80x25
[17179571.660000] fb0: VGA16 VGA frame buffer device
[17179571.864000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.892000] input: AT Translated Set 2 keyboard as /class/input/input1
[17179572.784000] Capability LSM initialized
[17179573.236000] SCSI subsystem initialized
[17179573.236000] ACPI: bus type scsi registered
[17179573.236000] libata version 1.20 loaded.
[17179573.240000] sata_via 0000:00:0f.0: version 1.1
[17179573.240000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 169
[17179573.240000] sata_via 0000:00:0f.0: routed to hard irq line 10
[17179573.240000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 169
[17179573.240000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 169
[17179574.460000] scsi0 : sata_via
[17179575.680000] scsi1 : sata_via
[17179575.700000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[17179575.700000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 169
[17179575.700000] PCI: VIA IRQ fixup for 0000:00:0f.1, from 255 to 9
[17179575.700000] VP_IDE: chipset revision 6
[17179575.700000] VP_IDE: not 100% native mode: will probe irqs later
[17179575.700000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[17179575.700000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:DMA
[17179575.700000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[17179575.700000] Probing IDE interface ide0...
[17179576.844000] hdb: LITE-ON DVD SOHD-167T, ATAPI CD/DVD-ROM drive
[17179576.900000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.900000] Probing IDE interface ide1...
[17179577.316000] hdc: ST3120022A, ATA DISK drive
[17179577.764000] hdd: HL-DT-ST DVDRAM GSA-4081B, ATAPI CD/DVD-ROM drive
[17179577.820000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.848000] hdb: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179577.848000] Uniform CD-ROM driver Revision: 3.20
[17179577.848000] hdc: max request size: 1024KiB
[17179577.848000] hdc: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.848000] hdc: cache flushes supported
[17179577.848000]  hdc: hdc1 hdc2 hdc3 < hdc5 >
[17179577.892000] hdd: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.228000] ieee1394: Initialized config rom entry `ip1394'
[17179578.228000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179578.228000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179578.296000] usbcore: registered new driver usbfs
[17179578.296000] usbcore: registered new driver hub
[17179578.296000] USB Universal Host Controller Interface driver v2.3
[17179578.368000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[177]  MMIO=[cfffb000-cfffb7ff]  Max Packet=[2048]
[17179578.376000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 185
[17179578.376000] PCI: VIA IRQ fixup for 0000:00:10.0, from 11 to 9
[17179578.376000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.376000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179578.376000] uhci_hcd 0000:00:10.0: irq 185, io base 0x0000c400
[17179578.376000] hub 1-0:1.0: USB hub found
[17179578.376000] hub 1-0:1.0: 2 ports detected
[17179578.480000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 185
[17179578.480000] PCI: VIA IRQ fixup for 0000:00:10.1, from 11 to 9
[17179578.480000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.480000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.480000] uhci_hcd 0000:00:10.1: irq 185, io base 0x0000c800
[17179578.480000] hub 2-0:1.0: USB hub found
[17179578.480000] hub 2-0:1.0: 2 ports detected
[17179578.584000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 185
[17179578.584000] PCI: VIA IRQ fixup for 0000:00:10.2, from 5 to 9
[17179578.584000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.584000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179578.584000] uhci_hcd 0000:00:10.2: irq 185, io base 0x0000cc00
[17179578.584000] hub 3-0:1.0: USB hub found
[17179578.584000] hub 3-0:1.0: 2 ports detected
[17179578.688000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 185
[17179578.688000] PCI: VIA IRQ fixup for 0000:00:10.3, from 5 to 9
[17179578.688000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179578.688000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179578.688000] uhci_hcd 0000:00:10.3: irq 185, io base 0x0000d000
[17179578.688000] hub 4-0:1.0: USB hub found
[17179578.688000] hub 4-0:1.0: 2 ports detected
[17179578.792000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 185
[17179578.792000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179578.792000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179578.792000] ehci_hcd 0000:00:10.4: irq 185, io mem 0xcfffbe00
[17179578.792000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.792000] hub 5-0:1.0: USB hub found
[17179578.792000] hub 5-0:1.0: 8 ports detected
[17179578.848000] usb 1-2: new low speed USB device using uhci_hcd and address 2[17179578.960000] Attempting manual resume
[17179578.980000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179578.980000] EXT3-fs: write access will be enabled during recovery.
[17179579.648000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc000084bff5]
[17179580.288000] usb 1-2: new low speed USB device using uhci_hcd and address 3[17179580.700000] usb 2-1: new low speed USB device using uhci_hcd and address 2[17179580.892000] usbcore: registered new driver hiddev
[17179580.916000] input: LuenKeung Co.,Ltd USB  Joystick as /class/input/input2
[17179580.916000] input: USB HID v1.10 Joystick [LuenKeung Co.,Ltd USB  Joystick] on usb-0000:00:10.0-2
[17179580.956000] input: HID 1241:1177 as /class/input/input3
[17179580.956000] input: USB HID v1.00 Mouse [HID 1241:1177] on usb-0000:00:10.1-1
[17179580.956000] usbcore: registered new driver usbhid
[17179580.956000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179583.248000] EXT3-fs: recovery complete.
[17179583.248000] kjournald starting.  Commit interval 5 seconds
[17179583.256000] EXT3-fs: mounted filesystem with ordered data mode.
[17179590.960000] ts: Compaq touchscreen protocol output
[17179592.000000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.020000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.040000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.052000] agpgart: Detected AGP bridge 0
[17179592.060000] agpgart: AGP aperture is 128M @ 0xd0000000
[17179592.112000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179592.268000] Floppy drive(s): fd0 is 1.44M
[17179592.292000] FDC 0 is a post-1991 82077
[17179592.304000] nvidia: module license 'NVIDIA' taints kernel.
[17179592.316000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179592.316000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
[17179592.360000] Real Time Clock Driver v1.12
[17179592.376000] parport: PnPBIOS parport detected.
[17179592.376000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179592.596000] input: PC Speaker as /class/input/input4
[17179592.684000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179592.684000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 201
[17179592.684000] eth0: VIA Rhine II at 0x1bc00, 00:11:09:a0:57:da, IRQ 201.
[17179592.684000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179592.744000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 209
[17179592.744000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179593.412000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179593.768000] lp0: using parport0 (interrupt-driven).
[17179593.796000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179593.796000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179593.796000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179593.852000] Adding 891568k swap on /dev/hdc5.  Priority:-1 extents:1 across:891568k
[17179593.988000] EXT3 FS on hdc2, internal journal
[17179594.108000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179594.108000] md: bitmap version 4.39
[17179594.828000] NET: Registered protocol family 17
[17179594.936000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179595.828000] NET: Registered protocol family 10
[17179595.828000] lo: Disabled Privacy Extensions
[17179595.828000] IPv6 over IPv4 tunneling driver
[17179596.140000] cdrom: open failed.
[17179596.592000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179596.652000] NTFS volume version 3.1.
[17179602.176000] ACPI: Power Button (FF) [PWRF]
[17179602.176000] ACPI: Power Button (CM) [PWRB]
[17179602.176000] ACPI: Sleep Button (CM) [SLPB]
[17179602.256000] ibm_acpi: ec object not found
[17179602.292000] pcc_acpi: loading...
[17179602.776000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179602.780000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[17179606.376000] eth0: no IPv6 routers present
[17179606.820000] ppdev: user-space parallel port driver
[17179607.056000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179607.060000] apm: overridden by ACPI.
[17179609.208000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179609.208000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179609.208000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179609.432000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179609.432000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179609.432000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179609.964000] Bluetooth: Core ver 2.8
[17179609.964000] NET: Registered protocol family 31
[17179609.964000] Bluetooth: HCI device and connection manager initialized
[17179609.964000] Bluetooth: HCI socket layer initialized
[17179609.980000] Bluetooth: L2CAP ver 2.8
[17179609.980000] Bluetooth: L2CAP socket layer initialized
[17179610.028000] Bluetooth: RFCOMM socket layer initialized
[17179610.028000] Bluetooth: RFCOMM TTY layer initialized
[17179610.028000] Bluetooth: RFCOMM ver 1.7
[17179625.620000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179625.996000] ISOFS: changing to secondary root
[17179917.744000] ibm_acpi: ec object not found

```

By the way where can I edit the machine stuff. And yeah now I know what's the name of the machine. 
Thanks!

---

### Post by lonrot on 2006-08-17
Please, I would really appreciate some help.

---

### Post by zxee on 2006-08-17
>  1.  detect your scanner device

      machine# tools/find-scanner
         find-scanner: found scanner "AGFA SNAPSCAN 310 1.20" at device
         /dev/XXXXX 

   2. if you want your scanner to be recognized easily, create a link. For SCSI scanners use:

      machine# ln -s /dev/XXXXX /dev/scanner

      For USB scanners use:

      machine# ln -s /dev/XXXXX /dev/usbscanner

   3. you should now scan using xscanimage

      machine$ xscanimage

That short howto should work.
What do you get when you enter > sane-find-scanner 
in a terminal? 
Whatever you get for /dev/xxx is what you use to create a link to the scanner (using the above quoted method) so if sane-find-scanner returns /dev/sca then that what you use to create the link. 
In ubuntu you might have to use sudo before the command(s)
The link command is > ln -s /dev/sca /dev/usbscanner
Note: replace the sca with the actual results you get from sane-find-scanner.

---

