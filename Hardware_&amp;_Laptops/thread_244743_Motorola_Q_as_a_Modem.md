---
title: "Motorola Q as a Modem?"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by angelmartini on 2006-08-26
Is it possible to use my Verizon Motorola Q as a modem in Linux?
I can do it in Windows.

---

### Post by extremx on 2008-01-14
Hi, was googleing and found this thread.

Ok, i also want to use my moto Q (q9m, windows mobile 6) as a usb modem, but i am having issues with it being assign to a /dev/USB0 or /dev/ACM0 (AMC0?)

my lsusb show that it sees it, but how do i get it assigned to a device variable? if i can get it to a device then i could use it.

Thanks in advance.

Here is my dmesg:
> [41042.836000] usb 1-3: new high speed USB device using ehci_hcd and address 5
[41042.968000] usb 1-3: configuration #1 chosen from 1 choice
[41042.968000] hub 1-3:1.0: USB hub found
[41042.968000] hub 1-3:1.0: 4 ports detected
[44704.716000] usb 2-7: new full speed USB device using ohci_hcd and address 4
[44704.928000] usb 2-7: configuration #1 chosen from 1 choice
[44705.000000] usbcore: registered new interface driver cdc_ether
[44705.004000] usb 2-7: bad CDC descriptors
[44705.004000] usbcore: registered new interface driver rndis_host


and my lsusb:

> Bus 002 Device 004: ID 22b8:7003 Motorola PCS
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 1293:2101 Belkin Components [hex] 104-key keyboard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0424:2504 Standard Microsystems Corp.
Bus 001 Device 001: ID 0000:0000


---

