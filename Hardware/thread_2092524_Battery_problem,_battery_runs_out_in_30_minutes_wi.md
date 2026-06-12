---
title: "Battery problem, battery runs out in 30 minutes with Quantal 64"
date: 2012-12-08
forum: Hardware
---

### Post by hansip on 2012-12-08
Well , Win7 + VMWare Workstation + Quantal 64bit = 90 min life. 
Dedicated Quantal 64bit partition can only last 30 minutes.
I've tried lowering LED Backlit and change things in powertop, but still no luck. 

Acer 4750G
Intel i5 2410M
4GB DDR3
Intel® HD Graphics 3000 + nVidia Optimus GT540M (no nvidia modules loaded yet)

Thanks in advance.

SOLVED :
it turns out i need bumblebee package even if dont intend to use the GT540M. because there's bbswitch module in bumblebee that will turn off my nvidia card. see [http://wiki.ubuntu.com/bumblebee](http://wiki.ubuntu.com/bumblebee)

oh yeah, in case you guys cannot load the bbswitch module (module not found) make sure your linux-image-xx and linux-headers-xx has the same version.

---

