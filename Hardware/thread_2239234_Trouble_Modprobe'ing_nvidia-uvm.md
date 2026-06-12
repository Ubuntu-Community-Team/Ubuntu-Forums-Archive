---
title: "Trouble Modprobe'ing nvidia-uvm"
date: 2014-08-12
forum: Hardware
---

### Post by bravech on 2014-08-12
I installed the Nvidia 340 driver from the xorg-edgers ppa, then installed CUDA 6.5RC, since I run 14.04, and after many failed attempts, I decided to try this route. When I run 
```
sudo modprobe nvidia
```
it works fine, but when I run
```
sudo modprobe nvidia-uvm
```
it throws this error
```
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_340_uvm'
modprobe: ERROR: could not insert 'nvidia_340_uvm': Function not implemented
```
My graphics card is an Nvdia GTX 750 Ti. This is being installed on a fresh version of Ubuntu 14.04.

---

### Post by bravech on 2014-08-12
Solved!
After adding the xorg-edgers ppa, install nvidia-340-uvm through apt-get.

---

### Post by Laryssa_Seabra on 2015-01-29
Worked for me, too. Thanks!

---

