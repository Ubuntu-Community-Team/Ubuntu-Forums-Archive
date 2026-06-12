---
title: "problems with ehci_hcd"
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by devnulljp on 2006-04-17
I have no end of problems with the ehci_hcd module - with this module loaded none of my usb devices work. A quick sudo rmmod ehci_hcd or sudo modprobe -r ehci_hcd and the problems are solved.

How can I disable this module permanently? I don't think a kernel recompile should be necessary as it's loaded up as a module.

Thanks

---

### Post by devnulljp on 2006-12-06
Answering my own question again:
```
sudo vi /etc/modprobe.d/blacklist
```
add a line
```
blacklist ehci_hcd
```

---

