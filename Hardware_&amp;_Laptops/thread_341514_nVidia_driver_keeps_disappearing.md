---
title: "nVidia driver keeps disappearing"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by Mazin on 2007-01-18
Somehow, my nVidia drivers magically broke.  I reinstalled nvidia-glx, nvidia-kernel-modules-common, and linux-restricted-modules-386 and it worked, *for that session*.

After I rebooted *the kernel module was gone*.  X failed on startup, saying that it couldn't load nvidia.ko.
Well, "modprobe nvidia" said it didn't exist, so I reinstalled nvidia-glx, nvidia-kernel-modules-common, and linux-restricted-modules-386 and it worked for that session.

Next reboot, nvidia.ko is gone.  Poof.

What's going on?? How do I fix it?

---

### Post by scrooge_74 on 2007-01-18
did you check the howto for Nvidia? [http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

