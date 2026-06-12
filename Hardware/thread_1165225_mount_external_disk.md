---
title: "mount external disk"
date: 2009-05-20
forum: Hardware
---

### Post by kumarnarain on 2009-05-20
Hai
I tried connecting my old sata hdd through a usb bridge......to restore some of my old data...but my new jaunty would have none of it....Pasted below is the output of tail  /var/log/messages::



kumar@kumarHome:~/Desktop$ tail -f /var/log/messages
May 16 17:14:41 kumarHome pulseaudio[3436]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May 16 17:14:41 kumarHome pulseaudio[3436]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
May 16 17:14:56 kumarHome kernel: [   54.693382] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
May 16 17:32:34 kumarHome kernel: [ 1112.200057] usb 2-1: USB disconnect, address 2
May 16 17:32:34 kumarHome kernel: [ 1112.200061] usb 2-1.1: USB disconnect, address 3
May 16 17:32:34 kumarHome kernel: [ 1112.444034] usb 2-1: new full speed USB device using uhci_hcd and address 4
May 16 17:32:34 kumarHome kernel: [ 1112.614212] usb 2-1: configuration #1 chosen from 1 choice
May 16 17:32:34 kumarHome kernel: [ 1112.616851] hub 2-1:1.0: USB hub found
May 16 17:32:34 kumarHome kernel: [ 1112.618791] hub 2-1:1.0: 4 ports detected
May 16 17:32:35 kumarHome kernel: [ 1112.901797] usb 2-1.1: new full speed USB device using uhci_hcd and address 5
May 16 17:32:58 kumarHome kernel: [ 1136.504055] usb 2-1: USB disconnect, address 4
May 16 17:32:58 kumarHome kernel: [ 1136.744034] usb 2-1: new full speed USB device using uhci_hcd and address 9
May 16 17:32:59 kumarHome kernel: [ 1136.913440] usb 2-1: configuration #1 chosen from 1 choice
May 16 17:32:59 kumarHome kernel: [ 1136.916422] hub 2-1:1.0: USB hub found
May 16 17:32:59 kumarHome kernel: [ 1136.918545] hub 2-1:1.0: 4 ports detected
May 16 17:32:59 kumarHome kernel: [ 1137.201334] usb 2-1.1: new full speed USB device using uhci_hcd and address 10
May 16 17:33:29 kumarHome kernel: [ 1167.626016] usb 2-1.1: new full speed USB device using uhci_hcd and address 11
May 16 17:34:00 kumarHome kernel: [ 1198.049682] usb 2-1.1: new full speed USB device using uhci_hcd and address 12
May 16 17:34:10 kumarHome kernel: [ 1208.369913] usb 2-1.1: new full speed USB device using uhci_hcd and address 13
May 16 17:34:20 kumarHome kernel: [ 1218.817143] usb 2-1.2: new full speed USB device using uhci_hcd and address 14
May 16 17:34:21 kumarHome kernel: [ 1218.922253] usb 2-1.2: not running at top speed; connect to a high speed hub
May 16 17:34:21 kumarHome kernel: [ 1218.960271] usb 2-1.2: configuration #1 chosen from 1 choice
May 16 17:34:21 kumarHome kernel: [ 1219.020675] Initializing USB Mass Storage driver...
May 16 17:34:21 kumarHome kernel: [ 1219.020891] scsi4 : SCSI emulation for USB Mass Storage devices
May 16 17:34:21 kumarHome kernel: [ 1219.021015] usbcore: registered new interface driver usb-storage
May 16 17:34:21 kumarHome kernel: [ 1219.021020] USB Mass Storage support registered.
May 16 17:34:26 kumarHome kernel: [ 1224.024388] scsi 4:0:0:0: Direct-Access     ST320082 6AS                   PQ: 0 ANSI: 2 CCS
May 16 17:34:26 kumarHome kernel: [ 1224.048029] sd 4:0:0:0: [sdb] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
May 16 17:34:26 kumarHome kernel: [ 1224.050268] sd 4:0:0:0: [sdb] Write Protect is off
May 16 17:34:26 kumarHome kernel: [ 1224.055281] sd 4:0:0:0: [sdb] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
May 16 17:34:26 kumarHome kernel: [ 1224.058268] sd 4:0:0:0: [sdb] Write Protect is off
May 16 17:34:26 kumarHome kernel: [ 1224.058283]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 sdb7 sdb8 sdb9 >
May 16 17:34:26 kumarHome kernel: [ 1224.165719] sd 4:0:0:0: [sdb] Attached SCSI disk
May 16 17:34:26 kumarHome kernel: [ 1224.165822] sd 4:0:0:0: Attached scsi generic sg2 type 0
May 16 17:34:28 kumarHome kernel: [ 1226.852328] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
May 16 17:34:28 kumarHome kernel: [ 1226.852337] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
May 16 17:34:31 kumarHome kernel: [ 1229.401382] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
May 16 17:34:31 kumarHome kernel: [ 1229.401392] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
May 16 17:34:34 kumarHome kernel: [ 1231.949436] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
May 16 17:34:34 kumarHome kernel: [ 1231.949446] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
May 16 17:34:36 kumarHome kernel: [ 1234.507495] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
May 16 17:34:36 kumarHome kernel: [ 1234.507505] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
May 16 17:34:39 kumarHome kernel: [ 1237.056554] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
May 16 17:34:39 kumarHome kernel: [ 1237.056564] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
May 16 17:34:40 kumarHome kernel: [ 1238.353576] usb 2-1.2: reset full speed USB device using uhci_hcd and address 14
May 16 17:34:55 kumarHome kernel: [ 1253.789918] usb 2-1.2: reset full speed USB device using uhci_hcd and address 14
May 16 17:34:56 kumarHome kernel: [ 1254.237924] usb 2-1.2: reset full speed USB device using uhci_hcd and address 14
May 16 17:34:56 kumarHome kernel: [ 1254.721934] usb 2-1.2: reset full speed USB device using uhci_hcd and address 14
May 16 17:34:57 kumarHome kernel: [ 1255.136009] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
May 16 17:34:57 kumarHome kernel: [ 1255.136708] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
May 16 17:34:57 kumarHome kernel: [ 1255.139222] usb 2-1.2: USB disconnect, address 14
May 16 17:34:57 kumarHome kernel: [ 1255.140517] scsi 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
May 16 17:34:57 kumarHome kernel: [ 1255.213950] usb 2-1.2: new full speed USB device using uhci_hcd and address 15
May 16 17:34:57 kumarHome kernel: [ 1255.665959] usb 2-1.2: new full speed USB device using uhci_hcd and address 16
May 16 17:34:58 kumarHome kernel: [ 1256.113970] usb 2-1.2: new full speed USB device using uhci_hcd and address 17
May 16 17:34:58 kumarHome kernel: [ 1256.597978] usb 2-1.2: new full speed USB device using uhci_hcd and address 1

Any ideas??

---

