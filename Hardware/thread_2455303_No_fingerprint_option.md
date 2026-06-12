---
title: "No fingerprint option"
date: 2020-12-17
forum: Hardware
---

### Post by kemosahbee on 2020-12-17
According to the [documentation]("https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en"), you should see a fingerprint option in Ubuntu 20.10., but I can't seem to find it anywhere. (see attachment)
Or am I looking at the wrong panel?

I use a Thinkpad  L13, with integrated scanner.

---

### Post by TheFu on 2020-12-24
[https://certification.ubuntu.com/hardware/201910-27400](https://certification.ubuntu.com/hardware/201910-27400) lists the expected hardware. Check that is what your system actually contains.  **lsusb** will list usb device identifiers.
Check that the driver is load.

---

