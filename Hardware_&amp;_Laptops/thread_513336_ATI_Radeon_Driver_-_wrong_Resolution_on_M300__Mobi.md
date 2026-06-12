---
title: "ATI Radeon Driver - wrong Resolution on M300 / Mobility X300"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by MarkSchmidt on 2007-07-30
Hi there!

I have a Dell Inspiron 6000 and am running Feisty. With my Mobility X300, the fglrx works just finde - of course without Desktop Effects. So I tried to use the radeon driver from this guide: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) . It installed well, and Desktop Effects worked great. Just my resolution got stuck at 1280 instead of 1680*1050 for my TFT. Yes, I had the correct resolution in xorg.conf etc - so I had to switch back to fglrx. Any mroe ideas how I could use the radeon driver? Is my chipset supported by it?

Thanks a lot!

---

### Post by likpok on 2007-07-30
You could try dpkg-recongfigure xserver-xorg (running as root). That will let you select various things like driver and resolution for X.

---

### Post by MarkSchmidt on 2007-07-31
Thanks for your response. I reconfigured the xorg.conf various times, and the 1680x1050 was the only resolution in it. So now, this is not the problem I am afraid :(

---

