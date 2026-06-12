---
title: "Epson Stylus SX105 Printer not working after 20.04 install"
date: 2020-09-06
forum: Hardware
---

### Post by maglin2 on 2020-09-06
The above printer worked in 16.04, but despite being detected and installed OK is unresponsive since fresh install of 20.04. It says printing completed, but nothing actually happens.

Any help in getting it going would be much appreciated.

Thanks

---

### Post by maglin2 on 2020-09-06
Should have mentioned that I've tried installing printer-driver-escpr (which worked in 16.04) and also downgrading 20.04 installed printer-driver-escpr to the version present in 16.04.

---

### Post by maglin2 on 2020-09-07
To finish the monologue (for the benefit of anyone else trying to keep one of these ancient printers going in 20.04) you need 

CUPS+Gutenprint v5.3.3 (color)

Admin is best done from localhost  in browser (couldn't get printer admin under settings to do it).

It wasn't presented as an option until I installed printer-driver-gutenprint.

---

### Post by alyana on 2020-10-23
Thank you so much you made my day =d>. I was helping a friend and we ran just exactly into this problem!

---

### Post by slickymaster on 2020-10-23
*Thread moved to **Hardware**.*

---

