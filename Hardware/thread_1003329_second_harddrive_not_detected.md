---
title: "second harddrive not detected"
date: 2008-12-06
forum: Hardware
---

### Post by delly47 on 2008-12-06
so i am new to ubuntu. its great, expect it wont detect my secondary harddrive. i have a sata harddrive as my primary master and it is partitioned with windows vista on one half and ubuntu on the other. i have another harddrive a maxtor 6L250R0 as the secondary master. ubuntu just wont pick this drive up. i have tried installing every disk manager and partition manager available on the package downloader. nothing picks it up. 
it is an ide harddrive hookup up to a sata motherboard port, via an adapter. is this causing the problem? i tryed hooking the sata cable into the other sata ports on the motherboard, none would pick it up.

i have read the dmesg command heres what i think is the error part


[    3.328323] ata_piix 0000:00:1f.1: version 2.12
[    3.328338] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.328384] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.328488] scsi0 : ata_piix
[    3.328612] scsi1 : ata_piix
[    3.330666] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.330670] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.492348] ata1.00: ATAPI: LITE-ON DVDRW SOHW-1633S, BPSA, max UDMA/66
[    3.492363] ata1.00: limited to UDMA/33 due to 40-wire cable
[    3.508284] ata1.00: configured for UDMA/33
[    3.508331] ata2: port disabled. ignoring.
[    3.509160] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1633S BPSA PQ: 0 ANSI: 5
[    3.509305] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.509311] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.509355] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.509435] scsi2 : ata_piix
[    3.509537] scsi3 : ata_piix
[    3.509594] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xa880 irq 19
[    3.509597] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa888 irq 19
[    3.520021] usb 3-1: device not accepting address 2, error -71
[    3.576046] hub 3-0:1.0: unable to enumerate USB device on port 1
[    3.672214] ata3.00: ATA-7: Maxtor 6Y160M0, YAR511W0, max UDMA/100
[    3.672219] ata3.00: 320173056 sectors, multi 16: LBA48 
[    3.688220] ata3.00: configured for UDMA/100
[    4.112021] usb 3-1: new low speed USB device using uhci_hcd and address 4
[    4.288127] usb 3-1: configuration #1 chosen from 1 choice
[    4.528019] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    4.701780] usb 4-1: configuration #1 chosen from 1 choice
[    4.704936] usbcore: registered new interface driver hiddev
[    4.727694] input: Logitech WingMan RumblePad as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input2
[    4.727807] input,hidraw0: USB HID v1.10 Joystick [Logitech WingMan RumblePad] on usb-0000:00:1d.2-1
[    4.727853] usbcore: registered new interface driver usbhid
[    4.727858] usbhid: v2.6:USB HID core driver
[    4.729798] usbcore: registered new interface driver libusual
[    4.744945] Initializing USB Mass Storage driver...
[    4.746064] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.747278] usbcore: registered new interface driver usb-storage
[    4.747288] USB Mass Storage support registered.
[    4.747456] usb-storage: device found at 2
[    4.747460] usb-storage: waiting for device to settle before scanning
[    4.757163] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    8.852035] ata4.00: qc timeout (cmd 0x27)
[    8.852043] ata4.00: failed to read native max address (err_mask=0x4)
[    9.745778] usb-storage: device scan complete
[    9.748760] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    9.751759] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    9.754758] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    9.757760] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    9.759657] scsi 4:0:0:0: Attached scsi generic sg1 type 0
[    9.760654] scsi 4:0:0:1: Attached scsi generic sg2 type 0
[    9.761622] scsi 4:0:0:2: Attached scsi generic sg3 type 0
[    9.762632] scsi 4:0:0:3: Attached scsi generic sg4 type 0
[    9.779983] Driver 'sd' needs updating - please use bus_type methods
[   19.016035] ata4.00: qc timeout (cmd 0x27)
[   19.016043] ata4.00: failed to read native max address (err_mask=0x4)
[   19.016047] ata4.00: revalidation failed (errno=-5)
[   29.180035] ata4.00: qc timeout (cmd 0x27)
[   29.180043] ata4.00: failed to read native max address (err_mask=0x4)
[   29.180047] ata4.00: revalidation failed (errno=-5)
[   29.180051] ata4.00: disabled
[   29.180070] ata4: soft resetting link
[   29.336058] ata4: EH complete
[   29.336212] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y160M0   YAR5 PQ: 0 ANSI: 5
[   29.336430] scsi 2:0:0:0: Attached scsi generic sg5 type 0
[   29.336793] 8139too 0000:03:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21


im guessing ata4 is my problem drives
this is driving me crazy. all my music is on this drive. any solutions?
my bios and windows vista both pick up this drive no problem. is it formatted wrong perhaps? DMA settings?
please help me. i hope i included enough info

thanks
mike

---

### Post by cdtech on 2008-12-06
Try typing the command:
```
sudo fdisk -l
```
see if Ubuntu list the drive.

---

### Post by delly47 on 2008-12-06
well heres what i get with fdisk -l

Disk /dev/sde: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x338c338b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       15921   127878140    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sde2           15922       19929    32194260    5  Extended
/dev/sde5           15922       19408    28009296   83  Linux
/dev/sde6           19409       19929     4184901   82  Linux swap / Solaris

Disk /dev/sdf: 8053 MB, 8053325312 bytes
255 heads, 63 sectors/track, 979 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         976     7839698    b  W95 FAT32


as you can see only my primary harddrive is detected. also my usb key that is connected as well.

why the heck isnt my second drive showing up

---

### Post by cdtech on 2008-12-06
Does it show up in your BIOS?

---

### Post by delly47 on 2008-12-06
yes it sure does, windows picks it up fine as well. do you need any more log files or anything?

---

