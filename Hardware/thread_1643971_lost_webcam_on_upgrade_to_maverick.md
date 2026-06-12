---
title: "lost webcam on upgrade to maverick"
date: 2010-12-12
forum: Hardware
---

### Post by mmoalem on 2010-12-12
hi there all - seems like i have lost my webcam after upgrading to ubuntu 10.10 from lucid.

the webcam is an integrated one in a sony vaio sz3 laptop. it's a ricoh model (Bus 001 Device 002: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 [R5U870]) and on lucid i used the drivers from here:
[http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)
at the time it was version 4 and it worked fine.
after upgrading i have lost the webcam (cheese, skype can't see nada)
i have followed the instructions on this:
[http://ubuntuforums.org/showthread.php?t=1597534](http://ubuntuforums.org/showthread.php?t=1597534)
but that didn't help. went back to arakhne page and realised mine is a wdm and not uvc and so i need he R5U870 and not the R5U87x. so installed the version 5 driver (the most recent) and firmware loader but still no joy
can anyone help?
it's says something about the kernel needs a module or something... i just installed the 2 deb files



EDIT - Solved using this:
[http://translate.google.com/translate?hl=en&sl=pt&tl=en&u=http://ubuntuforum-br.org/index.php%3Ftopic%3D49371.30&anno=2](http://translate.google.com/translate?hl=en&sl=pt&tl=en&u=http://ubuntuforum-br.org/index.php%3Ftopic%3D49371.30&anno=2)

---

### Post by mmoalem on 2010-12-13
anyone who can help?

---

### Post by galland on 2011-04-16
Hi all,

The driver version 0.11.5 provided by arakhne.org does not compile any more on Maverick due to changes in USB API of the Kernel.

Version 0.11.6 is now provided and solves this compilation problem.
Cheese works perfectly, but Skype still have problems to use the webcam.

Stéphane.

---

### Post by meinz on 2012-04-26
I just upgraded to 12.04 precise, the ricoh webcam is no longer working, could install your deb packages, but that has no effect. the cam is not even seen with lsusb.
See:
user18@sonytravel:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 002 Device 005: ID 174c:5106 ASMedia Technology Inc. Transcend StoreJet 25M3
Bus 002 Device 006: ID 03f0:0862 Hewlett-Packard 
Bus 007 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 007 Device 003: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 007 Device 004: ID 044e:3013 Alps Electric Co., Ltd 
Bus 007 Device 005: ID 044e:3012 Alps Electric Co., Ltd 

Are there any updates available?

---

