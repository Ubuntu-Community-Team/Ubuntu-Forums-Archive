---
title: "vmware and usb problems"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by m.h.shams on 2006-02-16
dear friends, 

i'v installed vmware on ubuntu, and a windows xp pro on it,

i have problem with usb devices. when i start windows xp, if i had any usb devices, i got this warning message :

```
The existing driver (**usb-storage**) could not be successfully disconnected.
(Operation not permitted)

Unload the driver manually, then try again
```

im new in ubuntu, please help me.

---

### Post by arvindkst on 2007-03-27
try 

rmmod usb-storage

to unload the driver, will not work if you have other usb devices still attached

---

