---
title: "SATA / SAS Controller installation (Mavell / Adaptec) ubuntu server 8.04.3"
date: 2009-10-11
forum: Hardware
---

### Post by TheNet1996 on 2009-10-11
Hi,

is there a way to install the mvsas.ko on ubuntu 8.04.3 server?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/327783](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/327783)

I have a Adaptec ASC-1405 with the Marvell Chip.

Thanks

---

### Post by mogie on 2009-10-30
I have the exact same problem here with 8.04.3 LTS.

I find the only solution is to get the newest kernel in which supports the drivers. 2.6.28-16 from 9.10, or else compile the 8.04.3 kernel manually (which I've never done before) with the CONFIG_SAS_SOMETHING option. 


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/358875](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/358875)

---

