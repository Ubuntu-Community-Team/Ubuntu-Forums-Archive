---
title: "[SOLVED] How install older virtual box modules?"
date: 2008-07-30
forum: General Help
---

### Post by evertmantel on 2008-07-30
To be able to use my bluetooth headset i need to use an older kernel version. One thing I'm missing though, is the virtualbox module for this kernel. It's not in the (standard) repositories anymore.

Can anyone tell me how i can still install

virtualbox-ose-modules-2.6.24-14-generic

So that also my virtual box works again?

Thanks!

---

### Post by Fire_Chief on 2008-07-30
You might be able to recompile the virtualbox modules to suit your older kernel. Often when a newer kernel is installed the modules have to be recompiled to work with it. So maybe it works in reverse too.```
sudo /etc/init.d/vboxdrv setup
```

Cheers!

---

### Post by jocko on 2008-07-30
> **evertmantel said:**
> To be able to use my bluetooth headset i need to use an older kernel version. One thing I'm missing though, is the virtualbox module for this kernel. It's not in the (standard) repositories anymore.

Can anyone tell me how i can still install

virtualbox-ose-modules-2.6.24-14-generic

So that also my virtual box works again?

Thanks!

Why not install the full (non-free) version of virtualbox instead of the crippled ose version? It will automatically build the modules for you.
Get rid of the ose version and download the correct .deb from [sun's website]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

---

### Post by evertmantel on 2008-07-30
"Usage: /etc/init.d/vboxdrv {start|stop|restart|status}"

No compiling started.. any other tips? (thanks for your reply)

---

### Post by Fire_Chief on 2008-07-30
Jocko is on the right track. I keep forgetting there are two versions of Virtualbox floating around. I am use the non-OSE version from Sun and it will compile the modules using the command I posted earlier. You should be able to download and install the latest deb from the Sun xVM website. I will automatically upgrade Virtualbox on your system and should start working.

Cheers!

---

### Post by jocko on 2008-07-30
> **Fire_Chief said:**
> You might be able to recompile the virtualbox modules to suit your older kernel. Often when a newer kernel is installed the modules have to be recompiled to work with it. So maybe it works in reverse too.```
sudo /etc/init.d/vboxdrv setup
```Cheers!

> **Fire_Chief said:**
> Jocko is on the right track. I keep forgetting there are two versions of Virtualbox floating around. I am use the non-OSE version from Sun and it will compile the modules using the command I posted earlier. You should be able to download and install the latest deb from the Sun xVM website. I will automatically upgrade Virtualbox on your system and should start working.

Cheers!

To make it even easier: If you have the package "dkms" installed, the virtualbox (non-ose) modules will be built automatically, without any need for you to run vboxdrv  setup manually. When a new kernel is installed, the modules will be built to match the kernel.

---

### Post by evertmantel on 2008-07-30
FireChief, Jocko,

Thanks! Works like a charm!No loss of the current winXP i had installed.. I'm impressed

---

### Post by evertmantel on 2008-08-04
There were some issues with using the update, however. I have seen some other posts as well complaining of the same stuff:
= loss of nvidia driver - you can't reinstall it either
= hibernating does not work properly anymore - it does not recover anymore

Solved these by reinstalling the kernel + kernel headers + non-free drivers for that kernel; basically everything that says "2.6.24-19" (for my kernel) and was installed before. After that I could reactivate the nvidia driver and hibernating worked without extra fiddling again.

---

