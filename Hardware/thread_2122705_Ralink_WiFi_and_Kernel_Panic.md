---
title: "Ralink WiFi and Kernel Panic"
date: 2013-03-05
forum: Hardware
---

### Post by pinballwizard on 2013-03-05
I have a strange issue. I have a new Compaq CQ58, and it uses a Ralink 3290 wifi card. I have tried running 12.04 and 12.10 and whilst they run fine, as soon as I compile the drivers into the kernel, I get random instances of kernel panic. 

I have tried evry kernel from 3.5 to 3.8 and still have this problem. I can have a stable system with no wifi, or I can have wifi for two minutes before I get panic.

Please help me, or tell me what outputs to post here and I will.

Ta.

---

### Post by Hadaka on 2013-03-06
Hi, have you tried this?
[http://ubuntuforums.org/showthread.php?t=2104690ead.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690ead.php?t=2104690)

---

### Post by pinballwizard on 2013-03-06
> **Hadaka said:**
> Hi, have you tried this?
[http://ubuntuforums.org/showthread.php?t=2104690ead.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690ead.php?t=2104690)

That's exactly what I did. And although it fixes the wireless issue, it results in kernel panic and I have to hard restart.

---

### Post by pinballwizard on 2013-03-06
Maybe it's something else causing the panic? It's just strange that I can use the system just fine untill I compile the driver into the kernel.

For an interim solution, I picked up a $10 Tenda 150N usb wifi adapter, and it runs perfect out the box.

---

### Post by pascalfares on 2013-04-25
i GET THE SAME PROBLEM KERNEL PANIC AFTER INSTALLING THE RT3290 MODULE PATCH

---

### Post by hanspoo on 2013-07-07
The same problem here, i've tried with 12.10 and 13.04 with no results, in 13.04 i've disabled de macros that leads to compilation errors, and in 12.10 blacklisted the drivers and all the instructions, it seems that HP is really no linux friendly.

---

