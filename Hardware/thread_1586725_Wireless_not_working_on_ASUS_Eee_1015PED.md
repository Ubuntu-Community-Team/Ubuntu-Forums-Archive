---
title: "Wireless not working on ASUS Eee 1015PED"
date: 2010-10-02
forum: Hardware
---

### Post by Veld on 2010-10-02
When I log in to Xubuntu, the "Hardware Drivers" app tells me I. need to activate the driver for "Broadcom STA", but after I click on "Activate", an error message pops up

>  Sorry, the installation of this driver failed.

Please have a look at the log file for details.: /var/log/jockey.log This is the error the logs shows:

>  2010-10-02 16:45:49,269 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-02 16:45:49,327 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-02 16:45:49,444 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-02 16:52:55,492 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-02 16:53:43,819 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-02 16:53:51,104 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-02 16:53:51,105 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-10-02 16:53:51,161 DEBUG: BroadcomWLHandler enabled(): kmod disabled  bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted What can you guys make of this?


Nevermind. Problem solved after updating. I was running Xubuntu out of the box.

---

### Post by 0x656b694d on 2010-11-12
Hi Veld,
Can you please confirm that your 1015PED can see wifi networks around now and you can connect to it? In public places, for instance.
Trying to figure the problems i'll run if will buy one for myself.
Thanks.

---

