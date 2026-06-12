---
title: "Can't see USB drive in my Lenovo T60"
date: 2010-06-11
forum: Hardware
---

### Post by lenny45 on 2010-06-11
Hey all, i use Ubuntu 10.04. Can't see USB flash drive when i plug it into my Lenovo T60. my USB mouse works fine but not my drive. any ideas? thx--lenny

---

### Post by lenny45 on 2010-06-11
ok, this worked for me!

sudo modprobe usb_storage 

use the above command in terminal to see a USB stick in Ubuntu. (may have to unplug/replug stick to see it).

---

