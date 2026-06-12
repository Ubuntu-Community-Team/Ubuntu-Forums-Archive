---
title: "Kernel and Video drivers..."
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Blackylol on 2009-10-22
So, I installed this kernel

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.4/)

all fine yes but, i wasnt able to install the driver for my nvidia video card using the easy way.... 

so i downloaded the drivers from nvidia site, tried to stop the X server to install them, but it was impossible I googled every single way and nothing. 

Restarted my pc and used the safe mode and logged as init 1 root. nvidia said something like it wasnt recomendable to install the drivers like that... but it was the only way for me to try it.

Then it asked for the nvidia kernel headers (or something like that) it didnt found any compatible in their ftp with my kernel... then tried to compile a whole kernel... and it was impossible aswell


I just want to upgrade my kernel to enable the force feedback in my g25 wheel, since it was added in kernel 2.6.30 ... i tried to compile my own kernel but it displayed many errors while compiling...

any idea of what can I do?

thanks.


my pc
Pentium 4 3.0 ht
mobo intel 865 glc
1gb ram
nvidia geforce 6600gt
ubuntu 9.04 jaunty
kernel 2.6.28 i think :p

---

### Post by cariboo on 2009-10-23
Make sure you have build-essential, it is in the repositories,  installed first before installing the nvidia binary drivers. Have a look at this [howto]("http://olearnfree.blogspot.com/2009/09/how-to-install-nvidia-driver-on-linux.html") for instruction on how to install the drivers.

---

