---
title: "One Usb stick fast other one slow"
date: 2008-09-09
forum: Hardware
---

### Post by zarqoon on 2008-09-09
I've a weird problem with one of my usb sticks. Its really slow about 2mb/s . But another one i have works just fine.
On my sisters windows machine they both work fine.
I looked at the dmesg output and it shows the following:

Traxdata 4gb stick (the slow one)
```
[127244.854740] usb 1-7: new high speed USB device using ehci_hcd and address 11
[127244.988545] usb 1-7: configuration #1 chosen from 1 choice
[127244.989100] scsi8 : SCSI emulation for USB Mass Storage devices
[127244.989133] usb-storage: device found at 11
[127244.989135] usb-storage: waiting for device to settle before scanning
[127249.985752] usb-storage: device scan complete
[127249.987241] scsi 8:0:0:0: Direct-Access                               0.00 PQ: 0 ANSI: 2
[127249.989984] sd 8:0:0:0: [sdd] 7897088 512-byte hardware sectors (4043 MB)
[127249.991733] sd 8:0:0:0: [sdd] Write Protect is off
[127249.991736] sd 8:0:0:0: [sdd] Mode Sense: 00 00 00 00
[127249.991738] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[127249.997106] sd 8:0:0:0: [sdd] 7897088 512-byte hardware sectors (4043 MB)
[127249.998732] sd 8:0:0:0: [sdd] Write Protect is off
[127249.998735] sd 8:0:0:0: [sdd] Mode Sense: 00 00 00 00
[127249.998736] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[127249.998739]  sdd: unknown partition table
[127250.657927] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[127250.657964] sd 8:0:0:0: Attached scsi generic sg3 type 0

```

The other one Maxflash 4gb
```
[127382.354095] usb 1-7: new high speed USB device using ehci_hcd and address 12
[127382.487804] usb 1-7: configuration #1 chosen from 1 choice
[127382.503894] scsi9 : SCSI emulation for USB Mass Storage devices
[127382.504846] usb-storage: device found at 12
[127382.504849] usb-storage: waiting for device to settle before scanning
[127387.501130] usb-storage: device scan complete
[127387.502128] scsi 9:0:0:0: Direct-Access     USB2.0   FlashDisk        0.00 PQ: 0 ANSI: 2
[127387.504986] sd 9:0:0:0: [sdd] 7897088 512-byte hardware sectors (4043 MB)
[127387.505861] sd 9:0:0:0: [sdd] Write Protect is off
[127387.505863] sd 9:0:0:0: [sdd] Mode Sense: 00 00 00 00
[127387.505865] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[127387.510734] sd 9:0:0:0: [sdd] 7897088 512-byte hardware sectors (4043 MB)
[127387.512608] sd 9:0:0:0: [sdd] Write Protect is off
[127387.512611] sd 9:0:0:0: [sdd] Mode Sense: 00 00 00 00
[127387.512612] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[127387.512615]  sdd: unknown partition table
[127387.577760] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[127387.577794] sd 9:0:0:0: Attached scsi generic sg3 type 0

```

It seems that the traxdata stick is not connected at usb2.0 speeds which would explain the thing being dead slow.
I've read about some problems with nautilus in hardy but that affected all drives and i am still using gutsy.

This is the line is added to lsusb when i connect 

Maxflash
```
Bus 001 Device 012: ID 1307:0165  

```
Traxdata
```
Bus 001 Device 013: ID 1307:0165  

```

The rest
```
Bus 002 Device 007: ID 062a:0201 Creative Labs 
Bus 002 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 002: ID 046d:c215 Logitech, Inc. 
Bus 002 Device 005: ID 04f9:0182 Brother Industries, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

I am kind of puzzled why the traxdata stick wont work at full speed.

---

