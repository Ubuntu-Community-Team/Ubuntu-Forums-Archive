---
title: "Ubuntu + FX 5200 = OpenGL 2.0?"
date: 2015-05-05
forum: Hardware
---

### Post by leeboy4130 on 2015-05-05
Fairly new Ubuntu 14.04 LTS user here. I have installed Ubuntu + LXDE on an old Dell Dimension 8300 PC. I need to run a program that requires OpenGL2.0. The program will not run at this point. So my first question is...

Is the NVIDIA FX 5200 even capable of OpenGL 2.0? I have read different answers... If my current configuration will not support OpenGL 2.0, I will move on to another PC.

If it is possible....

**lspci | grep VGA**
01:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)

**sudo lshw -C video**
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=64 maxlatency=1 mingnt=5
       resources: memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:fea00000-fea1ffff

**sudo ubuntu-drivers devices**
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000322sv000010DEsd000001B9bc03sc00i00
vendor   : NVIDIA Corporation
model    : NV34 [GeForce FX 5200]
driver   : nvidia-173 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

When I go to "Additional Drivers" it shows two drivers (sorry I can't figure out how to paste a screenshot):
[LIST]
[*]NVIDIA legacy binary driver - version 173.14.39 from nvidia-173 (proprietary, tested) 
[*]X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source) 
[/LIST]

The bullet is always set to the X.Org driver. When I select the NVIDIA driver and click "Apply Changes", it thinks for a bit and then re-selects the X.Org driver. Why can't I choose the NVIDIA driver to see if my program works with it?

Any help is greatly appreciated!

Edit: Just found the system log, problem loading NVIDIA driver:

[   168.839] (--) PCI:*(0:1:0:0) 10de:0322:10de:01b9 rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, BIOS @ 0x????????/131072
[   168.839] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   168.839] (II) "glx" will be loaded by default.
[   168.839] (II) LoadModule: "glx"
[   168.839] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[   168.884] (II) Module glx: vendor="NVIDIA Corporation"
[   168.884]     compiled for 4.0.2, module version = 1.0.0
[   168.884]     Module class: X.Org Server Extension
[   168.884] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:21:57 PST 2014
[   168.884] (II) LoadModule: "nvidia"
[   168.884] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   168.885] (II) Module nvidia: vendor="NVIDIA Corporation"
[   168.885]     compiled for 4.0.2, module version = 1.0.0
[   168.885]     Module class: X.Org Video Driver
**[   168.949]** (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
**[   168.949]** (EE) NVIDIA:     system's kernel log for additional error messages.
[   168.949] (II) UnloadModule: "nvidia"
[   168.949] (II) Unloading nvidia
[   168.949] (EE) Failed to load module "nvidia" (module-specific error, 0)
[   168.949] (==) Matched nvidia as autoconfigured driver 0
[   168.949] (==) Matched nouveau as autoconfigured driver 1
[   168.949] (==) Matched modesetting as autoconfigured driver 2
[   168.949] (==) Matched fbdev as autoconfigured driver 3
[   168.949] (==) Matched vesa as autoconfigured driver 4
[   168.949] (==) Assigned the driver to the xf86ConfigLayout
[   168.949] (II) LoadModule: "nvidia"
[   168.949] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   168.950] (II) Module nvidia: vendor="NVIDIA Corporation"
[   168.950]     compiled for 4.0.2, module version = 1.0.0
[   168.950]     Module class: X.Org Video Driver
**[   169.013]** (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
**[   169.013]** (EE) NVIDIA:     system's kernel log for additional error messages.
[   169.013] (II) UnloadModule: "nvidia"
[   169.013] (II) Unloading nvidia
**[   169.013]** (EE) Failed to load module "nvidia" (module-specific error, 0)
[   169.013] (II) LoadModule: "nouveau"
[   169.013] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   169.014] (II) Module nouveau: vendor="X.Org Foundation"
[   169.014]     compiled for 1.16.0, module version = 1.0.11
[   169.014]     Module class: X.Org Video Driver
[   169.014]     ABI class: X.Org Video Driver, version 18.0
[   169.014] (II) LoadModule: "modesetting"
[   169.014] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   169.015] (II) Module modesetting: vendor="X.Org Foundation"
[   169.015]     compiled for 1.16.0, module version = 0.9.0
[   169.015]     Module class: X.Org Video Driver
[   169.015]     ABI class: X.Org Video Driver, version 18.0
[   169.015] (II) LoadModule: "fbdev"
[   169.015] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   169.015] (II) Module fbdev: vendor="X.Org Foundation"
[   169.015]     compiled for 1.16.0, module version = 0.4.4
[   169.015]     Module class: X.Org Video Driver
[   169.015]     ABI class: X.Org Video Driver, version 18.0
[   169.015] (II) LoadModule: "vesa"
[   169.016] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   169.016] (II) Module vesa: vendor="X.Org Foundation"
[   169.016]     compiled for 1.16.0, module version = 2.3.3
[   169.016]     Module class: X.Org Video Driver
[   169.016]     ABI class: X.Org Video Driver, version 18.0
[   169.016] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[   169.016] (II) NOUVEAU driver for NVIDIA chipset families :
[   169.016]     RIVA TNT        (NV04)
[   169.016]     RIVA TNT2       (NV05)
[   169.016]     GeForce 256     (NV10)
[   169.016]     GeForce 2       (NV11, NV15)
[   169.016]     GeForce 4MX     (NV17, NV18)
[   169.016]     GeForce 3       (NV20)
[   169.017]     GeForce 4Ti     (NV25, NV28)
[   169.017]     GeForce FX      (NV3x)
[   169.017]     GeForce 6       (NV4x)
[   169.017]     GeForce 7       (G7x)
[   169.017]     GeForce 8       (G8x)
[   169.017]     GeForce GTX 200 (NVA0)
[   169.017]     GeForce GTX 400 (NVC0)
[   169.017] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   169.017] (II) FBDEV: driver for framebuffer: fbdev
[   169.017] (II) VESA: driver for VESA chipsets: vesa
[   169.017] (++) using VT number 7

---

### Post by leeboy4130 on 2015-05-06
Nothing??

It shows that I have the up to date driver so I assume re-downloading it won't help me... I looked in the kernal log and it showed where the NVIDIA failed and referenced me to the NVIDIA website to download the current driver that I already have.

---

### Post by mastablasta on 2015-05-07
so what driver is now installed NVidia proprietary or nouveau?

also looks like it doesn't support 2.0:
> **API SUPPORT**

[LIST]
[*]Complete DirectX support, including DirectX 9.0 and earlier
[*]OpenGL 1.5 and earlier support
[/LIST]

[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)

EDIT: but then again here they state they do support it: 
[http://www.nvidia.com/page/pg_20030304335345.html](http://www.nvidia.com/page/pg_20030304335345.html)

anyway make sure you have proprietary drives installed. the opensource NVidia drivers are reverse engineered and usually don't do a good job.

---

### Post by grahammechanical on 2015-05-07
> When I go to "Additional Drivers" it shows two drivers (sorry I can't figure out how to paste a screenshot):

[LIST]
[*]NVIDIA legacy binary driver - version 173.14.39 from nvidia-173 (proprietary, tested) 
[*]X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source) 
[/LIST]


And ubuntu-drivers devices is saying the same thing.

> driver   : nvidia-173 - distro non-free recommended

The latest versions of Ubuntu come with the latest proprietary drivers and in some cases the latest proprietary driver no longer supports older video cards. That is why the legacy proprietary driver is being recommend. Try to install anything newer and there may be problems.

I am in a similar situation. My Nvidia GT 220 works with nvidia 304 but if I try to move on to 346 I get problems.

Here are the technical specifications

> **API SUPPORT**

 
[LIST]
[*]Complete DirectX support, including DirectX 9.0 and earlier 
[*]OpenGL 1.5 and earlier support 
[/LIST]


[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)

Regards.

P.S. You may need to purge the Nvidia driver and restart a couple of times to get Additional Drivers working correctly. That is what I had to do.

---

### Post by Yellow Pasque on 2015-05-07
From what I can tell, the FX5200 only supports hardware acceleration for OpenGL 1.5, though it may be able to support OpenGL 2.x by using software acceleration for some features. Depending on how it advertises its OpenGL compliance and how the program checks for OpenGL support (by simply looking at version or looking at each extension individually), I think it's hard (impossible?) to give a concrete answer to whether a OpenGL 2.x program will run on it.

> [ 168.884] (II) NVIDIA GLX Module 304.125 Mon Dec 1 20:21:57 PST 2014
The log says you have the 304.xx driver installed, which will not work for your card. I'm not sure how you (or Ubuntu) managed to install that for your card.

EDIT: BTW, what kernal are you running? 

> I am in a similar situation. My Nvidia GT 220 works with nvidia 304 but if I try to move on to 346 I get problems.
It's not a similar situation. The 346 series dropped support for all pre-Fermi (pre-GT400) products, so you should not expect it to work. The "Additional Drivers" dialog should not offer it to you, and if it does, it's a bug.
The OP's card should be supported by the 173 driver.

---

### Post by leeboy4130 on 2015-05-09
> **Temüjin said:**
> 

EDIT: BTW, what kernal are you running? 



I believe this is my kernal version (newb):

```
uname -a
Linux dell-Dimension-8300 3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:24:07 UTC 2015 i686 i686 i686 GNU/Linux
```

BTW at some point while I was trying to figure out video drivers, my resolution get screwed up (large icons) and my screen was now a box instead of stretched to my monitor. I just did a clean install of Lubuntu 14.04. My previous posts were with Ubuntu 14.04 + LDXE, not sure if that matters. Anyways with the clean Lubuntu my screen resolution is fixed but I still cannot choose the proprietary driver in "Additional Drivers". I will try purging the NVIDIA driver and restarting as suggested above.

FYI:
```
glxinfo | grep "OpenGL version"
OpenGL version string: 1.5 Mesa 10.3.2
```

Thanks for the replies. I would at least like to try the proprietary driver if I can get it to switch over to it before giving up on this computer.

---

### Post by alex375 on 2015-05-09
you need blacklist nvidia_304 in '/etc/modprobe.d/blacklist.conf'

---

### Post by Yellow Pasque on 2015-05-09
> I believe this is my kernal version
Yes, that's your kernel version and that's part of the problem. Nvidia stopped updating the 173.xx driver last year, so it will not work with Ubuntu 14.04.2 (because 14.04.2 has a newer kernel and Xserver).

Your best bet to get the 173 proprietary driver running is to use a fresh install with 14.04**.1** image and make sure you **don't** upgrade kernel/Xserver to the newer versions found in the LTS point releases: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) (I don't think Ubuntu automatically upgrades you to later LTS kernels, but I can't remember).)
[http://cdimages.ubuntu.com/lubuntu/releases/trusty/release/](http://cdimages.ubuntu.com/lubuntu/releases/trusty/release/)

---

### Post by leeboy4130 on 2015-05-10
So I ended up doing a clean install of Lubuntu 14.04.1 as suggested. This allowed me to go to “Additional Drivers” and switch to the NVIDIA legacy driver which saved for the first time. After a restart I was happy to see:

```
glxinfo | grep "OpenGL version"
OpenGL version string: 2.1.2 NVIDIA 173.14.39
```

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

I then installed the program I have been trying to get going (Simplify3D) and it actually worked!

So about this... > make sure you **don't** upgrade kernel/Xserver to the newer versions found in the LTS point releases: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) (I don't think Ubuntu automatically upgrades you to later LTS kernels, but I can't remember).)

and I also found this... > For Ubuntu 14.04 and/or 14.04.1 users, just install all the system updates via **Software Updater** or run below commands one by one in a terminal (Ctrl+Alt+T):
 sudo apt-get update
sudo apt-get upgrade 
For the Kernel 3.16 and updated X stack, you have to install below packages manually by running command:
 *For Ubuntu Desktop:*
 sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic

Does this mean I can do the update/upgrade but as long as I don't manually install the 3.16 kernel my system should continue to function? I guess I am confused on the differences between the Ubuntu version number 14.04.2 and the 3.16 kernel. It sounds like it will update to 14.04.2 but still run on my current 3.13 kernel?

Thanks for the help I finally made some progress after a week!

---

### Post by Yellow Pasque on 2015-05-10
>  It sounds like it will update to 14.04.2 but still run on my current 3.13 kernel?
Yes, you will get all of the other package updates for 14.04.2 except the LTS kernel/X packages. You're good to go.

---

