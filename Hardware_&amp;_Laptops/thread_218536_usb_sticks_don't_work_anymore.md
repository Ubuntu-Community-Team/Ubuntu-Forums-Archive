---
title: "usb sticks don't work anymore"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by rattusdatorum on 2006-07-18
I tried 3 different usb sticks, but none is working, and before some updates (don't ask my which ones) everything was fine.
now I have the following problems:

-lsusb doesn't show the usbstick and takes about 1-2 minutes
-I can't find the device for the usbstick
-dmesg prints the following:

```
[17180248.680000] usb 1-4: new high speed USB device using ehci_hcd and address 3
[17180249.680000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17180260.224000] usb 1-4: device not accepting address 3, error -110
[17180260.336000] usb 1-4: new high speed USB device using ehci_hcd and address 4
[17180271.880000] usb 1-4: device not accepting address 4, error -110
[17180271.992000] usb 1-4: new high speed USB device using ehci_hcd and address 5
[17180282.416000] usb 1-4: device not accepting address 5, error -110
[17180282.952000] usb 1-4: new high speed USB device using ehci_hcd and address 7

```

please help me, I am little bit desperate "over here".

---

### Post by rattusdatorum on 2006-07-19
:confused: everyone on vacation or what is the problem?

---

### Post by rattusdatorum on 2006-07-20
:confused: don't tell no one knows an answer or at least hint about that!!!!!

btw. my usb-mouse and usb-camera work, so I don't have a defect hardware and it worked without problems before!!!

---

### Post by rattusdatorum on 2006-07-20
I booted with an older kernel and it works now, BUT the following
questions remain:

1) why did it happen?
2) what can I do about it?
3) will the problem be solved with the next kernel?
4) how can I support the "debuggers" out there?

---

