---
title: "Can't add x-fi card kernel module."
date: 2009-06-25
forum: Hardware
---

### Post by warnec on 2009-06-25
-------------------SOLVED--------------------------

see bottom for details, if you like ;)

Hi. I use Arch and I recently switched form 2.6.29 kernel to 2.6.30 kernel, what made me recompile my x-fi card driver (I installed it on 2.6.29 successfully) and everything went well (I mean, I had sound on 2.6.30 kernel). "modprobe ctxfi" worked, and system recognized my card. Now, I recently tried to install aditional packages to make mixeroid plasmoid work (it required some sort of alsa-python libraries), and that's what (I think) broke my x-fi driver. So I removed it, and reinstalled. Then, after successfully building it, I get:
```

[warnec@chakra ~]$ sudo modprobe /lib/modules/2.6.30-ARCH/kernel/drivers/ssound/ctxfi.ko
Has&#322;o:
WARNING: All config files need .conf: /etc/modprobe.d/alsa_blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/framebuffer_blacklist.pacsave, it will be ignored in a future release.
FATAL: Module /lib/modules/2.6.30_ARCH/kernel/drivers/ssound/ctxfi.ko not found.
[warnec@chakra ~]$

```
I tried simple "modprobe ctxfi":
```

[warnec@chakra ~]$ sudo modprobe ctxfi
WARNING: All config files need .conf: /etc/modprobe.d/alsa_blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/framebuffer_blacklist.pacsave, it will be ignored in a future release.
FATAL: Module ctxfi not found.
[warnec@chakra ~]$

```

And it's strange that modprobe can't find ctxfi, because it worked previously just after my update to 2.6.30. insmod finds the module:
```

[warnec@chakra ~]$ sudo insmod /lib/modules/2.6.30-ARCH/kernel/drivers/ssound/ctxfi.ko
insmod: error inserting '/lib/modules/2.6.30-ARCH/kernel/drivers/ssound/ctxfi.ko': -1 Unknown symbol in module
[warnec@chakra ~]$

```

Sure, it doesn't work, but previously (first time I tried to make x-fi work) it also didn't work, but modprobe worked like a charm. I don't know if that's the case, but my kernel is 2.6.30, and kernel-headers is still 2.6.29. Is that wrong?

EDIT.: Solved. I addded "ctxfi" to /etc/rc.conf and modprobe accepted ctxfi module without any problems ;)

---

### Post by Nepherte on 2009-06-25
Concerning the warning messages: [http://www.archlinux.org/news/450/](http://www.archlinux.org/news/450/)

---

