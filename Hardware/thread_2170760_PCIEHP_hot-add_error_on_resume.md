---
title: "PCIEHP hot-add error on resume"
date: 2013-08-27
forum: Hardware
---

### Post by Da_Panther on 2013-08-27
Hello, 

I have an issue with this error message scrolling on resume... I put my computer to sleep by closing the lid, and when I pop the lid up, I get this error message:

Aug 27 11:43:21 swordfishBook kernel: [ 7739.172107] pciehp 0000:00:1c.5: pcie04: Device 0000:03:00.0 already exists at 0000:03:00, cannot hot-add
Aug 27 11:43:21 swordfishBook kernel: [ 7739.172111] pciehp 0000:00:1c.4: pcie04: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add
Aug 27 11:43:21 swordfishBook kernel: [ 7739.172114] pciehp 0000:00:1c.5: pcie04: Cannot add device at 0000:03:00
Aug 27 11:43:21 swordfishBook kernel: [ 7739.172116] pciehp 0000:00:1c.4: pcie04: Cannot add device at 0000:02:00
Aug 27 11:43:21 swordfishBook kernel: [ 7739.172130] pciehp 0000:00:1c.4: pcie04: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add
Aug 27 11:43:21 swordfishBook kernel: [ 7739.172133] pciehp 0000:00:1c.4: pcie04: Cannot add device at 0000:02:00
Aug 27 11:43:21 swordfishBook kernel: [ 7739.172163] pciehp 0000:00:1c.5: pcie04: Device 0000:03:00.0 already exists at 0000:03:00, cannot hot-add
Aug 27 11:43:21 swordfishBook kernel: [ 7739.172166] pciehp 0000:00:1c.5: pcie04: Cannot add device at 0000:03:00

(I put spaces between the : and p in the lines because .... it gave this :p )
I have saved my entire resume log (from syslog) if anyone is interested in reading it all. 

I have read that there is a kernel patch that is available to correct this situation, by instructing the kernel to not try to re-add hardware that has not been disconnected after sleep. 
I am not so n00b in linux, but I do not know how to apply kernel patches.
Assuming I have the text that goes in the patch, how do I go about patching the kernel?

Thank you!

Marc-Antoine

---

