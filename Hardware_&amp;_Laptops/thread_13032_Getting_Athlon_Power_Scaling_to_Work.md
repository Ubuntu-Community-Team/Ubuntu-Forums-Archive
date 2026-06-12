---
title: "Getting Athlon Power Scaling to Work?"
date: 2005-01-28
forum: Hardware &amp; Laptops
---

### Post by ph00dz on 2005-01-28
First of all... let me say "thank you" to the folks who put this distro together. So far, it's awesome.

Most of my laptop stuff works (including the wireless, thanks to ndiswrapper ). Still, my laptop is running way hot sometimes...

How can I do the athlon power scaling stuff without acpi working? (I had to flip it off to get running... ) I have a HP pavilion ze4560, for whatever it's worth...

If it'd make a difference,I can certainly recompile the kernal... but will it becobvious when the scaling is in effect? Can I have it scale down by hand if I want?

Here's my dmesg:

```


Linux version 2.6.8.1-3-686 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 13:10:36 BST 2004
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
 BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000037ef0000 (usable)
 BIOS-e820: 0000000037ef0000 - 0000000037eff000 (ACPI data)
 BIOS-e820: 0000000037eff000 - 0000000037f00000 (ACPI NVS)
 BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
894MB LOWMEM available.
On node 0 totalpages: 229104
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 225008 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro acpi=off noacpi quiet splash apm=on 
Local APIC disabled by BIOS -- reenabling.
Found and enabled local APIC!
Initializing CPU#0
PID hash table entries: 4096 (order 12: 32768 bytes)
Detected 1855.081 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 900684k/916416k available (1469k kernel code, 14980k reserved, 689k data, 140k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3661.82 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000
CPU: After vendor identify, caps:  0383fbff c1cbfbff 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: After all inits, caps:        0383fbff c1cbfbff 00000000 00000020
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU: AMD mobile AMD Athlon(tm) XP2500+ stepping 00
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
enabled ExtINT on CPU#0
ESR value before enabling vector: 00000000
ESR value after enabling vector: 00000000
Using local APIC timer interrupts.
calibrating APIC timer ...
..... CPU clock speed is 1855.0042 MHz.
..... host bus clock speed is 265.0006 MHz.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4356k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f72c0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa0e7, dseg 0x400
spurious 8259A interrupt: IRQ7.
pnp: 00:00: ioport range 0x370-0x371 has been reserved
pnp: 00:0b: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:0b: ioport range 0x40b-0x40b has been reserved
pnp: 00:0b: ioport range 0x480-0x48f has been reserved
pnp: 00:0b: ioport range 0x4d6-0x4d6 has been reserved
pnp: 00:0b: ioport range 0x8000-0x803f has been reserved
pnp: 00:0b: ioport range 0x8040-0x807f has been reserved
PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Using ALI IRQ Router
PCI: Using IRQ router ALI [10b9/1533] at 0000:00:07.0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb.
Activating ISA DMA hang workarounds.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
PCI: Found IRQ 3 for device 0000:00:08.0
ttyS47 at I/O 0x8828 (irq = 3) is a 8250
ttyS1 at I/O 0x8840 (irq = 3) is a 8250
ttyS2 at I/O 0x8850 (irq = 3) is a 8250
ttyS3 at I/O 0x8860 (irq = 3) is a 8250
ttyS4 at I/O 0x8870 (irq = 3) is a 8250
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4356 blocks [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 140k freed
vesafb: probe of vesafb0 failed with error -6
thermal: Unknown symbol acpi_processor_set_thermal_limit
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Warning: ATI Radeon IGP Northbridge is not yet fully tested.
ALI15X3: IDE controller at PCI slot 0000:00:10.0
ALI15X3: chipset revision 196
ALI15X3: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x8080-0x8087, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:pio, hdd:pio
hda: IC25N040ATCS04-0, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 78140160 sectors (40007 MB) w/1768KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdc: SAMSUNG CDRW/DVD SN-324F, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 500432k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
apm: BIOS not found.
powernow_k7: Unknown symbol acpi_processor_unregister_performance
powernow_k7: Unknown symbol acpi_processor_register_performance
SCSI subsystem initialized
Synaptics Touchpad, model: 1
 Firmware: 5.9
 Sensor: 35
 new absolute packet format
 Touchpad has extended capability bits
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio1
mice: PS/2 mouse device common for all mice
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
Uniform CD-ROM driver Revision: 3.20
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: dm@uk.sistina.com
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.8.1-3-686
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected Ati IGP320/M chipset
agpgart: Maximum main memory to use for agp memory: 814M
agpgart: AGP aperture is 64M @ 0xd4000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
PCI: Assigned IRQ 9 for device 0000:00:02.0
ohci_hcd 0000:00:02.0: ALi Corporation USB 1.1 Controller
ohci_hcd 0000:00:02.0: irq 9, pci mem f89e9000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 4 ports detected
PCI: Found IRQ 5 for device 0000:00:06.0
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: IRQ 10 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
PCI: Found IRQ 10 for device 0000:00:0a.0
Yenta: CardBus bridge found at 0000:00:0a.0 [0000:0000]
Yenta: ISA IRQ mask 0x0818, PCI irq 10
Socket status: 30000007
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Found IRQ 10 for device 0000:00:0c.0
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0009000-d00097ff]  Max Packet=[2048]
natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
  originally by Donald Becker <becker@scyld.com>
  http://www.scyld.com/network/natsemi.html
  2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
PCI: Found IRQ 11 for device 0000:00:12.0
natsemi eth0: NatSemi DP8381[56] at 0xf8aaa000 (0000:00:12.0), 00:0d:9d:82:5c:35, IRQ 11, port TP.
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000d9d719e821ef4]
eth0: DSPCFG accepted after 0 usec.
NET: Registered protocol family 17
ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
PCI: Found IRQ 9 for device 0000:00:09.0
ndiswrapper: using irq 9
wlan0: ndiswrapper ethernet device 00:90:4b:47:f7:d6 using driver bcmwl5.sys
ndiswrapper device wlan0 supports WPA with AES/CCMP and TKIP ciphers
ndiswrapper: driver bcmwl5.sys (Broadcom,10/28/2003, 3.40.25.3) added
ndiswrapper (add_driver:1867): Cannot add duplicate driver
cs: IO port probe 0x0100-0x04ff: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02ea8a0(lo)
IPv6 over IPv4 tunneling driver
acpi: Unknown symbol acpi_processor_unregister_performance
acpi: Unknown symbol acpi_processor_register_performance
wlan0: no IPv6 routers present
eth0: no IPv6 routers present



```

---

