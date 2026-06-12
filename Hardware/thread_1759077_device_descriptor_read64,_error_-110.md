---
title: "device descriptor read/64, error -110"
date: 2011-05-15
forum: Hardware
---

### Post by gontofe on 2011-05-15
I've found various threads on this problem, and haven't been able to glean a solution from any of them.

When I try to mount my Bookeen Orizon via USB, I get the following errors:

DMESG
```
[ 2425.488054] usb 4-2: new full speed USB device using uhci_hcd and address 13
[ 2435.896056] usb 4-2: device not accepting address 13, error -110
[ 2435.896087] hub 4-0:1.0: unable to enumerate USB device on port 2

```

I can't unload ehci_hcd as it's not a module in 2.6.38-8, I've tried various solutions:

editing /sys/module/usbcore/parameters/old_scheme_first - the changes don't persist after a reboot

unbinding the devices in /sys/bus/pci/drivers/ehci_hcd

adding irqpoll to the boot options

turning my laptop off and unplugging it

I really am getting nowhere!

Is there not a simple solution to turning off ehci_hcd?

All I want to do is mount the drive!

---

