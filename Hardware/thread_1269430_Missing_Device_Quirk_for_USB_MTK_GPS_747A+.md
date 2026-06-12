---
title: "Missing Device Quirk for USB MTK GPS 747A+"
date: 2009-09-18
forum: Hardware
---

### Post by ode on 2009-09-18
Hi, I have just bought a MTK GPS 747A+ device. It doesn't seem to be supported in the 2.6.28 kernel which is included in Jaunty.

I've read it is fixed in 2.6.29 in [this BT747.org forum post](http://www.bt747.org/de/node/223) and it gives a [link to Kerneltrap.org](https://kerneltrap.org/mailarchive/git-commits-head/2009/1/28/4833594) containing a kernel patch.

I don't really want to upgrade to 9.10 yet or recompile the kernel. Is it possible to just add the relevant lines from the Kerneltrap post the current file on my system?

Thanks

---

### Post by ode on 2009-09-19
From reading around I found a various guides where I discovered how to modify and recompile the module.

I wasn't sure which dependencies I needed to make the module but I got all the stuff from [Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) page of the documentation.
```

sudo apt-get install fakeroot build-essential makedumpfile
sudo apt-get build-dep linux

```
Make a directory to download the kernel source to.
```

mkdir modbuild
cd modbuild

```
Get the build dependencies for the kernel and download the source. 
```
sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)

```
I followed the [recipe from Martin Pitt](https://wiki.ubuntu.com/KernelCustomBuild) in the comments of the KernelCustomBuild page of the Ubuntu Wiki.
**N.B. Download the patch file that is attached to this post to the working directory.**
Now need to patch the file, make and install the modules and run depmod.
```

tar -C linux-2.6.28/drivers/usb/class/ -xvf cdc-acm.patch.tar.gz
cd linux-2.6.28/drivers/usb/class/
patch < cdc-acm.patch
make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install

```
One thing that did not work for me was the install stage. It installed the newly compiled module in the wrong directory and left the old one in place.
To fix this run the below command.
```

sudo mv /lib/modules/2.6.28-*-generic/extra/* /lib/modules/2.6.28-*-generic/kernel/drivers/usb/class/

```
Finally run the last stage of the Martin's recipe.
```

sudo depmod -a

```

---

