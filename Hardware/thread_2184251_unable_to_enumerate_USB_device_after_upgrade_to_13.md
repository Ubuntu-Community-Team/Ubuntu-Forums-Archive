---
title: "unable to enumerate USB device after upgrade to 13.10"
date: 2013-10-28
forum: Hardware
---

### Post by muppet317 on 2013-10-28
I have recently upgraded to 13.10, however now my laptop no longer recognises my android phone (se xperia ray, running gingerbread). Under 13.04 it used to recognise the device automatically and automount the sd card. Now nothing happens when I connect it.

After I connect the phone lsusb does not recognise the device:
> Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


This is the output from dmesg | grep -i usb when I connect the phone:> 
[  964.040118] usb 2-2: new high-speed USB device number 2 using ehci-pci
[  964.173001] usb 2-2: Dual-Role OTG device on non-HNP port
[  964.173134] usb 2-2: can't set HNP mode: -32
[  964.288072] usb 2-2: new high-speed USB device number 3 using ehci-pci
[  964.421007] usb 2-2: Dual-Role OTG device on non-HNP port
[  964.421129] usb 2-2: can't set HNP mode: -32
[  964.536134] usb 2-2: new high-speed USB device number 4 using ehci-pci
[  964.557128] usb 2-2: Dual-Role OTG device on non-HNP port
[  964.557257] usb 2-2: can't set HNP mode: -32
[  964.672131] usb 2-2: new high-speed USB device number 5 using ehci-pci
[  964.693382] usb 2-2: Dual-Role OTG device on non-HNP port
[  964.693504] usb 2-2: can't set HNP mode: -32
[  964.696081] hub 2-0:1.0: unable to enumerate USB device on port 2
[  964.960113] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[  965.103152] usb 5-2: not running at top speed; connect to a high speed hub
[  965.128153] usb 5-2: Dual-Role OTG device on non-HNP port
[  965.130142] usb 5-2: can't set HNP mode: -32
[  965.240092] usb 5-2: new full-speed USB device number 3 using uhci_hcd
[  965.383145] usb 5-2: not running at top speed; connect to a high speed hub
[  965.408143] usb 5-2: Dual-Role OTG device on non-HNP port
[  965.410147] usb 5-2: can't set HNP mode: -32
[  965.520111] usb 5-2: new full-speed USB device number 4 using uhci_hcd
[  965.552152] usb 5-2: not running at top speed; connect to a high speed hub
[  965.575151] usb 5-2: Dual-Role OTG device on non-HNP port
[  965.577150] usb 5-2: can't set HNP mode: -32
[  965.688099] usb 5-2: new full-speed USB device number 5 using uhci_hcd
[  965.719149] usb 5-2: not running at top speed; connect to a high speed hub
[  965.742147] usb 5-2: Dual-Role OTG device on non-HNP port
[  965.745151] usb 5-2: can't set HNP mode: -32
[  965.746146] hub 5-0:1.0: unable to enumerate USB device on port 2

It shouldn't be the phone itself, as it connects normally to my netbook running xubuntu 13.04 and to my girlfriends windows 7 laptop, and I have tried using different cables / ports on my laptop but with the same result. My laptop does still recognise and automount my usb mp3 player when I connect that. I've also tried both MSC and MTP modes on the phone, which doesn't make any difference either.

I also recently installed AndroidSDK following this [https://help.ubuntu.com/community/AndroidSDK](https://help.ubuntu.com/community/AndroidSDK) but I wouldn't imagine that would have caused this problem.

I found this bug report which appears to be a similar problem - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1047527](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1047527) - but according to the comments the bug was fixed in quantal in 2012.

Any ideas on how I can get my computer to recognise my phone?

---

### Post by muppet317 on 2013-11-05
Sorry, didnt read the bug report properly, this had been fixed in quantal in 2012, but re-emerged in more recent kernel versions. Fix is committed for next version of the kernel, so hopefully won't have to wait too long for this to be resolved.

---

### Post by muppet317 on 2013-11-08
This has been fixed on the update to kernel 3.11.0-13-generic, marking as solved.

---

