---
title: "how to set nomodeset in lucid?"
date: 2010-05-29
forum: Hardware
---

### Post by hufemj on 2010-05-29
I'm having video driver problems with a Dell Latitude D600 and Lucid. It seems that nomodeset might help me. However how to actually install this parameter remains a mystery. Apparently the idea is to add it to /etc/default/grub. Except, that file does not exist on my installation. Has something changed with Lucid with regards to how grub2 is configured? Or is it that the default file is not included by default?

---

### Post by lavinog on 2010-05-29
It depends on your hardware:
[https://wiki.ubuntu.com/X/KernelModeSetting/](https://wiki.ubuntu.com/X/KernelModeSetting/)

---

### Post by drs305 on 2010-05-29
Very little has changed with the Grub2 version in Lucid as far as the default files and where they are located. You should be able to add that option to the GRUB_CMDLINE_LINUX_DEFAULT= line of /etc/default/grub.

First, check that you are using Grub2. It is the default bootloader for Lucid and you should see "grub-install (GNU GRUB 1.98-1ubuntu6)" or something similar as the result of this command:
```
grub-install -v
```

You can also check the version number at the top of the Grub menu when your system boots.

If you are using Grub2, and it is booting properly (but without the desired kernel option) next do a search for the applicable file:
```
sudo find / -type f -name grub
```
As you stated, it *should* be in the /etc/default folder.

---

### Post by oldfred on 2010-05-29
If you did an upgrade not a new install you may still have grub legacy 0.97. If that is the case you still edit menu.lst.

---

### Post by hufemj on 2010-05-30
> **drs305 said:**
> Very little has changed with the Grub2 version in Lucid as far as the default files and where they are located. You should be able to add that option to the GRUB_CMDLINE_LINUX_DEFAULT= line of /etc/default/grub.

First, check that you are using Grub2. It is the default bootloader for Lucid and you should see "grub-install (GNU GRUB 1.98-1ubuntu6)" or something similar as the result of this command:
```
grub-install -v
```

You can also check the version number at the top of the Grub menu when your system boots.

If you are using Grub2, and it is booting properly (but without the desired kernel option) next do a search for the applicable file:
```
sudo find / -type f -name grub
```
As you stated, it *should* be in the /etc/default folder.

Well, that solves the missing grub file mystery. For whatever reason, my desktop has grub2 and is running karmic. I did an upgrade to lucid on my laptop and it does indeed have the older grub.

Thanks!

---

### Post by jrhart on 2010-06-03
I found that if I used the *Radeon.modeset=1* parameter that I was using 100% of one processor in a CoreDuo gateway laptop with ATI mobility X1400 video. Using the *nomodeset *parameter brought the performance back to pre-Lucid levels.:)

---

