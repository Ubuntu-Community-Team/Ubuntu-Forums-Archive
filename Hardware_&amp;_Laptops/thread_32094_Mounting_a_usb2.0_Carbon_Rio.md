---
title: "Mounting a usb2.0 Carbon Rio"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by tread on 2005-05-06
I plug in my Rio Carbon in a usb port, and this is what I get:

```
May  6 02:12:59 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 3
May  6 02:13:00 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 4
May  6 02:13:00 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 5
May  6 02:13:11 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 4
May  6 02:13:12 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 6
May  6 02:13:12 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 7
May  6 02:13:24 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 5
May  6 02:13:25 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 8
May  6 02:13:25 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 9
May  6 02:13:36 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 6
May  6 02:13:37 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 10
May  6 02:13:38 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 11
May  6 02:13:49 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 7
May  6 02:13:50 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 12
May  6 02:13:50 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 13
May  6 02:14:02 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 9
May  6 02:14:02 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 14
May  6 02:14:03 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 15
May  6 02:14:14 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 10
May  6 02:14:15 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 16
May  6 02:14:15 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 17
May  6 02:14:26 localhost kernel: usb 4-3: new high speed USB device using ehci_hcd and address 11

```

This keeps increasing .. its hit address 57 at this point. Also, the player keeps switching on and off. Any idea what's happening here?

Thanks.

---

### Post by kanem on 2005-08-12
[QUOTE=tread]This keeps increasing .. its hit address 57 at this point. Also, the player keeps switching on and off. Any idea what's happening here?

Thanks.[/QUOTE]Well, in case you haven't fixed it by now....

Does this happen with other USB drives? If not I'd say it's something wrong with the Carbon. Mine mounts fine. Gave me some trouble with writing to it at first but after I reformatted it worked fine.

---

