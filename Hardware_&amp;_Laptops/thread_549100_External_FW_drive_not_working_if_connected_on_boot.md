---
title: "External FW drive not working if connected on boot."
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by affected on 2007-09-12
Hi,
I'm running Feisty with a 2.6.20-16-lowlatency kernel (from ubuntu studio), and have an IEEE1394 enclosure connected to a PCMCIA adapter (reported as "NEC Corporation IEEE 1394 Host Controller (rev 01)" by lspci). My problem is that if I have the external drive connected when I boot the computer up, it doesn't seem to get recognized, and even if I unplug it and plug it back in, it doesn't work. After the plug in-out routine, dmesg reports the following:

[  264.768000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004c0200000da7]
[  274.669000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[  274.929000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0005e3000000122d]
[  274.929000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[  275.091000] scsi3 : SBP-2 IEEE-1394
[  296.092000] ieee1394: sbp2: Error logging into SBP-2 device - timed out
[  296.092000] sbp2: probe of 0005e3000000122d-0 failed with error -16
[  296.092000] ieee1394: Failed to create unit 0005e3000000122d-0

The drive doesn't show up in /dev/ at all. If, however, I have the drive disconnected on boot, and only plug it in after the OS has booted up, it works fine. So I can work around the problem, but it's annoying. Any ideas?

---

