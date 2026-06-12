---
title: "Load NIC driver module at setup time?"
date: 2010-12-04
forum: Hardware
---

### Post by norbert78 on 2010-12-04
Hi folks,
I'm pretty new with Ubuntu and trying to get it installed on my EEE Box B202. The desktop versions of Ubuntu (10.04) work fine but originally my plan was to put a server version or a command line system to this machine (the plan is to run a subversion server here and a desktop system is the pure overkill for this). 

However, when I try to install the server version I get an error that the network card cannot be detected. I can finish the installation without a NIC, compile the driver from and load the module to the kernel. However, this is really annoying (as I have to do the complete network configuration manually afterwards).
I would really prefer to get the driver for my NIC into the system at setup time. 
The lspci on the system (using the desktop version) says:

[...]
01:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 11)

Putting the output of a lspci -n to [http://kmuto.jp/debian/hcl/index.rhtmlx](http://kmuto.jp/debian/hcl/index.rhtmlx) says that the NIC should work starting with kernel v2.6.29 and that JME (guess that this is a kernel module) is the driver. 

So the question that I have is: How do I configure the installer of Ubuntu Server to load this module at setup time? I would prefer the server 10.04.
Thanks for any tipp in advance
Regards
Norbert

---

