---
title: "After recent updates, X won't load Radeon driver: (EE) open /dev/dri/card0: No such"
date: 2017-05-16
forum: Hardware
---

### Post by hayden-haydentech on 2017-05-16
I'm currently running Ubuntu 16.04 LTS.  After installing all the system updates that had accumulated over the past couple weeks, my screens started to behave strangely.  I figured a reboot would solve things, but since then I just get a generic graphics driver instead of the Radeon driver.  The Radeon driver will not load.

I've been running this install since the 13.04 days with no problems, so this was a surprise.  I have dual monitors attached to the ATI card.

This error now appears in my Xorg.0.log:

[    36.276] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
    ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
*... lots of cards deleted...*
[    36.278] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    36.278] (II) FBDEV: driver for framebuffer: fbdev
[    36.278] (II) VESA: driver for VESA chipsets: vesa
[    36.346] (II) [KMS] drm report modesetting isn't supported.
**[    36.346] (EE) open /dev/dri/card0: No such file or directory**
[    36.346] (WW) Falling back to old probe method for modesetting
**[    36.346] (EE) open /dev/dri/card0: No such file or directory**
[    36.346] (II) Loading sub module "fbdevhw"
[    36.346] (II) LoadModule: "fbdevhw"
[    36.346] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    36.374] (II) Module fbdevhw: vendor="X.Org Foundation"
[    36.374]     compiled for 1.18.4, module version = 0.0.2
[    36.374]     ABI class: X.Org Video Driver, version 20.0
[    36.374] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[    36.374] (II) FBDEV(2): using default device
[    36.374] (WW) Falling back to old probe method for vesa
[B][    36.374] (EE) Screen 0 deleted because of no matching config section.

[/B]lspci shows this card installed:[B]
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
[/B]
uname -a:
**Linux billh1 4.4.0-64-generic #85-Ubuntu SMP Mon Feb 20 11:50:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux**

---

### Post by hayden-haydentech on 2017-05-16
Reverting to the 4.4.0-63 kernel restores all video card functionality.  The 4.4.0-64 release must be buggy in regards to dri.  I submitted a bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1691174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1691174)

---

### Post by deadflowr on 2017-05-16
Your updates seemed to be off.
There is an even newer kernel available: 4.4.0-78(?)(I think that's it)
Try updating again and see if the newer kernel gets installed.

---

### Post by hayden-haydentech on 2017-05-16
I've done several apt-get update / apt-get upgrades today.  I'm not offered anything newer than 4.4.0-64.  I'm on the 16.04 LTS version.  Maybe the newer kernels you see are for 16.10 or 17.04.

---

### Post by deadflowr on 2017-05-16
apt-get upgrade won't offer any kernel upgrades.
Use
```
sudo apt-get dist-upgrade
or
sudo apt upgrade
or 
sudo apt full-upgrade
```
A new kernel requires new packages, and apt-get upgrade will not install new packages.
dist-upgrade will install new packages.

apt is a more newly implemented command structure, and it's upgrade command will install new packages.
The apt full-upgrade command also installs new packages, with the added bonus that it can also remove older packages.
You can read what each does in each man page, [man apt]("http://manpages.ubuntu.com/manpages/zesty/man8/apt.8.html") and [man apt-get]("http://manpages.ubuntu.com/manpages/xenial/man8/apt-get.8.html")

The 4.4 kernel series is only available for 14.04.5 and 16.04 and 16.04.1.

---

### Post by hayden-haydentech on 2017-05-19
Reverting to the 4.4.0-63 kernel fixed the problem.  Jumping forward to the pre-release 4.4.0-68 kernel also fixed it.

---

