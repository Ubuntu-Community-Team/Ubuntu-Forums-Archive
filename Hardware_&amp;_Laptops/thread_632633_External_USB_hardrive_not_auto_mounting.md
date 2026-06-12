---
title: "External USB hardrive not auto mounting"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by slibuntu on 2007-12-05
Hi,
Havent been able to find an answer for this, my external hard drive isn't mounting automatically, even if its connected when i boot. Its a fat32 seagate 320gb drive, heres what dmesg gives when i connect it

```

[  504.028000] usb 5-6: new high speed USB device using ehci_hcd and address 4
[  504.160000] usb 5-6: configuration #1 chosen from 1 choice
[  504.260000] scsi3 : SCSI emulation for USB Mass Storage devices
[  504.260000] usb-storage: device found at 4
[  504.260000] usb-storage: waiting for device to settle before scanning
[  509.260000] usb-storage: device scan complete
[  509.260000] scsi 3:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
[  509.264000] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  509.264000] sd 3:0:0:0: [sdb] Write Protect is off
[  509.264000] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  509.264000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  509.268000] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  509.268000] sd 3:0:0:0: [sdb] Write Protect is off
[  509.268000] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  509.268000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  509.268000]  sdb: sdb1
[  509.304000] sd 3:0:0:0: [sdb] Attached SCSI disk
[  509.304000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  524.392000] usb 5-6: USB disconnect, address 4
[  533.668000] usb 5-6: new high speed USB device using ehci_hcd and address 5
[  533.800000] usb 5-6: configuration #1 chosen from 1 choice
[  533.800000] scsi4 : SCSI emulation for USB Mass Storage devices
[  533.800000] usb-storage: device found at 5
[  533.800000] usb-storage: waiting for device to settle before scanning
[  538.800000] usb-storage: device scan complete
[  538.800000] scsi 4:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
[  538.804000] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  538.804000] sd 4:0:0:0: [sdb] Write Protect is off
[  538.804000] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  538.804000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  538.804000] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  538.804000] sd 4:0:0:0: [sdb] Write Protect is off
[  538.804000] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  538.804000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  538.804000]  sdb: sdb1
[  538.836000] sd 4:0:0:0: [sdb] Attached SCSI disk
[  538.836000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  700.924000] usb 5-6: USB disconnect, address 5
[  711.440000] usb 5-6: new high speed USB device using ehci_hcd and address 6
[  711.572000] usb 5-6: configuration #1 chosen from 1 choice
[  711.572000] scsi5 : SCSI emulation for USB Mass Storage devices
[  711.572000] usb-storage: device found at 6
[  711.572000] usb-storage: waiting for device to settle before scanning
[  716.572000] usb-storage: device scan complete
[  716.572000] scsi 5:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
[  716.576000] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  716.576000] sd 5:0:0:0: [sdb] Write Protect is off
[  716.576000] sd 5:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  716.576000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  716.580000] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  716.580000] sd 5:0:0:0: [sdb] Write Protect is off
[  716.580000] sd 5:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  716.580000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  716.580000]  sdb: sdb1
[  716.612000] sd 5:0:0:0: [sdb] Attached SCSI disk
[  716.616000] sd 5:0:0:0: Attached scsi generic sg2 type 0


```


I'm able to mount it using sudo mount -t vfat /dev/sdb1 /media/sdb1, but i want it to 
work automatically, can anyone help?

---

### Post by gcastell on 2007-12-05
I had the same problem, check my solution [here]("http://ubuntuforums.org/showthread.php?t=629865"), maybe not the best solution but at least I made it work. :guitar:

---

### Post by slibuntu on 2007-12-06
No luck, im getting operation not permitted for each file individually when i run the command you mention, even though i am running it as sudo, any other ideas?
 
On a side note, i can't partition this drive either, the gParted live CD gives me an error when it tries to shrink the existing partition,

---

