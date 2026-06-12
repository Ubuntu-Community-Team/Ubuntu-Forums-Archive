---
title: "CFIO GPS Support through USB Card Reader?"
date: 2010-06-26
forum: Hardware
---

### Post by justinchudgar on 2010-06-26
I have a  Compact Flash form factor GPS (Holux 270) that I would like to be able  to use as a NTP time source. I have a box on my network with a USB CF  card reader that I wish to make into my NTP server, however, the CFIO  GPS is not recognized. I have tried manually modprobing usbserial and  garmin-gps, to no avail. Dmesg notes the device insertion, but not much  else. Same goes for syslog. [INDENT] 	Code:
 	Jun 25 18:11:07 media01 kernel: [838677.250018] usb 1-7: new high speed USB device using ehci_hcd and address 4
Jun 25 18:11:07 media01 kernel: [838677.402563] usb 1-7: configuration #1 chosen from 1 choice
Jun 25 18:11:07 media01 kernel: [838677.403360] scsi7 : SCSI emulation for USB Mass Storage devices
Jun 25 18:11:07 media01 kernel: [838677.403587] usb-storage: device found at 4
Jun 25 18:11:07 media01 kernel: [838677.403592] usb-storage: waiting for device to settle before scanning
Jun 25 18:11:12 media01 kernel: [838682.400248] usb-storage: device scan complete
Jun 25 18:11:12 media01 kernel: [838682.400843] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Jun 25 18:11:12 media01 kernel: [838682.401459] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Jun 25 18:11:12 media01 kernel: [838682.401957] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Jun 25 18:11:12 media01 kernel: [838682.402457] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Jun 25 18:11:12 media01 kernel: [838682.403369] sd 7:0:0:0: Attached scsi generic sg3 type 0
Jun 25 18:11:12 media01 kernel: [838682.416817] sd 7:0:0:1: Attached scsi generic sg4 type 0
Jun 25 18:11:12 media01 kernel: [838682.419509] sd 7:0:0:2: Attached scsi generic sg5 type 0
Jun 25 18:11:12 media01 kernel: [838682.420666] sd 7:0:0:3: Attached scsi generic sg6 type 0
Jun 25 18:11:12 media01 kernel: [838682.426851] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Jun 25 18:11:31 media01 kernel: [838701.285412] sd 7:0:0:2: [sde] Attached SCSI removable disk
Jun 25 18:11:31 media01 kernel: [838701.287270] sd 7:0:0:3: [sdf] Attached SCSI removable disk
Jun 25 18:11:31 media01 kernel: [838701.288011] sd 7:0:0:1: [sdd] Attached SCSI removable disk 
[/INDENT]I would like to GPS to show up as /dev/ttyS0 or  /dev/ttyUSB0, but I have no idea if it is possible to access a Compact  Flash IO device through a USB card reader. I have googled for a while,  but everything I have unearthed seems to refer to embedded systems using  either 2.4 or early 2.6 kernels. 

Any information is appreciated. Thank you.

---

