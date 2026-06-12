---
title: "USB Memory Stick in 10.4 not mounting"
date: 2010-07-02
forum: Hardware
---

### Post by kiptinui on 2010-07-02
Hi, 

I recently upgraded to 10.4 only to discover that none of my usb memory keys will mount. When I plug one in the dmesg output gives this and nothing more:

```
[13729.484038] usb 1-6: new high speed USB device using ehci_hcd and address 12
[13729.617924] usb 1-6: configuration #1 chosen from 1 choice
```

The device is also not available to manually mount in /dev

Sometimes, rather randomly, a device will mount properly but most of the time it fails. Anyone out there experiencing this or have a solution?

Also: I have discovered that if I reboot with a memory key inserted then it will mount and show on the desktop.

Thanks!

---

