---
title: "Wireless internet &amp; Custom Kernel"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by jerrykenny on 2008-01-15
This might come in handy if you meet the following criteria . . . 

 1 You're running Gutsy
 2 You have a laptop with a good working wireless connection (using gutsy)
 3 You're going to compile your own kernel.

Compiling your own kernel from kernel.org will speed up yer boot time, and will probably provide you with hours of demented frustration, . . . . . but the downside is, you'll lose access to the very usefull ubuntu-specific kernel & hardware support.

But heres a handy kludge . . . . .  if you cant get your wireless card working, for instance, even though youve faithfully followed Intels step by step fucXup.


In Essence, make all the firmware supplied by ubuntu available for your new kernel. its located in /lib/firmware.

a] sudo -s to root
b] cd to /lib/firmware
c] uname -r will tell how your custom kernel reports itself
d] cp -r <the ubuntu folder 2.6.22.whatever> <uname-r whatever>

hopefully on your next reboot, your custom kernel will locate the firmware, and you wont get error messages like

Aug 16 14:34:29 MyPC iwl4965: iwlwifi-4965.ucode firmware file req failed: Reason -2
Aug 16 14:34:29 MyPC iwl4965: Could not read microcode: -2


Good Luck

---

