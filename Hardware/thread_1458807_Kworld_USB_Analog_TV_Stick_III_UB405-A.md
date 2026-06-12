---
title: "Kworld USB Analog TV Stick III UB405-A"
date: 2010-04-20
forum: Hardware
---

### Post by dqueijo on 2010-04-20
I've bought a USB Stick that allows you to see TV by Antenna or direct cable, but it seems that it doesn't have support for Ubuntu Linux.

The product name is: **Kworld USB Analog TV Stick III UB405-A**

Has anyone faced this issue before? What should I do? :confused:

Thanks!

---

### Post by swlazlowski on 2010-04-30
was fighting wiht UB450-T - some thoughts 
One chip appear to be OMNITUNE TUA 9001 [http://www.infineon.com/cms/en/product/promopages/COM/TUA_9001/index.html](http://www.infineon.com/cms/en/product/promopages/COM/TUA_9001/index.html) the other is Realtek RTL2832U DVB-T 
Several howtos following the same strategy (as the one here -http://www.ubuntu-es.org/?q=node/123739) were not successful
Following the how-to available here [http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/readme.lv5tdlx.txt](http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/readme.lv5tdlx.txt) I managed to get it recognised. It seems to be working as scan and w_scan pick up some limited reception, but need to get a proper antena to check it.

---

