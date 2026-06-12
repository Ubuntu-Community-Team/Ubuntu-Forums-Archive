---
title: "Acer/Benq 310u scanner--won't work"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by woodsworth on 2006-10-16
OK, I put the appropriate firmware (u34v110.bin) in /etc/sane.d , edited /etc/sane.d/snapscan.conf appropriately, and it still doesn't work.

> woods@2[sane.d]$ scanimage -L
device `snapscan:libusb:002:002' is a Acer FlatbedScanner_5 flatbed scanner


Everything should be good here, but it isn't. When I click "preview" on xsane or Kooka, it just returns a black, distorted image, and does not, needless to say, scan properly.

Is there anything else I need to do?

---

