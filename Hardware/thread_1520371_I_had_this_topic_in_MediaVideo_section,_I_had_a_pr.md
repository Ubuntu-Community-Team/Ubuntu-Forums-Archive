---
title: "I had this topic in Media/Video section, I had a problem were, on one of my computers"
date: 2010-06-29
forum: Hardware
---

### Post by Kdar on 2010-06-29
I had this topic in Media/Video section, I had a problem were, on one of my computers, a remote receiver would not function correctly. It's light would always stay on after first press on the remove.
[http://ubuntuforums.org/showthread.php?t=1519797](http://ubuntuforums.org/showthread.php?t=1519797)

I unplug and pluged the receiver few times and used dmesg in terminal
```
[22490.424020] usb 4-1: new full speed USB device using uhci_hcd and address 5
[22490.619619] usb 4-1: configuration #1 chosen from 1 choice
[22551.562620] lo: Disabled Privacy Extensions
[22563.208539] usb 4-1: USB disconnect, address 5
[22578.804019] usb 4-1: new full speed USB device using uhci_hcd and address 6
[22579.004128] usb 4-1: configuration #1 chosen from 1 choice
```

Then I tried using modprobe
```
[armen@armen-desktop uhci_hcd]$ modprobe -r uhci_hcd
FATAL: Module uhci_hcd not found.

```

Is there something wrong with driver for my USB ports?

---

### Post by Kdar on 2010-06-30
anyone?

---

### Post by gordintoronto on 2010-06-30
Please identify the hardware you're using, the remote and the receiver.

---

### Post by Kdar on 2010-06-30
the remote is RRC-127, which is similar to GP-IR02BK.

And receiver is: Bus 003 Device 002: ID 1784:0008 TopSeed Technology Corp

---

### Post by Kdar on 2010-07-04
Anyone?

---

