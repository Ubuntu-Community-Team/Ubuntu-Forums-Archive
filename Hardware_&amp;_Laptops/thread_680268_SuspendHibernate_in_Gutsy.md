---
title: "Suspend/Hibernate in Gutsy"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by motion parallax on 2008-01-27
Acer Aspire 5610
Gutsy 7.10
Core Duo 1.73GHz
1G DDR2 RAM
Integrated Vid Chip

I have a problem with Suspend and Hibernate. Gutsy will suspend, but wifi stops working upon waking. With hibernate it goes down to a command line screen and locks.

I've spent a few hours looking for solutions, and the only two that I've found are below.

I'm not sure if either of these will fix it. The first answer refers to ATI drivers (I don't have an ATI card, though). I want to make sure these modifications won't cause other problems. If anybody thinks these may work, could you explain in lay terms how to implement them?


Suspend/Hibernation work with 7.12

With Gutsy release, there was a big problem using the ATI proprietary drivers. The Suspend/Hibernate function stopped working. The problem was due to the new SLUB allocator incorporated in 2.6.22 / 2.6.23 Kernel.

The problem has been solved in the AMD Catalyst 7.12 driver release. Suspend/hibernate is not working for FireGL 5250. For FireGL 5200, suspend works with the 7.12 fglrx kernel module loaded (which did not work before this release) , but does not work if X is running.

For Thinkpad T60 with ATI X1400, to get the laptop to wake up from suspend, I had to change the following in /etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false

Found here: [https://bugs.launchpad.net/ubuntu/+s...2/+bug/121653/](https://bugs.launchpad.net/ubuntu/+s...2/+bug/121653/)

([http://wiki.cchtml.com/index.php/Ubu...work_with_7.12](http://wiki.cchtml.com/index.php/Ubu...work_with_7.12)) <- found here



1) I installed uswsusp only to find that it did not have s2ram in the
ubuntu package. The s2both or whatever does not do the same for me so I removed the ubuntu package. I installed the one from Debian Lenny instead. I then
changed the hal suspend and hibernate scripts to only call s2ram and
s2disk respectively. These scripts are:

/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

For the hibernate one, I simply backed up the original file and removed
all the stuff and just put in s2disk. For the suspend, I put in s2ram.

---

