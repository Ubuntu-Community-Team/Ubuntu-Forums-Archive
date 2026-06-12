---
title: "increase performance with low-latency kernel"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by akatopaz on 2009-05-09
Hi all !
After testing the newly released jalopy, I've been annoyed by the poor responsiveness under X. I remembered I used to install low-latency kernel version. And surprisingly there are not available anymore for jalopy.

Before any details, here are the packages compiled for those how don't want to compile the kernel yourself :
[http://akatopaz.free.fr/ubuntu/kernel-low-latency](http://akatopaz.free.fr/ubuntu/kernel-low-latency)
You'll just need to download files and the do a 
```

sudo dpkg -i *.deb

```on downloaded files.

I've thus recompiled this low latency kernel.
```

apt-get install linux-source-2.6.28 kernel-package build-essentials
cd /usr/src
tar zxvf linux-source-2.6.28.tar.gz
cd linux-source-2.6.28
cp /boot/`uname -r`/config-* .config
make menuconfig
> ticked preemtible kernel
> unticked generic x86
> ticked core 2
> ticked 1000hz frequency for system tick
export CONCURRENCY_LEVEL=4
make-kpkg --stem linux --bzimage --revision="0" --append-to-version="-low-latency" --initrd kernel_image kernel_headers
cd ..

```Then install generated packages (headers and image).
```

dpkg -i linux-*.deb

```then after compilation, I've just had troubles with nvidia under DPMS that reported "error 20"


Hopes it increases your ubuntu experience :)
Topaz.

---

### Post by akatopaz on 2009-05-09
I'm currently uploading files, please wait 'til 3-4 pm before downloading files ...

---

