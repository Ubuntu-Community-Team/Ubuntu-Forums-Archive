---
title: "Asus P5w Dh Deluxe Compatibility Or Sth Problems"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by shoutingstar on 2007-05-25
Hello people

Yesterday i installed kubuntu on my pc, which has these parts:

Asus p5w dh deluxe
Intel core 2 duo E6600
G.Skill 2GB DDR2 HZ PC2-6400C4 (2x1GB) CAS4 Dual Channel Kit
Nvidia 7900GT 256 XFX
1 IDE hard disk, on which i have made the installation of kubuntu
2 Sata II hard disks, on which i have data on the one and data and windows on the other

I have i think a compatibility problem, because i couldnt do the installation if i hadnt disabled the jmicron sata socket, if i hadnt put the ide configuration on enhanced mode and pata.

If a change these on my bios, i cannot load kubuntu

As a result of the changes i did to install and work on ubuntu, i cant see my sata hard disks.

Can anybody help me?

Thank a priori

---

### Post by MCSE_Crossover on 2007-06-13
try changing the BIOS settings to Standard IDE SATA+PATA. Then, once grub loads, edit the kernel boot options and append "irqpoll" to the very end - after where it says "quit nosplash"

So it would say "kernel 2.blah blah blah blah blah ro quiet nosplash irqpoll"

Understand?

Or, you can try leaving the boot options the same, but instead, in the BIOS, change the IDE options to AHCI. This way will take longer to actually boot the machine, but both worked for me.

---

