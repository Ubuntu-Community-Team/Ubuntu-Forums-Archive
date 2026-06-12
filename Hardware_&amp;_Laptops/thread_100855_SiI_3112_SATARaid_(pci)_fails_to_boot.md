---
title: "SiI 3112 SATARaid (pci) fails to boot"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by BorisBarowski on 2005-12-08
Hi there
I installed ubuntu on my pc (thanks for the free disks !!), but i still have a major problem.

I have 2 IDE drives, and 2 extra Sata drives on a Silicon Image 3112 RAID card over pci. (disks aren't in RAID)

when the pci-card is plugged in, ubuntu stops loading after the screen with "loading modules"
it then jumps back to the previous screen with 
"Uncompressing linux ... ok, kernel is booting
loading, please wait"

well, i waited, it just hangs there, no disk activity, nothing

I found someone with the same problem:
[http://www.ubuntuforums.org/showthread.php?t=32640&highlight=PCI+sata](http://www.ubuntuforums.org/showthread.php?t=32640&highlight=PCI+sata)
no one answered there though, but i know i'm not alone now :p 

So, if you could help me, I'd really appreciate it.

Thanks in advance
Boris Barowski

---

### Post by BorisBarowski on 2005-12-09
Just found out that when i boot without any drives attached to the PCI controller, ubuntu DOES boot

hope this is any relevant to the problem, and helps to find a solution

---

