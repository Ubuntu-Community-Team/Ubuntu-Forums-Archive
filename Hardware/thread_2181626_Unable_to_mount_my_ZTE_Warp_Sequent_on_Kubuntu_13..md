---
title: "Unable to mount my ZTE Warp Sequent on Kubuntu 13.04"
date: 2013-10-18
forum: Hardware
---

### Post by aaronschillings on 2013-10-18
When I run lsusb in my Konsole(Terminal) with my phone attached this is what I see:

```
Bus 001 Device 002: ID 04f2:b3bd Chicony Electronics Co., Ltd Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 005 Device 006: ID 19d2:0306 ZTE WCDMA Technologies MSM 
Bus 005 Device 002: ID 062a:4101 Creative Labs 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

So I know that the system is reading my phone properly.  However, I"m unable to figure the name of the special device it is assigning the phone to.  When I run vi /var/log/syslog I see the following concerning my phone:

```
Oct 18 11:56:59 Chillin mtp-probe: checking bus 5, device 5: "/sys/devices/pci0000:00/0000:00:10.0/usb5/5-1"
Oct 18 11:56:59 Chillin mtp-probe: bus: 5, device: 5 was not an MTP device
Oct 18 11:56:59 Chillin kernel: [  349.255168] Initializing USB Mass Storage driver...
Oct 18 11:56:59 Chillin kernel: [  349.261280] scsi3 : usb-storage 5-1:1.0
Oct 18 11:56:59 Chillin kernel: [  349.261854] usbcore: registered new interface driver usb-storage
Oct 18 11:56:59 Chillin kernel: [  349.261861] USB Mass Storage support registered.
Oct 18 11:57:00 Chillin kernel: [  350.260124] scsi 3:0:0:0: Direct-Access     Linux    File-CD Gadget   0000 PQ: 0 ANSI: 2
Oct 18 11:57:00 Chillin kernel: [  350.263254] sd 3:0:0:0: Attached scsi generic sg3 type 0
Oct 18 11:57:00 Chillin kernel: [  350.264343] sd 3:0:0:0: [sdc] Attached SCSI removable disk
Oct 18 11:57:46 Chillin kernel: [  395.956827] usb 5-1: USB disconnect, device number 5
Oct 18 11:57:46 Chillin kernel: [  396.237017] usb 5-1: new high-speed USB device number 6 using xhci_hcd
Oct 18 11:57:46 Chillin kernel: [  396.256247] usb 5-1: New USB device found, idVendor=19d2, idProduct=0306
Oct 18 11:57:46 Chillin kernel: [  396.256260] usb 5-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Oct 18 11:57:46 Chillin kernel: [  396.256267] usb 5-1: Product: Android
Oct 18 11:57:46 Chillin kernel: [  396.256274] usb 5-1: Manufacturer: Android
Oct 18 11:57:46 Chillin kernel: [  396.256280] usb 5-1: SerialNumber: A0000032D93479 
```

I have my phone set to MTP mode in the USB options and also have the SDK and ADT drivers downloaded already.  Any advice would be much appreciated!

---

