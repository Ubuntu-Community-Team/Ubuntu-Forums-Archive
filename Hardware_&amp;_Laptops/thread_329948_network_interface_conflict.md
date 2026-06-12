---
title: "network interface conflict"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by eggdeng on 2007-01-02
After a fresh install of Edgy, I have got wireless (rt2500usb) working in a haphazard fashion. Basically, the connection fails at shorter and shorter intervals, in which case the card can still see the router (iwlist scan reports the mac address correctly) but ping fails.
 
For a number of reasons, I'm beginning to think that connection attempts are defaulting to the wrong interface, trying to use eth0, which is disabled, instead of wlan0. Any ideas on how I could check / configure this or force connection attempts to use a particular interface.

---

