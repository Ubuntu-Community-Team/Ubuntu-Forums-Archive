---
title: "Swapped Video Cards,Additional Drivers Says Nvidia Binary Is Installed, But It Isn't"
date: 2018-07-26
forum: Hardware
---

### Post by lostmoonofsaturn on 2018-07-26
I replaced the AMD card in an 18.04 machine with an Nvidia card, rebooted, used Additional Drivers to install the proprietary Nvidia driver, rebooted, and came back up on Nouveau.

When I run Additional Drivers now, it initially displays "No proprietary drivers in use" then displays the notice that the Nvidia proprietary driver is in use.  It is not. lsmod doesn't find the module and "modprobe -i nvidia" reports " Module nvidia not found in directory /lib/modules/..."

Is there a fix that does not involved reinstalling?

---

