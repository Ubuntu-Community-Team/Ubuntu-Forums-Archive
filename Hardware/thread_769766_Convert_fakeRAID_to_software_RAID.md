---
title: "Convert fakeRAID to software RAID"
date: 2008-04-26
forum: Hardware
---

### Post by aroddo on 2008-04-26
Hi,

some time ago I made installed a RAID-0 stripe with the onboard nvidia S-ATA controller (ASUS A8N-SLI Deluxe)
I wanted to mount that raid on my newly installed Ubuntu 8.04, of course.
I tried with dmraid and it fried my system very thoroughly, forcing me to reinstall it.

That's why I'd like to try without dmraid. Sinc Ubuntu apparently has a good Software RAID support, I'd like to know if and how you can adopt the old fakeRAID stripe as ubuntus software raid.

And in case it does work: Can you read that stripe under windows ?

Cheers!

---

### Post by aroddo on 2008-04-27
Forgot to mention:  I do not boot from the stripe! It's just a data partition, but I still want to use it.


[LIST]
[*]sda - Ubuntu/Windows
[*]sdb - RAID-0
[*]sdc - RAID-0
[/LIST]
I'd use dmraid, but the last time earned me a permanent stay in the busybox where I was informed that my boot device was busy. :(

---

