---
title: "Hardware USB Card"
date: 2009-02-15
forum: Hardware
---

### Post by RikardSvenningsen on 2009-02-15
I got a HP Vectra VL
CPU Pentium III 650 E
Bios HZ.01.10US
My problem is that When I use an External Harddrive and the speed is high for time like more than 1 minute. I loose the connection to my external drive.
It still looks like connected when I run mount, if I run ls in the mounted folder I get an IO error.
If I run sfdisk -l I can't see the disk.
I have attached dmesg log from the error report.
 
I equipped my pc with a Sandberg USB 2.0 Boost card to PCI (3 + 1 porte)
From spec.:
• 3 USB external ports and 1 USB internal port
(Type A)
• Supports USB 2.0 and 1.1
• EHCI based 480 MBit/s USB 2.0 Hi-Speed
compliant
• OHCI based 12 MBit/s USB 1.1 compliant
• Supports up to 127 devices
• Supports devices hot swap and wake-up
• Supports PCI-Bus Power Management Interface
Specifications release 2.1
• 32-bit 33MHz host interface compliant to PCI
specifications release 2.2
• Power 3.3V / 5V

---

### Post by RikardSvenningsen on 2009-02-22
It seems to the cable, got some inspiration by searches for "reset high speed USB device"

---

