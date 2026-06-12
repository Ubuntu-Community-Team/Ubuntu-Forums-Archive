---
title: "Check what HDD driver is being used"
date: 2009-02-25
forum: Hardware
---

### Post by b-boy on 2009-02-25
Hi 

How can I see what module is being used for my harddrive

---

### Post by kidders on 2009-02-26
Hi there,

That depends on what layer you're interested in. For example ...

```
$ lspci
...
...
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
...
...

$ ls -l /sys/devices/pci0000\:00/0000\:00\:12.0
...
...
lrwxrwxrwx 1 root root    0 2009-02-05 08:22 driver -> ../../../bus/pci/drivers/ahci
...
...
```By finding its PCI address, you can look up the controller card's "driver" symlink in /sys. Something like **lsmod | grep ahci** would give you a partial list of related drivers.

Alternatively, something like **udevinfo -a -n /dev/sda** would give you some driver information, as it traverses the device chain. You could also take a look through your dmesg logs shortly after rebooting, to get an idea of what drivers are being used, and why they were selected.

I hope that helps.

---

