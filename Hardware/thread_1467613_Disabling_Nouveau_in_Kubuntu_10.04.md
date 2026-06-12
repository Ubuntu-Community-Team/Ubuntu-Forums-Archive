---
title: "Disabling Nouveau in Kubuntu 10.04"
date: 2010-04-30
forum: Hardware
---

### Post by UrbenLegend on 2010-04-30
I am trying to install the nvidia proprietary drivers from the nvidia site. However when I run the script it says that nouveau is still running and can't load nvidia.ko. I've tried blacklisting nouveau in /etc/modprobe.d/blacklist.conf, but it still loads up on startup for some damned reason and I don't know how to get rid of it. Uninstalling the nouveau package in the package manager simply leaves me with a corrupted virtual console so I can't install the nvidia driver!

Does anyone know how to install the nvidia drivers properly? And no, I do not want to simply install the nvidia package in the package manager. That driver is never updated to the latest version.

---

### Post by Linuxforall on 2010-04-30
> **UrbenLegend said:**
> I am trying to install the nvidia proprietary drivers from the nvidia site. However when I run the script it says that nouveau is still running and can't load nvidia.ko. I've tried blacklisting nouveau in /etc/modprobe.d/blacklist.conf, but it still loads up on startup for some damned reason and I don't know how to get rid of it. Uninstalling the nouveau package in the package manager simply leaves me with a corrupted virtual console so I can't install the nvidia driver!

Does anyone know how to install the nvidia drivers properly? And no, I do not want to simply install the nvidia package in the package manager. That driver is never updated to the latest version.


blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

sudo apt-get --purge remove nvidia-*

reboot and login to terminal and run installer

All credit to Andy Boy

[http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

---

### Post by UrbenLegend on 2010-05-01
Nope still doesn't work. Nouveau is still loaded upon startup.

Also, nvidiafb and rivafb are already blacklisted by blacklist-framebuffer.conf. I tried blocking vga16fb, nouveau, and rivatv to no avail.

Only way I could work around it was to launch kubuntu in recovery mode, which does not load nouveau at startup, and install from there. But this is a **** poor solution if you ask me.

---

### Post by UrbenLegend on 2010-05-01
Actually you have to blacklist vga16fb and nouveau, THEN boot into recovery mode. Only then will nouveau not load on startup. I have a feeling that nouveau is being loaded by Plymouth during normal startup. Can anyone confirm?

EDIT: You might not actually need to blacklist vga16fb if you're planning to do the driver install in recovery mode. You certainly do need it though after the driver install in order to get the splash screen working properly.

---

### Post by mrpeenut24 on 2010-05-03
From what I can tell, it's stored in initramfs.  So you'll need to rebuild it.  That's why it works when you remove the nvidia drivers through apt-get, it does this for you.  If you don't already have an nvidia driver installed, you'll need to call > sudo update-initramfs -u

(from [here]("http://linux.derkeiler.com/Mailing-Lists/Fedora/2010-01/msg02151.html"))

---

### Post by gab1x on 2010-05-04
Maybe will help !!!

[NVIDIA driver installation on Ubuntu 10.04 - **nouveau** and **nvidia.ko** , **_problem ?_**]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9233555#post9233555") - Hope it helps , GL ;)

---

