---
title: "Please help!!! Virtual Box"
date: 2008-08-12
forum: General Help
---

### Post by justjohn924 on 2008-08-12
So i've installed virtualbox but every time I try to start the install for my xp guest os I get an error saying there is no kernel so I tried to run it in terminal as root and I get this. Someone please tell me what to do!


tannerandjohn@tannerandjohn-desktop:~$ sudo virtualbox
[sudo] password for tannerandjohn:
WARNING: The character device /dev/vboxdrv does not exist.
         Please install the virtualbox-ose-modules package for your kernel.

         You will not be able to start VMs until this problem is fixed.
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device

---

### Post by justjohn924 on 2008-08-12
Also if it helps I already have user preference set to vboxusr 

and I've installed virtualbox-ose-modules-server

I also tried virtualbox-ose-modules-generic but neither work

---

### Post by airjrdn on 2008-08-12
I got it working using this guide:

[http://ph.ubuntuforums.com/showthread.php?t=770745](http://ph.ubuntuforums.com/showthread.php?t=770745)

---

### Post by damis648 on 2008-08-12
Go into synaptic and install virtualbox-ose-modules for the kernel you are currently running. Then in terminal:
```
sudo modprobe vboxdrv
```
and try again.

PS. Do not run virtualbox as root (with sudo). Simply use
```
virtualbox
```
in terminal.

---

