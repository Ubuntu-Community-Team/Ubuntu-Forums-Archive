---
title: "Ipod Unmonting"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by passcode on 2005-05-23
When I unmount my iPod the screen still reads "Do not Disconnect." Should i worry about this or is this perfectly normal. I am using 4G 20gig iPod, connected via usb.

The iPod also auto mounts, all that I have done is changed the iPod directory in the gtkpod preferences. I have no other problems then this.

---

### Post by 23meg on 2005-05-23
try ejecting your ipod with the following command:
```
sudo eject /dev/sdb
```
assuming your ipod is sdb as usual.

---

