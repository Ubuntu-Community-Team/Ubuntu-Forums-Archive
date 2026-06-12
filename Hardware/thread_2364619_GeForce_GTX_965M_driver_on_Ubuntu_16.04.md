---
title: "GeForce GTX 965M driver on Ubuntu 16.04"
date: 2017-06-25
forum: Hardware
---

### Post by msd-ataei on 2017-06-25
Hi guys,

I have nvidia gpu GeForce GTX 965M on my laptop with Ubuntu 16.04 operating system. Here is the output of uname -a:

Linux Gigabyte-Aero-14 4.4.0-81-generic #104-Ubuntu SMP Wed Jun 14 08:17:06 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

here is the gpu info from lspci:
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 965M] (rev a1)

I used to manage to install the driver (I think nvidia-375) and my GPU was perfectly working. I was able to run my cuda kernels on my gpu. I don't know what I did that I lost my driver. I installed it again in TTY using:

sudo service lightdm stop
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-375

But it gives an error and says it cannot be installed! Here is the error from make.log

##########################
DKMS make.log for nvidia-375-375.66 for kernel 4.4.0-81-generic (x86_64)
Sun Jun 25 14:51:31 EDT 2017
make "CC=cc"  KBUILD_VERBOSE= -C /lib/modules/4.4.0-81-generic/build M=/var/lib/dkms/nvidia-375/375.66/build ARCH=x86_64 NV_KERNEL_SOURCES=/lib/modules/4.4.0-81-generic/build NV_KERNEL_OUTPUT=/lib/modules/4.4.0-81-generic/build NV_KERNEL_MODULES="nvidia nvidia-uvm nvidia-modeset nvidia-drm" INSTALL_MOD_DIR=kernel/drivers/video modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-81-generic'
Makefile:693: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler
  SYMLINK /var/lib/dkms/nvidia-375/375.66/build/nvidia/nv-kernel.o
  SYMLINK /var/lib/dkms/nvidia-375/375.66/build/nvidia-modeset/nv-modeset-kernel.o
.
.
.
###########################################

It seems it is a compiler error. I checked with gcc-4.8, gcc-5.3 and gcc-6 all gives me same error. I have exactly same error when I download driver from nvidia website and try to install it. Anyone has an idea? Thanks.

---

### Post by ajlongstreet on 2017-06-26
Did you try downloading from NVidia?

---

### Post by QIII on 2017-06-26
Before we send the OP trekking off again (as he said he has done) to download something from Nvidia that may be just as inscrutable, why don't we let the community have a chance to help with what he has going on right now?

---

### Post by msd-ataei on 2017-06-30
Thank you for your replies.

I realised this is the compiler issue. The only version of compiler doesn't give me any error is "gcc-4.9".

I have ubuntu 16.04 with kernek 4.4 and I was able to install nvidia-340. It is a little bit weird because I should be able to install nvidia-375 on ubuntu 16.04 (based on what people said in forums). But when I install nvidia-375 and reboot my laptop. I cannot log in. The login page doesn't show up and the screen is all black. At this point, I have no choice except to push Ctrl+Alt+F2 and uninstall nvidia-375.

---

### Post by Autodave on 2017-06-30
Assuming that you are running a 64 bit Linux, according to Nvidia's website 378 should work. You may want to give that a try. I am currently using the 378 driver with no problem.

Another thing you could also try is booting with your 340 installed and then going to ADDITIONAL DRIVERS and seeing what it recommends and try that driver.

---

