---
title: "Error when running &quot;make modules&quot;"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by Swinkle on 2005-12-28
Hi guys,

I'm having a problem that I'm hoping somebody can help me with. I've just tried to install a new graphics driver and following the instructions in the readme file for the driver I did make menuconfig in my /usr/src/linx-xxx folder.

I added the "Framebuffer Console support" as a module, saved the changes and ran "make modules" as instructed but I get the following error:

```
root@ubuntu:/usr/src/linux-headers-2.6.12-10-386# make modules
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
  HOSTCC  scripts/pnmtologo
make[1]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make: *** [arch/i386/kernel] Error 2

```

I've never run make modules before so I have no idea whether the added module is causing the problem or whether the problem was there undetected before. Can anyone shed a little light on this?

Thanks,
Dave

---

### Post by Swinkle on 2005-12-29
*bump*

Anyone?

---

### Post by sefs on 2007-04-22
Need some solutions to these compilation problems.

Thanks. :)

---

