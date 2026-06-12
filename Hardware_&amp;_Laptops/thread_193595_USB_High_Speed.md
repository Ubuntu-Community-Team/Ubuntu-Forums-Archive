---
title: "USB High Speed"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by Hellz on 2006-06-10
Welcome,

I want to use my USB hard disk in Dapper. OS recognize it, mount, but it doesn't work in High Speed mode. In system logs i can find:

```
Jun 10 13:32:40 hellz-desktop kernel: [4305689.779000] usb 2-1: new full speed USB device using uhci_hcd and address 7
Jun 10 13:32:40 hellz-desktop kernel: [4305689.900000] usb 2-1: not running at top speed; connect to a high speed hub
Jun 10 13:32:40 hellz-desktop kernel: [4305689.907000] scsi1 : SCSI emulation for USB Mass Storage devices
Jun 10 13:32:40 hellz-desktop kernel: [4305689.907000] usb-storage: device found at 7
Jun 10 13:32:40 hellz-desktop kernel: [4305689.907000] usb-storage: waiting for device to settle before scanning
Jun 10 13:32:45 hellz-desktop kernel: [4305694.912000]   Vendor: SAMSUNG   Model: SP0812N           Rev: 0811
Jun 10 13:32:45 hellz-desktop kernel: [4305694.912000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jun 10 13:32:45 hellz-desktop kernel: [4305694.917000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
Jun 10 13:32:45 hellz-desktop kernel: [4305694.917000] sda: assuming drive cache: write through
Jun 10 13:32:45 hellz-desktop kernel: [4305694.923000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
Jun 10 13:32:45 hellz-desktop kernel: [4305694.923000] sda: assuming drive cache: write through
Jun 10 13:32:45 hellz-desktop kernel: [4305694.923000]  sda: sda1 sda2 < sda5 >
Jun 10 13:32:45 hellz-desktop kernel: [4305694.953000] sd 1:0:0:0: Attached scsi disk sda
Jun 10 13:32:45 hellz-desktop kernel: [4305694.953000] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jun 10 13:32:45 hellz-desktop kernel: [4305694.955000] usb-storage: device scan complete
```

Can anyone help me? 
Regards,

Hellz

---

### Post by muriloq on 2006-10-31
I'm experiencing exactly the same problem here, but with a DVD drive. My external USB drive works perfectly, but the optical one gives the same message ( usb 2-1: not running at top speed; connect to a high speed hub ). 

The working HDD is recognized as

ID 05ab:0060 In-System Design USB 2.0 ATA Bridge

The faulty DVD rom is recognized as
0402:5621 ALi Corp. USB 2.0 Storage Device

They both are connected to the same USB 2.0 hub. I've removed the hub and connected it directly to the main board, too. I'm using Xubuntu 6.10 (Edgy Eft), with the default kernel.

---

### Post by muriloq on 2006-11-01
I've found the origin of my problem: ACPI support. After turning it off (in BIOS setup, changing "ACPI Aware OS" to "No"), all the USB devices were correctly detected. 

The DVD-ROM drive (ID 0402:5621 ALi Corp. USB 2.0 Storage Device) sometimes isn't detected, but turning it off and then on again solves the problem.

In order to verify easily if everything is alright I'm using the utility usbview. The USB 2.0 devices should be listed under EHCI, and their speed should be 480 Mb/s.

---

