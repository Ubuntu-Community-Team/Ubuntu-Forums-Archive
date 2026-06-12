---
title: "Disabling EHCI?"
date: 2010-09-22
forum: Hardware
---

### Post by nvidiasucks on 2010-09-22
Hey. I was wondering if it was possible to disable the EHCI nvidia usb controller while keeping the OHCI active?

```
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
```

From lspci

Also I've attempted to blacklist ehci_hcd and it done nothing. I can't disable USB 2.0 support on BIOS either :(

Any ideas?

---

