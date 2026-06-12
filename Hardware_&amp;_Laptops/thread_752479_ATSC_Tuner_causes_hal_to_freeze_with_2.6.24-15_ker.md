---
title: "ATSC Tuner causes hal to freeze with 2.6.24-15 kern"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by owenlinx on 2008-04-11
The computer freezes on hal during bootup. This is a kworld ATSC 115 set it up using this little how to from mythtv  [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)

Attached is dmesg, kern.log , and lshal. 

This is the bug on launchpad related to saa7134 kernel module.

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271)

if you blacklist the module in /etc/modprobe.d/blacklist file the kernel will boot.

---

