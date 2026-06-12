---
title: "Failed Kernal update-no wireless"
date: 2011-12-25
forum: Hardware
---

### Post by Linuxer on 2011-12-25
A couple of days ago, I installed the latest kernal update 2.6.32-37 and it failed to install.  I received the following message:

E: /var/cache/apt/archives/linux-headers-2.6.32-37_2.6.32-37.81_all.deb: unable to create `/usr/src/linux-headers-2.6.32-37/arch/arm/mach-stmp37xx/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-37/arch/arm/mach-stmp37xx/Makefile')
E: /var/cache/apt/archives/linux-headers-2.6.32-37-generic_2.6.32-37.81_i386.deb: unable to create `/usr/src/linux-headers-2.6.32-37-generic/include/config/nls/default.h.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-37-generic/include/config/nls/default.h')

Now, I no longer have wireless connectivity in both Ubuntu 10.04 LTS and Windows 7 (dual boot).  Everything worked perfectly for over a year until this kernal upgrade.

My hardware:
Lenovo G450
Wireless chip broadcom BCM4312

Thanks in advance for your help.

---

### Post by snowpine on 2011-12-25
Hmmm, full root partition maybe?

```
df -h
```

Anyway you should be able to choose your older, working kernel from the GRUB boot menu.

---

