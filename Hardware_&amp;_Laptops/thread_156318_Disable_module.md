---
title: "Disable module"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by colutti on 2006-04-06
I was looking for a way to disable a module but I did not find. I need to disable the acx_pci driver, because always i restart the computer the driver is load. 
I tried to find it in /etc/modules but i cant found a reference to the driver.
I need to use ndiswrapper instead acx_pci, but i cant have both loaded at the same time .. 

Rafael Colucci

---

### Post by ranf on 2006-04-07
Try adding acx_pci to /etc/hotplug/blacklist.

---

### Post by colutti on 2006-04-07
Hi ranf

Thanks a lot .. it works very well.

Rafael Colucci

---

