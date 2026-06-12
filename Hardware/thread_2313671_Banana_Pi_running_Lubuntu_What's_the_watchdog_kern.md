---
title: "Banana Pi running Lubuntu: What's the watchdog kernel module I'd need?"
date: 2016-02-14
forum: Hardware
---

### Post by timonoj on 2016-02-14
Hi guys,

I have a BananaPi running a rather heavy java task that seems to leak ram after a while, effectively hanging my BananaPi after some days. I have to then manually reboot it whenever I get back home, but I'd like it to just reboot on its own. I'm trying to set up the watchdog to avoid this, but I just saw I'd need to set up a kernel module in order to actually get the system to talk to the banana's hardware watchdog. How can I do this? What module is it, and how can I get it? Thanks a lot!

EDIT: Just checking the Kernel version, I'm a bit confused:
```

~$ dpkg -l | grep linux-image
ii  linux-image-3.1.10-6-ac100            3.1.10-6.10                             armhf        Linux kernel image for version 3.1.10 on Toshiba AC100-based systems
ii  linux-image-ac100                     3.1.10.6.2                              armhf        Linux kernel image for the ac100 architecture.

```the 

However I can see several linux-image-4.2.0-XX. Since these images don't boot from GRUB, I'm wondering how much trouble would it be to update the kernel to a more recent one?

Thanks!

---

### Post by J_Me on 2016-02-15
I'm not familiar with watchdog but this may help.[br]1[/br] [br]1[/br] To get a list of available modules run[br]1[/br] ~$ lsmod[br]1[/br] The third column will tell you the state of the module (Anything other than 0 means it's already active)   > However I can see several linux-image-4.2.0-XX. Where do you see this information, is it when you run '~$ dpkg -l | grep linux-image'. The 'ii' next to the kernel number means that the kernel is usable and 'rc' means it's been removed.[br]1[/br] [br]1[/br] To see the current kernel your using run[br]1[/br] ~$ uname -r[br]1[/br]

---

### Post by timonoj on 2016-02-15
Thanks for the help. However I don't think any of the disabled modules will help regarding watchdog, seems it might be missing :(
```

$ lsmod
Module                  Size  Used by
xt_multiport            2443  2 
iptable_filter          1493  1 
ip_tables              12937  1 iptable_filter
x_tables               17443  3 ip_tables,xt_multiport,iptable_filter
dm_crypt               16206  0 
rfcomm                 58241  0 
bnep                   14217  2 
bluetooth             264645  10 bnep,rfcomm
mali_drm                2608  0 
drm                   209226  1 mali_drm
mali                  111427  0 
ump                    52415  1 mali
nfsd                  227870  2 

```

Sorry I was not very specific, the place I see several linux-image-4.2.0-xx is on the repository:
```

$ apt-cache search linux-image
[...]
linux-image-3.19.0-49-generic-lpae - Linux kernel image for version 3.19.0 on ARM (hard float) SMP
linux-image-4.2.0-18-generic - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-18-generic-lpae - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-19-generic - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-19-generic-lpae - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-21-generic - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-21-generic-lpae - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-22-generic - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-22-generic-lpae - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-23-generic - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-23-generic-lpae - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-25-generic - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-25-generic-lpae - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-27-generic - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-4.2.0-27-generic-lpae - Linux kernel image for version 4.2.0 on ARM (hard float) SMP
linux-image-generic-lpae-lts-utopic - Generic Linux kernel image
linux-image-generic-lpae-lts-vivid - Generic Linux kernel image
linux-image-generic-lpae-lts-wily - Generic Linux kernel image
linux-image-keystone - Generic Linux kernel image
linux-image-3.13.0-5-exynos5 - Linux kernel image for version 3.13.0 on ARM (hard float) SMP
linux-image-ac100 - Linux kernel image for the ac100 architecture.
linux-image-3.1.10-6-ac100 - Linux kernel image for version 3.1.10 on Toshiba AC100-based systems

```

I was just wondering if I could go install a newer kernel of those listed, or will that turn my banana unbootable. After all I'm not so familiar with this flash based booting, just with grub. That still won't fix my problems with watchdog, anyway...I'd like to find a way to get a hardware watchdog enabled kernel...but not sure how to do that.

Oh, by the way:
```

$ uname -a
Linux TimoPi 3.4.103 #1 SMP PREEMPT Thu Dec 18 13:07:12 CST 2014 armv7l armv7l armv7l GNU/Linux

```

---

### Post by J_Me on 2016-02-16
> I was just wondering if I could go install a newer kernel of those listed, or will that turn my banana unbootable.  I don't see why not but then again you really should be making periodic backup's of your original sdcard anyway, so you always have a known good state to work from if things go bad. I've been using dd to do this for a long while now but I still have a ritual I go through every time just because it's so hazardous not only to the target media but also to the host computer that is being used to run the dd program.[br]1[/br] [br]1[/br]  Just get yourself a spare 8GB sdcard and use it for testing it gives you a lot of convenient options. That's the best solution I've found with these Pi boards.[br]1[/br] [br]1[/br]   For Watchdog, going by what this site lists it looks like you need at least kernel version(4.2-rc7) but I don't know for sure. [https://lkml.org/lkml/2016/2/9/577](https://lkml.org/lkml/2016/2/9/577) [br]1[/br] [br]1[/br]Hopefully you'll get a Watchdog specific answer and I have not cluttered your thread unnecessarily.

---

