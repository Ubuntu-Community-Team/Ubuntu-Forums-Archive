---
title: "Connecting external hard drive problems"
date: 2017-10-16
forum: Hardware
---

### Post by serapred on 2017-10-16
[COLOR=#242729][FONT=Arial]I'm using vmware with ubuntu 14.04 LTS. When i try to connect my seagate M3, the virtual machine actually recognize it, but it doesn't get mounted nor recognized by the system. After a little bit of digging, looks like the device is indeed connected as the command **lsusb** shows:[/FONT][/COLOR]
```
Bus 004 Device 004: ID 0bc2:61b6 Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```[COLOR=#242729][FONT=Arial]checking the syslog showed that the system actually tries to mount it, failing:[/FONT][/COLOR]
```
Oct 16 11:42:43 ubuntu kernel: [  479.209798] usb 4-1: new SuperSpeed USB device number 4 using xhci_hcd
Oct 16 11:42:43 ubuntu kernel: [  479.228756] usb 4-1: New USB device found, idVendor=0bc2, idProduct=61b6
Oct 16 11:42:43 ubuntu kernel: [  479.228774] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 16 11:42:43 ubuntu kernel: [  479.228775] usb 4-1: Product: M3
Oct 16 11:42:43 ubuntu kernel: [  479.228776] usb 4-1: Manufacturer: Seagate
Oct 16 11:42:43 ubuntu kernel: [  479.228777] usb 4-1: SerialNumber: NM124VYT
Oct 16 11:42:43 ubuntu kernel: [  479.427608] scsi host35: uas
Oct 16 11:42:43 ubuntu kernel: [  479.429253] usb 4-1: stat urb: status -32
Oct 16 11:42:43 ubuntu kernel: [  479.429273] scsi 35:0:0:0: tag#0 data cmplt err -32 uas-tag 1 inflight: CMD 
Oct 16 11:42:43 ubuntu kernel: [  479.429276] scsi 35:0:0:0: tag#0 CDB: Inquiry 12 00 00 00 24 00
Oct 16 11:42:41 ubuntu vmsvc[1298]: message repeated 10 times: [ [ warning] [guestinfo] Failed to get vmstats.]
Oct 16 11:42:43 ubuntu mtp-probe: checking bus 4, device 4: "/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/usb4/4-1"
Oct 16 11:42:43 ubuntu mtp-probe: bus: 4, device: 4 was not an MTP device
Oct 16 11:43:04 ubuntu kernel: [  500.862644] scsi 35:0:0:0: tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD 
Oct 16 11:43:04 ubuntu kernel: [  500.862650] scsi 35:0:0:0: tag#0 CDB: Inquiry 12 00 00 00 24 00
Oct 16 11:43:04 ubuntu kernel: [  500.862713] scsi host35: uas_eh_bus_reset_handler start
Oct 16 11:43:04 ubuntu kernel: [  500.977721] usb 4-1: reset SuperSpeed USB device number 4 using xhci_hcd
Oct 16 11:43:04 ubuntu kernel: [  501.014051] scsi host35: uas_eh_bus_reset_handler success
Oct 16 11:43:04 ubuntu kernel: [  501.014652] usb 4-1: stat urb: status -32
Oct 16 11:43:04 ubuntu kernel: [  501.017564] scsi 35:0:0:0: tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD 
Oct 16 11:43:04 ubuntu kernel: [  501.017567] scsi 35:0:0:0: tag#0 CDB: Test Unit Ready 00 00 00 00 00 00
Oct 16 11:43:04 ubuntu kernel: [  501.017570] scsi host35: uas_eh_bus_reset_handler start
Oct 16 11:43:05 ubuntu kernel: [  501.234951] usb 4-1: reset SuperSpeed USB device number 4 using xhci_hcd
Oct 16 11:43:05 ubuntu kernel: [  501.301555] scsi host35: uas_eh_bus_reset_handler success
Oct 16 11:43:05 ubuntu kernel: [  501.301561] scsi 35:0:0:0: Device offlined - not ready after error recovery

```[COLOR=#242729][FONT=Arial]Apparently i get this -32 error with this usb 4-1.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Does anyone has any idea of why this might happen? Can't find anything relevant online.[/FONT][/COLOR]

---

