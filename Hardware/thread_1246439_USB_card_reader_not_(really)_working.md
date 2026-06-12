---
title: "USB card reader not (really) working"
date: 2009-08-21
forum: Hardware
---

### Post by theturner on 2009-08-21
Hi there.

I've got a USB card reader, a [Trust 15092]("http://www.trust.com/products/product.aspx?artnr=15092") to be precise. The card reader itself is recognized when I plug it in, but any cards inside it aren't.
```

Aug 21 20:07:50 neutor kernel: [21546.596057] usb 1-2: new high speed USB device using ehci_hcd and address 3
Aug 21 20:07:50 neutor kernel: [21546.738839] usb 1-2: configuration #1 chosen from 1 choice
Aug 21 20:07:50 neutor kernel: [21546.739391] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 21 20:07:50 neutor kernel: [21546.752729] usb-storage: device found at 3
Aug 21 20:07:50 neutor kernel: [21546.752734] usb-storage: waiting for device to settle before scanning
Aug 21 20:07:55 neutor kernel: [21551.752332] usb-storage: device scan complete
Aug 21 20:07:55 neutor kernel: [21551.752932] scsi 4:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
Aug 21 20:07:55 neutor kernel: [21551.753396] scsi 4:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
Aug 21 20:07:55 neutor kernel: [21551.753895] scsi 4:0:0:2: Direct-Access     Generic- SM/xD Picture    1.02 PQ: 0 ANSI: 0
Aug 21 20:07:55 neutor kernel: [21551.755463] scsi 4:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0
Aug 21 20:07:56 neutor kernel: [21552.017637] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug 21 20:07:56 neutor kernel: [21552.017763] sd 4:0:0:0: Attached scsi generic sg3 type 0
Aug 21 20:07:56 neutor kernel: [21552.019018] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Aug 21 20:07:56 neutor kernel: [21552.019131] sd 4:0:0:1: Attached scsi generic sg4 type 0
Aug 21 20:07:56 neutor kernel: [21552.023482] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Aug 21 20:07:56 neutor kernel: [21552.023604] sd 4:0:0:2: Attached scsi generic sg5 type 0
Aug 21 20:07:56 neutor kernel: [21552.026229] sd 4:0:0:3: [sde] Attached SCSI removable disk
Aug 21 20:07:56 neutor kernel: [21552.026343] sd 4:0:0:3: Attached scsi generic sg6 type 0
```
This appears in syslog when I plug it in. Nautilus's "Computer" location also shows four removable USB drive icons.
Now, let's put a 6GB Hitachi Microdrive (basically, a hard disk in CF size) in the card reader:
```
Aug 21 20:10:57 neutor kernel: [21733.662218] sd 4:0:0:1: [sdc] 12000556 512-byte hardware sectors: (6.14 GB/5.72 GiB)
Aug 21 20:10:57 neutor kernel: [21733.662950] sd 4:0:0:1: [sdc] Write Protect is off
Aug 21 20:10:57 neutor kernel: [21733.662954] sd 4:0:0:1: [sdc] Mode Sense: 03 00 00 00
Aug 21 20:10:57 neutor kernel: [21733.662958] sd 4:0:0:1: [sdc] Assuming drive cache: write through
Aug 21 20:10:57 neutor kernel: [21733.663575] sd 4:0:0:1: [sdc] 12000556 512-byte hardware sectors: (6.14 GB/5.72 GiB)
Aug 21 20:10:57 neutor kernel: [21733.668749] sd 4:0:0:1: [sdc] Write Protect is off
Aug 21 20:10:57 neutor kernel: [21733.668758] sd 4:0:0:1: [sdc] Mode Sense: 03 00 00 00
Aug 21 20:10:57 neutor kernel: [21733.668762] sd 4:0:0:1: [sdc] Assuming drive cache: write through
Aug 21 20:10:58 neutor kernel: [21733.668777]  sdc: sdc1
Aug 21 20:11:00 neutor hald: mounted /dev/sdc1 on behalf of uid 1000
```
Works fine. Mounts automatically.

However, any flash memory card I have won't produce any results. I've tried a 512 MB SD card (not SDHC) and a 64 MB Memory Stick, and absolutely nothing happens. Not even a single line in syslog. Putting the card in the reader first and then plugging the reader in won't help either.

What's up? Am I missing some modules for handling flash based storage,or what? 
```
lsmod | grep sd
sd_mod                 33428  3 
crc_t10dif              1920  1 sd_mod
scsi_mod              152276  7 usb_storage,sg,sr_mod,sd_mod,aic7xxx,scsi_transport_spi,libata
```

Oh, and I'm using Ubuntu 9.04.
Thanks in advance for any help!

---

