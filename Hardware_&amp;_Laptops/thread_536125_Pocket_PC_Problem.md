---
title: "Pocket PC Problem"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by aconley1 on 2007-08-27
I've been trying to connect my Pocket PC to my Sony Vaio Laptop running Feisty.  When I run dmesg, I get the following output:

[ 1845.484000] ipaq 2-1:2.0: PocketPC PDA converter detected
[ 1845.484000] drivers/usb/serial/ipaq.c: active config #2 != 1 ??
[ 1845.484000] ipaq: probe of 2-1:2.0 failed with error -5

can anyone tell me what the probe failed with error-5 means?  or , What can I do to fix this?

Thanks

---

### Post by geraldm on 2007-08-28
-5 is EIO  - Input/Output error.
From looking at the source code, I would have expected -ENODEV -19
The driver expects to find configuration # 1 
It found configuration 2, then sent the error number.

For a solution, the driver needs to find and set to configuration # 1.
There might be information on that device in /proc/bus/usb/devices which would show
the configurations available.  An alternate command for information: lsusb -vv

Gerald

---

