---
title: "All USB Ports stop working"
date: 2022-06-26
forum: Hardware
---

### Post by a-shaatani on 2022-06-26
Hello

I'm using Zorn OS, which is based on Ubuntu 20.01

i was previously  windows user, 

Anyway, after using the OS, i found that the USB ports not working, i tried to apply some google fixes, and somehow they start working, 

Then, they stopped again and i can't get any sign for them anymore

When using $lsusb, the result is empty, nothing show us up

when dmesg

```
$ dmesg | grep xhci

[    0.898903] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.898916] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[   10.915057] xhci_hcd 0000:00:14.0: can't setup: -110
[   10.915077] xhci_hcd 0000:00:14.0: USB bus 1 deregistered
[   10.915236] xhci_hcd 0000:00:14.0: init 0000:00:14.0 fail, -110
[   10.915246] xhci_hcd: probe of 0000:00:14.0 failed with error -110


```

Any Ideas ?

---

