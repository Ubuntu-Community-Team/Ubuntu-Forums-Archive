---
title: "Ubuntu 10.04 internal sound Toshiba NB200"
date: 2010-05-18
forum: Hardware
---

### Post by djbenny on 2010-05-18
i updated the kernel last night and the sound started working!

updated from 2.6.32 to 2.6.34

thought it might help out some people

---

### Post by djbenny on 2010-05-19
> 32-bit users:

wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb)
sudo dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb linux-headers-2.6.34-020634_2.6.34-020634_all.deb linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb


64-bit users:

wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb)
sudo dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb linux-headers-2.6.34-020634_2.6.34-020634_all.deb linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) (Workaround D)

---

