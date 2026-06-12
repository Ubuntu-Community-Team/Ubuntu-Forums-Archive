---
title: "Installation: No CDROM DETECTED &amp; No Partitions Found"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by superhac007 on 2005-05-04
I have a brand new Dell Percision 370.  Which has a SATA hardrive, and a CD/DVD Burner.  

Problem 1:
I can't get the system to find my cdrom after I get into the install.  It says CDROM not dectected even though I am able to boot hoary from the disk.

Problem 2:
If i boot from an external USB cdrom then it finds the hoary cd, but then when its time to partition it says no partitions found.  E.g. it can't detect my SATA drive.


Any clues on how to solve this.  

Thanks!

---

### Post by fackamato on 2005-05-04
What's the output of lsmod and dmesg?

---

### Post by superhac007 on 2005-05-04
[QUOTE=fackamato]What's the output of lsmod and dmesg?[/QUOTE]

Theres quite a bit listed.  Is there anything in particular were looking for.

Looks like in the lsmod that just about every ide-core mondule is loaded.  From what I can tell i don't see any errors in dmesg output.

I would include the output, but i have no way of getting it since the machine is not on the network.

---

### Post by fackamato on 2005-05-04
[QUOTE=superhac007]Theres quite a bit listed.  Is there anything in particular were looking for.

Looks like in the lsmod that just about every ide-core mondule is loaded.  From what I can tell i don't see any errors in dmesg output.

I would include the output, but i have no way of getting it since the machine is not on the network.[/QUOTE]

If the machine has internet access then you could upload it somewhere. Else put it on a floppy?

---

### Post by superhac007 on 2005-05-04
[QUOTE=fackamato]If the machine has internet access then you could upload it somewhere. Else put it on a floppy?[/QUOTE]

I always forget about sneaker net...  E.g. Thunb drive!

Heres DMESG:
```

starting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
VBTN PCI0 PCI1 PCI2 PCI3 PCI4  KBD USB0 USB1 USB2 USB3 
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: Compressed image found at block 0
VFS: Mounted root (ext2 filesystem).
VFS: Mounted root (ext2 filesystem).
Trying to move old root to /initrd ... okay
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 21, io base 0xff80
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 22
uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 22, io base 0xff60
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xff40
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 23, io base 0xff20
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 21, pci mem 0xffa80800
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SCSI subsystem initialized
libata version 1.10 loaded.
ata_piix version 1.03
ACPI: PCI interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xFEA0 irq 14
usb 5-8: new high speed USB device using ehci_hcd and address 2
ata1: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
ata1: dev 0 ATAPI, max UDMA/33
ata1: dev 0 configured for UDMA/33
scsi0 : ata_piix
elevator: using anticipatory as default io scheduler
ata1: command 0xa0 timeout, stat 0x58 host_stat 0x21
ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xFEA8 irq 15
ATA: abnormal status 0xFF on port 0x177
ata2: disabling port
scsi1 : ata_piix
usbcore: registered new driver usbkbd
drivers/usb/input/usbkbd.c: :USB HID Boot Protocol keyboard driver
usbcore: registered new driver hiddev
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
usbcore: registered new driver usbserial_generic
usbcore: registered new driver usbserial
drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
vga16fb: initializing
vga16fb: mapped to 0xc00a0000
fb0: VGA16 VGA frame buffer device
Console: switching to colour frame buffer device 80x30
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
  Vendor: DVDRW     Model: IDE1004           Rev: 0051
  Type:   CD-ROM                             ANSI SCSI revision: 00
usb-storage: device scan complete
sr0: scsi3-mmc drive: 1x/40x writer cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
Attached scsi CD-ROM sr0 at scsi2, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi2, channel 0, id 0, lun 0,  type 5
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
ICH6: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
ICH6: chipset revision 3
ICH6: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
ide0: I/O resource 0x1F0-0x1F7 not free.
ide0: ports already in use, skipping probe
ide0: I/O resource 0x1F0-0x1F7 not free.
ide0: ports already in use, skipping probe
ide1: I/O resource 0x170-0x177 not free.
ide1: ports already in use, skipping probe
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
cdrom: open failed.
cdrom: open failed.
usb 5-6: new high speed USB device using ehci_hcd and address 3
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
  Vendor: LEXAR     Model: JUMPDRIVE SECURE  Rev: 1000
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi generic sg1 at scsi3, channel 0, id 0, lun 0,  type 0
usb-storage: device scan complete
SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
sda: assuming drive cache: write through
SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
sda: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1
Attached scsi disk sda at scsi3, channel 0, id 0, lun 0
VFS: Can't find an ext2 filesystem on dev sda1.
cramfs: wrong magic
Unable to identify CD-ROM format.
VFS: Can't find an ext2 filesystem on dev sda1.
cramfs: wrong magic
Unable to identify CD-ROM format.
VFS: Can't find an ext2 filesystem on dev sda1.
cramfs: wrong magic
Unable to identify CD-ROM format.
VFS: Can't find an ext2 filesystem on dev sda1.
cramfs: wrong magic
Unable to identify CD-ROM format.
VFS: Can't find an ext2 filesystem on dev sda1.
cramfs: wrong magic
Unable to identify CD-ROM format.
usb 5-6: USB disconnect, address 3
usb 5-6: new high speed USB device using ehci_hcd and address 4
scsi4 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: LEXAR     Model: JUMPDRIVE SECURE  Rev: 1000
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
sda: assuming drive cache: write through
SCSI device sda: 1014784 512-byte hdwr sectors (520 MB)
sda: assuming drive cache: write through
 /dev/scsi/host4/bus0/target0/lun0: p1
Attached scsi disk sda at scsi4, channel 0, id 0, lun 0
Attached scsi generic sg1 at scsi4, channel 0, id 0, lun 0,  type 0
usb-storage: device scan complete
VFS: Can't find an ext2 filesystem on dev sda1.
cramfs: wrong magic
Unable to identify CD-ROM format.

```

Heres lsmod.  I had to manually load vfat for my thumb drive. Just an FYI.

```

Module                  Size  Used by
nls_iso8859_1           4224  1 
nls_cp437               5888  1 
vfat                   12928  1 
fat                    37792  1 vfat
sd_mod                 16784  2 
isofs                  33720  0 
ide_cd                 38532  0 
ide_disk               18176  0 
ide_generic             1664  0 
pdc202xx_new            8576  0 
aec62xx                 7296  0 
alim15x3               11404  0 
amd74xx                13340  0 
atiixp                  6160  0 
cmd64x                 11292  0 
cs5520                  4992  0 
cs5530                  5504  0 
cy82c693                4868  0 
generic                 4480  0 
hpt34x                  5376  0 
ns87415                 4680  0 
opti621                 4612  0 
pdc202xx_old           10624  0 
rz1000                  3072  0 
sc1200                  7296  0 
serverworks             8840  0 
siimage                11520  0 
sis5513                15112  0 
slc90e66                5888  0 
triflex                 4224  0 
trm290                  4612  0 
via82cxxx              12956  0 
floppy                 54864  0 
sg                     35360  0 
sr_mod                 16036  0 
cdrom                  36508  2 ide_cd,sr_mod
parport_pc             34372  0 
parport                33480  1 parport_pc
fbcon                  34048  68 
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vga16fb                12488  2 
vgastate                8576  1 vga16fb
vesafb                  6948  0 
cfbcopyarea             3968  2 vga16fb,vesafb
cfbimgblt               3072  2 vga16fb,vesafb
cfbfillrect             3584  2 vga16fb,vesafb
usb_storage            64064  1 
usbserial              28136  0 
usbhid                 29376  0 
usbkbd                  6784  0 
thermal                13576  0 
processor              22708  1 thermal
fan                     4612  0 
ata_piix                8836  0 
libata                 44548  1 ata_piix
scsi_mod              119936  5 sd_mod,sg,sr_mod,usb_storage,libata
piix                    9988  1 
ide_core              118988  28 ide_cd,ide_disk,ide_generic,pdc202xx_new,aec62xx,alim15x3,amd74xx,atiixp,cmd64x,cs5520,cs5530,cy82c693,generic,hpt34x,ns87415,opti621,pdc202xx_old,rz1000,sc1200,serverworks,siimage,sis5513,slc90e66,triflex,trm290,via82cxxx,usb_storage,piix
ehci_hcd               29444  0 
uhci_hcd               30224  0 
usbcore               107384  7 usb_storage,usbserial,usbhid,usbkbd,ehci_hcd,uhci_hcd
evdev                   9088  0 
unix                   26164  8 


```

**Please note that I also have an external USB cdrom drive installed.**


Thanks for any help you can give!

---

### Post by superhac007 on 2005-05-04
I just upgraded to the latest A4 BIOS and still have the same problem.  Is there a problem with SATA or is a problem with the combination of SATA and IDE?

---

### Post by superhac007 on 2005-05-13
I am still stuck trying to get this to install.  Can anyone help?

---

### Post by superhac007 on 2005-05-17
[QUOTE=alastair]Not finding the SATA drives at install time /might/ be a BIOS issue. Linux SATA has no support (yet I think) for Advanced Host Controller Interface (AHCI), which is in the Intel ICH6 controller.

Go into your BIOS and check the SATA settings. Switch to "legacy" if available (or "ATA" mode maybe).

I think the support module is "ata_piix". Check using "lsmod" on a working system.

Hope that helps.[/QUOTE]

I ended up finding this post and it fixed my problem.  Heres the link: [http://www.ubuntuforums.org/showthread.php?t=25217](http://www.ubuntuforums.org/showthread.php?t=25217)

I had to go into the BIOS and change it from AHCI mode to ATA mode.  That worked liked a charm!

Thanks alastair!

---

### Post by taryneast on 2006-03-09
[QUOTE=superhac007]I ended up finding this post and it fixed my problem.  Heres the link: [http://www.ubuntuforums.org/showthread.php?t=25217](http://www.ubuntuforums.org/showthread.php?t=25217)

I had to go into the BIOS and change it from AHCI mode to ATA mode.  That worked liked a charm!

Thanks alastair![/QUOTE]

We had a similar problem with a SATA drive on our new DELL 9150. We also had a similar fix for it - it only saw the drive after we changed it from SATA mode to ATA in the BIOS.

---

