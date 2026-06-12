---
title: "USB Errors"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by blindspy on 2006-07-27
My USB mouse wont work. My usb printer works. My usb ipod does not work. My camera (usb) doesnt work. There are the errors from dmesg:
```
[17355160.400000] usb 4-2: new high speed USB device using ehci_hcd and address 63
[17355171.960000] usb 4-2: device not accepting address 63, error -110
[17355172.076000] usb 4-2: new high speed USB device using ehci_hcd and address 64
[17355183.632000] usb 4-2: device not accepting address 64, error -110
[17355183.752000] usb 4-2: new high speed USB device using ehci_hcd and address 65
[17355194.180000] usb 4-2: device not accepting address 65, error -110
[17355194.476000] usb 4-3: new high speed USB device using ehci_hcd and address 67
[17355206.032000] usb 4-3: device not accepting address 67, error -110
[17355206.152000] usb 4-3: new high speed USB device using ehci_hcd and address 68
[17355207.672000] usb 4-2: new high speed USB device using ehci_hcd and address 69
[17355219.224000] usb 4-2: device not accepting address 69, error -110
[17355219.336000] usb 4-2: new high speed USB device using ehci_hcd and address 70

```

Uname output:
```
2.6.15-26-k7 #1 SMP PREEMPT Mon Jul 17 20:36:04 UTC 2006 i686 GNU/Linux
```

Has anyone had any problems like this or know anything else to try? I'm open for suggestions.

---

