---
title: "Maxtor One Touch III 160Gb error"
date: 2008-07-08
forum: Hardware
---

### Post by puluca on 2008-07-08
Hi All,

I have the problem with Maxtor One Touch III 160Gb the external Hdd
does not work fine. 

Here some informations to help me to fix it:

root@casas01:/proc/scsi/usb-storage# uname -a
Linux casas01 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
root@casas01:/proc/scsi/usb-storage# 


1- dmesg after plugin the device:

[ 5828.859389] usb 5-4: new high speed USB device using ehci_hcd and address 10
[ 5829.007684] usb 5-4: configuration #1 chosen from 1 choice
[ 5829.026283] scsi9 : SCSI emulation for USB Mass Storage devices
[ 5829.036045] usb-storage: device found at 10
[ 5829.036056] usb-storage: waiting for device to settle before scanning
[ 5834.034438] usb-storage: device scan complete
[ 5839.644829] usb 5-4: reset high speed USB device using ehci_hcd and address 10
[ 5844.755616] usb 5-4: device descriptor read/64, error -71
[ 5855.101162] usb 5-4: reset high speed USB device using ehci_hcd and address 10
[ 5871.341306] usb 5-4: reset high speed USB device using ehci_hcd and address 10
[ 5871.589260] usb 5-4: reset high speed USB device using ehci_hcd and address 10
[ 5881.830817] usb 5-4: reset high speed USB device using ehci_hcd and address 10
[ 5881.965510] scsi 9:0:0:0: Device offlined - not ready after error recovery


My lspci

root@casas01:/dev# lspci | grep -i usb
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)

USB informations:

root@casas01:/proc/scsi/usb-storage# ls
9
root@casas01:/proc/scsi/usb-storage# cat 9
   Host scsi9: usb-storage
       Vendor: Maxtor
      Product: Maxtor OneTouch III
Serial Number: 2CAS7F91
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:
root@casas01:/proc/scsi/usb-storage# 


Help me to solve it please.

Regards
Puluca

---

