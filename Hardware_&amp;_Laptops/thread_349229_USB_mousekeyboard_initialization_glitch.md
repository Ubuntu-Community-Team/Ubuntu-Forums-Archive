---
title: "USB mouse/keyboard initialization glitch"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by muguwmp67 on 2007-01-29
Starting yesterday, after my system boots into the login screen, my mouse and keyboard are not initialized (which makes the machine look like its hung).  After about 90 seconds, the keyboard and mouse begin working.

I've checked the system log and there are a series of errors that say:

[17179615.948000] usb 2-3: device descriptor read/64, error -110
[17179616.164000] usb 2-3: new high speed USB device using ehci_hcd and address 4
[17179621.184000] usb 2-3: device descriptor read/8, error -110
[17179626.304000] usb 2-3: device descriptor read/8, error -110
[17179626.520000] usb 2-3: new high speed USB device using ehci_hcd and address 5
[17179631.540000] usb 2-3: device descriptor read/8, error -110
[17179636.660000] usb 2-3: device descriptor read/8, error -110

This was working fine prior to yesterday.  Does anyone have any guidance as to where I should start troubleshooting?  If I boot into windows, or use the live cd, the mouse and keyboard work correctly in both environments.

---

