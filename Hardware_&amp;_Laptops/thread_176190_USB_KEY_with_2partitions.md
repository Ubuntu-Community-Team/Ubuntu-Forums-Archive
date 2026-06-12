---
title: "USB KEY with 2partitions"
date: 2006-05-14
forum: Hardware &amp; Laptops
---

### Post by ashrack on 2006-05-14
Just received an USB KEY "Patriot Memory 256MB". But this key is different than the other USBs I've seen since it creates 2drives on connection. Her's 'dmesg'
```
[4296583.830000] usb 4-3: new high speed USB device using ehci_hcd and address 3[4296584.481000] Initializing USB Mass Storage driver...
[4296584.482000] scsi0 : SCSI emulation for USB Mass Storage devices
[4296584.482000] usb-storage: device found at 3
[4296584.482000] usb-storage: waiting for device to settle before scanning
[4296584.482000] usbcore: registered new driver usb-storage
[4296584.482000] USB Mass Storage support registered.
[4296589.483000]   Vendor:           Model: USB DISK Pro      Rev: PMAP
[4296589.483000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4296589.483000]   Vendor:           Model: USB DISK Pro      Rev: PMAP
[4296589.483000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4296589.488000] usb-storage: device scan complete
[4296589.552000] Driver 'sd' needs updating - please use bus_type methods
[4296589.554000] SCSI device sda: 430528 512-byte hdwr sectors (220 MB)
[4296589.555000] sda: Write Protect is off
[4296589.555000] sda: Mode Sense: 23 00 00 00
[4296589.555000] sda: assuming drive cache: write through
[4296589.559000] SCSI device sda: 430528 512-byte hdwr sectors (220 MB)
[4296589.559000] sda: Write Protect is off
[4296589.560000] sda: Mode Sense: 23 00 00 00
[4296589.560000] sda: assuming drive cache: write through
[4296589.560000]  sda: sda1
[4296589.662000] sd 0:0:0:0: Attached scsi removable disk sda
[4296589.666000] SCSI device sdb: 50176 512-byte hdwr sectors (26 MB)
[4296589.667000] sdb: Write Protect is off
[4296589.667000] sdb: Mode Sense: 23 00 00 00
[4296589.667000] sdb: assuming drive cache: write through
[4296589.671000] SCSI device sdb: 50176 512-byte hdwr sectors (26 MB)
[4296589.672000] sdb: Write Protect is off
[4296589.672000] sdb: Mode Sense: 23 00 00 00
[4296589.672000] sdb: assuming drive cache: write through
[4296589.672000]  sdb: sdb1
[4296589.688000] sd 0:0:0:1: Attached scsi removable disk sdb
[4296589.701000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4296589.701000] sd 0:0:0:1: Attached scsi generic sg1 type 0
[4296590.407000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4296590.528000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```
I tried the USB KEY in WinXP and also on other computers and on all of them it creates 2drives. Why is that so???

---

### Post by NinjitsuStylee on 2006-07-26
I believe it has to do with a system called U3. 

[www.u3.com](www.u3.com) should explain it.

---

