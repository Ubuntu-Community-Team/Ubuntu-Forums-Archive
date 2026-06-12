---
title: "HP dv5z-1002 in Ubuntu 8.04.1 wired connection problem"
date: 2008-09-13
forum: Hardware
---

### Post by jollychang on 2008-09-13
This problem is very stranger.
when I used the live cd,and the wired connection is ok.
After I installed the Ubuntu in my harddisk(install is okay),but the wired doesn't work!!!(P.S: it is wired not the wireless problem)
I have try dhcp/static ip/ ip v4LL on the networking manager
of cource I have try the ifconfig/ sudo ifdown /ifup
nothing is ok.
the device manager disappear in the ubuntu menu.
I have try the Debian's iso...it can't be install in the second step.
It ask me to mount the CD-ROM.How can i mount that....it's to hard....
Help~help~

---

### Post by BenAshton24 on 2008-09-13
Hey, make sure you have all the drivers installed, you can find them in synaptic package manager (system --> administration --> synaptic) most likely an issue with motherboard drivers. to mount cdrom you do the following command just change "sdc0" to whatever your cdrom is at (just experiment, most likely sdc0 or sdc1)
> sudo mount /dev/sdc0
hope this helps though I'm not to sure about everything your asking?
Ben.

---

