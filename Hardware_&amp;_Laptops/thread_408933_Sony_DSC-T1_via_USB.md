---
title: "Sony DSC-T1 via USB"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by dday376 on 2007-04-13
I have a Sony DSC-T1 USB camera.  When I connect it to my laptops internal USB1.1 port, it works fine.  However, when I connect it to my external USB card - Adaptec DuoConnect AUA-1422 - the camera blips on, then back off, and I get no connection.

Output from dmesg:

```

[17179836.624000] usb 2-2: new full speed USB device using ohci_hcd and address 2
[17179836.888000] usb 2-2: configuration #1 chosen from 1 choice
[17180630.172000] usb 2-2: USB disconnect, address 2
[17207568.928000] hub 4-0:1.0: over-current change on port 1
[17207569.032000] hub 4-0:1.0: over-current change on port 2
[17207575.228000] hub 4-0:1.0: over-current change on port 1
[17207575.332000] hub 4-0:1.0: over-current change on port 2
[17207579.260000] hub 4-0:1.0: over-current change on port 1
[17207579.364000] hub 4-0:1.0: over-current change on port 2
[17207626.388000] hub 4-0:1.0: over-current change on port 1
[17207626.492000] hub 4-0:1.0: over-current change on port 2
[17207645.028000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[17207645.160000] usb 4-3: configuration #1 chosen from 1 choice
[17207645.292000] hub 4-0:1.0: over-current change on port 1
[17207645.396000] hub 4-0:1.0: over-current change on port 2
[17207645.500000] usb 4-3: USB disconnect, address 3
[17209364.948000] ohci_hcd 0000:00:02.0: wakeup
[17209365.720000] ohci_hcd 0000:00:02.0: wakeup
[17209366.104000] usb 1-2: new full speed USB device using ohci_hcd and address 2
[17209366.312000] usb 1-2: not running at top speed; connect to a high speed hub
[17209366.336000] usb 1-2: configuration #1 chosen from 1 choice
[17209820.940000] usb 1-2: USB disconnect, address 2

```

You can see the last 4 lines show where it connects and disconnects just fine from the built-in USB port, but the speed is almost unbearable for image transfers.  I use the USB card frequently with other devices - Sony Katana, wireless mouse, iPod Video - with no problems.  I've googled for 'over-current', but have only found problem reports, no solutions, and none were related to a USB camera at all.

Any help is appreciated!

---

