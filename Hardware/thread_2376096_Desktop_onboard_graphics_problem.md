---
title: "Desktop onboard graphics problem"
date: 2017-10-30
forum: Hardware
---

### Post by coldraven on 2017-10-30
I've been given an old PC that someone foolishly tried to update to Windows 10. The update did not succeed, Windows was using 100% of the CPU and the disk drive was continually churning away at maximum. The PC itself has not been used very much, there is almost no dust inside. I had hoped to install a Linux distro and give the PC to someone as a gift.
Here are some specs: Dual core CPU at 2Ghz and 4 GB RAM
Motherboard is a MSI (Microstar) MS-7313 (I updated the BIOS to the latest version, dated 2007!)
The onboard graphic chip is unfortunately a VIA Tech. K8M800/K8N800/K8N800A (S3 UNICHROME PRO)

I wiped the HDD and installed Linux Mint 18.2. Everything works but it displays a permanent notification saying the it is running graphics in software rendering mode and should only be used for troubleshooting. 
I tried booting from a Lubuntu 17.10 live CD and copied the /var/log/Xorg.0.log
In the log file I see that it tried twice to load openchrome but failed, here's a snippet.
```
[    76.754] (II) LoadModule: "glx"
[    76.757] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    77.154] (II) Module glx: vendor="X.Org Foundation"
[    77.155]     compiled for 1.19.5, module version = 1.0.0
[    77.155]     ABI class: X.Org Server Extension, version 10.0
[    77.155] (==) Matched openchrome as autoconfigured driver 0
[    77.155] (==) Matched modesetting as autoconfigured driver 1
[    77.155] (==) Matched fbdev as autoconfigured driver 2
[    77.155] (==) Matched vesa as autoconfigured driver 3
[    77.155] (==) Assigned the driver to the xf86ConfigLayout
[    77.155] (II) LoadModule: "openchrome"
[    77.156] (WW) Warning, couldn't open module openchrome
[    77.156] (II) UnloadModule: "openchrome"
[    77.156] (II) Unloading openchrome
[    77.156] (EE) Failed to load module "openchrome" (module does not exist, 0)
[    77.156] (II) LoadModule: "modesetting"
[    77.157] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    77.238] (II) Module modesetting: vendor="X.Org Foundation"
[    77.238]     compiled for 1.19.5, module version = 1.19.5
[    77.238]     Module class: X.Org Video Driver
[    77.238]     ABI class: X.Org Video Driver, version 23.0
[    77.238] (II) LoadModule: "fbdev"
[    77.238] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    77.239] (II) Module fbdev: vendor="X.Org Foundation"
[    77.239]     compiled for 1.19.3, module version = 0.4.4
[    77.239]     Module class: X.Org Video Driver
[    77.239]     ABI class: X.Org Video Driver, version 23.0
[    77.239] (II) LoadModule: "vesa"
[    77.239] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    77.265] (II) Module vesa: vendor="X.Org Foundation"
[    77.265]     compiled for 1.19.3, module version = 2.3.4
[    77.265]     Module class: X.Org Video Driver
[    77.265]     ABI class: X.Org Video Driver, version 23.0
[    77.265] (==) Matched openchrome as autoconfigured driver 0
[    77.265] (==) Matched modesetting as autoconfigured driver 1
[    77.265] (==) Matched fbdev as autoconfigured driver 2
[    77.265] (==) Matched vesa as autoconfigured driver 3
[    77.265] (==) Assigned the driver to the xf86ConfigLayout
[    77.265] (II) LoadModule: "openchrome"
[    77.266] (WW) Warning, couldn't open module openchrome
[    77.266] (II) UnloadModule: "openchrome"
[    77.266] (II) Unloading openchrome
[    77.266] (EE) Failed to load module "openchrome" (module does not exist, 0)
[    77.266] (II) LoadModule: "modesetting"
[    77.266] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    77.267] (II) Module modesetting: vendor="X.Org Foundation"
[    77.267]     compiled for 1.19.5, module version = 1.19.5
[    77.267]     Module class: X.Org Video Driver
[    77.267]     ABI class: X.Org Video Driver, version 23.0
[    77.267] (II) UnloadModule: "modesetting"
[    77.267] (II) Unloading modesetting
```

I searched but only found very old results.

The motherboard has an unused AGP 8x slot so I have two questions:
1) Is it possible to install the openchrome driver?
2) Buy a AGP 8x card, if so which make/model should I get?
Thanks in advance

---

### Post by Autodave on 2017-10-30
Hopefully, some one else will have more info than I do. I ndid a quick search on AGP cards. While there are many still available, any of them over 1/2 gig memory are quite expensive. So, I kept my search at 256K or less. All that I found will only be using the legacy driver if you are going w/Nvidia. I would assume that the AMD will be the same.

If the PC is not goin  g to be used for gaming other than solitaire or mahjongg, then one of the 128K boards should be fine and will cost you less than $20.

---

### Post by ajgreeny on 2017-10-30
Those old integrated VIA graphic are a problem now and may be even harder to solve without using Autodave's suggestion of a low cost 128MB AGP card.

Nevertheless here is a reference to a thread about the same problem;
[https://ubuntuforums.org/showthread.php?t=2069995](https://ubuntuforums.org/showthread.php?t=2069995)

It's 5 years old but may still be worth trying the solution shown there in the hope that it might work for you too.

---

### Post by mörgæs on 2017-10-30
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276/)

You could try to experiment with Vesa drivers before searching for a new (old) graphics card.

---

### Post by coldraven on 2017-10-30
Thanks everyone, I've been searching eBay and thought that I had found a cheap 128Mb card only to discover that they don't post to my location....aaaargh!
<goes off to try again>

Edit: I just bought a nVidia 256Mb card. I hope that this solves the problem. Thanks for looking!

---

### Post by mörgæs on 2017-10-30
If your Hyperborea is the same as mine I might have a card you can get.

---

### Post by coldraven on 2017-10-30
> **mörgæs said:**
> If your Hyperborea is the same as mine I might have a card you can get.
Sorry but I might have exaggerated my Latitude a little :) I'm a bit further south than you are. One day I would love to visit Iceland, at the moment I do not have enough money but things can change. In the early days of the Internet I put out too much personal information, now I try to keep a minimal footprint. I'm not paranoid but I object to the level of snooping that seems to have become the new normal.

---

### Post by coldraven on 2017-11-05
I'll mark this thread as solved but in fact I now have a different problem. I bought a Nvidia GeForce FX 5500 AGP 8x card, that solved one problem but I will start a new thread about the display issues that I now have.

---

