---
title: "Ubuntu 10.10 &amp; ATI Radeon Mobility X1600 (M56P)"
date: 2010-10-10
forum: Hardware
---

### Post by zipeppe on 2010-10-10
Hi,

my laptop ASUS A6J-Q008 won't use ATI proprietary drivers, while it works using the **X.Org X server AMD/ATI Radeon display driver** .

No errors when tried to install **fglrx** by Synaptic Package Manager, but after the 1st reboot the module doesn't load properly:

```

[   98.497804] fgl_glxgears[1706]: segfault at 4 ip 009fa5a0 sp bf813a1c error 4 in libGL.so.1.2[98d000+b4000]
[  109.899607] fglrxinfo[1707]: segfault at 4 ip 005295a0 sp bfc27f9c error 4 in libGL.so.1.2[4bc000+b4000]
[  153.157190] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  153.157200] Disabling lock debugging due to kernel taint
[  153.335928] [fglrx] Maximum main memory to use for locked dma buffers: 1885 MBytes.
[  153.336652] [fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
[  153.336658] [fglrx:firegl_init_module] *ERROR* firegl_init_devices failed

```

Any idea to install and use proprietary AMD/ATI driver for such a videocard?

Thanks

---

### Post by Confused Computer User on 2010-11-28
Hi Zipeppe,

I have the same card minus the mobility part. I'm running Ubuntu 10.04 on it. Believe me when I say say that i had one heck of a time getting this card to run compiz. The effects were choppy and even minimizing windows seemed to take forever when special effects were on. If you have experienced similar problems then I'd recommend reading this thread:

[http://ubuntuforums.org/showthread.php?t=1473104](http://ubuntuforums.org/showthread.php?t=1473104)

The solution for me, to save you time was:
> **Temüjin said:**
> ```
gksu gedit /etc/modprobe.d/radeon-kms.conf
```
Copy/paste:
```
options radeon modeset=0
```
Save. Quit. Restart.



The problem is that the X1600 is not supported by the ATI proprietary driver. I believe that Catalyst 9.3 was the last Catalyst release to feature support for the X1600. But two points come up:

> **ssri said:**
> 1) Catalyst 9.3 will only work with Xserver v1.5.2, not v1.6.x and above.  So, you may have to downgrade your Xserver ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue))

2) Catalyst 9.3 only supports kernels 2.6.28 and below.  There is a patch for 2.6.29 [([http://aur.archlinux.org/packages.php?ID=25105](http://aur.archlinux.org/packages.php?ID=25105));([http://www.linuxquestions.org/questions/linux-hardware-18/fglrx-9.3-patch-for-2.6.29.x-kernel-722858/](http://www.linuxquestions.org/questions/linux-hardware-18/fglrx-9.3-patch-for-2.6.29.x-kernel-722858/))].  In short, best to stick with the opensource drivers for your environment.


Hope this helps...

---

### Post by Fafler on 2010-11-28
The only way to make the x1600 work with the Catalyst drivers is to install the last version of Ubuntu that comes with the old compatible X server. I think it's 8.10.

If you can still boot, just uninstall and go back to the open source driver. Do you have any specific problems with it, you need to solve?

---

### Post by Confused Computer User on 2010-11-28
Update:

I did a clean install of Ubuntu 10.04. I later added the ATI X1600 card without any modifications.... It worked right away with the open drivers. So I'm not sure how things might change from 10.04 to 10.10 since i'm a newb but one thing is certain. You are better off with the open drivers than the proprietary one for this model and brand of video card.

Cheers.

---

