---
title: "External hard drive will not mount after partial reformat"
date: 2009-05-19
forum: Hardware
---

### Post by johnnyxxxcakes on 2009-05-19
I was going to run a low-level format on my laptop's internal hard drive and I forgot to unplug the external hard drive (My Book 500GB) from the USB port, so it began a wipe on that disk as well. I quickly turned off the laptop, and tried to plug the external into another computer to see what it had erased, but it will not mount. I tried to mount it on Ubuntu and Puppy Linux, and I get nothing.

Any ideas what I should do?

[COLOR="Red"]EDIT: I forgot to mention something. After I removed the external hard drive, I restarted the low-level format process on just the internal hard drive. So I get back from school today and their was a failure wiping both drives. Currently, I'm running the system from the Ubuntu 9.04 LiveCD.[/COLOR]

---

### Post by logos34 on 2009-05-19
> **johnnyxxxcakes said:**
> 
Any ideas what I should do?


[Testdisk.]("http://www.cgsecurity.org/wiki/TestDisk")

sudo apt-get install testdisk

sudo testdisk

---

