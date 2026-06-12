---
title: "Slow Graphics Performance After Installation of Updates"
date: 2016-08-10
forum: Hardware
---

### Post by Kale_Freemon on 2016-08-10
Hello all.

So, I'm running an old PNY Nvidia GeForce 5200 FX AGP card in my old P4 Dell Dimension 4500. I am using the open source drivers since the proprietary drivers are not supported on 16.04.

For awhile, the performance was great, and I could watch videos with little to no issues.

Today, there was an update that I installed. After that update, and rebooting the machine, I can no longer watch videos as they are choppy as can be.

I also noticed that I no longer have the ability to change my screen resolution. I'm stuck in 1280 x 1024 with a refresh rate of 77.

I'm not sure what's going on at this point.

Any ideas on how to fix this would be great. Thank you in advance.

Below is everything that updated today on my system.

```
Start-Date: 2016-08-10  09:17:41Commandline: aptdaemon role='role-commit-packages' sender=':1.45'
Install: linux-image-extra-4.4.0-34-generic:i386 (4.4.0-34.53, automatic), linux-headers-4.4.0-34-generic:i386 (4.4.0-34.53, automatic), linux-headers-4.4.0-34:i386 (4.4.0-34.53, automatic), linux-image-4.4.0-34-generic:i386 (4.4.0-34.53, automatic)
Upgrade: libmpx0:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libgcc-5-dev:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), linux-headers-generic:i386 (4.4.0.31.33, 4.4.0.34.36), linux-libc-dev:i386 (4.4.0-31.50, 4.4.0-34.53), xserver-common:i386 (2:1.18.3-1ubuntu2.2, 2:1.18.3-1ubuntu2.3), libcurl3:i386 (7.47.0-1ubuntu2, 7.47.0-1ubuntu2.1), xserver-xorg-core:i386 (2:1.18.3-1ubuntu2.2, 2:1.18.3-1ubuntu2.3), grub-common:i386 (2.02~beta2-36ubuntu3.1, 2.02~beta2-36ubuntu3.2), linux-image-generic:i386 (4.4.0.31.33, 4.4.0.34.36), cpp-5:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), snapd:i386 (2.0.10, 2.11+0.16.04), binutils:i386 (2.26.1-1ubuntu1~16.04.1, 2.26.1-1ubuntu1~16.04.3), language-selector-common:i386 (0.165.3, 0.165.4), libitm1:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libxatracker2:i386 (11.2.0-1ubuntu2, 11.2.0-1ubuntu2.1), grub2-common:i386 (2.02~beta2-36ubuntu3.1, 2.02~beta2-36ubuntu3.2), libegl1-mesa-drivers:i386 (11.2.0-1ubuntu2, 11.2.0-1ubuntu2.1), libcilkrts5:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libegl1-mesa:i386 (11.2.0-1ubuntu2, 11.2.0-1ubuntu2.1), libasan2:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libquadmath0:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), grub-pc:i386 (2.02~beta2-36ubuntu3.1, 2.02~beta2-36ubuntu3.2), libgbm1:i386 (11.2.0-1ubuntu2, 11.2.0-1ubuntu2.1), grub-pc-bin:i386 (2.02~beta2-36ubuntu3.1, 2.02~beta2-36ubuntu3.2), gcc-5-base:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libstdc++-5-dev:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libubsan0:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), g++-5:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libgfortran3:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libwayland-egl1-mesa:i386 (11.2.0-1ubuntu2, 11.2.0-1ubuntu2.1), gcc-5:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libgomp1:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libgl1-mesa-dri:i386 (11.2.0-1ubuntu2, 11.2.0-1ubuntu2.1), mesa-vdpau-drivers:i386 (11.2.0-1ubuntu2, 11.2.0-1ubuntu2.1), libatomic1:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), language-selector-gnome:i386 (0.165.3, 0.165.4), libcc1-0:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), libstdc++6:i386 (5.4.0-6ubuntu1~16.04.1, 5.4.0-6ubuntu1~16.04.2), curl:i386 (7.47.0-1ubuntu2, 7.47.0-1ubuntu2.1), linux-generic:i386 (4.4.0.31.33, 4.4.0.34.36), libcurl3-gnutls:i386 (7.47.0-1ubuntu2, 7.47.0-1ubuntu2.1), less:i386 (481-2.1, 481-2.1ubuntu0.1)

```


Update:

It would appear that the latest kernel upgrade that was pushed out is what was causing my problem. I booted back into my system using the 4.4.0-31 kernel and everything is acting normal again.

Anyone know of anyway to allow me to use the latest version of the kernel available without causing such issues?

---

