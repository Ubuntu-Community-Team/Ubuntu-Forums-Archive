---
title: "Does not detect wireless networks.  Help"
date: 2011-10-03
forum: Hardware
---

### Post by iNeeed on 2011-10-03
Hello Ubuntu's

I recently installed 11.04 and now my wireless is not detecting any networks.  It was working fine in my previous version of ubuntu.  I am using a Dell Inspiron 6400 Laptop 
I imagine it is something with my wirelss driver. It says it is activated but I can not see any networks.  
Any help greatly appreciated! 

It says I have Broadcom STA Wireless driver and it is activated.
This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

---

### Post by diasf on 2011-10-03
sudo iwlist eth1 scanning

(assuming eth1 is your wifi interface)

---

