---
title: "Print processing very slow with 12.04"
date: 2012-05-18
forum: Hardware
---

### Post by markiangooley on 2012-05-18
I belatedly upgraded my desktop to 11.10 and then soon afterwards to 12.04.  When I send a print job to my USB-connected Brother HL-5250DN , even something as brief as an Ubuntu test page using CUPS, it takes a great deal of time for anything to be printed.  The printer flashes a light indicating it is getting data, but it's as if the data are being generated very slowly indeed.  The system monitor shows little CPU use.

Am I missing something obvious?  Before these upgrades, only a very few (presumably complex) print jobs took very long.

Thanks.

---

### Post by Suncat2000 on 2012-10-21
I am also having USB printing problems since upgrading to 12.04. With 11.10 my printing was working very well to both my HP LaserJet 1320n and my Canon ip4000.

After the upgrade, I have tried to print a test page from a remote client and tried to print a web page locally. The printer acted like it was sending data to the printer, but even leaving the printer running overnight (6+ hours), the document never printed on my ip4000, connected via USB.

Even after cancelling the print job, the printer continued to appear that it was actively printing something, but I had to unplug the power before that finally stopped.

---

### Post by Suncat2000 on 2012-10-21
I got some relief from my USB printing problem with the following hack that was suggested on another bug post.

> In addition, you can try to force uni-directional mode by
```

lpadmin -p <queue> -o usb-unidir-default=true
```

---

