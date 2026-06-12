---
title: "how to ignore a printer? i need to talk directly with it via libusb"
date: 2009-12-16
forum: Hardware
---

### Post by hybris0 on 2009-12-16
Hi,
i have an usb printer and i neeed to drive it directly using libusb.

My problem is that the printer does not appear in the usb device list (lsusb), so i can't open it.

I already blacklisted the usblp module (on a debian system this was sufficient) but the printer wizard keeps popping up and apparently it takes "ownership" of the printer that never appears as an available usb device.

How to tell the print wizard to mind his own business when it sees an usb printer with a particular VID and PID?

thanks

---

