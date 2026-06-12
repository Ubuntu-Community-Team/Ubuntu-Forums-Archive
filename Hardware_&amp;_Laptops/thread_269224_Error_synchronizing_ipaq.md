---
title: "Error synchronizing ipaq"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by damotor on 2006-10-01
Im' tryng to synchronize my ipaq 3950 through USB.
When I plug it I get this in dmesg:
```
Oct  1 20:33:22 localhost kernel: [17184387.740000] usb 3-1: new full speed USB device using uhci_hcd and address 47
Oct  1 20:33:22 localhost kernel: [17184387.876000] ipaq 3-1:1.0: PocketPC PDA converter detected
Oct  1 20:33:22 localhost kernel: [17184387.876000] usb 3-1: PocketPC PDA converter now attached to ttyUSB0
```
Then I do "sudo synce-serial-config ttyUSB0" wich returns
```
You can now run synce-serial-start to start a serial connection.
```
After that I write "dccm -d 3 -f" and I recieve
```
dccm[8536]: Running in foreground
dccm[8536]: Running command: /home/yo/.synce/scripts/dccm.sh start
ERROR: Couldn't attach to DCOP server!
dccm[8536]: Listening for connections on port 5679
```
And finally "sudo synce-serial-start" returns :
```
synce-serial-start is now waiting for your device to connect
```
This new lines appear in dmesg:
```
Oct  1 20:34:46 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Oct  1 20:34:46 localhost pppd[8568]: pppd 2.4.4b1 started by root, uid 0
```
But when I write "synce-pstatus" I get
```
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
```

What can I do? pls

---

