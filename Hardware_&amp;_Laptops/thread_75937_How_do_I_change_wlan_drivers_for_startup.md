---
title: "How do I change wlan drivers for startup?"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by FaQuid on 2005-10-14
I have a dlink wlancard that doesn't work with the standard driver in ubuntu so I'am using ndiswrapper, works just fine. But I would like ndiswrapper to start at startup and not the default driver. How do I change it?

edit: I just tought of this but I think I put this thread in the wrong section so sry :)

---

### Post by Rogmo on 2005-10-15
Try this at the console:


```
sudo modprobe ndiswrapper

sudo echo ndiswrapper >> /etc/modules
``` 


I'll hope this helps

---

