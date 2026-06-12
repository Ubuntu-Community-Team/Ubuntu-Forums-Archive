---
title: "USB dropped and won't recognizes in any computers"
date: 2012-01-02
forum: Hardware
---

### Post by 2ltk on 2012-01-02
My friend dropped her USB storage stick onto tiles and it won't recognizes on her computer. She gave the stick to me, and it wouldn't mount on Ubuntu 11.10
Is there a way I can force USB storage to mount it?
I need help asap.
Here is the error from the log
new full speed USB device number 54 using uhci_hcd
[15656.092045] usb 5-2: device descriptor read/64, error -71
[15656.316038] usb 5-2: device descriptor read/64, error -71
[15656.532045] usb 5-2: new full speed USB device number 55 using uhci_hcd
[15656.652045] usb 5-2: device descriptor read/64, error -71
[15656.876043] usb 5-2: device descriptor read/64, error -71
[15657.092044] usb 5-2: new full speed USB device number 56 using uhci_hcd
[15657.500022] usb 5-2: device not accepting address 56, error -71
[15657.612041] usb 5-2: new full speed USB device number 57 using uhci_hcd
[15658.020031] usb 5-2: device not accepting address 57, error -71
[15658.020053] hub 5-0:1.0: unable to enumerate USB device on port 2

---

### Post by bluexrider on 2012-01-02
> **2ltk said:**
> My friend dropped her USB storage stick onto tiles and it won't recognizes on her computer. She gave the stick to me, and it wouldn't mount on Ubuntu 11.10
Is there a way I can force USB storage to mount it?
I need help asap.
Here is the error from the log
new full speed USB device number 54 using uhci_hcd
[15656.092045] usb 5-2: device descriptor read/64, error -71
[15656.316038] usb 5-2: device descriptor read/64, error -71
[15656.532045] usb 5-2: new full speed USB device number 55 using uhci_hcd
[15656.652045] usb 5-2: device descriptor read/64, error -71
[15656.876043] usb 5-2: device descriptor read/64, error -71
[15657.092044] usb 5-2: new full speed USB device number 56 using uhci_hcd
[15657.500022] usb 5-2: device not accepting address 56, error -71
[15657.612041] usb 5-2: new full speed USB device number 57 using uhci_hcd
[15658.020031] usb 5-2: device not accepting address 57, error -71
[15658.020053] hub 5-0:1.0: unable to enumerate USB device on port 2
If there were anything important on it......say goodbye.

might try this [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

