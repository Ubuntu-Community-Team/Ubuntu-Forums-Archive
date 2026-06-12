---
title: "Repository Nvidia install"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by Nythain on 2007-04-11
So i switch from edgy to feisty this morning and i hear the nvidia-glx driver in the repository is a much more recent and stable (9755 i believe) so im like ill give installing the repo driver a second chance.

So, can anyone give me a list of the packages im gonna need to install... i know nvidia-glx-new but are there any others like nvidia-settings or nvidia-kernel-common or the likes???

---

### Post by Ekril on 2007-04-12
nvidia-glx - NVIDIA binary XFree86 4.x/X.Org driver
nvidia-kernel-common - NVIDIA binary kernel module common files
nvidia-xconfig - The NVIDIA X Configuration Tool
nvidia-kernel-2.6.20.4 - NVIDIA binary kernel module for Linux 2.6.20.4

I have installed these and it's 9755 now. But when i made a search i have seen nvidia-glx-new

i will give a try to it and make you know what it is. 


You may make packages search by typing "apt-cache search xyz" xyz is just some part of the search like a search term . for example for nvidia i wrote "apt-cache search nvidia" 

Take Care

---

### Post by Titus A Duxass on 2007-04-12
A simple "sudo apt-get install nvidia-glx" will pick up the other packages as well.

---

### Post by kerry_s on 2007-04-12
> **Nythain said:**
> So i switch from edgy to feisty this morning and i hear the nvidia-glx driver in the repository is a much more recent and stable (9755 i believe) so im like ill give installing the repo driver a second chance.

So, can anyone give me a list of the packages im gonna need to install... i know nvidia-glx-new but are there any others like nvidia-settings or nvidia-kernel-common or the likes???

Newer nvidia drivers have nvidia-settings and nvidia-xconfig built in. only the 7xxx you need to install the separate packages.

You need:
linux-restricted-modules-generic  <- install first
nvidia-glx-new <-check if your card is supported
else
nvidia-glx <-should be the same as you used in edgy

---

