---
title: "barcode reader - how to setup using udev?"
date: 2011-02-19
forum: Hardware
---

### Post by ar600 on 2011-02-19
I have a Holtek USB barcode reader which works fine when plugged in - Ubuntu 10.04.2. The problem is that the translated characters are merged with keyboard input.

Can anyone tell me how to write a udev rule so that:
1) the usbhid module is used to translate raw data to characters
2) the reader appears as a separate device which can be opened to read the scanned code

So far, I have managed to make the raw device appear in /dev but the translated characters still get merged with keyboard input. I created '/etc/udev/rules.d/10-barcode-reader.rules' containing:

> SUBSYSTEM=="usb", ATTRS{idVendor}=="04d9", ATTRS{idProduct}=="1400", SYMLINK+="barcode-reader"Any ideas?

Thanks
--
  Andy

---

