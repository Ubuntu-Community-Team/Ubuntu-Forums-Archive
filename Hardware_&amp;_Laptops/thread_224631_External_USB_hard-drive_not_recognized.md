---
title: "External USB hard-drive not recognized"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by espenbe on 2006-07-28
I just bought an external USB 2.0 hard-drive (Maxtor personal storage 3200), but I can't get it to work with my Kubuntu 6.06. I don't know what is wrong. Here is some output:

```
espenbe@ball-9164:~$ lsusb 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 004 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

```
espenbe@ball-9164:~$ tail /var/log/messages
Jul 28 16:36:25 ball-9164 kernel: [17180739.880000] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jul 28 16:36:25 ball-9164 kernel: [17180740.020000] hub 4-1:1.0: USB hub found
Jul 28 16:36:25 ball-9164 kernel: [17180740.024000] hub 4-1:1.0: 4 ports detected
Jul 28 16:36:26 ball-9164 kernel: [17180740.352000] usb 4-1.2: new low speed USB device using uhci_hcd and address 3
Jul 28 16:36:26 ball-9164 kernel: [17180740.520000] input: Logitech Optical USB Mouse as /class/input/input4
Jul 28 16:36:26 ball-9164 kernel: [17180740.520000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.3-1.2
Jul 28 16:38:36 ball-9164 kernel: [17180870.644000] usb 4-2: new full speed USB device using uhci_hcd and address 4
Jul 28 16:38:37 ball-9164 kernel: [17180871.204000] usb 4-2: new full speed USB device using uhci_hcd and address 5
Jul 28 16:38:37 ball-9164 kernel: [17180871.764000] usb 4-2: new full speed USB device using uhci_hcd and address 6
Jul 28 16:38:38 ball-9164 kernel: [17180872.284000] usb 4-2: new full speed USB device using uhci_hcd and address 7

```

```
espenbe@ball-9164:~$ dmesg|tail
[17180870.644000] usb 4-2: new full speed USB device using uhci_hcd and address 4
[17180870.764000] usb 4-2: device descriptor read/64, error -71
[17180870.988000] usb 4-2: device descriptor read/64, error -71
[17180871.204000] usb 4-2: new full speed USB device using uhci_hcd and address 5
[17180871.324000] usb 4-2: device descriptor read/64, error -71
[17180871.548000] usb 4-2: device descriptor read/64, error -71
[17180871.764000] usb 4-2: new full speed USB device using uhci_hcd and address 6
[17180872.172000] usb 4-2: device not accepting address 6, error -71
[17180872.284000] usb 4-2: new full speed USB device using uhci_hcd and address 7
[17180872.692000] usb 4-2: device not accepting address 7, error -71
```


Because of this, I don't know how to access it to format it or mount it. Any wizards who can give me any clues?

Espen

---

### Post by rbalfour on 2006-07-28
Here is some info about that drive and Linux / MAC.

[http://techreport.com/forums/viewtopic.php?t=40970](http://techreport.com/forums/viewtopic.php?t=40970)

---

