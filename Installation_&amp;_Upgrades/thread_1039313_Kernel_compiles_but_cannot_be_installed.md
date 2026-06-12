---
title: "Kernel compiles but cannot be installed"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by boing0 on 2009-01-14
Hi there,
I googled a lot on this without any success. I hope you can help.
I am using a fresh installed Ubunto 8.10 on a Core2 Duo with 1 GB RAM.

Here is what I did:
```

sudo apt-get update
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
sudo apt-get install linux-source
cd ~
mkdir kernelpatching
cd kernelpatching
cp /usr/src/linux-source-2.6.27.tar.bz2 .
tar -xvf linux-source-2.6.27.tar.bz2
cd linux-source-2.6.27
make mrproper
//applied a kernel patch here
sudo cp /boot/config-`uname -r` ./.config
sudo make oldconfig
sudo make-kpkg clean
sudo fakeroot make-kpkg --initrd --append-to-version=-myKernel kernel_image kernel_headers
cd ..
ls -l
sudo dpkg -i linux-image-2.6.27.2-myKernel.Custom_i386.deb

```

I received the following error:
```

 trying to overwrite `/lib/firmware/whiteheat.fw', which is also in package linux-image-2.6.27.4-otherKernelIbuildEarlier

```
I could solve this by disabling Device Support -> USB -> USB Serial Converter Support.

I recompiled the kernel and when trying to install it, I get the following:
```

trying to overwrite `/lib/firmware/vicam/firmware.fw', which is also in package linux-image-2.6.27.4-otherKernelIbuildEarlier

```
Google is no help this time. I also don't see what this has to do with that other kernel I compiled, because I am not even running that one anymore...
```
uname -r
 2.6.27-7-generic
```

Thanks for any help!

---

### Post by boing0 on 2009-01-15
up

---

### Post by boing0 on 2009-01-15
I still dont quite understand why this is happening but I couls solve it by deinstalling the other kernel:

```

sudo dpkg --purge linux-image-myOtherKernel 

```

During a window popped open and asked something about grub. I did chose default, which was something like "keep current file".

I then could install the other Kernel, but dpkg did not update my  /boot/grub/menu.lst. So I copied one entry and changed it:

```

title		Ubuntu 8.10, myKernel
uuid		71364fbf-99b6-44c9-a8cf-bd26bff3417a
kernel		/boot/ vmlinuz-2.6.27.2-myKernel root=UUID=71364fbf-99b6-44c9-a8cf-bd26bff3417a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

```

But now the system does not start up:
```

Error 15 file not found

```

any ideas?

---

### Post by Kuraboy on 2009-04-06
Hi, I am also getting the same error when I install the dep pacakge, and this is also my second kernel compilation. Dose it mean you can't have more than one own compiled kernel?

---

