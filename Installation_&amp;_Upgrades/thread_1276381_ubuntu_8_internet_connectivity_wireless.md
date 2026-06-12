---
title: "ubuntu 8 internet connectivity wireless"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by middlepath on 2009-09-27
hi,

i am trying to connect through ubuntu desktop wireless to the internet with a linksys router, however, it seems that when i sudo lsmod | grep ipw2000 it shows no output seems like there is no driver for my wifi adapter....

how do i get the wifi adapter, will appreciate any info on this.

thanks much.

middlepath

---

### Post by rreese6 on 2009-09-27
please give more information. 

post the following output from these commands:
```
lspci
sudo lshw -C network
ifconfig
iwconfig

```
you can put all that data in a compressed file and attach here.

---

