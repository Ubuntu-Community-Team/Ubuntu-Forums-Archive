---
title: "confused about linux source,image,headers ?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by alimahmoudy on 2009-04-24
Hello.
In my /usr/src directory, i have 3 folders

linux-headers-2.6.24-23-generic
linux-headers-2.6.24-23
linux-2.6.24

I've been trying to apply a patch, and i need to download the linux source as i've read.
Could someone explain what that means ?

And by using the command

```
sudo apt-get source linux-image-$(uname -r)
```

I would download the source as it says in the tutorial ? or i already have it and it's the linux-2.6.24 folder ??

I would appreciate if someone clarifies what source,image and headers are :S thanks alot

---

### Post by alimahmoudy on 2009-04-24
anyone :S ?

---

### Post by echo6 on 2009-04-25
uname -r places into the command line argument your currently running kernel version, therefore fetches the correct kernel source.  The Linux headers is partial kernel source code required to build additional modules/drivers for your running kernel, without requiring the full linux kernel source code.

linux-2.6.24 looks like a good candidate for your kernel source tree, you should be able to cd into it and "make menuconfig" providing you have the correct dependencies installed, usually libncurses5-dev kernel-package and build-essential.

---

