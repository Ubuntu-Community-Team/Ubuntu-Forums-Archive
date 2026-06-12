---
title: "SD Card Reader"
date: 2010-10-24
forum: Hardware
---

### Post by gerowen on 2010-10-24
Any time I "safely remove" or unmount an SD card before removing it, I'm unable to use my SD card reader until I reboot the computer.  If I just pull it out, I'm good.  I'm using a Toshiba Satellite L355D-S7829 laptop and Ubuntu 10.10 64bit.

---

### Post by gerowen on 2010-10-24
Turns out there's already a bug in launchpad for this, apparently the "Safely Remove" is safely removing my reader instead of just the SD card, thereby making it unusable until I reboot.  This bug has been around a while though, maybe I'll try doing the "eject" option in the future.

[Launchpad Bug Report](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/504440)

---

### Post by ugm6hr on 2010-10-24
This is also not necessarily an Ubuntu-specific issue.
My dad's desktop card reader does the same in XP.

---

