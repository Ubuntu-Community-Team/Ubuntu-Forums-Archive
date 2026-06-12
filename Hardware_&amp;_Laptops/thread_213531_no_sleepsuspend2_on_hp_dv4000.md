---
title: "no sleep/suspend2 on hp dv4000"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by reacocard on 2006-07-11
I cannot get sleep or hibernation(via suspend2) to work on my hp dv4000 laptop. it appears to work, but on resume I just get a blank screen. for suspend2, I am using the kernel from here: [http://dagobah.ucc.asn.au/dapper-kernels/](http://dagobah.ucc.asn.au/dapper-kernels/)
I've searched these forums, but nothing seems to apply to this. any ideas?

---

### Post by Paerez on 2006-07-11
do you have an ati video card? I cannot suspend/hibernate if I use the fglrx driver with my radeon 9000, but if I use the ati or radeon driver its fine.

---

### Post by reacocard on 2006-07-11
nope. intel 915 integrated graphics.

---

### Post by reacocard on 2006-07-11
okay, i found the problem. if compiz is running, suspend(2) does not work. if i switch to metacity (or just kill compiz) it works. any ideas on how to automatically turn off compiz on suspend(2) and restart it on resume?

---

### Post by reacocard on 2006-07-11
alright, got compiz to restart for suspend2 by editing /etc/hibernate/common.conf
any ideas for regular sleep?

---

