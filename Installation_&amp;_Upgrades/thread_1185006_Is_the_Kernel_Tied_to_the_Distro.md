---
title: "Is the Kernel Tied to the Distro?"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by beastrace91 on 2009-06-11
My question in its simplest form is this - is the Kernel tied directly to the distro or is there a way I can use a different Kernel (other than the default) with a distro?

The reason I ask is because I would really like to install Ubuntu 9.04 on my G1Sn but there is an issue with the way the latest Kernel addresses memory that cause my graphics drivers to not work properly. I have a kernel patch that allows it to work for the 2.6.27.xx kernel but it does not work with the latest 2.6.28.xx (the one Jaunty uses) Is there a way I can use Jaunty with the older kernerl? I'd really love the boot time increases as well as the other features offered by Jaunty.

Thanks,
~Jeff

---

### Post by densou on 2009-06-11
yep, you can do it and that stuff is all avaiable on .deb packages! (daily bleeding-edge builds included!)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

you can install a new kernel using Gdebi (graphical way, just double-clicking) or Terminal (command line)

I'd recommend to use command line for my own taste :p ;)

e.g. wanna install final 2.6.30 kernel -32 bit version- ? Here you are what to *cut'n'paste* into your prompt:

```

wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
$ sudo dpkg -i linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb linux-headers-2.6.30-020630_2.6.30-020630_all.deb linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
```

---

### Post by beastrace91 on 2009-06-12
So that being said it would be safe to say I can install Jaunty and then build my 2.6.27 kernel to run on?

~Jeff

---

