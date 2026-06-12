---
title: "cu: open (/dev/ttyUSB0): Permission denied cu: /dev/ttyUSB0: Line in use"
date: 2017-04-26
forum: Hardware
---

### Post by nulesus on 2017-04-26
Cant connect via serial terminal  /dev/ttyUSB0. I have tried several term programs with negative results. Denied even with root!

```
[66769.479819]  sdb: sdb1 sdb2 sdb3
[66769.482958] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[68702.975870]  sdb: sdb1 sdb2 sdb3
[68704.164366]  sdb: sdb1 sdb2 sdb3
[69330.742421]  sdb: sdb1 sdb2 sdb3 sdb4
[69793.979443] usb 10-2: USB disconnect, device number 3
[70942.448253] usb 10-2: new full-speed USB device number 4 using xhci_hcd
[70942.642402] usb 10-2: New USB device found, idVendor=067b, idProduct=2303
[70942.642415] usb 10-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[70942.642422] usb 10-2: Product: USB-Serial Controller D
[70942.642428] usb 10-2: Manufacturer: Prolific Technology Inc. 
[70943.706009] usbcore: registered new interface driver usbserial
[70943.706026] usbcore: registered new interface driver usbserial_generic
[70943.706037] usbserial: USB Serial support registered for generic
[70943.707451] usbcore: registered new interface driver pl2303
[70943.707463] usbserial: USB Serial support registered for pl2303
[70943.707487] pl2303 10-2:1.0: pl2303 converter detected
[70943.708391] usb 10-2: pl2303 converter now attached to ttyUSB0

root@ubuntus:/home/nulesus/Desktop# cu -l /dev/ttyUSB0 -s 38400
cu: open (/dev/ttyUSB0): Permission denied
cu: /dev/ttyUSB0: Line in use
root@ubuntus:/home/nulesus/Desktop# 
```

please help

---

### Post by Xian on 2017-04-26
While still as root try this:

# chmod 666 /dev/ttyUSB0

(... or ttyUSB1)

---

