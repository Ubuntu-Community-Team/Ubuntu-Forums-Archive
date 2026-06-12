---
title: "Custom Kernel..."
date: 2008-11-07
forum: General Help
---

### Post by icanfly0307 on 2008-11-07
hi,
      i have ubuntu 8.04 on my old laptop with 256mb ram and 20gig hdd. my boot times are currently ok. i'm not saying its great but its not bad either. will compiling my own custom kernel help increase boot times along with a few tweaks? If it will, could someone recommend a kernel version to go out with and how to compile it within Ubuntu?

Thanks for all your help...

---

### Post by kidders on 2008-11-07
> **icanfly0307 said:**
> will compiling my own custom kernel help increase boot timesIn general, no. Most of the boot process is spent waiting for things to happen, so it's unlikely that tweaking your kernel will have very much impact. Of course, depending on what you change, and what kind of hardware you have, you may even slow the boot process down slightly, I suppose.

Building your own kernel is something you're most likely to feel the benefit (or other side-effects!) of *after* you're machine has booted.

> **icanfly0307 said:**
> could someone recommend a kernel version to go out withImo, unless you have a good reason for *not* doing so, you should always use the newest one available from the official Ubuntu repos. There's plenty of help on configuring and building kernels for Ubuntu around. That said, general documentation targeted at any distro (particularly Debian-like ones) is still worth reading.

I hope that helps.

---

### Post by LateNiteTV on 2008-11-07
i disagree with what kidders said. 
the generic kernels have practically every commonly used driver in them. so on boot, all those drivers that you dont need are being loaded, consequently slowing down boot time. if you know what hardware you have and know what module needs to be loaded and comment out all the unnecessary stuff in your kernel config, then your boot times will speed up.

---

### Post by kidders on 2008-11-07
> **LateNiteTV said:**
> on boot, all those drivers that you dont need are being loadedI'm not sure that makes sense. The whole point in a modular kernel is to avoid loading drivers when you don't need them. For example, let's say you were to rebuild your kernel with no network card drivers except the one you need. There would be no difference in boot time, because there would be no difference in the number of drivers being loaded.

In any case, loading kernel modules is a very brief process. The time it takes is dwarfed by that spent starting services. To extend LateNiteTV's suggestion a little, let's say you omitted drivers for hardware you *do* have, but don't want to use ... eg parallel port, floppy drive, etc. That might save you something of the order of a few tenths of a second.

Doing things like the following will have a much greater impact on boot time ...[LIST]
[*]Disabling unnecessary boot-time checks in your BIOS configurator.
[*]Disabling any services you don't use much (eg printing, bluetooth).
[*]If you really want to (and you know what you're doing), you could tinker with the service startup order, so your boot *appears* to take less time.
[*]Again, if you know what you're doing, you could prelink large applications like Gnome/KDE to shorten loading times.
[/LIST]

---

### Post by icanfly0307 on 2008-11-08
Hey guys,
         Thanks for all your replies. I found a good guide to help decrease the boot time for Ubuntu. I guess I'll update my system and avoid compiling a custom kernel. It takes a lot of time anyway. I've got one more issue down my back...

During the boot process, I disabled usplash so that I can see what's going on in the background. Unfortunately, the boot seems to hang while loading the CD Drive drivers. It hangs at a line that says something like,"...CD Revision Driver (xxx.xxx)..." The boot process continues about 5 minutes later :confused:. Is there a way to completely remove my CD Drive from being recognized at boot? It's broken anyway...:(

Thanks again for your help...

---

### Post by kidders on 2008-11-08
> **icanfly0307 said:**
> the boot seems to hang while loading the CD Drive drivers.You could try blacklisting the driver so it doesn't load, or disabling the device in your BIOS configurator. Alternatively, you could just unplug it, I suppose.

---

### Post by icanfly0307 on 2008-11-08
> **kidders said:**
> You could try blacklisting the driver so it doesn't load, or disabling the device in your BIOS configurator. Alternatively, you could just unplug it, I suppose.

Thanks, I think disabling the CD Drive in the BIOS will do the trick... :D

---

