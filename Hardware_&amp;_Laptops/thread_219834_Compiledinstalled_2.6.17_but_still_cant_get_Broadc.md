---
title: "Compiled/installed 2.6.17 but still cant get Broadcom wifi working??"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by NeuroticSteelShed on 2006-07-20
I have compiled/installed kernel 2.6.17, but I still cant see my Broadcom 1390 wifi card listed in network manager. I uninstalled ndiswrapper so I dont believe that is causing a conflict. How can I tell if the module needed for my card is installed/loaded. And if it is not installed/loaded, how would I go about doing so?? ](*,)

---

### Post by linuxnewbie946 on 2006-07-20
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
Should solve your problem.

---

### Post by NeuroticSteelShed on 2006-07-20
Ok, I will try that link, but I think I am going to have problems. My card shows up like this.

0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re                          v 02)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev                           01)

I belive the first listing is my "wired" card. The second listing I believe is my wireless card. And it is listed as an Unknown device. Which I dont think is a good thing??

---

### Post by NeuroticSteelShed on 2006-07-20
Ok, SWING and a miss. I tried that forum, and NO go. I am also not sure how to remove the files it placed, Im not sure if that matters or not. Any other ideas. Or should I simply wait for the next release of Ubuntu?? Will it have the 2.6.17 kernel (or greater) built in, w/the module support already up and running??

---

### Post by etc on 2006-07-22
I compiled the vanilla 2.6.17 kernel with the ck patchset, after hearing the new Broadcom drivers would be included with this kernel.  In the default dapper kernel, the bcm43xx module would load and my Broadcom card would work.  Now, with the 2.6.17 kernel, there is no bcm43xx module so I do not know how to get my wireless card to work. EDIT: I'd also rather not use ndiswrapper at all, because that is just another problem itself

I've also just noticed that in my kernel-headers, I have the bcm43xx module.  When I configured my kernel sources, with xconfig, I did not see the option for broadcom wireless support at all.

```
$ uname -a
Linux laptop 2.6.17-ck1 #1 SMP Wed Jun 28 22:32:33 EDT 2006 i686 GNU/Linux
$ sudo modprobe -l | grep bcm43xx
$ locate bcm43xx
/usr/src/kernel-headers-2.6.17-ck1/drivers/net/wireless/bcm43xx
/usr/src/kernel-headers-2.6.17-ck1/drivers/net/wireless/bcm43xx/Makefile
/usr/src/kernel-headers-2.6.17-ck1/drivers/net/wireless/bcm43xx/Kconfig

```

---

### Post by discord on 2006-07-24
The support for the broadcom chipset in the kernel does not yet support the dell 1390 chipset. At least thats what I believe. I'm working on a fix to get network-manager working with ndiswrapper at the moment.

---

