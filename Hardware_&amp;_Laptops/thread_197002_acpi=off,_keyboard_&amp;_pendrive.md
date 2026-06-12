---
title: "acpi=off, keyboard &amp; pendrive"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by biker3 on 2006-06-15
Hello, I use a Packard Bell iGo6208. I can use the keyboard only if I boot with parameter: "acpi=off", because if I don't use this parameter, it seems locked and I have to use Ubuntu only with mouse.
But the pendrive isn't detected. When I insert it obtain:

[ 922.085327] usb 1-2: new full speed USB device using ohci_hcd and address 2
[ 923.083969] ohci_hcd 0000:00:02.0: Unlink after no-IRQ? Controller is probably using the wrong IRQ.

And I try to see the new dev doing "ls /dev/ without pendrive and with it, but I can't see none new.

Some solution? Thanks

---

### Post by Greg2 on 2006-06-15
[QUOTE=biker3]I use a Packard Bell iGo6208. I can use the keyboard only if I boot with parameter: "acpi=off"[/QUOTE]
I’m not familiar with your laptop model, but I would suggest that you remove the acpi=off parameter and try pci=routeirq with the Dapper release kernel.

---

### Post by biker3 on 2006-06-15
Hi, I try your grub's parameter but the keyboard seems locked while the system starting and when the desktop finish to start. I did "apt-get upgrade" and I installed kernel 2.6.15-25-686 and now USB gooooooooo:D 

Thanks

---

