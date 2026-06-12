---
title: "8GB of RAM and nvidia drivers"
date: 2008-09-29
forum: General Help
---

### Post by rafelamer on 2008-09-29
Hi,

I have installed Ubuntu 8.04 on my new PC (Intel Quad Core with 8GB of RAM).
I I run the linux-image-2.6.24-19-(generic|i386) kernel only 3.5 GB of RAM are detected and if I run the linux-image-2.6.24-19-(server|openvz) the 8 GB of RAM are detected, but I can't install the Nvidia driver (173.14.12).

The Nvidia driver runs fine with the generic|i386 kernel.

Does anybody knows how I can run the Nvdia driver and the kernel detects all the RAM?

Thanks in advance.

Rafel Amer
Thecnic University of Catalonia

---

### Post by wolfen69 on 2008-09-29
the 32bit version of ubuntu will not see more than 3.5gb. you will need to install the 64bit version of ubuntu for it to utilize all your ram.

---

### Post by jordilin on 2008-09-29
> **rafelamer said:**
> Hi,

I have installed Ubuntu 8.04 on my new PC (Intel Quad Core with 8GB of RAM).
I I run the linux-image-2.6.24-19-(generic|i386) kernel only 3.5 GB of RAM are detected and if I run the linux-image-2.6.24-19-(server|openvz) the 8 GB of RAM are detected, but I can't install the Nvidia driver (173.14.12).
Rafel Amer
Thecnic University of Catalonia

Intel Quad Core? I would download 64bit version and you will be able to use all these resources

---

### Post by cariboo on 2008-09-29
The sever release of Ubuntu isn't meant to have a gui, If you want to use the server release you will have to complie the driver for your video card. A much better alternative would be to use he x86-64 desktop release.

Jim

---

### Post by bawilson2 on 2008-09-29
You'll need to make sure you're using the 64 bit version of the driver. 


Here's the 173.14.12 version:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/NVIDIA-Linux-x86_64-173.14.12-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/NVIDIA-Linux-x86_64-173.14.12-pkg2.run)

I've had a whole lot more luck using the beta 177.67 drivers:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/177.67/NVIDIA-Linux-x86_64-177.67-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/177.67/NVIDIA-Linux-x86_64-177.67-pkg2.run)

The choice is yours!

---

