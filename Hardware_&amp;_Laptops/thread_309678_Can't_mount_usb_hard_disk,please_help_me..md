---
title: "Can't mount usb hard disk,please help me."
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by shada on 2006-11-29
-------------------------------------------------------------------------
shada@laf-ubuntu:~$ dmesg|tail
[17193114.864000] usb 4-1: new full speed USB device using uhci_hcd and address 3
[17193115.004000] scsi3 : SCSI emulation for USB Mass Storage devices
[17193115.004000] usb-storage: device found at 3
[17193115.004000] usb-storage: waiting for device to settle before scanning
[17193120.120000] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[17193120.368000] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[17193120.616000] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[17193120.752000] usb-storage: device scan complete
shada@laf-ubuntu:~$ ls /dev/sd*
ls: /dev/sd*: No such file or directory
shada@laf-ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 003: ID 04ce:0002 ScanLogic Corp. SL11R-IDE IDE Bridge
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000
shada@laf-ubuntu:~$
-------------------------------------------------------------------------
I'm use ubuntu6.06
why not exist sda?
please help me.

---

### Post by chinese_ys on 2006-11-30
I use edgy. but after I plugin the usb disk, I can see the sda. I do not know why, hope some body will answer.

---

### Post by shada on 2006-11-30
top

---

