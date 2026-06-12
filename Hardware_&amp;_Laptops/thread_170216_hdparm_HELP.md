---
title: "hdparm HELP"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by lindos on 2006-05-04
how to increase the disk read speed using hdparm?
Drive details:
Samsung IDE
dma = on
multicount = 16
with these setting the disk read speed is 28Mbps

---

### Post by reech on 2006-05-04
Hmm - i cant seem to get faster than udma2 with mine ? 

Should be hdparm -Xn (n=udma mode1-6) to set the udma speed for the HD assuming the bus has dma enabled.

---

### Post by hajk on 2006-05-04
What kind of HD? IDE? SATA? What's the device name for the disk?

---

