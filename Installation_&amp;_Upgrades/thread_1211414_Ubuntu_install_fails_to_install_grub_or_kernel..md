---
title: "Ubuntu install fails to install grub or kernel."
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by MrUmunhum on 2009-07-12
Hi group,

  I have a Fujitsu Lifebook that I am attemping to install Ubuntu 9.04 on. The install runs most of the way but does not install the kernel or grub, so I can't boot the new system to fix anything. I have tried the install 3 times with the same results. All the installs failed at the same place. It drops out of the install and tries to report the error. Not sure if the report made it back to the support group.

  I then tried to chroot the /target file system and run apt-get to install grub, that worked but the same method failed to install the kernel, 'apt-get install kernel-packages'.  

  I have Fedora Core 10 installed on this laptop but it is giving me troubles with building OpenWRT so I want to try Ubuntu.

Bottom line, how can I get the kernel installed using the install CD??

---

### Post by coffeecat on 2009-07-12
Chrooting sounds like the way to go, but I think this is where you went wrong with the kernel.

> **MrUmunhum said:**
>  but the same method failed to install the kernel, 'apt-get install kernel-packages'. 

According to Synaptic, kernel-package (no 's') is a utility for building your own kernel. If you want the stock Ubuntu kernel you need a different set of packages. I've had a look in Synaptic to see which packages I've got installed (in Jaunty), and if you apt-get install the following lot in a chroot environment, it should do the trick.

linux-generic
linux-image-generic
linux-headers
linux-headers-generic
linux-restricted-modules-generic
linux-restricted-modules-common

... and for good measure....

linux-firmware

To be honest, you may not have to apt-get all those - some may depend on others - and some are metapackages which will bring in specific versions of the kernel, headers, etc. I'm not sure which are the key packages, but you won't do any harm apt-getting the lot.

---

### Post by MrUmunhum on 2009-07-12
> **coffeecat said:**
> Chrooting sounds like the way to go, but I think this is where you went wrong with the kernel.



According to Synaptic, kernel-package (no 's') is a utility for building your own kernel. If you want the stock Ubuntu kernel you need a different set of packages. I've had a look in Synaptic to see which packages I've got installed (in Jaunty), and if you apt-get install the following lot in a chroot environment, it should do the trick.

linux-generic
linux-image-generic
linux-headers
linux-headers-generic
linux-restricted-modules-generic
linux-restricted-modules-common

... and for good measure....

linux-firmware

To be honest, you may not have to apt-get all those - some may depend on others - and some are metapackages which will bring in specific versions of the kernel, headers, etc. I'm not sure which are the key packages, but you won't do any harm apt-getting the lot.

Thanks for your answer. I did manage to get it fixed with 
'apt-get install linux-386'
It did all the magic for me, install kernel and create initrd.img.

Pretty nice.

Thanks for your time.

---

