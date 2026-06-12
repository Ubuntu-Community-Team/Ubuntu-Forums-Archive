---
title: "MSI H97M-G43 Motherboard feedback"
date: 2015-03-29
forum: Hardware
---

### Post by Lalaith on 2015-03-29
Hi, 

We want to build a Linux Desktop from scratch. It's the first time, so we would like to go for specially linux-friendly parts.
When it comes to motherboards, we didn't find any clear compatibility list surfing the net, so went straight to review mobos.
We are thinking of an MSI H97M-G43, but it is rather new and in their website they only offer drivers for Win7 and Win8. 
Did anyone try it already and can give us feedback on the ease of use for a linux desktop?

Is there any Motherboard vendor well known for being "linux-friendly/ubuntu-friendly"?

Many thanks in advance!

---

### Post by oldfred on 2015-03-29
It seems like many work but with some minor (or if important to you major issues)

       MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

Gigabyte's seem to need IOMMU setting changed in UEFI, not sure what that really does, but without it USB ports and some other things do not work correctly.
Asrocks have extra SATA ports called asmedia that do not work and if any of those ports are use then system does not work. Not sure if others use same technology.
I just built new system with Asus-AR and had to make many UEFI setting changes but otherwise system seems to work ok, so far.

All drivers are in Linux if you have a new enough version of Linux. Sometimes changes to kernel or support software take a bit to be developed as many vendors do not directly support Linux. And then it takes a bit more before all those changes are in the standard distributions. In those cases some users end up being testers and have to install the very newest kernel before distributions like Ubuntu have verified it all works and done testing.

---

