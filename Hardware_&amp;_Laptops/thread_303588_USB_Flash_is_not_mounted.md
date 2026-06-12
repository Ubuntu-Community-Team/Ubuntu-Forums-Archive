---
title: "USB Flash is not mounted"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by mesh2005 on 2006-11-20
I installed Ubuntu 6.0. 6 64-bit on a Compaq Presario V6000 notebook. I connected the wireless mouse to it. Each time I try to connect the flash disk, I cannot see it mounted at all especially if the mouse is connected. I tried to disconnect the mouse, hence the usb disk is mounted as /dev/sdb1.
I tried to mount /dev/sdb1 manually while the flash is connected but I couldn't. Please advise.
Thank you

---

### Post by Jussi Kukkonen on 2006-11-20
Are you sure the laptop gives enough power for both devices? If you are using a single usb port and a unpowered usb hub, that could be the problem.

You can try this:
-- when the mouse is connected, run:
```
tail -f -n 0 /var/log/messages
```
-- then connect the disk, and see what you get as output
Paste the output here if you can't figure out the problem.

---

### Post by mesh2005 on 2006-11-23
Thank you for your reply. I followed the steps you mentioned above and here are the log messages:
Nov 23 23:46:42 amir-laptop kernel: [  765.966087] usb 1-1: new high speed USB device using ehci_hcd and address 3
Nov 23 23:46:43 amir-laptop kernel: [  766.465976] ehci_hcd 0000:00:0b.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
Nov 23 23:46:54 amir-laptop kernel: [  771.782681] usb 1-1: new high speed USB device using ehci_hcd and address 4
Nov 23 23:47:05 amir-laptop kernel: [  777.600772] usb 1-1: new high speed USB device using ehci_hcd and address 5
Nov 23 23:47:16 amir-laptop kernel: [  782.861459] usb 1-1: new high speed USB device using ehci_hcd and address 6

I hope you can solve it, thank you

---

