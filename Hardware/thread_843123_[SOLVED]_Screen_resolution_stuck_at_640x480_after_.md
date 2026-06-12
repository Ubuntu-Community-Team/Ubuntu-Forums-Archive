---
title: "[SOLVED] Screen resolution stuck at 640x480 after NVIDIA driver update"
date: 2008-06-28
forum: Hardware
---

### Post by nurfimus on 2008-06-28
I am on a Dell Inspiron 1520 with an NVIDIA 8600M GT.

I tried updating my NVIDIA driver from 169.12 to 173.14.05. Had some issues closing out of X11 and doing it at root level, but I was eventually able to install it using EnvyNG. For some reason, after I rebooted my display is stick at 640x480. The NVIDIA driver is not showing up in System>Administration>Hardware Drivers, and it won't let me resize the resolution in System>Preferences>Screen Resolution. I'm worried I screwed something up when trying to install it manually at root.

Does anyone know how I can resolve this?

Thanks in advance!

---

### Post by overdrank on 2008-06-28
> **nurfimus said:**
> I am on a Dell Inspiron 1520 with an NVIDIA 8600M GT.

I tried updating my NVIDIA driver from 169.12 to 173.14.05. Had some issues closing out of X11 and doing it at root level, but I was eventually able to install it using EnvyNG. For some reason, after I rebooted my display is stick at 640x480. The NVIDIA driver is not showing up in System>Administration>Hardware Drivers, and it won't let me resize the resolution in System>Preferences>Screen Resolution. I'm worried I screwed something up when trying to install it manually at root.

Does anyone know how I can resolve this?

Thanks in advance!

Hi and you can try and boot into recovery mode and use xfix to correct the graphics or reconfigure you xorg with this command in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` If you used Envy to install the drivers after you manually installed this could cause some issues.

---

