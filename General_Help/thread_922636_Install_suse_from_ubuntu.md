---
title: "Install suse from ubuntu"
date: 2008-09-17
forum: General Help
---

### Post by hjaeger on 2008-09-17
Is it possible to install opensuse openSUSE-11.0-DVD-i386-iso.iso from ubuntu without a dvdrom?

---

### Post by russlar on 2008-09-17
> **hjaeger said:**
> Is it possible to install opensuse openSUSE-11.0-DVD-i386-iso.iso from ubuntu without a dvdrom?

erm.... use unetbootin and a usb flash stick to make a bootable usb drive, and boot to that.

---

### Post by northern lights on 2008-09-17
From within Ubuntu, download the GNU/Linux version of [unetbootin]("http://lubi.sourceforge.net/unetbootin.html"). Run```
sudo apt-get update && sudo apt-get install p7zip-full
```since that package is required for unetbootin to work. Then make unetbootin executable```
sudo chmod 774 ~/unetbootin-linux-281
```(if it's somewhere other than the home folder, enter the respective path)

Thereafter, you can run it either via the terminal or by double-clicking the file in nautilus.

Selct your distro and version of choice, i.e. openSUSE 11, select the device to install to and click OK. Alternatively you could make it use the .iso, but I wouldn't see the need why. Anyhow, reboot and select the unetbootin boot option. openSUSE will be installed.

[EDIT]
Seeing the above post, while it is possible to install to a flashdrive, unetbootin allows direct installation to a partition.
Plus, installing to USB requires the package 'mtools' ontop of 'p7zip-full'.
[/EDIT]

---

