---
title: "Freescale mpc8308vmagd PowerQuicc II pro aka Bigfoot Killer E2100"
date: 2015-07-21
forum: Hardware
---

### Post by Lokz on 2015-07-21
Hello everyone, 
I will be starting an effort to write a driver for the Bigfoot Killer E2100. It is a system on a chip network interface found on the Gigabyte g1.guerilla motherboard. 
Much help appreciated, will update this thread with more info.

Here`s the roadmap :

1. Write the initialization code for the chip and code to load the blop.
Init sequence can be found here [http://cache.freescale.com/files/32bit/doc/ref_manual/MPC8308RM.pdf](http://cache.freescale.com/files/32bit/doc/ref_manual/MPC8308RM.pdf)

2. Assemble a minimal linux blop with all the necessary drivers for the system. 

3. Write the linux driver to send & receive network data from the chip via pci-e.

Hope I can get tips and help from you all.

---

### Post by KeeperOS on 2016-05-19
Hi, is this effort still ongoing 'cause as of Ubuntu 16.04 there's still no support for that chip.

BTW, my motherboard is the Gigabyte G1.Sniper (1366), virtually identical to the Guerilla and Assassin except for a couple of differences each (one has a different sound chip, the other more PCI-E slots)

(Also, does this help? [http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332) )

---

