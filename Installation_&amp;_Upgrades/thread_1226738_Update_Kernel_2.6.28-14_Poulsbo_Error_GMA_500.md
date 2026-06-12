---
title: "Update Kernel 2.6.28-14 Poulsbo Error GMA 500"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by gypsumwolf on 2009-07-29
I have a Dell Mini 10 running Xubuntu.

After Xubuntu updated it had a Poulsbo error and would not use the Intel driver. I had to step back to Kernel 2.6.28-13 instead of use the newer 2.6.28-14. Did anyone with Ubuntu (or variant) get this error?

I commented out the newer kernel in grub so it just boots the *13 Kernel and it works like normal.

---

### Post by JasenGroves on 2009-07-29
> **gypsumwolf said:**
> I have a Dell Mini 10 running Xubuntu.

After Xubuntu updated it had a Poulsbo error and would not use the Intel driver. I had to step back to Kernel 2.6.28-13 instead of use the newer 2.6.28-14. Did anyone with Ubuntu (or variant) get this error?

I commented out the newer kernel in grub so it just boots the *13 Kernel and it works like normal.

By no way am I right about how I did this... But somehow it worked...

I had the error that xpsb wouldn't load and went through the options several times. So in frustration, I went into Synaptic, searched for "PSB" and completely removed anything highlighted as installed... rebooted into kernel *.14's limited display and installed the psb kernel header, kernel source, firmware, modules, xpsb, and then rebooted into kernel *.14's limited display and then installed the xserver-xorg-video-psb last... rebooted and then it worked... 

I should point out that all the packages I found were from searching Synaptic for "PSB".

But, seriously, my method was hit-or-miss, and I kind of Homer-Simpsoned it. But somehow it worked...

---

### Post by pahautane on 2009-07-30
I had the same problem, however, I also remembered that when I installed the psb-kernel-source package it compiled for my currently installed kernel (2.6.28-13). So I took a stab in the dark and guessed that I needed to reinstall the psb-kernel-source package so that it would compile for the new kernel. I was able to get things working by doing the following:

1. Boot to the 2.6.28-14 kernel.
2. When you encounter the error switch to a command prompt.
3. Remove the psb-kernel-source package:
```
sudo apt-get remove psb-kernel-source
```
4. Reinstall the psb-kernel-source package:
```
sudo apt-get install psb-kernel-source
```
5. Restart:
```
sudo shutdown -r now
```
6. Boot to the 2.6.28-14 kernel and everything should work.

WARNING:
Note that if this doesn't work you may now have a broken psb-kernel-source package for the old kernel. You should be able to repeat the process above but boot to 2.6.28-13 in step 1 to get the old kernel working again. However, I haven't tested this so I can't guarantee that it will work.

Hope that helps.
Cheers

---

### Post by Lifer999 on 2009-07-30
Thanks for this.  It worked fine for my Dell Mini12.

---

### Post by JasenGroves on 2009-07-30
> **pahautane said:**
> I had the same problem, however, I also remembered that when I installed the psb-kernel-source package it compiled for my currently installed kernel (2.6.28-13). So I took a stab in the dark and guessed that I needed to reinstall the psb-kernel-source package so that it would compile for the new kernel. I was able to get things working by doing the following:

1. Boot to the 2.6.28-14 kernel.
2. When you encounter the error switch to a command prompt.
3. Remove the psb-kernel-source package:
```
sudo apt-get remove psb-kernel-source
```
4. Reinstall the psb-kernel-source package:
```
sudo apt-get install psb-kernel-source
```
5. Restart:
```
sudo shutdown -r now
```
6. Boot to the 2.6.28-14 kernel and everything should work.

WARNING:
Note that if this doesn't work you may now have a broken psb-kernel-source package for the old kernel. You should be able to repeat the process above but boot to 2.6.28-13 in step 1 to get the old kernel working again. However, I haven't tested this so I can't guarantee that it will work.

Hope that helps.
Cheers

Sooo.... what you're saying is I had gone through just a few unnecessary steps? :D I'm glad someone out there followed up to make sure we're doing right, thanks!

---

