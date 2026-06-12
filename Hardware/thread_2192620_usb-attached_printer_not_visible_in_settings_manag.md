---
title: "usb-attached printer not visible in settings manager"
date: 2013-12-08
forum: Hardware
---

### Post by rwohlhueter on 2013-12-08
[Running Unbuntu 13.10 on AMD64 machine]

After upgrading from Ubuntu 12.04 to 13.10 I have lost the ability to configure one of my usb-connected printers (which worked fine under 12.04 with the appropriate cups definition.)

Both printers show up in output from `lsusb`:
...
Bus 003 Device 003: ID 04a9:1093 Canon, Inc. PIXMA iP4000
Bus 003 Device 002: ID 04a9:307c Canon, Inc. CP-200
...

The PIXMA iP4000 installs and works fine.  But when I use settings manager | printers | "+" to add the CP-200, it isn't reported among the available, locally-attached printers. That is, in the "Select Device" window, I'm presented only with:  "Canon iP4000 (200DE2)", "Generic CUPS PDF", "Serial Port #1", and "Enter URI".

Why is the second usb printer not reported?  How can I work around the omission, and manually set up a printer queue for the CP-200?

Thanks for any tips,
Bob W.

---

