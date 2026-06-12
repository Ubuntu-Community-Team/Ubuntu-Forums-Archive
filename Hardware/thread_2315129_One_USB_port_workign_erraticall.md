---
title: "One USB port workign erraticall"
date: 2016-02-26
forum: Hardware
---

### Post by Graeme_Pietersz on 2016-02-26
I have one usb port that does not work properly.

Devices plugged  into it look exactly the same in lsusb as they do plugged into another  port, but they do not work. I have tried two mice, a keboard, USB storage and a  mobile dongle. The usual error is:

```
 xhci_hcd 0000:00:14.0: Not enough bandwidth. Proposed: 4294967276, Max: 1607
[373552.353989] xhci_hcd 0000:00:14.0: Not enough bandwidth
[373552.353994] usb 1-2: can't set config #1, error -12
```

Not enough bandwidth for a keyboard?

All the devices work on my other USB ports. One worked once on this port but then stopped.

I have found out that this can be due to driver issues, but then how do the other four USB ports work? If the hardware is dead, how is the device correctly recognised?

---

