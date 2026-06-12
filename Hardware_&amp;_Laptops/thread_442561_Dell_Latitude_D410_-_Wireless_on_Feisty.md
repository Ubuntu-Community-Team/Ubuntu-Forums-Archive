---
title: "Dell Latitude D410 - Wireless on Feisty"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by raylu on 2007-05-13
In edgy, my wireless card worked fine. The KNetworkManager doesn't work with my wireless card; what can I do?

---

### Post by madmetal on 2007-05-15
> **raylu said:**
> In edgy, my wireless card worked fine. The KNetworkManager doesn't work with my wireless card; what can I do?

which wireless card do you have?
check  System >> Administration >> Restricted Drivers Manager for wifi drivers..


UAResolved.

---

### Post by raylu on 2007-05-17
Sorry, I'm in Kubuntu actually...

According to [http://www.dell.com/content/products/productdetails.aspx/latit_d420?c=us&l=en&s=bsd&cs=04#tn4](http://www.dell.com/content/products/productdetails.aspx/latit_d420?c=us&l=en&s=bsd&cs=04#tn4)
Intel® 3945 WiFi 802.11a/g, Dell Wireless 1390 802.11g, Dell Wireless 1490 802.11a/g Dual-Band Mini-Cards, Dell Wireless 5700 Mobile Broadband CDMA EVDO (Verizon Wireless US)

---

### Post by chili555 on 2007-05-18
It probably doesn't have all four of these simultaneously, does it?

Let's narrow things down. Please open a terminal and do:```
sudo lshw -C network
``` and post the result here. Thanks.

---

