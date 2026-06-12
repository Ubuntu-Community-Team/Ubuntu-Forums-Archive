---
title: "Problem Starting Raid Array on Boot"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by minorthreat on 2005-08-18
I'm having trouble getting my Raid 5 Array to start when my system boots up.  The array is a 7 disk sata array and works perfectly if I start it by hand after booting the system.  It looks to me that the problem might be that the sata drives aren't being recognized by the system until after the command to start the raid array is run.  This causes an error when the system tries to mount the array on boot.

Here is the dmesg output:
```

().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
pnp: 00:00: ioport range 0x4400-0x447f has been reserved
pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
pnp: 00:00: ioport range 0x4200-0x427f has been reserved
pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
pnp: 00:01: ioport range 0x5000-0x503f has been reserved
pnp: 00:01: ioport range 0x5100-0x513f has been reserved
audit: initializing netlink socket (disabled)
audit(1124324855.006:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
inotify device minor=63
ACPI: PS/2 Keyboard Controller [PS2K] at I/O 0x60, 0x64, irq 1
ACPI: PS/2 Mouse Controller [PS2M] at irq 12
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
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
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP established hash table entries: 8192 (order: 4, 65536 bytes)
TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
TCP: Hash tables configured (established 8192 bind 8192)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1 
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4308KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
NFORCE2-U400R: IDE controller at PCI slot 0000:00:09.0
NFORCE2-U400R: chipset revision 163
NFORCE2-U400R: not 100% native mode: will probe irqs later
NFORCE2-U400R: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE2-U400R: 0000:00:09.0 (rev a3) UDMA133 controller
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 6Y120L4, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(133)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (459 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 650592k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
devfs_mk_dev: could not append to parent for md/0
EXT3-fs: unable to read superblock
Real Time Clock Driver v1.12
input: PC Speaker
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 176M
agpgart: AGP aperture is 64M @ 0xd8000000
i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 21 (level, high) -> IRQ 21
ohci_hcd 0000:00:02.0: PCI device 10de:0087 (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 21, pci mem 0xe0001000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 4 ports detected
ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 20 (level, high) -> IRQ 20
ohci_hcd 0000:00:02.1: PCI device 10de:0087 (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 20, pci mem 0xe0002000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 4 ports detected
ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 21 (level, high) -> IRQ 21
ehci_hcd 0000:00:02.2: PCI device 10de:0088 (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 21, pci mem 0xe0003000
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: park 0
ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 8 ports detected
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.31.
ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 20 (level, high) -> IRQ 20
PCI: Setting latency timer of device 0000:00:04.0 to 64
eth0: forcedeth.c: subsystem: 01462:7119 bound to 0000:00:04.0
ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 21 (level, high) -> IRQ 21
PCI: Setting latency timer of device 0000:00:06.0 to 64
eth0: no link during initialization.
intel8x0_measure_ac97_clock: measured 49819 usecs
intel8x0: clocking to 48000
eth0: link up.
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
SCSI subsystem initialized
libata version 1.10 loaded.
sata_nv version 0.6
ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 22 (level, high) -> IRQ 22
PCI: Setting latency timer of device 0000:00:0b.0 to 64
ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xAC00 irq 22
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xAC08 irq 22
NET: Registered protocol family 17
ata1: no device found (phy stat 00000000)
scsi0 : sata_nv
ata2: no device found (phy stat 00000000)
scsi1 : sata_nv
sata_promise version 1.01
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 18
ata3: SATA max UDMA/133 cmd 0xCEA2C200 ctl 0xCEA2C238 bmdma 0x0 irq 18
ata4: SATA max UDMA/133 cmd 0xCEA2C280 ctl 0xCEA2C2B8 bmdma 0x0 irq 18
ata5: SATA max UDMA/133 cmd 0xCEA2C300 ctl 0xCEA2C338 bmdma 0x0 irq 18
ata6: SATA max UDMA/133 cmd 0xCEA2C380 ctl 0xCEA2C3B8 bmdma 0x0 irq 18
ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata3: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata3: dev 0 configured for UDMA/133
scsi2 : sata_promise
ata4: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata4: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata4: dev 0 configured for UDMA/133
scsi3 : sata_promise
ata5: no device found (phy stat 00000000)
scsi4 : sata_promise
ata6: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata6: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata6: dev 0 configured for UDMA/133
scsi5 : sata_promise
  Vendor: ATA       Model: ST3400832AS       Rev: 3.02
  Type:   Direct-Access                      ANSI SCSI revision: 05
  Vendor: ATA       Model: ST3400832AS       Rev: 3.02
  Type:   Direct-Access                      ANSI SCSI revision: 05
  Vendor: ATA       Model: ST3400832AS       Rev: 3.02
  Type:   Direct-Access                      ANSI SCSI revision: 05
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
ACPI: PCI interrupt 0000:02:07.0[A] -> GSI 19 (level, low) -> IRQ 19
ata7: SATA max UDMA/133 cmd 0xCEA46200 ctl 0xCEA46238 bmdma 0x0 irq 19
ata8: SATA max UDMA/133 cmd 0xCEA46280 ctl 0xCEA462B8 bmdma 0x0 irq 19
ata9: SATA max UDMA/133 cmd 0xCEA46300 ctl 0xCEA46338 bmdma 0x0 irq 19
ata10: SATA max UDMA/133 cmd 0xCEA46380 ctl 0xCEA463B8 bmdma 0x0 irq 19
SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host2/bus0/target0/lun0: p1
Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdb: drive cache: write back
SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdb: drive cache: write back
 /dev/scsi/host3/bus0/target0/lun0: p1
Attached scsi disk sdb at scsi3, channel 0, id 0, lun 0
SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdc: drive cache: write back
SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdc: drive cache: write back
 /dev/scsi/host5/bus0/target0/lun0: p1
Attached scsi disk sdc at scsi5, channel 0, id 0, lun 0
ata7: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata7: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata7: dev 0 configured for UDMA/133
scsi6 : sata_promise
ata8: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata8: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata8: dev 0 configured for UDMA/133
scsi7 : sata_promise
ata9: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata9: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata9: dev 0 configured for UDMA/133
scsi8 : sata_promise
ata10: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata10: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata10: dev 0 configured for UDMA/133
scsi9 : sata_promise
  Vendor: ATA       Model: ST3400832AS       Rev: 3.03
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdd: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdd: drive cache: write back
SCSI device sdd: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdd: drive cache: write back
 /dev/scsi/host6/bus0/target0/lun0: p1
Attached scsi disk sdd at scsi6, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3400832AS       Rev: 3.03
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sde: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sde: drive cache: write back
SCSI device sde: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sde: drive cache: write back
 /dev/scsi/host7/bus0/target0/lun0: p1
Attached scsi disk sde at scsi7, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3400832AS       Rev: 3.03
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdf: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdf: drive cache: write back
SCSI device sdf: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdf: drive cache: write back
 /dev/scsi/host8/bus0/target0/lun0: p1
Attached scsi disk sdf at scsi8, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3400832AS       Rev: 3.03
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdg: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdg: drive cache: write back
SCSI device sdg: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdg: drive cache: write back
 /dev/scsi/host9/bus0/target0/lun0: p1
Attached scsi disk sdg at scsi9, channel 0, id 0, lun 0
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f4200(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present

```

Am I correct in what I think is wrong?  If so (and if not) how do I go about fixing this?

---

### Post by nad on 2005-08-19
The drives are recognized. Is /etc/default/mdadm set to autostart?

---

### Post by minorthreat on 2005-08-19
Yes, it is set to autostart:
```

START_DAEMON=true
MAIL_TO="root"
AUTOSTART=true

```

---

### Post by nad on 2005-08-19
It appears that your initrd does not have raid support. I suppose that you have added the raid since system installation. See; 
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/Software-RAID-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/Software-RAID-HOWTO) 

and man mkinitrd .

Use the mkinitrd command to make a new initrd image (with the raid running), place it in your /boot directory and reference it from your grub/menu.lst

---

### Post by minorthreat on 2005-08-19
I just ran the following command after starting and mounting the raid array:
```

sudo mkinitrd -r /dev/hda1 -0 /boot/initrd.img-2.6.11-1-386-raid

```

I then changed the initrd referenced in /boot/grub/menu.lst.

Unfortunately, it still doesn't work.  I'm getting the same error (which I probably should've posted before...):
```

fsck.ext3: Invalid argument while trying to open /dev/md0
/dev/md0:
The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

```

I can still start and mount the raid when I finish booting.  It appears nothing has changed.

So unless I ran the command improperly, which is definitely possible, it seems that that didn't work.

dmesg:
```

5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APCF] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APCG] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APCH] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APCI] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APCK] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APCM] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21) *0, disabled.
ACPI: PCI Interrupt Link [APSI] (IRQs 22) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 14 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
pnp: 00:00: ioport range 0x4400-0x447f has been reserved
pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
pnp: 00:00: ioport range 0x4200-0x427f has been reserved
pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
pnp: 00:01: ioport range 0x5000-0x503f has been reserved
pnp: 00:01: ioport range 0x5100-0x513f has been reserved
audit: initializing netlink socket (disabled)
audit(1124488277.984:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
inotify device minor=63
ACPI: PS/2 Keyboard Controller [PS2K] at I/O 0x60, 0x64, irq 1
ACPI: PS/2 Mouse Controller [PS2M] at irq 12
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
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
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP established hash table entries: 8192 (order: 4, 65536 bytes)
TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
TCP: Hash tables configured (established 8192 bind 8192)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1 
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4308KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
NFORCE2-U400R: IDE controller at PCI slot 0000:00:09.0
NFORCE2-U400R: chipset revision 163
NFORCE2-U400R: not 100% native mode: will probe irqs later
NFORCE2-U400R: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE2-U400R: 0000:00:09.0 (rev a3) UDMA133 controller
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: Maxtor 6Y120L4, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(133)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (459 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 650592k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
devfs_mk_dev: could not append to parent for md/0
EXT3-fs: unable to read superblock
Real Time Clock Driver v1.12
input: PC Speaker
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 176M
agpgart: AGP aperture is 64M @ 0xd8000000
i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 21 (level, high) -> IRQ 21
ohci_hcd 0000:00:02.0: PCI device 10de:0087 (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: irq 21, pci mem 0xe0001000
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 4 ports detected
ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 20 (level, high) -> IRQ 20
ohci_hcd 0000:00:02.1: PCI device 10de:0087 (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.1 to 64
ohci_hcd 0000:00:02.1: irq 20, pci mem 0xe0002000
ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 4 ports detected
ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 21 (level, high) -> IRQ 21
ehci_hcd 0000:00:02.2: PCI device 10de:0088 (nVidia Corporation)
PCI: Setting latency timer of device 0000:00:02.2 to 64
ehci_hcd 0000:00:02.2: irq 21, pci mem 0xe0003000
ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 64 is not supported by device 0000:00:02.2
ehci_hcd 0000:00:02.2: park 0
ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 8 ports detected
forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.31.
ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 20 (level, high) -> IRQ 20
PCI: Setting latency timer of device 0000:00:04.0 to 64
eth0: forcedeth.c: subsystem: 01462:7119 bound to 0000:00:04.0
eth0: no link during initialization.
ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 21 (level, high) -> IRQ 21
PCI: Setting latency timer of device 0000:00:06.0 to 64
intel8x0_measure_ac97_clock: measured 49830 usecs
intel8x0: clocking to 47363
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
eth0: link up.
NET: Registered protocol family 17
SCSI subsystem initialized
libata version 1.10 loaded.
sata_nv version 0.6
ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 22 (level, high) -> IRQ 22
PCI: Setting latency timer of device 0000:00:0b.0 to 64
ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xAC00 irq 22
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xAC08 irq 22
ata1: no device found (phy stat 00000000)
scsi0 : sata_nv
ata2: no device found (phy stat 00000000)
scsi1 : sata_nv
sata_promise version 1.01
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 18
ata3: SATA max UDMA/133 cmd 0xCEA2C200 ctl 0xCEA2C238 bmdma 0x0 irq 18
ata4: SATA max UDMA/133 cmd 0xCEA2C280 ctl 0xCEA2C2B8 bmdma 0x0 irq 18
ata5: SATA max UDMA/133 cmd 0xCEA2C300 ctl 0xCEA2C338 bmdma 0x0 irq 18
ata6: SATA max UDMA/133 cmd 0xCEA2C380 ctl 0xCEA2C3B8 bmdma 0x0 irq 18
ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata3: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata3: dev 0 configured for UDMA/133
scsi2 : sata_promise
ata4: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata4: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata4: dev 0 configured for UDMA/133
scsi3 : sata_promise
ata5: no device found (phy stat 00000000)
scsi4 : sata_promise
ata6: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata6: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata6: dev 0 configured for UDMA/133
scsi5 : sata_promise
  Vendor: ATA       Model: ST3400832AS       Rev: 3.02
  Type:   Direct-Access                      ANSI SCSI revision: 05
  Vendor: ATA       Model: ST3400832AS       Rev: 3.02
  Type:   Direct-Access                      ANSI SCSI revision: 05
  Vendor: ATA       Model: ST3400832AS       Rev: 3.02
  Type:   Direct-Access                      ANSI SCSI revision: 05
ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
ACPI: PCI interrupt 0000:02:07.0[A] -> GSI 19 (level, low) -> IRQ 19
ata7: SATA max UDMA/133 cmd 0xCEA4E200 ctl 0xCEA4E238 bmdma 0x0 irq 19
ata8: SATA max UDMA/133 cmd 0xCEA4E280 ctl 0xCEA4E2B8 bmdma 0x0 irq 19
ata9: SATA max UDMA/133 cmd 0xCEA4E300 ctl 0xCEA4E338 bmdma 0x0 irq 19
ata10: SATA max UDMA/133 cmd 0xCEA4E380 ctl 0xCEA4E3B8 bmdma 0x0 irq 19
SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host2/bus0/target0/lun0: p1
Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdb: drive cache: write back
SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdb: drive cache: write back
 /dev/scsi/host3/bus0/target0/lun0: p1
Attached scsi disk sdb at scsi3, channel 0, id 0, lun 0
SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdc: drive cache: write back
SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdc: drive cache: write back
 /dev/scsi/host5/bus0/target0/lun0: p1
Attached scsi disk sdc at scsi5, channel 0, id 0, lun 0
ata7: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata7: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata7: dev 0 configured for UDMA/133
scsi6 : sata_promise
ata8: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata8: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata8: dev 0 configured for UDMA/133
scsi7 : sata_promise
ata9: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata9: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata9: dev 0 configured for UDMA/133
scsi8 : sata_promise
ata10: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:407f
ata10: dev 0 ATA, max UDMA/133, 781422768 sectors: lba48
ata10: dev 0 configured for UDMA/133
scsi9 : sata_promise
  Vendor: ATA       Model: ST3400832AS       Rev: 3.03
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdd: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdd: drive cache: write back
SCSI device sdd: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdd: drive cache: write back
 /dev/scsi/host6/bus0/target0/lun0: p1
Attached scsi disk sdd at scsi6, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3400832AS       Rev: 3.03
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sde: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sde: drive cache: write back
SCSI device sde: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sde: drive cache: write back
 /dev/scsi/host7/bus0/target0/lun0: p1
Attached scsi disk sde at scsi7, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3400832AS       Rev: 3.03
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdf: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdf: drive cache: write back
SCSI device sdf: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdf: drive cache: write back
 /dev/scsi/host8/bus0/target0/lun0: p1
Attached scsi disk sdf at scsi8, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3400832AS       Rev: 3.03
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdg: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdg: drive cache: write back
SCSI device sdg: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sdg: drive cache: write back
 /dev/scsi/host9/bus0/target0/lun0: p1
Attached scsi disk sdg at scsi9, channel 0, id 0, lun 0
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f4200(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present

```

---

### Post by nad on 2005-08-19
"then the superblock is corrupt"

This is why the raid does not autostart. Try running fsck with an alternate superblock.

I had a similar problem recently. My raid would not autostart even after being marked clean by fsck. I could however manually start it. Using an alternate superblock, I was never able to repair the filesystem. Continual bad block scans (thankfully on a 50MB /boot partition) showed an increasing number of bad blocks approaching 10%.

The manufacturers drive utility check (also run several times) declared the drive error free! I now knew better some several hours later and proceded to replace the disk.

---

### Post by minorthreat on 2005-08-19
I don't think the superblock is bad though.  If I start the array manuallly and then run:
```
sudo e2fsck /dev/md0
``` I get the following output: ```
/dev/md0: clean, 934/293044224 files, 9982565/586063104 blocks

```

Edit:

I'm running e2fsck -c /dev/md0 right now, but since it's a large array, it's taking awhile.  I'll post the results here when done.

---

### Post by minorthreat on 2005-08-22
This is what I got back from running e2fsck -c /dev/md0

```

e2fsck 1.35 (28-Feb-2004)
Checking for bad blocks (read-only test): done                        
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/md0: ***** FILE SYSTEM WAS MODIFIED *****
/dev/md0: 934/293044224 files (45.8% non-contiguous), 9982565/586063104 blocks

```

Would it have output there if there were bad blocks?  If not, how do I see how many bad blocks there are?

---

### Post by nad on 2005-08-22
Your file system is severely fragmented. Whether this is the problem or not, I do not know.

I repeat, "Try running fsck with an alternate superblock".

---

### Post by minorthreat on 2005-08-22
As far as i've always heard, fragmentation doesn't matter in linux.  But I'll try running e2fsck with an alternate superblock.

---

### Post by nad on 2005-08-23
Fragmentation always matters, regardless of operating system. It is just that most file systems available to linux are resistant to this degree of fragmentation, unless of course your file system is nearly full.

As always, the easiest way to defragment a file system is to copy it to a fresh partition. In your instance it would seem a prudent thing to do.

---

### Post by minorthreat on 2005-08-23
This is what I get when I run e2fsck -b 8193 /dev/md0:
```

e2fsck 1.35 (28-Feb-2004)
e2fsck: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

But if I run it without specifying a superblock (e2fsck /dev/md0) I get the following:
```

e2fsck 1.35 (28-Feb-2004)
/dev/md0: clean, 934/293044224 files, 9982565/586063104 blocks

```

---

### Post by minorthreat on 2005-08-23
I also took your advise and copied everything off the /dev/md0 and put it back on, and now it's down to 7.9% non-contiguous.  However, that didn't solve the issue at hand.

---

### Post by nad on 2005-08-23
Bingo.

Now, you are the system administrator. You:

A) Scratch your head and phone that new blond in reception.

B) Get another cup of coffee and continue your Quake session.

C) Stare at the calendar to find your next vacation day.

D) Put together and implement a data backup procedure.

Edit:

"I also took your advise and copied everything off the /dev/md0 and put it back on, and now it's down to 7.9% non-contiguous. However, that didn't solve the issue at hand."

I strongly suspect a failing hard drive.

---

### Post by minorthreat on 2005-08-23
Clearly, the answer would be D.

Hm... a failing harddrive would be a nuisance on brand new drives, but I can deal with that.  Why would that cause the raid array not to start and mount on boot though?  Shouldn't a raid5 array be able to handle (gracefully) a failed/failing harddrive?

---

### Post by nad on 2005-08-23
Good question. You would think so. I surmise that the raid superblock itself is not correct or being correctly updated.

Try: mdadm -Q --examine /dev/hard_drive_designation_here (not md device number).

Also, read your logs. You may be pointed in the correct direction. My humble opinion is only that.

---

### Post by minorthreat on 2005-08-23
Hm... thank you very much for all of your help.  Could you point me in the direction of the logs I should check out?

This is the output of running mdadm -Q --examine /dev/sdg1 (It was the same for all of the drives /dev/sd[a-g]1):
```

/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.01
           UUID : 0b2f3ebf:6dc4ef80:539cf252:e2348106
  Creation Time : Sat Aug 13 00:50:55 2005
     Raid Level : raid5
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 0

    Update Time : Tue Aug 23 12:29:59 2005
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f546296c - correct
         Events : 0.22114

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     6       8       97        6      active sync   /dev/sdg1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       8       81        5      active sync   /dev/sdf1
   6     6       8       97        6      active sync   /dev/sdg1

```

---

### Post by nad on 2005-08-23
Most system log files may be found in /var/log . You may also wish to read any mail in /var/mail as some errors are set to automatically mail the administrator (usually the first added user to a system) or the root account (which is just mail).

I don't see any problems in your query, but, as I stated in my first reply, I couldn't find any other reason for the failure. I've dealt with hundreds of hard drives over the years. I am seeing increasingly high failure rates among new drives. Apparently, the manufacturers would rather RMA a drive rather than increase the quality in the first place. This is especially true of consumer grade drives. One of the first lessons I learned as a teenage mechanic was that the correct question is what to do _when_ it fails, not _if_.

---

### Post by minorthreat on 2005-08-23
Again, I can't thank you enough for taking the time to try and solve this problem.  I'll take a look through the logs and see what I can find, if anything.

I'd have to agree with you about hard drives.  The only ones I've had fail are the most recent ones I've bought.  I have an about 8 year old drive from an old dell still running strong.  It's a good reason to keep backup and and extra disk on hand for the raid though.

---

### Post by rotten777 on 2005-08-25
try this:

```
apt-get install raidtools2
```




make sure your raidtab shows like this... (obviously modifying the partitions as needed)


```
raiddev /dev/md0
          raid-level      1
          nr-raid-disks   2
          nr-spare-disks  0
          persistent-superblock 1
          device          /dev/sdb6
          raid-disk       0
          device          /dev/sdc5
          raid-disk       1

```

```
mkraid /dev/md0
cat /proc/mdstat
```


if you have errors with any of it, post it up.

---

### Post by nad on 2005-08-25
minorthreat,

Upon reading the previous post and scanning this thread, I considered that your /etc/mdadm/mdadm.conf hasn't been set up yet.

---

### Post by rotten777 on 2005-08-26
ahh thats another piece


make sure you have something like:


```

DEVICE              /dev/hde5
DEVICE              /dev/hd55
ARRAY              /dev/md0 devices=/dev/hde5,/devhdg5

```

---

### Post by rotten777 on 2005-08-26
well we're both having the same problem but i've found a different fix.

3ware Escalade 8006-2LP.... i give up. true hardware RAID is much much easier. I'm not sure if it's just something not in initrd or what but i'm tired of tinkering.

---

### Post by minorthreat on 2005-08-26
Thanks for the tips.  I won't be by my computer for a few days, and i don't have time to test them now, but I will try them when I can.

I am pretty sure i set up my mdadm.conf already though.  However, I may have tweaked it improperly trying to get this to work, so I'll definitely take a look there again.

---

### Post by tabweb on 2006-08-01
Isn't mdadm.conf an option? I have a 12 disk jbod running mdadm with raid 1 on 10 drives and the other two has spares. I am using mdadm.conf only to describe the spares because I couldn't find any other place to add them. However, I'm sure that mdadm.conf is not required for most. It's one of the differences between mdadm and raidtools, where you had to have the /etc/raidtab file.

---

