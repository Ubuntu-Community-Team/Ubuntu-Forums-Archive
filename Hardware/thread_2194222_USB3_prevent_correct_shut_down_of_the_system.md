---
title: "USB3 prevent correct shut down of the system"
date: 2013-12-17
forum: Hardware
---

### Post by rigobot on 2013-12-17
Hello,

My system, since I've upgraded to the kernel 3.12, when is shut down from Ubuntu 13.10 it turns on after few seconds. The problem does not exist if I turn off the USB3 support from the (UEFI) bios.
I tried to add all the various option in the GRUB command line to enable/disable ACPI, disable IRQ and so on with no luck (I don't think that ACPI is the problem here).
Probably it's worth to know that if I run 
```
lsmod |grep hc
```
I get as result:
```
ahci                   30063  4 
libahci                32118  1 ahci
```
whether or not I have the USB3 support enabled. Should not be there a XHCI module?
If I run:
```
sudo modprobe xhci
```
nothing happens, no errors, no module loaded.

Thank you for any help!

---

### Post by varunendra on 2013-12-20
Modules xhci, uhci and ohci etc. are built in the kernel, they are not separate modules that can be modprobe'd with modeprobe command.

However, I'm not sure how to disable it. As a wild guess, you may try adding (without quotes) "xhci.enable=0" or "xhci_hcd.enable=0" to the kernel boot line, but be warned, this is a pure guess with almost a guarantee to fail. :|

---

