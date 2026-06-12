---
title: "What headers to install for ATI drivers"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by BM85 on 2005-03-17
I'm a newbie to linux and was following this guide ( [http://ubuntuforums.org/archive/index.php/t-13226.html](http://ubuntuforums.org/archive/index.php/t-13226.html) ) on how to install Ati drivers. From reading the post it seems that I need install the proper the proper linux header. I have an AMD64 ( K8 ) running 32bit Ubuntu so I'm not sure which headers to install.

Heres my linux version:
Linux home 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

And heres the headers available:
linux-headers-2.6.8.1-3 - Header files related to Linux kernel version 2.6.8.1
linux-headers-2.6.8.1-3-386 - Linux kernel headers 2.6.8.1 on 386
linux-headers-2.6.8.1-3-686 - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.8.1-3-686-smp - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.8.1-3-k7 - Linux kernel headers 2.6.8.1 on AMD K7
linux-headers-2.6.8.1-3-k7-smp - Linux kernel headers 2.6.8.1 on AMD K7 SMP
linux-headers-2.6.8.1-4 - Header files related to Linux kernel version 2.6.8.1
linux-headers-2.6.8.1-4-386 - Linux kernel headers 2.6.8.1 on 386
linux-headers-2.6.8.1-4-686 - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.8.1-4-686-smp - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.8.1-4-k7 - Linux kernel headers 2.6.8.1 on AMD K7
linux-headers-2.6.8.1-4-k7-smp - Linux kernel headers 2.6.8.1 on AMD K7 SMP
linux-headers-2.6.8.1-5 - Header files related to Linux kernel version 2.6.8.1
linux-headers-2.6.8.1-5-386 - Linux kernel headers 2.6.8.1 on 386
linux-headers-2.6.8.1-5-686 - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.8.1-5-686-smp - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.8.1-5-k7 - Linux kernel headers 2.6.8.1 on AMD K7
linux-headers-2.6.8.1-5-k7-smp - Linux kernel headers 2.6.8.1 on AMD K7 SMP


I'm completely new to linux so help would be greatly appreciated.

---

### Post by trigg on 2005-03-17
[QUOTE=BM85]I'm a newbie to linux and was following this guide ( [http://ubuntuforums.org/archive/index.php/t-13226.html](http://ubuntuforums.org/archive/index.php/t-13226.html) ) on how to install Ati drivers. From reading the post it seems that I need install the proper the proper linux header. I have an AMD64 ( K8 ) running 32bit Ubuntu so I'm not sure which headers to install.

Heres my linux version:
Linux home 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

And heres the headers available:
linux-headers-2.6.8.1-3 - Header files related to Linux kernel version 2.6.8.1
linux-headers-2.6.8.1-3-386 - Linux kernel headers 2.6.8.1 on 386
linux-headers-2.6.8.1-3-686 - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.8.1-3-686-smp - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.8.1-3-k7 - Linux kernel headers 2.6.8.1 on AMD K7
linux-headers-2.6.8.1-3-k7-smp - Linux kernel headers 2.6.8.1 on AMD K7 SMP
linux-headers-2.6.8.1-4 - Header files related to Linux kernel version 2.6.8.1
linux-headers-2.6.8.1-4-386 - Linux kernel headers 2.6.8.1 on 386
linux-headers-2.6.8.1-4-686 - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.8.1-4-686-smp - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.8.1-4-k7 - Linux kernel headers 2.6.8.1 on AMD K7
linux-headers-2.6.8.1-4-k7-smp - Linux kernel headers 2.6.8.1 on AMD K7 SMP
linux-headers-2.6.8.1-5 - Header files related to Linux kernel version 2.6.8.1
linux-headers-2.6.8.1-5-386 - Linux kernel headers 2.6.8.1 on 386
linux-headers-2.6.8.1-5-686 - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.8.1-5-686-smp - Linux kernel headers 2.6.8.1 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.8.1-5-k7 - Linux kernel headers 2.6.8.1 on AMD K7
linux-headers-2.6.8.1-5-k7-smp - Linux kernel headers 2.6.8.1 on AMD K7 SMP


I'm completely new to linux so help would be greatly appreciated.[/QUOTE]
 The key is to install the headers for the kernel that you are currently running, which at this point appears to be 2.6.8.1-3-386  -- so install those headers.  If you wish to change your kernel - then install different headers accordingly.

trigg

---

### Post by Forge on 2005-09-01
I believe you'll find you don't want just the headers, you actually want the whole kernel source that matches your running kernel.

---

