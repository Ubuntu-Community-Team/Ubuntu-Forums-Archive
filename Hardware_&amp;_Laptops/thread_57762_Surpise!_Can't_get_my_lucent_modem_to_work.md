---
title: "Surpise! Can't get my lucent modem to work"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by N8MAN1068 on 2005-08-17
heh
been doing some reading on:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ubuntu-install.html](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ubuntu-install.html)
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)
[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

./scanModem identifies a 'The modem has a supported Lucent/Agere DSP (digital signal processing) chipset'
Few wrenches though...I have a AMD XP 2600+ cpu, so i'm running the K7 kernels, and the above packages require the i386 packages.
ubuntu was originally installed with the i386 packages, and it seemed to run ok, but i installed the correct amd kernels, rebooted, then completely removed the i386 kernels.
should i reinstall them?

what about us AMD folks?  ](*,)

---

### Post by az on 2005-08-18
No, you can compile the drivers for the k-7 arch.  Just install build-essential and linux-headers-2.6.10-5-k7...

The precompiled drivers in the ubuntu kernel do not work for you?

---

### Post by N8MAN1068 on 2005-08-18
Negative. Ubuntu drivers did not work.

Got a link to that k7 arch?

Gonna give it one last go today....then I'll be heading to Best Buy for either a Creative Labs-Modem Blaster, or Staples for a Zoom V.92 external modem(label says it works w/ Linux+Unix..haha)

---

### Post by az on 2005-08-18
[QUOTE=N8MAN1068]Got a link to that k7 arch?

QUOTE]


I was not clear, my bad.  The driver you have can be compiled for the 386, 686 or k7 kernels, depending on the linux-headers you use.  Those are all part of the 386 architecture.  So, you do not have to do anything different than the usual procudure, other than use the linux-headers for your running kernel which is k7 in this case.

---

### Post by blastus on 2005-08-19
I forgot to mention that Wiki post [https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent) is for i386 only. But I imagine the procedure for AMD for the same modem would be kind of similar. Instead of using the linux-headers-2.6.10-5-386 package you would use the AMD linux header package...I'm not sure what package it is though?

Apparently there are two ways to get a Lucent WinModem to work on Ubuntu:

1. Use the precompiled modules (I'm not sure how to do that yet)
2. Compile the modules yourself

I'm not sure what the procedure is if you use the precompiled modules. But if you compile the modules yourself you need the build-essential package and the linux headers package for your kernel.

---

### Post by az on 2005-08-19
[QUOTE=blastus] Instead of using the linux-headers-2.6.10-5-386 package you would use the AMD linux header package...I'm not sure what package it is though?
[/QUOTE]


linux-headers-2.6.10-5-k7


386 is for all architechtures
686 is for Pentium (II, III, IV)
k7 is for AMD
smp if if you have multiple processors.

apt-cache search linux-image-2.6.10

---

