---
title: "Issues with FTDI serial converter, Ubuntu, and USB3.0"
date: 2015-10-08
forum: Hardware
---

### Post by marc59 on 2015-10-08
Hi,

I'm using Ubuntu 12.04LTS to communicate with some EPOS hardware. The hardware requires the use of a USB to serial converter.

I've been testing the system successfully on a virtual machine on my mac running Ubuntu 12.04.

I recently transferred to using an Intel NUC mini computer. I have been having problems getting the USB to serial converter working on this new computer.

Everything in Ubuntu is the same on both the virtual machine and the intel NUC (version of Ubuntu, all software packages, config files etc).

On both of them the FTDI device shows up on /dev/ttyUSB0. However on my mac it is attached to a USB1.1 root hub, and on the intel NUC it is attached to a USB2.0 root hub.

I think this may be the cause of the problems. Both my mac and the NUC have USB3.0 ports so not sure why it's behaving like this?

Is there any way to get it working with the USB2.0 port? Or to force the NUC to use a 1.1 hub?

Any help is much appreciated!

Thanks,
Marc

---

