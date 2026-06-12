---
title: "Lost USB receiver when I connect it to downstream."
date: 2009-07-12
forum: Hardware
---

### Post by jcadam on 2009-07-12
Hello. 

I just lost my bluetooth mouse receiver when I connect it to USB downstream. Attached to upstream, directly to the PC rather then connect it via a usb hub, it works fine. And I have done some investigate on this....

When I attached the receiver to USB upstream, the outputs of lsusb would be:
```
Bus 007 Device 002: ID 0aae:001f NEC infrontia Corp. (Nitsuko) 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 007: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 005 Device 006: ID 04fe:0007 PFU, Ltd 
Bus 005 Device 005: ID 04fe:0008 PFU, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

When connect it to downstream via a usb hub, lsusb outputs goes here:
```

Bus 007 Device 002: ID 0aae:001f NEC infrontia Corp. (Nitsuko) 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 006: ID 04fe:0007 PFU, Ltd 
Bus 005 Device 005: ID 04fe:0008 PFU, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

It seems the receiver simply not be recognized on downstream. Is there any suggestion on this? Thanks for you help!

---

