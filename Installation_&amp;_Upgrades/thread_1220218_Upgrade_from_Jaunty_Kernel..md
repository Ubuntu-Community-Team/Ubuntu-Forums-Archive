---
title: "Upgrade from Jaunty Kernel."
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by dArAzAc on 2009-07-22
I've fallen in love with Xubuntu 9.04 Jaunty, except that I get some pretty unbearable Kernel Panic with the default Jaunty Kernel. I'm wondering if I can just run ```
sudo apt-get kernel-image-x.x.x
``` to solve this. If so, what kernel version should I upgrade to? Kernel.org says that the current stable version is 2.6.30.2, is that compatible with Xubuntu 9.04? If so, does that kernel have a stable Real-Time version?

---

### Post by khelben1979 on 2009-07-22
The kenels which you see in Synaptic is supposed to be working with Ubuntu Jaunty, unless you've added other sources in your /etc/apt/sources.list file.

I think that if you need a really new kernel, you should probably go for Ubuntu Karmic instead. I have no experience with either Jaunty or Karmic myself, so I don't know what their standard kernels contains.

---

### Post by dArAzAc on 2009-07-22
Is there a way to install the Karmic Kernel into my current system?

---

### Post by khelben1979 on 2009-07-22
> **dArAzAc said:**
> Is there a way to install the Karmic Kernel into my current system?

If there is, I certainly wouldn't recommend it. Better to build your own.

[NixCraft Howto: Compile Linux kernel 2.6]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html").

---

### Post by dArAzAc on 2009-07-22
Alright, I think I'll just do a fresh install of Karmic, thanks for your help!

---

### Post by khelben1979 on 2009-07-22
> **dArAzAc said:**
> Alright, I think I'll just do a fresh install of Karmic, thanks for your help!

2.6.30-5.6 kernel based on 2.6.30-rc5 is what you're going to get if you go with [Karmic alpha 1]("http://www.ubuntu.com/testing/karmic/alpha1").

Good luck with it!

---

