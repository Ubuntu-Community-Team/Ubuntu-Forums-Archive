---
title: "ubuntu 12.04: kernel does not detect hotplugging USB3.0 drive"
date: 2012-06-18
forum: Hardware
---

### Post by aa-hcl on 2012-06-18
Hi,

I have ubuntu 12.04.

I have recently upgraded to latest kernel (3.2.0-25-generic) and hotpluging the USB3.0 HDD is NOT working any more, it was working OK with the previous kernel. When I plug the drive before booting, the drive is recognized and working OK.

When I monitor the kernel and udev by typing "sudo udevadm monitor"  I do not see any message when I plug in the USB  harddrive into the USB3.0 socket (which I have through the USB3.0 EC card on the laptop). When I plug the same drive to the USB2.0 socket, everything works and corresponding messages can be seen through "sudo udevadm monitor" and in /var/log/kern.log.

How the kernel detects the event that I plug in the HDD?
How to monitor it?

Any help or ideas regarding how to fix it or identify as "kernel bug" would be really appreciated!!!

Please help!

Many thanks!

---

