---
title: "Maxtor OneTouch II Problems"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by fastkeys38 on 2005-07-05
Hi

When I first installed Ubuntu this 300GB VFAT Maxtor OneTouchII drive used to mount up fine.

I've recently gone to use it again (since doing the upgrade 2.6.10-34) and now when I plug the device I get:

usb 1-1: new full speed USB device using uhci_hcd and address 3
usb 1-1: device descriptor read/64, error -71
usb 1-1: device descriptor read/64, error -71
usb 1-1: new full speed USB device using uhci_hcd and address 4
usb 1-1: device descriptor read/64, error -71
usb 1-1: device descriptor read/64, error -71

The device is therefore not recognised.

I borrowed another identical drive but get the same message. Both drives mount fine on Wintel/Mac boxes.

I've read lots of similar messages about 2.6.10 and USB support.

I tried issuing rmmod uhci-hdc but it makes no odds.

Is there a workaround on it's way?

Cheers

Alex

---

### Post by fastkeys38 on 2005-07-05
OK much wierdness.

I rebooted and it made no difference, so I plugged it in to a different USB port and it worked fine.

Strange thing is it WAS working in that port (I never remove the cable) and the board only has one USB controller on it?!

Time will tell if I've been lucky this time...  :roll:

---

### Post by puluca on 2008-07-08
Hi All,

I have the same problem with Maxtor One Touch III 160Gb.

Here some informations to help me to fix it:

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

If you need any other informations call me I will be happy in provide that.

Help me to solve it please.

Regards
Puluca

---

