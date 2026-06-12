---
title: "USB external HDD and MP3 key"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by rbonnefoi on 2006-06-18
Hello,

I have several problems mounting USB disks. I think it happened since I upgraded from breezy to dapper. Anyway, it used to work fine a few weeks ago.

I have 2 IDE hdd converted to an external one using a usb enclosure and one MP3 key. And I can't mount them at all. Here is the informations I have :

From **dmesg** :

```
[17292477.000000] usb 1-3: new high speed USB device using ehci_hcd and address 7
[17292477.132000] scsi4 : SCSI emulation for USB Mass Storage devices
[17292477.132000] usb-storage: device found at 7
[17292477.132000] usb-storage: waiting for device to settle before scanning
[17292487.744000] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[17292497.988000] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[17292503.232000] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[17292513.480000] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[17292513.620000]  4:0:0:0: scsi: Device offlined - not ready after error recovery
[17292513.620000] usb-storage: device scan complete
```

from **lsusb** :
```
Bus 001 Device 007: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
```

from **cat /proc/bus/usb/devices** :
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-25-k7 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04b4 ProdID=6830 Rev= 0.01
S:  Manufacturer=Cypress Semiconductor
S:  Product=USB2.0 Storage Device
S:  SerialNumber=DEF10A9CF0CE
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
```

and finally from **lsmod | grep usb** :
```
usb_storage            80000  0
usbnet                 18952  1 cdc_ether
usbcore               138948  6 usb_storage,cdc_ether,usbnet,ehci_hcd,ohci_hcd
scsi_mod              145736  4 usb_storage,sr_mod,sbp2,libata
```

I do really not know how to solve it. Any help would be greatly appreciated, as this disk is used as a backup disk.

Thanks.

Remi.

---

