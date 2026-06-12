---
title: "Configuring CBM 1000 parallel thermal printer in 64 bit jaunty"
date: 2009-06-05
forum: Hardware
---

### Post by killerisation on 2009-06-05
This page suggests that what i am trying to do is possible:
[http://www.linuxquestions.org/hcl/showproduct.php?product=1866](http://www.linuxquestions.org/hcl/showproduct.php?product=1866)
however its not until i take the advice of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369850](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369850) and [http://linux.derkeiler.com/Mailing-Lists/Debian/2006-06/msg02216.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2006-06/msg02216.html) and do the following that i have a lp0 device.

killerisation@meanmachine:~$ sudo rmmod lp                 
killerisation@meanmachine:~$ sudo rmmod parport_pc         
killerisation@meanmachine:~$ sudo /sbin/insmod /lib/modules/2.6.28-11-generic/kernel/drivers/parport/parport_pc.ko io=0x378 irq=7
killerisation@meanmachine:~$ sudo /sbin/insmod /lib/modules/2.6.28-11-generic/kernel/drivers/char/lp.ko
killerisation@meanmachine:~$ sudo chown killerisation\: /dev/lp0

yet still when i enter the following the printer ceases to do anything (although it no longer gives an error message).

killerisation@meanmachine:~$ sudo echo "hello" > /dev/lp0

Any ideas about where the problem might be?
Also, how do i get the above commands to run at boot?

---

