---
title: "External HD not mounting"
date: 2009-03-14
forum: Hardware
---

### Post by nwadams on 2009-03-14
Hi

My External HD is not mounting on my dell xps m1330 laptop. 
It is an acomdata samba external drive enclosure with a 1TB drive in it.
usb 2.0

It mounts ok on my desktop running the same version of ubuntu. 

```
nwadams@nwadams-laptop:~$ lsusb
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

nwadams@nwadams-laptop:~$ dmesg | tail
[ 1377.018454] usb 4-1: new high speed USB device using ehci_hcd and address 17
[ 1377.124899] usb 4-1: device descriptor read/64, error -71
[ 1377.192809] usb 4-1: device descriptor read/64, error -71
[ 1377.381863] usb 4-1: new high speed USB device using ehci_hcd and address 18
[ 1377.451288] usb 4-1: device descriptor read/64, error -71
[ 1377.527619] usb 4-1: device descriptor read/64, error -71
[ 1377.637157] usb 4-1: new high speed USB device using ehci_hcd and address 19
[ 1377.784025] usb 4-1: device not accepting address 19, error -71
[ 1377.822227] usb 4-1: new high speed USB device using ehci_hcd and address 20
[ 1377.947432] usb 4-1: device not accepting address 20, error -71
```

drive isn't showing up in fdisk -l
if i plug it in before boot it is detected and mounts properly.
if i run lsusb right after i plug it in it shows up in lsusb for a few seconds and then if i run it again its gone 
here's lsusb and dmesg | tail right after i plug it in. 5 seconds later and both those commands show similar to above. 

```
nwadams@nwadams-laptop:~$ lsusb
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 021: ID 0c0b:b157 Dura Micro, Inc. (Acomdata) 
Bus 004 Device 005: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
nwadams@nwadams-laptop:~$ dmesg | tail
[ 1377.527619] usb 4-1: device descriptor read/64, error -71
[ 1377.637157] usb 4-1: new high speed USB device using ehci_hcd and address 19
[ 1377.784025] usb 4-1: device not accepting address 19, error -71
[ 1377.822227] usb 4-1: new high speed USB device using ehci_hcd and address 20
[ 1377.947432] usb 4-1: device not accepting address 20, error -71
[ 1482.919699] usb 4-1: new high speed USB device using ehci_hcd and address 21
[ 1482.965814] usb 4-1: configuration #1 chosen from 1 choice
[ 1482.967914] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1482.968006] usb-storage: device found at 21
[ 1482.968009] usb-storage: waiting for device to settle before scanning

```
is there any issue that the bus number in these two lines is the same
Bus 004 Device 021: ID 0c0b:b157 Dura Micro, Inc. (Acomdata) 
Bus 004 Device 005: ID 05a9:2640 OmniVision Technologies, Inc.

Oh and usb thumbdrives work perfectly

---

### Post by nwadams on 2009-03-15
bump...Nobody can help me???

---

### Post by nwadams on 2009-03-19
bump...again. New info, it seems to work better with 8.10 (a third computer)

---

