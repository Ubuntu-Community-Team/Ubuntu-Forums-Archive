---
title: "Asus PCE-AC68"
date: 2017-02-19
forum: Hardware
---

### Post by wgmvanhees on 2017-02-19
Anyone have any expierence with the Asus PCE-AC68? It is a PCIE card with the BCM4360 chipset and I'm planning to use it to add router functionality to my Linux box. I need to know whether it 1) works reliably and 2) the driver can reach speeds at or near the level of the Windows driver. I found info it should be supported but hope someone can confirm.

---

### Post by wildmanne39 on 2017-02-19
Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1574196](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1574196)
It does work but not in the 5GHZ range at the moment.

---

### Post by wgmvanhees on 2017-02-19
It seems channel 104 is the problem but channel 40 works fine, but information like this was indeed what I was looking for. Seems like this chip is indeed not a good candidate. I'll search further. Off course, I'm open to suggestions to any PCIE cards with wireless AC that obtain speeds of at least 850Mbps.

---

### Post by wildmanne39 on 2017-02-19
I believe this is the card you want to buy:
[http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth.html](http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth.html)
The best wireless person on the forum uses one and helps a lot of people use this card to its best capabilities.

---

