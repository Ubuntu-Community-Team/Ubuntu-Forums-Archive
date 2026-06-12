---
title: "Canon printer conflict"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by GhentK on 2007-08-17
I have two Canon printers: a stationary iP5200R (network printer) and a mobile iP1700 (USB). I've used the [iP2200 drivers](http://software.canon-europe.com/products/0010231.asp) for the iP1700 and [this HowTo](http://translate.google.com/translate?u=http%3A%2F%2Fwww.linux-club.de%2Fftopic74287.html&langpair=de%7Cen&hl=EN&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools) for the iP5200R. They both work great with their respective drivers.

See, this is where trouble arises. The drivers work fine on their own with their respective printer, but they cannot be installed at the same time, and thus, I cannot use both printers at the same time.

The packages that conflict are cnijfilter-ip4200-2.60-1.i386 (iP5200R) and libcnbj-2.6 (iP1700).

The error given when trying to install libcnbj-2.6 with cnijfliter... installed is: "E: /var/cache/apt/archives/libcnbj-2.6_0-1_i386.deb: trying to overwrite `/usr/lib/bjlib/cifip4200.conf', which is also in package cnijfilter-ip4200".

Does anyone have any ideas about how to fix this problem?

Thanks in advance.

---

