---
title: "nx6125 and sd card reader"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by cyril.scetbon on 2006-06-05
Hi all,

I was using breezy but my sd card reader was not working. After having tested the dapper live cd to test my sd card reader and enjoyed it, I've decided to migrate to dapper. However, it's not working as with breezy. I've downloaded kernel 2.6.17 and applied the latest patch, chosen sdhci driver unsuccessfully.

Anyone ?

---

### Post by dantum on 2006-06-06
Hi,

Yeah the card reader support for SD cards has only recently been added to the kernel. It should be out as standard with 2.6.17. Dapper Drake has support ported to the current working kernel. I have nx6125 but haven't played with card reader yet.

---

### Post by cyril.scetbon on 2006-06-15
[QUOTE=dantum]Hi,

Yeah the card reader support for SD cards has only recently been added to the kernel. It should be out as standard with 2.6.17. Dapper Drake has support ported to the current working kernel. I have nx6125 but haven't played with card reader yet.[/QUOTE]

It works by using kernel >= 2.6.17-rc1 with patches from [http://list.drzeus.cx/pipermail/sdhci-devel/2006-May/000809.html](http://list.drzeus.cx/pipermail/sdhci-devel/2006-May/000809.html) + module fakephp
+ use of the following commands in rc.local :

modprobe fakephp
setpci -s 02:04.4 86.b=90
setpci -s 02:04.3 4c.b=02 # FlashMedia SD disable
setpci -s 02:04.4 04.b=06 # SDHCI Mem+ BusMaster+
setpci -s 02:04.4 88.b=01 # SDHCI DMA enable
modprobe sdhci
modprobe mmc_block

U must modify it with values got from lspci -v

---

