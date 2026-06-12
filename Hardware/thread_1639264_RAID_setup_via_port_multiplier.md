---
title: "RAID setup via port multiplier"
date: 2010-12-06
forum: Hardware
---

### Post by tylersontag on 2010-12-06
Hey all, i recently purchased this 5 bay RAID server with 3Gbps PCI-e port multiplier

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816132015](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132015)

But i'm curious how i'm supposed to manage this...  Will it just be the case that when i put this together, i'll just see each drive as a seperate connected drive and i'll need to use MDADM to manage them as a software RAID?   Or am i off my mark here?

---

### Post by Fafler on 2010-12-07
Just pop it in and it should detect the drives individually. When you setup up the RAID, use the devices in /dev/disk/by-id/. This way you can use the serial number of each drive instead of the dynamically assigned device names like /dev/sda.

---

