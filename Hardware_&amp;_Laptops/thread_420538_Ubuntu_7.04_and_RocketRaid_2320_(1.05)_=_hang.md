---
title: "Ubuntu 7.04 and RocketRaid 2320 (1.05) = hang"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by seer_tenedos on 2007-04-23
Guys I need some help.  When i installed Ubuntu 7.04 i found it had no support for the RocketRaid 2320 so i downloaded the lastest linux driver source (1.05) from highpoint.  Following instructions [ in this post ]("http://ubuntuforums.org/showthread.php?t=311723") i managed to create the required driver module though i did get a warning saying that a .cmd file could nto be found and executed the driver seemed to build ok. I then installed the driver with no problem.  After that i tried using modprobe to load the drive right away and discovered that modprobe would not return.

After a reboot the card still did nto work ether.  I reinstalled from scratch and performed a kernel patch instead though i did it on the 2.6.20.7 version of the kernel and i mad the rocket raid driver part of the kernel.  This time whent he pc booted up it would halt.  I changed grub and removed the quite command and you can see the last thing the kernel does before it hangs is it starts the  RocketRaid 2320 drivers.


Can anyone tell em where i should go from here to try to get the rocket raid to work.  I just want the disks to function as HD's not raided.

---

### Post by seer_tenedos on 2007-04-23
Also i am running the server edition of Ubuntu.

---

### Post by Navillus on 2007-07-15
Hey, good luck. Im getting this exact same error right now. Will post back if I find anything

---

### Post by rubberduckey on 2007-07-16
Hi! I'm having the same problem as well (except I'm using the RocketRaid 2310). Tried both installing the module and compiling it into the kernel. It just hangs on boot at the point you mentioned.

---

