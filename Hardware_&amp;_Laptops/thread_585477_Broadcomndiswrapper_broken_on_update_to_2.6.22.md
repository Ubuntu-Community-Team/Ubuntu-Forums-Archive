---
title: "Broadcom/ndiswrapper broken on update to 2.6.22"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by WastedMeat on 2007-10-21
I had my " Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" working fine with ndiswrapper and a 2.6.20 kernel.  When I updated to 2.6.22 (and from Feisty to Gutsy**), not only does the wireless not work, but a root process named 'ntos_wq/0' monopolizes  my processor whenever the device is activated.  If I do not deactivate the wifi with a function key, the machine will hang indefinitely at the stage during boot when it first activates the card.

I have tried reinstalling ndiswrapper, but beyond that, I am not sure what to do.  I can't at the moment run an lsmod from the problematic kernel, but I will do that whenever I get a chance.

**I am fairly certain this problem is specific to the kernel in spite of the general update because not only does the problem disappear if I use the old kernel from the new OS version, but I experienced the same problem with Gentoo a while ago while updating to the same kernel, and it is among the reasons I no longer have Gentoo on this machine.

---

### Post by WastedMeat on 2007-10-27
lsmod did not show anything useful.

Is there anything else should post to provide further information?  This is a very significant problem and I would really appreciate any help.

---

