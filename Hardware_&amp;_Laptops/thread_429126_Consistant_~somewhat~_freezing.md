---
title: "Consistant ~somewhat~ freezing"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by 80r on 2007-04-30
I'm on a Dell Inspiron 600m laptop and I've used the Ubuntu 6.06 Live CD, Ubuntu 6.10 Live CD, Ubuntu 6.10 on USB, Xubuntu 7.04 Live CD, and Xubuntu 7.04 installed, and every time about 5-10 minutes in, it does this odd sort of freeze that I've never seen before.  It freezes for 10 seconds, works for 1 second, freezes for 10, works for 1, etc. until I restart.  It all works fine in Windows though.  Anyone know what this problem is caused by or could link me to somewhere that has the solution.  I tried searching around but since this really isn't "freezing" I come up with nothing related.

Oh and it's not overheating.

---

### Post by simonn on 2007-04-30
The only time I have come across something like this is with a dodgy USB DTV dongle.

Check dmesg and /var/log/messages before you reboot. Although this may be a challenge if you only have the odd second here an there to do anything. Probably the best thing to do is use a different boot CD, e.g.[http://www.sysresccd.org?](http://www.sysresccd.org?) If this does not have the same problem, you can boot in to ubuntu reproduce the problem, boot using sysreccd, mount your root drive you will have all the logs (dmesg and messages) in /[mount point]/var/log.

It does not sound like memory, but try memcheck anyway - should be an entry in the grub menu when you reboot.

---

