---
title: "Just bought a GeForce GTX 465, need help with resolution"
date: 2010-08-27
forum: Hardware
---

### Post by Ubuntarded on 2010-08-27
Just bought this today after my 7800 GTX died, and the screen resolution is absolutely ridiculous. It's difficult enough to even see what I'm typing because everything is so enormous on-screen. How can I adjust the display so I can get a more reasonable resolution?

---

### Post by davidmohammed on 2010-08-27
use grub and boot to recovery mode.

choose to boot to a terminal session

type

sudo apt-get purge nvidia*

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

reboot

then go to administration - hardware drivers to reinstall the recommended nvidia driver.

---

### Post by Ubuntarded on 2010-08-27
My boot process skips right through grub, or perhaps I'm not doing something right and my lack of experience with Ubuntu is to blame, forgot to mention I'm a noob.

My boot process is as follows:

Screen that prompts F1 due to a prior boot failure (old video card died)
blanks screens
Ubuntu

---

### Post by davidmohammed on 2010-08-28
when booting - press and hold shift.  This will display your grub.  At this point, select the recovery mode option

---

### Post by realzippy on 2010-08-28
*If* you had installed the "current" driver for your old 7800 GTX
card,

```
sudo nvidia-xconfig
```

might do it without purging the old driver.

---

