---
title: "xpad360 issues in Gusty"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by jimmyhilldrix on 2008-03-28
I've followed the instructions for installing the 360 controller module.  After downloading the source files and creating the make file I run the following commands

sudo make

sudo cp xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/

sudo depmod -a
sudo modprobe xpad

sudo gpasswd -a <user> plugdev

Then i restart.

Generally after a restart, the controller will work fine.  If I unplug it and plug it back in, however, it doesn't work.  The only way to fix this problem is to restart the computer.  Sometime I simply have to reinstall the module.

Is there any way to install the module such that it will work if unplugged and plugged back in.  Or is there an easy way to restart the usb subsystem so that it will recognize the controller if it is plugged in after being unplugged?

Thanks for any help.

---

