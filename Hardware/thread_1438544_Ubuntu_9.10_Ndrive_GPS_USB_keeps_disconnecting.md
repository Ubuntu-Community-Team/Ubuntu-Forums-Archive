---
title: "Ubuntu 9.10 Ndrive GPS USB keeps disconnecting"
date: 2010-03-25
forum: Hardware
---

### Post by pleandro on 2010-03-25
Hi,
I have a Ndrive GPS (WinCE) and when I connect to my Acer laptop (Aspire 5630), it keeps conecting/disconnecting.

Here are the relevant entries in my log files:

...
Mar 25 09:45:35 uhuru kernel: [ 2725.184145] usb 3-1: new full speed USB device using uhci_hcd and address 12
Mar 25 09:45:36 uhuru kernel: [ 2725.330990] usb 3-1: configuration #1 chosen from 1 choice
Mar 25 09:45:43 uhuru kernel: [ 2732.384190] usb 3-1: USB disconnect, address 12
Mar 25 10:24:27 uhuru kernel: [ 5056.384086] usb 3-1: new full speed USB device using uhci_hcd and address 13
Mar 25 10:24:27 uhuru kernel: [ 5056.527079] usb 3-1: configuration #1 chosen from 1 choice
Mar 25 10:24:27 uhuru kernel: [ 5056.545082] USB Serial support registered for PocketPC PDA
Mar 25 10:24:27 uhuru kernel: [ 5056.545177] ipaq 3-1:1.0: PocketPC PDA converter detected
Mar 25 10:24:27 uhuru kernel: [ 5056.547058] usb 3-1: PocketPC PDA converter now attached to ttyUSB0
Mar 25 10:24:27 uhuru kernel: [ 5056.547090] usbcore: registered new interface driver ipaq
Mar 25 10:24:27 uhuru kernel: [ 5056.547094] ipaq: v0.5:USB PocketPC PDA driver
Mar 25 10:24:34 uhuru kernel: [ 5063.584121] usb 3-1: USB disconnect, address 13
Mar 25 10:24:34 uhuru kernel: [ 5063.584521] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 25 10:24:34 uhuru kernel: [ 5063.584552] ipaq 3-1:1.0: device disconnected
Mar 25 10:24:37 uhuru kernel: [ 5067.048079] usb 3-1: new full speed USB device using uhci_hcd and address 14
Mar 25 10:24:37 uhuru kernel: [ 5067.190913] usb 3-1: configuration #1 chosen from 1 choice
Mar 25 10:24:37 uhuru kernel: [ 5067.193817] ipaq 3-1:1.0: PocketPC PDA converter detected
Mar 25 10:24:37 uhuru kernel: [ 5067.195881] usb 3-1: PocketPC PDA converter now attached to ttyUSB0
Mar 25 10:24:44 uhuru kernel: [ 5074.248558] usb 3-1: USB disconnect, address 14
Mar 25 10:24:44 uhuru kernel: [ 5074.248890] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 25 10:24:44 uhuru kernel: [ 5074.248919] ipaq 3-1:1.0: device disconnected
Mar 25 10:24:48 uhuru kernel: [ 5077.712079] usb 3-1: new full speed USB device using uhci_hcd and address 15
Mar 25 10:24:48 uhuru kernel: [ 5077.854726] usb 3-1: configuration #1 chosen from 1 choice
Mar 25 10:24:48 uhuru kernel: [ 5077.859535] ipaq 3-1:1.0: PocketPC PDA converter detected
Mar 25 10:24:48 uhuru kernel: [ 5077.869893] usb 3-1: PocketPC PDA converter now attached to ttyUSB0
Mar 25 10:24:55 uhuru kernel: [ 5084.912116] usb 3-1: USB disconnect, address 15
Mar 25 10:24:55 uhuru kernel: [ 5084.912452] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 25 10:24:55 uhuru kernel: [ 5084.912481] ipaq 3-1:1.0: device disconnected
Mar 25 10:24:59 uhuru kernel: [ 5088.376091] usb 3-1: new full speed USB device using uhci_hcd and address 16
Mar 25 10:24:59 uhuru kernel: [ 5088.518476] usb 3-1: configuration #1 chosen from 1 choice
Mar 25 10:24:59 uhuru kernel: [ 5088.524614] ipaq 3-1:1.0: PocketPC PDA converter detected
Mar 25 10:24:59 uhuru kernel: [ 5088.526744] usb 3-1: PocketPC PDA converter now attached to ttyUSB0
Mar 25 10:25:06 uhuru kernel: [ 5095.577081] usb 3-1: USB disconnect, address 16
Mar 25 10:25:06 uhuru kernel: [ 5095.577429] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 25 10:25:06 uhuru kernel: [ 5095.577459] ipaq 3-1:1.0: device disconnected
Mar 25 10:25:09 uhuru kernel: [ 5099.097042] usb 3-1: new full speed USB device using uhci_hcd and address 17
Mar 25 10:25:09 uhuru kernel: [ 5099.243275] usb 3-1: configuration #1 chosen from 1 choice
Mar 25 10:25:09 uhuru kernel: [ 5099.248883] ipaq 3-1:1.0: PocketPC PDA converter detected
Mar 25 10:25:09 uhuru kernel: [ 5099.250551] usb 3-1: PocketPC PDA converter now attached to ttyUSB0
Mar 25 10:25:17 uhuru kernel: [ 5106.488615] usb 3-1: USB disconnect, address 17
Mar 25 10:25:17 uhuru kernel: [ 5106.488968] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Mar 25 10:25:17 uhuru kernel: [ 5106.488997] ipaq 3-1:1.0: device disconnected
...

Any help?
Thanks.

---

