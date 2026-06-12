---
title: "Help me hide lots of uhci-hcd errors at boot..."
date: 2015-08-21
forum: Hardware
---

### Post by mcoyle on 2015-08-21
Running Ubuntu for me is like restoring an old 57 Chevy. I wanna hear the engine perfectly purring.

Right now, my engine is spitting out a kernel module error I can't seem to track down. The listing below repeats on the screen about 3 times after grub and before Plymouth. A list of the modules shows nothing named uchi so I can't blacklist it.

Any suggestions on how to suppress this? 

Apple MacBook Pro 6.2, Ubuntu 15.04, kernel 3.19.0-26-generic.

Thanks!

```

uhci_hcd: USB Universal Host Controller Interface driver
uhci_hcd 0000:00:1a.0: Found HC with no IRQ. Check BIOS/PCI 0000:00:1a.0 setup!
uhci_hcd 0000:00:1a.0: init 0000:00:1a.0 fail, -19
uhci_hcd 0000:00:1d.0: Found HC with no IRQ. Check BIOS/PCI 0000:00:1d.0 setup!
uhci_hcd 0000:00:1d.0: init 0000:00:1d.0 fail, -19

```

---

### Post by dino99 on 2015-08-22
Looks like an upstream kernel issue : report to beg the missing module for that chipset

note: first you can search on LKML about that chipset to know if there is already some discussions about it

---

