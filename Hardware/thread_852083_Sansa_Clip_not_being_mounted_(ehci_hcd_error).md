---
title: "Sansa Clip not being mounted (ehci_hcd error?)"
date: 2008-07-07
forum: Hardware
---

### Post by simonz on 2008-07-07
My Sansa Clip works great under Windows Vista.  On Ubuntu it doesn't always get mounted.  When I plug it in I get the following output from 'dmesg'

[  114.765095] usb 6-3: new high speed USB device using ehci_hcd and address 5
[  114.848295] ehci_hcd 0000:00:1a.7: port 3 reset error -110
[  114.848326] hub 6-0:1.0: hub_port_status failed (err = -32)

The temporary workaround "sudo modprobe -r ehci_hcd" seems to fix the problem, but doesn't survive a reboot.

Has anyone found a way to fix this so that it will survive a reboot and not downgrade to USB 1.0?

simonz

---

### Post by ubuntoogood on 2008-07-09
command "sudo modprobe -r ehci_hc" not reconginzed for me, any thoughts?  none of the other fixes work.

although i did a reboot and now i'm seeing "FATAL: Module ehci_hc not found."

---

### Post by ninotsmindelivar on 2009-04-02
Not to pull thread necromancy, but i'm having the same issue on as late as 9.04 with my fuze. Wondering where ehci-hcd is disappearing to... Out of curiosity, despite the module not appearing, are you getting 2.0 speeds for your non-sansa usb devices?

---

### Post by Vostrocity on 2009-04-19
Same problem with my e260 on 8.10...

---

