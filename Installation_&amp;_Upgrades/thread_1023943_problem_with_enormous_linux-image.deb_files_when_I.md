---
title: "problem with enormous linux-image.deb files when I compile the debian way"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by graysky on 2008-12-28
The topic pretty much sums up my experience [compiling a kernel the debian way](http://technowizah.com/2005/12/debian-how-to-custom-kernel-compile.html) under Ubuntu 8.10.

I compiled my 2.6.27.10 kernel using the /boot/config-2.6.27-9-generic file as a starting point (just added a few minor tweaks including my processor type which is Newer Core2/Xeon and upping the timer frequency from 250 to 300 Hz).  I also disabled Xen support because it gives errors otherwise.  The main reason I recompiled was so that my cpu frequency scaler would work which is doesn't with the stock Ubuntu kernel.

ANYWAY, here is my problem: my linux-image-2.6.27.10-custom_amd64.deb is enormous at 236 M.  This is in stark contrast to the standard kernel-image.deb which is 22 M.  Also, when I compile kernels under Debian/Lenny using the Debian config, they are also around 22 M.

Is there an option in the menuconfig that adds in source or something that would explain the 11x size difference?

Debian:
```
5.9M 2008-12-25 12:42 linux-headers-2.6.27.10-xeon64_2_amd64.deb
20M 2008-12-25 12:41 linux-image-2.6.27.10-xeon64_2_amd64.deb
```

Ubuntu:
```
6.5M 2008-12-28 14:37 linux-headers-2.6.27.10-ubuntu64_1_amd64.deb
257M 2008-12-28 14:36 linux-image-2.6.27.10-ubuntu64_1_amd64.deb
```

---

### Post by graysky on 2008-12-28
I went though line-by-line with the Debian kernel config and indeed, the Ubuntu config had a bunch of debugging options enabled under Kernel and elsewhere.  Just got the kernel built and it's the right size after disabling these debugging options.

```
6.5M 2008-12-28 16:36 linux-headers-2.6.27.10-ubuntu64_1_amd64.deb
22M 2008-12-28 16:36 linux-image-2.6.27.10-ubuntu64_1_amd64.deb
```

Now the real question is why doesn't the kernel-image in the repo have the same huge size?  After all, it is built from the same config file as the one I copied over from the /boot isn't it :(

---

