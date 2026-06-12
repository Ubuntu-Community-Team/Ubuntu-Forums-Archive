---
title: "USB hard disk not working"
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by sudharshanan on 2006-10-08
Hi,
I am relatively new to linux. I have dapper on my system with XP. My usb hard drive is not working in linux. I did a serach online and this problem seems to be quite common.THis is what the dmesg output looks like:



[17184263.052000] usb-storage: device found at 4
[17184263.052000] usb-storage: waiting for device to settle before scanning
[17184268.276000]   Vendor: HITACHI_  Model: DK23FA-80         Rev: 00M3
[17184268.276000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17184268.280000] SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
[17184268.280000] sda: assuming drive cache: write through
[17184268.280000] SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
[17184268.280000] sda: assuming drive cache: write through
[17184268.280000]  sda: sda1
[17184268.704000] sd 3:0:0:0: Attached scsi disk sda
[17184268.704000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17184268.712000] usb-storage: device scan complete
[17184299.472000] usb 4-4: reset high speed USB device using ehci_hcd and address 4
[17184302.584000] usb 4-4: device descriptor read/64, error -110


I tried disabling the ehci_hcd module. If i do that, the disk is stillnot working. I keep getting a uhci_hcd reset error which foes like this:

[17183342.072000] usb-storage: device found at 2
[17183342.072000] usb-storage: waiting for device to settle before scanning
[17183348.696000]   Vendor: HITACHI_  Model: DK23FA-80         Rev: 00M3
[17183348.696000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183348.700000] SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
[17183348.700000] sda: assuming drive cache: write through
[17183348.704000] SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
[17183348.704000] sda: assuming drive cache: write through
[17183348.704000]  sda: sda1
[17183348.868000] sd 1:0:0:0: Attached scsi disk sda
[17183348.868000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17183348.872000] usb-storage: device scan complete
[17183379.248000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17183410.764000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17183442.256000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17183473.752000] usb 2-2: reset full speed USB device using uhci_hcd and address 2


If someone could help me on this it wud be gr8. I have very little space for unix on my machine and i need this drive very badly.

cheers,
sudhar

---

### Post by dannytherocker on 2006-10-09
> **sudharshanan said:**
> Hi,
I am relatively new to linux. I have dapper on my system with XP. My usb hard drive is not working in linux. I did a serach online and this problem seems to be quite common.THis is what the dmesg output looks like:



[17184263.052000] usb-storage: device found at 4
[17184263.052000] usb-storage: waiting for device to settle before scanning
[17184268.276000]   Vendor: HITACHI_  Model: DK23FA-80         Rev: 00M3
[17184268.276000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17184268.280000] SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
[17184268.280000] sda: assuming drive cache: write through
[17184268.280000] SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
[17184268.280000] sda: assuming drive cache: write through
[17184268.280000]  sda: sda1
[17184268.704000] sd 3:0:0:0: Attached scsi disk sda
[17184268.704000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17184268.712000] usb-storage: device scan complete
[17184299.472000] usb 4-4: reset high speed USB device using ehci_hcd and address 4
[17184302.584000] usb 4-4: device descriptor read/64, error -110


I tried disabling the ehci_hcd module. If i do that, the disk is stillnot working. I keep getting a uhci_hcd reset error which foes like this:

[17183342.072000] usb-storage: device found at 2
[17183342.072000] usb-storage: waiting for device to settle before scanning
[17183348.696000]   Vendor: HITACHI_  Model: DK23FA-80         Rev: 00M3
[17183348.696000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183348.700000] SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
[17183348.700000] sda: assuming drive cache: write through
[17183348.704000] SCSI device sda: 156301489 512-byte hdwr sectors (80026 MB)
[17183348.704000] sda: assuming drive cache: write through
[17183348.704000]  sda: sda1
[17183348.868000] sd 1:0:0:0: Attached scsi disk sda
[17183348.868000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17183348.872000] usb-storage: device scan complete
[17183379.248000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17183410.764000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17183442.256000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[17183473.752000] usb 2-2: reset full speed USB device using uhci_hcd and address 2


If someone could help me on this it wud be gr8. I have very little space for unix on my machine and i need this drive very badly.

cheers,
sudhar

This is the same problem I have with my laptop. Try downgrade your kernel: i.e. use 2.6.15-23....should work
I also tried Edgy Eft beta, and works perfectly!!!!

---

### Post by caprenter on 2006-10-22
I think I've had a similar problem, but I managed to get my flash disk (and an external hard drive) working by removing ehic_hcd, but not straight away.

To do it, 
I had to reboot the computer (with the flash disk UNplugged)
Run:
sudo modprobe -r ehic_hcd 
(in a terminal and enter my password)

Then I could plug in the flash disk, and it works fine, via uhic_hcd

If I had plugged in the flash disk first, it just didn't work. It killed all USB functionality and I would need to reboot things that did work before to work again (i.e. USB printer)

I'm now wondering why? What's wrong with ehic_hcd (or is it my flash disk and external hard drive?) 

Any use?

---

### Post by aslakjo on 2006-11-07
This worked like magic!

tanks!

---

### Post by caprenter on 2006-11-07
I've done a bit of investigating since and think that what the 'fix' of removing ehic_hcd does is revert you back to USB 1 functionality. (controlled by uhic_hcd)

So your devices will work, but only at the slower USB 1 speeds. For me this isn't really a problem, but I would like to know how to get USB 2 working.

---

