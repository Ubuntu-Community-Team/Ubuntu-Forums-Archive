---
title: "Startech USB external HDD Trouble"
date: 2015-05-12
forum: Hardware
---

### Post by syntaxerror3 on 2015-05-12
I have a Startech 2 bay HDD to USB that I cannot seem to miount drives on.
Output of (sudo lusb:)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 174c:5106 ASMedia Technology Inc. Transcend StoreJet 25M3
Bus 004 Device 004: ID 2109:0810  
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 2109:3431  
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Output of: (dmesg | tail )
[  481.259269] usb 4-2.2: Product: AS2105
[  481.259272] usb 4-2.2: Manufacturer: ASMedia
[  481.259274] usb 4-2.2: SerialNumber: 00000000000000000000
[  481.259580] usb-storage 4-2.2:1.0: USB Mass Storage device detected
[  481.259755] usb-storage 4-2.2:1.0: Quirks match for vid 174c pid 5106: 800000
[  481.259849] scsi5 : usb-storage 4-2.2:1.0
[  482.259140] scsi 5:0:0:0: Direct-Access     ASMT     2105             0    PQ: 0 ANSI: 5
[  482.259485] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  482.260451] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  513.747443] systemd-hostnamed[2272]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

Tried to manually mount with a failure message and cannot find a good GUI utility to use (NOOB)

---

