---
title: "5 minute delay before booting"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by bondu on 2005-05-04
When booting form the install CDs , I get the boot screen, hit return for normal install.  It loads the kernal then waits 5 mintues before uncompressiong the kernel.
Has anyone seen this problem before or know what could be cuasing it?

Tyan Tiger MP
Dual AMD Duron 1G


pci bus 0x0000 cardnum 0x00 function 0x00: vendor 0x1022 device 0x700c
 Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] System Controller

pci bus 0x0000 cardnum 0x01 function 0x00: vendor 0x1022 device 0x700d
 Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] AGP Bridge

pci bus 0x0000 cardnum 0x07 function 0x00: vendor 0x1022 device 0x7410
 Advanced Micro Devices [AMD] AMD-766 [ViperPlus] ISA

pci bus 0x0000 cardnum 0x07 function 0x01: vendor 0x1022 device 0x7411
 Advanced Micro Devices [AMD] AMD-766 [ViperPlus] IDE

pci bus 0x0000 cardnum 0x07 function 0x03: vendor 0x1022 device 0x7413
 Advanced Micro Devices [AMD] AMD-766 [ViperPlus] ACPI

pci bus 0x0000 cardnum 0x07 function 0x04: vendor 0x1022 device 0x7414
 Advanced Micro Devices [AMD] AMD-766 [ViperPlus] USB

pci bus 0x0000 cardnum 0x09 function 0x00: vendor 0x1106 device 0x3044
 VIA Technologies, Inc. IEEE 1394 Host Controller

pci bus 0x0000 cardnum 0x0a function 0x00: vendor 0x1412 device 0x1712
 IC Ensemble Inc ICE1712 [Envy24]

pci bus 0x0000 cardnum 0x0d function 0x00: vendor 0x8086 device 0x1229
 Intel Corp. 82557/8/9 [Ethernet Pro 100]

pci bus 0x0001 cardnum 0x05 function 0x00: vendor 0x102b device 0x2537
 Matrox Graphics, Inc.  Device unknown

---

### Post by superhac007 on 2005-05-04
Trying turing ACPI off...  Add acpi=off before booting as a kernel option.  I think you press 'e' when grub starts... or just type help at the prompt for a list of grub options.

---

### Post by bondu on 2005-05-04
I tried that already, and it did not work.

---

### Post by superhac007 on 2005-05-04
Have been able to install it?

---

### Post by bondu on 2005-05-04
yes, I was able to install it.  Everything works fine one I am logged in.

The only problem is every time I reboot, it takes 5 mintues before it start to uncompress the kernel.

---

### Post by superhac007 on 2005-05-04
[QUOTE=bondu]yes, I was able to install it.  Everything works fine one I am logged in.

The only problem is every time I reboot, it takes 5 mintues before it start to uncompress the kernel.[/QUOTE]

Okay... so its not just related to the install disks...  Let me look into it.

---

### Post by superhac007 on 2005-05-04
Can you post the output from this command:

```

# dmesg

```

When you turned off APIC in the kernel, DId you also turn it off in the BIOS?

---

### Post by bondu on 2005-05-09
Linux version 2.6.10-5-k7 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:56:05 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
 BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e4800 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000080000000 (usable)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
1152MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000f7510
On node 0 totalpages: 524288
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 225280 pages, LIFO batch:16
  HighMem zone: 294912 pages, LIFO batch:16
DMI 2.3 present.
ACPI: Unable to locate RSDP
Intel MultiProcessor Specification v1.4
    Virtual Wire compatibility mode.
OEM ID: TYAN     Product ID: GUINNESS     APIC at: 0xFEE00000
Processor #0 6:7 APIC version 16
Processor #1 6:7 APIC version 16
WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
I/O APIC #2 Version 17 at 0xFEC00000.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Processors: 1
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 65536 bytes)
Detected 1010.114 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 2071616k/2097152k available (1595k kernel code, 24580k reserved, 721k data, 164k init, 1179648k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1994.75 BogoMIPS (lpj=997376)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff c1c7fbff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383fbff c1c7fbff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 64K (64 bytes/line)
CPU: After all inits, caps: 0383fbff c1c7fbff 00000000 00000020 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU: AMD Duron(tm) MP Processor stepping 00
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=0
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4540k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfd7e0, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f74d0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9e7a, dseg 0x400
PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
pnp: 00:09: ioport range 0x4d0-0x4d1 has been reserved
audit: initializing netlink socket (disabled)
audit(1115618903.719:0): initialized
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
BIOS failed to enable PCI standards compliance, fixing this error.
I/O APIC: AMD Errata #22 may be present. In the event of instability try
        : booting with the "noapic" option.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 16384 buckets, 128Kbytes
TCP: Hash tables configured (established 524288 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kpnpbiosd not stopped
 Strange, kseriod not stopped
 done
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4540KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
AMD7411: IDE controller at PCI slot 0000:00:07.1
AMD7411: chipset revision 1
AMD7411: not 100% native mode: will probe irqs later
AMD7411: 0000:00:07.1 (rev 01) UDMA100 controller
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:DMA
Probing IDE interface ide0...
hda: ST3120026A, ATA DISK drive
hdb: Maxtor 6Y160P0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(33)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 p7 p8 p9 p10 >
hdb: max request size: 1024KiB
hdb: 320173056 sectors (163928 MB) w/7936KiB Cache, CHS=19929/255/63, UDMA(33)
hdb: cache flushes supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 p3
Probing IDE interface ide1...
hdc: Memorex CRW-1622, ATAPI CD/DVD-ROM drive
hdd: ATAPI 48X CDROM, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  -\|/-done (466 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 2048248k swap on /dev/hda7.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
hdc: ATAPI 6X CD-ROM CD-R/RW drive, 1024kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X CD-ROM drive, 128kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda8, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda5, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda9, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda10, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-k7
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected AMD 760MP chipset
agpgart: Maximum main memory to use for agp memory: 1920M
agpgart: AGP aperture is 64M @ 0xf4000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd 0000:00:07.4: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] USB
ohci_hcd 0000:00:07.4: irq 11, pci mem 0xdc000
ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 4 ports detected
usb 1-2: new low speed USB device using ohci_hcd and address 2
e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
e100: eth0: e100_probe: addr 0xf0101000, irq 5, MAC addr 00:90:27:62:87:DD
usbcore: registered new driver hiddev
input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouseÆ Explorer] on usb-0000:00:07.4-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ts: Compaq touchscreen protocol output
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0315d40(lo)
IPv6 over IPv4 tunneling driver

---

