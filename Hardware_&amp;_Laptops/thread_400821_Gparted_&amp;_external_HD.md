---
title: "Gparted &amp; external HD"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by DapperMe17 on 2007-04-03
Hi

Kubuntu 6.10


I'd like to partition a Rock Mobile external HD, using Gparted Live. 


When I run Gparted off the CD, I can see my HD power light change, but it doesn't locate the external drive. 

However, when I run lsusb from the Gparted CD terminal, the external HD does indeed show.


I've done some messing with unplugging & turning the external on/off, but haven't come up with  anything.

Could I be doing something wrong?


Thanks

---

### Post by teaker1s on 2007-04-04
while I'm no expert, it sounds like you haven't got the external drive mounted, you could use **pmount** also **fdisk -l ** will list device partitions

---

### Post by DapperMe17 on 2007-04-05
Good to go!


Thanks

---

