---
title: "Install kernel 2.6.29 on Ubuntu 8.10 kernel 2.6.27"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by ShanshanZg on 2009-06-12
Hi Everyone, 
My current system is Ubuntu 8.10 64 bit kernel 2.6.27. I installed kernel 2.6.29. I did this by following an instruction from someone's blog:
# Download [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629_2.6.29-020629_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629_2.6.29-020629_all.deb)
# Download your kernel headers packe;
I386:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_i386.deb)
AMD64: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_amd64.deb)
# Download your kernel compile;
I386:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb)
AMD64: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_amd64.deb)
# Install the files in the same order as mentions above.

The installation went well. I rebooted, but didn't see the new kernel listed on the boot menu. 

I further checked the installed kernels;
shanshan@maui:~$ dpkg --list | grep linux-image
ii  linux-image-2.6.27-7-generic              2.6.27-7.14                           Linux kernel image for version 2.6.27 on x86
ii  linux-image-2.6.29-020629-generic         2.6.29-020629                         Linux kernel image for version 2.6.29 on x86
ii  linux-image-generic                       2.6.27.7.11                           Generic Linux kernel image

Is the new kernel installed or not? What am I still missing? How can I boot into the new kernel?
Thank you,
Shanshan

---

