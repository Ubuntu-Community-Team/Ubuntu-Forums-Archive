---
title: "Install Hoary on EVO 510"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by mururoa on 2005-07-12
I try to install Hoary on a Compaq EVO 510 with seagate HD but the installer did not find any HD.
When booting he finds the IDE controller, fail to find the attached HD ( Seagate 20 Gb ) on IDE0 ( complaining about IRQ 14 failed or something like that ), find the CDROM on IDE1 and stop in the partitionning section because he cant find any partition to install linux.
Windows XP and Red Hat 9 where installed without problems on this computer and are still running.
I tried to boot using noacpi, nolacpi and pci=noapic but now I dont know what parameter to use in order to enable the HD detection.
Any idea ?

---

### Post by Triton on 2005-07-12
Update the BIOS

---

### Post by mururoa-fr on 2005-07-12
I updated the bios but this is not the pbm ( from 2.14 to 2.21 ).

The question is : wich parameter(s) can you specify at startup to allow hard drive detection when you already know that the HD is working and used under both Windows XP and Red Hat Linux 9 ?
Hard drive is not that old, a Seagate ST320011A 20 Gb ...

BTW the exact message at startup is :
ide0: probed IRQ 14 and default IRQ 14 failed.

---

### Post by mururoa on 2005-07-12
Uh ?
Should I stick to Red Hat or someone can point the pbm or give the parameter to use ?

---

### Post by Triton on 2005-07-13
I think you should be looking for another issue.  Do you have another drive to try in it for troubleshooting?

---

### Post by mururoa-fr on 2005-07-13
No, I have no other drive right now that I can use for test.
On Red Hat 9 the ide0 is found on IRQ 14.
On windows IRQ 14 too and DMA.

---

### Post by mururoa-fr on 2005-07-18
I'm still sticked on that problem.
Really anyone can give the parameter to enter at boot in order to enable HD detection or just point to a direction I may find a solution ?
It's just about detecting a working IDE HD that is used in both Linux and Windows eh ?!

---

### Post by mururoa-fr on 2005-07-18
Okay, found myself the solution ... offline.
Cant say thanks to anyone but in case somebody fall into the same problem here is the solution.
Keywords : probed IRQ 14 and default IRQ 14 failed.
The parameter is pci=routeirq.
Then HD is detected and properly setup for reboot after installation.

---

