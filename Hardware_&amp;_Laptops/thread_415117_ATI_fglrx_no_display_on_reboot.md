---
title: "ATI fglrx no display on reboot"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by applefreakpeeps on 2007-04-20
Hi folks!
                First time i am posting here.. I have been having this strange problem with the fglrx drivers. I was using Fedora but now have installed Feisty i386. I installed the restricted ati driver, but upon reboot my comp screen goes blank at the GDM login screen and the system freezes. ie. All activity stops.

The same problem I am having ever since fglrx 8.33.6. The older versions (till 8.32.5) work fine with the same method of install and i even get DRI (was using XGL+Beryl in FC6 with 8.32.5 on default 2.6.18 kernel). I have tried many distros (OpenSuse 10.2, Fedora 6 (newer kernels from 2.6.19 onwards), ubuntu 7.04 now) in vain, but same problem recurs in all.

The problem is new kernels work only with new fglrx drivers, which dont seem to work on my computer. What could be the issue? I am using a 

AMD 64 3200+ Venice
Gigabyte GA-K8N51-GMF9 (Nforce 430) Motherboard
ATI X1800XT 512 MB DDR3 graphics (MSI RX1800XT-VT-2D-512E)
1 GB DDR 400 RAM

:confused: 

PLEASE HELP!!!!

---

### Post by MindRiot on 2007-04-20
Perhaps you forgot to rebuild the ATI driver  modules with the new kernel.

Just a thought.

You should be able to do so from a terminal prompt by following the instructions outlined here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by applefreakpeeps on 2007-04-20
I have tried building manually (from the run file) and also by using the readily available xorg-x11-fglrx driver (downloaded using synaptic restricted drivers).. same problem with both:confused:

---

### Post by applefreakpeeps on 2007-04-20
any help???

---

### Post by applefreakpeeps on 2007-04-21
Attached is xorg log file....

please help

:confused:

---

### Post by applefreakpeeps on 2007-06-13
somebody pls help.. wat may be the problem??

---

