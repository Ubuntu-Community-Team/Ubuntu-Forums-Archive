---
title: "libusb scanner requires root"
date: 2008-12-27
forum: Hardware
---

### Post by jimbolaya on 2008-12-27
I noticed after doing two quick upgrades (from 7.04 to 8.04) that the USB scanners now use libusb as part of the drivers.  I moved from using an Epson with a snapscan backend to an HP 8200 using an avision backend with libusb.

Unfortunately, because libusb is being used there appears to be no scanner device created.  That means that I cannot run saned as a non-root user.  This is bad security.

Is there some better way to run saned than as root for libusb based scanners?

James

---

### Post by cariboo on 2008-12-28
Usually with most scanners, if you add yourself to the scanner group, you don't need to be root to use the scanner. Go to System-->Administration-->Users & Groups and add yourself to the scanner group.

Jim

---

