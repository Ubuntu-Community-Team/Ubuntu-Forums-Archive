---
title: "HP Pavilion jMicron 5 in 1 card reader help"
date: 2009-05-24
forum: Hardware
---

### Post by vonti on 2009-05-24
I've got a problem with my memory card reader - it doesn't work.

lspci 
```
0a:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
0a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```please help, I really need it

---

### Post by vonti on 2009-05-27
bump

---

### Post by Dark_Stang on 2009-05-27
This looks like a known issue. Probably an issue with the kernel. The only useful thing I've found is from a Gentoo site that states...
> # SD/MMC card: just enable "MMC/SD/SDIO card support" ---> "MMC block device driver" in kernel config, drivers section 
[http://en.gentoo-wiki.com/wiki/HP_Pavilion_DV5_(PUMA](http://en.gentoo-wiki.com/wiki/HP_Pavilion_DV5_(PUMA))

---

### Post by Samer Eberlin on 2010-12-08
Hi Vonti and Dark_Stang!

I had gotten the same problem... and to solve it on Ubuntu 10.04, we just need to load the "mmc_core" and "mmc_block" kernel module (the current kernel version already support it).

```
sudo echo mmc_block >> /etc/modules
```

And then, reboot your machine with your memory card inserted :-)

Thanks and BR,
/Samer.

---

