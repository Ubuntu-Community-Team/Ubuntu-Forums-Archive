---
title: "Mount of Lexar USB drive results"
date: 2015-03-25
forum: Hardware
---

### Post by mcollard@gmail.com on 2015-03-25
I get the following error. It uses FAT-16, but I cannot determine why it's selecting EXT4. 

Suggestions? 

[427888.406830] usb 2-1.2: new high-speed USB device number 39 using ehci-pci
[427888.503165] usb 2-1.2: New USB device found, idVendor=05dc, idProduct=a660
[427888.503172] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[427888.503176] usb 2-1.2: Product: JD Mercury
[427888.503180] usb 2-1.2: Manufacturer: Lexar Media
[427888.503184] usb 2-1.2: SerialNumber: 67CBB612022733090207
[427888.503969] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[427888.504469] scsi11 : usb-storage 2-1.2:1.0
[427889.504483] scsi 11:0:0:0: Direct-Access     Lexar    JD Mercury       1100 PQ: 0 ANSI: 0 CCS
[427889.505001] sd 11:0:0:0: Attached scsi generic sg4 type 0
[427889.508463] sd 11:0:0:0: [sdd] 1965056 512-byte logical blocks: (1.00 GB/959 MiB)
[427889.509548] sd 11:0:0:0: [sdd] Write Protect is off
[427889.509555] sd 11:0:0:0: [sdd] Mode Sense: 43 00 00 00
[427889.510901] sd 11:0:0:0: [sdd] No Caching mode page found
[427889.510904] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[427889.516682] sd 11:0:0:0: [sdd] No Caching mode page found
[427889.516688] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[427889.518045]  sdd: sdd1
[427889.523697] sd 11:0:0:0: [sdd] No Caching mode page found
[427889.523704] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[427889.523709] sd 11:0:0:0: [sdd] Attached SCSI removable disk
[427889.812830] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem

---

