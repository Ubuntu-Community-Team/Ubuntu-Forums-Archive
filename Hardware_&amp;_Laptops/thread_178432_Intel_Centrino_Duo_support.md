---
title: "Intel Centrino Duo support?"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by halfthelaw on 2006-05-17
Here are the specs of the Dell Latitude D620 laptop which I am trying to install on:
Processor: Intel Core Duo T2300
Chipset: Intel 945GM
Sound: Integrated
Graphics: Intel GMA 950
Storage: SATA/integrated
Network: Intel PRO/ Wireless 3945ABG 802.11a/b/g

Since I wasn't able to find details on whether or not this laptop or these components were supported, can anyone provide me with any clues as to whether or not this might work?

---

### Post by John.Michael.Kane on 2006-05-17
Everything in that machine looks golden. I beleave you will need to install the 686 smp kernel after you finsh the install so both cores are seen,and used.

---

### Post by dragonflyFZX on 2006-05-18
have a look at:

[http://ubuntuforums.org/showthread.php?t=160679&highlight=dell+latitude+d620]("http://ubuntuforums.org/showthread.php?t=160679&highlight=dell+latitude+d620")

---

### Post by halfthelaw on 2006-07-07
Wireless worked with the default install. However, after I uninstalled the 386 kernel and installed the 686 kernel, it stopped working. How can I get it working again?

EDIT: nm, it's working after an update of all system packages.

---

### Post by elglas on 2006-07-24
i'm assuming your issue is with the x server crashing

I've found 

```
sudo depmod -a
```

works well

---

### Post by el3ktro on 2006-08-26
Hm, I just bought an Averatec 2460 with the exact same hardware, same CPU, same chipset, same graphics. The onboard NIC is a Realtek 8139 and it has the same wireless as yours - but I can neither run the Ubuntu Desktop CD, nor Knoppix nor the Gentoo Install CD on it :-(

I found out that the 8139too driver for the onboard NIC crashes the systemm so I found a way to not load this module during startup - but the system still hangs during hardware autodetection - so there must be another module which causes the system to freeze. If I boot Gentoo without hardware autodetection everything works fine (except I don't have wireless & wired network)

I've just been on the Intel homepage and they state that the Centrino platform and the chipset that we both have is fully supported on Linux - so what's wrong with my setup?

Can anybody help me?

Tom

---

