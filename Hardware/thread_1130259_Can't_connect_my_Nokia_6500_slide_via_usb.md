---
title: "Can't connect my Nokia 6500 slide via usb"
date: 2009-04-19
forum: Hardware
---

### Post by Dinchamion on 2009-04-19
Hello,

I'm running a 8.10 x86_64, and I can't access my Nokia 6500 slide (well, specifically the memory card in it) when I'm trying to connect it via usb cable.

dmsg | tail gives me:
```
[186445.873614] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[186445.873628] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[186445.890611] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[186445.890622] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[186445.907611] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[186445.907621] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[186445.924621] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[186445.924635] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[186445.941667] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[186445.941686] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
```

lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 019: ID 0421:0023 Nokia Mobile Phones 
Bus 001 Device 005: ID 0458:301c KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 004: ID 04d9:0462 Holtek Semiconductor, Inc. 
Bus 001 Device 003: ID 046d:0a0b Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

It doesn't mount up, doesn't show up in /dev, and google just doesn't seem to give any pointers. I find it wierd since I don't want to use it as a phone, just as a usb stick, which I should be able to do.

---

