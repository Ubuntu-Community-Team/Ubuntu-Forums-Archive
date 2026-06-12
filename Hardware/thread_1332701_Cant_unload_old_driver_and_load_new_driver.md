---
title: "Cant unload old driver and load new driver"
date: 2009-11-20
forum: Hardware
---

### Post by confused_user on 2009-11-20
Hi, i'm trying to unload a broken driver for my wireless card and load the newer one.

My wifi card is currently using rtl8180 and it want it to use RTL8187Se

matt@matt-netbook:~$ modprobe -l | grep rtl8187
kernel/drivers/net/wireless/rtl8187.ko
kernel/drivers/staging/rtl8187se/rtl8187se.ko

ok cool, just to prove that rtl8180 is there too

modprobe -l | grep rtl8180
kernel/drivers/net/wireless/rtl8180.ko

so i should just be able to remove rtl8180 and insert rtl8187?

matt@matt-netbook:~$ sudo modprobe -r rtl8180
[sudo] password for matt: 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

does not do anything, wireless card is still on and connected

matt@matt-netbook:~$ sudo modprobe rtl8187
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

restart wireless card via network manager and it loads up rtl8180 everytime.

I have tried disabling the network card while i perform the above steps, rebooting afterwards...all to no avail.

I have no idea what WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
 means but from what i have read it's just some jumped up debian developer trying to make some kind of point - I dont think it's an actual problem.

Help!

---

### Post by confused_user on 2009-11-22
bump

is there any info i can provide to help?

---

