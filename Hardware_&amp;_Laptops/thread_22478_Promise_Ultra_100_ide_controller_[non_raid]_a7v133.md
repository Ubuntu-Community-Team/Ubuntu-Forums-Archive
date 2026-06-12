---
title: "Promise Ultra 100 ide controller [non raid] a7v133 motherboard"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by discord on 2005-03-28
hello,

I have an a7v133 with the promise 20265 chipset. Whenever I mount the drives which are atached to the onboard promise controller and update the locatedb the machine crashes. Also if I activly use a drive attached to the promise controller it will crash, Anyone able to use their promise Ultra 100 without their computer crashing? I will post my dmesg output and the modules i have loded below.

Linux Version 2.6.8.1-5-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Mon Mar 14 21:44:04 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
 BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000002ffec000 (usable)
 BIOS-e820: 000000002ffec000 - 000000002ffef000 (ACPI data)
 BIOS-e820: 000000002ffef000 - 000000002ffff000 (reserved)
 BIOS-e820: 000000002ffff000 - 0000000030000000 (ACPI NVS)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
767MB LOWMEM available.
On node 0 totalpages: 196588
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 192492 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 ASUS                                  ) @ 0x000f6a80
ACPI: RSDT (v001 ASUS   A7V133-C 0x30303031 MSFT 0x31313031) @ 0x2ffec000
ACPI: FADT (v001 ASUS   A7V133-C 0x30303031 MSFT 0x31313031) @ 0x2ffec080
ACPI: BOOT (v001 ASUS   A7V133-C 0x30303031 MSFT 0x31313031) @ 0x2ffec040
ACPI: DSDT (v001   ASUS A7V133-C 0x00001000 MSFT 0x0100000b) @ 0x00000000
ACPI: PM-Timer IO Port: 0xe408
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
Local APIC disabled by BIOS -- reenabling.
Found and enabled local APIC!
Initializing CPU#0
PID hash table entries: 4096 (order 12: 32768 bytes)
Detected 1545.022 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 771896k/786352k available (1337k kernel code, 13692k reserved, 731k data, 204k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3055.61 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000
CPU: After vendor identify, caps:  0383fbff c1cbfbff 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps:        0383fbff c1cbfbff 00000000 00000020
CPU: AMD Athlon(TM) XP 1800+ stepping 02
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: IRQ9 SCI: Edge set to Level Trigger.
enabled ExtINT on CPU#0
ESR value before enabling vector: 00000000
ESR value after enabling vector: 00000000
Using local APIC timer interrupts.
calibrating APIC timer ...
..... CPU clock speed is 1544.0345 MHz.
..... host bus clock speed is 268.0581 MHz.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4136k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xf1180, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
spurious 8259A interrupt: IRQ7.
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Interrupt Link {LNKA} (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link {LNKB} (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link {LNKC} (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link {LNKD} (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
ACPI: PCI Root Bridge {PCI0} (00:00)
PCI: Probing PCI hardware (bus 00)
Disabling VIA memory write queue (PCI ID 0305, rev 03): {55} 89 & 1f -> 09
ACPI: PCI Interrupt Routing Table {\_SB_.PCI0._PRT}
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fc4f0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc520, dseg 0xf0000
pnp: 00:12: ioport range 0xe400-0xe47f could not be reserved
pnp: 00:12: ioport range 0xe800-0xe83f could not be reserved
PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
PCI: Using ACPI for IRQ routing
ACPI: PCI Interrupt Link {LNKD} enabled at IRQ 5
ACPI: PCI interrupt 0000:00:04.2{D} -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI interrupt 0000:00:04.3{D} -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI interrupt 0000:00:0d.0{A} -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI Interrupt Link {LNKB} enabled at IRQ 10
ACPI: PCI interrupt 0000:00:11.0{A} -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link {LNKA} enabled at IRQ 11
ACPI: PCI interrupt 0000:01:00.0{A} -> GSI 11 (level, low) -> IRQ 11
Simple Boot Flag at 0x3a set to 0x1
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Applying VIA southbridge workaround.
PCI: Disabling Via external APIC routing
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 8
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
ACPI: (supports S0 S1 S4 S5)

---

### Post by discord on 2005-03-28
ACPI wakeup devices:
PWRB PCI0 UAR1 UAR2 USB0 USB1
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4136 blocks {1 disk} into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
ACPI: Processor {CPU0} (supports C1 C2, 16 throttling states)

NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:04.1

---

### Post by discord on 2005-03-28
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:04.1
    ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:DMA

---

### Post by discord on 2005-03-28
hda: Maxtor 2F040L0, ATA DISK drive
hdb: Maxtor 6Y060L0, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
hdb: max request size: 128KiB
hdb: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host0/bus0/target1/lun0: p1
hdc: MAXTOR 6L080J4, ATA DISK drive
hdd: ST340015A, ATA DISK drive
ide1 at 0x170-0x177,0x376 on irq 15
hdc: max request size: 128KiB
hdc: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host0/bus1/target0/lun0: p1
hdd: max request size: 128KiB
hdd: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host0/bus1/target1/lun0: p1 p2
PDC20265: IDE controller at PCI slot 0000:00:11.0
ACPI: PCI interrupt 0000:00:11.0{A} -> GSI 10 (level, low) -> IRQ 10
PDC20265: chipset revision 2
PDC20265: 100% native mode on irq 10
PDC20265: (U)DMA Burst Bit ENABLED Primary PCI Mode Secondary PCI Mode.
    ide2: BM-DMA at 0x8800-0x8807, BIOS settings: hde:pio, hdf:pio
    ide3: BM-DMA at 0x8808-0x880f, BIOS settings: hdg:pio, hdh:pio
hde: Maxtor 6E040L0, ATA DISK drive
ide2 at 0xa000-0xa007,0x9802 on irq 10
hde: max request size: 128KiB
hde: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host2/bus0/target0/lun0: p1 p2 p3 p4
hdg: Maxtor 6E040L0, ATA DISK drive
ide3 at 0x9400-0x9407,0x9002 on irq 10
hdg: max request size: 128KiB
hdg: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host2/bus1/target0/lun0: p1 p2 < p5 >
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by discord on 2005-03-28
Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
psmouse.c: Failed to reset mouse on isa0060/serio1
input: PS/2 Generic Mouse on isa0060/serio1
psmouse.c: Failed to enable mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
parport0: PC-style at 0x378 (0x778) {PCSPP,TRISTATE}
parport_pc: Via 686A parallel port: io=0x378
lp0: using parport0 (polling).
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: {email}dm@uk.sistina.com{/email}
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdd1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdd2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
NTFS driver 2.1.15 {Flags: R/O MODULE}.
NTFS volume version 3.1.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdg1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
NTFS volume version 3.1.
NTFS volume version 3.1.
inserting floppy driver for 2.6.8.1-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
agpgart: Maximum main memory to use for agp memory: 690M
agpgart: AGP aperture is 32M @ 0xe6000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:04.2{D} -> GSI 5 (level, low) -> IRQ 5
uhci_hcd 0000:00:04.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:04.2: irq 5, io base 0000d400
uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:04.3{D} -> GSI 5 (level, low) -> IRQ 5
uhci_hcd 0000:00:04.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:04.3: irq 5, io base 0000d000
uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-2: new low speed USB device using address 2
usbcore: registered new driver hiddev
Linux Tulip driver version 1.1.13 (May 11, 2002)
ACPI: PCI interrupt 0000:00:0d.0{A} -> GSI 5 (level, low) -> IRQ 5
tulip0:  MII transceiver #1 config 1000 status 786d advertising 01e1.
eth0: ADMtek Comet rev 17 at 0xa400, 00:04:5A:41:36:B4, IRQ 5.
drivers/usb/input/hid-core.c: ctrl urb status -2 received
drivers/usb/input/hid-core.c: timeout initializing reports

input: USB HID v1.00 Mouse {Logitech Inc. iFeel Mouse   } on usb-0000:00:04.2-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
NET: Registered protocol family 17
eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) {PWRF}
eth0: no IPv6 routers present

EOF


Module                  Size  Used by
proc_intf               3968  0 
freq_table              4356  0 
cpufreq_userspace       5336  0 
cpufreq_powersave       2048  0 
button                  6936  0 
ac                      5132  0 
battery                 9740  0 
ipv6                  230148  10 
af_packet              20872  2 
joydev                  9536  0 
tulip                  42528  0 
crc32                   4608  1 tulip
usbhid                 28864  0 
uhci_hcd               29328  0 
usbcore               104292  4 usbhid,uhci_hcd
pci_hotplug            30640  0 
via_agp                 8832  1 
agpgart                31784  1 via_agp
pcspkr                  3816  0 
rtc                    12216  0 
floppy                 54996  0 
reiserfs              207600  0 
nls_cp437               6016  3 
ntfs                   88660  3 
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
parport_pc             32064  1 
lp                     10436  0 
parport                37320  2 parport_pc,lp
ide_cd                 38276  0 
tsdev                   7168  0 
cdrom                  35872  1 ide_cd
evdev                   9216  0 
mousedev               10124  1 
psmouse                17800  0 
ext3                  109672  5 
jbd                    54552  1 ext3
ide_generic             1664  0 
via82cxxx              13084  1 
pdc202xx_old           15516  1 
ide_disk               16768  15 
ide_core              125272  5 ide_cd,ide_generic,via82cxxx,pdc202xx_old,ide_disk
unix                   26160  614 
fan                     4236  0 
thermal                13200  0 
processor              17712  1 thermal
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


EOF

---

### Post by discord on 2005-03-28
had trouble posting sorry about that

---

