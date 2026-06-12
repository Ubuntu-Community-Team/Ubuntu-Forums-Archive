---
title: "USB Not Hot Swapping"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by monestri on 2007-11-01
7.04 configured my system so usb devices worked when I plugged them in when the OS was running. After upgrading to 7.10 I find that my mouse & usb printer only work when they're plugged into the laptop from boot. I've consulted the forums and Ubuntu Help & Support but found nothing under usb hot swapping (if this is the right term i'm not sure). Any help would be appreciated. Thank you in advance.

---

### Post by monestri on 2007-11-01
*Update* 

Figured out a solution. I installed the usbmount package from Synaptic. 

```
sudo apt-get install usbmount
```

You must restart you computer for the changes to take affect.

---

