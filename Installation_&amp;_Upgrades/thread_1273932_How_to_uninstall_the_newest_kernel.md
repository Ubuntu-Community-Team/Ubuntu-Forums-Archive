---
title: "How to uninstall the newest kernel?"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by joseantmm on 2009-09-23
Suddenly I couldn't boot from the usual kernel in Ubuntu 9.04 64-bit and am now using an older one. I would like to reinstall the newer one.

In Synaptic I see the following packages installed:

linux-headers-2.6.28-15
linux-headers-2.6.28-15-generic
linux-image-2.6.28-15-generic
linux-restricted-modules-2.6.28-15-generic

linux-image-2.6.28-11-generic
linux-restricted-modules-2.6.28-11-generic

I have noticed that the older packages have no dependencies. But they are the ones in use. However, if I try to uninstall all the newer version packages, Synaptic will also uninstall:

linux-headers
linux-headers-generic
linux-image-generic
linux-restricted-modules-generic
dkms

How should I reinstall the new kernel in order to make it work? Which 2.6.28-15 packages do I have to remove and how? 

Thanks so much,

---

### Post by sgosnell on 2009-09-23
If you have the .15 kernel as a .deb, just open it with gdebi and install it.  You can get .deb files of all current kernels [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  Personally, I like the 2.6.30 kernel, but if you want to stay with the 2.6.28, it's up to you.  You should be able to go to the appropriate folder in the link, click on the .deb file you want, and download it.  Depending on your browser settings, you may get a choice to save or open it.  You can do it either way, your choice.  

If you want to do it via Synaptic, just find the .15 kernel, click on it, and select Mark for Installation, then Apply.  That should do it for you.  You shouldn't have to remove anything.  Just be aware that you can't make any changes to the kernel you currently have booted.  Boot to an older kernel, then you can change what you like with the newer one(s).

---

### Post by scragar on 2009-09-23
```
sudo apt-get --reinstall install linux-headers-2.6.28-15 linux-headers-2.6.28-15-generic linux-image-2.6.28-15-generic linux-restricted-modules-2.6.28-15-generic
```

---

### Post by joseantmm on 2009-09-24
I actually just enabled the jaunty-proposed repository and updated the newer kernel. 

I would have liked to update to the .30 kernel but I am too much of a newbie to know the benefits / risks.

Thanks so much for your prompt replies.

---

### Post by sgosnell on 2009-09-24
The benefit is that everything works out of the box, at least on my EEE, and everything seems to be much snappier.  I haven't seen any downside.  If a kernel gives you problems, you can always boot from any other you have installed.  That's why I always keep at least two installed, sometimes more.  I like to try out new kernels, and having a known good one in the grub system lets me revert when one doesn't work.  The .31 kernel won't boot on an EEE PC, and I found that out by trying it.  When it didn't, I just booted from the .30 kernel and removed it.  I still have high hopes for the .31 kernel, which is supposed to run browsers and other software much more efficiently, thus faster.  The .30 does it pretty well for me.

---

