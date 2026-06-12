---
title: "Problems changing to 686 kernel...also nVidia drivers (edgy)"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by avinashv on 2006-11-28
I am a very new Ubuntu user (4 days), and spent the last three days fighting with my laptop to get it installed (there were some proprietary partitions), but it's all good now.

My laptop is a Toshiba Qosmio F15 AV 201, 1.8Ghz Centrino, 512MB RAM.

Right off the bat, I was told to upgrade to the linux-686 kernel, by typing ```
sudo apt-get install linux-686
```.

And I did...and nothing happened.  The GRUB bootlist wasn't modified, the new kernels weren't installed where they were meant to.  I checked a few different places for how to update the kernel, and this was all that I was meant to do.

The other problem is getting the nVidia drivers properly installed.  The laptop I am using has the nVidia GoFX5700, in the list of supported cards.

I've done the usual methods outlined everywhere (update linux-restricted modules, install nvidia-glx, run nvidia-xconfig), but every single time the booting process stalls and hangs at the nVidia graphic.  I tried to disable it (not really expecting much, ttytt), and it did not do anything.

I am fairly confident that the kernel I am using is the cause of this.

Any help would really be appreciated, thanks.

---

### Post by burwaco on 2006-11-28
root@box:/# **apt-cache search linux-image**
alsa-base - ALSA driver configuration files
linux-image-2.6.17-10-386 - Linux kernel image for version 2.6.17 on i386
linux-image-2.6.17-10-generic - Linux kernel image for version 2.6.17 on x86/x86_64
linux-image-2.6.17-10-server - Linux kernel image for version 2.6.17 on x86/x86_64
linux-image-2.6.17-10-server-bigiron - Linux kernel image for version 2.6.17 on BigIron Server Equipment
linux-image-386 - Linux kernel image on 386.
linux-image-686 - Obsoleted by: linux-image-generic
linux-image-debug-2.6.17-10-386 - Linux kernel debug image for version 2.6.17 on i386
linux-image-debug-2.6.17-10-generic - Linux kernel debug image for version 2.6.17 on x86/x86_64
linux-image-debug-2.6.17-10-server - Linux kernel debug image for version 2.6.17 on x86/x86_64
linux-image-debug-2.6.17-10-server-bigiron - Linux kernel debug image for version 2.6.17 on BigIron Server Equipment
linux-image-generic - Generic Linux kernel image
linux-image-k7 - Obsoleted by: linux-image-generic
linux-image-server - Linux kernel image on Server Equipment.
linux-image-server-bigiron - Linux kernel image on BigIron Server Equipment.
linux-686-smp - Obsoleted by: linux-image-generic
linux-image-kdump - Linux Kernel Crash Dump Image.
linux-image-2.6.15-26-686 - Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP
linux-image-2.6.15-27-386 - Linux kernel image for version 2.6.15 on 386.
linux-image-2.6.15-23-386 - Linux kernel image for version 2.6.15 on 386.
linux-image-2.6.15-26-386 - Linux kernel image for version 2.6.15 on 386.
linux-image-2.6.18.3-custom - Linux kernel binary image for version 2.6.18.3-custom
root@box:/# **apt-get install linux-image-2.6.17-10-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by avinashv on 2006-11-28
I don't understand--do I type this?  After entering the first one I only see a listing for the 386 kernel--I have a 686-compatible processor...

---

### Post by avinashv on 2006-11-28
Oh, and also, I thought the kernels to install were the "linux-686", or "linux-386".  The descriptions for the image said that the images shouldn't be installed, rather, the packages themselves should be installed.

Again, I am new to this.  If someone gives me a solution, I would really appreciate an explanation to why I've gone wrong so I learn from this.

---

### Post by civilian on 2006-11-28
I think its this line in particular that burwaco wanted you to see:

linux-686-smp - Obsoleted by: linux-image-generic

EDIT: meaning you would want to install linux-image-generic instead of linux-686-smp

---

### Post by avinashv on 2006-11-28
The default kernel installed when you start Ubuntu is "generic"--that means I am good to go?

OK, thanks!

Any solutions on the nVidia problems I have been having?

---

### Post by lingnoi on 2006-11-29
Is your nvidia problem related to the problem I have been having?

[https://bugs.launchpad.net/distros/ubuntu/+source/nvidia-kernel-common/+bug/71029](https://bugs.launchpad.net/distros/ubuntu/+source/nvidia-kernel-common/+bug/71029)

---

### Post by avinashv on 2006-11-29
Unfortunately not, sorry.

I got everything fixed though -- just did a reformat, followed some new guides, and hey presto, it was all good.

Thanks to those who helped.

---

