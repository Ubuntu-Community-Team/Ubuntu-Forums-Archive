---
title: "Cannot get 8400M GS at resolution  higher than 640X480"
date: 2008-08-05
forum: Hardware
---

### Post by tekio on 2008-08-05
Lately I've been toying with the idea of switching from Debian to Ubuntu. For some reason there is a serious issue in getting a nVidia 8400M GS to work with Ubuntu 8.04 (the very latest release). I've tried every driver offered by nVidia for this card as well as all drivers offered by Envy installer.

This is really weird as others have reported this to work. I'm a noob, but can usually get video to function properly. Hopefully someone who has got this working can assist me.

PS: Kernel version is 2.6.24-16-generic

Thank you


EDIT:
Full resolution is possible with VESA drivers. Performance is too poor though.

---

### Post by tuxxy on 2008-08-05
Did you try and enable it through system > admin > hardware drivers

---

### Post by tamoneya on 2008-08-05
take a look into nvidia-settings.  Run the following commands in terminal (applications -> accessories -> terminal).
```
sudo apt-get update
sudo apt-get install nvidia-settings
gksudo nvidia-settings
```

---

### Post by tekio on 2008-08-05
The driver was enabled. All option of the nVidia console are disabled. Thanks tought.

---

### Post by tekio on 2008-08-05
Got it!

If anyone is having the same problems here is the fix:
wget [http://uk.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run](http://uk.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run)

chmod 500 ./NVIDIA-Linux-x86-173.14.12-pkg1.run

sh ./NVIDIA-Linux-x86-173.14.12-pkg1.run

Follow all the prompts to build a new module/driver

ctl+alt+backspace or reboot

Enjoy!

---

