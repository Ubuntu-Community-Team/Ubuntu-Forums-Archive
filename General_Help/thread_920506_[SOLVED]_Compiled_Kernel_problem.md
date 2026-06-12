---
title: "[SOLVED] Compiled Kernel problem"
date: 2008-09-15
forum: General Help
---

### Post by alberto ferreira on 2008-09-15
I use Ubuntu 8.04 with no problems at all but I want to use a compiled kernel to see some performance boost :D

Hardware:
CPU:AMD Opteron 146
Graphic Card:Nvidia 7600GT
MB:Asus A8N-SLI Premium

Current kernel:2.6.24-16-generic

Compiling the kernel --- I don't know if I am doing everything right:

1-Install tools:
$sudo apt-get update
$sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

2-Get the Kernel source:
$cd ~/src ---> Is this folder ok? or I have to do this in /usr/src ?
$wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.1.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.1.tar.bz2)
     2.1-Decompress source:
     tar xjf linux-2.6.18.1.tar.bz2
     ln -s linux-2.6.18.1 linux
     cd ./linux 

############################################
3-Should I have updated the source? Compiling a kernel with a different version from the standard and current one creates problems?
---
Then I could have patched the source but I didn't, so, the kernel I compiled is the 2.6.18.1 and the kernel that I'm currently using is the standard one that comes with Ubuntu 8.04 (2.6.24-16-generic).
############################################

4-Kernel configuration:
cp /boot/config-`uname -r` ./.config
make menuconfig --> There I removed useless things for me like CPU frequency control support...

5-Compilation:
sudo make-kpkg clean
sudo fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 

After the .deb packages are created, I install both (the image and the headers), then I run: 
$sudo update-grub

After that I boot the system selecting the new kernel and then I get this:

Starting up...
Uncompressing Linux... Ok, booting the kernel.

But then, nothing happens, I waited 5 minutes and it just stays there. What is wrong?





Thanks

---

### Post by drs305 on 2008-09-15
Just a couple of observations. Kernel 19 is the latest recommended kernel in synaptic, so you might want to try updating to it.

I have a similar system to yours and used this thread to do my compilation of kernel 26. Saying the thread is a bit long is an understatement but the first post provides the steps and it went well for me.
[Master Kernel Thread ]("http://ubuntuforums.org/showthread.php?t=311158")

To make things a little simpler, there is also the kernelcheck app which helps automate certain aspects of the kernel build.
[HowTo: Installing and using KernelCheck  ]("http://ubuntuforums.org/showthread.php?t=618563")

---

