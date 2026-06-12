---
title: "REQUEST: HOWTO on custom kernel compilation."
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by laggerzero on 2005-06-03
Ubuntu is the only distro that I have ever tried where I can not get a custom kernel to compile correctly. The closest I have been is getting the system to boot but the screen is still black.

If someone that has been able to apply the ubuntu patches to the latest kernel and get it to compile along with the initrd could post how they did it i would greatly appreciate it.

---

### Post by SnhKnives on 2005-06-03
[QUOTE=laggerzero]Ubuntu is the only distro that I have ever tried where I can not get a custom kernel to compile correctly. The closest I have been is getting the system to boot but the screen is still black.

If someone that has been able to apply the ubuntu patches to the latest kernel and get it to compile along with the initrd could post how they did it i would greatly appreciate it.[/QUOTE]

x2

---

### Post by laggerzero on 2005-06-10
anyone?

---

### Post by jrhodes on 2005-06-10
A standard debian HOWTO on the same topic should suit your purpose.

---

### Post by laggerzero on 2005-06-10
that doesn't work in ubuntu. The debian patches don't work and neither the ubuntu ones. As far as I know, I haven't heard of anyone compiling a successful kernel in ubuntu.

---

### Post by jrhodes on 2005-06-10
well you'd naturally have to change some things, but the general gist of the howto should still apply. 

Where are you getting your sources? Kernel.org or apt?

---

### Post by laggerzero on 2005-06-10
i'm getting them through apt. I've also tried the ones at kernel.org. none of them have worked

---

### Post by az on 2005-06-10
install fakeroot, build-essential, libncurses5-dev, linux-tree and kernel-package

Enter the source tree
fakeroot make menuconfig
fakeroot make-kpkg --revision=2 --appent-to-version=mycustomkernel kernel_image Kernel_headers
sudo dpkg -i (the kernel image you just created)

---

### Post by GilGalad on 2005-06-10
[QUOTE=azz]
fakeroot make-kpkg --revision=2 --appent-to-version=mycustomkernel kernel_image Kernel_headers
sudo dpkg -i (the kernel image you just created)[/QUOTE]

If you do it in the debian way, using make-kpkg it creates some packages called kernel-*deb instead of linux-*.deb which is how the kernel images are called in Ubuntu. However it works except for...

[QUOTE=laggerzero]The closest I have been is getting the system to boot but the screen is still black.
[/QUOTE]

You need to copy the vesafb.ko module into /lib/modules/<kernel version>/initrd/ and then run mkinitrd again.

---

### Post by az on 2005-06-10
[QUOTE=GilGalad]If you do it in the debian way, using make-kpkg it creates some packages called kernel-*deb instead of linux-*.deb which is how the kernel images are called in Ubuntu. However it works except for...



You need to copy the vesafb.ko module into /lib/modules/<kernel version>/initrd/ and then run mkinitrd again.[/QUOTE]


You are making a custom kernel.  You do not need it to match the ubuntu stock kernel name.

Also, instead of copyinf the modules, why not just edit mkinitrd.conf in /etc/mkinitrd and not have to do it by hand everytime?

---

### Post by bjrnfrdnnd on 2005-06-18
I tried to follow the steps in [https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28kernel%29](https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28kernel%29)
and therefore, I ran 
make-kpkg --initrd --stem linux --revision=custom.1.0 kernel_image

for my new custom 2.6.11 kernel.


Alas, on reboot, the screen is dark.

There is no vesafb.ko module, and no /lib/modules/<kernel version>/initrd directory!

---

