---
title: "How does linux handle hardware?"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by grim1234 on 2006-03-08
I'm interested in learning how linux, specifically ubuntu, handles hardware and drivers. 

Can anyone recommend any good reading material on the subject?

Thanks,

G.

---

### Post by az on 2006-03-08
What do you mean?  How they are written or developed?

How are they loaded?

Drivers are kernel modules.  When you boot, the kernel and an initrd (a ram disk) containing some hardware detection scripts as well as some essential modules (IDE, PCI, ...) are loaded.  Once the root filesystem can be mounted, it is checked and then the initrd pivot-roots into the root filesystem where the init scripts are run.

Hotplug is run and that detects the remaining hardware (sound, etc...) and loads the modules.  In Dapper, hotplug will be retired and HAL and udev will be used for loading kernel modules.

Some hardware is configured by the package manager.  The X server autodetects your video hardware when you install the package.  I think it has trouble detecting hardware once the x server has been started.  WHen you change you video card, it is best to boot into recovery mode (so that the x server is not started) and tell the package to reconfigure itself.

---

### Post by grim1234 on 2006-03-08
Thanks for your response. My question was purely from a user's point of view. I want to be able to understand how linux will install drivers for each piece of hardware, how that hardware is identified (by both the system and the user), how I can see which kernel modules or similar are loaded at which time, and also, how I can resolve issues with hardware (such as my graphics drivers / wireless)  if needed.

---

