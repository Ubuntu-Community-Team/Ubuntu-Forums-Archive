---
title: "Segmentation Fault on Clean Install"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by gonsalvr on 2009-08-23
I'm using a Gateway Solo and trying to install Ubuntu 8.10 and or 9.10, on a thoroughly wiped HDD using Hirem's. Everytime I attempt to install it fails with a Segmentation Fault.  I have been trying to research to understand what is going wrong but the inputs are very confusing. Using Hirem's I have run all the tests and everything seems to appear functioning.
Can anyone point me in the right direction to fix this problem?

Thanks,
randy

---

### Post by running_rabbit07 on 2009-08-23
Can you boot the LiveCD at all?

If so can you go to System>Administration>Partition Editor and take a screenshot and post it?

---

### Post by RJARRRPCGP on 2009-08-23
> **gonsalvr said:**
> I'm using a Gateway Solo and trying to install Ubuntu 8.10 and or 9.10, on a thoroughly wiped HDD using Hirem's. Everytime I attempt to install it fails with a Segmentation Fault.  I have been trying to research to understand what is going wrong but the inputs are very confusing. Using Hirem's I have run all the tests and everything seems to appear functioning.
Can anyone point me in the right direction to fix this problem?

Thanks,
randy

Sounds like a bad CD or a motherboard problem. You may have bad caps on your motherboard or power supply. 

[http://badcaps.net](http://badcaps.net)

---

### Post by gonsalvr on 2009-08-23
I just did another wipe drive and attempted to install Ubuntu 9.04 Jaunty Jackelope.  I'm on two computers so I have to type the entry:

*Loading hardware drivers...
udevd-event[2221]: '/sbin/modprobe -b pci:v0000125Dd00001978sv0000107Bsd00002550bc04sc01i00' abnormal exit

Segmentation fault

Note: From what I can tell there were no error messages up to this point, it was all [ok]

Any thoughts?

Thanks,
randy****

---

### Post by running_rabbit07 on 2009-08-23
Can you start the LiveCD and choose the boot without making changes option?

---

