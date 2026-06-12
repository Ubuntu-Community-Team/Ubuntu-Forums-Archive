---
title: "VirtualBox error"
date: 2008-09-19
forum: General Help
---

### Post by XWolf on 2008-09-19
So I'm new to Ubuntu and linux overall so I don't know much, anyway when trying to run VirtualBox I get the following error.

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

So I searched around looking for as to how to install the virtualbox-ose-modules package... It led me to a thread off of these forums. However to command that worked for most people didn't for me. I didn't get an error when installing the package... however I still get the same error when trying to run VirtualBox. Any solutions?

-XWolf.

---

### Post by washeddang on 2008-09-19
Just to be sure, you can install the VirtualBox kernel module by running this command:

sudo aptitude install virtualbox-ose-modules-generic

or by searching for virtualbox-ose-modules-generic in Synaptic. Also, have you rebooted since trying to install the package? If not, reboot and give it a try or run this in a terminal:

sudo modprobe -a vboxdrv

---

