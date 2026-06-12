---
title: "can't get Microsolutions Backpack dvd+rw to work in Warty"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by gangalee on 2005-02-15
I've got a [USB DVD+rw](http://www.micro-solutions.com/downloads/linux/index3.asp)  that I can't seem to get fully working under Warty.
I've attached different outputs. Please let me know what else I can do to get it working or further output to troubleshoot.

Thanks

dmesg
```
Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000007fec000 (usable)
 BIOS-e820: 0000000007fec000 - 0000000007ff0000 (reserved)
 BIOS-e820: 00000000100a0000 - 0000000010100000 (reserved)
 BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
127MB LOWMEM available.
On node 0 totalpages: 32748
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 28652 pages, LIFO batch:6
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI disabled because your bios is from 2000 and too old
You can enable it with acpi=force
Built 1 zonelists
Kernel command line: root=/dev/hda5 ro quiet splash noapic
Local APIC disabled by BIOS -- reenabling.
Could not enable APIC!
Initializing CPU#0
PID hash table entries: 512 (order 9: 4096 bytes)
Detected 498.688 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 122604k/130992k available (1336k kernel code, 7840k reserved, 728k data, 204k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 985.08 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000
CPU: After vendor identify, caps:  0383f9ff 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU: After all inits, caps:        0383f9ff 00000000 00000000 00000040
CPU: Intel Pentium III (Coppermine) stepping 03
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4116k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfc0ce, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fe2d0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xe2f4, dseg 0x40
pnp: 00:01: ioport range 0x800-0x83f has been reserved
pnp: 00:01: ioport range 0x840-0x84f has been reserved
pnp: 00:01: ioport range 0x3f0-0x3f1 has been reserved
pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 512 buckets, 4Kbytes
TCP: Hash tables configured (established 8192 bind 16384)
NET: Registered protocol family 8
NET: Registered protocol family 20
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4116 blocks [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
thermal: Unknown symbol acpi_processor_set_thermal_limit
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX4: IDE controller at PCI slot 0000:00:07.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x0860-0x0867, BIOS settings: hda:DMA, hdb:pio
hda: FUJITSU MHT2030AT, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(33)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 p7 p8 >
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 184696k swap on /dev/hda7.  Priority:-1 extents:1
EXT3 FS on hda5, internal journal
input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: dm@uk.sistina.com
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda8, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
input: PC Speaker
Real Time Clock Driver v1.12
inserting floppy driver for 2.6.8.1-3-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 440BX Chipset.
agpgart: Maximum main memory to use for agp memory: 94M
agpgart: AGP aperture is 64M @ 0xf4000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Found IRQ 11 for device 0000:00:03.0
PCI: Sharing IRQ 11 with 0000:00:03.1
PCI: Sharing IRQ 11 with 0000:00:07.2
Yenta: CardBus bridge found at 0000:00:03.0 [1028:0091]
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:03.0, mfunc 0x01261222, devctl 0x66
Yenta: ISA IRQ mask 0x0618, PCI irq 11
Socket status: 30000020
PCI: Found IRQ 11 for device 0000:00:03.1
PCI: Sharing IRQ 11 with 0000:00:03.0
PCI: Sharing IRQ 11 with 0000:00:07.2
Yenta: CardBus bridge found at 0000:00:03.1 [1028:0091]
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:03.1, mfunc 0x01261222, devctl 0x66
Yenta: ISA IRQ mask 0x0618, PCI irq 11
Socket status: 30000006
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Enabling device 0000:02:00.2 (0000 -> 0002)
ehci_hcd 0000:02:00.2: NEC Corporation USB 2.0
ehci_hcd 0000:02:00.2: irq 11, pci mem c892d000
ehci_hcd 0000:02:00.2: new USB bus registered, assigned bus number 1
ehci_hcd 0000:02:00.2: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
ohci_hcd 0000:02:00.0: NEC Corporation USB
PCI: Setting latency timer of device 0000:02:00.0 to 64
ohci_hcd 0000:02:00.0: irq 11, pci mem c892f000
ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
PCI: Enabling device 0000:02:00.1 (0000 -> 0002)
ohci_hcd 0000:02:00.1: NEC Corporation USB (#2)
PCI: Setting latency timer of device 0000:02:00.1 to 64
ohci_hcd 0000:02:00.1: irq 11, pci mem c8938000
ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 1 port detected
usb 1-1: new high speed USB device using address 2
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
acpi: Unknown symbol acpi_processor_unregister_performance
acpi: Unknown symbol acpi_processor_register_performance
udf: registering filesystem
paride: bpck registered as protocol 0
```

lsmod
```
Module                  Size  Used by
bpck                    9984  0 
paride                  8704  1 bpck
isofs                  33976  0 
udf                    79876  0 
proc_intf               3968  0 
freq_table              4356  0 
cpufreq_userspace       5336  0 
cpufreq_powersave       2048  0 
ipv6                  230020  14 
ds                     17796  4 
ohci_hcd               19460  0 
ehci_hcd               27780  0 
usbcore               104292  4 ohci_hcd,ehci_hcd
yenta_socket           19328  1 
pcmcia_core            63156  2 ds,yenta_socket
pci_hotplug            30640  0 
intel_agp              20512  1 
agpgart                31784  1 intel_agp
floppy                 54996  0 
rtc                    12216  0 
pcspkr                  3816  0 
nls_iso8859_1           4352  1 
nls_cp437               6016  1 
vfat                   13312  1 
fat                    41792  1 vfat
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
parport_pc             32064  1 
lp                     10436  0 
tsdev                   7168  0 
parport                37320  3 paride,parport_pc,lp
evdev                   9088  0 
ide_cd                 38276  0 
cdrom                  35872  1 ide_cd
mousedev               10124  1 
psmouse                17800  0 
ext3                  109544  4 
jbd                    54552  1 ext3
ide_generic             1664  0 
piix                   12576  1 
ide_disk               16768  7 
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  787 
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
```

lspci
```
Module                  Size  Used by
bpck                    9984  0 
paride                  8704  1 bpck
isofs                  33976  0 
udf                    79876  0 
proc_intf               3968  0 
freq_table              4356  0 
cpufreq_userspace       5336  0 
cpufreq_powersave       2048  0 
ipv6                  230020  14 
ds                     17796  4 
ohci_hcd               19460  0 
ehci_hcd               27780  0 
usbcore               104292  4 ohci_hcd,ehci_hcd
yenta_socket           19328  1 
pcmcia_core            63156  2 ds,yenta_socket
pci_hotplug            30640  0 
intel_agp              20512  1 
agpgart                31784  1 intel_agp
floppy                 54996  0 
rtc                    12216  0 
pcspkr                  3816  0 
nls_iso8859_1           4352  1 
nls_cp437               6016  1 
vfat                   13312  1 
fat                    41792  1 vfat
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
parport_pc             32064  1 
lp                     10436  0 
tsdev                   7168  0 
parport                37320  3 paride,parport_pc,lp
evdev                   9088  0 
ide_cd                 38276  0 
cdrom                  35872  1 ide_cd
mousedev               10124  1 
psmouse                17800  0 
ext3                  109544  4 
jbd                    54552  1 ext3
ide_generic             1664  0 
piix                   12576  1 
ide_disk               16768  7 
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  787 
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
```

messages
```
Feb 15 16:16:19 localhost kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Feb 15 16:16:19 localhost kernel: IPv6 over IPv4 tunneling driver
Feb 15 16:16:19 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Feb 15 16:16:19 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb 15 16:16:57 localhost gconfd (cwa2-3537): starting (version 2.8.1), pid 3537 user 'cwa2'
Feb 15 16:16:57 localhost gconfd (cwa2-3537): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 15 16:16:57 localhost gconfd (cwa2-3537): Resolved address "xml:readwrite:/home/cwa2/.gconf" to a writable configuration source at position 1
Feb 15 16:16:57 localhost gconfd (cwa2-3537): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 15 16:17:31 localhost gconfd (cwa2-3537): Resolved address "xml:readwrite:/home/cwa2/.gconf" to a writable configuration source at position 0
Feb 15 16:19:15 localhost kernel: udf: registering filesystem
```

---

### Post by gangalee on 2005-02-22
after modifying my /etc/hotplug/usb.handmap
```
#these are the entries for bpck-usb devices
bpckusb 0x0003 0x0ac9 0x0000 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x0001 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x1000 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x1001 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x1002 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x1003 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x1004 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x1005 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x1006 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x1007 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x0010 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
bpckusb 0x0003 0x0ac9 0x0011 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
usb-storage 0x0003 0x0ac9 0x10ff 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000
``` 

updated lsmod:
```

Module                  Size  Used by
bpck                    9984  0 
paride                  8704  1 bpck
usb_storage            59200  0 
scsi_mod              115148  1 usb_storage
proc_intf               3968  0 
freq_table              4356  0 
cpufreq_userspace       5336  0 
cpufreq_powersave       2048  0 
ipv6                  230020  14 
ds                     17796  4 
af_packet              20872  0 
ohci_hcd               19460  0 
ehci_hcd               27780  0 
usbcore               104292  5 usb_storage,ohci_hcd,ehci_hcd
yenta_socket           19328  1 
pcmcia_core            63156  2 ds,yenta_socket
pci_hotplug            30640  0 
intel_agp              20512  1 
agpgart                31784  1 intel_agp
floppy                 54996  0 
rtc                    12216  0 
pcspkr                  3816  0 
nls_iso8859_1           4352  1 
nls_cp437               6016  1 
vfat                   13312  1 
fat                    41792  1 vfat
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
parport_pc             32064  1 
lp                     10436  0 
tsdev                   7168  0 
parport                37320  3 paride,parport_pc,lp
evdev                   9088  0 
ide_cd                 38276  0 
cdrom                  35872  1 ide_cd
mousedev               10124  1 
psmouse                17800  0 
ext3                  109544  4 
jbd                    54552  1 ext3
ide_generic             1664  0 
piix                   12576  1 
ide_disk               16768  7 
ide_core              125272  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   25904  753 
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
``` 

dmesg: ```
Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000007fec000 (usable)
 BIOS-e820: 0000000007fec000 - 0000000007ff0000 (reserved)
 BIOS-e820: 00000000100a0000 - 0000000010100000 (reserved)
 BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
127MB LOWMEM available.
On node 0 totalpages: 32748
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 28652 pages, LIFO batch:6
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI disabled because your bios is from 2000 and too old
You can enable it with acpi=force
Built 1 zonelists
Kernel command line: root=/dev/hda5 ro quiet splash noapic
Local APIC disabled by BIOS -- reenabling.
Could not enable APIC!
Initializing CPU#0
PID hash table entries: 512 (order 9: 4096 bytes)
Detected 498.547 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 122604k/130992k available (1336k kernel code, 7840k reserved, 728k data, 204k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 985.08 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000
CPU: After vendor identify, caps:  0387f9ff 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU serial number disabled.
CPU: After all inits, caps:        0383f9ff 00000000 00000000 00000040
CPU: Intel Pentium III (Coppermine) stepping 03
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4116k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfc0ce, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fe2d0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xe2f4, dseg 0x40
pnp: 00:01: ioport range 0x800-0x83f has been reserved
pnp: 00:01: ioport range 0x840-0x84f has been reserved
pnp: 00:01: ioport range 0x3f0-0x3f1 has been reserved
pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 512 buckets, 4Kbytes
TCP: Hash tables configured (established 8192 bind 16384)
NET: Registered protocol family 8
NET: Registered protocol family 20
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4116 blocks [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
thermal: Unknown symbol acpi_processor_set_thermal_limit
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX4: IDE controller at PCI slot 0000:00:07.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x0860-0x0867, BIOS settings: hda:DMA, hdb:pio
hda: FUJITSU MHT2030AT, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(33)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 p7 p8 >
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 184696k swap on /dev/hda7.  Priority:-1 extents:1
EXT3 FS on hda5, internal journal
input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: dm@uk.sistina.com
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda8, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
input: PC Speaker
Real Time Clock Driver v1.12
inserting floppy driver for 2.6.8.1-3-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 440BX Chipset.
agpgart: Maximum main memory to use for agp memory: 94M
agpgart: AGP aperture is 64M @ 0xf4000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Found IRQ 11 for device 0000:00:03.0
PCI: Sharing IRQ 11 with 0000:00:03.1
PCI: Sharing IRQ 11 with 0000:00:07.2
Yenta: CardBus bridge found at 0000:00:03.0 [1028:0091]
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:03.0, mfunc 0x01261222, devctl 0x66
Yenta: ISA IRQ mask 0x0618, PCI irq 11
Socket status: 30000020
PCI: Found IRQ 11 for device 0000:00:03.1
PCI: Sharing IRQ 11 with 0000:00:03.0
PCI: Sharing IRQ 11 with 0000:00:07.2
Yenta: CardBus bridge found at 0000:00:03.1 [1028:0091]
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:03.1, mfunc 0x01261222, devctl 0x66
Yenta: ISA IRQ mask 0x0618, PCI irq 11
Socket status: 30000006
usbcore: registered new driver usbfs
usbcore: registered new driver hub
PCI: Enabling device 0000:02:00.2 (0000 -> 0002)
ehci_hcd 0000:02:00.2: NEC Corporation USB 2.0
ehci_hcd 0000:02:00.2: irq 11, pci mem c892d000
ehci_hcd 0000:02:00.2: new USB bus registered, assigned bus number 1
ehci_hcd 0000:02:00.2: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
ohci_hcd 0000:02:00.0: NEC Corporation USB
PCI: Setting latency timer of device 0000:02:00.0 to 64
ohci_hcd 0000:02:00.0: irq 11, pci mem c8938000
ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
PCI: Enabling device 0000:02:00.1 (0000 -> 0002)
ohci_hcd 0000:02:00.1: NEC Corporation USB (#2)
PCI: Setting latency timer of device 0000:02:00.1 to 64
ohci_hcd 0000:02:00.1: irq 11, pci mem c8893000
ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 1 port detected
usb 1-3: new high speed USB device using address 2
NET: Registered protocol family 17
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
acpi: Unknown symbol acpi_processor_unregister_performance
acpi: Unknown symbol acpi_processor_register_performance
SCSI subsystem initialized
Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
paride: bpck registered as protocol 0
``` 

tail /var/log/messages:
```
Feb 22 18:00:43 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Feb 22 18:01:25 localhost gconfd (cwa2-3571): starting (version 2.8.1), pid 3571 user 'cwa2'
Feb 22 18:01:25 localhost gconfd (cwa2-3571): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 22 18:01:25 localhost gconfd (cwa2-3571): Resolved address "xml:readwrite:/home/cwa2/.gconf" to a writable configuration source at position 1
Feb 22 18:01:25 localhost gconfd (cwa2-3571): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 22 18:01:54 localhost gconfd (cwa2-3571): Resolved address "xml:readwrite:/home/cwa2/.gconf" to a writable configuration source at position 0
Feb 22 18:04:07 localhost kernel: SCSI subsystem initialized
Feb 22 18:04:07 localhost kernel: Initializing USB Mass Storage driver...
Feb 22 18:04:07 localhost kernel: usbcore: registered new driver usb-storage
Feb 22 18:04:07 localhost kernel: USB Mass Storage support registered.
``` 

I'm still not getting the /dev/ file! ](*,)

---

### Post by gangalee on 2005-02-22
making sure my avatar works

---

### Post by gangalee on 2005-03-14
I finally got the DVD+RW drive to show up as a /dev/sr0 after installing the PNP407D.EXE driver installation package on the Windows side and trying BPFLASH.exe to update the EEPROM.

It can be found at the top of this page:
[http://www.micro-solutions.com/downloads/index.asp](http://www.micro-solutions.com/downloads/index.asp)

However, the drive doesn't show up as Ubuntu's special /dev/hdc cdrom so it doesn't mount automatically, and more importantly, it doesn't mount as a rewritable or even writable device. How do I get that going?

---

### Post by gangalee on 2005-09-07
Got it working under Hoary!

after a while however, I get bad dvd-burns where the disk will complete burning, then will be unreadable, or it doesn't complete burning. 

Here's some output:
Devices
-----------------------
_NEC DVD+RW ND-1100A 1.A0 (/dev/scd0, ) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD+R; DVD+RW] [DVD-ROM; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; RAW/R96R]
HL-DT-ST CD-RW GCE-8483B B105 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
Using VA_DJ_DRAMA_PRESENTS_YOU000.RAR;1 for  newchoons/VA-DJ_Drama_Presents_Young_Jeezy-Trap_Or_Die-2005.rar (VA-DJ_Drama_Presents_Young_Jeezy-Tha_Streets_Iz_Watchin-2004-POiSE.rar)
/dev/scd0: "Current Write Speed" is 2.4x1385KBps.
[B]:-( unable to WRITE@LBA=0h: Input/output error
:-( write failed: Input/output error[/B] ](*,) 

growisofs comand:
-----------------------
/usr/bin/growisofs -Z /dev/scd0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=dao -dvd-compat -speed=2.4 -gui -graft-points -volid gator choons -volset  -appid K3B THE CD KREATOR VERSION 0.11.23 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher cwa2 -preparer K3b - Version 0.11.23 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /home/ira/.kde/tmp-gator/k3b1gorba.tmp -rational-rock -hide-list /home/ira/.kde/tmp-gator/k3bvaZ5Wb.tmp -full-iso9660-filenames -iso-level 2 -path-list /home/ira/.kde/tmp-gator/k3b4kVGra.tmp

---

