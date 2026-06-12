---
title: "[SOLVED] USB/IDE bridge :: ATAPI6 not working"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by fethio on 2007-10-13
Hi,

I am trying access an old hard linux hard drive using a USB/IDE brigde device called ULTRA Mini Portable Disk. I found out that people have already successfully done this, see for example the link::

[http://ubuntuforums.org/showthread.php?t=243787&highlight=ATAPI6+bridge](http://ubuntuforums.org/showthread.php?t=243787&highlight=ATAPI6+bridge)

in my system when i do [FONT=Courier New]lspci[/FONT] it returns with a line: 

> 
Bus 001 Device 011: ID 067b:3507 Prolific Technology, Inc. PL3507 ATAPI6 Bridge
so I guess, the device is recongnized. A [FONT=Courier New]dmesg[/FONT] input returns:

> usb 1-2: new high speed USB device using ehci_hcd and address 11
usb 1-2: new device found, idVendor=067b, idProduct=3507
usb 1-2: new device strings: Mfr=1, Product=2, SerialNumber=0
usb 1-2: Product: Mass Storage Device
usb 1-2: Manufacturer: Prolific Technology Inc.
usb 1-2: configuration #1 chosen from 1 choice
scsi5 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 11
  Vendor: WDC AC25  Model: 100L              Rev: 20.0
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 10085041 512-byte hdwr sectors (5164 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 10085041 512-byte hdwr sectors (5164 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 sda:<6>sda: Current: sense key: No Sense
    Additional sense: No additional sense information
 unknown partition table
sd 5:0:0:0: Attached scsi disk sda
usb-storage: device scan complete
sda: Current: sense key: No Sense
    Additional sense: No additional sense information
usb 1-2: reset high speed USB device using ehci_hcd and address 11
sda: Current: sense key: No Sense
    Additional sense: No additional sense information
usb 1-2: reset high speed USB device using ehci_hcd and address 11
usb 1-2: reset high speed USB device using ehci_hcd and address 11
usb 1-2: reset high speed USB device using ehci_hcd and address 11
sda: Current: sense key: No Sense
    Additional sense: No additional sense information


and I am unable to use the device. Do you have any idea what I may be missing? A service that is not running maybe?

Thanks,
Fethi

---

### Post by fethio on 2007-10-13
well as it turns out in pardus linux I mounted another old disk of mine, if anybodys interested without problems. 

The initial disk that was not recognized contained an old linux install (debian kernel 2.0 or 2.2, as far as I can remember). Now maybe its corrupted, and I don't have any other reason why it shouldn't mount??

So the good part is that mu external USB/IDE bridge is working under linux, the bad part is I am unable to access my old files...

Fethi

---

